# MDN-Normal flow(ER)

- Normal flow is the default layout for CSS elements.
- By default, block-level elements are laid out in the block flow direction, which is based on the parent's writing mode.
- Inline elements sit on the same line along with adjacent text nodes, if there is space on the same line.
- Collapsing margins is only relevant in the vertical direction.
- Understanding normal flow makes it easier to modify the behavior of elements in the future.

<aside>
💡 Key words: Normal flow; Block-level elements; Inline elements; Collapsing margins; Box model; Writing mode; Parent element; Adjacent text; Overflowing content; Margin collapsing

</aside>

# Normal Flow

This article explains normal flow, or the way that webpage elements lay themselves out if you haven't changed their layout.

As detailed in the last lesson introducing layout, elements on a webpage lay out in normal flow if you haven't applied any CSS to change the way they behave. And, as we began to discover, you can change how elements behave either by adjusting their position in normal flow or by removing them from it altogether. Starting with a solid, well-structured document that's readable in normal flow is the best way to begin any webpage. It ensures that your content is readable even if the user's using a very limited browser or a device such as a screen reader that reads out the content of the page. In addition, since normal flow is designed to make a readable document, by starting in this way you're working *with* the document rather than struggling *against* it as you make changes to the layout.正如在介绍网页布局的上一课所述，如果您没有应用任何CSS来改变元素的行为，那么网页上的元素将按照正常流程布局。同时，正如我们开始发现的那样，您可以通过调整元素在正常流程中的位置或将其完全从中删除来改变它们的行为方式。从一个结构良好、可读性强的文档开始，是开始任何网页的最佳方式。这确保了即使用户使用非常有限的浏览器或屏幕阅读器等设备来阅读页面内容，您的内容也是可读的。此外，由于正常流程旨在生成可读文档，通过这种方式开始，您正在与文档一起工作，而不是在对布局进行更改时与文档对抗。

Before digging deeper into different layout methods, it's worth revisiting some of the things you have studied in previous modules with regard to normal document flow.在深入研究不同的布局方法之前，重新审视一下您在以前模块中学习的有关正常文档流的一些内容是值得的。

## How are elements laid out by default?

The process begins as the boxes of individual elements are laid out in such a way that any padding, border, or margin they happen to have is added to their content. This is what we call the **box model**. 该过程开始时，单个元素的框被布置在一起，以便任何填充、边框或边距都被添加到它们的内容中。这就是我们所说的**盒模型**。

By default, a [block level element](https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level_elements)'s content fills the available inline space of the parent element containing it and the element grows along the block dimension to accommodate its content. The size of [inline elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Inline_elements) is just the size of their content. You can't set width or height on inline elements — they just sit inside the content of block level elements — except for images. Unlike other inline elements, images can be resized without changing their `display` property. If you want to control the size of an inline element in this manner, you need to set it to behave like a block level element (e.g., with `display: block;` or `display: inline-block;`, which mixes characteristics from both).默认情况下，[块级元素](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Block-level_elements)的内容填充包含它的父元素的可用内联空间，元素沿块维度增长以容纳其内容。[内联元素](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Inline_elements)的大小仅仅是它们的内容大小。您无法在内联元素上设置宽度或高度——它们只是处于块级元素的内容中——除了图像。与其他内联元素不同，图像可以调整大小而不改变其`display`属性。如果您想以这种方式控制内联元素的大小，您需要将其设置为像块级元素一样的行为（例如，使用`display: block;`或`display: inline-block;`，它混合了两者的特性）。

That explains how elements are structured individually, but how about the way they're structured when they interact with one another? The normal layout flow (mentioned in the layout introduction article) is the system by which elements are placed inside the browser's viewport. By default, block-level elements are laid out in the *block flow direction*, which is based on the parent's [writing mode](https://developer.mozilla.org/en-US/docs/Web/CSS/writing-mode) (*initial*: horizontal-tb). Each element will appear on a new line below the last one, with each one separated by whatever margin that's been specified. In English, for example, (or any other horizontal, top to bottom writing mode) block-level elements are laid out vertically. 这解释了单独构建元素的方式，但是它们相互作用时该如何结构化呢？正常的布局流程（在布局介绍文章中提到）是指将元素放置在浏览器视窗内的系统。默认情况下，块级元素在块流方向上布局，这基于父元素的书写模式（*initial*：horizontal-tb）。每个元素将出现在上一个元素的下方一行，每个元素之间用指定的间距分隔。例如，在英语中（或其他水平，从上到下的书写模式中），块级元素垂直布局。

Inline elements behave differently. They don't appear on new lines; instead, they all sit on the same line along with any adjacent (or wrapped) text content as long as there is space for them to do so inside the width of the parent block level element. If there isn't space, then the overflowing content will move down to a new line. 内联元素的行为不同。它们不会出现在新行上；相反，只要在父级块级元素的宽度内有空间，它们就与任何相邻（或包装）文本内容一起位于同一行上。如果没有空间，溢出的内容将移到新行上。

If two vertically adjacent elements both have a margin set on them and their margins touch, the larger of the two margins remains and the smaller one disappears. This is known as **[margin collapsing](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing)**. Collapsing margins is only relevant in the **vertical direction**. 如果两个垂直相邻的元素都设置了外边距，并且它们的外边距触摸到了一起，那么较大的外边距将保留，较小的外边距将消失。这被称为**[外边距折叠](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing)**。外边距折叠仅在**垂直方向**上才相关。

Let's look at a simple example that explains all of this:

```css
<h1>Basic document flow</h1><p>
  I am a basic block level element. My adjacent block level elements sit on new
  lines below me.
</p><p>
  By default we span 100% of the width of our parent element, and we are as tall
  as our child content. Our total width and height is our content + padding +
  border width/height.
</p><p>
  We are separated by our margins. Because of margin collapsing, we are
  separated by the width of one of our margins, not both.
</p><p>
  Inline elements <span>like this one</span> and <span>this one</span> sit on
  the same line along with adjacent text nodes, if there is space on the same
  line. Overflowing inline elements will
  <span>wrap onto a new line if possible (like this one containing text)</span>,
  or just go on to a new line if not, much like this image will do:
  <img src="long.jpg" alt="snippet of cloth" /></p>
```

```css
body {
  width: 500px;
  margin: 0 auto;
}

p {
  background: rgba(255, 84, 104, 0.3);
  border: 2px solid rgb(255, 84, 104);
  padding: 10px;
  margin: 10px;
}

span {
  background: white;
  border: 1px solid black;
}

```

![截屏2023-04-11 18.07.32.png](MDN-Normal%20flow(ER)%20f4ab72f096cb46348c0e8b7c82fc5acc/%25E6%2588%25AA%25E5%25B1%258F2023-04-11_18.07.32.png)

## Summary

In this lesson you've learned the basics of normal flow — the default layout for CSS elements. By understanding how inline elements, block elements, and margins behave by default, it'll be easier to modify their behavior in the future.