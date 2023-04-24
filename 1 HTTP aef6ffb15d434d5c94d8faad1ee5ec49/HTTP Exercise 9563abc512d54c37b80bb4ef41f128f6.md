# HTTP Exercise

This document contains exercises related to HTTP and a Java server. It covers topics such as URL fragments, the Accept and User-Agent headers, encoding special characters in URLs, and the Apache web server. The Java server exercise involves creating a web server using the Spring Boot framework and handling HTTP requests using annotations such as @RestController and @GetMapping.

## Exercise part

### Set up:

1. add this line to the ‘Vagrantfile’.

```java
config.vm.network "forwarded_port", guest: 8000, host: 8000
```

So in the Vagrantfile, it will look like this:

![截屏2023-03-09 13.29.29.png](HTTP%20Exercise%209563abc512d54c37b80bb4ef41f128f6/%25E6%2588%25AA%25E5%25B1%258F2023-03-09_13.29.29.png)

(P.S. Better not to have two port here, I couldn’t open the web afterwards, so I commented out the line with the host 8080 using @ since it is shellscript. )

Then restart the vagrant VM and try flollowing:

Run command:

```java
wget localhost:8000 
//used to download the content of a web page hosted on the local machine
//(localhost) using port 8000, typically via the HTTP protocol.
```

and we get the:

![截屏2023-03-09 13.31.28.png](HTTP%20Exercise%209563abc512d54c37b80bb4ef41f128f6/%25E6%2588%25AA%25E5%25B1%258F2023-03-09_13.31.28.png)

on the machine where you want to run the *server*. It should time out after a couple of seconds (or instantly) with "failed" and some error message. It should say it is failed since it means no one is using this port.

Next run:

```java
netstat -tan

//The command "netstat -tan" is used to display a list of active 
//network connections (TCP and UDP) on the system, 
//including both listening and established connections, 
//with the IP addresses and port numbers displayed in numerical 
//form instead of resolving the hostnames.
```

![截屏2023-03-09 13.33.07.png](HTTP%20Exercise%209563abc512d54c37b80bb4ef41f128f6/%25E6%2588%25AA%25E5%25B1%258F2023-03-09_13.33.07.png)

Make sure there is no value “8000” under local address and a state of LISTEN or ESTABLISHED.

If you get a lot of lines, `netstat -tan | grep 8000`will help.

(When you are in your own machine, you can always use this line to check if the line is been used, if you’ve already used the port on VM, you can actually )

## A basic HTTP server an client

Open a terminal on the machine where you want to run the server, and download the file [http-response](https://cs-uob.github.io/COMSM0085/exercises/part2/resources/http-response) to the folder where your terminal is open (for example with `wget`). Then run the command. 

(Tips: copy the link and use wget.)

```

nc -l -p 8000 < http-response
```

when you run this line, there is actually no response on your terminal, but you can go to the web browser and type in: localhost:8000

![截屏2023-03-09 14.15.42.png](HTTP%20Exercise%209563abc512d54c37b80bb4ef41f128f6/%25E6%2588%25AA%25E5%25B1%258F2023-03-09_14.15.42.png)

and you can get 

![截屏2023-03-09 14.17.06.png](HTTP%20Exercise%209563abc512d54c37b80bb4ef41f128f6/%25E6%2588%25AA%25E5%25B1%258F2023-03-09_14.17.06.png)

If there is any other messages, you need to check your port. 

This calls the tool `nc` ("network cat") and tells it to listen on TCP port 8000 (`-l -p 8000`), e.g. to run a server there. When a client connects, `nc` will by default read from its standard input and write this to the client, so we use a shell redirect to make it read from a file instead. The file contains some standard HTTP:

```html

HTTP/1.1 200 OK
Content-type: text/plain
Content-length: 18
Connection: close

Hello over HTTP!

```

(If you want to type this out yourself or copy-paste, you **must** save the file with CRLF line endings and put two newlines after the hello message.)

`nc` will block until you connect a client. Open another terminal on the machine you want to run your client and run （可以打开VM或者在自己的电脑上都可以运行这一行）

```html

wget -q -S -O - localhost:8000

```

You have now made a HTTP connection from the wget client to the nc server. The server terminal should print out the HTTP request it got from the client (this is built into wget) and the client should print out the response from the server (which comes from the file).

## Connecting with web browser

Run `nc -l -p 8000 < http-response`again on your server machine (kill the old one with `Control+C`first if it hasn't terminated already).

Open a web browser on your client machine (e.g. your own PC/laptop, or a lab machine). If you're using chrome/edge or firefox, open the debug tools (`F12`) and go to the network tab before you open the page. 

*打开浏览器然后输入: localhost:8000, 然后fn+F12打开debug tool*  

Navigate to `localhost:8000`. You should see the line "Hello over HTTP!" and `nc` will print the HTTP request from your browser. You can then close it with `Control+C` if it doesn't terminate by itself. In your browser's debug tools, on the network tab you should see a file `localhost`, click this and then select *Headers* in the details that appear.

*⬇️ Select localhost*

![截屏2023-03-09 14.29.01.png](HTTP%20Exercise%209563abc512d54c37b80bb4ef41f128f6/%25E6%2588%25AA%25E5%25B1%258F2023-03-09_14.29.01.png)

![截屏2023-03-09 14.34.33.png](HTTP%20Exercise%209563abc512d54c37b80bb4ef41f128f6/%25E6%2588%25AA%25E5%25B1%258F2023-03-09_14.34.33.png)

## Header: 标头

This details page shows you the HTTP request details, including the response code (`200 OK`
 in this case) and all the headers sent in both directions. This screen is one of the first places you should look at when something web-based that you've coded is not working correctly or at all, as HTTP is normally the lowest layer you need to care about.

此详细信息页面显示HTTP请求的详细信息，包括响应代码（在此情况下为“200 OK”）以及在两个方向上发送的所有标头。当你编写的基于Web的某些东西不正确或根本不工作时，此屏幕通常是你应该查看的第一个地方，因为HTTP通常是你需要关心的最低层。

In particular, the `Content-type`header is a common source of mistakes: if you want to serve e.g. a script or a stylesheet but you don't set the correct type header, your browser may download the file just fine but won't do anything with it. Similarly, whether you send `text/plain`or `text/html`determines whether the browser will interpret a file you navigate to as HTML or not.

特别是，`Content-type`头部是错误的常见来源：如果您想提供例如脚本或样式表，但您没有设置正确的类型头部，您的浏览器可能会下载文件，但不会执行任何操作。同样，发送`text/plain`或`text/html`决定浏览器是否将您导航到的文件解释为HTML。

## A web server in C

1. clone the repository `https://github.com/emikulic/darkhttpd`
2. Compile the program either with `make` or simply `gcc darkhttpd.c -o darkhttpd`. The server's job is to serve files within a folder, so make a subfolder called `web`and then run it with `./darkhttpd web --port 8000`. You can stop it again at the end of the exercise with `Control+C`.

use

```html
 cd ~/darkhttpd/
```

compile it with ‘make’

and then 

```html
mkdir web
```

then run 

```html
 ./darkhttpd web --port 8000
```

So you can reopen the web: port 8000 and check the changed,

**then every time if you want to load the website, you can do following:**

1. `make` or simply `gcc darkhttpd.c -o darkhttpd`
2. `./darkhttpd web --port 8000`

You can now experiment with the following:

- Create some files (plain text, HTML, image etc.) in `web/`.
- Access them from your browser with `localhost:8000/FILENAME`, for example `web/hello.txt` would become `localhost:8000/hello.txt`.
- Observe the HTTP headers in your browser's developer tools, and the server logs printed in the server terminal.

(TIPs: for creating some files just use: 1. cd web, 2. mkdir)

(then echo "Hello, world!" > hello.txt)

![截屏2023-03-09 14.59.53.png](HTTP%20Exercise%209563abc512d54c37b80bb4ef41f128f6/%25E6%2588%25AA%25E5%25B1%258F2023-03-09_14.59.53.png)

- Observe the HTTP headers in your browser's developer tools, and the server logs printed in the server terminal.
    
    ![截屏2023-03-09 15.07.05.png](HTTP%20Exercise%209563abc512d54c37b80bb4ef41f128f6/%25E6%2588%25AA%25E5%25B1%258F2023-03-09_15.07.05.png)
    

You can try this out for yourself if you want: make a HTML file called `one.html5` in the web directory and access it with the browser. (`.html5` is not an official extension, it's something I just made up. The correct one to use for proper websites is `.html`.) The server won't send a `Content-type` header at all, since it doesn't know this extension, so the browser will either display it as a plain text file or download the file instead of showing it. 如果你想尝试一下，可以在网络目录中创建一个名为 `one.html5` 的 HTML 文件，并使用浏览器访问它。（`.html5` 不是官方扩展名，我只是编造了一个。正确的扩展名是 `.html`。）由于服务器不知道这个扩展名，所以不会发送 `Content-type` 头，因此浏览器要么将其显示为纯文本文件，要么下载文件而不是显示它。

Edit the map in the source file and change the entry for `text/html` to read `" html htm html5"`, keeping the space at the start of the string. Recompile the server. 在源文件中编辑地图，并将“text / html”的条目更改为““ html htm html5””，保留字符串开头的空格。重新编译服务器。

By editing the map in the source file and changing the entry for **`text/html`** to **`" html htm html5"`**, you are updating the server's configuration to recognize files with the extensions **`.html`**, **`.htm`**, and **`.html5`** as files of the MIME type **`text/html`**.

After recompiling the server with this change, when the server serves a file with one of these extensions, it will include a **`Content-type`** header in the HTTP response, indicating that the file being sent is of type **`text/html`**. This header helps the client (usually a web browser) understand how to process and render the received file correctly.

![截屏2023-03-09 15.27.26.png](HTTP%20Exercise%209563abc512d54c37b80bb4ef41f128f6/%25E6%2588%25AA%25E5%25B1%258F2023-03-09_15.27.26.png)

Rename the file to `two.html5` and restart the server and try and open the file in the browser. This time, the file will display as a HTML page.

```html
cd web
```

```html
mv one.html5 two.html5
```

so we can see the file will display as a HTML page.

![截屏2023-03-09 15.31.18.png](HTTP%20Exercise%209563abc512d54c37b80bb4ef41f128f6/%25E6%2588%25AA%25E5%25B1%258F2023-03-09_15.31.18.png)

Why did you have to rename the file? Because the browser will otherwise try and be clever if it thinks you're trying to access a file that you've just downloaded already. The server sends a `Last-modified` header, and if the browser notices you're asking for a file you have just downloaded, with the same timestamp as the HTTP header indicates, then your browser might ignore the rest of the request and not see that another header has changed. Changing the file name forces the browser to look again as it thinks it's a different file now. Deleting the downloaded file, or editing the file on the server, would both have the same effect. 为什么你不得不重命名文件？因为，如果浏览器认为你正在尝试访问一个刚刚下载过的文件，它将试图变得聪明。服务器发送一个`Last-modified`头，如果浏览器注意到你正在请求一个你刚刚下载过的文件，其时间戳与HTTP头指示的相同，则你的浏览器可能会忽略请求的其余部分，而不看到另一个头已经更改。更改文件名会迫使浏览器再次查看，因为它认为现在是另一个文件。删除已下载的文件或编辑服务器上的文件都会产生同样的效果。

There is a moral here: if you're doing web development, and you are trying to find out why a change you made isn't showing in the browser (even if you refresh the page), it might be a cache problem. On the network tab of the developer tools window, there should be a checkbox to "disable cache" which you might want to turn on in this case and reload the page again, to exclude the cache as the possible source of the problem.这里有一个教训：如果你在进行网页开发，尝试查明为什么你所做的更改没有显示在浏览器中（即使你刷新了页面），那可能是缓存问题。在开发者工具窗口的网络选项卡中，应该有一个“禁用缓存”的复选框，在这种情况下你可以勾选它并重新加载页面，以排除缓存作为问题可能来源。

### **MCQ Questions:**

1. What is the purpose of the command `wget localhost:8000`?
    - A. To download the content of a web page hosted on a remote machine
    - B. To download the content of a web page hosted on the local machine
    - C. To upload content to a web page hosted on a remote machine
    - D. To upload content to a web page hosted on the local machine
2. What is the purpose of the command `netstat -tan`?
    - A. To display a list of active network connections on the system
    - B. To display a list of inactive network connections on the system
    - C. To display a list of open ports on the system
    - D. To display a list of closed ports on the system
3. What does the command `nc -l -p 8000 < http-response` do?
    - A. Downloads the contents of a web page hosted on a remote machine
    - B. Downloads the contents of a web page hosted on the local machine
    - C. Runs a server that listens on TCP port 8000
    - D. Runs a client that connects to a server on TCP port 8000
4. What does the `Content-type` header indicate in an HTTP response?
    - A. The MIME type of the content being sent
    - B. The length of the content being sent
    - C. The IP address of the server sending the content
    - D. The port number of the server sending the content
5. What is the purpose of the `Last-modified` header in an HTTP response?
    - A. To indicate the MIME type of the content being sent
    - B. To indicate the length of the content being sent
    - C. To indicate the last time the content being sent was modified
    - D. To indicate the IP address of the server sending the content
6. What is the purpose of the `disable cache` checkbox on the network tab of the browser's developer tools?
    - A. To prevent the browser from caching the contents of a web page
    - B. To prevent the server from caching the contents of a web page
    - C. To prevent the client from caching the contents of a web page
    - D. To prevent the network from caching the contents of a web page

### **Answers:**

1. B. To download the content of a web page hosted on the local machine
2. A. To display a list of active network connections on the system
3. C. Runs a server that listens on TCP port 8000
4. A. The MIME type of the content being sent
5. C. To indicate the last time the content being sent was modified
6. A. To prevent the browser from caching the contents of a web page

## 1.3 HTTP/URL research exercise:

Research online what the following are and what they do:

### **The *fragment* part of a URL.**

The fragment part of a URL is a component that appears at the end of a URL and is separated from the rest of the URL by a "#" symbol. It is also known as the fragment identifier or the anchor. URL 的片段部分是出现在 URL 结尾的一个组成部分，与 URL 的其余部分用 "#" 符号分隔开。它也被称为片段标识符或锚点。

The fragment part of a URL specifies a specific section or location within the target resource, such as a web page or a document. For example, in the URL **`https://www.example.com/document.html#section3`**, the fragment part is **`#section3`**.

URL 的片段部分指定了目标资源中的特定部分或位置，例如网页或文档。例如，在 URL **`https://www.example.com/document.html#section3`** 中，片段部分是 **`#section3`**。

When a user clicks on a link with a fragment part, the browser will scroll the target resource to the specified section or location, making it visible to the user. This is often used to link to a specific part of a long web page or document. 当用户点击带有片段部分的链接时，浏览器会滚动目标资源到指定的部分或位置，使其对用户可见。这经常用于链接到长网页或文档的特定部分。

The fragment part of a URL is not sent to the server when the browser requests the resource, and is only used by the client-side browser to navigate within the target resource. Therefore, it is not necessary for the server to know or handle the fragment part of a URL. URL 的片段部分在浏览器请求资源时不会发送到服务器，仅由客户端浏览器用于在目标资源中导航。因此，服务器不需要知道或处理 URL 的片段部分。

### **The `Accept` header sent by the HTTP client.**

The **`Accept`** header is a request header sent by the HTTP client (such as a web browser or a mobile app) to indicate the types of content that it can understand and handle. The header specifies one or more MIME types, and the server is expected to respond with a resource in one of those types, if possible. *`Accept`*头是由HTTP客户端（如Web浏览器或移动应用程序）发送的请求头，用于指示其可以理解和处理的内容类型。头部指定一个或多个MIME类型，服务器应该在可能的情况下以其中一种类型响应资源。

For example, a web browser might send an **`Accept`** header like this:

```html

Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
```

This header specifies that the browser can handle HTML documents (**`text/html`**), XHTML documents (**`application/xhtml+xml`**), and XML documents (**`application/xml`**), with a preference for HTML over the other types. The **`q`** parameter after each MIME type specifies a quality value between 0 and 1, with a higher value indicating a higher preference.这个标题指定了浏览器可以处理 HTML 文档 (**`text/html`**), XHTML 文档 (**`application/xhtml+xml`**), 以及 XML 文档 (**`application/xml`**), 优先使用 HTML 类型。每个 MIME 类型后面的 **`q`** 参数指定了一个 0 到 1 之间的质量值，较高的值表示较高的优先级。

In this example, the client indicates that it prefers to receive content in the following order of preference:

1. **`text/html`**
2. **`application/xhtml+xml`**
3. **`application/xml`** with a q-value of 0.9
4. Any other media type (**`/*`**) with a q-value of 0.8

When the server receives this header, it can use this information to determine the best format to send the requested content in, based on what the client can handle and the available formats on the server. If the server cannot provide any of the media types specified in the **`Accept`** header, it may return an HTTP **`406 Not Acceptable`** status code.

If the server can provide a resource in one of the requested MIME types, it will include a **`Content-Type`** header in the response indicating the type of the resource. For example, if the server responds with an HTML document, it might include a **`Content-Type`** header like this:

```html

Content-Type: text/html; charset=utf-8
```

This indicates that the content of the response is an HTML document encoded in UTF-8.

By including an **`Accept`** header in the request, the client can indicate its preferences and capabilities to the server, and the server can respond with an appropriate resource. This allows for flexible and efficient communication between clients and servers over the web.

### The `User-agent` header sent by the HTTP client. What does your browser send?

The **`User-Agent`** header is a request header sent by the HTTP client (such as a web browser or a mobile app) to identify itself to the server. The header contains information about the client software, including the name, version, and operating system.**`User-Agent`** 头是由 HTTP 客户端 (例如 Web 浏览器或移动应用程序) 发送的请求头，用于向服务器标识自身。该头包含有关客户端软件的信息，包括名称、版本和操作系统。

For example, a web browser might send a **`User-Agent`** header like this:

```html

User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/94.0.4606.61 Safari/537.36
```

This header indicates that the browser is Mozilla version 5.0, running on Windows 10 (Win64; x64) with the WebKit rendering engine and the Chrome/94.0.4606.61 browser version.

The **`User-Agent`** header can be used by servers to tailor their responses to the client software, such as by serving different versions of a web page or application based on the client's capabilities or limitations.

***This is my User-Agent:*** 

```jsx
Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML,
like Gecko) Chrome/112.0.0.0 Safari/537.36
```

### How do you encode a path that contains a space in an URL? Which other characters are "special" and need to be treated this way in paths?

To encode a path that contains a space or other special characters in a URL, you can use URL encoding. This involves replacing each special character with a percent sign followed by its ASCII code in hexadecimal format. For example, a **space** is replaced with **`%20`**.

So if you have a path like **`/path with spaces/file.txt`**, you would encode it as **`/path%20with%20spaces/file.txt`** in the URL.

Other special characters that need to be encoded in paths include:

- **`/`**: Used to separate **path** **components**. If you want to include a slash in a path component, you need to encode it as **`%2F`**.
- **`?`**: Used to separate the **path** from the **query** string. If you want to include a question mark in a path component, you need to encode it as **`%3F`**.
- **`#`**: Used to indicate a **fragment identifier**. If you want to include a hash symbol in a path component, you need to encode it as **`%23`**.
- **`%`**: Used to encode **special characters**. If you want to include a percent symbol in a path component, you need to encode it as **`%25`**.

Apart from the space character, several other characters are considered "special" and need to be percent-encoded in URL paths. Some of these characters include:

- **`!`** (exclamation mark): **`%21`**
- **`"`** (double quotes): **`%22`**
- **`$`** (dollar sign): **`%24`**
- **`&`** (ampersand): **`%26`**
- **`'`** (single quote): **`%27`**
- **`(`** (left parenthesis): **`%28`**
- **`)`** (right parenthesis): **`%29`**
- **``** (asterisk): **`%2A`**
- **`+`** (plus sign): **`%2B`**
- **`,`** (comma): **`%2C`**
- **`/`** (forward slash): **`%2F`**
- **`:`** (colon): **`%3A`**
- **`;`** (semicolon): **`%3B`**
- **`<`** (less than): **`%3C`**
- **`=`** (equals sign): **`%3D`**
- **`>`** (greater than): **`%3E`**
- **`?`** (question mark): **`%3F`**
- **`@`** (at sign): **`%40`**
- **`[`** (left square bracket): **`%5B`**
- **`]`** (right square bracket): **`%5D`**
- **`^`** (caret): **`%5E`**
- ``` (backtick): **`%60`**
- **`{`** (left curly brace): **`%7B`**
- **`|`** (pipe): **`%7C`**
- **`}`** (right curly brace): **`%7D`**
- **`~`** (tilde): **`%7E`**

There are many other characters that have special meanings in URLs and need to be encoded in certain contexts, such as query strings and headers. It's generally a good practice to URL encode any characters that might have special meanings, to ensure that they are interpreted correctly by the server and client.

In JavaScript, you can use the **`encodeURIComponent()`** function to automatically encode special characters in a URL path component:

```jsx
const pathComponent = "folder with spaces/file name.txt";
const encodedPathComponent = encodeURIComponent(pathComponent);
console.log(encodedPathComponent);
// Output: "folder%20with%20spaces%2Ffile%20name.txt"

```

### Which web server is the University of Bristol using for `www.bristol.ac.uk`, according to the headers? Read up online on this server and the organisation of the same name that maintains it.

![截屏2023-03-09 15.42.31.png](HTTP%20Exercise%209563abc512d54c37b80bb4ef41f128f6/%25E6%2588%25AA%25E5%25B1%258F2023-03-09_15.42.31.png)

According to the HTTP response headers for **[www.bristol.ac.uk](http://www.bristol.ac.uk/)**, the University of Bristol is using the Apache web server to host its website. The **`Server`** header in the response indicates the server software and version number, as shown below:

```

Server: Apache/2.4.6 (Red Hat Enterprise Linux) OpenSSL/1.0.2k-fips mod_fcgid/2.3.9 PHP/7.2.24
```

**We can check from here:**

![截屏2023-03-09 15.49.40.png](HTTP%20Exercise%209563abc512d54c37b80bb4ef41f128f6/%25E6%2588%25AA%25E5%25B1%258F2023-03-09_15.49.40.png)

**Apache HTTP Server**, commonly known as Apache, is an open-source web server software developed and maintained by the Apache Software Foundation. It was first released in 1995 and has since become the most widely used web server globally, powering a large percentage of websites on the internet.

The Apache Software Foundation (ASF) is a non-profit organization that oversees the development and management of the Apache HTTP Server and many other open-source software projects. It provides support for the Apache community and ensures that the software is freely available under the Apache License, which is a permissive, free software license that allows for the reuse, modification, and distribution of the software.

Apache HTTP Server is known for its flexibility, extensibility, and high-performance capabilities. Some key features of Apache include:

1. **Modularity**: Apache has a modular architecture, which allows you to extend its functionality with various modules or plugins. These modules can provide additional features like SSL/TLS encryption, caching, authentication, or support for programming languages like PHP and Python.
2. **Cross-platform compatibility**: Apache runs on various operating systems, including Unix-based systems (e.g., Linux, macOS), Windows, and others. This cross-platform compatibility makes it suitable for a wide range of server environments.
3. **.htaccess files**: Apache allows you to configure settings on a per-directory basis using .htaccess files. These files enable you to apply settings like URL rewriting, access control, and caching without modifying the main server configuration.
4. **Virtual hosting**: Apache supports virtual hosting, which allows you to serve multiple websites from a single server. You can configure virtual hosts based on domain names or IP addresses, making it easy to manage multiple websites on a shared server.
5. **Security features**: Apache provides various security features like access control, SSL/TLS support for encrypted connections, and protection against common web attacks such as cross-site scripting and SQL injection.

The Apache Software Foundation also manages other popular projects like Apache Tomcat (a Java-based web server and servlet container), Apache Hadoop (a big data processing framework), and Apache Cassandra (a distributed NoSQL database), among many others.

## MCQ questions

1. What is the fragment part of a URL?
    - A. A component that appears at the beginning of a URL
    - B. A component that appears at the end of a URL and is separated from the rest of the URL by a "#" symbol
    - C. A component that appears in the middle of a URL
    - D. A component that appears after the query string in a URL
2. What is the Accept header sent by the HTTP client?
    - A. A request header sent by the HTTP client to identify itself to the server
    - B. A request header sent by the HTTP client to indicate the types of content that it can understand and handle
    - C. A response header sent by the server to indicate the type of content that it is sending
    - D. A response header sent by the server to indicate the status of the request
3. What is the User-Agent header sent by the HTTP client?
    - A. A request header sent by the HTTP client to identify itself to the server
    - B. A request header sent by the HTTP client to indicate the types of content that it can understand and handle
    - C. A response header sent by the server to indicate the type of content that it is sending
    - D. A response header sent by the server to indicate the status of the request
4. Which web server is the University of Bristol using for [www.bristol.ac.uk](http://www.bristol.ac.uk/), according to the headers?
    - A. Nginx
    - B. Apache
    - C. IIS
    - D. Tomcat
5. What is URL encoding?
    - A. The process of converting a URL to binary format
    - B. The process of converting a URL to a more compact representation
    - C. The process of replacing special characters in a URL with their ASCII code in hexadecimal format
    - D. The process of encrypting a URL to make it more secure
6. What is the purpose of the fragment part of a URL?
    - A. To identify the server that should handle the request
    - B. To specify the port number that should be used for the connection
    - C. To identify a specific section or location within the target resource
    - D. To specify the HTTP method that should be used for the request
7. What is the purpose of the User-Agent header sent by the HTTP client?
    - A. To identify the server that should handle the request
    - B. To indicate the types of content that the client can understand and handle
    - C. To specify the port number that should be used for the connection
    - D. To identify the client software, including the name, version, and operating system
8. What is the most widely used web server software?
    - A. IIS
    - B. Nginx
    - C. Apache
    - D. Tomcat
9. Which organisation maintains the Apache HTTP Server?
    - A. The Apache Software Foundation
    - B. The Mozilla Foundation
    - C. The Linux Foundation
    - D. The Free Software Foundation
10. What is the purpose of the quality value (q-value) in the Accept header?
    - A. To indicate the types of content that the client can understand and handle
    - B. To specify the order of preference for the listed media types
    - C. To specify the encoding format for the content
    - D. To indicate the size of the content in bytes

Answers:

1. B
2. B
3. A
4. B
5. C
6. C
7. D
8. C
9. A
10. B

# 1.4  A server in JAVA

## Compile and run

Make sure you have java and maven installed as we did earlier in the unit. On alpine, you need to do the following if you have not done so already:

- Install the packages `openjdk17` and `maven`. (sudo apk add…..)
- Add the line `export PATH="$PATH:/usr/lib/jvm/java-17-openjdk/bin/"` to your `~/.profile` file. (nano ~/.profile)
- Run `source ~/.profile`.

Clone the repository `git@github.com:cs-uob/COMSM0085` if you have not done so already, and navigate to the folder `code/server01`. In this folder, run `mvn spring-boot:run` to compile and run the sample application. The first time you do this, it might download lots of files.

This runs a web server on port 8000.

![截屏2023-03-09 19.39.35.png](HTTP%20Exercise%209563abc512d54c37b80bb4ef41f128f6/%25E6%2588%25AA%25E5%25B1%258F2023-03-09_19.39.35.png)

## Explore the application

The `pom.xml` file tells maven that this is a spring boot project, and what the project is called (`softwaretools.server01`).

![截屏2023-03-09 19.41.15.png](HTTP%20Exercise%209563abc512d54c37b80bb4ef41f128f6/%25E6%2588%25AA%25E5%25B1%258F2023-03-09_19.41.15.png)

Under `src/main/resources` you find two files. First, `application.properties` which is a spring file configured to run on port 8000 (the default would otherwise be 8080). Secondly, a HTML file that the application can serve.

当我们进入文件nano `[application.properties](http://application.properties)` 时，发现里面只有一行

![截屏2023-03-09 19.43.42.png](HTTP%20Exercise%209563abc512d54c37b80bb4ef41f128f6/%25E6%2588%25AA%25E5%25B1%258F2023-03-09_19.43.42.png)

Under `src/main/java`/softwaretools/server01 is the source code. This is only two files, but of course the whole spring framework is active when the application runs. `Server01Application`is the main class, but this just contains boilerplate code for now.

![截屏2023-03-09 19.46.22.png](HTTP%20Exercise%209563abc512d54c37b80bb4ef41f128f6/%25E6%2588%25AA%25E5%25B1%258F2023-03-09_19.46.22.png)

`Controller.java` is the interesting one: in application development, *Model - View - Controller*
 is one of several patterns to structure an application, where a *Controller*
 is a piece of code that does the heavy lifting part, for example replying to a HTTP request.

![截屏2023-03-09 19.56.02.png](HTTP%20Exercise%209563abc512d54c37b80bb4ef41f128f6/%25E6%2588%25AA%25E5%25B1%258F2023-03-09_19.56.02.png)

Spring works with annotations, special classes whose name begins with an `@` sign. When the server starts, spring scans all files for annotations and sets up code to deal with them. Here we can see:

- `@SpringBootApplication` (on the `Server01Application` class) tells spring that this is the main file to run.
- `@RestController` tells spring that this class contains methods to deal with HTTP requests. It is so named because spring has libraries to make implementing the REST principles particularly easy.
- `@AutoWired` on a field tells spring that this field is spring's responsibility to set up when the application starts. The `ResourceLoader` is part of spring and lets you access files in `src/main/resources`.
- `@GetMapping(PATH)` tells spring that this method should be called to reply to a HTTP GET request for the provided path (there is of course also a `@PostMapping` and so on).

The `mainPage` method, which is called when you load `localhost:8000`, shows the basic way to reply to a HTTP request: set up any headers you need - in this case the content type - and return a `ResponseEntity` taking three parameters: the HTTP body of the response to return (this will be shown in your browser), the HTTP headers to set, and the response code which is 200 (OK) here.

The `htmlPage` method replies to requests for `localhost:8000/html`. Here we want to serve a file, so we use the resource loader to get it from the classpath which includes the `src/main/resources` folder (or rather, the version of it that ends up in the compiled JAR file). It also shows a second way to create a `ResponseEntity` using the *builder* pattern.

## Exercise:

Compile and run the application, and test both `localhost:8000` an `localhost:8000/html` in your browser. Observe both the headers in the developer tools, and the log messages that spring prints out for each request.

1. cd ~/COMSM0085/code/server01  → mvn clean compile → mvn spring-boot:run

⬇️ localhost:8000

![截屏2023-03-09 20.04.15.png](HTTP%20Exercise%209563abc512d54c37b80bb4ef41f128f6/%25E6%2588%25AA%25E5%25B1%258F2023-03-09_20.04.15.png)

⬇️`localhost:8000/html`

![截屏2023-03-09 20.04.43.png](HTTP%20Exercise%209563abc512d54c37b80bb4ef41f128f6/%25E6%2588%25AA%25E5%25B1%258F2023-03-09_20.04.43.png)

1. Add a method that replies to requests for `localhost:8000/bad` with a HTTP `404 NOT FOUND` error. The body of the page can be a simple string with a message of your choice. Stop and restart the application, and check that you get the correct error message when you try and open this page.

1. cd ~/COMSM0085/code/server01/src/main/java/softwaretools/server01
2. nano **Controller.java**
3. add the method in Controller.java.

![截屏2023-03-09 20.14.53.png](HTTP%20Exercise%209563abc512d54c37b80bb4ef41f128f6/%25E6%2588%25AA%25E5%25B1%258F2023-03-09_20.14.53.png)

```java
@GetMapping("/bad")
public ResponseEntity<String> notFound() {
HttpHeaders headers = new HttpHeaders();
headers.setContentType(MediaType.TEXT_PLAIN);
String body = "Page not found";
return new ResponseEntity<>(body, headers, HttpStatus.NOT_FOUND);
}
```

And remember to add these lines at the beginning:

```java
import org.springframework.http.HttpStatus;
import org.springframework.http.MediaType;
```

1. *go back and re-run it*  

(cd ~/COMSM0085/code/server01  → mvn clean compile → mvn spring-boot:run)

1. *Then we can check the [localhost](http://localhost):8000/bad*

![截屏2023-03-09 20.27.31.png](HTTP%20Exercise%209563abc512d54c37b80bb4ef41f128f6/%25E6%2588%25AA%25E5%25B1%258F2023-03-09_20.27.31.png)

Some conclusion:

- The exercise involves creating a web server using Java and the Spring Boot framework.
- Before running the application, make sure to install Java and Maven and add the Java path to the system PATH variable.
- The application runs on port 8000 by default and serves an HTML file.
- The source code for the application is in the **`src/main/java`** folder, which contains only two files: **`Server01Application.java`** and **`Controller.java`**.
- **`Controller.java`** is the main class that handles HTTP requests using annotations such as **`@RestController`**, **`@Autowired`**, and **`@GetMapping`**.
- There are two methods in **`Controller.java`**: **`mainPage()`** and **`htmlPage()`**. The former responds to requests to the root URL (**`/`**) and the latter responds to requests to **`/html`**.
- To add a new method to handle requests to **`/bad`** with a 404 error, you can add a new method to **`Controller.java`** with a **`@GetMapping("/bad")`** annotation and return a **`ResponseEntity`** object with a 404 status code and a message in the body.

### **MCQ Questions:**

1. What is the purpose of the **`pom.xml`** file in a Spring Boot project?
    - A. To specify the version of Java to use.
    - B. To specify the name of the main class.
    - C. To specify the project name and other configuration options.
    - D. To specify the dependencies and plugins for the project.
2. What is the purpose of the **`@SpringBootApplication`** annotation in the **`Server01Application`** class?
    - A. To specify the URL path for the HTTP server.
    - B. To indicate that this is the main class for the Spring Boot application.
    - C. To specify the HTTP headers to include in the response.
    - D. To indicate the type of HTTP request to handle.
3. What is the purpose of the **`@RestController`** annotation in the **`Controller`** class?
    - A. To specify the URL path for the HTTP server.
    - B. To indicate that this class contains methods to deal with HTTP requests.
    - C. To specify the HTTP headers to include in the response.
    - D. To indicate the type of HTTP request to handle.
4. What is the purpose of the **`@Autowired`** annotation in the **`Controller`** class?
    - A. To specify the URL path for the HTTP server.
    - B. To indicate that this class contains methods to deal with HTTP requests.
    - C. To specify the HTTP headers to include in the response.
    - D. To indicate that this field is managed by Spring and should be initialized automatically.
5. What is the purpose of the **`@GetMapping`** annotation in the **`Controller`** class?
    - A. To specify the URL path for the HTTP server.
    - B. To indicate that this class contains methods to deal with HTTP requests.
    - C. To specify the HTTP headers to include in the response.
    - D. To indicate the type of HTTP request to handle.
6. What is the purpose of the **`ResponseEntity`** class?
    - A. To specify the URL path for the HTTP server.
    - B. To indicate that this class contains methods to deal with HTTP requests.
    - C. To represent an HTTP response, including the body, headers, and status code.
    - D. To indicate the type of HTTP request to handle.
7. What is the purpose of the **`404 NOT FOUND`** error code?
    - A. To indicate that the server encountered an error while processing the request.
    - B. To indicate that the requested resource was not found on the server.
    - C. To indicate that the client should try the request again later.
    - D. To indicate that the client is not authorized to access the requested resource.
8. What is the purpose of the **`@GetMapping("/bad")`** annotation in the **`Controller`** class?
    - A. To specify the URL path for the HTTP server.
    - B. To indicate that this method handles requests to the **`/bad`** URL.
    - C. To specify the HTTP headers to include in the response.
    - D. To indicate the type of HTTP request to handle.
    
    ### Answers:
    
    1. D 
    2. B
    3. B
    4. D
    5. D
    6. C
    7. B
    8. B