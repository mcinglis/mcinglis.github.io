---
layout: default
title: A Platform to Call My Own
---

This is my platform, and mine alone.

I write templates in plain text, commit them to a local [Git](http://git-scm.com) repository, and push those changes up to my [GitHub Pages](http://pages.github.com/) [repository](https://github.com/zenmunki/zenmunki.github.io). GitHub processes those templates with [Jekyll](https://github.com/mojombo/jekyll/), and serves the generated files at [minglis.id.au](http://minglis.id.au).

I could've pointed my domain at a blog running on WordPress, Tumblr, or Blogger, so why have I opted for Jekyll?

At first, it was appealing to have complete control of every page. From byte 0 to EOF, I decide what's sent. My visitors are only subject to what I want: no analytics, tracking, ads, or broken [semantics](https://en.wikipedia.org/wiki/Semantic_web).

It's close to the metal, and I love it. How do I add [FOAF](http://xmlns.com/foaf/spec/) annotations to my profile, or add [Open Graph](http://ogp.me/) metadata to my posts, or semantically license my site content with [Creative Commons](https://creativecommons.org/licenses/by/3.0/)? I just add them to the template. Plugins? No thanks.

Jekyll affords me a simple conceptual model of how my website works. Pages are parsed to objects, and their layout then determines where to put stuff. That's pretty much it. In contrast, I have no idea how platforms like WordPress or Blogger work. I enter stuff into a textarea and it's magic the rest of the way. [Donald Norman](http://www.jnd.org/) wrote about the importance of providing users a clear conceptual model in the [first chapter](http://www.sharritt.com/CISHCIExam/norman.html#1) of his book, [The Design of Everyday Things](https://en.wikipedia.org/wiki/The_Design_of_Everyday_Things).

With Git and Jekyll, [I own my data](http://www.ironfroggy.com/on/web-data-ownership/owning-your-cloud-data). Git means I have to have a local copy of my site to change it. Jekyll means my work is stored in plain text. Ergo, I'll always have my own copy of my data in a future-proof format.

If you run a blog on WordPress, Tumblr or Blogger, I bet you don't export your posts very often. What would you do if your service took down your blog *right now*? Maybe the [Internet Archive](https://archive.org) archived your site. If so, maybe you would bother to scrape the archives to download your posts. Maybe you'd get lazy and just download every page as-is. Even then, if you do manage to save your posts, will you bother to publish them elsewhere? Can you publish them at their old location, or will the [URLs and feeds die](http://www.w3.org/Provider/Style/URI.html)?

Because I own my data and my domain, I can guarantee persistence. If GitHub shuts down in ten years, I'll serve my site from somewhere else, and point my domain there. If my account is [cracked](http://catb.org/jargon/html/C/cracker.html), or GitHub closes my account [for some reason](https://help.github.com/articles/github-terms-of-service), and my data is deleted, no worries: I have a copy on my computer.

And then there's the small stuff. I can write my posts in Vim. Using Git means my site is versioned, so I don't need to create copies of files if I want to experiment. GitHub Issues lets other people raise issues, contribute material, and fix things.

It's not perfect, but this is my platform.

Now to make something of it.
