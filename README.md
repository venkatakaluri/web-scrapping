# web-scrapping
!pip install beautifulsoup4 requests google-cloud-storage google-cloud-bigquery

import requests
from bs4 import BeautifulSoup

url = 'https://example.com/data'  # Replace with your target URL
response = requests.get(url)
soup = BeautifulSoup(response.content, 'html.parser')

data = []
table = soup.find('table')  # Assuming data is in a table
for row in table.find_all('tr')[1:]:
    cols = row.find_all('td')
    data.append([col.text.strip() for col in cols])

print(data)
