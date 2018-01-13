---
id: 671
title: 'My Setup and Tools - July 2016'
date: 2016-07-01T16:13:51+00:00
author: Richard Borges
layout: post
guid: https://richardborges.net/?p=671
permalink: /my-setup-and-tools-july-2016/
categories:
  - Software
tags:
  - Tools
---

Here is my development setup list of tools. 

* VS 2015 community edition
* Jet Brains Resharper ( paid )
* Productivity Power Tools 2015 (free plugin to VS2015)
* [Web Essentials](https://visualstudiogallery.msdn.microsoft.com/ee6e6d8c-c837-41fb-886a-6b50ae2d06a2) 2015.5 (free plugin for VS2015)
* automapper.org  
* [bootbox.js](http://bootboxjs.com/) make your pop-over front and centre. Bootbox.js is a small JavaScript library which allows you to create programmatic dialog boxes using Bootstrap modals, without having to worry about creating, managing or removing any of the required DOM elements or JS event handlers.   
* animate.css for nice bouncy effects  
* Templating engine [underscorejs](underscorejs.org)
* momentjs.com moment.js library to format date time in javascript
* Less to css or use http://css2less.co for legacy css to less conversion (makes my css� code clearner in my VS project).
* Bootstrap , input group , components -> search button to the right of the text box
* Organize your javascript library http://requirejs.org
* Dependency Injection library: NinJect.MVC5 ver: 3.2.1.0
* Use convention over configuration PM>install-package Ninject.extensions.conventions
* Unit Testing tools (add to Test project): Moq PM> install-package moq -version:4.2.1510.2205
* Unit Testing tools (add to Test project): FluentAssertions PM> install-package FluentAssertions -version:3.3.0
* Unit Testing a repository. google.com.au search for 'mock dbset' to get code from MSDN.  https://msdn.microsoft.com/en-us/library/dn314429.aspx. Use that code to populate my DBSet for testing.
* Integration Test: (Integration Test project) use nUnit because it has a feature to initialization databases that MSTest does not have.  
    PM> install-package nunit -version:2.6.3
* DotCover by JetBrains - to find how much of our code is covered by our tests


