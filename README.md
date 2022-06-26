### Module 10 Challenge: Mission-to-Mars

## Background: Robin's web app is looking good and functioning well, but she wants to add more polish to it. She had been admiring images of Mars’s hemispheres online and realized that the site is scraping-friendly. She would like to adjust the current web app to include all four of the hemisphere images. To do this, use BeautifulSoup and Splinter to scrape full-resolution images of Mars’s hemispheres and the titles of those images, store the scraped data on a Mongo database, use a web application to display the data, and alter the design of the web app to accommodate these images.

# Deliverables

*1. Scrape Full-Resolution Mars Hemisphere Images and Titles*

![Full Res Images of Mars' Hemisphere](https://user-images.githubusercontent.com/102566199/175832244-0c73e864-4080-462e-b8d5-c25a4a02659b.png)

```
{
  # 2. Create a list to hold the images and titles.
hemisphere_image_urls = []

# 3. Write code to retrieve the image urls and titles for each hemisphere on the site.

# create a list of all of the hemispheres
links = browser.find_by_css('a.product-item img')


# looping through the list of the links to click the link, find the sample anchor, return the href

#use len to let it look through the list of links
for i in range(len(links)):
    hemisphere = {}
    
    # find elements on each loop 
    browser.find_by_css('a.product-item img')[i].click()
    
    # find the Sample image to extract the href
    sample_elem = browser.links.find_by_text('Sample').first
    hemisphere['img_url'] = sample_elem['href']
    
    # Get the hemisphere title 
    hemisphere['title'] = browser.find_by_css('h2.title').text
    
    # add/append hemisphere title object to list created in step 2
    hemisphere_image_urls.append(hemisphere)
    
    # return to the starting page
    browser.back() 
}
