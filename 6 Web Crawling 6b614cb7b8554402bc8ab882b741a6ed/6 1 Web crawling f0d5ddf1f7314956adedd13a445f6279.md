# 6.1 Web crawling

**Something from slides:** 

![截屏2023-04-22 23.47.29.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-22_23.47.29.png)

![截屏2023-04-22 23.50.05.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-22_23.50.05.png)

**`wget -p <url>`** is a command that is used to download a web page and all of its assets, such as images, stylesheets, and scripts, and save them to a local directory.

When using the **`wget -p <url>`** command, there are some things that **will not be saved** to the local directory along with the web page and its assets. These include:

1. Database information: **`wget`** will not download any information that is stored in a database, such as user information or comments.
2. Dynamic content: **`wget`** will not download any content that is generated dynamically by the server, such as search results or personalized content.
3. Streaming content: **`wget`** will not download any content that is streamed, such as video or audio.
4. Content from other domains: **`wget`** will only download content that is hosted on the same domain as the specified URL. Content from other domains will not be downloaded.
5. Content that is blocked by **`robots.txt`**: **`wget`** will not download any content that is disallowed by the rules in the **`robots.txt`** file.
6. Content that requires authentication: **`wget`** will not download any content that requires authentication, such as login pages or password-protected content.

It's important to keep these limitations in mind when using **`wget`** to download web pages and their assets. In some cases, it may be necessary to use additional tools or techniques to download certain types of content or to access content that is not publicly available.

![截屏2023-04-22 23.51.06.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-22_23.51.06.png)

**`robots.txt`** is a text file that is placed in the root directory of a website to instruct web robots, also known as crawlers or spiders, which pages or files they should or should not crawl or index. The purpose of **`robots.txt`** is to prevent web robots from accessing parts of the website that the website owner does not want to be indexed by search engines or disclosed to the public.

Here's an example of a **`robots.txt`** file:

```jsx
User-agent: *
Disallow: /private/
Disallow: /admin/
```

In the above example, the **`User-agent`** line specifies that the rules apply to all robots, while the **`Disallow`** lines specify that the directories **`/private/`** and **`/admin/`** should not be crawled or indexed by web robots. This means that web robots will not be able to access or index any pages or files within those directories.

It's important to note that while **`robots.txt`** can be used to prevent web robots from accessing certain pages or files, it is not a security mechanism and should not be relied upon to prevent unauthorized access to sensitive information. Additionally, web robots are not required to comply with the rules in **`robots.txt`**, and some may ignore the file altogether.

![截屏2023-04-22 23.52.51.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-22_23.52.51.png)

**Recursive downloading** refers to the process of downloading a website and **all of its contents,** including all **pages**, **images**, **videos**, and **other files**. This is typically done using a tool like **`wget`**, which allows you to download an entire website with a single command.

To perform a recursive download using **`wget`**, you can use the **`-r`** (recursive) option. This option tells **`wget`** to follow links on each page it downloads and download all of the linked pages and files as well.

Here's an example of how to use **`wget`** to perform a recursive download:

```
wget -r https://www.example.com
```

In the above example, **`wget`** is used to download the entire **`www.example.com`** website, including all pages and files.

By default, **`wget`** will download the files to the current directory. You can use the **`-P`** (directory prefix) option to specify a different directory to save the files to.

```
wget -r -P /path/to/directory https://www.example.com
```

In the above example, **`wget`** is used to download the entire **`www.example.com`** website and save it to the **`/path/to/directory`** directory.

The **`wget -r -l N <url>`** command is used to recursively download a website up to a certain depth specified by the **`N`** parameter. The **`-r`** option is used to tell **`wget`** to download recursively, while the **`-l N`** option specifies the maximum recursion depth.

Here's an example of how to use **`wget`** with the **`-r -l N`** options:

```
wget -r -l 2 https://www.example.com
```

In the above example, **`wget`** is used to download the **`www.example.com`** website up to a depth of 2 levels. This means that **`wget`** will download the home page and any pages that are directly linked to it (level 1), as well as any pages that are linked to those pages (level 2).

The **`-l N`** option can be used to limit the amount of data that is downloaded and to prevent **`wget`** from downloading the entire website. This can be useful for limiting the amount of time and bandwidth used by the download.

![截屏2023-04-22 23.55.49.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-22_23.55.49.png)

The **`wget -m <url>`** command is used to mirror a website, which means it downloads the website's content and creates a local copy that is an exact duplicate of the original website. The **`-m`** option is used to tell **`wget`** to mirror the website.

Here's an example of how to use **`wget`** with the **`-m`** option:

```
wget -m https://www.example.com
```

In the above example, **`wget`** is used to mirror the **`www.example.com`** website. This means that **`wget`** will download all of the content from the website, including pages, images, and other files, and create a local copy of the website that is an exact duplicate of the original.

The **`-m`** option is similar to the **`-r`** option, which is used for recursive downloading, but it includes additional options to ensure that the local copy of the website is an exact duplicate of the original. For example, the **`-k`** option is used to convert links in the downloaded files to work offline, while the **`-np`** option is used to prevent **`wget`** from downloading files from parent directories.

![截屏2023-04-22 23.56.26.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-22_23.56.26.png)

When web crawling, it's important to be aware of ethical considerations and to follow best practices to avoid any negative impact on the website or its users. Here are some key ethical considerations to keep in mind:

1. **Respect copyright and intellectual property**: It is important to respect copyright and intellectual property laws. This means that you should not download or distribute content that is protected by copyright without permission.
2. **Respect privacy:** It's important to respect the privacy of website owners and their users. This means that you should not collect or use personal information without permission.
3. **Follow website terms of service**: It's important to follow the terms of service of the website you are crawling. Some websites may prohibit web crawling or may have restrictions on the number of requests that can be made from a single IP address.
4. **Avoid overloading the server**: It's important to avoid overloading the server or causing excessive traffic to the website. This can be done by setting reasonable limits on the number of requests made, using appropriate delays between requests, and avoiding parallel requests.
5. **Attribute the source**: If you use content from a website that you have crawled, it's important to attribute the source and give credit to the website owner.

By following these ethical considerations and best practices, you can ensure that your web crawling activities are responsible and respectful of website owners and their users.

## Exercise

So far in this unit we've had you use `wget` only for one of its simplest use-cases: when you want to download a single file from the web. Consistent with the Unix philosophy that tools should 'do one thing well', `wget` is capable of a lot more than this.

To demonstrate this, we're going to have you first run a server to deploy a website locally, and then test out various `wget` options by connecting to that server via localhost. This of course doesn't mean that `wget` can only do these things via localhost -- it's designed to work with real websites -- but we decided that getting ~200 students to test out web-crawling on a particular live website was probably not a great idea, so we're having each of you run your own.

### Set up the server

As with the HTTP exercises, it would be best to either carry out these steps directly on a lab machine or on your own machine (optionally from the Alpine Linux VM with ports forwarded). If you are using a lab machine via SSH instead then you'll need to open a second SSH session *to the same lab machine* in another terminal, to act as a client for the next parts of the exercise. However, we'll periodically invite you to check things in your browser, which is a lot simpler if you're not trying to use a remote machine.

First, download the [webpages to be served by the webserver](https://cs-uob.github.io/COMSM0085/exercises/part2/resources/cattax.tar.gz). If you like you can even do this using `wget`:

```
(step 1)
wget https://cs-uob.github.io/COMSM0085/exercises/part2/resources/cattax.tar.gz
```

Then extract the contents of the tarball using (step 2)`tar -xzf cattax.tar.gz` in the folder you downloaded it to. This will create a folder `cattax` which contains some webpages and resources.

(The webpage looks like this below)

![截屏2023-04-19 17.28.23.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_17.28.23.png)

Next, use the `darkhttpd` server from a previous week's exercises to serve the content of the `cattax` folder on `localhost:8080`. *(Refer to the HTTP week's exercise instructions if you have forgotten how to do this)*.

How to do this:

1. First of all, git clone the darkhttpd in the folder (I put it in the same location with my cattac):

```jsx
git clone https://github.com/emikulic/darkhttpd
```

1. check if the darkhttpd is installed or need to be updated

```jsx
brew install darkhttpd 
```

1. go back to the folder where cattac is(part2), and use following command :

```jsx
darkhttpd cattax --port 8080
```

Then we got the message saying that:

![截屏2023-04-19 17.44.00.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_17.44.00.png)

1. if we try to check the webpage with localhost:8080, we will get the following page:

![截屏2023-04-19 17.44.31.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_17.44.31.png)

You can check that this is working in a browser (unless you are connecting via SSH) by navigating to `localhost:8080/index.html` -- you should see a webpage talking about **Felidae**. You'll need to leave this server running -- the simplest way forward would be to open another terminal for the steps below. 

*(Alternatively: use your shell expertise to figure out how to run the server in the background without its output interfering with the rest of what you're going to be doing in this terminal).*

This means we can **leave the terminal open** for the connection, or we can run this command line:

```bash
darkhttpd cattax --port 8080 > /dev/null 2>&1 &
```

- **`darkhttpd`**: This is the name of the command-line program that we're running. It's a small, lightweight HTTP server that can be used to serve static content.
- **`cattax`**: This is the directory that we want to serve. In this case, we want to serve the contents of the **`cattax`** directory.
- **`-port 8080`**: This specifies the port number that the server should listen on. In this case, we're using port 8080.
- **`> /dev/null`**: This is a shell redirection operator that redirects the standard output (stdout) of the **`darkhttpd`** command to the special file **`/dev/null`**. **`/dev/null`** is a special file on Unix-like systems that discards all data that is written to it. This means that any output that would normally be printed to the terminal by **`darkhttpd`** will be discarded instead of being displayed.
- **`2>&1`**: This is another shell redirection operator that redirects the standard error (stderr) of the **`darkhttpd`** command to the same place as the standard output. In other words, any error messages that would normally be printed to the terminal by **`darkhttpd`** will also be discarded instead of being displayed.
- **`&`**: This is a shell operator that tells the shell to run the command in the background. This means that the **`darkhttpd`** command will be started as a background process, and the shell will immediately return control to the user, allowing them to continue entering commands in the terminal.

![截屏2023-04-19 17.50.05.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_17.50.05.png)

After we run this line, we got a number which is 67803, this means that the **`darkhttpd`**
server has started successfully, and its process ID is **`67803`**

You can now open a web browser and navigate to **`http://localhost:8080`** to view the contents of the **`cattax`** folder.

Also, since you have used the **`&`** symbol at the end of the command, the **`darkhttpd`** server is running in the background, and you can continue using your terminal for other tasks. If you want to stop the **`darkhttpd`** server later, you can use the **`kill`** command and provide the process ID of the **`darkhttpd`** server process. For example, you can use the following command to stop the **`darkhttpd`** server:

```bash
kill 67803
```

## Single-page Download

To keep your filesystem tidy, we're going to work within a 'client' folder. We'll be repeatedly downloading files and sometimes deleting them, and you'll neither want lots of duplicated webpages littering your filesystem nor want to run `rm *` in a directory that possibly contains files you don't want deleted.

Make sure you are in the parent directory that contains `cattax` (i.e., you can type `ls` and see the directory `cattax` in the output) and *not inside* `cattax` itself. Then create a directory and move into it:

```

mkdir client
cd client

```

Now we'll start with the simple use of `wget` you have already become familiar with:

```

wget localhost:8080/index.html

```

![截屏2023-04-19 18.16.02.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_18.16.02.png)

This downloads the same `index.html` as is being served from `cattax` by `darkhttpd`. 

However, if you open this downloaded file in your browser, you'll see that there's a sense in which something missing -- `wget` has only downloaded the specific HTML file you requested, and not any of the resources that the page itself references, like the CSS file -- so the version you open in your browser from your `client` directory won't look the same as the version being served via localhost. 

![截屏2023-04-19 18.17.15.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_18.17.15.png)

(成功地下载到了client里, 如果使用wget那么只会下载特定的html文件,而不是全部)

所以如果我们用wget 去copy 一个网页的话, 我们就可以的带特定的页面,尝试用wget去复制了bbc首页的代码, 有11884行

![截屏2023-04-19 18.33.06.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_18.33.06.png)

This can be desirable default behaviour (we only asked it to get that page, after all), but if we wanted to download a copy of a webpage and later read that webpage's copy with the styles and images it was originally created to contain, we'd need to get `wget` to also download these resources.

One way to do this would be to manually identify each of the required resources and download them one-by-one. But this is tedious, repetitive work -- highly suited to automation -- and moreover, `wget` can save us the effort. Try the following, and **read the output**.

一种方式就是一个页面一个页面的去复制,但是就是重复单调的工作

```

wget -p localhost:8080/index.html
```

*(The **`wget`**command is a command-line utility for downloading files from the web. The **`-p`**
 option tells **`wget`**to download all files necessary to display the given webpage. The **`localhost:8080/index.html`**argument specifies the URL of the webpage to download.)*

Notice that this time `wget` downloaded multiple files. It also created a directory named `localhost:8080` to store all the files in. This is helpful organisation if you're ever using `wget` to download pages from multiple different websites -- it stores them under directories named after the domain you requested them from.

![截屏2023-04-19 18.36.50.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_18.36.50.png)

*(If we use this command line, and we can copy the three files.)*

If you read the output carefully you'll notice that as well as the `index.html` we requested directly, `wget` has also downloaded the `catstyle.css` file referenced in that page, and another file called `robots.txt` that you didn't ask for and which isn't mentioned in `index.html`. 

![截屏2023-04-19 18.37.14.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_18.37.14.png)

This 'robots' file is part of a standard for responsible web crawling, and tells crawling tools which parts of a website they are or aren't allowed to visit. When you use `wget` to crawl a webpage or website it will check the site's `robots.txt` to understand which resources it may not be allowed to download. You can read more about how these files are written [here](https://developers.google.com/search/docs/crawling-indexing/robots/robots_txt).

Open the `index.html` file from the new `localhost:8080` folder that was created, and you should see that it looks just like the version you got in your browser by navigating to the URI `localhost:8080/index.html`. *(There are some cases where this wouldn't be true for a webpage -- wget can sometimes not be permitted access to some resources required to display a page the same way as it is shown in your browser).*

### what is robot.txt?

**`robots.txt`** is a standard used by websites to communicate with web robots and automated web crawlers, also known as "spiders" or "bots". It is a plain text file that contains instructions for these automated agents on what parts of the website they are allowed to access and crawl.

The **`robots.txt`** file is typically located in the root directory of a website, and it specifies which web pages or directories the automated agents are allowed to crawl and index. By default, web robots are allowed to crawl and index all pages on a website, so the **`robots.txt`** file is used to limit their access to certain pages or directories.

For example, a website may use the **`robots.txt`** file to exclude certain pages from being crawled and indexed by search engines, or to prevent web scrapers from harvesting its content.

It's important to note that the **`robots.txt`** file is a voluntary standard, and not all web robots and crawlers follow it. Additionally, some malicious bots may ignore the **`robots.txt`** file and attempt to access restricted pages regardless. Therefore, it's important to use other security measures, such as authentication and access controls, to protect sensitive information on a website.

<aside>
💡 extra attempt:

</aside>

When we try to copy the webpage of bbc,if we use wget -p … we will only get the index since The **`-p`** option in **`wget`**stands for "page requisites," which tells **`wget`**to download all the resources needed to display the web page, such as images, stylesheets, and scripts. However, **`wget`**
will not download external resources that are hosted on other domains, unless the **`--span-hosts`**option is also used.

Therefore, we can try to use 

```bash
wget -p --span-hosts [https://www.bbc.co.uk](https://www.bbc.co.uk/)
```

- **`wget`**: This is the name of the command-line utility we are using to download files from the web.
- **`p`**: This is a short option that stands for "page requisites". It tells **`wget`** to download all the resources necessary to display the webpage, such as images, stylesheets, and scripts.
- **`-span-hosts`**: This is a long option that tells **`wget`** to follow links to external domains and download files from those domains as well. In other words, if the webpage at **`https://www.bbc.co.uk/`** includes images or other resources hosted on external domains, **`wget`** will download those resources as well.
- **`https://www.bbc.co.uk`**: This is the URL of the webpage that we want to download. In this case, we are downloading the webpage located at **`https://www.bbc.co.uk/`**.

When you run this command, **`wget`** will download the **`index.html`** file of the webpage at **`https://www.bbc.co.uk/`**, as well as any resources necessary to display the page, such as images, stylesheets, and scripts. The **`--span-hosts`** option ensures that **`wget`** will download any external resources hosted on other domains as well, if any are present on the page.

### Crawling a site

The version of the webpage you downloaded using the previous command still has one major flaw: the links on the page don't work. Or, rather, the links to the 'Felinae' and 'Pantherinae' pages are broken, because those links are made relative to the webpage, and the corresponding files don't exist in the client's folder. The link to Wikipedia in the page footer *does* still work, because the `href` attribute of that link is set to a full URI.

![截屏2023-04-19 19.34.40.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_19.34.40.png)

What do we do if we want to **download more than one webpage** from a site? Wget supports something called '**recursive downloading**'. Simply put, when used in this manner it will follow all links internal to a site and download the resources displayed at those links, storing a copy locally and creating a directory structure if necessary. One version of this recursion is to use the `-r` (or `--recursive`) option, which downloads all linked pages up to a certain maximum depth. Try this out:

```

wget -r -l 1 localhost:8080/index.html
```

![截屏2023-04-19 19.36.20.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_19.36.20.png)

This downloads recursively with the 'level' (maximum depth of recursion) set to 1 level of recursion. You should see that both the requested `index.html` and the two pages linked from that resource have been downloaded, along with `robots.txt`. 

![截屏2023-04-19 19.37.22.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_19.37.22.png)

Notice as well that the Wikipedia page has not been downloaded -- it's not hosted at `localhost:8080`, so `wget` ignores it, and the link will work from the downloaded page anyway. Our two newly-downloaded pages, however, will contain dead links to other pages, because we limited the depth of recursion to just one hop. If we increase this:

```

wget -r -l 2 localhost:8080/index.html
```

![截屏2023-04-19 19.38.40.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_19.38.40.png)

![截屏2023-04-19 19.38.57.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_19.38.57.png)

You'll see that a *lot* more files get downloaded. These are only very small, simple web-pages, without many links (contrast, for example, any given Wikipedia page). Very short recursion depths can capture an awful lot of a domain, and if you ever tell `wget` to crawl links without caring about which domain they belong to, this becomes explosively worse (`-l 2` in such a case for our `index.html` would involve downloading everything linked from the Wikipedia page referenced in the footer -- several hundred resources). In the case of our cattax website, however, there are still a few pages that are more than 2 steps away from the index page. Let's start afresh:

```

rm -r localhost:8080
wget -m localhost:8080/index.html
```

![截屏2023-04-19 19.40.21.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_19.40.21.png)

The `-m` flag is designed to provide some sensible defaults for 'mirroring' an entire website (something you might do if you wanted to keep a copy of it for offline browsing, or for providing a public backup of a valuable resource). It sets the recursion level to infinite and checks timestamps before downloading files, as well as setting a few more configuration settings. For many cases where you might want to download an entire website, this is the flag you would use -- perhaps also with a polite `-w 1`, which sets a 1-second delay between requests, to avoid over-burdening the server if the website is large.

所以如果我们想要下载完整网站的时候可以使用这个

# Further Exercises

### 1. **Read `man wget` to understand what the `i` `-force-html` and `-spider` options do. Download a copy of this webpage (the one you are currently reading) and use `wget` to test all the links on the page. Are there any broken links?**

*Understand the options:* 

- **`i`** or **`-input-file=FILE`**: This option tells **`wget`** to download URLs found in a local or external file. The file should contain a list of URLs, one per line.
- **`-force-html`**: When used with **`i`**, this option treats the input file as an HTML file. It searches for URLs within the file even if it doesn't have the proper HTML structure. This is useful when the input file contains raw URLs mixed with HTML code.
- **`-spider`**: This option doesn't download the files or pages but only checks if they exist. It is commonly used to test links for their validity. When a URL is not accessible or broken, **`wget`** will report an error.

*To download the page we can use :* 

```bash
wget https://cs-uob.github.io/COMSM0085/exercises/part2/scrape/crawl.html
```

![截屏2023-04-19 19.52.13.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_19.52.13.png)

To test the links on the page, we can try

```bash
wget -p -k -E https://cs-uob.github.io/COMSM0085/exercises/part2/scrape/crawl.html
```

![截屏2023-04-19 19.53.49.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_19.53.49.png)

- **`wget`**: This is the command-line tool for downloading files and web pages from the internet.
- **`p`** or **`-page-requisites`**: This option downloads all files necessary to properly display the page, such as images, stylesheets, and scripts. This is useful for offline viewing.
- **`k`** or **`-convert-links`**: This option modifies the links in the downloaded HTML files so that they point to the local files instead of their online counterparts. This is helpful when you want to browse the downloaded website offline.
- **`E`** or **`-adjust-extension`**: This option adds the appropriate file extension to downloaded files, such as **`.html`** or **`.css`**, if they are missing. This can be useful for ensuring that files are recognized correctly by web browsers or other software.
- **`https://cs-uob.github.io/COMSM0085/exercises/part2/scrape/crawl.html`**: This is the URL of the webpage you want to download.

So, the command you provided will download the webpage located at **`https://cs-uob.github.io/COMSM0085/exercises/part2/scrape/crawl.html`**, along with its necessary resources for proper offline viewing, and convert the links within the downloaded files to point to the local copies.

***and then*** 

*: to check the validity of the links found in a given file or URL without downloading the actual files or pages*

```bash
wget --spider --force-html -i crawl.html
```

- **`wget`**: This is the command-line tool for downloading files and web pages from the internet.
- **`-spider`**: This option tells **`wget`** to only check if the URLs exist, without downloading them. It is commonly used to test links for their validity. If a URL is not accessible or broken, **`wget`** will report an error.
- **`-force-html`**: This option treats the input file or URL as an HTML file. It searches for URLs within the file even if it doesn't have the proper HTML structure. This is useful when the input file contains raw URLs mixed with HTML code.
- **`i`** or **`-input-file=FILE`**: This option tells **`wget`** to download or check URLs found in a local or external file. The file should contain a list of URLs, one per line. In this case, the provided URL will be treated as the input file.

![截屏2023-04-19 20.08.47.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_20.08.47.png)

These incomplete links are relative URLs, which means they are not complete addresses by themselves and need to be combined with a base URL to form a proper URL.

In order to resolve this issue, you can use the **`-B`** or **`--base`** option to specify the base URL. The base URL should be the root URL of the website where the **`crawl.html`** file is hosted. In this case, the base URL is **`https://cs-uob.github.io/COMSM0085/`**. Modify the command as follows:

```bash
wget --spider --force-html -i crawl.html -B [https://cs-uob.github.io/COMSM0085/](https://cs-uob.github.io/COMSM0085/)
```

***and then we can get following result:***

![截屏2023-04-19 20.10.21.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_20.10.21.png)

### 2. Tell `wget` to use a different user agent string in a request to your server running on localhost. Check what the request looks like to your server.

*To use a different agent string, we can use the following command:*

```bash
wget --user-agent="My Custom User Agent" http://localhost:8080/
```

*and then we got the result :*

![截屏2023-04-19 21.20.14.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_21.20.14.png)

To check what the request looks like to my server:

1. We can set up a server script by using shell script:(nano server.sh)

```bash
#!/bin/bash

while true; do
  { echo -ne "HTTP/1.1 200 OK\r\nContent-Length: 2\r\n\r\nOK"; } | nc -l -p 8080 | while read line; do
    if echo "$line" | grep -q "User-Agent"; then
      echo "$line"
    fi
  done
done
```

This is a simple Bash script that creates a server that listens on port 8080 and sends an "HTTP/1.1 200 OK" response with a content length of 2 and a response body "OK" to any incoming request. The server will log incoming requests that have a "User-Agent" header.

Let's break down the script:

- **`#!/bin/bash`**: This line specifies the interpreter for the script, which is Bash in this case.
- **`while true; do`**: This starts an infinite loop.
- **`{ echo -ne "HTTP/1.1 200 OK\r\nContent-Length: 2\r\n\r\nOK"; } | nc -l -p 8080`**: This creates a simple server that listens on port 8080 using **`nc`** (netcat) and sends a predefined HTTP response. The response has an "HTTP/1.1 200 OK" status line, a "Content-Length: 2" header, and a response body of "OK".
- **`| while read line; do`**: This reads the incoming request line by line.
- **`if echo "$line" | grep -q "User-Agent"; then`**: This checks if the current line contains the "User-Agent" string.
- **`echo "$line"`**: If the "User-Agent" string is found, the script prints the line containing it.
- **`fi`**: This ends the if statement.
- **`done`**: This ends the inner while loop.
- **`done`**: This ends the outer while loop.

---

---

---

1. save the file and exit the text editor.
2. Make the **`server.sh`** file executable by running the following command:

```bash
chomod +x server.sh
```

1. open another terminal and go to the directory where [server.sh](http://server.sh) at. And Run:

```bash
./server.sh
```

Server script is now set up and listening for incoming requests on port 8080. To see the User-Agent string in the incoming requests, you can use the **`wget`**command with a custom User-Agent in another terminal:

1. Then you might got no response, go back to the terminal and run:

```bash
wget --user-agent="My Custom User Agent" [http://localhost:8080/](http://localhost:8080/)
```

one side we might get the message that: (html.3 is because I have same multiple times)

![截屏2023-04-19 21.48.30.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_21.48.30.png)

And we open the other terminal where we are running the server.sh, we can see following message:(success!)

![截屏2023-04-19 21.44.23.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_21.44.23.png)

note that I had the error message because the port:8080 was running, so I killed it with the reference number. 

![截屏2023-04-19 21.51.34.png](6%201%20Web%20crawling%20f0d5ddf1f7314956adedd13a445f6279/%25E6%2588%25AA%25E5%25B1%258F2023-04-19_21.51.34.png)

### 3. How would `wget -l 1 http://example.com` differ from `wget -p http://example.com`? *(Hint: think about external resources)*.

- **`wget -l 1 http://example.com`** and **`wget -p http://example.com`** both download the specified URL, but they behave differently in terms of handling external resources and the depth of the download.

**`wget -l 1 http://example.com`**:

- The **`l 1`** option sets the maximum recursion depth to 1. This means that **`wget`** will download the main page (**[http://example.com](http://example.com/)**) and only the resources directly linked to it, without following any further links. It will not download any external resources (e.g., images, CSS, JavaScript) that are not hosted on the same domain.

**`wget -p http://example.com`**:

- The **`p`** option (short for **`-page-requisites`**) tells **`wget`** to download all the files that are necessary to display the HTML page properly, including images, stylesheets, and scripts. This option will download external resources as well, even if they are hosted on different domains, as long as they are required to display the page correctly.下载正确显示 HTML 页面所需的所有文件，包括图像、样式表和脚本。此选项也会下载外部资源，即使它们托管在不同的域中，只要它们是正确显示页面所必需的。

### 4. Look for 'Recursive Accept/Reject options' in the `wget` manpage. How would you get `wget` to crawl pages from multiple different domains?

To get **`wget`** to crawl pages from multiple different domains, you can use the **`--domains`** option along with **`--span-hosts`** in the 'Recursive Accept/Reject options' section of the **`wget`** manpage.

Here's how you can use these options:

**`wget --recursive --level=depth --span-hosts --domains=example.com,example2.com http://example.com`**

- **`-recursive`**: This option enables the recursive retrieval of web pages.
- **`-level=depth`**: This option sets the maximum recursion depth to **`depth`**. Replace **`depth`** with the desired number, or use **`inf`** for infinite depth.
- **`-span-hosts`**: This option allows **`wget`** to visit pages from different hosts within the same recursive retrieval session.
- **`-domains=example.com,example2.com`**: This option is a comma-separated list of domains you want to crawl. In this example, it is set to crawl pages from example.com and example2.com.

By using these options, you can get **`wget`** to crawl pages from multiple different domains as specified in the **`--domains`** option.

### 5. Look up what `nc` does. What is clobbering, and why would or wouldn't you want to do it?

**`nc`** (short for netcat) is a versatile networking utility that can be used for reading from and writing to network connections using TCP or UDP. It is often called the "Swiss army knife" of networking because of its flexibility and wide range of use cases. **`nc`** can be used for port scanning, port redirection, creating backdoors, transferring files, and as a simple chat server or client, among other things.

Clobbering, in the context of file handling, refers to overwriting an existing file with a new one, usually without any confirmation or backup. When you clobber a file, the original content is lost and replaced with the new content.

There are scenarios where you might want to enable or disable clobbering:

1. Enable clobbering:
    - When you want to update a file with new content and don't care about the old content.
    - When you are confident that the new content is correct, and there's no need to keep a backup of the old content.
2. Disable clobbering:
    - When you want to preserve the original content and avoid accidental overwriting.
    - When you want to keep multiple versions of a file, such as for backup or historical purposes.

In the case of **`wget`**, you can control clobbering using the **`-nc`** or **`--no-clobber`** option. This option prevents **`wget`** from overwriting existing files when downloading, and is useful when you want to avoid accidental file overwrites.