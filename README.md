import pandas as pd
import time
from selenium import webdriver
from bs4 import BeautifulSoup as bs
driver = webdriver.Chrome("E:\\jupyter\\chromedriver_win32\\chromedriver") 
driver.get("https://foursquare.com/explore?mode=url&ne=40.806793%2C-73.865376&q=Food&sw=40.668921%2C-74.094715")
# elems = driver.find_elements_by_xpath("//a[@href]")

# //*[@id="results"]/ul/li[2]/div
time.sleep(5)
#x = bs(driver.find_element_by_xpath('//*[@id="results"]/ul/li[2]/div/div[2]/div[1]/div/div[2]').get_attribute("innerHTTML"), "html.parser")
#html = driver.page_source()
#soup = bs(html, 'html.parser')
#title = soup.find('div',{'class':'venueName'})t
title = driver.find_elements_by_class_name('venueName') # Select all images with cars.....
#print(title.text)
title_list = []
for elem in title:
    elem_list = elem.text
    title_list.append(elem_list)
    
    
descp = driver.find_elements_by_class_name('tipText') # Select all images with cars.....
#print(title.text)
descp_list =[]
for item in descp:
    item_list = item.text
    descp_list.append(item_list)
    
address = driver.find_elements_by_class_name('venueAddress') # Select all images with cars.....
#print(title.text)
address_list =[]
for item1 in address:
    item1_list = item1.text
    address_list.append (item1.text)
    
  
#rank = driver.find_elements_by_class_name('venueScore positive') # Select all images with cars.....
#print(title.text)
rank = driver.find_elements_by_class_name('venueDetails') # Select all images with cars.....
#print(title.text)

print(rank)
for elem1 in rank:
    print (elem1.text)
    
  #for link in element:
   # href = link.find_element_by_css_selector('a').get_attribute('href')
    #print (href)
    
#print (elem)
  #  href = link.find_element_by_css_selector('a').get_attribute('href')
  #  for element in link:
   # print (href)


#continue_link = driver.find_element_by_tag_name('a')
#elem = driver.find_elements_by_xpath('//*[@id="results"]/ul/li[2]/div/div[2]/div[1]/div/div[2]/h2/a')
#x = str(continue_link)
#print(continue_link)
#print(elem)
elems = driver.find_elements_by_xpath("//a[@href]")
for elem in elems:
    print(elem.get_attribute("href"))

    
   # import pandas as pd

list1 = [1, 2, 3]
list2 = [4, 5, 6]
list3 = [7, 8, 9]

df = pd.DataFrame(list(zip(*[title_list, descp_list,address_list]))).add_prefix('Col')

df.to_csv('fileare.csv', index=False)

print(df)
