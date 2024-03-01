Certainly! BeautifulSoup is a Python library for pulling data out of HTML and XML files. Below is a cheat sheet for some common tasks using BeautifulSoup.

### Installation:

```bash
pip install beautifulsoup4
```

### Importing BeautifulSoup:

```python
from bs4 import BeautifulSoup
```

### Parsing HTML:

```python
# Parse HTML content from a string
soup = BeautifulSoup(html_content, 'html.parser')

# Parse HTML content from a file
with open('example.html', 'r') as file:
    soup = BeautifulSoup(file, 'html.parser')
```

### Navigating the HTML tree:

```python
# Accessing tags
title_tag = soup.title
div_tag = soup.div

# Accessing tag contents
title_text = soup.title.text
div_text = soup.div.text

# Finding all occurrences of a tag
all_paragraphs = soup.find_all('p')
```

### Searching for tags:

```python
# Finding the first occurrence of a tag
first_paragraph = soup.find('p')

# Finding all occurrences of a tag with a specific class
paragraphs_with_class = soup.find_all('p', class_='my_class')

# Finding all occurrences of a tag with a specific attribute
tags_with_attribute = soup.find_all('div', attrs={'data-id': '123'})
```

### Accessing tag attributes:

```python
# Accessing attribute value
image_src = soup.img['src']

# Accessing all attributes of a tag
all_attributes = soup.a.attrs
```

### Extracting text:

```python
# Extracting text from a tag
paragraph_text = soup.p.text

# Stripping extra whitespaces
clean_text = paragraph_text.strip()
```

### Modifying the HTML:

```python
# Modifying tag contents
soup.p.string = 'New text'

# Adding a new tag
new_div = soup.new_tag('div')
new_div.string = 'New content'
soup.body.append(new_div)

# Removing a tag
tag_to_remove = soup.find('div', class_='remove_me')
tag_to_remove.decompose()
```

### Handling HTML entities:

```python
# Converting HTML entities to Unicode
decoded_text = BeautifulSoup("&lt;p&gt;This is a &quot;quote&quot;&lt;/p&gt;", 'html.parser').text
```

[BeautifulSoup Documentation](https://www.crummy.com/software/BeautifulSoup/bs4/doc/).
