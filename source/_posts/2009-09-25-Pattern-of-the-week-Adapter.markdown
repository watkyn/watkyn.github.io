---
layout: post
title: Pattern of the week - Adapter
date: 2009-09-25 21:33:09 UTC
updated: 2009-09-25 21:33:09 UTC
comments: false
categories: patterns
---

From Java Design Patterns:<br /><span class="docEmphStrong">The intent of</span> A<span class="docEmphSmaller">DAPTER</span> <span class="docEmphStrong"><a name="client expects"></a>is to provide the interface that a client expects while using the services of a class with a different interface.<br /><br />This actually makes sense to me right out of the gate.  I've probably read about and used Adapter before but needed a refresher on what it actually was.<br /><br />So lets say that I have a lab processing class that takes LabOrder objects and processes them somehow.  Another team in my company has a service that supplies LabResults from a different vendor than the one I work with but they like the processing class I made and want me to process their LabResult class also.<br /><br />I see that the objects do similar things but have slightly different methods, so I create an adapter class that implements the LabOrder interface and delegates to the LabResult object that is passed in to the constructor.  No code changes required for the lab processing class.<br /><br />githup <a href="http://github.com/watkyn/scripts/blob/master/patterns/adapter.rb">Adapter</a> code<br /><br /><br /></span>
