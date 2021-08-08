# Mission to Mars

Building a web application that scrapes various websites for data related to the Mission to Mars and displays the information in a single HTML page. The following outlines what was done.

## Step 1 - Web Scraping

Initial scrape completed using Jupyter Notebook, BeautifulSoup, Pandas, and Requests/Splinter.

* Created a Jupyter Notebook file called `mission_to_mars.ipynb` , this file is used to complete all of scraping and analysis tasks. The following outlines what was scraped.

### NASA Mars News

* Scraped the [Mars News Site](https://redplanetscience.com/) to collect the latest News Title and Paragraph Text. Assigned the text to variables (news_title, new_p) that can be referenced later.

### JPL Mars Space Images - Featured Image

* Visited the url for the Featured Space Image site [here](https://spaceimages-mars.com).

* Used splinter to navigate the site and find the image url for the current Featured Mars Image and assigned the url string to a variable called `featured_image_url`.

### Mars Facts

* Visited the Mars Facts webpage [here](https://galaxyfacts-mars.com) and used Pandas to scrape the table containing facts about the planet including Diameter, Mass, etc.

* Used Pandas to convert the data to a HTML table string.

### Mars Hemispheres

* Visited the astrogeology site [here](https://marshemispheres.com/) to obtain high resolution images for each of Mar's hemispheres.

* Clicked each of the links to the hemispheres in order to find the image url to the full resolution image.

* Saved both the image url string for the full resolution hemisphere image, and the Hemisphere title containing the hemisphere name. Used a Python dictionary to store the data using the keys `img_url` and `title`.

* Appended the dictionary with the image url string and the hemisphere title to a list. This list contains one dictionary for each hemisphere.

- - -

## Step 2 - MongoDB and Flask Application

Used MongoDB with Flask templating to create a new HTML page that displays all of the information that was scraped from the URLs above.

* Started by converting Jupyter notebook into a Python script called `scrape_mars.py` with a function called `scrape` that executes all scraping code from above and returns one Python dictionary containing all of the scraped data.

* Next, created a route called `/scrape` that will import `scrape_mars.py` script and call `scrape` function.

  * Stored the return value in Mongo as a Python dictionary.

* Created a root route `/` that will query Mongo database and pass the mars data into an HTML template to display the data.

* Created a template HTML file called `index.html` that will take the mars data dictionary and display all of the data in the appropriate HTML elements. 

