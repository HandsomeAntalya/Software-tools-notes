# HTTP (lecture)

HTTP is a request-response protocol that defines how clients and servers communicate with each other. The protocol includes headers, methods, and status codes to facilitate this communication. Clients send requests to servers, and servers send back responses. The most commonly used methods are GET, POST, PUT, DELETE, and HEAD. Cookies and sessions are used to maintain user state and track user behavior. By adhering to the rules and conventions of the HTTP protocol, web clients and servers can effectively exchange information and provide a seamless browsing experience for users.

# 1.1 HTTP Slide

HTTP (Hypertext Transfer Protocol **超文本传送协议**) is an application protocol for distributed, collaborative, and hypermedia information systems. It is the foundation of data communication for the World Wide Web. (Text has some markup on it.) HTTP（超文本传输协议）是一个用于分布式、协作式和超媒体信息系统的应用协议。它是万维网的数据通信的基础。(文本上有一些标记)。

![截屏2023-04-21 19.36.01.png](HTTP%20(lecture)%20acfbb5bb04f64d33966ea1ca451eb51f/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_19.36.01.png)

![截屏2023-04-21 19.36.22.png](HTTP%20(lecture)%20acfbb5bb04f64d33966ea1ca451eb51f/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_19.36.22.png)

Request response protocol:

In the context of HTTP, "protocol" refers to a set of rules and conventions that govern communication between web clients (like web browsers) and web servers over the internet or other networks. HTTP stands for HyperText Transfer Protocol, and it is the foundation of data communication on the World Wide Web.在HTTP的上下文中，"协议 "指的是一套规则和惯例，用于管理网络客户（如网络浏览器）和网络服务器在互联网或其他网络上的通信。HTTP是超文本传输协议的缩写，它是万维网上数据通信的基础。

A protocol, in general, is a system of rules and procedures that define how data is transmitted, formatted, and processed between devices or software applications. In the case of HTTP, the protocol specifies how requests and responses should be structured, as well as the methods and status codes that are used to facilitate communication between clients and servers. 一般来说，协议是一个规则和程序系统，它定义了数据如何在设备或软件应用程序之间传输、格式化和处理。就HTTP而言，协议规定了请求和响应的结构，以及用于促进客户和服务器之间通信的方法和状态代码。

HTTP is a request-response protocol, meaning that clients send requests to servers, and servers send back responses. The protocol defines the structure of these requests and responses, including headers, methods (like GET, POST, PUT, DELETE), and status codes (like 200 OK, 404 Not Found, 500 Internal Server Error). By adhering to the rules and conventions of the HTTP protocol, web clients and servers can effectively exchange information and provide a seamless browsing experience for users. HTTP是一个请求-响应协议，意味着客户向服务器发送请求，而服务器则发送响应。该协议定义了这些请求和响应的结构，包括标题、方法（如GET、POST、PUT、DELETE）和状态代码（如200 OK、404 Not Found、500 Internal Server Error）。通过遵守HTTP协议的规则和惯例，网络客户和服务器可以有效地交换信息，为用户提供无缝的浏览体验。

![截屏2023-04-21 19.39.21.png](HTTP%20(lecture)%20acfbb5bb04f64d33966ea1ca451eb51f/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_19.39.21.png)

Client server relationship : client is the one making the request and server is the one response the request. 

In the context of HTTP, the client and server are two key components that interact with each other to facilitate the exchange of information on the internet. Here's an overview of how they work together:

1. Client 客户端: The client is typically a web browser (like Chrome, Firefox, or Safari) or any application that makes HTTP requests to web servers. The client's main function is to send requests to the server and display the server's response, which usually contains the resources needed to render a web page (like HTML, CSS, JavaScript, images, etc.).： 客户端通常是一个网络浏览器（如Chrome、Firefox或Safari）或任何向网络服务器发出HTTP请求的应用程序。客户端的主要功能是向服务器发送请求并显示服务器的响应，通常包含渲染网页所需的资源（如HTML、CSS、JavaScript、图像等）。
2. Server 服务器: The server is a computer or software application that hosts websites and listens for incoming HTTP requests from clients. When a server receives a request, it processes the request, retrieves the requested resources, and sends them back to the client in an HTTP response. 服务器是一个计算机或软件应用程序，它承载网站并监听来自客户端的HTTP请求。当服务器收到一个请求时，它会处理该请求，检索所请求的资源，并在HTTP响应中把它们送回给客户。

The basic process of client-server interaction in HTTP is as follows:

1. The client initiates an HTTP request by entering a URL (Uniform Resource Locator) in the browser's address bar or clicking a link on a web page. This request typically includes information such as the HTTP method (e.g., GET, POST), the requested URL, headers (containing additional information about the client and the request), and sometimes a message body (e.g., when submitting a form using POST).客户端通过在浏览器的地址栏中输入一个URL（统一资源定位器）或点击网页上的一个链接来发起一个HTTP请求。这个请求通常包括HTTP方法（如GET、POST）、被请求的URL、标题（包含关于客户端和请求的额外信息）等信息，有时还包括一个消息体（例如，当使用POST提交表单时）。
2. The request is sent over the internet or another network to the server that hosts the requested resource. The server processes the request, which may involve querying databases, executing server-side scripts, or performing other operations to generate the appropriate response.该请求通过互联网或其他网络被发送到托管所请求资源的服务器。服务器处理请求，这可能涉及查询数据库、执行服务器端脚本或执行其他操作以产生适当的响应。
3. The server constructs an HTTP response, which includes a status code (indicating the result of the request, such as 200 OK, 404 Not Found, etc.), headers (providing metadata about the response), and a message body (containing the requested resource or an error message).服务器构建一个HTTP响应，其中包括一个状态代码（表示请求的结果，如200 OK、404 Not Found等）、头信息（提供关于响应的元数据）和一个消息体（包含请求的资源或错误信息）。
4. The server sends the HTTP response back to the client.服务器将HTTP响应发回给客户端。
5. The client receives the response, processes it, and displays the content to the user. If the response contains an HTML document, the browser will render the web page by interpreting the HTML, CSS, and JavaScript content. If additional resources are required (e.g., images, stylesheets, or scripts), the client may make additional HTTP requests to the server to retrieve them.客户端接收响应，处理它，并将内容显示给用户。如果响应包含一个HTML文档，浏览器将通过解释HTML、CSS和JavaScript内容来渲染网页。如果需要额外的资源（如图像、样式表或脚本），客户端可能会向服务器发出额外的HTTP请求以获取这些资源。
6. Once all the necessary resources have been received, the client renders the complete web page for the user to interact with. 一旦收到所有必要的资源，客户端就会渲染完整的网页，供用户交互使用。

Throughout this process, the client and server adhere to the rules and conventions of the HTTP protocol to ensure reliable and consistent communication.

[data:image/svg+xml,%3csvg%20xmlns=%27http://www.w3.org/2000/svg%27%20version=%271.1%27%20width=%2738%27%20height=%2738%27/%3e](data:image/svg+xml,%3csvg%20xmlns=%27http://www.w3.org/2000/svg%27%20version=%271.1%27%20width=%2738%27%20height=%2738%27/%3e)

![截屏2023-04-21 19.39.36.png](HTTP%20(lecture)%20acfbb5bb04f64d33966ea1ca451eb51f/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_19.39.36.png)

req = read()  → reads request from socket. (blocking call, server waits for the message)

This code snippet is a simple representation of a server's main loop that continuously listens for incoming requests, processes them, and sends back responses. The loop runs indefinitely, as indicated by the **`while(1)`** statement. Here's a step-by-step explanation of the code:

1. **`while(1)`**: This is a while loop that runs indefinitely because the condition (1) is always true. It's a common way to create an infinite loop in programming languages.
2. **`req = read();`**: This line represents a function call to **`read()`**, which presumably listens for incoming client requests and returns the received request. The received request is stored in the **`req`** variable.
3. **`resp = serve(req);`**: This line calls the **`serve()`** function, which takes the received request (**`req`**) as an argument and processes it. This function is responsible for handling the request, such as retrieving resources, executing server-side scripts, or querying databases. The result of the processing is stored in the **`resp`** variable, which represents the server's response to the client.
4. **`write(resp);`**: This line calls the **`write()`** function, which takes the response (**`resp`**) as an argument and sends it back to the client.

This code snippet is a simple representation of how a server works: continuously reading incoming requests, processing them, and sending responses back to the clients. In practice, real-world server applications would be more complex and often involve multithreading or asynchronous processing to handle multiple client requests concurrently.

![截屏2023-04-21 19.44.37.png](HTTP%20(lecture)%20acfbb5bb04f64d33966ea1ca451eb51f/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_19.44.37.png)

Get / HTTP 1.1 

In the context of HTTP, headers, request headers, and response headers are important components of the communication between a client (usually a web browser) and a server. Here's an explanation of each term:

1. **Headers:** Headers are key-value pairs that convey metadata (additional information) about an HTTP request or response. Headers help the client and server understand specific details about the request or response, such as content type, encoding, cache policies, and more.头信息是传达关于HTTP请求或响应的元数据（额外信息）的键值对。头信息帮助客户端和服务器了解关于请求或响应的具体细节，如内容类型、编码、缓存策略等。
2. **Request headers:** Request headers are headers included in an HTTP request sent by the client to the server. They provide information about the client, the requested resource, and the desired response format, among other details. Some common request headers are:请求头是由客户发送给服务器的HTTP请求中包含的头。它们提供关于客户端、所请求的资源和所希望的响应格式等细节的信息。一些常见的请求头是：
    - **`Accept`**: Specifies the content types that the client can handle in the response.
    - **`Accept-Encoding`**: Indicates the compression algorithms the client supports.
    - **`Authorization`**: Contains credentials for authentication and authorization.
    - **`Host`**: Specifies the domain name and port number of the server the client is sending the request to.
    - **`User-Agent`**: Identifies the client software (e.g., browser) and provides information about the client's operating system and device.
3. **Response headers**: Response headers are headers included in an HTTP response sent by the server to the client. They provide information about the server, the response content, and any additional instructions for the client. Some common response headers are: 响应头是由服务器发送给客户端的HTTP响应中包含的头。它们提供了关于服务器、响应内容和对客户端的任何额外指示的信息。一些常见的响应头是：
    - **`Content-Type`**: Specifies the media type of the response body (e.g., text/html, application/json).
    - **`Content-Encoding`**: Indicates the compression algorithm used for the response body.
    - **`Content-Length`**: Specifies the length (in bytes) of the response body.
    - **`Cache-Control`**: Provides caching directives for the client (e.g., how long the client can store the response in its cache).
    - **`Set-Cookie`**: Instructs the client to store cookies, which can be used for maintaining state and tracking purposes.

When a client sends an HTTP request to a server, it includes request headers to provide additional information about the request. The server then processes the request and sends an HTTP response back to the client, including response headers with additional information about the response. By understanding and using headers, both clients and servers can communicate more effectively and efficiently.

![截屏2023-04-21 19.49.43.png](HTTP%20(lecture)%20acfbb5bb04f64d33966ea1ca451eb51f/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_19.49.43.png)

get : a resource from another server.

![截屏2023-04-21 19.50.38.png](HTTP%20(lecture)%20acfbb5bb04f64d33966ea1ca451eb51f/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_19.50.38.png)

most usage : get or post

head request : to check the size of file if you went to download it 

1. **`GET`**: The GET method requests a representation of the specified resource from the server. It is used for retrieving data without modifying it. The requested data is typically returned in the response body (e.g., an HTML page, an image, or a JSON object). GET requests should be idempotent, meaning that making the same request multiple times should have the same effect as making it once. GET方法从服务器上请求一个指定资源的表示。它用于检索数据，而不对其进行修改。所请求的数据通常在响应体中返回（例如，一个HTML页面，一个图像，或一个JSON对象）。GET请求应该是空闲的，也就是说，多次提出相同的请求应该与一次提出相同的效果。
2. **`HEAD`**: The HEAD method is similar to the GET method, but it requests only the headers of the specified resource, not the actual data (i.e., the response body is empty). This method is useful when you want to retrieve metadata about a resource, such as its content type, size, or last modification date, without actually downloading the resource itself. HEAD方法类似于GET方法，但它只请求指定资源的头文件，而不是实际数据（即响应体是空的）。当你想检索一个资源的元数据时，比如它的内容类型、大小或最后修改日期，而不需要实际下载资源本身，这种方法很有用。
3. **`POST`**: The POST method submits data to the server to be processed, typically in the form of a new resource creation or updating an existing resource. The data to be submitted is included in the request body. The server processes the data and sends an appropriate response, which may include a status code (e.g., 201 Created for successful resource creation) and additional information about the result of the operation. POST requests are not idempotent, meaning that making the same request multiple times may have different effects. POST方法将数据提交给服务器进行处理，通常以创建新资源或更新现有资源的形式。要提交的数据被包含在请求正文中。服务器处理数据并发送一个适当的响应，其中可能包括一个状态代码（例如，201创建成功的资源）和关于操作结果的额外信息。POST请求不是等效的，这意味着多次进行相同的请求可能会有不同的效果。
4. **`PUT`**: The PUT method updates an existing resource on the server with the data provided in the request body or creates a new resource if the specified resource does not exist. This method is idempotent, meaning that making the same request multiple times should have the same effect as making it once. Unlike POST, which can be used for a variety of purposes, PUT is specifically meant for updating or creating resources.PUT方法用请求正文中提供的数据更新服务器上的现有资源，如果指定的资源不存在，则创建一个新资源。这个方法是等效的，这意味着多次发出相同的请求和一次发出相同的效果。与POST不同的是，PUT可以用于各种目的，它是专门用于更新或创建资源的。 
5. **`DELETE`**: The DELETE method requests the server to delete the specified resource. If the deletion is successful, the server typically returns a 204 No Content status code to indicate that the operation was successful and no further information is available. DELETE requests should be idempotent, meaning that making the same request multiple times should have the same effect as making it once.DELETE方法请求服务器删除指定的资源。如果删除成功，服务器通常会返回一个204 No Content状态代码，表示操作成功，没有进一步的信息可用。DELETE请求应该是等效的，也就是说，多次发出相同的请求和一次发出相同的效果。

These HTTP methods help define the various actions that can be performed on resources on the server. By using different methods, clients can request, submit, update, or delete data in a clear and standardized manner, which is essential for effective communication between clients and servers.

![截屏2023-04-21 19.53.07.png](HTTP%20(lecture)%20acfbb5bb04f64d33966ea1ca451eb51f/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_19.53.07.png)

![截屏2023-04-21 19.53.26.png](HTTP%20(lecture)%20acfbb5bb04f64d33966ea1ca451eb51f/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_19.53.26.png)

Most commonly used are 200 ok, but 201 means request has been created. 

The HTTP response code 204 No Content indicates that the request was successful, but there is no response body to send back. This is often used for successful DELETE requests or PUT/POST requests that do not require a response body.

4xx and 5xx are error code, the difference is 4xx is client error, 5xx codes are server error itself. 

![截屏2023-04-21 19.55.16.png](HTTP%20(lecture)%20acfbb5bb04f64d33966ea1ca451eb51f/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_19.55.16.png)

content-type:  format of response body is going to be. 

```jsx
wget -S -O - [http://bristol.ac.uk](http://bristol.ac.uk/) 2>&1 | head -31
```

- **`wget`**: This is a command-line utility to download files and web pages from the internet.
- **`S`**: This option tells **`wget`** to display server response headers.
- **`O -`**: This option tells **`wget`** to direct the downloaded content to the standard output (the **``** character means "standard output" in this context).
- **`http://bristol.ac.uk`**: This is the URL of the webpage you want to download.
- **`2>&1`**: This part of the command redirects the standard error (file descriptor 2) to the standard output (file descriptor 1), merging both outputs. This is useful because **`wget`** prints server response headers to standard error by default. 命令的这一部分将标准错误（文件描述符2）重定向到标准输出（文件描述符1），合并两个输出。这很有用，因为wget默认将服务器响应头打印到标准错误。
- **`|`**: This symbol, called a pipe, directs the output of the previous command (in this case, **`wget`**) as input to the next command (in this case, **`head`**).
- **`head -31`**: This command prints the first 31 lines of the input it receives. In this case, it will print the first 31 lines of the output from the **`wget`** command, which includes the server response headers.

This command will download the content of the Bristol University webpage (**[http://bristol.ac.uk](http://bristol.ac.uk/)**), display the server response headers, and print the first 31 lines of the output, which should include the headers.

![截屏2023-04-21 19.59.49.png](HTTP%20(lecture)%20acfbb5bb04f64d33966ea1ca451eb51f/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_19.59.49.png)

IP Address is port 80 : standard port number. 

![截屏2023-04-21 20.01.21.png](HTTP%20(lecture)%20acfbb5bb04f64d33966ea1ca451eb51f/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_20.01.21.png)

Cookies

![截屏2023-04-21 20.03.02.png](HTTP%20(lecture)%20acfbb5bb04f64d33966ea1ca451eb51f/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_20.03.02.png)

don’t need to remember anything. 

![截屏2023-04-21 20.03.18.png](HTTP%20(lecture)%20acfbb5bb04f64d33966ea1ca451eb51f/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_20.03.18.png)

can remember something …

A cookie, in the context of web browsing and HTTP, is a small piece of data stored by a web browser on the user's device. Cookies are sent by a web server to the browser and then returned unchanged by the browser each time it subsequently accesses that server. Cookies serve a variety of purposes, such as: 在网络浏览和HTTP的背景下，cookie是网络浏览器存储在用户设备上的一小段数据。Cookie由网络服务器发送至浏览器，然后在每次访问该服务器时由浏览器返回，不作任何改动。Cookies有多种用途，如:

1. **Session management**会话管理: Cookies can store information about a user's session, such as login credentials or items in a shopping cart. This helps maintain a consistent user experience as they navigate through a website. Cookies可以存储有关用户会话的信息，如登录凭证或购物车中的物品。这有助于在用户浏览网站的过程中保持一致的用户体验。
2. **Personalization** 个人化: Cookies can store user preferences, such as language settings, theme selections, or other customizations. This allows websites to remember a user's preferences and tailor the content and appearance of the site accordingly. Cookies可以存储用户的偏好，如语言设置、主题选择或其他定制。这使得网站能够记住用户的偏好，并相应地调整网站的内容和外观。
3. **Tracking**追踪:  Cookies can be used to track user behavior on a website, such as the pages they visit, the time spent on each page, and the links they click. This information can be used for analytics, targeted advertising, or other marketing purposes.  Cookies可用于跟踪用户在网站上的行为，如他们访问的页面、在每个页面上花费的时间以及他们点击的链接。这些信息可用于分析、定向广告或其他营销目的。

A cookie consists of a name, a value, and some optional attributes, such as the domain, path, expiration date, and security flags. When a server sends an HTTP response to a browser, it can include a **`Set-Cookie`** header, which instructs the browser to store the cookie on the user's device. The browser then sends the cookie back to the server in the **`Cookie`** header of subsequent HTTP requests.

Although cookies have many legitimate uses, they can also raise privacy concerns because they can be used to track user behavior across websites and build detailed profiles of user activities. As a result, many jurisdictions have implemented laws and regulations governing the use of cookies and requiring websites to inform users about their cookie policies and obtain user consent before setting cookies.

![截屏2023-04-21 20.04.24.png](HTTP%20(lecture)%20acfbb5bb04f64d33966ea1ca451eb51f/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_20.04.24.png)

Sessions, in the context of web applications and cookies, are a way to maintain a consistent user experience by preserving the user's state as they navigate through a website. When a user logs in, submits a form, or adds items to a shopping cart, the web application needs to remember this information across different pages and requests. Sessions are a server-side mechanism to store this information, while cookies are used on the client-side (in the web browser) to maintain a reference to the associated server-side session. 会话，在网络应用程序和cookies的背景下，是一种通过保存用户在网站上浏览时的状态来保持一致的用户体验的方法。当用户登录、提交表格或向购物车添加物品时，网络应用需要在不同的页面和请求中记住这些信息。会话是一种服务器端的机制，用于存储这些信息，而cookies则用于客户端（在网络浏览器中），以保持对相关服务器端会话的引用。

When a user visits a website that uses sessions, the server creates a unique session identifier (session ID) for that user. This session ID is then sent to the client's browser and stored as a cookie. The server can associate various data with this session ID, such as login status, user preferences, or shopping cart contents. 当用户访问一个使用会话的网站时，服务器为该用户创建一个独特的会话标识符（会话ID）。然后，这个会话ID被发送到客户的浏览器，并作为一个cookie存储。服务器可以将各种数据与这个会话ID联系起来，如登录状态、用户偏好或购物车内容。

With each subsequent request the user makes to the website, the browser sends the session ID cookie back to the server. The server can then use the session ID to look up the stored session data and maintain the user's state across requests. This allows the server to remember the user's actions and preferences as they navigate the website. 在用户向网站提出的每个后续请求中，浏览器都会将会话ID cookie送回服务器。然后，服务器可以使用会话ID来查询存储的会话数据，并在不同的请求中保持用户的状态。这允许服务器在用户浏览网站时记住他们的行动和偏好。

When the user logs out or closes the browser, the session can be terminated on the server-side, and the session cookie can be removed from the client's browser. 当用户注销或关闭浏览器时，会话可以在服务器端终止，并且会话cookie可以从客户的浏览器中删除。

It's important to note that sessions and cookies are different concepts, but they work together to maintain the user's state in a web application. Sessions are a server-side mechanism for storing user data, while cookies are a client-side mechanism for persisting the session ID and maintaining a reference to the associated server-side session. 需要注意的是，会话和cookie是不同的概念，但它们一起工作以维护用户在网络应用中的状态。会话是一种存储用户数据的服务器端机制，而cookie是一种客户端机制，用于持久化会话ID并维护对相关服务器端会话的引用。

## Differences between cookies and sessions:

Cookies and sessions are both mechanisms used to store and manage user-specific information in web applications, but they serve different purposes and are stored in different locations.

Cookie和session是用于在web应用程序中存储和管理用户特定信息的机制，但它们具有不同的目的并存储在不同的位置。

Cookies:

1. Cookies are small pieces of data that are stored on the client-side, in the user's browser.Cookie是存储在客户端，即用户的浏览器中的小数据片段。
2. Cookies are sent with every HTTP request to the server, allowing the server to recognize the user and maintain user-specific information.Cookie与每个HTTP请求一起发送到服务器，允许服务器识别用户并维护用户特定信息。
3. Cookies have an expiration time and can be set to persist across multiple visits to a website.Cookie具有过期时间，并且可以设置为在多次访问网站时持久存在。
4. Cookies can be used to store a variety of data, such as login credentials, user preferences, or tracking data.Cookie可用于存储各种数据，例如登录凭据、用户首选项或跟踪数据。
5. Cookies are limited in size, typically up to 4KB.Cookie的大小有限，通常为4KB。

Sessions:

1. Sessions are used to store and manage user-specific data on the server-side.会话用于在服务器端存储和管理特定于用户的数据。
2. Sessions maintain the user's state across a series of requests from the same user.会话在同一用户的一系列请求之间维护用户的状态。
3. Session data is stored on the server, and the user is associated with a session through a session ID.会话数据存储在服务器上，用户通过会话ID关联到会话。
4. The session ID can be stored in a cookie or passed in the URL, allowing the server to retrieve the corresponding session data when needed.会话ID可以存储在cookie中或通过URL传递，允许服务器在需要时检索相应的会话数据。
5. Sessions have a timeout period, after which they expire and are no longer available.会话有一个超时期，在此之后它们会过期并且不再可用。

In summary, cookies store user-specific data on the client-side (browser), while sessions maintain user-specific data on the server-side. Cookies are sent with every HTTP request, while session data is accessed on the server using a session ID that can be stored in a cookie or passed through the URL.

![截屏2023-04-21 20.05.45.png](HTTP%20(lecture)%20acfbb5bb04f64d33966ea1ca451eb51f/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_20.05.45.png)

to track you activity. 

## **Multiple Choice Questions**

1. Which HTTP method is used to submit data to the server for processing?
    
    
    - A. GET
    - B. PUT
    - C. POST
    - D. DELETE
    
2. Which HTTP method is idempotent?
    - A. GET
    - B. POST
    - C. DELETE
    - D. Both A and C
    
3. What status code is typically returned by the server after a successful resource creation using POST?
    - A. 200 OK
    - B. 201 Created
    - C. 204 No Content
    - D. 404 Not Found
    
4. What is the purpose of cookies in HTTP?
    - A. To store user preferences
    - B. To track user behavior
    - C. To manage user sessions
    - D. All of the above
    
5. Which HTTP response code indicates a client-side error?
    - A. 200 OK
    - B. 201 Created
    - C. 404 Not Found
    - D. 500 Internal Server Error
    
6. What is the purpose of sessions in web applications?
    - A. To store user preferences
    - B. To track user behavior
    - C. To manage user authentication
    - D. To maintain user state
    
7. Which HTTP response code indicates a successful request with no response body?
    - A. 200 OK
    - B. 201 Created
    - C. 204 No Content
    - D. 404 Not Found
    
8. Which HTTP method is used to update an existing resource on the server?
    - A. GET
    - B. PUT
    - C. POST
    - D. DELETE
    
9. Which HTTP response code indicates a successful request with a response body?
    - A. 200 OK
    - B. 201 Created
    - C. 204 No Content
    - D. 404 Not Found
    
10. What is the difference between cookies and sessions in web applications?
    - A. Cookies are server-side, while sessions are client-side
    - B. Cookies store user data, while sessions maintain user state
    - C. Cookies are used for tracking user behavior, while sessions are used for session management
    - D. Cookies and sessions are the same thing
    

**Answer Key**

1. C
2. D
3. B
4. D
5. C
6. D
7. C
8. B
9. A
10. B

(About question 10, answer C)

The statement "C. Cookies are used for tracking user behavior, while sessions are used for session management" is not entirely wrong, but it does not provide a comprehensive comparison between cookies and sessions.

Cookies can be used for tracking user behavior, but their primary purpose is to store user-specific data on the client-side. This data can include user preferences, login credentials, and other information that helps maintain user state across requests.

On the other hand, sessions are primarily used for managing user state on the server-side during a series of requests. They can also store user-specific data, but the main focus is on maintaining the user's state between requests.

While both cookies and sessions can be used for managing user state and storing data, they have different storage locations (client-side for cookies and server-side for sessions) and are used in different scenarios based on their specific advantages and limitations.