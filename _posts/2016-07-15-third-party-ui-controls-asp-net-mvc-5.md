---
id: 711
title: 'Third party UI controls - ASP.Net MVC 5'
date: 2016-07-15T16:14:05+00:00
author: Richard Borges
layout: post
guid: https://richardborges.net/?p=711
permalink: /third-party-ui-controls-asp-net-mvc-5/
categories:
  - Software
---
The wonderful people at Syncfusion have offered a community license for free which gives you over 650+ controls. Head over [here](https://www.syncfusion.com/products/communitylicense).

After a bit of fiddling using their [online documentation](http://help.syncfusion.com/aspnetmvc/chart/getting-started), I&#8217;ve finally been able to use the chart control in my ASP.Net MVC5 code.  The 3 main dlls , I needed of the chart control are (changes to the web.config):

<pre class="wp-code-highlight prettyprint linenums:1">&lt;assemblies&gt;
      &lt;add assembly="Syncfusion.EJ, Version=14.2460.0.26, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" /&gt;
      &lt;add assembly="Syncfusion.Linq.Base, Version=14.2460.0.26, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" /&gt;
      &lt;add assembly="Syncfusion.EJ.Mvc, Version=14.2500.0.26, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" /&gt;
&lt;/assemblies&gt;
</pre>

To get around a Visual Studio build error, I had to add the following to the web.config

<pre class="wp-code-highlight prettyprint linenums:1">&lt;dependentAssembly&gt;
     &lt;assemblyIdentity name="Syncfusion.EJ" culture="neutral" publicKeyToken="3d67ed1f87d44c89" /&gt;
     &lt;bindingRedirect oldVersion="0.0.0.0-14.2460.0.26" newVersion="14.2460.0.26" /&gt;
&lt;/dependentAssembly&gt;
&lt;dependentAssembly&gt;
    &lt;assemblyIdentity name="Syncfusion.Linq.Base" culture="neutral" publicKeyToken="3d67ed1f87d44c89" /&gt;
    &lt;bindingRedirect oldVersion="0.0.0.0-14.2460.0.26" newVersion="14.2460.0.26" /&gt;
&lt;/dependentAssembly&gt;
</pre>

And lastly one javascript library, ej.widgets.all.min (8,466 kb), which after using their tool [csg](http://csg.syncfusion.com/), � (for the chart control only) reduced it to (ej.chart.min.js) 909kb.

In _layout.cshtml, added:

<pre class="wp-code-highlight prettyprint linenums:1">&lt;script src="~/Scripts/ej/ej.chart.min.js"&gt;&lt;/script&gt;    
@RenderSection("scripts", required: false)    
@Html.EJ().ScriptManager()
</pre>

and in viewname.cshtml, added

<pre class="wp-code-highlight prettyprint linenums:1">@(Html.EJ().Chart("presentationReport"))
</pre>

<!--more-->

Quite happy with the end-result.
  
<img class="alignnone size-medium wp-image-751" src="https://richardborges.net/wp-content/uploads/2016/07/SampleChart-300x156.png" alt="SampleChart" width="300" height="156" srcset="https://richardborges.net/wp-content/uploads/2016/07/SampleChart-300x156.png 300w, https://richardborges.net/wp-content/uploads/2016/07/SampleChart.png 338w" sizes="(max-width: 300px) 100vw, 300px" />