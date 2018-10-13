---
id: 1032
title: Moving from Wordpress to github pages
date: 2018-01-07T17:55:38+00:00
author: Richard Borges
layout: post
guid: https://richardborges.net/?p=1032
permalink: /moving-from-wordpress-to-github-pages/
categories:
  - Software
  - Uncategorized
tags:
  
---
[updated] 13 Oct 2018

I was finally prodded into action when my wordpress blog site certificate expired. 

Using a few excellent resources available on the interwebs, I was able to run (generate in jekyll) the site locally on a Windows 10 machine and then push it to github (richardborges.github.io), which hosts for free ! 

### Running the site locally. 
The main steps where
0. Make sure you have [ Bash on Ubuntu on Windows](https://docs.microsoft.com/en-us/windows/wsl/install-win10) and have visited [jekyll on Windows](https://jekyllrb.com/docs/windows/)
1. Install jekyll on Windows 10 bash ( Bash on Ubuntu on Windows ) using instructions at https://jekyllrb.com/docs/windows/
2. I used my d drive to create a directory for my blog site (appears in mnt in bash)
3. I liked the [Cayman theme](https://pages-themes.github.io/cayman/) so downloaded it from github 
4. How to run locally ?
    1. Open a bash shell window  ( not git bash, the desktop app, but bash, the command). You can now mount the drive where your blog is saved (locally)
    ``` 
    cd /mnt/d/RichardBorges.github.io 
    ```  
    ==> i.e. my local directory on d drive where the cayman theme has been unzipped
    3. ``` bundle exec jekyll serve ```, this starts up the website locally
    4. browse to  http://127.0.0.1:4000 
    5. add new posts
    6. rinse and repeat

### Running the site at richarborges.github.io
1. Commit your local changes to your local github repository. As the site is generated locally by jekyll, I only commit the fully built site to github. The fully build website is found at _site/
2. In bash shell
  ```
  cd _site/ 
  git add . 
  git commit -m "This is the initial commit of my blog"
  git remote add origin https://github.com/richardborges/richardborges.github.io.git
  git push -u origin master
  ```
3. If the remote repository ( at github ) has not been setup, check using
```
  git remote -v
  git config --global user.name "richardborges"
  git config --global user.email "richardborges@company.com"  
  git remote -v
```
4. push your changes to remote
```
  git push -u origin master
```
You should now be able to see your site at richardborges.github.io

### Pointing richardborges.net to richardborges.github.io
1. Firstly I added https://github.com/richardborges/richardborges.github.io.git . Go to settings >> custom domain  
![custom domain](/assets/images/posts/2018/01/customdomain.https.png)
This creates a CNAME file in the remote repository ( remember to pull it to local later on)

2. We need to find the IP address of the remote, so use dig in bash shell
```
dig richardborges.github.io
```
![dig in bash shell](/assets/images/posts/2018/01/digrichardborges.github.io.PNG)
3. Now we need to update our DNS record ( at the the DNS hoster to point to the github.io IP address)
![DNS maintenance](/assets/images/posts/2018/01/arecords.png)
Also see [Setting up an apex domain](https://help.github.com/articles/setting-up-an-apex-domain/)
4. Now I can use richardborges.net to visit my blog. Yay.


### These websites proved invaluable... 

[Build A Blog With Jekyll And GitHub Pages](https://www.smashingmagazine.com/2014/08/build-blog-jekyll-github-pages/)

[Setting up a Jekyll blog using Windows 10 Bash and hosting on GitHub Pages • Keerat Singh • Aug 5, 2016](http://keerats.com/blog/2016/setup-jekyll-blog-windows-10-bash-host-github-pages/)

[Jekyll on Windows](https://jekyllrb.com/docs/windows/)

[How to install Jekyll on Windows 10 with “Windows subsystem for Linux”](https://davidburela.wordpress.com/2017/05/17/how-to-install-jekyll-on-windows-10-with-windows-subsystem-for-linux/)

[Developers can run Bash Shell and user-mode Ubuntu Linux binaries on Windows 10 ](https://www.hanselman.com/blog/DevelopersCanRunBashShellAndUsermodeUbuntuLinuxBinariesOnWindows10.aspx)

[Windows Subsystem for Linux out of Beta!](https://blogs.msdn.microsoft.com/commandline/2017/07/28/windows-subsystem-for-linux-out-of-beta/)

[Transform your plain text into static websites and blogs.](https://jekyllrb.com/)

[Using Jekyll as a static site generator with GitHub Pages](https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/)

[How-to: Migrating Blog from WordPress to Jekyll, and Host on Github](https://girliemac.com/blog/2013/12/27/wordpress-to-jekyll/)


{% comment %}
Might you have an include in your theme? Why not try it here!
{% include my-themes-great-include.html %}
{% endcomment %}

