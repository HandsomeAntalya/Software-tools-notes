# 5.4 Dynamic Structure, p2

The rest of `script.js` is concerned with displaying data about a given ward in the `<main>`
 section of the page. In fact, it consists of just one function, called `displayData`. Let us look at its structure, whilst eliding some of its implementation details:

```jsx
function displayData(id, name) {
  
  function buildPopulation(records) {
    ...
  }

  return function () {
    ...
  }
}
```

When called with two arguments `id` and `name`, the function `displayData` does two things:

1. It defines a [nested function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions#nested_functions_and_closures) called `buildPopulation`. This is a function whose definition is *local* to `displayData`: it can only be used within its body, but not in the rest of the program. However, this function is allowed to refer to the arguments of its enclosing function (i.e. `id` and `name`). We sometimes call this an *auxiliary function* **/ ɔːɡˈzɪliəri ˈfʌŋkʃn / 辅助函数**, or a *helper function*.
2. It returns an anonymous [arrow function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions#arrow_functions). Thus, `displayData` will return... a newly defined, anonymous function! Recall that in the previous part of the script, `displayData` was used only in one line, namely`b` is a button, and its `onclick` property is a function that will be run when it is clicked. Thus, `displayData` should return a function. To construct such a function we need to know the `id` and `name` of the ward whose data is to be displayed, so `displayData` needs to take them as parameters.
    
    ```jsx
    
       b.onclick = displayData(id, name);
    ```
    
    `b`is a button, and its `onclick` property is a function that will be run when it is clicked. Thus, `displayData`should return a function. To construct such a function we need to know the `id`and `name`of the ward whose data is to be displayed, so `displayData`needs to take them as parameters.
    
    Both of these constitute examples of functional programming in action.
    
    Let us now look in more detail in the function that is returned:
    
    ```jsx
    function displayData(id, name) {
      
      function buildPopulation(records) {
        ...
      }
    
      return function () {
        let wards = fetch(`https://opendata.bristol.gov.uk/api/v2/catalog/datasets/population-estimates-time-series-ward/records?limit=20&select=mid_year,population_estimate&refine=ward_2016_code:${id}`)
          .then(response => response.json())
          .then(data => {
            let heading = document.createElement('h1');
            heading.innerText = name;
            
            let population = buildPopulation(data.records);
    
            let dataPane = document.getElementById("dataPane");
            dataPane.textContent = '';
            dataPane.append(heading, population);
          })
          .catch(err => console.log(err));
      }
    }
    ```
    
    The pattern here is much the same as before: an HTTP request is made, its response is parsed as JSON, and then processed.
    
    这里的模式与之前的模式非常相似：发出 HTTP 请求，将其响应解析为 JSON，然后进行处理。
    
    The endpoint is determined as before, but now asks for data from the `[population-estimates-time-series-ward](https://opendata.bristol.gov.uk/explore/dataset/population-estimates-time-series-ward/information/?disjunctive.ward_2016_name)`dataset, which contains estimates of the population that lives in each Bristol ward. We extract only the `mid_year` and `population_estimate`fields, which contain the year in the middle of which the population is estimated, and the actual estimate itself. We also use a new feature of the API, namely the `refine`query parameter. This allows us to extract only records one of whose *facets*(i.e. fields of data) has a particular value. At this point in our code, we know the variable `id`holds the ID of the ward whose population we want to display, say `E05010914`for Southville. By peeking in some sample data, we can work out that if we pass the query parameter.
    
    端点像以前一样确定，但现在要求从 `[population-estimates-time-series-ward](https://opendata.bristol.gov.uk/explore/dataset/population-estimates-time-series-ward/information/?disjunctive.ward_2016_name)` 数据集中获取数据，其中包含居住在每个布里斯托尔选区的人口估计值。我们仅提取`mid_year`和`population_estimate`字段，其中包含人口估计中间的年份，以及实际估计本身。我们还使用了 API 的一个新功能，即 `refine`查询参数。这允许我们只提取其中一个 *方面*（即数据字段）具有特定值的记录。此时在我们的代码中，我们知道该变量`id`包含我们要显示其人口的病房的 ID，例如`E05010914`Southville。通过查看一些示例数据，我们可以计算出如果我们传递查询参数
    
    ```jsx
    refine=ward_2016_code:E05010914
    ```
    
    The value `E050109141` is presumably stored in the `id`argument. However, `id`is a variable in our JavaScript program, so it needs to be turned into a string, which can then be spliced into the URL at the right position. Fortunately, modern versions of JavaScript provide a neat way of doing this, namely [template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals). Instead of enclosing the URL string in single quotes as before, we now enclose it in backticks. Then, we can use any JavaScript expression `e`that evaluates to a string by writing `${e}`directly in the URL string. Thus,
    
    我们只会检索 Southville 的人口估计值。
    
    该值`E050109141`大概存储在`id`参数中。但是，`id` 在我们的JavaScript程序中是一个变量，所以需要将其转为字符串，然后拼接到URL中合适的位置。幸运的是，现代版本的 JavaScript 提供了一种简洁的方式来做到这一点，即[模板文字](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)。我们现在不再像以前那样用单引号将 URL 字符串括起来，而是用反引号将其括起来。然后，我们可以通过直接在 URL 字符串中`e`写入来使用任何计算结果为字符串的JavaScript 表达式。`${e}`因此，
    
    ```jsx
    https://opendata.bristol.gov.uk/api/v2/catalog/datasets/population-estimates-time-series-ward/records?limit=20&select=mid_year,population_estimate&refine=ward_2016_code:${id}
    ```
    
    evaluates to the correct string at runtime.
    
    The rest of the function is unremarkable. It creates an `<h1>` heading containing the name of the ward. Then, it calls the local function `buildPopulation`, passing the records in the data returned by the HTTP request. The `<main>` tag is retrieved through its unique ID, its contents are erased, and replaced by the heading and whatever was returned by `buildPopulation`.
    
    A version of this function is run every time someone clicks a ward button.
    
    在运行时评估为正确的字符串。
    
    其余的功能没什么特别的。它创建一个`<h1>`包含病房名称的标题。然后，它调用本地函数 `buildPopulation`，传递 HTTP 请求返回的数据中的记录。通过其唯一 ID 检索标签`<main>`，其内容被删除，并替换为标题和返回的任何内容`buildPopulation`。
    
    每次有人点击 ward 按钮时都会运行此函数的一个版本。
    
    ## **Generating tables**
    
    The rest of the application is contained in the auxiliary `buildPopulation`function:
    
    ```jsx
    function buildPopulation(records) {
    
        // Make heading
        let heading = document.createElement('h2');
        heading.innerText = 'Population';
    
        // Make table
        let table = document.createElement('table');
        table.setAttribute('id','populationTable');
    
        // Make table header
        let header = document.createElement('tr');
        header.innerHTML = '<th>Year</th><th>Population</th></tr>';
        table.appendChild(header);
        
        // Populate table
        records.sort((x1, x2) => x1.record.fields.mid_year < x2.record.fields.mid_year ? -1 : 1)
          .forEach(r => {
            let year = document.createElement('td');
            year.innerText = r.record.fields.mid_year;
            let population = document.createElement('td');
            population.innerText = r.record.fields.population_estimate;
    
            let row = document.createElement('tr');
            row.append(year, population);
            table.appendChild(row);
        });
        
        let population = new DocumentFragment();
        population.append(heading, table);
        
        return population;
      }
    ```
    
    收到一个数组后`records`，此函数开始构建一个 `<table>`包含两列的新数组，年份和人口。建立标题后，它按年份对记录进行排序。这是通过内置 `[sort](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)` 函数实现的，该函数采用高阶参数来决定两个记录中的哪一个先出现。它有一个有趣的界面：负数表示第一个参数出现在第二个之前，而正数则相反。
    
    然后程序遍历记录，并`<tr>`为每个数据点创建一行。最后，它将这些数据组装到一个表中，在前面加上一个`<h2>` 标题，并返回一个`DocumentFragment`由标题和表格组成的。
    
    因此，应用程序的这一部分负责检索和呈现请求的数据。
    
    ### Exercises *(easy)*.
    
     Make the app present only population estimates after the year 2015.
    
    This may be achieved in two ways:
    
    - by changing the REST API call; or
    - by processing the data after it has been fetched.
    
    The second one is significantly easier.
    
    [Hint: Moreover, the second one can be achieved with one line of code if you use Array. filte[r](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter).]
    
    We can use the second method by adding this line:
    
    ```jsx
    function buildPopulation(records) {
      // ...
    
      // Filter records to only include years after 2015
      records = records.filter(r => r.record.fields.mid_year > 2015);
    
      // Populate table
      records.sort((x1, x2) => x1.record.fields.mid_year < x2.record.fields.mid_year ? -1 : 1)
        .forEach(r => {
          // ...
      });
    
      // ...
    }
    ```
    
    ![截屏2023-04-13 20.41.24.png](5%204%20Dynamic%20Structure,%20p2%204bac00f9c612487e9ba52162f03a8ae3/%25E6%2588%25AA%25E5%25B1%258F2023-04-13_20.41.24.png)
    
    If we went to use the first method, we can :
    
    To change the app to present only population estimates after the year 2015 by modifying the REST API call, you can add a filter to the API request URL. You can achieve this by updating the fetch call in the **`displayData`** function.
    
    Here's the modified **`displayData`** function with the necessary change:
    
    ```jsx
    function displayData(id, name) {
      // ...
    
      return function () {
        // Add a filter to the API call to only fetch data after the year 2015
        let wards = fetch(`https://opendata.bristol.gov.uk/api/v2/catalog/datasets/population-estimates-time-series-ward/records?limit=20&select=mid_year,population_estimate&refine=ward_2016_code:${id}&refine.mid_year=2016:`)
          .then(response => response.json())
          .then(data => {
            // ...
          })
          .catch(err => console.log(err));
      }
    }
    ```
    
    By adding **`&refine.mid_year=2016:`** to the API request URL, you are refining the data fetched to include only population estimates after the year 2015. This way, you don't need to filter the data after it has been fetched.
    
    ## *Exercise*.
    
    Expand this application so it also presents an estimate of life expectancy for each ward. I recommend that you define an auxiliary function
    
    ```jsx
    
      function buildLifeExpectancy(records) {
        ...
      }
    ```
    
    which, given the data, builds the necessary HTML elements - as above.
    
    You will also face another problem, which is that you will need to use data from two HTTP requests. The obvious way to do this is to nest two fetch calls:
    
    ```jsx
    
    fetch('first-URL')
      .then(response => response.json())
      .then(data1 =>
        fetch('second-URL')
          .then(response => response.json())
          .then(data2 => {
            // ... here you can use both data1 and data2 ...
          });
      );
    
    ```
    
    However, recent versions of JavaScript provide a neater way of doing this, namely `[Promise.all](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/all)`. This function accepts an array of promises, and returns a single 'composite' promise. When all the premises in the array are resolved, it passes an array of the returned values to its `then()` clause. In this particular instance, you could do something like
    
    ```jsx
    
    Promise.all([fetch('first-URL'), fetch('second-URL')])
      .then([response1, response2] => Promise.all([response1.json(), response2.json()]))
      .then([data1, data2] => {
        // ... here you can use both data1 and data2 ...
      });
    
    ```
    
    or, in a more succinct style:
    
    ```jsx
    
    Promise.all([fetch('first-URL'), fetch('second-URL')])
      .then(responses => Promise.all(responses.map(r => r.json())))
      .then([data1, data2] => {
        // ... here you can use both data1 and data2 ...
      });
    ```
    
    Well, we have finished this task:
    
    ![截屏2023-04-15 17.32.09.png](5%204%20Dynamic%20Structure,%20p2%204bac00f9c612487e9ba52162f03a8ae3/%25E6%2588%25AA%25E5%25B1%258F2023-04-15_17.32.09.png)
    
    My code:
    
    ```jsx
    window.onload = function () {
        let wards = fetch('https://opendata.bristol.gov.uk/api/v2/catalog/datasets/wards/records?limit=50&select=name,ward_id')
            .then(response => response.json())
            .then(populateWards)
            .catch(err => console.log(err));
    }
    
    function populateWards(wards) {
        let buttons = new DocumentFragment();
    
        // Sort the wards alphabetically
        wards.records.sort((w1, w2) => w1.record.fields.name.localeCompare(w2.record.fields.name));
    
        wards.records.forEach(w => {
            const [id, name] = [w.record.fields.ward_id, w.record.fields.name];
            const b = document.createElement("button");
            b.textContent = name;
    
            // Make each button appear on a separate line
            b.style.display = 'block';
    
            // Use addEventListener instead of setting onclick property
            // b.addEventListener('click', displayData(id, name));
            b.addEventListener('click', () => displayData(id, name)());
    
            // b.onclick = displayData(id, name);
            buttons.appendChild(b);
        });
    
        let nav = document.getElementById("nav");
        nav.textContent = '';
        nav.append(buttons);
    }
    
    function displayData(id, name) {
        return function () {
            let timestamp = new Date().getTime();
            Promise.all([
    
                fetch(`https://opendata.bristol.gov.uk/api/v2/catalog/datasets/population-estimates-time-series-ward/records?limit=20&select=mid_year,population_estimate&refine=ward_2016_code:${id}`),
                fetch(`https://opendata.bristol.gov.uk/api/v2/catalog/datasets/life-expectancy-in-bristol/records?limit=100&refine.ward_code=${id}`)
            ])
                .then(responses => Promise.all(responses.map(r => r.json())))
                .then(([populationData, lifeExpectancyData]) => {
                    let heading = document.createElement('h1');
                    heading.textContent = name;
    
                    let population = buildPopulation(populationData.records);
                    let lifeExpectancy = populateLifeExpectancy(lifeExpectancyData, id);
    
                    let dataPane = document.getElementById("dataPane");
                    dataPane.textContent = '';
                    dataPane.append(heading, population, lifeExpectancy);
                })
                .catch(err => console.log(err));
        }
        function createElementText(tag, text) {
            let elem = document.createElement(tag);
            elem.textContent = text;
            return elem;
        }
    
        function createElementWith(tag, xs) {
            let elem = document.createElement(tag);
            for (const x of xs) {
                elem.appendChild(x);
            }
            return elem;
        }
        function buildPopulation(records) {
            let table = document.createElement('table');
            table.id = 'populationTable';
            let headerRow = createElementWith('tr', [
                createElementText('th', 'Year'),
                createElementText('th', 'Population Estimate'),
            ]);
            table.appendChild(headerRow);
    
            for (let r of records
                .filter(d => d.record.fields.mid_year >= 2015)
                .sort((x1, x2) => (x1.record.fields.mid_year < x2.record.fields.mid_year ? -1 : 1))) {
                let row = createElementWith('tr', [
                    createElementText('td', r.record.fields.mid_year),
                    createElementText('td', r.record.fields.population_estimate),
                ]);
                table.appendChild(row);
            }
    
            return table;
        }
    
        function populateLifeExpectancy(lifeExpectancyData, wardCode) {
            // Filter records based on the ward code
            let records = lifeExpectancyData.records.filter(r => r.record.fields.ward_code === wardCode);
    
            // Call the buildLifeExpectancy function with filtered records
            return buildLifeExpectancy(records);
        }
        function buildLifeExpectancy(records) {
            let container = document.createElement('div');
            container.className = 'table-container';
    
            let table = document.createElement('table');
            table.className = 'life-expectancy-table';
    
            let heading = document.createElement('h2');
            heading.textContent = 'Life Expectancy';
            container.appendChild(heading);
    
            if (records.length == 0) {
                let noDataMessage = document.createElement('p');
                noDataMessage.textContent = 'Sorry! No life expectancy data available for this ward';
                container.appendChild(noDataMessage);
                return container;
            }
    
            let headerRow = createElementWith('tr', [
                createElementText('th', 'Period'),
                createElementText('th', 'Ward'),
                createElementText('th', 'Male Life Expectancy'),
                createElementText('th', 'Female Life Expectancy'),
                createElementText('th', 'Average Life Expectancy')
            ]);
            table.appendChild(headerRow);
    
            let filteredRecords = records.filter(r => (
                r.record.fields.hasOwnProperty('male_life_expectancy') &&
                r.record.fields.hasOwnProperty('female_life_expectancy') &&
                r.record.fields.hasOwnProperty('year') &&
                r.record.fields.hasOwnProperty('ward_name')
            ));
    
            for (let r of filteredRecords.sort((x1, x2) => (x1.record.fields.period < x2.record.fields.period ? -1 : 1))) {
                let maleLifeExpectancy = r.record.fields.male_life_expectancy.toFixed(0);
                let femaleLifeExpectancy = r.record.fields.female_life_expectancy.toFixed(0);
                let avgLifeExpectancy = ((r.record.fields.male_life_expectancy + r.record.fields.female_life_expectancy) / 2).toFixed(0);
                let row = createElementWith('tr', [
                    createElementText('td', r.record.fields.year),
                    createElementText('td', r.record.fields.ward_name),
                    createElementText('td', maleLifeExpectancy),
                    createElementText('td', femaleLifeExpectancy),
                    createElementText('td', avgLifeExpectancy)
                ]);
                table.appendChild(row);
            }
    
            container.appendChild(table);
            return container;
        }
    
    }
    ```
    
    Question List: 
    
    I think I encontered peoblem here, I couldn’t load my page correctly, and I dont know how to solve it, I am not sure if I am getting the correct form of API key on this page:
    
    [https://opendata.bristol.gov.uk/explore/dataset/life-expectancy-in-bristol/api/?disjunctive.ward_name](https://opendata.bristol.gov.uk/explore/dataset/life-expectancy-in-bristol/api/?disjunctive.ward_name)
    
    api key i used is:
    
    ```jsx
    fetch(`https://opendata.bristol.gov.uk/api/records/1.0/search/?dataset=life-expectancy-in-bristol&q=ward_2016_code:'${id}'&sort=period&rows=20`)
    ```