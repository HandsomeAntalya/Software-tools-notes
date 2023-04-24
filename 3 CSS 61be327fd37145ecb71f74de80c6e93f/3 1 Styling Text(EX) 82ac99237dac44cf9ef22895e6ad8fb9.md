# 3.1 Styling Text(EX)

## Styling Text

Under [resources/sometext.html](https://cs-uob.github.io/COMSM0085/exercises/part2/resources/sometext.html) you have a basic text-based HTML document with some information about your degree. Download this file and open it in your browser, you will see it displayed with the default stylesheet (and any customisations you might have applied, such as selecting a default font and size).

File Location: COMSM0085/exercises/part2/resources/sometext.html

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8" />
        <title>Some Text</title>
        <!-- <link rel="stylesheet" href="reset.css" /> -->
    </head>
    <body>
        <h1>Computer Science at the University of Bristol</h1>
        <p>The BSc and MEng Computer Science programmes provide you with a solid and <em>practical</em> introduction to the fundamentals of Computer Science, followed by opportunities to specialise in exciting research areas including Machine Learning, Human-Computer Interaction and Computational Neuroscience.</p>
        <h2>A practical experience</h2>
        <p>At Bristol, we teach you the practical skills that you will need for a successful career. Our curruiculum has a strong project-oriented focus:</p>
        <ul>
            <li>In your second year, you will complete a group software project in which to develop software for a real client to address a real-world problem.</li>
            <li>In your third year (and fourth year if you are on the MEng), you complete two pieces of coursework in your first term and one <em>mini-project</em> in your second term.</li>
            <li>You complete your degree with a large individual project in your final term. On the MEng, you also take a more advanced group software project in your third year.</li>
        </ul>    
        <p>Our degrees are accreded by <a href="www.bcs.org">BCS, the British Computing Society</a> who are the professional body for computing in the United Kingdom.</p>        
        <h2>Structure of the Degree</h2>
        <p>The first two years are common to the BSc and MEng degrees. In these years, you learn the basics of programming in different approaches and languages, including <em>Imperative Programming (C language)</em>, <em>Functional Programming (Haskell language)</em>, <em>Object-Oriented Programming (Java language)</em> and <em>Concurrent Programming (Go language)</em>.</p>
        <p>You will also learn the foundations of algorithms and data structures, data science, programming language and compiler design, system administration on Linux, design and user testing, and computer architecture.</p>
        <p>In your first year you will also take two mathematics units that teach you the mathematical skills you may need in your optional units in later years.</p>
        <p>On the BSc, in third year you take two coursework options and three exam-based options in your first term, and in second term you complete a final project (dissertation) worth 2/3 of the term and a mini-project worth 1/3 of the term. You do not have any final exams at the end of your degree.</p>
        <p>On the MEng, you take an advanced group software project in the second term instead of a dissertation. In fourth year, the structure is the same as for 3rd year BSc but you pick your units from a different menu of more advanced options.</p>
        <h2>Assessment</h2>
        <p>Assessment at Bristol is a mix of coursework, written exams, vivas (oral exams) and class tests. On some units, you may submit work and then give a presentation or take an oral exam on the work you submitted.</p>
        <p>Written exams take place in separate exam periods after each term. Coursework and class tests take place during term. Vivas are arranged separately for each unit and may take place during term or during the exam periods.</p>
        <p>Your first year does not count towards your final degree classification. For the BSc, the degree weightings are 25% Year 2 and 75% Year 3, and for the MEng they are 10% Year 2, 40% Year 3 and 50% Year 4.</p>
    </body>
</html>
```

### What is stylesheet?

A stylesheet is a file or a set of rules that defines the appearance, layout, and formatting of a document, typically written in HTML or XHTML. In the context of web development, the term "stylesheet" usually refers to a Cascading Style Sheet (CSS) file.

A stylesheet contains a series of CSS rulesets, which consist of selectors and declaration blocks. Selectors are used to target specific HTML elements on the page, while declaration blocks contain one or more declarations that define the styles for those elements. Each declaration consists of a CSS property and its corresponding value.

Here's an example of a simple CSS stylesheet:

```css

/* This is a CSS comment */
body {
  font-family: Arial, sans-serif;
  background-color: lightgray;
}

h1 {
  color: darkblue;
  font-size: 32px;
}

p {
  color: black;
  font-size: 16px;
}
```

In this example, the stylesheet contains rulesets for the **`body`**, **`h1`**, and **`p`** elements. The **`body`** ruleset sets the font family and background color for the entire page, while the **`h1`** and **`p`** rulesets define the color and font size for the headings and paragraphs, respectively.

When a browser loads an HTML document, it also loads any linked stylesheets and applies the CSS rules to the corresponding elements on the page. This process determines the visual appearance of the content, including colors, fonts, layout, and other styles.

External stylesheets are typically stored in separate files with the ".css" file extension and are linked to an HTML document using the **`<link>`** element in the **`<head>`** section:

```html

<!DOCTYPE html>
<html>
<head>
  <title>Example Page</title>
  <link rel="stylesheet" type="text/css" href="styles.css">
</head>
<body>
  <h1>Welcome to the Example Page</h1>
  <p>This is a paragraph of text.</p>
</body>
</html>
```

In this example, the **`styles.css`** file is an external stylesheet that is linked to the HTML document.

## Reading Mode

Many browsers have a *reading mode* which is meant to make text as easy to read as possible. Let's simulate this - create a new link to a stylesheet in the header (call it something like `sometext.css`) and insert the following:

```css

body {
    margin: 0 auto;
    max-width: 40em;
    line-height: 125%;
}
```

This already looks much better, but you can play with the parameters to get something that's perfect for you.

1. create a file called sometext.css and add those line in, maybe we can do more extension like, but maybe we can stick on the exercise first. 

```css
/* sometext.css */
body {
  font-family: Georgia, serif;
  font-size: 18px;
  line-height: 1.6;
  color: #333;
  background-color: #f7f2e8;
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

h1, h2, h3, h4, h5, h6 {
  font-weight: bold;
  margin: 1em 0;
}

h1 {
  font-size: 32px;
}

p, ul, ol {
  margin: 1em 0;
}

a {
  color: #1a0dab;
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}

img {
  max-width: 100%;
  height: auto;
}
```

1. We need to link the “sometext.css” with sometext.html by adding the link in: 
    
    ![截屏2023-03-16 16.22.16.png](3%201%20Styling%20Text(EX)%2082ac99237dac44cf9ef22895e6ad8fb9/%25E6%2588%25AA%25E5%25B1%258F2023-03-16_16.22.16.png)
    

Some explanations with the setting:

- The `max-width` is doing most of the work here, following the design principle (that's fairly well replicated with studies) that most people find text easier to read if lines are not much longer than some limit, quoted variously as [around 60 characters](https://baymard.com/blog/line-length-readability). Since an 'm' is wider than the average character and `em` rather than e.g. `px` is the correct thing to use here (as it's relative to the font being used), I went for 40em.
- The `margin: 0 auto` centers content horizontally if it has a fixed width. The space around the text both gets the left margin away from the edge of the window, and gives the eye an area around the text free of distractions.
- Increasing the line height follows the same principle, sometimes known as giving the text *room to breathe*. Experiment with different line heights if you like to see which one suits you best. Note: it's possible to overdo this. Double-spacing (`line-height: 200%`) was common for dissertations in the typewriter era, mainly to give proofreaders and markers space to write comments between the lines. This is considered bad design nowadays, and you should not do it.

If you want, you can try a few other things:

- Change the `font-size`. The default is `16px` but depending on your screen size, resolution and distance from your eyes you might want a larger one.
- Set a different `font-family`. The values `serif` and `sans-serif` give default choices across all operating systems, you could set this to a more specific font on yours such as `Calibri` (if on Windows) but bear in mind this will not work for Mac users.
- Set a `background-color` on the body, either a light but not quite white one (pale yellow/brown is often used), or go dark mode with a dark background and a light `color` for the font itself.

### we can make changes based on this:

```css
body {
    font-family: Calibri, Arial, sans-serif;
    font-size: 20px;
    line-height: 1.8; /* Increased line height for better readability */
    color: #f0f0f0; /* Changed text color to white */
    background-color: #222222; /* Changed background color to black */
    max-width: 40em; /* which is 640px */
    margin: 0 auto;
    padding: 20px;
}
```

Therefore, based on the changes we’ve made, our page would look like this: 

![截屏2023-03-16 16.37.55.png](3%201%20Styling%20Text(EX)%2082ac99237dac44cf9ef22895e6ad8fb9/%25E6%2588%25AA%25E5%25B1%258F2023-03-16_16.37.55.png)

**Advanced note:**

Tricks like this- which you can code as a browser extension if you want to - might be particularly helpful for visually impaired or dyslexic students so you can force any website to use fonts and styles that work for you.

If you are designing for dyslexic **诵读困难的** people other than yourself, the best you can do is give them a way to configure the fonts and colours themselves (for example with a menu that lets you change them via JavaScript) - different dyslexic people might have different preferences that work for them, for example one person may prefer serif fonts to sans-serif or the other way round, there is no one best design for everyone.

There are statistical trends which mean that "use sans serif fonts" is good advice if you have to pick one font (for example for printed material) but one of the advantages of the web is that you do not have to choose one font in advance, you can let different users select different preferences.

For this task, maybe we can 

1. Create a button that can enable the reading mode. (Notice we add link to the sometext.css)

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8" />
        <title>Some Text</title>
<!--        <link rel="stylesheet" href="reset.css" />-->
<!--        <link rel="stylesheet" type="text/css" href="sometext.css"> // this is to link the basic readmode-->
        <link id="mainStylesheet" rel="stylesheet" type="text/css" href="sometext.css" disabled>
<!--        <link id="readingModeStylesheet" rel="stylesheet" type="text/css" href="reading-mode.css"> // this is to link the reading mode-->
        <script src="sometext.js"></script>
    </head>
    <body>
        <h1>Computer Science at the University of Bristol</h1>
        <p>The BSc and MEng Computer Science programmes provide you with a solid and <em>practical</em> introduction to the fundamentals of Computer Science, followed by opportunities to specialise in exciting research areas including Machine Learning, Human-Computer Interaction and Computational Neuroscience.</p>
        <button id="toggleReadingMode">Toggle Reading Mode</button>
        //省略中间的代码啦
        <script src="toggleReadingMode.js"></script>
    </body>
</html>
```

1. Write a toggleReadingMode.js

```jsx
const toggleReadingMode = document.getElementById('toggleReadingMode');
const mainStylesheet = document.getElementById('mainStylesheet');
const readingModeStylesheet = document.getElementById('readingModeStylesheet');

let readingModeEnabled = false;

toggleReadingMode.addEventListener('click', () => {
    readingModeEnabled = !readingModeEnabled;

    if (readingModeEnabled) {
        mainStylesheet.disabled = true;
        readingModeStylesheet.disabled = false;
    } else {
        mainStylesheet.disabled = false;
        readingModeStylesheet.disabled = true;
    }
});
```

## Starting from Scratch

Uncomment the line that includes `reset.css` in the HTML file (comments go from `<!--` to `-->`, a relic of when HTML was connected with XML). The file is at [resources/reset.css](https://cs-uob.github.io/COMSM0085/exercises/part2/resources/reset.css) so download it to the same folder as your HTML file.

![截屏2023-03-16 17.08.43.png](3%201%20Styling%20Text(EX)%2082ac99237dac44cf9ef22895e6ad8fb9/%25E6%2588%25AA%25E5%25B1%258F2023-03-16_17.08.43.png)

You now have almost no styling at all: headings, lists, paragraphs all just look like text.

![截屏2023-03-16 17.22.39.png](3%201%20Styling%20Text(EX)%2082ac99237dac44cf9ef22895e6ad8fb9/%25E6%2588%25AA%25E5%25B1%258F2023-03-16_17.22.39.png)

In your own stylesheet, which you should include *after* `reset.css`, either try and recreate the default settings or try out ones that look good to you.

Headings are meant to stand out among the paragraphs, and the extra white space around them (padding or margin) is as important as the larger font size and bold font. You could try leaving headings the same size as the body font but still `font-weight: bold` and use just padding to make them stand out. (Since a heading relates to the text after it not the text before it, it is good design to have a greater margin/padding above the heading than below it.)

The default body font size is `font-size: 16px`. If you want to make the headings larger, you should not set an absolute value (such as 24px) but one relative to the default size. Since the default size comes from the `<html>` and `<body>` elements, you have two ways to do this: either with a percentage e.g. `h1 { font-size: 150%; }` which makes headings 1.5 times as big as the paragraph font, or using the `em/rem` units (setting a font size in ems refers to the em size of the parent unit).

```css
/* http://meyerweb.com/eric/tools/css/reset/ 
   v2.0 | 20110126
   License: none (public domain)
*/

html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed, 
figure, figcaption, footer, header, hgroup, 
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
	margin: 0;
	padding: 0;
	border: 0;
	font-size: 100%;
	font: inherit;
	vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure, 
footer, header, hgroup, menu, nav, section {
	display: block;
}
body {
	font-size: 16px;
	line-height: 1.5;
	font-family: Arial, sans-serif;
	color: #333;
	padding: 20px;
}
ol, ul {
	margin-bottom: 1em;
	padding-left: 1.5em;
}
blockquote, q {
	quotes: none;
}
h1 {
	font-size: 1.5em;
}

h2 {
	font-size: 1.25em;
}

p {
	margin-bottom: 1em;
}
a {
	color: #0066cc;
	text-decoration: none;
} /*anchor*/

a:hover {
	text-decoration: underline;
}
blockquote:before, blockquote:after,
q:before, q:after {
	content: '';
	content: none;
}
table {
	border-collapse: collapse;
	border-spacing: 0;
}
```

In the browser, open the developer tools and type the following in the console 控制台 and press ENTER:

```css

document.body.style.fontSize="24px";

```

![截屏2023-03-16 17.33.12.png](3%201%20Styling%20Text(EX)%2082ac99237dac44cf9ef22895e6ad8fb9/%25E6%2588%25AA%25E5%25B1%258F2023-03-16_17.33.12.png)

(Since this is JavaScript, the property is called `fontSize` not `font-size` as dashes are not allowed in identifiers.)

This increases the body text size from 16px to 24px (if you have manually set a different size in your stylesheet, you might need to set it to `"24px !important"` to override this). If you had set your headings to fixed sizes like 18px, then headings would now be smaller than the body text - if you have correctly used relative sizing, then headings will now still be 1.5 times as big as the body fonts or whichever multiple you set them to be. That is the right way to do it.

## Vertical Rhythm

![https://zellwk.com/images/2016/why-vertical-rhythm/baseline-print.png](https://zellwk.com/images/2016/why-vertical-rhythm/baseline-print.png)

Here is another design principle worth knowing about. Look at this image, part of a screenshot of one way to style the text on the page:

![https://cs-uob.github.io/COMSM0085/exercises/part2/css/rhythm1.png](https://cs-uob.github.io/COMSM0085/exercises/part2/css/rhythm1.png)

The principle here is that we imagine a grid with 20px high lines, and lay out everything according to that. Under [resources/baseline.png](https://cs-uob.github.io/COMSM0085/exercises/part2/resources/baseline.png) there is an image 1px wide and 20px high with the last pixel coloured pink. Download that image to the folder with the HTML file and set

```

body {
    background-image: url("baseline.png");
}

```

![截屏2023-03-16 17.38.09.png](3%201%20Styling%20Text(EX)%2082ac99237dac44cf9ef22895e6ad8fb9/%25E6%2588%25AA%25E5%25B1%258F2023-03-16_17.38.09.png)

This will make the image repeat horizontally and vertically, and you can now see the design behind this approach:

![https://cs-uob.github.io/COMSM0085/exercises/part2/css/rhythm2.png](https://cs-uob.github.io/COMSM0085/exercises/part2/css/rhythm2.png)

The baselines of the paragraph text all sit on the grid lines. The important thing here is that when a heading interrupts the flow of text, the total height of the heading is an exact multiple of the grid height, even if the font size is different.

Try and recreate this layout or a similar one using vertical rhythm, starting from the reset stylesheet so you have to do everything yourself from scratch. Notes:

- The aim is that all paragraphs have their baselines on the grid, even if there are other elements (headlings, lists) earlier in the document.
- This means that the total height of headings must be an exact multiple of the grid size; you can assume that the text in a heading does not require more than one line.
- You should set all sizes, including margins and padding, in terms of relative units (either ems/rems or percentages).
- The base font size here is the default 16px. Start with the max-width and line-height from the first example, and modify the line height if necessary for your font to get the lines of paragraph text the right distance apart.
- The paragraphs themselves have a margin at the bottom (the empty line after the first paragraph) that also appears between paragraphs of text (not shown in the image) when one `<p>` tag follows another. You might also need to give them a small top padding to get the text on the lines, not between them.
- The shading around the headings is `background-color: rgba(0, 0, 255, 0.25);` to be semitransparent and let the lines show through, to see that while the heading text itself doesn't have to sit on a grid line, the total height of a heading including padding does respect the grid. However this shading is just to motivate the layout: if you want an actual coloured background, then you should set a `padding-left: 0.5em;` or something on the headings to make the text not start just on the edge of a coloured box. This improves readability.
- You will also need to style the `<ul>` list to have some spacing before and after, and to keep everything on the grid lines. You get the bullets back with the following code - or one of many other options [listed on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/list-style):

```css

ul {
    padding-left: 2em; /* the bullets appear in the padding */
    list-style-type: disc;
    list-style-position: outside;
}
```

- Don't forget to style the link. `text-decoration: underline` is one option; or you can read more on MDN about [styling links](https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text/Styling_links) including how to make a link someone has visited before look different to a new one.

还是没有弄好，下次再看一看