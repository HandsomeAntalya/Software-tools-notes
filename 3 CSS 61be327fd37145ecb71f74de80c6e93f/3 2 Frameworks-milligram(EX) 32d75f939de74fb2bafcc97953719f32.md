# 3.2 Frameworks-milligram(EX)

Now that you know some CSS, you could write your own framework - one or more stylesheet files that implement your idea of good design. In this exercise we will look at some examples.

注: 这一章的练习都在COMSM0085/exercises/part2/resources下面,如果需要run,检查页面的话就可以直接在intellJ里面点击运行.

![截屏2023-04-11 15.48.16.png](3%202%20Frameworks-milligram(EX)%2032d75f939de74fb2bafcc97953719f32/%25E6%2588%25AA%25E5%25B1%258F2023-04-11_15.48.16.png)

## Milligram

Milligram is, in its own words, a "minimalist CSS framework".

Download the page1.html file and open it in the browser: it contains some text and a sign-up form for a CSS conference.

![截屏2023-04-11 15.49.29.png](3%202%20Frameworks-milligram(EX)%2032d75f939de74fb2bafcc97953719f32/%25E6%2588%25AA%25E5%25B1%258F2023-04-11_15.49.29.png)

![截屏2023-04-11 15.50.55.png](3%202%20Frameworks-milligram(EX)%2032d75f939de74fb2bafcc97953719f32/%25E6%2588%25AA%25E5%25B1%258F2023-04-11_15.50.55.png)

根据提示在页面前加入这几行之后,网站变成了这个样子:

![截屏2023-04-11 15.51.49.png](3%202%20Frameworks-milligram(EX)%2032d75f939de74fb2bafcc97953719f32/%25E6%2588%25AA%25E5%25B1%258F2023-04-11_15.51.49.png)

```css
<link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Roboto:300,300italic,700,700italic">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/normalize/8.0.1/normalize.css">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/milligram/1.4.1/milligram.css">
```

- The first one loads Google's [Roboto web font](https://fonts.google.com/specimen/Roboto), which the designers of Milligram selected as their default. Because it is loaded as a web resource, it should work across different browsers and operating systems, you don't need to install it first.
- The next line loads `normalize.css`, an alternative to `reset.css` that provides a consistent stylesheet across browsers. Try out the page with just the first two stylesheets and see how it looks now - the font won't have changed because no-one has set `font-family` yet, that will happen in the next stylesheet, but the margins will be slightly different.
- The third one adds Milligram itself. Your page now uses a different style, for example the form fields and labels are laid out vertically and the register button is purple.(如果我们把这一行注释掉的话,那么页面的效果就会消失)

Milligram chooses to style the whole page by default, but you can customise this further. One of their features is a *container* that gives its content a fixed maximum width.

- Add `class="container"` to the `<main>` element, save and reload. See how the page behaves when you make the window wider and narrower. The page will always have some left/right padding, but the form adapts to the window size.

这个任务呢就是需要我们在这里

![截屏2023-04-11 16.00.48.png](3%202%20Frameworks-milligram(EX)%2032d75f939de74fb2bafcc97953719f32/%25E6%2588%25AA%25E5%25B1%258F2023-04-11_16.00.48.png)

变成

![截屏2023-04-11 16.01.10.png](3%202%20Frameworks-milligram(EX)%2032d75f939de74fb2bafcc97953719f32/%25E6%2588%25AA%25E5%25B1%258F2023-04-11_16.01.10.png)

而后页面会变成这也样子: 表格居中了

![截屏2023-04-11 16.01.33.png](3%202%20Frameworks-milligram(EX)%2032d75f939de74fb2bafcc97953719f32/%25E6%2588%25AA%25E5%25B1%258F2023-04-11_16.01.33.png)

In Milligram, the **`container`** class is designed to create a centered, responsive container with a maximum width.

The **`container`** class in Milligram applies the following styles:

```css
.container {
  margin-left: auto;
  margin-right: auto;
  max-width: 112.0rem;
  padding-left: 2.0rem;
  padding-right: 2.0rem;
  width: 100%;
}
```

These styles ensure that the content inside the container is centered on the page, has a maximum width, and has some padding on the left and right sides. The container will also be responsive to different screen sizes, as it has a 100% width.

Milligram is a minimalist CSS framework, and it provides a small set of classes for basic styling and layout. Here are some of the common classes provided by Milligram:

1. Typography:
    - **`.title`**: Applies a larger font size to headings, useful for page titles.
    - **`.caption`**: Applies a smaller font size, useful for captions and smaller texts.
2. Buttons:
    - **`.button`**: Styles a button element or an input element with type="button" or "submit".
    - **`.button-clear`**: Applies a transparent background to a button element.
3. Forms:
    - **`.input`**: Styles an input element, like text input, email input, etc.
    - **`.label`**: Styles a label element.
    - **`.select`**: Styles a select element (drop-down list).
    - **`.textarea`**: Styles a textarea element.
4. Layout:
    - **`.container`**: Creates a responsive, centered container with a maximum width and padding.
    - **`.row`**: Represents a row in a grid system.
    - **`.column`**, **`.col`**: Represents a column in a grid system. You can combine these classes with sizing classes like **`.column-50`** or **`.col-50`** for a column that takes up 50% of the available width.
5. Utility classes:
    - **`.clearfix`**: Clears floated elements inside a container.
    - **`.float-left`**: Floats an element to the left.
    - **`.float-right`**: Floats an element to the right.

Please note that Milligram is a minimalistic framework, so it doesn't have as many classes as some other popular frameworks like Bootstrap. However, it's great for simple projects or as a starting point for custom styling. You can find more information about Milligram and its classes in the official documentation: **[https://milligram.io/](https://milligram.io/)**

因为刚才虽然美观了不少,但是我们css的header 还是没有居中,所以我们需要这样一下加一个style 

![截屏2023-04-11 16.11.01.png](3%202%20Frameworks-milligram(EX)%2032d75f939de74fb2bafcc97953719f32/%25E6%2588%25AA%25E5%25B1%258F2023-04-11_16.11.01.png)

这样子我们的网页就会好看多啦!

![截屏2023-04-11 16.12.50.png](3%202%20Frameworks-milligram(EX)%2032d75f939de74fb2bafcc97953719f32/%25E6%2588%25AA%25E5%25B1%258F2023-04-11_16.12.50.png)

- In the developer tools, activate mobile mode a.k.a. *toggle device emulation*, on chrome/edge this is the second icon from the left in the top left of the developer panel. The text looks much too small now!
- This is due to a number of factors including higher pixel density on mobile screens. Milligram can handle mobile devices, but it needs the following line in the header:

当我们用f12检查我们的网页的时候, 我们使用手机模式的话也不会有什么奇怪的formating, 这是因为

这一行(第十行: milligram带的,帮我们把内容弄的更好了)

![截屏2023-04-11 16.26.39.png](3%202%20Frameworks-milligram(EX)%2032d75f939de74fb2bafcc97953719f32/%25E6%2588%25AA%25E5%25B1%258F2023-04-11_16.26.39.png)

![截屏2023-04-11 16.28.01.png](3%202%20Frameworks-milligram(EX)%2032d75f939de74fb2bafcc97953719f32/%25E6%2588%25AA%25E5%25B1%258F2023-04-11_16.28.01.png)

This line, which is often (but not always) good practice to include in a HTML5 page anyway, tells a mobile browser (or a device pretending to be one) to adopt sensible defaults including larger fonts depending on the pixel density and no horizontal scrollbars. You can read more about this [on MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Viewport_meta_tag)

### Viewport basics

A typical mobile-optimized site contains something like the following:

`<meta name="viewport" content="width=device-width, initial-scale=1" />`

Not all devices are the same width; you should make sure that your pages work well in a large variation of screen sizes and orientations.

The basic properties of the "viewport" `<meta>` tag include:

`width`

Controls the size of the viewport. It can be set to a specific number of pixels like `width=600` or to the special value `device-width`, which is [100vw](https://developer.mozilla.org/en-US/docs/Web/CSS/length#relative_length_units_based_on_viewport), or 100% of the viewport width. Minimum: `1`. Maximum: `10000`. Negative values: ignored.

`height`

Controls the size of the viewport. It can be set to a specific number of pixels like `height=400` or to the special value `device-height`, which is [100vh](https://developer.mozilla.org/en-US/docs/Web/CSS/length#vh), or 100% of the viewport height. Minimum: `1`. Maximum: `10000`. Negative values: ignored.

`initial-scale`

Controls the zoom level when the page is first loaded. Minimum: `0.1`. Maximum: `10`. Default: `1`. Negative values: ignored.

`minimum-scale`

Controls how much zoom out is allowed on the page. Minimum: `0.1`. Maximum: `10`. Default: `0.1`. Negative values: ignored.

`maximum-scale`

Controls how much zoom in is allowed on the page. Any value less than 3 fails accessibility. Minimum: `0.1`. Maximum: `10`. Default: `10`. Negative values: ignored.

`user-scalable`

Controls whether zoom in and zoom out actions are allowed on the page. Valid values: `0`, `1`, `yes`, or `no`. Default: `1`, which is the same as `yes`. Setting the value to `0`, which is the same as `no`, is against Web Content Accessibility Guidelines (WCAG).

`interactive-widget`

Specifies the effect that interactive UI widgets, such as a virtual keyboard, have on the page's viewports. Valid values: `resizes-visual`, `resizes-content`, or `overlays-content`. Default: `resizes-visual`.

On [the milligram documentation page](https://milligram.io/#typography) you can read more about the elements that Milligram styles for you, and how you can customise this (e.g. buttons).

![截屏2023-04-11 16.38.03.png](3%202%20Frameworks-milligram(EX)%2032d75f939de74fb2bafcc97953719f32/%25E6%2588%25AA%25E5%25B1%258F2023-04-11_16.38.03.png)

Have a look in your browser's developer tools at how Milligram styles the page: select an element in the *Elements* tab (or right-click it and choose *Inspect*), then look at the styles that appear in the *Styles* area. How does Milligram set the following?

- Size of heading fonts
    
    ![截屏2023-04-11 16.40.37.png](3%202%20Frameworks-milligram(EX)%2032d75f939de74fb2bafcc97953719f32/%25E6%2588%25AA%25E5%25B1%258F2023-04-11_16.40.37.png)
    

- Form fields take up the full width of the container

Milligram sets the width of form fields (such as **`input`**and **`textarea`**elements) using the **`width`**
 property with a value of **`100%`**This ensures that the form fields take up the full width of their containing element.

- Form labels and fields appear below each other

Milligram uses the **`display`** property with a value of **`block`**for form labels and fields, which ensures that they take up the full width of their containing element and appear below each other. By default, block-level elements start on a new line and span the entire width of their parent element.

- Labels are closer to their own field than the field above

Milligram sets the **`margin`**property for form labels and fields to create appropriate spacing between them. For example, it might set a larger bottom margin for form labels and a smaller top margin for form fields to achieve the desired spacing.

- Size and centering of everything in a container on wide enough screens

Milligram uses the **`max-width`**property to set a maximum width for the container, which prevents it from expanding beyond a certain size on larger screens. To center the container, it sets the left and right margins to **`auto`**. This evenly distributes the remaining space on either side of the container, effectively centering it.

[3.2.2 Bulma](3%202%20Frameworks-milligram(EX)%2032d75f939de74fb2bafcc97953719f32/3%202%202%20Bulma%2027cbb88e5d6b4e44b0093bf749284629.md)