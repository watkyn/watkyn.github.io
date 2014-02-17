---
layout: post
title: vim compiled with ruby support on Lion
date: 2012-01-06 21:03:30 UTC
updated: 2012-01-06 21:03:30 UTC
comments: false
categories: osx ruby vim
---

If you are a vim user on a Mac and you also like the <a href="https://github.com/wincent/Command-T">Command-t</a> plugin you have no doubt had to deal with the default vim, which does not come with ruby support out of the box. I have resorted to using <a href="http://code.google.com/p/macvim/">MacVim</a> for most of my needs but once in a while I wish Command-t was there for me in a vim terminal (read tmux).<br /> <br />Well, I just found out that MacVim ships with a Vim and MacVim executable, so just use that.<br /> <br />I added this alias to my bash profile and all was good:<br /><br /><span style="font-weight:bold;">alias vim=&#39;/Applications/MacVim.app/Contents/MacOS/Vim&#39;</span><br /><br />That will take precedence over /usr/bin/vim (except if you do sudo vim, then you are back to the old /usr/bin/vim).<br /> <br />Good enough, is what I say.<br /> <br /><br />PS. I made a symlink from /Applications/MacVim.app/Contents/MacOS/Vim into /usr/bin/vim and it didn&#39;t work quite right. I got a bunch of warnings about color scheme, etc. Not sure why, but I didn't feel the need to dig deeper. That is why I went the alias route.