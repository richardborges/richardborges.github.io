---
id: 1039
title: Using VS Code for editing and publishing
date: 2019-05-27T05:25:38+00:00
author: Richard Borges
layout: post
guid: https://richardborges.net/?p=1039
permalink: /using-vs-code-for-editing-and-publishing/
categories:
  - Software    
tags: vscode

---

For a while, I have been using the Windows bash shell to run the blog locally while I edit and then used the bash shell to commit my changes to Github. I've now started using VS Code to edit and deploy my blog, all from VS Code. How do I do this?
1. Launch VS Code ( Visual Studio Code) and open up the folder of the blog e.g. D:\RichardBorges.github.io
1. In the terminal window ( in VSCode ) ensure that you have a wsl terminal ( Windows Subsystem for Linux). I'm running Windows 10, i.e. a Windows bash shell. Read more [here] (https://code.visualstudio.com/docs/editor/integrated-terminal)
1. Type 
```bash
bundle exec jekyll serve
```
in the terminal window and this will build and launch the site locally at http://127.0.0.1:4000.
![screenshot](/assets/images/posts/2019/05/vscodeeditor.png)
1. Once you have finished editing, its time to use the 'Source control' tools to add (stage the changes) and commit to git hub. All within VS Code. 
![Add to GitHub](/assets/images/posts/2019/05/vscodegithub.png)
1. Commit and push to GitHub. This generates the latest blog post at [GitHub](https://richardborges.github.io)  