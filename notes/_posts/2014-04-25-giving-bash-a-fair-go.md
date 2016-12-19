---
layout:    "default"
date:      "2014-04-25T14:20:30-04:00"
updated:   "2014-05-29T12:30:00-04:00"
title:     "Giving Bash a Fair Go"
---

I've been [reading](http://matt.might.net/articles/bash-by-example/) [up](http://robertmuth.blogspot.de/2012/08/better-bash-scripting-in-15-minutes.html) [on](http://mywiki.wooledge.org/BashGuide) [Bash](http://tldp.org/LDP/abs/html/abs-guide.html) lately. I've become fascinated by [streams](https://en.wikipedia.org/wiki/Stream_%28computing%29) and the simplicity of shell programming.

I love that Bash is built around streams, and that it's the default shell of all major \*nix operating systems.

I dislike Bash's rigid and arcane syntax, lack of data structures, and inability to cleanly define arguments for functions and scripts. I wish there were better (built-in) tools for writing argument parsers for shell scripts.

I wrote some Bash scripts earlier this week to make it easier to make new posts on my site.

``` bash
#!/bin/bash


newpost() {
    local  category="$1"
    local     title="$2"
    local      link="${3:-''}"

    local published="$(date)"
    _newpost_header "$category" "$title" "$published" "$link" \
        > "$(_newpost_filename "$category" "$title" "$published")"
}


_newpost_header() {
    local  category="$1"
    local     title="$2"
    local published="$(_newpost_header_date "$3")"
    local      link="$4"

    local headersep="---"
    echo "$headersep"
    echo "layout: default"
    echo "title: '$title'"
    echo "published: '$published'"
    if [[ $category = "links" ]]; then
        echo "link: '$link'"
    fi
    echo "$headersep"
}


_newpost_header_date() {
    date --date="$@" --iso-8601='minutes'
}


_newpost_filename() {
    local category="$1"
    local    title="$(_newpost_fntitle "$2")"
    local     date="$(_newpost_fndate "$3")"
    echo "$category/_posts/$date-$title".md
}


_newpost_fndate() {
    date --date="$@" +'%Y-%m-%d'
}


# $ _newpost_fntitle This is-a Ca$h   Title
# this-is-a-cah-title
_newpost_fntitle() {
    local title="$@"
    _newpost_joinwords '-' $(echo "$title" |
                              tr --delete --complement '[:alnum:]\- ' |
                              tr '[:upper:]' '[:lower:]')
}


# $ _newpost_joinwords '-' "These are"   S0me  words
# These are-S0me-words
_newpost_joinwords() {
    local IFS="$1"
    shift
    echo "$*"
}


# If we aren't an interactive shell, then run the main function.
if [[ $- != *i* ]]; then
    set -o errexit
    set -o pipefail
    set -o nounset
    newpost "$@"
fi
```

I realized that because the `newpost` function only does redirection, its components should be broken off into other scripts so that they are usable via the common interface - text - and not only to other Bash scripts.

I then rewrote the header generation part like so:

``` bash
#!/bin/bash

set -o errexit
set -o pipefail
set -o nounset


readonly PROGRAM_NAME="$0"


main() {
    local i=1
    for arg in "$@"; do
        case "$arg" in
            '-y' | '--layout' )    local    layout="${@[$i]}" ;;
            '-t' | '--title' )     local     title="${@[$i]}" ;;
            '-p' | '--published' ) local published="${@[$i]}" ;;
            '-l' | '--link' )      local      link="${@[$i]}" ;;
            '--help' )             _print_help; exit 0;       ;;
        esac
        (( i += 1 ))
    done
    layout=${layout:-'default'}
    title=${title:-''}
    published=${published:-$(date)}
    link=${link:-''}

    local headersep='---'
    echo "$headersep"
    echo "layout:    '$layout'"
    echo "title:     '$title'"
    echo "published: '$(date --date="$published" --iso-8601='minutes')'"
    if [[ $link ]]; then
        echo "link:      '$link'"
    fi
    echo "$headersep"
}


print_help() {
    cat <<EOF
Usage: $PROGRAM_NAME [options...]
Prints the header of a new Jekyll post to stdout.

  -y, --layout LAYOUT   the 'layout' attribute of the header
  -t, --title TITLE     the 'title' attribute of the header
  -p, --published DATE  the 'published' attribute of the header (default: now)
  -l, --link LINK       the 'link' attribute of the header
      --help            display this help and exit
EOF
}


main "$@"
```

Pretty succinct, simple and readable for a Bash script. Unfortunately, there's repetition of the script argument names, and in their assignment to variables. I can't work out anyway I can avoid this while keeping the script simple.

So, I turned to Python. Although it depends on a virtual machine an order of
magnitude more complex than GNU Bash's implementation, Python provides a capable
standard library and a reliable and consistent syntax. In particular, it
provides the [`argparse`](https://docs.python.org/3.3/howto/argparse.html)
module for parsing command-line arguments.

You can view my Python rewrites of the above scripts [here](https://github.com/{{ site.author.github }}/jekyll-scripts/). While argument parsing and input validation are easier, you can see how painful it is to redirect IO in Python. I've gone to great lengths to try to retain the stream-based architecture that is easily achievable with Bash, but I'm not sure if I actually achieved that - or if it's even worth it with Python.

Still, Bash's inability to easily process command-line arguments puts it out of the running for non-throwaway scripting, in my opinion. Bash shines at stream programming, but it becomes a pain when you want to address edge cases, handle command-line arguments, or work with data structures.

