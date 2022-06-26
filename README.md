### Module 10 Challenge: Mission-to-Mars

## Background: 

Adjust the current web app to include all four of the hemisphere images. To do this, use BeautifulSoup and Splinter to scrape full-resolution images of Mars’s hemispheres and the titles of those images, store the scraped data on a Mongo database, use a web application to display the data, and alter the design of the web app to accommodate these images.

# Deliverables

*1. Scrape Full-Resolution Mars Hemisphere Images and Titles*

![Full Res Images of Mars' Hemisphere](https://user-images.githubusercontent.com/102566199/175832244-0c73e864-4080-462e-b8d5-c25a4a02659b.png)

```
{
  # 2. Create a list to hold the images and titles.
hemisphere_image_urls = []
# 3. Write code to retrieve the image urls and titles for each hemisphere on the site.
links = browser.find_by_css('a.product-item img')

for i in range(len(links)):
    hemisphere = {}
    browser.find_by_css('a.product-item img')[i].click()
    sample_elem = browser.links.find_by_text('Sample').first
    hemisphere['img_url'] = sample_elem['href']
    hemisphere['title'] = browser.find_by_css('h2.title').text
    hemisphere_image_urls.append(hemisphere)
    browser.back() 
}

Code will retrieve full-resolution images and titles for each Hemisphere.

*2. Update the Web App with Mars’s Hemisphere Images and Titles*

![Each Hemisphere Image](https://user-images.githubusercontent.com/102566199/175832461-58582e1f-70ef-4933-8bfd-fe5ef1666148.png)


*3. Add Bootstrap 3 Components* 

![Styling and Customizing Title and Button](https://user-images.githubusercontent.com/102566199/175832502-0f215e34-0c32-4ebd-b363-a1ca52033237.png)

```
{
<div class="jumbotron text-center">
        <p><font color = "pink" face="WildWest"</p>
        <h1>Mission to Mars</h1>
        <!-- Add a button to activate scraping script -->
        <p><a class="btn btn-info btn-lg" href="/scrape" role="button"><strong>Scrape New Data</strong></a>
}
        



