# 5.3 Dynamic Structure p1

When you point your browser at `app.html`, the "Initialising..." string appears in the left of the screen (the `<nav>`) only for a fraction of a second. This is the time it takes to load and execute the code in `script.js`, which provides the dynamic behaviour of the app.

### Making some buttons

Indeed, looking at `script.js` we notice that it goes straight into business:

```jsx
window.onload = function () {
  let wards = fetch('https://opendata.bristol.gov.uk/api/v2/catalog/datasets/wards/records?limit=50&select=name,ward_id')
    .then(response => response.json())
    .then(populateWards)
    .catch(err => console.log(err));
}
```

This fragment of code creates a function, and assigns it to `[window](https://developer.mozilla.org/en-US/docs/Web/API/Window)`.`[onload](https://developer.mozilla.org/en-US/docs/Web/API/GlobalEventHandlers/onload)`. This means that this function, which takes no arguments, will be called when the browser window has finished loading the page.

The body of the function makes an HTTP request to the Bristol City Council API. This returns a promise; when it is resolved, it is parsed as JSON, which itself creates another promise. Finally, when *that* promise is resolved, the `populateWards`function is called with the fetched JSON as argument. If any of these steps cause an error, the last line catches it, and prints it on the console (only visible if you press F12). These four lines are a modern JavaScript idiom that uses all the latest technology: the fetch API; promises; and higher-order, anonymous functions.

One might wonder: what will the input passed to `populateWards` in this call look like? To answer this we can peek at the above URL and see what it returns: on any Linux machine we may run

```bash
curl -X 'GET' 'https://opendata.bristol.gov.uk/api/v2/catalog/datasets/wards/records?select=name,ward_id' | json_pp | less
```

and the result might look like this:

![截屏2023-04-13 20.02.04.png](5%203%20Dynamic%20Structure%20p1%204fae27943aab4bc6be569c976157c4aa/%25E6%2588%25AA%25E5%25B1%258F2023-04-13_20.02.04.png)

which will make a `GET` request at this URL, parse the result as JSON (`json_pp`), and display it in scrollable format (`less`). The result looks a lot like this:

```bash
{
   "links" : ...,
   "records" : [
      {
         "links" : ...,
         "record" : {
            "fields" : {
               "name" : "Eastville",
               "ward_id" : "E05010897"
            },
            "id" : "996b607b4c31e6aca6a7614bd02ea18a4c14c525",
            "size" : 40500,
            "timestamp" : "2020-09-03T10:02:58.597Z"
         }
      },
      {
         "links" : ...,
         "record" : {
            "fields" : {
               "name" : "Southville",
               "ward_id" : "E05010914"
            },
            "id" : "bc2f85ccc34ca606a2fe6473491b5fc50fd4e0d1",
            "size" : 25544,
            "timestamp" : "2020-09-03T10:02:58.597Z"
         }
      },
      ...
   ],
   "total_count" : 34
}
```

I have abbreviated the `links`fields, which add a lot of noise to the output. We can thus see that this HTTP request returns a JSON object which contains the names and ward IDs of all the wards of the city of Bristol! The final field returns the total record count, which is 34.

我已经缩写了`links`字段，这给输出增加了很多噪音。因此我们可以看到，这个 HTTP 请求返回了一个 JSON 对象，其中包含布里斯托尔市所有选区的名称和选区 ID！最后一个字段返回总记录数，即 34。

![截屏2023-04-13 20.04.26.png](5%203%20Dynamic%20Structure%20p1%204fae27943aab4bc6be569c976157c4aa/%25E6%2588%25AA%25E5%25B1%258F2023-04-13_20.04.26.png)

Unlike SQL databases, which come with a strongly-typed data schema, the data here is semi-structured at best. We may discern its structure by looking at the above output. The top-level object has a `records`field, which contains an array of records. Each of these records is a JSON object itself. Its `record`field contains a field called `fields`, which contains the `name` and `ward_id`of each ward.

与带有强类型数据模式的 SQL 数据库不同，这里的数据充其量是半结构化的。我们可以通过查看上面的输出来辨别它的结构。顶级对象有一个`records`字段，其中包含一个记录数组。这些记录中的每一个都是一个 JSON 对象本身。它的`record` 字段包含一个名为 的字段`fields`，其中包含每个ward的`name`和`ward_id` 。

Advanced note

One might ask: how did I figure out the correct URL to obtain all the wards?

Unlike relational databases, where a predetermined schema tells the developer exactly where to look, the situation with APIs is more of a trial-and-error affair. Many APIs you will have to use in your life are poorly documented, and using them invovles some guesswork.

In this particular instance, I went on the [Open Data Bristol](https://opendata.bristol.gov.uk/explore/?sort=modified) website, and looked through the available datasets. There I found a dataset called ['Wards'](https://opendata.bristol.gov.uk/explore/dataset/wards/information/). The description seemed to match what I wanted, which was confirmed by clicking on the 'Table' tab, and seeing some sample data.

Using the 'API' tab on the same page is misleading, as it presents an interface for querying the old version (v1) of their API. Following the link to the ['full API console'](https://opendata.bristol.gov.uk/api/v2/console) reveals that there is a modern, REST-type API (v2), described in a format known as [OpenAPI](https://swagger.io/docs/specification/about/). This is the current industry standard for describing REST APIs.

Looking through the documentation, it was evident that the endpoint of interest is

```bash

/catalog/datasets/{dataset_id}/records
```

I replaced `{dataset_id}` with the id of the ward dataset (`wards`). I also passed in two query parameters:

- `limit=50` which limits the response to contain at most 50 data points in the JSON object (which is way more than the Bristol wards)
- `select=name,ward_id` which limits the fields in the response to those in which we are interested

To test this I used variations of the above `curl` command, and looked at the output.

Now that we understand the structure of the data returned from that endpoint, we can go ahead and write the `populateWards`function:

```jsx
function populateWards(wards) {
  let buttons = new DocumentFragment();
//The first line creates a [DocumentFragment](https://developer.mozilla.org/en-US/docs/Web/API/DocumentFragment) called buttons.

  wards.records.forEach(w => {
      const [id, name] = [w.record.fields.ward_id, w.record.fields.name];
      const b = document.createElement("button");
      b.textContent = name;
      b.onclick = displayData(id, name);
      buttons.appendChild(b);
  });
  
  let nav = document.getElementById("nav");
  nav.textContent = '';
  nav.append(buttons);
}
```

This function is a callback that will receive the JSON object containing ward names.

The first line creates a `[DocumentFragment](https://developer.mozilla.org/en-US/docs/Web/API/DocumentFragment)` called `buttons`. Loosely speaking, this is an object that can be used to collect a bunch of stuff that will be added to a page. When creating many new elements on a page it is prudent to add them to a `DocumentFragment` first, and only then add it to the page. That way they will all appear on the page at roughly the same time, and the user will not see new elements appear on the page one after the other.

The next part of the function iterates through every ward. First, it extracts the `id` and `name` fields. Then, it creates a new `<button>`, and sets its text to be the name of the ward. When each of these buttons is clicked, the function returned by the call to `displayData` will be run. Each new button is then added to the `DocumentFragment` using the `[appendChild](https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild)` function.

Finally, the `<nav>` is obtained by using its ID. Its contents are deleted, and replaced by the `DocumentFragment` containing all these new buttons, by using the [append](https://developer.mozilla.org/en-US/docs/Web/API/Element/append) function.

In short, this is the bit of code that creates the buttons on the navigation section on the left!

<aside>
💡 Of course, someone could argue that the wards of Bristol do not change very often, and that as a consequence it is slow and wasteful to perform an HTTP request to obtain a list of wards; it would be much better to simply hard-code these buttons and their names into the app. This developer could well be right.

</aside>

Before any modification, our code looks like this:

![截屏2023-04-13 20.17.27.png](5%203%20Dynamic%20Structure%20p1%204fae27943aab4bc6be569c976157c4aa/%25E6%2588%25AA%25E5%25B1%258F2023-04-13_20.17.27.png)

Exercise:

1. Modify the code above so that each button is on a separate line.

```jsx
// Make each button appear on a separate line
      b.style.display = 'block';
```

1. Modify the code above so that buttons appear in alphabetical order.

```jsx
// Sort the wards alphabetically
    wards.records.sort((w1, w2) => w1.record.fields.name.localeCompare(w2.record.fields.name));
```

1. The linesets a button's `[onclick](https://developer.mozilla.org/en-US/docs/Web/API/GlobalEventHandlers/onclick)`property to be a newly-created function. Sometimes this is undesirable. For example, if another script had already added some code for what should happen when a button is clicked, this would completely replace it. Change this line so that it instead adds an `[EventListener](https://developer.mozilla.org/en-US/docs/Web/API/EventListener)` to `b`, so that it simply adds functionality, without interfering with other code.
    
    ```jsx
    
    b.onclick = displayData(id, name);
    ```
    

```jsx
// Use addEventListener instead of setting onclick property
    b.addEventListener('click', displayData(id, name));
```

[*Hint.* Exercises 1 and 2 can be completed by adding one line of code for each. For the second one, use `[Array.sort](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)`].

After modification, our code looks like this:

![截屏2023-04-13 20.19.21.png](5%203%20Dynamic%20Structure%20p1%204fae27943aab4bc6be569c976157c4aa/%25E6%2588%25AA%25E5%25B1%258F2023-04-13_20.19.21.png)