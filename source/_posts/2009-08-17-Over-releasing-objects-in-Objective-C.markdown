---
layout: post
title: Over releasing objects in Objective-C
date: 2009-08-17 13:11:41 UTC
updated: 2009-08-17 13:11:41 UTC
comments: false
categories: iphone objective-c
---

I just learned the difference between over releasing an object and attempting to release an unallocated object.
I saw this example in an iPhone book where an instance variable was being released before it was assigned.

``` objective-c
– (void)parserDidStartDocument:(NSXMLParser *)parser {
  [tweetsString release];
  tweetsString = [[NSMutableString alloc] initWithCapacity: (20 * (140 + 20)) ];
  // more code
}
```
I was wondering why the release on the first line was not blowing up, since I have experienced errors in my code when I over release an object (that is, I call release on an object more than once).  
So I tried an experiment and put multiple [<span class="blsp-spelling-error" id="SPELLING_ERROR_8">tweetString</span> release]; calls all in a row, thinking this would blow up. 
 But it works just fine.

The reason is that a nil object (one that has never been allocated) is never sent any messages.  There are no NullPointerExceptions since the messages are just discarded. Objective-C is a no-op language on nil, and you can rely on that in your code this way. So it is safe to call release on an unallocated object, but you cannot send release to an object more than once AFTER it has been allocated.<br /><br />I should have realized this before, since this is the way properties work when set to retain.

