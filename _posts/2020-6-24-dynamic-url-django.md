---
layout: post
category: blog
title:  "Django - dynamically type url"
date:   2020-06-24
tags: web server-side django python
---

<pre><code>"adults": "1"
"childs":"0"
"infants":"0"
"res": "0"
"vehicle":"0"
outbound_route = '1040'
outbound_date = '19-02-2019'
inbound_route = '1042'
inbound_date = '20-02-2019'

url = "https://booking.snav.it/#/booking/rates"  # no trailing /
final_url = '/'.join([url, outbound_route, outbound_date, inbound_route, inbound_date])
res = requests.get(final_url, params=params)
</code></pre>

or you could use a formatted string literal:

<pre><code>url = "https://booking.snav.it/#/booking/rates/"
final_url = f'{url}{outbound_route}/{outbound_date}/{inbound_route}/{inbound_date}
</code></pre>

### output
<pre><code>https://booking.snav.it/#/booking/rates/1040/19-02-2019/1042/19-02-2019?adults=1&childs=0&infants=0&res=0&vehicle=0</code></pre>