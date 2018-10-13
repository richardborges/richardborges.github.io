---
id: 1035
title: Elasticsearch upgrade
date: 2018-10-12T12:25:38+00:00
author: Richard Borges
layout: post
guid: https://richardborges.net/?p=1035
permalink: /elasticsearch-upgrade/
categories:
  - Software  
  - Uncategorized
tags:
  
---

These are my notes on upgrading [elasticseach](https://elastic.co) from v5.3 to v6.4.2. This was done on Windows Server 2016 with 32GB RAM and 500GB hdd. The source data was about 300GB in size. 

### Steps
![elastic.co](/assets/images/posts/2018/10/elastic.co.png) 
1. Download elasticsearch + kibana from [downloads](https://www.elastic.co/downloads). After extracting to my local drive, I used [NSSM](https://nssm.cc/) to run these as windows services. You should now be able to visit http://localhost:9200 (elasticsearch) and http://localhost:5601 ( kibana )
2. Copy across the 5.3 data using robcopy. Install elasticsearch 5.3 ( update elasticsearch.yml ) to run 5.3 at http://localhost:8200 ( as 6.4.2 is running on port 9200)
3. Create the new indices on 6.4.2
4. Migrate the data from 5.3 to 6.4.2 using reindex


### Additional resources
1. Upgrade [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/6.4/setup-upgrade.html)


{% comment %}
Might you have an include in your theme? Why not try it here!
{% include my-themes-great-include.html %}
{% endcomment %}