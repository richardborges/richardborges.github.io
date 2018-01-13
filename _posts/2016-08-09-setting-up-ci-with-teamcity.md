---
id: 931
title: Setting up CI with TeamCity
date: 2016-08-09T22:37:51+00:00
author: Richard Borges
layout: post
guid: https://richardborges.net/?p=931
permalink: /setting-up-ci-with-teamcity/
categories:
  - Software
---
I have used an Azure Virtual Machine (Win 2008 Server, standard DS1 1core-3.5GB memory) for this.
  
Download JetBrains TeamCity on the server. I planned to install both the server and the build agent on the one box. This will do for now. I will look at moving the build agent to another server if there is demand. Accepted the default settings during installation.

I wanted to connect to bitbucket to retrieve the latest source using SSH. I added a new user (called BuildUser) to Bitbucket and added an SSH public key (bit bucket has good documentation on creating SSH keys. I used my bash shell to create these for the BuildUser user). One gotcha was that the Username had to be 'git'.

<img class="alignnone size-medium wp-image-973" src="/assets/images/posts/2016/08/VCSroot-300x226.png" alt="VCSroot" width="300" height="226" srcset="/assets/images/posts/2016/08/VCSroot-300x226.png 300w, /assets/images/posts/2016/08/VCSroot.png 829w" sizes="(max-width: 300px) 100vw, 300px" />

I created the build steps:
  
1. Installing nuget packages
  
2. Build the VS2015 solution

<img class="alignnone size-medium wp-image-1001" src="/assets/images/posts/2016/08/TeamCityMSBuild-300x115.png" alt="TeamCityMSBuild" width="300" height="115" srcset="/assets/images/posts/2016/08/TeamCityMSBuild-300x115.png 300w, /assets/images/posts/2016/08/TeamCityMSBuild.png 804w" sizes="(max-width: 300px) 100vw, 300px" />

To use the MSBuild, I had to download and install [Build tools](https://www.microsoft.com/en-us/download/details.aspx?id=48159) and [install agents](https://www.microsoft.com/en-us/download/details.aspx?id=48152) for Visual Studio 2015.

These [videos](https://www.youtube.com/watch?v=gQAuHWgSJ_o - build Zen Digital) by Zen Digital proved useful.