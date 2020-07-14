---
layout: post
category: blog
title:  "Python - Web Scraping with Selenium"
date:   2020-07-03
tags: python web_scraping
image: ""
---

<pre><code>final_url = f'{url}{name}001&termArray=f_20_2310/'
driver = webdriver.Chrome()
driver.get(final_url)
response = driver.execute_script("return document.documentElement.outerHTML")
driver.quit()
soup = BeautifulSoup(response, "lxml")
panel = soup.find('div', attrs={'id':'classScheduleBody'})
</code></pre>

### how to web scrape without opening the browser
<pre><code>from selenium.webdriver.chrome.options import Options

options = Options()
options.add_argument('--headless')</code></pre>