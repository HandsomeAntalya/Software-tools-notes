# HTML Element  (Lecture)

- [ ]  Use the `<link>` element to link external resources such as style sheets, fonts, icons, and other files to an HTML document
- [ ]  Place the `<link>` element in the `<head>` section of the HTML document
- [ ]  Create a form using the `<form>` element to allow users to enter and submit data to a web server
- [ ]  Use input elements such as text fields, checkboxes, radio buttons, dropdown lists, and buttons to collect user data in a form
- [ ]  Process the data entered in a form by a server-side script or application that can store, retrieve, or manipulate the data as required
- [ ]  Use the `<table>` element to create tables that can display data in rows and columns
- [ ]  Use the `<caption>` element to provide a caption or title for the table
- [ ]  Create tables that are easy to read and navigate, and that are accessible to all users

![截屏2023-04-21 21.42.32.png](HTML%20Element%20(Lecture)%202fbe4ce3bc3640c9871774567e508eb3/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_21.42.32.png)

href → mechanical path

/ : refer to a document root 

In HTML, the **`<link>`** element is used to link external resources such as style sheets, fonts, icons, and other files to an HTML document. The **`<link>`** element must be placed in the **`<head>`** section of the HTML document.

Here's an example of how to use the **`<link>`** element to link a style sheet to an HTML document:

```html
<head>
  <link rel="stylesheet" type="text/css" href="style.css">
</head>
```

In the above example, the **`<link>`** element links an external CSS file called **`style.css`** to the HTML document. The **`rel`** attribute specifies the relationship between the current document and the linked document, which in this case is a stylesheet. The **`type`** attribute specifies the MIME type of the linked document, which is a CSS file in this example. The **`href`** attribute specifies the URL of the linked document.

Here's another example of how to use the **`<link>`** element to link an icon to an HTML document:

```html
<head>
  <link rel="icon" type="image/png" href="favicon.png">
</head>
```

In the above example, the **`<link>`** element links an icon file called **`favicon.png`** to the HTML document. The **`rel`** attribute specifies the relationship between the current document and the linked document, which in this case is an icon. The **`type`** attribute specifies the MIME type of the linked document, which is a PNG image in this example. The **`href`** attribute specifies the URL of the linked document.

Using the **`<link>`** element to link external resources is important in web development, as it allows web pages to load faster by separating content and presentation, and makes it easier to maintain and update web pages.

Forms 

![截屏2023-04-21 21.45.36.png](HTML%20Element%20(Lecture)%202fbe4ce3bc3640c9871774567e508eb3/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_21.45.36.png)

![截屏2023-04-21 21.45.49.png](HTML%20Element%20(Lecture)%202fbe4ce3bc3640c9871774567e508eb3/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_21.45.49.png)

method and action

submission always handled in a button

In HTML, the **`<form>`** element is used to create a form that allows users to enter and submit data to a web server. A form typically consists of input elements such as text fields, checkboxes, radio buttons, dropdown lists, and buttons that are used to collect user data. The data entered in a form is then processed by a server-side script or application that can store, retrieve, or manipulate the data as required. 在HTML中，**`<form>`**元素用于创建一个表单，允许用户输入并提交数据到Web服务器。表单通常由输入元素组成，如文本字段、复选框、单选按钮、下拉列表和按钮，用于收集用户数据。然后，一个服务器端的脚本或应用程序处理表单中输入的数据，可以根据需要存储、检索或操作数据。

Here's an example of how to create a simple form in HTML:

```html

<form action="submit-form.php" method="post">
  <label for="name">Name:</label>
  <input type="text" id="name" name="name" required>

  <label for="email">Email:</label>
  <input type="email" id="email" name="email" required>

  <label for="message">Message:</label>
  <textarea id="message" name="message"></textarea>

  <input type="submit" value="Submit">
</form>
```

In the above example, the **`<form>`** element creates a form that will be submitted to a server-side script called **`submit-form.php`** when the user clicks the submit button. The **`method`** attribute specifies the HTTP method used to submit the form data, which is **`post`** in this example. The **`action`** attribute specifies the URL of the server-side script that will process the form data.在上面的示例中，**`<form>`** 元素创建了一个表单，当用户单击提交按钮时，该表单将提交到一个名为 **`submit-form.php`** 的服务器端脚本。**`method`** 属性指定了用于提交表单数据的 HTTP 方法，在此示例中为 **`post`**。**`action`** 属性指定了将处理表单数据的服务器端脚本的 URL。

The form contains three input elements: a text input field for the user's name, an email input field for the user's email address, and a textarea element for the user's message. Each input element has a corresponding **`id`** attribute and a **`name`** attribute that will be used to identify the input data when the form is submitted.表单包含三个输入元素：一个文本输入字段用于用户的姓名，一个电子邮件输入字段用于用户的电子邮件地址，以及一个文本区域元素用于用户的消息。每个输入元素都有一个相应的 **`id`** 属性和一个 **`name`** 属性，这些属性将在提交表单时用于标识输入数据。

The **`<label>`** element is used to associate a label with an input element, which provides a textual description of the input element for screen readers and other assistive technologies. The **`for`** attribute of the **`<label>`** element must match the **`id`** attribute of the corresponding input element.**`<label>`** 元素用于将标签与输入元素关联起来，为屏幕阅读器和其他辅助技术提供输入元素的文本描述。**`<label>`** 元素的 **`for`** 属性必须与相应输入元素的 **`id`** 属性匹配。

Finally, the form contains a submit button that the user can click to submit the form data to the server.最后，表单包含一个提交按钮，用户可以单击该按钮将表单数据提交到服务器。

Using forms is an important part of web development, as it allows users to interact with web applications and websites in a meaningful way. It's important to create forms that are easy to use and accessible to all users, including those with disabilities.使用表单是 Web 开发的重要部分，因为它允许用户以有意义的方式与 Web 应用程序和网站进行交互。创建易于使用且对所有用户包括残障用户都可访问的表单非常重要。

![截屏2023-04-21 21.46.54.png](HTML%20Element%20(Lecture)%202fbe4ce3bc3640c9871774567e508eb3/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_21.46.54.png)

![截屏2023-04-21 21.47.04.png](HTML%20Element%20(Lecture)%202fbe4ce3bc3640c9871774567e508eb3/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_21.47.04.png)

![截屏2023-04-21 21.47.18.png](HTML%20Element%20(Lecture)%202fbe4ce3bc3640c9871774567e508eb3/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_21.47.18.png)

![截屏2023-04-21 21.47.35.png](HTML%20Element%20(Lecture)%202fbe4ce3bc3640c9871774567e508eb3/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_21.47.35.png)

### Table structure

In HTML, the **`<table>`** element is used to create tables that can display data in rows and columns. Tables can be used to present a variety of information, such as schedules, product listings, pricing, and more. Here's an example of how to create a simple table in HTML:

```html
<table>
  <caption>Monthly Sales Report</caption>
  <thead>
    <tr>
      <th>Month</th>
      <th>Product A</th>
      <th>Product B</th>
      <th>Total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>January</td>
      <td>$5,000</td>
      <td>$7,000</td>
      <td>$12,000</td>
    </tr>
    <tr>
      <td>February</td>
      <td>$6,000</td>
      <td>$8,000</td>
      <td>$14,000</td>
    </tr>
    <tr>
      <td>March</td>
      <td>$4,000</td>
      <td>$6,000</td>
      <td>$10,000</td>
    </tr>
  </tbody>
</table>

```

In the above example, the **`<table>`** element creates a table that contains a caption and two sections: a header section (specified using the **`<thead>`** element) and a body section (specified using the **`<tbody>`** element). 在上面的例子中，**`<table>`** 元素创建了一个包含标题和两个部分的表格：头部部分（使用 **`<thead>`** 元素指定）和主体部分（使用 **`<tbody>`** 元素指定）。

The table contains four columns, specified using the **`<th>`** element in the header row and the **`<td>`** element in the data rows. The **`<th>`** element is used to create table headers, which are typically bold and centered, while the **`<td>`** element is used to create table cells that contain data. 该表格包含四列，使用标题行中的 **`<th>`** 元素和数据行中的 **`<td>`** 元素指定。**`<th>`** 元素用于创建表头，通常是粗体且居中，而 **`<td>`** 元素用于创建包含数据的表格单元格。

Each row of data is enclosed in a **`<tr>`** element, and each cell of data is enclosed in a **`<td>`** element. The first column in each row contains the name of the month, while the other columns contain sales data for two products and a total for each month. 每一行数据都被包含在一个**`<tr>`**元素中，每个数据单元格都被包含在一个**`<td>`**元素中。每一行的第一列包含月份名称，而其他列包含两个产品的销售数据和每月总销售额。

The **`<caption>`** element is used to provide a caption or title for the table, which can help to provide context for the data and improve accessibility for users with disabilities.**`<caption>`** 元素用于为表格提供标题或标题，这有助于为数据提供上下文并提高残障用户的可访问性。

Using tables is an important part of web development, as it allows developers to present data in a structured and organized way. It's important to create tables that are easy to read and navigate, and that are accessible to all users.

![截屏2023-04-21 21.47.46.png](HTML%20Element%20(Lecture)%202fbe4ce3bc3640c9871774567e508eb3/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_21.47.46.png)

main body :<td>

![截屏2023-04-21 21.48.56.png](HTML%20Element%20(Lecture)%202fbe4ce3bc3640c9871774567e508eb3/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_21.48.56.png)

### MCQ Questions:

1. What HTML element is used to link external resources such as style sheets, fonts, icons, and other files to an HTML document?
    - A. `<form>`
    - B. `<table>`
    - C. `<link>`
    - D. `<caption>`
2. Where should the `<link>` element be placed in an HTML document?
    - A. In the `<body>` section
    - B. In the footer section
    - C. In the `<head>` section
    - D. In the navigation section
3. What is the purpose of forms in web development?
    - A. To create tables that can display data in rows and columns
    - B. To link external resources such as style sheets, fonts, icons, and other files to an HTML document
    - C. To allow users to enter and submit data to a web server
    - D. To provide a caption or title for a table
4. What is the HTTP method used to submit form data in the example given in the document?
    - A. `GET`
    - B. `POST`
    - C. `PUT`
    - D. `DELETE`
5. What is the purpose of the `<caption>` element in a table?
    - A. To create table headers
    - B. To create table cells that contain data
    - C. To provide a title or caption for the table
    - D. To specify the URL of the linked document
6. What is the recommended location for the `<link>` element in an HTML document?
    - A. In the `<body>` section
    - B. In the footer section
    - C. In the `<head>` section
    - D. In the navigation section
7. What is the purpose of the `<th>` element in a table?
    - A. To create table headers
    - B. To create table cells that contain data
    - C. To provide a title or caption for the table
    - D. To specify the URL of the linked document
8. What is the purpose of the **`<form>`** element in HTML?
    - A. To create tables that can display data in rows and columns
    - B. To link external resources such as style sheets, fonts, icons, and other files to an HTML document
    - C. To allow users to enter and submit data to a web server
    - D. To provide a caption or title for a table
9. What is the purpose of the **`<label>`** element in a form?
    - A. To create table headers
    - B. To create table cells that contain data
    - C. To provide a title or caption for the table
    - D. To associate a label with an input element
    
    ### Answers:
    
    1. C 
    2. C
    3. C
    4. B
    5. C
    6. C
    7. A
    8. C
    9. D
    
    Quiz from W3School:
    
    1. What is the correct HTML element for inserting a line break?
    
    A. <lb>    
    
    B. <break>
    
    C. <br>
    
    1. What is the correct HTML for adding a background color?
    
    A. <body bg="yellow">    
    
    B. <background>yellow</background>
    
    C. <body style="background-color:yellow;">
    
    1. What is the correct HTML for creating a hyperlink?
    
    A. <a url="http://www.w3schools.com">W3Schools.com</a>  
    
    B.<a name="http://www.w3schools.com">W3Schools.com</a>
    
    C.<a>http://www.w3schools.com</a>
    
    D.<a href="http://www.w3schools.com">W3Schools</a>
    
    1. How can you open a link in a new tab/browser window?
    
    A. <a href="url" target="new">    
    
    B. <a href="url" new>
    
    C. <a href="url" target="_blank">
    
    1. Inline elements are normally displayed without starting a new line.
    
    A. False    
    
    B. True
    
    1. How can you make a numbered list?
    
    A. <ul>    
    
    B. <ol>   
    
    C. <dl>
    
    D. <list>
    
    1. How can you make a bulleted list?
    
    A. <list>   
    
    B. <ul>  
    
    C. <dl>
    
    D. <ol>
    
    1. What is the correct HTML for making a checkbox?
    
    A<input type="checkbox">   
    
    B<check>
    
    C<input type="check">
    
    D<checkbox>
    
    1. What is the correct HTML for making a text input field?
    
    A<input type="text">  
    
    B<textfield>
    
    C<textinput type="text">
    
    D<input type="textfield">
    
    1. What is the correct HTML for making a drop-down list?
    
    A<list>    
    
    B<input type="list">
    
    C<input type="dropdown">
    
    D<select>
    
    1. What is the correct HTML for making a text area?
    
    A<input type="textarea">    
    
    B<textarea>    
    
    C<input type="textbox">
    
    1. What is the correct HTML for inserting a background image?
    
    A<background img="background.gif">    
    
    B<body bg="background.gif">
    
    C<body style="background-image:url(background.gif)">
    
    1. An <iframe> is used to display a web page within a web page.
    
    A.There is no such thing as an <iframe>   
    
    B.True   
    
    C.False
    
    1. Which HTML element defines the title of a document?
    
    A. <head> 
    
    B. <title>   
    
    C. <meta>
    
    1. C
    2. C
    3. D
    4. C
    5. B
    6. B
    7. B
    8. A
    9. A
    10. D
    11. B
    12. C
    13. B
    14. B
    
    ![截屏2023-04-23 23.27.25.png](HTML%20Element%20(Lecture)%202fbe4ce3bc3640c9871774567e508eb3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_23.27.25.png)
    
    ![截屏2023-04-23 23.27.38.png](HTML%20Element%20(Lecture)%202fbe4ce3bc3640c9871774567e508eb3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_23.27.38.png)
    
    ![截屏2023-04-23 23.27.46.png](HTML%20Element%20(Lecture)%202fbe4ce3bc3640c9871774567e508eb3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_23.27.46.png)
    
    ![截屏2023-04-23 23.27.56.png](HTML%20Element%20(Lecture)%202fbe4ce3bc3640c9871774567e508eb3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_23.27.56.png)
    
    ![截屏2023-04-23 23.28.11.png](HTML%20Element%20(Lecture)%202fbe4ce3bc3640c9871774567e508eb3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_23.28.11.png)
    
    In html, onblur and onfocus are: event attributes.
    
    ![截屏2023-04-23 23.28.24.png](HTML%20Element%20(Lecture)%202fbe4ce3bc3640c9871774567e508eb3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_23.28.24.png)
    
    ![截屏2023-04-23 23.28.36.png](HTML%20Element%20(Lecture)%202fbe4ce3bc3640c9871774567e508eb3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_23.28.36.png)
    
    ![截屏2023-04-23 23.28.52.png](HTML%20Element%20(Lecture)%202fbe4ce3bc3640c9871774567e508eb3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_23.28.52.png)
    
    which input type defines a slider control: range
    
    ![截屏2023-04-23 23.29.09.png](HTML%20Element%20(Lecture)%202fbe4ce3bc3640c9871774567e508eb3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_23.29.09.png)
    
    which HTML element is used to display a scalar measurement within a range?
    
    <meter>