# Collecting-Data-Using-Web-Scraping
Collecting Data Using Web Scraping
#this url contains the data you need to scrape
url = "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DA0321EN-SkillsNetwork/labs/datasets/Programming_Languages.html"
#import libraries
from bs4 import BeautifulSoup
import requests
# get the contents of the webpage in text format and store in a variable called data
data  = requests.get(url).text
data
soup = BeautifulSoup(data,"html.parser")  # create a soup object using the variable 'data'
for link in soup.find_all('a'):  # in html anchor/link is represented by the tag <a>
    print(link.get('href'))
    #find a html table in the web page
table = soup.find('table') # in html table is represented by the tag <table>
for row in table.find_all('tr'): # in html table row is represented by the tag <tr>
    # Get all columns in each row.
    cols = row.find_all('td') # in html a column is represented by the tag <td>
    Language_name = cols[1].getText() # store the value in column 3 as color_name
    annual_average_salary = cols[3].getText() # store the value in column 4 as color_code
    print("{}--->{}".format(Language_name,annual_average_salary))
