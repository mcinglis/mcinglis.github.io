---
layout:    "default"
date:      "2014-05-26 00:21:45-04:00"
title:     "How to Import Mail from Thunderbird to Evolution"
tags:      ['howto']
---

Of the graphical email clients, I dislike [Evolution](https://wiki.gnome.org/Apps/Evolution/) the least. It's integrated with GNOME, and has PGP signing and encryption built in.

As of Evolution 3.10.4 and [Thunderbird](https://www.mozilla.org/en-US/thunderbird) 24.5:

You don't need to install dodgy addons to get your email out of Thunderbird, because Thunderbird stores its email in the Mbox format on your disk.

First, for safety, quit Thunderbird.

In Evolution, go to *File > Import...*. Select *Import a single file* in the *Importer Type* section. Then, for *Filename*, select the desired file at `~/.thunderbird/<profile>/Mail/<account>/<FolderName>` to import all the email in that folder. For example, I had an "Archive" folder containing folders "2014", "2013", so to import the mail in "2013" I selected `thunderbird/<profile>/Mail/<account>/Archives.sbd/2013`. Evolution will hang if the selected file is large. Make sure "Berkeley Mailbox (mbox)" is selected for *File type*. On the next section, you can select the folder (in Evolution) to import the mail into. Hit *Import*, and you're done.

You have to repeat this process for all the folders you want to import from Thunderbird.

