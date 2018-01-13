---
id: 311
title: Supplying credentials for an API call
date: 2016-03-18T15:22:20+00:00
author: Richard Borges
layout: post
guid: https://richardborges.net/?p=311
permalink: /supplying-credentials-for-an-api-call/
categories:
  - Software
---
For testing APIs, I use a tool called Postman. Its free and available on the Chrome <a href="https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop?hl=en" target="_blank">Webstore</a>. Install and launch the app. To test an api call which requires authentication, turn on the Interceptor in Postman

<img class="alignnone size-medium wp-image-351" src="/assets/images/posts/2016/03/Postman.Interceptor-300x98.png" alt="Postman.Interceptor" width="300" height="98" srcset="/assets/images/posts/2016/03/Postman.Interceptor-300x98.png 300w, /assets/images/posts/2016/03/Postman.Interceptor.png 563w" sizes="(max-width: 300px) 100vw, 300px" />

This will prompt for a plug in to be installed in chrome.

<img class="alignnone size-medium wp-image-341" src="/assets/images/posts/2016/03/Chrome.Interceptor-300x11.png" alt="Chrome.Interceptor" width="300" height="11" srcset="/assets/images/posts/2016/03/Chrome.Interceptor-300x11.png 300w, /assets/images/posts/2016/03/Chrome.Interceptor.png 575w" sizes="(max-width: 300px) 100vw, 300px" />

Once you to that, login to your application in chrome. The login credentials will be passed on to Postman and you can proceed with the API call testing.