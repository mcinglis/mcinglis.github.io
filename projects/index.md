---
layout: default
title: Projects
hide_license: true
hide_comments: true
---

**[Libargs](https://github.com/mcinglis/libargs)**: a C library for parsing command-line arguments according to a declarative speculation. Automatic help text generation is a todo, but can be added without changing the API.

**[Liblogging](https://github.com/mcinglis/liblogging)**: a barebones logging library for C; flexible yet simple. This is all I want a logging library to be.

**[Libarray](https://github.com/mcinglis/libarray)**, **[Libvec](https://github.com/mcinglis/libvec)**: more generic data structure libraries for C. I'm most proud of my API innovations around [view](https://github.com/mcinglis/libarray/blob/5545d42dc36e915f5301cba88f322aa603ddbac7/source.c.jinja#L582) and [query](https://github.com/mcinglis/libarray/blob/5545d42dc36e915f5301cba88f322aa603ddbac7/source.c.jinja#L885) functions, and my in-place, allocation-free [quicksort implementation](https://github.com/mcinglis/libarray/blob/5545d42dc36e915f5301cba88f322aa603ddbac7/source.c.jinja#L2951).

**[Libmaybe](https://github.com/mcinglis/libmaybe)**: a "generic" C library providing value-or-nothing semantics. It works within my typeclass convention system; equality is defined for `Maybe_X` if it's also defined for the type `X`.

**[Libtypes](https://github.com/mcinglis/libtypes)**, **[Libbase](https://github.com/mcinglis/libbase)**, **[Libstr](https://github.com/mcinglis/libstr)**: utility functions for the standard C types (and some new types like `ord`). The safe, bounded arithmetic functions have proven to be very useful. These libraries provide the base for my generic typeclass templating approach to C programming, as implemented in my other libraries.

**[Libpp](https://github.com/mcinglis/libpp)**, **[Libmacro](https://github.com/mcinglis/libmacro)**: standards-*conformant* functional-programming macros for the C preprocessor. It's implemented with template files rendered by [a Python script](https://github.com/mcinglis/tplrender).

**[Puck](https://github.com/mcinglis/puck)**: a command-line tool for managing project dependencies. With a package's direct dependencies specified (by Git URLs) in a JSON file, Puck will recursively fetch and build all dependencies per the command. It's still a bit rough, but has worked well enough for me.

**[Macrofun](https://github.com/mcinglis/macrofun)**: standards-defying functional-programming macros for the C preprocessor.

**[Assembly Sandbox](https://github.com/mcinglis/assembly-sandbox)**: my forays into x86-64 assembly programming. It's really fun, and I've learned a lot.

**[Jekyll Scripts](https://github.com/mcinglis/jekyll-scripts)**: some scripts that handle creating new posts for my website. They should be usable on any Jekyll site that uses the same header-data convention mine does.

