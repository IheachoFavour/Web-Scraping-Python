# Web-Scraping-Python
This project demonstrates the use of web scraping techniques to extract data from the Jumia e-commerce website, Mobile Phones Category. The goal is to gather relevant information and store it in a structured format for further analysis.

## Project Description
Beautiful Soup library was used to scrape the necessary data: 
- Product Name
- Color
- New Price
- Old Price
- Discount percentage
- Rating
- Store Name
- Shipping Type
- Where was the phone shipped from?
  
### The collected data is then stored in a **CSV file**, which can be used for various purposes, such as:
- Competitive price analysis
- Product trend monitoring
- Sentiment analysis based on customer reviews

## Technologies Used
- Python
- BeautifulSoup (for HTML parsing)
- Requests (for making HTTP requests)
- Pandas (for data manipulation and storage)
- Re library (Regular expression library for pattern matching)

## Code Snippet
**Importing Necessary librairies**
``` python
import pandas as pd
from bs4 import BeautifulSoup 
import requests
import re
```
**Getting Old and New Prices Columns**
```python
#Get the prices (new and old)
        price = article.find('div' , class_ = 'prc').text.strip()
        price_match = re.search(r'^\₦?\s*\d+(,\d{3})*', price)
        if price_match:
            price_text = price_match.group()
            price_text = price_text.replace('₦', '').strip()
            price = int(price_text.replace(',', ''))
        else:
            price = 'N/A'
            
        old_price_element = article.find('div', class_='old')
        if old_price_element:
            old_price = old_price_element.text.strip()
            old_price_match = re.search(r'^\₦?\s*\d+(,\d{3})*', old_price)
            if old_price_match:
                old_price_text = old_price_match.group()
                old_price_text = old_price_text.replace('₦', '').strip()
                old_price = int(old_price_text.replace(',', ''))
            else:
                old_price = 'N/A'
        else:
            old_price = 'N/A'
```
## Result
![image](https://github.com/IheachoFavour/Web-Scraping-Python/assets/125609035/d91fc798-5ff9-433e-afa4-f7fc90f2af32)

## Future Improvements
The current version of the project can be further enhanced with the following improvements:
- *Implement error handling and retry mechanisms to handle website changes or network issues.*
- *Add support for scraping multiple pages or categories of the website.*
- *Integrate the scraping process with a scheduling system to automate regular data collection.*
- *Explore the use of more advanced techniques, such as dynamic content scraping or headless browser automation.*
