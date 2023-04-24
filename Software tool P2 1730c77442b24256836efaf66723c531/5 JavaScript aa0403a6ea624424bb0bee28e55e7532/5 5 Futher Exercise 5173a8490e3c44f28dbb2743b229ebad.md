# 5.5 Futher Exercise

## Simplify your code:

If you have changed the app so that it displays life expectancy as well, you will notice that you have amassed a formidable amount of code. For example, my solution runs to 116 lines - all to achieve something that is essentially simple.

For example, to create the population data table we wrote the following code:

```jsx
let year = document.createElement('td');
year.textContent = r.record.fields.mid_year;

let population = document.createElement('td');
population.textContent = r.record.fields.population_estimate;

let row = document.createElement('tr');
row.append(year, population);
table.appendChild(row);

```

Staring at this code, certain patterns become evident: every time we want to create a new HTML tag, we must:

1. create the HTML element,
2. set its `textContent` (or `innerHTML` elsewhere), and
3. assemble things hierarchically (in rows, tables, etc.)

This pattern occupies the majority of our code. It is an artifact of the way the DOM API is designed. For example, it would be preferable if we had a constructor `document.createElementWithText(tag, text)` which allowed to construct a new element of the DOM, and immediately initialize it with some text.

Luckily, JavaScript is a particularly expressive language, and such an interface can be defined:

```jsx

function createElementText(tag, text) {
  let elem = document.createElement(tag);
  elem.textContent = text;
  return elem;
}
```

This small function performs steps 1 and 2, and then returns the new element.

To deal with 3, i.e. the hierarchical assembly of elements, we can define a function

```jsx

function createElementWith(tag, xs) {
  let elem = document.createElement(tag);
  for (const x of xs) {
    elem.appendChild(x);
  }
  return elem;
}
```

This function takes the name of a tag, and an array `xs` of elements. It then creates a new element with this tag, and appends everything in `xs` as children of this new element. Finally, it returns the newly constructed element.

These functions allow us to create new elements of the DOM in a more functional style. For example, an array containing the rows of the population table can be created using the following code fragment:

```jsx

  records.filter(d => d.record.fields.mid_year >= 2015)
    .sort((x1, x2) => x1.record.fields.mid_year < x2.record.fields.mid_year ? -1 : 1)
    .map(r =>
      createElementWith('tr', [
        createElementText('td', r.record.fields.mid_year),
        createElementText('td', r.record.fields.population_estimate)
      ])
```

The expressions in the body correspond to the actual tree structure of the row. As a result, they are much more readable.

### *Exercise*.

Rewrite the application using the functions defined above (and similar ones). Try to make it as succinct and readable as possible.

For example, my version of the complete application (with life expectancy) runs to 114 lines, and that is without making much of an effort to be succint. This is only 2 lines shorter than my previous version, but one must remember that about 20 of these lines are the new functions, and we could factor these out in a separate JavaScript [module](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules). This amounts to a 19% reduction in the amount of code - which can be rather significant in larger projects.

Of course, larger projects are likely to use frameworks like React to build such applications, whose use of JSX and [function components](https://www.robinwieruch.de/react-function-component/) deal with exactly this sort of problem.

Old version of buildpopulation:

```jsx
function buildPopulation(records) {

        // Make heading
        let heading = document.createElement('h2');
        heading.textContent = 'Population';

        // Make table
        let table = document.createElement('table');
        table.setAttribute('id', 'populationTable');

        // Make table header
        let header = document.createElement('tr');
        header.innerHTML = '<th>Year</th><th>Population</th></tr>';
        table.appendChild(header);

        // Filter records to only include years after 2015 (Exercise 1)
        records = records.filter(r => r.record.fields.mid_year >= 2015);

        // Populate table
        records.sort((x1, x2) => x1.record.fields.mid_year < x2.record.fields.mid_year ? -1 : 1)
            .forEach(r => {
                let year = document.createElement('td');
                year.textContent = r.record.fields.mid_year;
                let population = document.createElement('td');
                population.textContent = r.record.fields.population_estimate;

                let row = document.createElement('tr');
                row.append(year, population);
                table.appendChild(row);
            });

        let population = new DocumentFragment();
        population.append(heading, table);

        return population;
    }
```

New version of build population:

```jsx
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
```

Old version of build life expentancy:

```jsx
function buildLifeExpectancy1(records) {
        // Make container for table
        let container = document.createElement('div');
        container.className = 'table-container';

        let table = document.createElement("table");
        table.className = 'life-expectancy-table';

        // Make heading
        let heading = document.createElement('h2');
        heading.textContent = 'Life Expectancy';

        if (records.length == 0) {
            let noDataMessage = document.createElement('p');
            noDataMessage.textContent = 'Sorry! No life expectancy data available for this ward';
            return noDataMessage;
        }

        // Make table header
        let header = document.createElement('tr');
        header.innerHTML = '<th>Period</th><th>Ward</th><th>Male Life Expectancy</th><th>Female Life Expectancy</th><th>Average Life Expectancy</th>';
        table.appendChild(header);

        // Populate table
        records.forEach(r => {
            // Check if all required fields are present
            if (!r.record.fields.hasOwnProperty('male_life_expectancy') ||
                !r.record.fields.hasOwnProperty('female_life_expectancy') ||
                !r.record.fields.hasOwnProperty('year') ||
                !r.record.fields.hasOwnProperty('ward_name')) {
                return;
            }

            let period = document.createElement('td');
            period.textContent = r.record.fields.year;

            let ward = document.createElement('td');
            ward.textContent = r.record.fields.ward_name;

            let maleLifeExpectancy = document.createElement('td');
            maleLifeExpectancy.textContent = r.record.fields.male_life_expectancy.toFixed(0);

            let femaleLifeExpectancy = document.createElement('td');
            femaleLifeExpectancy.textContent = r.record.fields.female_life_expectancy.toFixed(0);

            let averageLifeExpectancy = document.createElement('td');
            let avgLifeExpectancy = ((r.record.fields.male_life_expectancy + r.record.fields.female_life_expectancy) / 2).toFixed(0);
            averageLifeExpectancy.textContent = avgLifeExpectancy;

            let row = document.createElement('tr');
            row.append(period, ward, maleLifeExpectancy, femaleLifeExpectancy, averageLifeExpectancy);
            table.appendChild(row);
        });

        let lifeExpectancyFragment = new DocumentFragment();
        lifeExpectancyFragment.append(heading, table);

        return lifeExpectancyFragment;
    }
```

new version of build life-expentancy:

```jsx
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
```