---
layout: post
title: Legacy Code - Extract Interface
date: 2010-01-11 14:53:29 UTC
updated: 2010-01-11 14:53:29 UTC
comments: false
categories: refactoring
---

Micheal Feathers book "Working with legacy code " has a chapter called Extract Interface.  This is taken from Fowler's Refactoring book and applied to legacy code.<br /><br />The motivation for extracting an interface is different between the two books.  Refactoring looks at this from the point of code organization and structure.  Working With Legacy Code looks at this as a dependency breaking mechanism to get a class under test.<br /><br />Both aims are to make the code more maintainable over time, and the use of interfaces to represent concepts in code is a great way to do that.<br /><br />How would this play into something like ruby?  Well, the dependency issue is virtually non-existent from a testing point of view.  Getting a class under test is as easy as using a mocking library (Actually, the same can be said for Java in the example from Micheal's book).
