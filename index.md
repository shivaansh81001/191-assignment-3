# Price of iPhone 16 Globally

Welcome to our data analysis page. This project aims to provide insights into the global pricing of the iPhone 16 across various countries and regions. Below, you will find an analysis of pricing trends, currency conversion impacts, and other suspects 😉 of the price difference.

---

## Table of Contents
1. [Prerequisites](#Prerequisites)
2. [Introduction](#introduction)
3. [Key Features of the iPhone 16](#key-features-of-the-iphone-16)
4. [Global Pricing Overview](#global-pricing-overview)
5. [Analysis of Price Variations](#analysis-of-price-variations)
6. [Currency and Economic Impact](#currency-and-economic-impact)
7. [Conclusion](#conclusion)
8. [References](#references)

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

Then finally we did manage to get the final table which contained values for iphone in different countries represented in CAD $ for the ease of things.


---

## Analysis of Price Variations

Several factors contribute to the pricing differences of the iPhone 16 globally:
1. **Import Taxes and Duties**: Countries like India impose high tariffs on imported goods.
2. **Currency Exchange Rates**: Fluctuations in currency impact local pricing.
3. **Regional Tax Policies**: Sales tax or VAT rates significantly affect end-user pricing.

---

## Currency and Economic Impact

This section delves into the role of economic factors in shaping iPhone pricing:
- **Currency Strength**: Stronger currencies generally result in lower local pricing.
- **Market Strategies**: Apple’s pricing strategy often adjusts to align with local market conditions.
- **Economic Indicators**: Inflation and purchasing power influence affordability.

---

## Conclusion

The iPhone 16's global pricing reflects a complex interplay of taxes, currency exchange rates, and Apple's regional strategies. Understanding these variations is key for global customers and provides insights into broader economic trends.

---

## References

- Apple Official Website: [apple.com](https://www.apple.com)
- Currency Exchange Rates: [xe.com](https://www.xe.com)
- Regional Tax Information: Government tax portals of respective countries.
