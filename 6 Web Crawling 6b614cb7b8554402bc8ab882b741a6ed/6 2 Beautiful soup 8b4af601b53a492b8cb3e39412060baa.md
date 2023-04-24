# 6.2 Beautiful soup

start a python session just type in ‘python’

![截屏2023-04-23 00.02.03.png](6%202%20Beautiful%20soup%208b4af601b53a492b8cb3e39412060baa/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.02.03.png)

![截屏2023-04-23 00.03.46.png](6%202%20Beautiful%20soup%208b4af601b53a492b8cb3e39412060baa/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.03.46.png)

To find the parent or child element of a given element using Beautiful Soup, you can use the **`parent`** and **`find_all`** methods, respectively.

Here's an example of how to use Beautiful Soup to find the parent element of a given element:

```python
from bs4 import BeautifulSoup

html_doc = """
<html>
  <body>
    <div>
      <p>Some text</p>
    </div>
  </body>
</html>
"""

soup = BeautifulSoup(html_doc, 'html.parser')
p_tag = soup.find('p')

parent_div = p_tag.parent
print(parent_div)
```

In the above example, the **`p`** element is first found using the **`find`** method. The **`parent`** method is then used to find the parent **`div`** element of the **`p`** element. The result is printed to the console.

Here's an example of how to use Beautiful Soup to find the child elements of a given element:

```python
from bs4 import BeautifulSoup

html_doc = """
<html>
  <body>
    <div>
      <p>Some text</p>
      <ul>
        <li>Item 1</li>
        <li>Item 2</li>
      </ul>
    </div>
  </body>
</html>
"""

soup = BeautifulSoup(html_doc, 'html.parser')
div_tag = soup.find('div')

child_ul = div_tag.find_all('ul')
print(child_ul)
```

In the above example, the **`div`** element is first found using the **`find`** method. The **`find_all`** method is then used to find all **`ul`** elements that are children of the **`div`** element. The result is printed to the console.

In summary, to find the parent element of a given element using Beautiful Soup, you can use the **`parent`** method. To find the child elements of a given element, you can use the **`find_all`** method.

![截屏2023-04-23 00.04.04.png](6%202%20Beautiful%20soup%208b4af601b53a492b8cb3e39412060baa/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.04.04.png)

# Exercise:

Previously in this unit we have taught you how to construct webpages, including how to construct webpages so that they present structured information (e.g., the contents of a database). The presumption has generally been that you are designing webpages for (usually visual) consumption by a human using a standard web browser, or at most writing Javascript functions that will help a human use a webpage in particular way.在本单元之前，我们已经教过您如何构建网页，包括如何构建网页以使其呈现结构化信息（例如，数据库的内容）。通常的假设是，您正在为使用标准网络浏览器的人（通常是视觉）消费设计网页，或者至多编写 Javascript 函数来帮助人们以特定方式使用网页。

However, there are situations where you may need to write code that interacts with webpages in an automated fashion -- perhaps to extract some data from webpages that isn't available in a more machine-friendly format. This *scraping* of webpages is a valuable (if sometimes maliciously applied) skill that can be useful to many kinds of software engineers and data scientists. This exercise talks you through some applications of one of the most common frameworks, a Python library called BeautifulSoup.但是，在某些情况下，您可能需要编写以自动化方式与网页交互的代码——也许是为了从网页中提取一些数据，而这些数据无法以对机器更友好的格式提供。这种网页*抓取*是一种有价值的（如果有时被恶意应用的话）技能，对许多软件工程师和数据科学家都有用。本练习将带您了解最常见框架之一的一些应用程序，该框架是一个名为 BeautifulSoup 的 Python 库。

## Setup

First, you'll need to install `python3` and `py3-pip` if you didn't already install those packages as part of the Build Tools exercises in Part 1.

Next, you want to install the BeautifulSoup library, 

**which you can achieve with `sudo pip install bs4` (or just `pip install bs4` to use the user installation mode).**

You can test that python is working by just typing `python` at the command line -- it should launch the interactive interpreter, which will prompt you for Python code with `>>>`. 

**Type `from bs4 import BeautifulSoup`.** 

If this completes then you've successfully imported the library.

![当下面没有出现error message 那么就说明安装成功了, Remember to import the necessary libraries or classes each time you start a new Python session.每次有新的python session 的时候呢都需要**Type `from bs4 import BeautifulSoup`.** ](6%202%20Beautiful%20soup%208b4af601b53a492b8cb3e39412060baa/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_19.08.16.png)

当下面没有出现error message 那么就说明安装成功了, Remember to import the necessary libraries or classes each time you start a new Python session.每次有新的python session 的时候呢都需要**Type `from bs4 import BeautifulSoup`.** 

## Interacting with Soup

Next, enter something like the following:

```

file = "cattax/index.html"
soup = BeautifulSoup(open(file, 'r'))

```

*(You may need to change the 'file' line to reflect where the `cattax/index.html` file really is relative to where you launched `python`. Also, if you close the interpreter at any point remember you'll need to re-run the `import` line above to get the library).*

if so, then it means  you have successfully imported the BeautifulSoup class and created a BeautifulSoup object called **`soup`**

![截屏2023-04-20 19.35.33.png](6%202%20Beautiful%20soup%208b4af601b53a492b8cb3e39412060baa/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_19.35.33.png)

You now have a 'soup' object, which is a Python object that has various methods for interacting with HTML (and XML) documents and accessing their contents. To start with, just type `soup` in your interpreter. Python will print out the basic textual representation of the object, which is just the source of the `index.html` page. Next, let's attempt one of the commonest use-cases for scraping.

```

soup.get_text()

```

*After we imput the soup.get_text(), we can see that all the textual content of webpage has been copied:* 

![截屏2023-04-20 19.38.34.png](6%202%20Beautiful%20soup%208b4af601b53a492b8cb3e39412060baa/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_19.38.34.png)

You should see a string containing the textual content of the webpage. If you call `print` on the result, you should see that the text has been laid out in a fair approximation of how the visible text would appear on a webpage.

```

text = soup.get_text()
print(text)

```

![截屏2023-04-20 19.44.48.png](6%202%20Beautiful%20soup%208b4af601b53a492b8cb3e39412060baa/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_19.44.48.png)

Getting the visible text out of a page is a common requirement if, e.g., you were going to use the webpage as input to an NLP system. 

You can also access non-visible portions of the page -- `soup.title` will give you the title element of the webpage: 

*soup.title: can check the title of soup*

![截屏2023-04-20 19.46.20.png](6%202%20Beautiful%20soup%208b4af601b53a492b8cb3e39412060baa/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_19.46.20.png)

and `soup.title.text` will get you the textual content within the title element. 

*get the text of soup title:*

![截屏2023-04-20 19.47.11.png](6%202%20Beautiful%20soup%208b4af601b53a492b8cb3e39412060baa/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_19.47.11.png)

Note the difference: `soup.title` is a BeautifulSoup element (of type `Tag`), and has methods associated with being a tag; `soup.title.text` is just a string, and only has methods that apply to strings.

As HTML documents are structured, you can interact with them in a structured manner. `soup.head` will get you a soup object reflecting the 'head' part of the HTML structure, 

*get the soup object reflecting the ‘head’ part of HTML structure*

![截屏2023-04-20 19.48.21.png](6%202%20Beautiful%20soup%208b4af601b53a492b8cb3e39412060baa/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_19.48.21.png)

and `soup.head.findChildren()` will return a list containing all of the 'children' elements inside the head. 

 *a list containing all of the 'children' elements inside the head.* 

![截屏2023-04-20 19.48.46.png](6%202%20Beautiful%20soup%208b4af601b53a492b8cb3e39412060baa/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_19.48.46.png)

By knowing the structure of the document you can thus navigate to certain elements programmatically. This doesn't just relate to the tags, either: you can also access the value of attributes. `soup.head.meta['charset']` would access the `charset` attribute of the meta tag in the head of the document.

*access the `charset` attribute of the meta tag in the head of the document.*

![截屏2023-04-20 19.49.18.png](6%202%20Beautiful%20soup%208b4af601b53a492b8cb3e39412060baa/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_19.49.18.png)

# Exercises

### 1.Take a look at some other examples from [the BeautifulSoup documentation](https://beautiful-soup-4.readthedocs.io/en/latest/#navigating-the-tree), in particular regarding the use of the `.find_all()` method.

[Beautiful Soup Documentation — Beautiful Soup 4.4.0 documentation.pdf](6%202%20Beautiful%20soup%208b4af601b53a492b8cb3e39412060baa/Beautiful_Soup_Documentation__Beautiful_Soup_4.4.0_documentation.pdf)

The `find_all()`method scans the entire document looking for results, but sometimes you only want to find one result. If you know a document only has one <body> tag, it’s a waste of time to scan the entire document looking for more. Rather than passing in `limit=1` every time you call `find_all`, you can use the `find()` method. These two lines of code are nearly
 equivalent:

```css
soup.find_all('title', limit=1)
# [<title>The Dormouse's story</title>]

soup.find('title')
# <title>The Dormouse's story</title>
```

### 2. Use your interpreter to access a list of all the `<strong>` elements in the webpage, and figure out how to print out just the text contained within them.

```css
strong_elements = soup.find_all('strong')

for element in strong_elements:
    print(element.get_text())
```

![截屏2023-04-20 19.59.48.png](6%202%20Beautiful%20soup%208b4af601b53a492b8cb3e39412060baa/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_19.59.48.png)

1. How would you use `.find_all()` to find all `<div>` elements with a particular class value (e.g., 'container')? Would your method work if the div had multiple classes?

```python
# Find all <div> elements with the 'container' class
div_elements = soup.find_all('div', class_='container')

# Iterate through the elements and print each one
for div in div_elements:
    print(div)
    print()  # Print an empty line for better readability
```

*and we can get the output:*

![截屏2023-04-20 20.04.01.png](6%202%20Beautiful%20soup%208b4af601b53a492b8cb3e39412060baa/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_20.04.01.png)

This line uses a dictionary to specify the attribute and its value. In this case, it looks for a 'class' attribute with the exact value 'container'. If an element has multiple classes, this method will only find it if the 'container' class is the first class in the attribute.

```python
**div_elements = soup.find_all('div', {'class': 'container'})**
```

This line uses the **`class_`** parameter (note the underscore) to specify the class value. This method will find all **`<div>`** elements with the 'container' class, even if there are other classes present. The underscore is used to avoid conflicts with the reserved keyword **`class`** in Python.

the **`<div>`**has multiple classes, the method shown above will only work if the 'container' class is the first class in the class attribute. To find **`<div>`**lements that have the 'container' class regardless of its position among multiple classes, use the following code:

```python
**div_elements = soup.find_all('div', class_='container')**
```

## A Scraping Script

Download [this python script](https://cs-uob.github.io/COMSM0085/exercises/part2/resources/scrape.py) to the directory that contains your `cattax` folder (*not* into `cattax` itself). On the command line, you should be able to run this script with `python scrape.py`. You'll see that it prints out a series of lines related to all the files in `cattax`.

run the script with python [scrape.py](http://scrape.py) and you will get the message that 

![截屏2023-04-20 20.10.31.png](6%202%20Beautiful%20soup%208b4af601b53a492b8cb3e39412060baa/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_20.10.31.png)

Open `scrape.py` in an editor and inspect what it is doing. 

*this is how the code look like:*

```python
from bs4 import BeautifulSoup
import os

for file in os.listdir('cattax'):
  if file[-4:] == 'html':
    soup = BeautifulSoup(open('cattax/'+file,'r'), features='html.parser')
    print(soup.title.text + " : " + soup.h1.text)
```

The script imports two libraries, one is BeautifulSoup and the other is `os`, which allows the script to use certain operating system functions. 

`os.listdir` is then used to list the contents of our `cattax` directory and iterate over them. We filter the filenames by checking to see which of them end with the string 'html', and if they do then we open the file and parse it into a BeautifulSoup object. Then, we print out text from certain elements, separated by a ':'. Understand how this works, asking a TA or lecturer for help if you aren't sure.

# Exercises

### 1. Modify `scrape.py` so that it *also* prints out the contents of the 'info' paragrah in each page (this can be a second print statement). Run the script again to test that it works.

```python
# Exercise 1 for prints out the contents of the 'info' paragrah in each page
from bs4 import BeautifulSoup
import os

for file in os.listdir('cattax'):
  if file[-4:] == 'html':
    soup = BeautifulSoup(open('cattax/' + file, 'r'), features='html.parser')
    print(soup.title.text + " : " + soup.h1.text)

    info_paragraph = soup.find('p', class_='info')
    if info_paragraph:
      print("Info paragraph:", info_paragraph.get_text())
    else:
      print("Info paragraph not found")

    print()  # Print an empty line for better readability
```

To modify the **`scrape.py`**script to print the contents of the 'info' paragraph in each page, we can use the **`.find()`** method to find the first **`<p>`**element with the 'info' class and then extract the text from it. Here's the modified script:

*and we can get the result:* 

![截屏2023-04-20 20.20.42.png](6%202%20Beautiful%20soup%208b4af601b53a492b8cb3e39412060baa/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_20.20.42.png)

### 2. Currently the script prints something for *every* page. Modify it so it would only print something out for the leaf nodes -- those pages that don't have a 'container' element of their own.(Question about it )

```python
from bs4 import BeautifulSoup
import os

for file in os.listdir('cattax'):
    if file[-4:] == 'html':
        soup = BeautifulSoup(open('cattax/' + file, 'r'), features='html.parser')
        
        container_element = soup.find('div', class_='container')
        
        # Check if the page is a leaf node (no 'container' element)
        if container_element is None:
            print(soup.title.text + " : " + soup.h1.text)
            
            info_paragraph = soup.find('p', class_='info')
            if info_paragraph:
                print("Info paragraph:", info_paragraph.get_text())
            else:
                print("Info paragraph not found")
            
            print()  # Print an empty line for better readability
```

![截屏2023-04-20 20.26.45.png](6%202%20Beautiful%20soup%208b4af601b53a492b8cb3e39412060baa/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_20.26.45.png)

### 3. Printing things out can be useful, but often we want to store values we scrape for later programmatic work. Rather than printing out information, create and update a [Python dict](https://realpython.com/python-dicts/) for all leaf nodes where the dictionary keys are the titles of a page and the values are the corresponding content of the 'info' box. *Run your script with `python -i scrape.py` and it will execute your script and then place you in an interactive session immediately following your script's execution. You can then check that the dictionary's contents are what you expect by interacting with the dict object in your interpreter.*

```python
from bs4 import BeautifulSoup
import os

# Initialize an empty dictionary to store the leaf node information
leaf_nodes = {}

for file in os.listdir('cattax'):
    if file[-4:] == 'html':
        soup = BeautifulSoup(open('cattax/' + file, 'r'), features='html.parser')

        container_element = soup.find('div', class_='container')

        # Check if the page is a leaf node (no 'container' element)
        if container_element is None:
            title = soup.title.text
            info_paragraph = soup.find('p', class_='info')
            
            if info_paragraph:
                info_text = info_paragraph.get_text()
            else:
                info_text = "Info paragraph not found"

            # Add the title and info text to the dictionary
            leaf_nodes[title] = info_text

# Print the dictionary to verify its contents
print(leaf_nodes)
```

and then we need to run the script with:

```python
python -i scrape.py
```

![截屏2023-04-20 20.32.22.png](6%202%20Beautiful%20soup%208b4af601b53a492b8cb3e39412060baa/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_20.32.22.png)

the output you provided shows the information stored in the **`leaf_nodes`** dictionary. The keys are the titles of the pages (the species or subspecies names), and the values are the corresponding content of the 'info' box. Each key-value pair in the dictionary represents a leaf node from the HTML files.

The **`python -i scrape.py`** command executed your script and then placed you in an interactive session where you can interact with the **`leaf_nodes`** dictionary or any other objects in your script.

The output format is typical for a Python dictionary, and you can further interact with or process the **`leaf_nodes`** dictionary in your interactive session or modify the script to meet your requirements.

## When to scrape

As we discuss in this week's lectures, scraping webpages can come with some risks, depending upon how you go about it and what you do with the results. Guidelines you should follow include:

正如我们在本周的讲座中所讨论的那样，抓取网页可能会带来一些风险，这取决于你如何去做以及你如何处理这些结果。你应该遵循的准则包括：

- Always respect the [robots.txt](https://developers.google.com/search/docs/crawling-indexing/robots/robots_txt) presented by a site. Resources denied to crawlers may be protected for a legal or ethical reason.始终尊重网站提供的robots.txt, 拒绝向爬虫提供的资源可能是出于法律或道德原因而受到保护。
- Always look for an API first. If a site will provide you with a JSON endpoint to query for the structured data you want, it is both easier and more polite to use that API instead of scraping the same data from webpages designed for human consumption. 总是先寻找API。如果一个网站为你提供一个JSON端点来查询你想要的结构化数据，那么使用该API比从为人类消费设计的网页上抓取相同的数据更容易也更有礼貌。
- Be very careful about any scraping behind an authenticated log-in, such as from a logged-in social media account. Think about the privacy expectations people have about the content you are collecting, both in legal and ethical terms. If you post publicly something that was intended only for a limited audience, you could be betraying a confidence, and might even face legal repercussions.对于任何在认证登录后的搜刮行为要非常小心，例如从登录的社交媒体账户中搜刮。从法律和道德的角度考虑人们对你所收集的内容的隐私期望。如果你公开发布只针对有限受众的内容，你可能背叛了信任，甚至可能面临法律后果。
- Generally beware that being able to access and read information from the web does not mean you are permitted to republish it, even in a modified form.一般来说，要注意的是，能够访问和阅读来自互联网的信息。

## Further reading

You may have noticed that we downloaded our webpages with `wget` in the previous exercise, and then dealt with their content using Python in this one. If you were writing a Python tool that was meant to do something specific with the content of a webpage, then you would often want to avoid using a second tool, and make web requests directly from your program. The Python library that is most often recommended for requesting web resources is the [Requests library](https://docs.python-requests.org/en/latest/), and getting familiar with it would be useful both if you wanted to access web pages programmatically and if you need to interact with a website's API.你可能已经注意到，我们在前面的练习中用`wget`下载了我们的网页，然后在这个练习中用Python处理了它们的内容。如果你正在编写一个Python工具，旨在对网页的内容做一些特定的处理，那么你通常希望避免使用第二个工具，而直接从你的程序中进行网络请求。最常被推荐用于请求网络资源的 Python 库是 [Requests 库](https://docs.python-requests.org/en/latest/)，如果你想以编程方式访问网页，或者需要与网站的 API 进行交互，熟悉它将非常有用。

We've also been dealing with the content of *static* websites, without the dynamic content like that you learned about in the Javascript exercises. Scraping dynamic sites gets trickier, as your scraper needs to have a browser-like context to execute Javascript within, and often might need to pretend to interact with the page. Systems like [Selenium](https://www.selenium.dev/documentation/) are designed for cases like this.

我们还一直在处理*静态*网站的内容，而没有像你在Javascript练习中学习的动态内容。刮取动态网站变得更加棘手，因为你的刮刀需要有一个类似于浏览器的上下文来执行Javascript，而且经常需要假装与页面互动。像[Selenium](https://www.selenium.dev/documentation/)这样的系统就是为这种情况设计的。

## Expand:

**Web Crawling**

Web crawling, also known as spidering or web indexing, is the process of systematically browsing and navigating through a collection of web pages to discover and catalog their content. Web crawlers, or spiders, are automated programs that visit websites, follow hyperlinks, and gather information about the pages they visit. The primary goal of web crawling is to create an index of web pages to facilitate searching or further data analysis.

Search engines like Google, Bing, and Yahoo use web crawlers to discover new web pages, index their content, and update their databases. This helps them provide relevant search results to users.

**Web Scraping**

Web scraping, on the other hand, is the process of extracting specific information from web pages. It involves downloading the HTML content of a web page, parsing it, and extracting the desired data, usually in a structured format like JSON, CSV, or a database.

Web scraping is used for various purposes, such as data analysis, data mining, sentiment analysis, price comparison, and more. It's a technique often employed by developers, data scientists, and researchers to collect data from websites that do not provide an API or a structured data format for easy access.

In summary, web crawling is about discovering and indexing web pages, while web scraping is about extracting specific information from those web pages. Often, web crawling is the first step in a larger data extraction process, followed by web scraping to gather the desired information.