---
layout: post
title: SVN Eclipse Mountain Lion and Homebrew
date: 2013-02-14 14:28:37 UTC
updated: 2013-02-14 14:28:37 UTC
comments: false
categories: eclipse svn osx
---

I was frustrated trying to figure out how to get subversion installed on my OSX machine so that it would be compatible with Eclipse. I wanted to go with the JavaHL svn adapter but I had already installed svn using homebrew.<br />I tried to reinstall svn with homebrew like this but got an error:
<br /><pre>$ brew install --universal --java subversion<br />   Error: subversion dependency neon not installed with:<br />     --universal<br /><br /></pre>There are several dependencies that need to be uninstalled before installing subversion again with --univeral and --java options <br />For me it was this:<br /><br /><pre><br />$ brew rm neon<br />$ brew rm sqlite<br />$ brew rm serf<br /></pre><br />Then this worked:<br /><pre>$ brew install --universal --java subversion</pre>
