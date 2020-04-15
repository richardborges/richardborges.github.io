---
id: 1043
title: Underlying provider failed on open
date: 2020-04-15T05:25:38+00:00
author: Richard Borges
layout: post
guid: https://richardborges.net/?p=1043
permalink: /underlying-provider-failed-on-open/
categories:
  - Software
tags: Error

---
I was working on a Web App which uses a SQL database and EntityFramework. The app is hosted in Azure.
I spent some time fixing up the csproj file so that the build and release pipelines work correctly i.e. once the code is committed to the repository, a build is kicked off and deployment takes place.

So far so good. However on visiting the site I see this error:
> Error        : The underlying provider failed on Open.
> Stack Trace    : at System.Data.Entity.Core.EntityClient.EntityConnection.Open()
>   at System.Data.Entity.Core.Objects.ObjectContext.EnsureConnection(Boolean shouldMonitorTransactions)

Hmmm. The code runs perfectly locally, where is this error coming from?  I updated the web.config and eventually added the connection strings to Azure App Service > Configuration
![Connection string in Azure App Service](/assets/images/posts/2020/04/appserviceconnectionstring.png)

No luck.

Then I found the Azure App Service > Diagnose and solve problems > Diagnostic Tools > Profiler 
![Diagnose and solve problems](/assets/images/posts/2020/04/appservicediagnostictools.png)

Then selected the "Check Connection String", et voila the error is seen in a web.config under the Views. That saved the day for me. There are a few other tools on that page which I will investigate down the track. For now this was a good find !
