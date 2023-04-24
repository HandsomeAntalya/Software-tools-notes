# URLs (lecture)

A URL (Uniform Resource Locator) is a standardized address format used to locate resources on the internet. It consists of several components, including scheme, domain name, subdomain, port number, path, query string, and fragment identifier. A URI (Uniform Resource Identifier) is a more general term used to identify a resource, either by location (like a URL) or by name (like a URN, Uniform Resource Name). REST (Representational State Transfer) is an architectural style for designing networked applications that follows a set of constraints and principles aimed at creating scalable, maintainable, and high-performing web services. RESTful APIs typically use HTTP as the transport protocol and rely on standard HTTP methods to perform CRUD (Create, Read, Update, Delete) operations on resources.

![截屏2023-04-21 20.36.22.png](URLs%20(lecture)%201301a3867c8c44c79c48b9915a48dfd4/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_20.36.22.png)

A URL (Uniform Resource Locator) is a standardized address format used to locate resources on the internet. It serves as a reference to a specific web page, file, or other resource, and provides all the information needed for a web browser or other client to request and access that resource.

URL（统一资源定位符）是一种标准化的地址格式，用于在互联网上定位资源。它作为特定网页、文件或其他资源的引用，并提供所有所需的信息，以便网络浏览器或其他客户端请求和访问该资源。

A typical URL consists of several components, including:

1. **Scheme 方案**: This specifies the protocol used to access the resource, such as HTTP (Hypertext Transfer Protocol) or HTTPS (HTTP Secure) for web pages, FTP (File Transfer Protocol) for file transfers, or other protocols like mailto or tel for email and telephone links.：这指定用于访问资源的协议，例如用于网页的HTTP（超文本传输协议）或HTTPS（HTTP安全） ，用于文件传输的FTP（文件传输协议），或用于电子邮件和电话链接的mailto或tel等其他协议。
2. **Domain name 域名**: The domain name is the human-readable address that identifies the server hosting the resource. It consists of a series of labels separated by dots (e.g., example.com). The rightmost label in a domain name is called the top-level domain (TLD), such as .com, .org, or .net.域名是标识托管资源的服务器的可读地址。它由一系列由点分隔的标签组成（例如，[example.com](http://example.com/)）。域名中最右边的标签称为顶级域（TLD），[例如.com](http://xn--fsqu6v.com/)、.org或.net。
3. **Subdomain 子域名**: Subdomains are optional and can be used to further organize and identify specific sections or services within a domain. For example, blog.example.com might represent a blog hosted on the example.com domain.子域名是可选的，可以用于进一步组织和标识域中的特定部分或服务。例如，blog.example.com可能表示托管在example.com域上的博客。
4. **Port number 端口号**: The port number is an optional component that specifies which port on the server should be used to access the resource. By default, HTTP uses port 80 and HTTPS uses port 443. If a non-default port is used, it must be specified in the URL (e.g., **[http://example.com:8080](http://example.com:8080/)**).端口号是可选组件，指定应使用服务器上的哪个端口来访问资源。默认情况下，HTTP使用端口80，HTTPS使用端口443。如果使用非默认端口，则必须在URL中指定（例如，[http://example.com:8080](http://example.com:8080/)）。
5. **Path 路径**: The path indicates the location of the resource on the server, often corresponding to a file or directory structure. It consists of a sequence of segments separated by slashes (e.g., /path/to/resource). 路径指示服务器上资源的位置，通常对应于文件或目录结构。它由一系列由斜杠分隔的段组成（例如，/path/to/resource）。
6. **Query string 查询字符串**: The query string is an optional component that starts with a question mark (?) and includes a series of key-value pairs separated by ampersands (&). It is used to provide additional information to the server, often as input parameters for a script or application (e.g., **[http://example.com/search?q=query](http://example.com/search?q=query)**). 查询字符串是可选组件，以问号（？）开头，并包括一系列由和号（&）分隔的键值对。它用于向服务器提供附加信息，通常作为脚本或应用程序的输入参数（例如，[http://example.com/search?q=query）。](http://example.com/search?q=query%EF%BC%89%E3%80%82)
7. **Fragment identifier片段标识符:** The fragment identifier is an optional component that starts with a hash sign (#) and is used to point to a specific section or element within the resource, often on a web page. It is processed by the client and not sent to the server (e.g., **[http://example.com/page#section](http://example.com/page#section)**). 片段标识符是可选组件，以井号（＃）开头，用于指向资源内的特定部分或元素，通常在网页上。它由客户端处理，而不发送到服务器（例如，[http://example.com/page＃section）。](http://example.com/page%EF%BC%83section%EF%BC%89%E3%80%82)

A complete URL might look like this:

```
https://www.example.com:443/path/to/resource?query=value#fragment
```

In this example, the scheme is "https", the domain name is "**[www.example.com](http://www.example.com/)**", the port number is 443, the path is "/path/to/resource", the query string is "?query=value", and the fragment identifier is "#fragment".在这个例子中，方案是“https”，域名是“**[www.example.com](http://www.example.com/)”，端口号是443，路径是“/path/to/resource”，查询字符串是“?query=value”，片段标识符是“#fragment”。

## URL Component

![截屏2023-04-21 20.37.58.png](URLs%20(lecture)%201301a3867c8c44c79c48b9915a48dfd4/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_20.37.58.png)

host: machine or a server you went to connect to 

end of host: port

path: specific resource on the machine. 

## URI and URL

A URI (Uniform Resource Identifier) and a URL (Uniform Resource Locator) are both used to identify resources, but they serve slightly different purposes:

1. **URI (Uniform Resource Identifier)**: A URI is a more general term used to identify a resource, either by location (like a URL) or by name (like a URN, Uniform Resource Name). A URI can be thought of as a superset that encompasses both URLs and URNs. In other words, all URLs and URNs are URIs, but not all URIs are URLs or URNs. A URI can be used to identify resources uniquely, regardless of how they are accessed or retrieved. URI 是一个更一般的术语，用于标识资源，可以通过位置（例如 URL）或名称（例如 URN，Uniform Resource Name）进行标识。 URI 可以被视为一个超集，包含了 URL 和 URN。换句话说，所有的 URL 和 URN 都是 URI，但并非所有的 URI 都是 URL 或 URN。无论如何访问或检索资源，URI 可以用来唯一标识资源。
2. **URL (Uniform Resource Locator)**: A URL is a specific type of URI that not only identifies a resource but also provides the means to locate and access that resource on the internet. A URL contains information about the protocol, domain name, port number, path, query string, and fragment identifier needed to request and access a resource. In most common usage, the terms "URI" and "URL" are used interchangeably, but technically, a URL is a subset of URI.URL 是 URI 的一个特定类型，它不仅标识资源，还提供了定位和访问该资源所需的手段。 URL 包含有关协议、域名、端口号、路径、查询字符串和片段标识符的信息，这些信息都是请求和访问资源所需的。在大多数常见用法中，“URI” 和 “URL” 可以互换使用，但从技术上讲，URL 是 URI 的一个子集。

**Here's an analogy to help illustrate the difference:**

- A URI is like an identification number (e.g., a Social Security number), which uniquely identifies a person regardless of their current location. URI 就像身份证号码一样（例如社会安全号码），可以唯一标识一个人，无论他们现在在哪里。
- A URL is like a home address, which provides the specific location of a person and the means to find and reach them. URL 就像家庭地址一样，提供了一个人的具体位置和找到并联系他们的方式。

In summary, a URI is a more general term that encompasses both URLs and URNs, while a URL is a specific type of URI that not only identifies a resource but also provides the means to locate and access that resource on the internet.总之，URI 是一个更一般的术语，包括了 URL 和 URN，而 URL 是 URI 的一个特定类型，不仅标识资源，还提供了定位和访问该资源的手段。

![截屏2023-04-21 20.39.40.png](URLs%20(lecture)%201301a3867c8c44c79c48b9915a48dfd4/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_20.39.40.png)

query start with ?

two parameters : name and action 

separated with &

![截屏2023-04-21 20.41.01.png](URLs%20(lecture)%201301a3867c8c44c79c48b9915a48dfd4/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_20.41.01.png)

A URI scheme is the first part of a Uniform Resource Identifier (URI) that identifies the protocol or the method used to access or interact with a resource. It is followed by a colon (:) and forms the beginning of the URI. Different URI schemes are used for various types of resources and services on the internet. URI（统一资源标识符）方案是标识用于访问或与资源交互的协议或方法的URI的第一部分。它后面跟着一个冒号（:）并形成URI的开头。不同的URI方案用于互联网上的各种类型的资源和服务。

Here are some common URI schemes and their purposes:

1. **http** and **https**: These schemes are used for accessing web pages and other resources via the Hypertext Transfer Protocol (HTTP) and the secure version of HTTP, HTTPS (HTTP Secure). Example: **`http://www.example.com`** or **`https://www.example.com`.** 这些方案用于通过超文本传输协议（HTTP）和HTTP的安全版本HTTPS（HTTP安全）访问网页和其他资源。例如：**`http://www.example.com`或`https://www.example.com`**
2. **ftp** and **ftps**: These schemes are used for accessing files and directories on remote servers via the File Transfer Protocol (FTP) and its secure version, FTPS (FTP Secure). Example: **`ftp://ftp.example.com`** or **`ftps://ftps.example.com`.** 这些方案用于通过文件传输协议（FTP）及其安全版本FTPS（FTP安全）访问远程服务器上的文件和目录。例如：**`ftp://ftp.example.com`或`ftps://ftps.example.com`**
3. **mailto**: This scheme is used for composing and sending email messages. When clicked, it typically opens the user's default email client with a new message composed to the specified address. Example: **`mailto:user@example.com`.** 这个方案用于编写和发送电子邮件。当单击时，通常会打开用户的默认电子邮件客户端，并撰写一个新的消息发送到指定的地址。例如：**`mailto:user@example.com`**
4. **tel**: This scheme is used for dialing telephone numbers. When clicked, it typically opens the user's default phone or VoIP application with the specified number dialed. Example: **`tel:+1234567890`.** 这个方案用于拨打电话号码。当单击时，通常会打开用户的默认电话或VoIP应用程序，并拨打指定的号码。例如：**`tel:+1234567890`**
5. **file**: This scheme is used for accessing local files on a user's computer or a shared network drive. Example: **`file:///C:/Users/user/Documents/file.txt`.** 这个方案用于访问用户计算机或共享网络驱动器上的本地文件。例如：**`file:///C:/Users/user/Documents/file.txt`**
6. **data**: This scheme is used for embedding small pieces of data directly into a URI, usually in the form of a base64-encoded string. It is commonly used for inline images in HTML or CSS. Example: **`data:image/png;base64,iVBOR...`** 这个方案用于将小块数据直接嵌入URI中，通常以base64编码的字符串形式出现。它通常用于HTML或CSS中的内联图像。例如：**`data:image/png;base64,iVBOR...`**
7. **ssh**: This scheme is used for accessing remote servers securely via the Secure Shell (SSH) protocol. Example: **`ssh://user@server.example.com`.** 这个方案用于通过安全外壳（SSH）协议安全地访问远程服务器。例如：**`ssh://user@server.example.com`**

These are just a few examples of the numerous URI schemes available. Each scheme has specific rules and requirements for the structure and format of the URI following the colon. The choice of a scheme depends on the type of resource being accessed and the protocol used to access it.

这些只是众多可用URI方案的几个例子。每个方案都有特定的规则和要求，用于冒号后面的URI的结构和格式。选择方案取决于所访问资源的类型和用于访问它的协议。

![截屏2023-04-21 20.41.34.png](URLs%20(lecture)%201301a3867c8c44c79c48b9915a48dfd4/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_20.41.34.png)

Http is stateless, if we do need to carry any state that should be held in the request to the server. 

REST (Representational State Transfer) is an architectural style for designing networked applications. It was introduced by Roy Fielding in his 2000 doctoral dissertation as a set of constraints and principles aimed at creating scalable, maintainable, and high-performing web services. REST is commonly used for building APIs (Application Programming Interfaces) that allow different software systems to communicate with each other.

HTTP是无状态的，如果我们需要携带任何状态，那应该在请求发送到服务器时进行保存。

REST（表征状态转移）是一种用于设计网络应用程序的架构风格。它由Roy Fielding在他的2000年博士论文中引入，作为一组旨在创建可伸缩、易维护和高性能Web服务的约束和原则。REST通常用于构建API（应用程序编程接口），以允许不同的软件系统彼此通信。

Here are some key concepts and principles of REST:

1. **Resources 资源**: In REST, everything is considered a resource. A resource is an object or a piece of data that can be identified by a unique URI (Uniform Resource Identifier). Examples of resources include users, articles, or products in an e-commerce system.  在REST中，一切都被视为资源。资源是可以通过唯一的URI（统一资源标识符）进行识别的对象或数据片段。资源的例子包括在电子商务系统中的用户、文章或产品。
2. **Stateless**  **无状态**: Each request from a client to a server must contain all the information needed to process the request. The server should not store any information about the client's state between requests. This statelessness improves scalability and reliability, as the server can be stateless and does not need to maintain session information for each client. 每个来自客户端到服务器的请求都必须包含处理请求所需的所有信息。服务器不应该在请求之间存储任何有关客户端状态的信息。这种无状态性能提高了可伸缩性和可靠性，因为服务器可以是无状态的，不需要为每个客户端维护会话信息。
3. **Client-Server 客户端-服务器**:  REST follows a client-server architecture, where the client and server are separate entities that communicate over a network. The client is responsible for the user interface, while the server manages the resources and processes requests. This separation of concerns allows for greater flexibility, maintainability, and scalability.  REST遵循客户端-服务器架构，其中客户端和服务器是相互独立的实体，它们通过网络进行通信。客户端负责用户界面，而服务器管理资源并处理请求。这种关注点的分离允许更大的灵活性、可维护性和可扩展性。
4. **Cacheable 可缓存**:  Responses from the server can be cached by the client to improve performance. The server must explicitly indicate whether a response is cacheable or not. Caching can reduce the load on the server and improve the responsiveness of the application. 服务器的响应可以被客户端缓存以提高性能。服务器必须明确指示响应是否可缓存。缓存可以减轻服务器的负载并提高应用程序的响应能力。
5. **Layered System 分层系统**: REST architectures can be composed of multiple layers, with each layer having a specific responsibility. This allows for better separation of concerns, modularity, and maintainability. A client only interacts with the layer directly above it and is unaware of the other layers in the system.  REST结构可以由多个层组成，每个层具有特定的职责。这允许更好的关注点分离、模块化和可维护性。客户端只与其上面的层交互，并不知道系统中的其他层。
6. **Uniform Interface 统一接口**:  REST APIs should have a consistent and uniform interface, making them easy to use and understand. This is achieved by using standard HTTP methods (GET, POST, PUT, DELETE, etc.) and adhering to a set of conventions and best practices. REST API应该具有一致和统一的接口，使其易于使用和理解。这通过使用标准的HTTP方法(GET、POST、PUT、DELETE等）和遵守一组约定和最佳实践来实现。

In practice, RESTful APIs typically use HTTP as the transport protocol and rely on standard HTTP methods to perform CRUD (Create, Read, Update, Delete) operations on resources:在实践中，RESTful API通常使用HTTP作为传输协议，并依赖标准的HTTP方法来执行CRUD（创建、读取、更新、删除）操作：

- **GET**: Retrieve a resource or a collection of resources ; 检索资源或资源集合
- **POST**: Create a new resource; 创建新资源
- **PUT** or **PATCH**: Update an existing resource; 更新现有资源
- **DELETE**: Remove a resource; 删除资源

REST has become a popular choice for building web services and APIs due to its simplicity, scalability, and alignment with web technologies. Many modern web applications and mobile apps use RESTful APIs to communicate with servers and exchange data.

由于其简单性、可扩展性和与Web技术的一致性，REST已成为构建Web服务和API的流行选择。许多现代Web应用程序和移动应用程序使用RESTful API与服务器通信并交换数据。

![截屏2023-04-21 20.43.30.png](URLs%20(lecture)%201301a3867c8c44c79c48b9915a48dfd4/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_20.43.30.png)

1. What does URI stand for?
    - (a) Uniform Resource Identifier
    - (b) Universal Resource Identifier
    - (c) Unitary Resource Identifier
    - (d) Unique Resource Identifier
2. What is the difference between a URI and a URL?
    - (a) There is no difference; the terms can be used interchangeably.
    - (b) A URI identifies a resource, while a URL identifies a resource and provides the means to locate and access it.
    - (c) A URL identifies a resource, while a URI identifies a resource and provides the means to locate and access it.
    - (d) A URL is a subset of a URI.
3. What is the purpose of a query string in a URL?
    - (a) To identify the resource being accessed
    - (b) To provide additional information about the resource being accessed
    - (c) To specify the protocol used to access the resource
    - (d) To specify the location of the resource
4. How are parameters in a query string separated?
    - (a) By commas
    - (b) By colons
    - (c) By semicolons
    - (d) By ampersands
5. What is a URI scheme?
    - (a) The first part of a URI that identifies the protocol or method used to access a resource
    - (b) The part of a URI that identifies the resource being accessed
    - (c) The part of a URI that specifies the location of the resource
    - (d) The part of a URI that provides additional information about the resource being accessed
6. Which URI scheme is used for accessing files and directories on remote servers via the File Transfer Protocol (FTP)?
    - (a) http
    - (b) ftp
    - (c) mailto
    - (d) tel
7. Which URI scheme is used for composing and sending email messages?
    - (a) http
    - (b) ftp
    - (c) mailto
    - (d) tel
8. Which URI scheme is used for dialing telephone numbers?
    - (a) http
    - (b) ftp
    - (c) mailto
    - (d) tel
9. What is the principle of statelessness in HTTP?
    - (a) The client must send all information needed to process the request with each request.
    - (b) The server must store information about the client's state between requests.
    - (c) The client must maintain session information for each request.
    - (d) The server must send all information needed to process the request with each response.
10. What is REST?
    - (a) A protocol for accessing remote servers securely via the Secure Shell (SSH) protocol
    - (b) An architectural style for designing networked applications
    - (c) A scheme for embedding small pieces of data directly into a URI
    - (d) A standard for composing and sending email messages
11. What are resources in REST?
    - (a) Objects or pieces of data that can be identified by a unique URI
    - (b) A set of constraints and principles aimed at creating scalable and maintainable web services
    - (c) A consistent and uniform interface for accessing web services
    - (d) A set of standard HTTP methods for performing CRUD operations on resources
12. Which HTTP method is used to retrieve a resource or a collection of resources?
    - (a) POST
    - (b) GET
    - (c) DELETE
    - (d) PUT
13. Which HTTP method is used to create a new resource?
    - (a) GET
    - (b) POST
    - (c) PUT
    - (d) DELETE
14. Which HTTP method is used to update an existing resource?
    - (a) GET
    - (b) POST
    - (c) PUT
    - (d) DELETE
    
    Answer:
    
    1. A
    2. B
    3. B
    4. D
    5. A
    6. B
    7. C
    8. D
    9. A
    10. B
    11. A
    12. B
    13. B
    14. C