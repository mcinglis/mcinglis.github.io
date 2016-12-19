---
layout:    "default"
date:      "2014-05-29 11:56:47-04:00"
title:     "Defensive Bash Programming"
link:      "http://www.kfirlavi.com/blog/2012/11/14/defensive-bash-programming/"
comments:
    - from: "https://news.ycombinator.com/item?id=7816085"
      published: "2014-05-29T10:00-04:00"
      content: |
          The article mentions so many topics, but misses almost all important ones.

          * First of all, use proper quoting. There are so many possibilities for file names, command line arguments, etc. that every unquoted usage of a variable is essentially a security risk.

          * Then, start your script with `set -e`, which stops the script whenever one of the commands fail, instead of blindly continuing and messing things up. This is the most important option for robust shell scripts.

          * Also use `set -u` which makes the script stop on undefined variables. This includes `$1`, `$2`, etc., so it provides checks for missing arguments for free.

          * In addition to `set -e`, also set `set -o pipefail`, otherwise a pipe will only break if the last command fails, while with `set -o pipefail` the pipe fails whenever any command of the pipe fails.

          * After that, you may continue with spacing issues in `for` loops, and that you should not pipe the `find` output directly (instead, use either `-print0` + `xargs -0`, or use `-exec`), and similar stuff.

          When you got all of this right, and only then!, you may start worrying about the (relatively) minor issues mentioned in the article.
---

This post is a nice start, but it misses a bunch of (important) protections to use when programming Bash - see [this post](/notes/2014/04/25/giving-bash-a-fair-go.html) for links and discussion.

I've included a comment from HN echoing a similar sentiment.


