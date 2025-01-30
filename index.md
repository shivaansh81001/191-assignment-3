This project aims to provide insights into the global pricing of the iPhone 16 across various countries and regions. Below, you will find an analysis of pricing trends, currency conversion impacts, and other suspects 😉 of the price difference.

---

## Table of Contents
1. [Prerequisites](#Prerequisites)
2. [Introduction](#introduction)
3. [Key Features of the iPhone 16](#key-features-of-the-iphone-16)
4. [Global Pricing Overview](#Global-Pricing-Overview)
5. [SO WHAT IS CAUSING THIS HUGE PRICE DIFFERENCE? IS IT INFLATION?](#SO-WHAT-IS-CAUSING-THIS-HUGE-PRICE-DIFFERENCE?-IS-IT-INFLATION?)
6. [Actual Reason](#Actual-Reason)
7. [Conclusion](#conclusion)


---
## Prerequisites
Firstly, we need to import a few python libraries which will help us to analyse and scrape the data. These will also enable us to clean, organize, and maniplulate the data according to our needs.<br>
These libraries are-<br>
- ***Datascience library*** - for creating the tables and performing related functions
- ***requests*** - to send and fetch requests from the browser 
- ***json*** - to convert the fetched requests to readable dictionary formats 
- ***numpy,pandas,matplotlib*** - to manipulate, clean and visualize the data    
- ***BeautifulSoup*** - to scrape the web
  

## Introduction

The iPhone 16, the latest in Apple's flagship smartphone lineup, is one of the most anticipated devices of the year. This page explores how pricing differs across countries and regions, factoring in aspects like:

---

## Key Features of the iPhone 16

Here are some of the standout features of the iPhone 16:
- **Next-gen A-series chip** for faster performance.
- **Advanced camera system** with improved low-light capabilities.
- **Longer battery life** and enhanced power efficiency.
- **New design and build materials** for improved durability.
- **5G enhancements** for better connectivity.

---

## Global Pricing Overview
We used the BeautifulSoup library and scraped the browser to find out the current global prices of the latest model of iphone and this is what we found -<br>
<br>
![image](https://github.com/user-attachments/assets/d4219f7d-fd96-4d54-92bf-d458fd4a7b02)
<br>
As we can see from the table, the prices scraped from the web, might not always clean so we had to implemet some functions to clean the data, and after a lot of cleaning and brushing and wiping, we were able to obtain a table which was in local currencies 🤦‍♂️<br>
<br>
![image](https://github.com/user-attachments/assets/bbb8cf3c-1de1-4509-955c-949b36a4a99f)

### So how do we standardize these local currencies?
<br>
Thats when APIs help us!
<br>
We used currency exchange APIs to obtain the conversion rates with CAD $ as the base currencey,<br>
![image](https://github.com/user-attachments/assets/9dc49d28-4a1b-45ad-ba4b-eaf3c94db558)

so all the prices we see now one will be in CAD$ , RIGHT??? NO , not so easily <br>

<br>
Turns out, the table we scraped for the prices, does not tell the currency codes but only the country. <br>
So we scraped an additional table from wikipedia, which contained the code, for the country and corresponding name <br>

![image](https://github.com/user-attachments/assets/a9c77ab3-48d2-41ac-b08a-ad3bf0d0c334)

Now, we just need to join the tables of echange rates and country codes to get the resulting <br>

![image](https://github.com/user-attachments/assets/5e928260-1335-4265-879d-dd0dd6b812b2)

Then finally we did manage to get the final table which contained values for iphone in different countries represented in CAD $ for the ease of things.<br>

![image](https://github.com/user-attachments/assets/f08171d5-5128-4675-aa91-d964c46b31b6)

And here are the results that we found from the analysis:<br>
Country with **most expensive** iphone 16 is **India** with price **$CAD 1325.51** <br>
Country with **least expensive** iphone 16 is **United States** with price **$CAD 1122.97**



---

## SO WHAT IS CAUSING THIS HUGE PRICE DIFFERENCE? IS IT INFLATION?

We decided to inspect our first suspect which was inflation. Inflain must be high in the countries where iphone is so expensive right? So for the ease of things , we decided to inspect countries with most expensive iphone and least expensive iphone and we started comparing the inflation rates of India and USA by scraping the web one more time.  <br>

**Then we use linear regression to calculate the line of best fit to caluculate the inflation rates of both the countries in Year 2030

Firstly, US <br>

![image](https://github.com/user-attachments/assets/3911b234-1d76-44e1-8799-cacfc9d7d9ea)

![image](https://github.com/user-attachments/assets/544775a8-9ad8-4851-b6a4-d34e6cb687de)
We can see from the line , the inflation in US is on a rise and by Year 2030 will reach approximately **~ 4.90%** <br>
<br>
Secondly, India <br>
![image](https://github.com/user-attachments/assets/79e930d2-ddd7-40ea-98ef-0622607aca49)

![image](https://github.com/user-attachments/assets/0b8db2d5-5dc4-416a-a1ea-a00b6ca7d31c)

We can see from the result, the inflation in India is on the decline by year 2030 and is approximated as **~2.09%** <br>

### But this doesn't make any sense ?!

If inflation was the sole reason iPhones would have been more expensive in US than India, but thats not the case.

---

## Actual Reason

To analyze that if there is any other factore involved, we calculate PPP (Purchase Power Parity) which compares the price of item to as whether the currency is overvalued or undervalued relative to one another.
If the currency does end up to be undervalued, we shall know that there are other factors involved. <br>

First, we analyze how much of a markup % has been placed on iPhone in each country, after that we calcuate the PPP dividing the local currency with canadian price. 

PPP= (Price in country * exchange rate)/canadian price

![image](https://github.com/user-attachments/assets/c377ad48-133a-4822-933b-78e13224ed97)

Now, we compare the PPP to the exchange rate, <br>
The indian rupee (~60 / CAD) << PPP (70/ CAD$) <br>
vs <br>
The USD (0.72 $/ CAD) ~= PPP(0.711 $/ CAD)<br>

That tells us that there are factors involved other than just the exchange rate. The indian rupee is extremely undervalued as shown in the figure below

![image](https://github.com/user-attachments/assets/dc74bba9-74e4-4ca3-b812-dd023b0d3d83)

---

## Conclusion 

Based on further investigation, we can assume there are other factors affecting iphone price in different countries.

For example, just take price in India as reference, the main factor leads to pricer is the high import taxes."Consequently, Apple is subject to customs duties, which have a direct impact on the final prices. Additionally, the Goods and Services Tax (GST) of *18% *further contributes to the cost, resulting in a cumulative increase of *40% *in the final price."

Attribution notice "https://economictimes.indiatimes.com/news/how-to/why-iphones-are-still-pricier-in-india-despite-made-in-india-production/articleshow/103682053.cms?from=mdr" By THE ECONOMIC TIMES NEWS

Despite the fact that since 2016, Apple has been manufaturing products in India, iphones are not entirely made in India but only assembled in India. Because of the supply chain, all the components required for iphone production are not manufactured in the same country, which potentially lead to the pricy cost.

In addtion, older-generation models drive the majority of sales for Apple in India, as the "Pro" models help it improve the affordability of base models and old_generation models. These iphones will become a better buy in India then other countries.

Attribution notice "https://timesofindia.indiatimes.com/gadgets-news/why-made-in-india-iphones-do-not-lead-to-a-price-cut/articleshow/103676724.cms" By THE TIMES OF INDIA

In conclusion, we can suggest three factors are affecting iphone's price in different countries. 1 import duties, 2 cost, 3 the sales of older-generation models differences


---

This section delves into the role of economic factors in shaping iPhone pricing:
- **Currency Strength**: Stronger currencies generally result in lower local pricing.
- **Market Strategies**: Apple’s pricing strategy often adjusts to align with local market conditions.
- **Transpotation Factors**: Apple's products are not directly manufactured in most countries like India

---


