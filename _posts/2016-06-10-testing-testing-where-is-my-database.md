---
id: 571
title: 'Testing Testing - where is my database?'
date: 2016-06-10T16:03:44+00:00
author: Richard Borges
layout: post
guid: https://richardborges.net/?p=571
permalink: /testing-testing-where-is-my-database/
categories:
  - Software
  - Uncategorized
---
Recently while creating a unit test (MSTest VS2015) to test my repository pattern, I hit a snag. Despite having defined the database in my app.config of the Test project, I could not locate my newly created database.

Turns out I needed to initialise my db in the test class , like so:

<pre class="wp-code-highlight prettyprint linenums:1">// Declare this property - this is set by MSTest
 public TestContext TestContext { get; set; }

 // In test initialization 
 [ClassInitialize]
 public static void SetUp(TestContext context)
 {
 AppDomain.CurrentDomain.SetData("DataDirectory", Path.Combine(context.TestDeploymentDir, string.Empty));
 }</pre>

Saw this useful tip at <a href="http://stackoverflow.com/questions/12450515/when-to-use-mdf-and-when-sdf" target="_blank">http://stackoverflow.com/questions/12450515/when-to-use-mdf-and-when-sdf</a>, which also talks about the differences between sdf (Server Explorer does not show table schema) and mdf (Server Explorer displays table schema).

Also came across this interesting <a href="http://www.mortenanderson.net/entity-framework-code-first-where-is-my-database" target="_blank">article</a> on locating your LocalDB.

&nbsp;