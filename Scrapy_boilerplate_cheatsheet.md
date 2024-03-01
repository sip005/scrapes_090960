Scrapy, a powerful web scraping framework for Python.

### Installation:

```bash
pip install scrapy
```

### Create a new Scrapy project:

```bash
scrapy startproject project_name
```

### Spiders:

```python
# Create a new spider
scrapy genspider spider_name example.com

# Example of a basic spider
import scrapy

class MySpider(scrapy.Spider):
    name = 'my_spider'
    start_urls = ['http://example.com']

    def parse(self, response):
        # Extract data using XPath or CSS selectors
        title = response.css('title::text').get()
        yield {'title': title}

        # Follow links
        next_page = response.css('a.next_page::attr(href)').get()
        if next_page:
            yield scrapy.Request(url=next_page, callback=self.parse)
```

### Selectors:

```python
# Using XPath
title = response.xpath('//h1/text()').get()

# Using CSS selectors
paragraph = response.css('p::text').get()
```

### Item Pipeline:

```python
# Define an item in items.py
import scrapy

class MyItem(scrapy.Item):
    title = scrapy.Field()
    description = scrapy.Field()

# Process items in pipelines.py
class MyPipeline:
    def process_item(self, item, spider):
        # Process and store the item
        return item

# Enable the pipeline in settings.py
ITEM_PIPELINES = {
    'myproject.pipelines.MyPipeline': 300,
}
```

### Middlewares:

```python
# Example of a middleware to change User-Agent
from scrapy.downloadermiddlewares.useragent import UserAgentMiddleware

class MyUserAgentMiddleware(UserAgentMiddleware):
    def process_request(self, request, spider):
        request.headers['User-Agent'] = 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.3'

# Enable the middleware in settings.py
DOWNLOADER_MIDDLEWARES = {
    'myproject.middlewares.MyUserAgentMiddleware': 543,
}
```

### Settings:

```python
# Set user-agent and other settings in settings.py
USER_AGENT = 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.3'
ROBOTSTXT_OBEY = False  # To ignore robots.txt rules during scraping
```

### Running the Spider:

```bash
# Run the spider
scrapy crawl spider_name

# Save output to a file
scrapy crawl spider_name -o output.json
```

[Scrapy Documentation](https://docs.scrapy.org/).
