---
layout: post
title: Pattern of the week - Composite
date: 2009-06-08 13:12:54 UTC
updated: 2009-06-08 13:12:54 UTC
comments: false
categories: patterns
---

The intent of the COMPOSITE pattern is to let clients treat individual objects and compositions of objects uniformly. (Java Design Patterns)<br /><br />There are objects that have children and there are objects that don't.  The objects that have children can have a common interface with the objects that do not have children, and so Composite.<br /><br />The example I used in my code (see below) was that of a Menu and MenuItems.  Swing uses this model for its menus.  A Menu may or may not have sub menus.  A MenuItem, however, never has sub menus; it is always the end of the road, a leaf.<br /><br />A process may want to traverse a tree of objects but it does not want to have to figure out who has child elements and who does.  Composite attempts to solve this problem by establishing a common interface between the two types.  Then the object that has children can traverse its children when the common method is called and call the common method on the child objects.<br /><br />Here is a <a href="http://github.com/watkyn/scripts/blob/4666ef973f91edc6d4fbf8ca5f8ecee3e269a734/patterns/composite.rb">link to the ruby code</a> I wrote up to help me understand Composite better.<br /><br /><br />I ran into another good example over the weekend.  We went to a tree identification outing and the naturalist there had a identification key.  It used decision tree logic, and I thought to myself, "Hey, the Composite pattern in real life!".  What a geek I am sometimes.<br /><br />Each question led to either one or many follow up questions.  I thought of putting the logic into an iPhone application, and realized I could model the questions as Composites.  Some questions would be trees, and others would be leaves.  Perfect for a tree identification app!
