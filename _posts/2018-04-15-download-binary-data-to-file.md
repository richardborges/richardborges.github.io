---
id: 1034
title: Download binary data to file
date: 2018-04-15T01:00:38
author: Richard Borges
layout: post
guid: https://richardborges.net/?p=1034
permalink: /download-binary-data-to-file/
categories:
  - Software  
tags:
  - Tools
---

I had some binary data in a table in SQL and wanted to save it locally. The data was emails (msg files). I could have done this using powershell and the Invoke-SqlCmd commandlet, but for whatever reason, invoke-sqlcmd refused to work on my machine. After spending a few hours trying to get that to work, I gave up and jumped on stackoverflow to find another solution. 

### Linqpad to the rescue 
I happened on this link [Script to save varbinary data to disk](https://stackoverflow.com/questions/4056050/script-to-save-varbinary-data-to-disk/40520791#40520791) which was just the solution I was looking for. Download [LinqPad 5](https://www.linqpad.net/Download.aspx) (the free version is fine) and then

```
/*
This LinqPad script saves data stored in a VARBINARY field to the specified folder.
1. Connect to SQL server and select the correct database in the connection dropdown (top right), the 'this' in the C# code
2. Change the Language to C# Program
3. Change "Attachments" to the name of your table that holds the VARBINARY data
4. Change "AttachmentBuffer" to the name of the field that holds the data
5. Change "Id" to the unique identifier field name
6. Change "1090" to the identity of the record you want to save
7. Change the path to where you want to save the file. Make sure you choose the right extension.
8. Think of 'ci' in the C# code as a placeholder

Notes: Windows 10 may give you "Access Denied" error when trying to save directly to C:\. Rather save to a subfolder. 
*/

void Main()
{
    var context = this;
    var query = 
        from ci in context.Attachments
        where ci.Id == 1090
        select ci.AttachmentBuffer
    ;
    byte[] result = query.Single().ToArray();
    File.WriteAllBytes(@"c:\DEV\dumpfile.xlsx", result);
    Console.WriteLine("Done");
}
```

Thanks to SO user [Altron Seige](https://stackoverflow.com/users/375114/atron-seige) for his valuable explanation. 



{% comment %}
Might you have an include in your theme? Why not try it here!
{% include my-themes-great-include.html %}
{% endcomment %}
