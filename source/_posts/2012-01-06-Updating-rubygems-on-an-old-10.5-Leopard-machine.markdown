---
layout: post
title: Updating rubygems on an old 10.5 Leopard machine
date: 2012-01-06 21:04:18 UTC
updated: 2012-01-06 21:04:18 UTC
comments: false
categories: osx ruby
---

I ran into this problem today when trying to update my ruby gems on a fresh OSX 10.5 machine for testing:<br /><br />Updating RubyGems...<br />ERROR:  While executing gem ... (Gem::RemoteSourceException)<br />    HTTP Response 302 fetching http://gems.rubyforge.org/yaml<br /><br /><br />After a little googling I saw where gems were stored on S3 so I just added the --source option and that worked.  Here is the command for posterity.<br /><br />gem update --system --source http://production.s3.rubygems.org/