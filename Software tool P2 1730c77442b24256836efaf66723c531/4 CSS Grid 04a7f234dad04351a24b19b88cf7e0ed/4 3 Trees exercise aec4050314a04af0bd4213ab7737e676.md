# 4.3 Trees exercise

The task is to make page looks like this in the end:

On media that is 600px or wider, the page should look like this:

![截屏2023-04-12 19.23.10.png](4%203%20Trees%20exercise%20aec4050314a04af0bd4213ab7737e676/%25E6%2588%25AA%25E5%25B1%258F2023-04-12_19.23.10.png)

From 400px to 600px, the page should show all trees except the "featured" ones in two columns:

![截屏2023-04-12 19.23.42.png](4%203%20Trees%20exercise%20aec4050314a04af0bd4213ab7737e676/%25E6%2588%25AA%25E5%25B1%258F2023-04-12_19.23.42.png)

And below 400px width, all trees should be shown in a single column layout, whether featured or not.

## Exercise

General non-grid-related CSS that you can just paste in:

looks like this ⬇️ after paste the code in:

![截屏2023-04-12 19.24.39.png](4%203%20Trees%20exercise%20aec4050314a04af0bd4213ab7737e676/%25E6%2588%25AA%25E5%25B1%258F2023-04-12_19.24.39.png)

- The grid should be horizontally centered if the screen is wider than the grid, by setting `margin: 0 auto` on the container.

```css
.container {
    margin: 20px auto;
    padding: 0 10px;
}
```

- The grid should be applied to the container div, **with a margin of 20px on top and bottom** (this has to come after the horizontal centering), and **a padding of 10px on left and right** (this has to be padding, not margin, to avoid undoing the centering again).
- Set a grid gap of 20px.

```css
.container {
    display: grid;
    grid-gap: 20px;
    margin: 20px auto;
    padding: 0 10px;
}
```

- If the screen is **at least 600px** wide, then the container should have a **maximum width of 960px** and ***four*** equally wide columns. **Featured trees should take up a 2x2 space on the grid, all other trees a 1x1 space.**

```css
**@media (min-width: 600px) {**
.container {
    ...//上面的内容
    max-width: 960px;
    grid-template-columns: repeat(*4*, 1fr);
}

.card.featured {
    grid-column: span 2;
    grid-row: span 2;
}
```

- Between 400px and 600px, the grid should **only be *two* columns wide**, trees still take up 2x2 space if featured and **1x1 otherwise.**

```css
@media (min-width: 400px) {
    .container {
        max-width: 600px;
        grid-template-columns: repeat(*2*, 1fr);
    }
}
```

- Below 400px, make a grid with only **one** column, and all trees take up **1x1 space**. Note that you do not need to do anything for this as this is the default - just make sure that your other grid rules such as making featured trees 2x2 only apply on larger screens.

```css
@media (max-width: 400px) {
    .card.featured {
        grid-template-columns: 1fr;
    }
}
```

After finishing the code:

![截屏2023-04-12 19.53.23.png](4%203%20Trees%20exercise%20aec4050314a04af0bd4213ab7737e676/%25E6%2588%25AA%25E5%25B1%258F2023-04-12_19.53.23.png)

and we can check for the view in mobile phone:

![截屏2023-04-12 19.54.12.png](4%203%20Trees%20exercise%20aec4050314a04af0bd4213ab7737e676/%25E6%2588%25AA%25E5%25B1%258F2023-04-12_19.54.12.png)

For smaller view:

![截屏2023-04-12 19.55.04.png](4%203%20Trees%20exercise%20aec4050314a04af0bd4213ab7737e676/%25E6%2588%25AA%25E5%25B1%258F2023-04-12_19.55.04.png)