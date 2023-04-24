# Software tools Question

### Web crawling question:

1. Can we download the video from a website by using wget?
2. Are there any tips for us to fetch the correct API.

why my API doesn’t work if I delete limit = 100:

```jsx
fetch(`https://opendata.bristol.gov.uk/api/v2/catalog/datasets/life-expectancy-in-bristol/records?limit=100&refine.ward_code=${id}`)
```

1. when we download the webpage what is the meaning of ‘lack of last modified header’

![截屏2023-04-21 14.41.06.png](Software%20tools%20Question%20b1f1f1ee8c8e48b2bec987b96a47889a/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_14.41.06.png)

1. for the task:. (6.1)Tell `wget` to use a different user agent string in a request to your server running on localhost. Check what the request looks like to your server. Does this mean that we need to write our own server script then check how it look it?

1. For the task (6.1) **Read `man wget` to understand what the `i` `-force-html` and `-spider` options do. Download a copy of this webpage (the one you are currently reading) and use `wget` to test all the links on the page. Are there any broken links?**

what does the broken links mean? is it because it is blocked by firewall?

*Understand the options:* 

- **`i`** or **`-input-file=FILE`**: This option tells **`wget`** to download URLs **found in a local** or external file. The file should contain a list of URLs, one per line.
- **`-force-html`**: When used with **`i`**, this option treats the input file as an HTML file. It searches for URLs within the file even if it doesn't have the proper HTML structure. This is useful when the input file contains raw URLs mixed with HTML code.
- **`-spider`**: This option doesn't download the files or pages but only checks if they exist. It is commonly used to test links for their validity. When a URL is not accessible or broken, **`wget`** will report an error.

1. check the exercise about the beautiful soup, is it correct?

More question:

1. Any suggestions about how can we effectively prepare the exam? Go through all the exercise, and be able to write the code, and how far should we go for the additional reading?

function based component question about react

### Some extra questions

1. **Static server and dynamic server** 

A static server serves static content, which means the content is fixed and does not change based on user interactions or input. Static content can include HTML, CSS, images, and other files that make up a website or application.

On the other hand, a dynamic server serves dynamic content, which means the content changes based on user input or other factors. Dynamic content is generated on the server-side, often using a programming language such as PHP, Python, or Ruby, and can include things like user-specific information, data from a database, or content generated on-the-fly.

In summary, the main difference between a static server and a dynamic server is that a static server serves fixed content, while a dynamic server generates content based on user interactions or other factors.

1. **React generate dynamic content**

Yes, React is a popular JavaScript library for building user interfaces, and it is often used to generate dynamic content on the client-side. With React, you can create components that can update their content based on user interactions, data from an API, or changes in the application's state.

React's virtual DOM (Document Object Model) allows for efficient updating of the UI without having to reload the entire page, which can make it a powerful tool for building dynamic web applications. With React, you can also easily manage the state of your application, which allows for even more flexibility in generating dynamic content.

So, in short, React can be used to generate dynamic content on the client-side, and it is a powerful tool for building interactive and responsive user interfaces.

1. **darkhttpd serve static content** 

darkhttpd is a lightweight web server that is primarily designed to serve static content. It is a simple and efficient web server that can handle HTTP requests and serve static files such as HTML, CSS, images, and other resources.

One of the key features of darkhttpd is its small size and low resource usage, making it ideal for serving static files on low-powered devices or in environments with limited resources. However, darkhttpd does not support dynamic content generation, so it may not be the best choice for applications that require dynamic content.

In summary, darkhttpd is a static web server that is well-suited for serving static content efficiently and with low resource usage. If you need to serve dynamic content, you may need to consider a different web server or a framework that can generate dynamic content, such as Apache or Nginx with PHP or Python.