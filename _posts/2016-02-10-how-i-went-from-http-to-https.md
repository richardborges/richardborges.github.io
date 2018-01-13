---
id: 101
title: How I went from http to https
date: 2016-02-10T05:37:09+00:00
author: Richard Borges
layout: post
guid: http://richardborgesblog.azurewebsites.net/?p=101
permalink: /how-i-went-from-http-to-https/
categories:
  - Software
tags:
  - https ssl startssl.com troy hunt
---
Today I went from http to https.

Today I went from here (http): <a href="/assets/images/posts/2016/02/http.richardborges.net_.png" rel="attachment wp-att-131"><img class="wp-image-131 size-medium aligncenter" src="/assets/images/posts//2016/02/http.richardborges.net_-300x220.png" alt="no cert" width="300" height="220" srcset="/assets/images/posts/2016/02/http.richardborges.net_-300x220.png 300w, /assets/images/posts/2016/02/http.richardborges.net_.png 617w" sizes="(max-width: 300px) 100vw, 300px" /></a> to (https:) :

<a href="http://richardborgesblog.azurewebsites.net/wp-content/uploads/2016/02/https.richardborges.net_.png" rel="attachment wp-att-141"><img class="size-medium wp-image-141 aligncenter" src="/assets/images/posts//2016/02/https.richardborges.net_-300x223.png" alt="https" width="300" height="223" srcset="/assets/images/posts/2016/02/https.richardborges.net_-300x223.png 300w, /assets/images/posts/2016/02/https.richardborges.net_.png 616w" sizes="(max-width: 300px) 100vw, 300px" /></a>

&nbsp;

Thanks to Troy Hunt in providing the <a href="http://www.troyhunt.com/2013/09/the-complete-guide-to-loading-free-ssl.html" target="_blank">instructions</a>. That post was written in Sep 2013. I had to conduct a few trial and errors to get https working for my site.

### Background:

My blog ( richardborges.net ) is hosted on Azure site (richardborgesblog.azurewebsites.net). I have pointed richardborgesblog.azurewebsites.net to richardborges.net. Visit the excellent PluralSight course by Troy Hunt on how to do this.

<p style="text-align: justify;">
  I have used startssl.com to obtain the certificate for richardborges.net. I used the free option. Firstly create a login. Startssl.com will ask you to verify yourself by emailing you a verification code. Use the verification code to generate a client certificate for your browser and import into your browser. ( In google chrome , I used the import certificates option in advanced settings). Once that is done revisit startssl.com and click on authenticate.
</p>

<a href="http://richardborgesblog.azurewebsites.net/wp-content/uploads/2016/02/StartSSL.Authenticate.png" rel="attachment wp-att-181"><img class="alignnone size-medium wp-image-181" src="/assets/images/posts//2016/02/StartSSL.Authenticate-300x146.png" alt="StartSSL.Authenticate" width="300" height="146" srcset="/assets/images/posts/2016/02/StartSSL.Authenticate-300x146.png 300w, /assets/images/posts/2016/02/StartSSL.Authenticate.png 600w" sizes="(max-width: 300px) 100vw, 300px" /></a>

To create a new certificate, I used the certification wizard:

<a href="http://richardborgesblog.azurewebsites.net/wp-content/uploads/2016/02/SSLCertificateWizad.png" rel="attachment wp-att-201"><img class="alignnone size-medium wp-image-201" src="/assets/images/posts//2016/02/SSLCertificateWizad-300x111.png" alt="SSLCertificateWizad" width="300" height="111" srcset="/assets/images/posts/2016/02/SSLCertificateWizad-300x111.png 300w, /assets/images/posts/2016/02/SSLCertificateWizad.png 600w" sizes="(max-width: 300px) 100vw, 300px" /></a>

Next, I validated the domain (a verification code was sent by startsll.com to my domain email address.)

<a href="http://richardborgesblog.azurewebsites.net/wp-content/uploads/2016/02/VerifyYourDomainName.png" rel="attachment wp-att-203"><img class="alignnone size-medium wp-image-203" src="/assets/images/posts/2016/02/VerifyYourDomainName-300x124.png" alt="VerifyYourDomainName" width="300" height="124" srcset="/assets/images/posts/2016/02/VerifyYourDomainName-300x124.png 300w, /assets/images/posts/2016/02/VerifyYourDomainName.png 600w" sizes="(max-width: 300px) 100vw, 300px" /></a>

I then used the PKI system to generate the private key. Saved that password :).<a href="http://richardborgesblog.azurewebsites.net/wp-content/uploads/2016/02/GeneratePKI.PrivateKey.png" rel="attachment wp-att-191"><img class="alignnone size-medium wp-image-191" src="/assets/images/posts/2016/02/GeneratePKI.PrivateKey-300x138.png" alt="GeneratePKI.PrivateKey" width="300" height="138" srcset="/assets/images/posts/2016/02/GeneratePKI.PrivateKey-300x138.png 300w, /assets/images/posts/2016/02/GeneratePKI.PrivateKey.png 485w" sizes="(max-width: 300px) 100vw, 300px" /></a>

The submit button then generated a private key. I downloaded Private Key as ssl.key.

Once that was done, I created the certificate, which was� issued immediately.

I download the zip (richardborges.net.zip) file which containted the certificate, the intermediate certificate and the root CA certificate. There is also an option to� retrieve the issued certificate at “Tool Box” – “Certificate List” .

Next I generated the  pfx (Microsoft Azure requires a pfx file)  file using the Tool Box. Used the same password as one for the Private Key. Pasted the contents of &#8220;ssl.key&#8221; in the private key text box� and the content of &#8220;2_richardborges.net.cert&#8221; in the certificate text box.

<a href="http://richardborgesblog.azurewebsites.net/wp-content/uploads/2016/02/GeneratePFX.png" rel="attachment wp-att-221"><img class="alignnone size-medium wp-image-221" src="/assets/images/posts/2016/02/GeneratePFX-300x146.png" alt="GeneratePFX" width="300" height="146" srcset="/assets/images/posts/2016/02/GeneratePFX-300x146.png 300w, /assets/images/posts/2016/02/GeneratePFX.png 600w" sizes="(max-width: 300px) 100vw, 300px" /></a>

This generated the PFX file, which I downloaded and the used in Microsoft Azure portal, under custom domains and ssl.

That&#8217;s it. The certificate is valid for one year. Thank you startSSL.com.

[Update] : Images were not being displayed in Google Chrome under https (and rightly so, however IE11 played along). Updated Settings in WordPress general settings :<figure id="attachment_291" style="width: 300px" class="wp-caption alignnone">

<img class="size-medium wp-image-291" src="/assets/images/posts/2016/02/httpsURL-300x166.png" alt="WP general settings" width="300" height="166" srcset="/assets/images/posts/2016/02/httpsURL-300x166.png 300w, /assets/images/posts/2016/02/httpsURL.png 593w" sizes="(max-width: 300px) 100vw, 300px" />