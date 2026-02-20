# _q000 - **SurrealQL**_

(merge at 2025-02-19)

![SurrealQL][icon_SurrealQL]

SurrealQL is a powerful and intuitive database query language that closely resembles traditional SQL but comes with unique differences and improvements.

SurrealQL is designed to provide developers with a seamless and intuitive way to interact with SurrealDB. It offers a familiar syntax and supports various statement types, allowing you to perform complex database operations efficiently.

While SurrealQL shares similarities with traditional SQL, it introduces enhancements and optimizations that make it well-suited for working with SurrealDB's advanced features and data models. Whether you are querying data, modifying records, or managing database structures, SurrealQL provides a comprehensive set of capabilities to meet your needs.

## _q000a - **Key Features**_

SurrealQL offers several key features that make it a powerful tool for working with SurrealDB:

- **Familiar Syntax**: SurrealQL adopts a syntax similar to traditional SQL, making it easy for developers familiar with SQL to transition to SurrealDB seamlessly.

- **Advanced Querying**: SurrealQL supports a wide range of querying capabilities, including filtering, sorting, aggregating, and joining data from multiple tables.

- **Data Manipulation**: With SurrealQL, you can easily insert, update, and delete records in your SurrealDB database, allowing you to manage your data effectively.

- **Graph relationships**: SurrealQL supports graph relationships, allowing you to define and query relationships between records in your database.

- **Schema Management**: SurrealQL provides features for creating and modifying database schemas, allowing you to define the structure of your data and enforce data integrity.

- **Performance Optimization**: SurrealQL incorporates optimizations specific to SurrealDB, ensuring efficient execution of queries and minimizing resource usage.

## _q000b - **Getting Started**_

To start using [SurrealQL][SurrealQL038], refer to the documentation on the various statement types and their syntax. The statements page provides comprehensive examples and explanations for each statement type, helping you understand how to construct queries and interact with SurrealDB effectively.

SurrealQL empowers you to leverage the full potential of SurrealDB and enables you to build robust and scalable applications. Let's dive into the world of SurrealQL and unlock the capabilities of SurrealDB together!

[![**go to YouTube**][icon_YT]][yt01]

---
---

## _q001 - **Demo data**_

To quickly test out SurrealDB and SurrealQL functionality, we've included two demo datasets here in `.surql` files which you can download and [`import`][SurrealDB_cli_import] into SurrealDB using the [CLI][SurrealDB_cli].

### _q001a - **Surreal Deal Store - there is a lot in store for you!**_

Surreal Deal Store is our new and improved demo dataset based on our [SurrealDB Store][net__SurrealDB_Store].
The dataset is made up of 12 tables using both [graph relations][SurrealQL076] and [record links][SurrealQL021].

In the diagram below, the nodes in pink are the [standard tables][SurrealQL063], the ones in purple represent the [edge tables][SurrealQL076] which shows relationships between records and SurrealDB as a graph database. The nodes in grey are the [pre-computed table views][SurrealQL063].

![Surreal Deal Data Mode][img_demo_overview]

#### _q001a1 - **Download**_

| Dataset | URL |
| --- | --- |
| [Surreal Deal Store][getSURQL_001] | [https://datasets.surrealdb.com/surreal-deal-store.surql][getSURQL_001] |
| [Surreal Deal Store (mini)][getSURQL_002] | [https://datasets.surrealdb.com/surreal-deal-store-mini.surql][getSURQL_002] |

#### _q001a2 - **Import**_

Once one of the datasets has been downloaded, it's now time to [start the server][SurrealDB_cli_start].

```bash
# Create a new in-memory server
surreal start --user root --pass secret --allow-all
```

Lastly, use the [import command][SurrealDB_cli_import] to add the dataset.

Use the command below to import the [surreal deal store dataset][getSURQL_001]:

```bash
surreal import --conn http://localhost:8000 --user root --pass secret --ns main --db main surreal-deal-store.surql
```

To import the surreal downloaded the [Surreal Deal store (mini)][getSURQL_002] use the command below:

```bash
surreal import --conn http://localhost:8000 --user root --pass secret --ns main --db main surreal-deal-store-mini.surql
```

Please be aware that the import process might take a few seconds.

#### _q001a3 - **Using Curl**_

First, start the SurrealDB server:

```bash
# Create a new in-memory server
surreal start --user root --pass secret --allow-all
```

Then download the file and load it into the database:

```bash
# Download the file
curl -L "https://datasets.surrealdb.com/surreal-deal-store.surql" -o surreal-deal-store.surql

# Load the file into the database using the rest endpoint
curl -v -X POST -u "root:secret" -H "Surreal-NS: main" -H "Surreal-DB: main" -H "Accept: application/json" --data-binary @surreal-deal-store.surql http://localhost:8000/import
```

If you want to use the mini version:

```bash
# Download the file
curl -L "https://datasets.surrealdb.com/surreal-deal-store-mini.surql" -o surreal-deal-store-mini.surql

# Load the file into the database using the rest endpoint
curl -v -X POST -u "root:secret" -H "Surreal-NS: main" -H "Surreal-DB: main" -H "Accept: application/json" --data-binary @surreal-deal-store-mini.surql http://localhost:8000/import
```

#### _q001a4 - **Sample queries**_

Here are some sample queries you can run on the Surreal Deal Store dataset. We've also included a [App Surrealist Mini][net__SurrealistMini] below to help you run these queries.

> [!NOTE]
> The query results below have been limited to 4 rows for brevity. If you remove the `LIMIT 4` clause from the queries, you'll see the full results.

[Try in App Surrealist Mini][trySURQL_001]

---
---

## _q002 - **Operators**_

A variety of operators in SurrealQL allow for complex manipulation of data, and advanced logic.

| Operator | Description |
| :--- | :--- |
| [`&&`][SurrealQL002_and] [`AND`][SurrealQL002_and] | Checks whether both of two values are truthy |
| [`\|\|`][SurrealQL002_or] [`OR`][SurrealQL002_or] | Checks whether either of two values is truthy |
| [`!`][SurrealQL002_not] | Reverses the truthiness of a value |
| [`!!`][SurrealQL002_notnot] | Determines the truthiness of a value |
| [`??`][SurrealQL002_null] | Check whether either of two values are truthy and not NULL |
| [`?:`][SurrealQL002_truthy] | Check whether either of two values are truthy |
| [`=`][SurrealQL002_equal] [`IS`][SurrealQL002_equal] | Check whether two values are equal |
| [`!=`][SurrealQL002_notequal] [`IS NOT`][SurrealQL002_notequal] | Check whether two values are not equal |
| [`==`][SurrealQL002_exact] | Check whether two values are exactly equal |
| [`?=`][SurrealQL002_anyequal] | Check whether any value in a set is equal to a value |
| [`*=`][SurrealQL002_allequal] | Check whether all values in a set are equal to a value |
| [`~`][SurrealQL002_similar] | Compare two values for equality using fuzzy matching |
| [`!~`][SurrealQL002_similar] | Compare two values for inequality using fuzzy matching |
| [`?~`][SurrealQL002_similar] | Check whether any value in a set is equal to a value using fuzzy matching |
| [`*~`][SurrealQL002_similar] | Check whether all values in a set are equal to a value using fuzzy matching |
| [`<`][SurrealQL002_less] | Check whether a value is less than another value |
| [`<=`][SurrealQL002_lessequal] | Check whether a value is less than or equal to another value |
| [`>`][SurrealQL002_more] | Check whether a value is greater than another value |
| [`>=`][SurrealQL002_moreequal] | Check whether a value is greater than or equal to another value |
| [`+`][SurrealQL002_add] | Add two values together |
| [`-`][SurrealQL002_sub] | Subtract a value from another value |
| [`*`][SurrealQL002_mul] [`×`][SurrealQL002_mul] | Multiply two values together |
| [`/`][SurrealQL002_div] [`÷`][SurrealQL002_div] | Divide a value by another value |
| [`**`][SurrealQL002_pow] | Raises a base value by another value |
| [`CONTAINS`][SurrealQL002_co_equ] [`∋`][SurrealQL002_co_equ] | Checks whether a value contains another value |
| [`CONTAINSNOT`][SurrealQL002_co_not] [`∌`][SurrealQL002_co_not] | Checks whether a value does not contain another value |
| [`CONTAINSALL`][SurrealQL002_co_all] [`⊇`][SurrealQL002_co_all] | Checks whether a value contains all other values |
| [`CONTAINSANY`][SurrealQL002_co_any] [`⊃`][SurrealQL002_co_any] | Checks whether a value contains any other value |
| [`CONTAINSNONE`][SurrealQL002_co_non] [`⊅`][SurrealQL002_co_non] | Checks whether a value contains none of the following values |
| [`INSIDE`][SurrealQL002_in_equ] [`IN`][SurrealQL002_in_equ] [`∈`][SurrealQL002_in_equ] | Checks whether a value is contained within another value |
| [`NOTINSIDE`][SurrealQL002_in_not] [`NOT IN`][SurrealQL002_in_not] [`∉`][SurrealQL002_in_not] | Checks whether a value is not contained within another value |
| [`ALLINSIDE`][SurrealQL002_in_all] [`⊆`][SurrealQL002_in_all] | Checks whether all values are contained within other values |
| [`ANYINSIDE`][SurrealQL002_in_any] [`⊂`][SurrealQL002_in_any] | Checks whether any value is contained within other values |
| [`NONEINSIDE`][SurrealQL002_in_non] [`⊄`][SurrealQL002_in_non] | Checks whether no value is contained within other values |
| [`OUTSIDE`][SurrealQL002_outside] | Checks whether a geometry type is outside of another geometry type |
| [`INTERSECTS`][SurrealQL002_inter] | Checks whether a geometry type intersects another geometry type |
| [`@@`][SurrealQL002_matches] [`@[ref]@`][SurrealQL002_matches] | Checks whether the terms are found in a full-text indexed field |
| [`<\|4\|>`][SurrealQL002_knn] [`<\|3,HAMMING\| >`][SurrealQL002_knn] | Performs a K-Nearest Neighbors (KNN) search to find a specified number of records closest to a given data point, optionally using a defined distance metric. Supports customizing the number of results and choice of distance calculation method. |

### _q002aa - **`&&` or `AND`**_

The `and` operator checks whether both of two values are [truthy][SurrealQL027].

```surql
/**[test]

[[test.results]]
value = "30"

*/

SELECT * FROM 10 AND 20 AND 30;

-- 30
```

### _q002ab - **`||` or `OR`**_

The `or` operator checks whether either of two values are [truthy][SurrealQL027].

```surql
/**[test]

[[test.results]]
value = "[10]"

*/

SELECT * FROM 0 OR false OR 10;

-- 10
```

### _q002ac - **`!` (not)**_

The `not` operator reverses the truthiness of a value.

```surql
/**[test]

[[test.results]]
value = "[false]"

[[test.results]]
value = "[false]"

*/

SELECT * FROM !(TRUE OR FALSE);
-- false

SELECT * FROM !"Has a value";
-- false
```

### _q002ad - **`!!` (not not)**_

The `not not` operator is simply an application of the `!` operator twice. It can be used to determines the truthiness of a value.

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM !!"Has a value";
-- true
```

### _q002ae - **`??` (null coalescing)**_

The `null coalescing operator` checks whether either of two values are [truthy][SurrealQL027] and not `NONE` or `NULL`.

```surql
/**[test]

[[test.results]]
value = "[0]"

*/

SELECT * FROM NULL ?? 0 ?? false ?? 10;

-- 0
```

### _q002af - **`?:` (truthy coalescing)**_

The `truthy coalescing operator` checks whether either of two values are [truthy][SurrealQL027].

```surql
/**[test]

[[test.results]]
value = "[10]"

*/

SELECT * FROM NULL ?: 0 ?: false ?: 10;

-- 10
```

### _q002ag - **`=` or `IS`**_

The `equal` operator checks whether two values are equal.

```surql
/**[test]

[[test.results]]
value = "[false]"

*/

SELECT * FROM true = "true";
-- false
```

```surql
/**[test]

[[test.results]]
value = "[false]"

*/

SELECT * FROM 10 = "10";
-- false
```

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM 10 = 10.00;
-- true
```

```surql
/**[test]

[[test.results]]
value = "[false]"

*/

SELECT * FROM 10 = "10.3";
-- false
```

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM [1, 2, 3] = [1, 2, 3];
-- true
```

```surql
/**[test]

[[test.results]]
value = "[false]"

*/

SELECT * FROM [1, 2, 3] = [1, 2, 3, 4];
-- false
```

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM { this: "object" } = { this: "object" };
-- true
```

```surql
/**[test]

[[test.results]]
value = "[false]"

*/

SELECT * FROM { this: "object" } = { another: "object" };
-- false
```

### _q002ah - **`!=` or `IS NOT`**_

The `not equal` operator checks whether two values are not equal.

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM 10 != "15";
-- true
```

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM 10 != "test";
-- true
```

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM [1, 2, 3] != [3, 4, 5];
-- true
```

### _q002ai - **`==` (exact)**_

The `exact` operator checks whether two values are exact. This operator also checks that each value has the same type.

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM 10 == 10;
-- true
```

```surql
/**[test]

[[test.results]]
value = "[false]"

*/

SELECT * FROM 10 == "10";
-- false
```

```surql
/**[test]

[[test.results]]
value = "[false]"

*/

SELECT * FROM true == "true";
-- false
```

### _q002aj - **`?=` (any equal)**_

The `any equal` operator checks whether any value in an array equals another value.

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM [10, 15, 20] ?= 10;
-- true
```

### _q002ak - **`*=` (all equal)**_

The `all equal` operator checks whether all values in an array equals another value.

```surql
/**[test]

[[test.results]]
value = ""

*/

SELECT * FROM [10, 10, 10] *= 10;
-- true
```

### _q002al - **`~` `?~` `!~` `*~` (similarity)**_

These operators used to compare two values for equality using fuzzy matching. They have been removed since 3.0 to avoid implicitly preferring one algorithm over another, as the type of fuzzy matching to use will depend on each individual case.

Please use the `string::similarity::*` functions instead:

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "true"

*/

let $threshold = 10;

string::similarity::smithwaterman("test text", "Test") > $threshold;
-- true
```

### _q002am - **`<` (less)**_

The `less than` operator checks whether a value is less than another value.

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM 10 < 15;
-- true
```

### _q002an - **`<=` (less or equal)**_

The `less than or equal` operator checks whether a value is less than or equal to another value.

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM 10 <= 15;
-- true
```

### _q002ao - **`>` (more)**_

The `greater than` operator checks whether a value is less than another value.

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM 15 > 10;
-- true
```

### _q002ap - **`>=` (more or equal)**_

The `greater than or equal` operator checks whether a value is less than or equal to another value.

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM 15 >= 10;
-- true
```

### _q002aq - **`+` (add)**_

The `add` operator adds two values together.

```surql
/**[test]

[[test.results]]
value = "[20]"

*/

SELECT * FROM 10 + 10;
-- 20
```

```surql
/**[test]

[[test.results]]
value = "['test this']"

*/

SELECT * FROM "test" + " " + "this";
-- "test this"
```

```surql
/**[test]

[[test.results]]
value = "[13h30m]"

*/

SELECT * FROM 13h + 30m;
-- "13h30m"
```

### _q002ar - **`-` (sub)**_

The `subtract` operator subtracts a value from another value.

```surql
/**[test]

[[test.results]]
value = "[10]"

*/

SELECT * FROM 20 - 10;
-- 10
```

```surql
/**[test]

[[test.results]]
value = "[1m]""

*/

SELECT * FROM 2m - 1m;
-- 1m
```

### _q002as - **`*` or `×` (mul)**_

The `multiply` operator multiplies a value by another value.

```surql
/**[test]

[[test.results]]
value = "[40]"

*/

SELECT * FROM 20 * 2;
-- 40
```

### _q002at - **`/` or `÷` (div)**_

The `divide` operator divides a value by another value.

```surql
/**[test]

[[test.results]]
value = "[10]"

*/

SELECT * FROM 20 / 2;
-- 10
```

### _q002au - **`**` (pow)**_

The `power` operator raises a base value by another value.

```surql
/**[test]

[[test.results]]
value = "[8000]"

*/

SELECT * FROM 20 ** 3;
-- 8000
```

### _q002av - **`CONTAINS` or `∋`**_

The `contains` operator checks whether a value contains another value.

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM [10, 20, 30] CONTAINS 10;
-- true
```

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM "this is some text" CONTAINS "text";
-- true
```

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM {
  type: "Polygon",
  coordinates: [[
    [-0.38314819, 51.37692386], [0.1785278, 51.37692386],
    [0.1785278, 51.61460570], [-0.38314819, 51.61460570],
    [-0.38314819, 51.37692386]
  ]]
} CONTAINS (-0.118092, 51.509865);

-- true
```

### _q002aw - **`CONTAINSNOT` or `∌`**_

The `not contains` operator checks whether a value does not contain another value.

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM [10, 20, 30] CONTAINSNOT 15;
-- true
```

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM "this is some text" CONTAINSNOT "other";
-- true
```

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM {
  type: "Polygon",
  coordinates: [[
    [-0.38314819, 51.37692386], [0.1785278, 51.37692386],
    [0.1785278, 51.61460570], [-0.38314819, 51.61460570],
    [-0.38314819, 51.37692386]
  ]]
} CONTAINSNOT (-0.518092, 53.509865);

-- true
```

### _q002ax - **`CONTAINSALL` or `⊇`**_

The `contains all` operator checks whether a value contains all of multiple values.

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM [10, 20, 30] CONTAINSALL [10, 20, 10];
-- true
```

### _q002ay - **`CONTAINSANY` or `⊃`**_

The `contains any` operator checks whether a value contains any of multiple values.

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM [10, 20, 30] CONTAINSANY [10, 15, 25];
-- true
```

### _q002az - **`CONTAINSNONE` or `⊅`**_

⚠️⚠️⚠️

### _q002ba - **`INSIDE` or `∈` or `IN`**_

The `inside` operator checks whether a value is contained within another value.

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM 10 INSIDE [10, 20, 30];
-- true
```

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM "text" INSIDE "this is some text";
-- true
```

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM (-0.118092, 51.509865) INSIDE {
  type: "Polygon",
  coordinates: [[
    [-0.38314819, 51.37692386], [0.1785278, 51.37692386],
    [0.1785278, 51.61460570], [-0.38314819, 51.61460570],
    [-0.38314819, 51.37692386]
  ]]
};

true
```

> Available since: V2.1.0

This operator can also be used to check for the existence of a key inside an [object][SurrealQL018]. To do so, precede `IN` with the field name as a string.

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

"name" IN {
    name: "Riga",
    country: "Latvia"
};

-- true
```

`IN` can also be used with a record ID as long as the ID is expanded to include the fields. Both of the following queries will return `true`.

```surql
/**[test]

[[test.results]]
value = "[{ country: 'Latvia', id: city:riga, name: 'Riga', population: 605273 }]"

[[test.results]]
value = "true"

[[test.results]]
value = "true"

*/

CREATE city:riga SET name = "Riga", country = "Latvia", population = 605273;

"name" IN city:riga.*;
"name" IN city:riga.{ name, country };
```

### _q002bb - **`NOTINSIDE` or `∉` or `NOT IN`**_

The `not inside` operator checks whether a value is not contained within another value.

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM 15 NOTINSIDE [10, 20, 30];
-- true
```

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM "other" NOTINSIDE "this is some text";
-- true
```

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM (-0.518092, 53.509865) NOTINSIDE {
  type: "Polygon",
  coordinates: [[
    [-0.38314819, 51.37692386], [0.1785278, 51.37692386],
    [0.1785278, 51.61460570], [-0.38314819, 51.61460570],
    [-0.38314819, 51.37692386]
  ]]
};

-- true
```

### _q002bc - **`ALLINSIDE` or `⊆`**_

The `all inside` operator checks whether all of multiple values are contained within another value.

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM [10, 20, 10] ALLINSIDE [10, 20, 30];
-- true
```

### _q002bd - **`ANYINSIDE` or `⊂`**_

The `any inside` operator checks whether any of multiple values are contained within another value.

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM [10, 15, 25] ANYINSIDE [10, 20, 30];
-- true
```

### _q002be - **`NONEINSIDE` or `⊄`**_

The `none inside` operator checks whether none of multiple values are contained within another value.

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM [15, 25, 35] NONEINSIDE [10, 20, 30];
-- true
```

### _q002bf - **`OUTSIDE`**_

The `outside` operator checks whether a geometry value is outside another geometry value.

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM (-0.518092, 53.509865) OUTSIDE {
  type: "Polygon",
  coordinates: [[
    [-0.38314819, 51.37692386], [0.1785278, 51.37692386],
    [0.1785278, 51.61460570], [-0.38314819, 51.61460570],
    [-0.38314819, 51.37692386]
  ]]
};

-- true
```

### _q002bg - **`INTERSECTS`**_

The `intersects` operator checks whether a geometry value intersects another geometry value.

```surql
/**[test]

[[test.results]]
value = "[true]"

*/

SELECT * FROM {
  type: "Polygon",
  coordinates: [[
    [-0.38314819, 51.37692386], [0.1785278, 51.37692386],
    [0.1785278, 51.61460570], [-0.38314819, 51.61460570],
    [-0.38314819, 51.37692386]
  ]]
} INTERSECTS {
  type: "Polygon",
  coordinates: [[
    [-0.11123657, 51.53160074], [-0.16925811, 51.51921169],
    [-0.11466979, 51.48223813], [-0.07381439, 51.51322956],
    [-0.11123657, 51.53160074]
  ]]
};

-- true
```

### _q002bh - **`MATCHES`**_

The `matches` operator checks whether the terms are found in a full-text indexed field.

```surql
SELECT * FROM book WHERE title @@ 'rust web';

[
  {
    id: book:1,
    title: 'Rust Web Programming'
  }
]
```

Using the matches operator with a reference checks whether the terms are found, highlights the searched terms, and computes the full-text score.

```surql
SELECT id,
    search::highlight('<b>', '</b>', 1) AS title,
    search::score(1) AS score
FROM book
WHERE title @1@ 'rust web'
ORDER BY score DESC;

[
  {
    id: book:1,
    score: 0.9227996468544006f,
    title: '<b>Rust</b> <b>Web</b> Programming'
  }
]
```

> Available since: V3.0.0

#### _q002bh1 - **`AND`, `OR`, and numeric operators inside `@@`**_

In addition to the `AND` keyword, the `OR` matches operator can also be used as of 3.0.0-beta. This allows a single string to be compared against instead of needing to specify individual parts of the string.

```surql
/**[test]

[[test.results]]
value = "[{ id: document:1, text: 'It is rare that I find myself penning a personal note in my chronicles.' }]"

[[test.results]]
value = "NONE"

[[test.results]]
value = "NONE"

[[test.results]]
value = "[{ id: document:1, text: 'It is rare that I find myself penning a personal note in my chronicles.' }]"

[[test.results]]
value = "[{ id: document:1, text: 'It is rare that I find myself penning a personal note in my chronicles.' }]"

[[test.results]]
value = "[{ id: document:1, text: 'It is rare that I find myself penning a personal note in my chronicles.' }]"

[[test.results]]
value = "[{ id: document:1, text: 'It is rare that I find myself penning a personal note in my chronicles.' }]"

[[test.results]]
value = "[{ id: document:1, text: 'It is rare that I find myself penning a personal note in my chronicles.' }]"

*/

CREATE document:1 SET text = "It is rare that I find myself penning a personal note in my chronicles.";
DEFINE ANALYZER simple TOKENIZERS blank,class FILTERS lowercase;
DEFINE INDEX some_index ON document FIELDS text FULLTEXT ANALYZER simple;

-- @AND@ and @OR@: can use the entire string
SELECT * FROM document WHERE text @AND@ "personal rare";
SELECT * FROM document WHERE text @OR@ "personal nice weather today";

-- Separate AND and OR outside of matches operator:
-- Must specify parts of string to check for match
SELECT * FROM document WHERE text @@ "personal" AND text @@ "rare";
SELECT * FROM document WHERE text @@ "personal note";
SELECT * FROM document WHERE text @@ "personal" OR text @@ "nice weather today";
```

### _q002bi - **`KNN`**_

K-Nearest Neighbors (KNN) is a fundamental algorithm used for classifying or regressing based on the closest data points in the feature space, with its performance and scalability critical in applications involving large datasets.

In practice, the efficiency and scalability of the KNN algorithm are crucial, especially when dealing with large datasets. Different implementations of KNN are tailored to optimize these aspects without compromising the accuracy of the results.

SurrealDB supports different K-Nearest Neighbors methods to perform KNN searches, each with unique requirements for syntax.
Below are the details for each method, including how to format your query with examples:

#### _q002bi1 - **Brute Force Method**_

Best for smaller datasets or when the highest accuracy is required.

```syntax title="SurrealQL Syntax"
<|K,DISTANCE_METRIC|>
```

- K: The number of nearest neighbors to retrieve.
- DISTANCE_METRIC: The metric used to calculate distances, such as EUCLIDEAN or MANHATTAN.

```surql
/**[test]

[[test.results]]
value = "[{ id: pts:3, point: [8, 9, 10, 11] }]"

[[test.results]]
value = "[{ id: pts:3 }]"

*/

CREATE pts:3 SET point = [8,9,10,11];
SELECT id FROM pts WHERE point <|2,EUCLIDEAN|> [2,3,4,5];
```

#### _q002bi2 - **HNSW Method**_

Recommended for very large datasets where speed is essential and some loss of accuracy is acceptable.

```syntax title="SurrealQL Syntax"
<|K,EF|>
```

- K: The number of nearest neighbors.
- EF: The size of the dynamic candidate list during the search, affecting the search's accuracy and speed.

```surql
/**[test]

[[test.results]]
value = "[{ id: pts:3, point: [8, 9, 10, 11] }]"

[[test.results]]
value = "NONE"

[[test.results]]
value = "[{ id: pts:3 }]"

*/

CREATE pts:3 SET point = [8,9,10,11];
DEFINE INDEX mt_pts ON pts FIELDS point HNSW DIMENSION 4 DIST EUCLIDEAN EFC 150 M 12;
SELECT id FROM pts WHERE point <|10,40|> [2,3,4,5];
```

### _q002bj - **Using the `ANY`/`ALL` operators for string indexes**_

> Available since: Vv2.4.0

An index defined on a string value can be used via the operators `CONTAINSANY`, `ALLINSIDE`, or `ANYINSIDE`. The operator `CONTAINS`, however, will not use a defined index as `CONTAINS` is used for substring matches between strings themselves as opposed to an index lookup.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "NONE"

[[test.results]]
value = "[{ id: account:billy, name: 'Billy McConnell' }]"

[[test.results]]
value = "[{ id: account:billy, name: 'Billy McConnell' }]"

[[test.results]]
value = "[{ id: account:billy, name: 'Billy McConnell' }]"

[[test.results]]
value = "[{ id: account:billy, name: 'Billy McConnell' }], [{ detail: { direction: 'forward', table: 'account' }, operation: 'Iterate Table' }, { detail: { type: 'Memory' }, operation: 'Collector' }, { detail: { type: 'KeysAndValues' }, operation: 'RecordStrategy' }, { detail: { count: 1 }, operation: 'Fetch' }]"

[[test.results]]
value = "[{ detail: { plan: { index: 'name_index', operator: 'union', value: ['Billy McConnell'] }, table: 'account' }, operation: 'Iterate Index' }, { detail: { type: 'Memory' }, operation: 'Collector' }, { detail: { type: 'KeysAndValues' }, operation: 'RecordStrategy' }, { detail: { count: 1 }, operation: 'Fetch' }]"

*/

DEFINE FIELD name ON account TYPE string;
DEFINE INDEX name_index ON account FIELDS name;

CREATE account:billy SET name = "Billy McConnell";

-- Both return the user Billy McConnell
SELECT * FROM account WHERE name CONTAINS "Billy McConnell";
SELECT * FROM account WHERE name CONTAINSANY ["Billy McConnell"];

-- However, CONTAINS does not use the index
SELECT * FROM account WHERE name CONTAINS "Billy McConnell" EXPLAIN FULL;
-- CONTAINSANY + putting the value inside an array will use the index
SELECT * FROM account WHERE name CONTAINSANY ["Billy McConnell"] EXPLAIN FULL;
```

### _q002bk - **Types of operators, order of operations and binding power**_

To determine which operator is executed first, a concept called "binding power" is used. Operators with greater binding power will operate directly on their neighbours before those with lower binding power. The following is a list of all operator types from greatest to lowest binding power.

| Operator name | Description |
| :--- | :--- |
| `Unary` | The `Unary` operators are `!`, `+`, and `-`. |
| `Nullish` | The `Nullish` operators are `?:` and `??`. |
| `Range` | The `Range` operator is `..`. |
| `Cast` | The `Cast` operator is ``, with `type_name` a stand in for the type to cast into. For example, `` or ``. |
| `Power` | The only `Power` operator is `**`. |
| `MulDiv` | The `MulDiv` (multiplication and division) operators are `*`, `/`, `÷`, and `%`. |
| `AddSub` | The `AddSub` (addition and subtraction) operators are `+` and `-`. |
| `Relation` | The `Relation` operators are `<=`, `>=`, `∋`, `CONTAINS`, `∌`, `CONTAINSNOT`, `∈`, `INSIDE`, `∉`, `NOTINSIDE`, `⊇`, `CONTAINSALL`, `⊃`, `CONTAINSANY`, `⊅`, `CONTAINSNONE`, `⊆`, `ALLINSIDE`, `⊂`, `ANYINSIDE`, `⊄`, `NONEINSIDE`, `OUTSIDE`, `INTERSECTS`, `NOT`, and `IN`. |
| `Equality` | The `Equality` operators are `=`, `IS`, `==`, `!=`, `*=`, `?=`, and `@`. |
| `And` | The `And` operators are `&&` and `AND`. |
| `Or` | The `Or` operators are `\|\|` and `OR`. |

### _q002bl - **Examples of binding power**_

The following samples show examples of basic operations of varying binding power. The original example is followed by the same example with the parts with higher binding power in parentheses, then the final expression after the first bound portion is calculated, and finally the output.

**MulDiv first, then AddSub**

```surql title="MulDiv first, then AddSub"
/**[test]

[[test.results]]
value = "13"

[[test.results]]
value = "13"

[[test.results]]
value = "13"

[[test.results]]
value = "13"

*/
 
1 + 3 * 4;
1 + (3 * 4);
-- Final expression
1 + 12;
-- Output
13
```

**Power first, then MulDiv**

```surql title="Power first, then MulDiv"
/**[test]

[[test.results]]
value = "24"

[[test.results]]
value = "24"

[[test.results]]
value = "24"

[[test.results]]
value = "24"

*/
 
2**3 * 3;
(2**3) * 3;
-- Final expression
8*3;
-- Output
24
```

**Unary first, then cast**

```surql title="Unary first, then cast"
/**[test]

[[test.results]]
value = "'-4'"

[[test.results]]
value = "'-4'"

[[test.results]]
value = "'-4'"

*/

<string>-4;
<string>(-4);
-- Output
"-4"
```

**Cast first, then Power**

```surql title="Cast first, then Power"
/**[test]

[[test.results]]
value = "387420489"

[[test.results]]
value = "387420489"

[[test.results]]
value = "387420489"

[[test.results]]
value = "387420489"

*/
 
<number>"9"**9;
(<number>"9")**9;
-- Final expression
9**9;
-- Output
387420489
```

**AddSub first, then Relation**

```surql title="AddSub first, then Relation"
/**[test]

[[test.results]]
value = "true"

[[test.results]]
value = "true"

[[test.results]]
value = "true"

[[test.results]]
value = "true"
*/
 
"c" + "at" IN "cats";
("c" + "at") IN "cats";
-- Final expression
"cat" IN "cats";
-- Output
true
```

**And first, then Or**

```surql title="And first, then Or"
/**[test]

[[test.results]]
value = "true"

[[test.results]]
value = "true"

[[test.results]]
value = "true"

[[test.results]]
value = "true"

*/
 
true AND false OR true;
(true AND false) OR true;
-- Final expression
false OR true;
-- Output
true
```

**Unary, then Cast, then Power, then AddSub**

```surql title="Unary, then Cast, then Power, then AddSub"
/**[test]

[[test.results]]
value = "20dec"

[[test.results]]
value = "20dec"

[[test.results]]
value = "20dec"

*/
 
<decimal>-4**2+4;
((<decimal>(-4))**2)+4;
-- Output
20dec
```

---
---

## _q003 - **Data types**_


SurrealQL allows you to describe data with specific data types. These data types are used to validate data and to generate the appropriate database schema.

| Type | Description |
| :--- | :--- |
| `any` | Use this when you explicitly don't want to specify the field's data type. The field will allow any data type supported by SurrealDB. |
| `array` | An array of items. The array type also allows you to define which types can be stored in the array and the required length.  `array`, `array<string>`, `array<string, 10>` |
| `bool` | Describes whether something is truthy or not. |
| [`bytes`][SurrealQL003_bytes] | Stores a value in a byte array. `<bytes>value`, `bytes` |
| `datetime` | An [RFC 3339][net__RFC_3339] compliant data type that stores a date with time and time zone. |
| `decimal` | Data type for storing [decimal floating point][net__wiki_decimal128] numbers. |
| `duration` | Store a value representing a length of time. Can be added or subtracted from datetimes or other durations. |
| `float` | Data type for storing [floating point][net__wiki_float64] numbers. Larger or extremely precise values should be stored as a decimal. |
| [`geometry`][SurrealQL003_geometry] | [RFC 7946][net__RFC_7946] compliant data type for storing geometry in the [GeoJson format][net__geojson].  `geometry<feature>`, `geometry<point>`, `geometry<line>`, `geometry<polygon>`, `geometry<multipoint>`, `geometry<multiline>`, `geometry<multipolygon>`, `geometry<collection>` |
| `int` | Store a value in a 64 bit signed integer. Values can range between `-9223372036854775808` and `9223372036854775807` (inclusive). Larger values should be stored as a float or a decimal. |
| `number` | Store numbers without specifying the type. SurrealDB will detect the type of number and store it using the minimal number of bytes. |
| `object` | Store formatted objects containing values of any supported type including nested objects or arrays. |
| `regex` | A compiled regular expression that can be used for matching strings. |
| [`literal`][SurrealQL015] | A value that may have multiple representations or formats, similar to an enum or a union type. Can be composed of strings, numbers, objects, arrays, or durations.  `”a” \| “b”`, `[number, “abc”]`, `123 \| 456 \| string \| 1y1m1d` |
| `option` | Makes types optional and guarantees the field to be either empty (NONE) or some other type.  `option<number>` |
| `range` | A range of possible values. Lower and upper bounds can be set, in the absence of which the range becomes open-ended. A range of integers can be used in a FOR loop.  `0..10`, `0..=10`, `..10`, `‘a’..‘z’` |
| `record` | Store a reference to another record. The value must be a Record ID. Add the record name inside angle brackets to restrict the reference to only certain record names.  `record`,`record<user>`,`record<user \| administrator>` |
| `set` | A set of items. The set type also allows you to define which types can be stored in the set and the required length. Items are automatically deduplicated and orderd. `set`, `set<string>`, `set<string, 10>` |
| `string` | Describes a text-like value. |

### _q003a - **Example geometry**_

```surql
-- Define a field with a single type
DEFINE FIELD location ON TABLE restaurant TYPE geometry<point>;
-- Define a field with any geometric type
DEFINE FIELD area ON TABLE restaurant TYPE geometry<feature>;
-- Define a field with specific geometric types
DEFINE FIELD area ON TABLE restaurant TYPE geometry<polygon|multipolygon|collection>;
```

### _q003b - **Example bytes**_

```surql
-- Define a field with a single type
DEFINE FIELD image ON TABLE product TYPE bytes;

-- Create a record with a bytes field and set the value
CREATE foo SET value = <bytes>"bar";

```

---
---

## _q004 - **Arrays**_

An array is a collection of values contained inside `[]` (square brackets), each of which is stored at a certain index. Individual indexes and slices of indexes can be accesses using the same square bracket syntax.

```surql
/**[test]

[[test.results]]
value = "[1, 2, 3, 4, 5]"

[[test.results]]
value = "1"

[[test.results]]
value = "[1, 2, 3]"

*/

-- Return a full array
RETURN [1,2,3,4,5];
-- Return the first ("zeroeth") item
RETURN [1,2,3,4,5][0];
-- Return indexes 0 up to and including 2 of an array
RETURN [1,2,3,4,5][0..=2];
```

```surql title="Output"
-------- Query 2 (200µs) --------

[
  1,
  2,
  3,
  4,
  5
]

-------- Query 3 (99.999µs) --------

1

-------- Query 4 (100.001µs) --------

[
  1,
  2,
  3
]
```

Working with arrays is one of the most important skills when working with SurrealDB, as [`SELECT`][SurrealQL079] statements return an array of values by default unless the `ONLY` keyword is used on an array that contains a single item.

```surql
/**[test]

[[test.results]]
value = "[9]"

[[test.results]]
value = "9"

[[test.results]]
error = "'Expected a single result output when using the ONLY keyword'"

*/

-- Even this returns an array
SELECT * FROM 9;
-- Use the `ONLY` clause to return a single item
SELECT * FROM ONLY 9;
-- Error: array has more than one item
SELECT * FROM ONLY [1,9];
```

```surql title="Output"
-------- Query 1  --------

[
  9
]

-------- Query 2 --------

9

-------- Query 3 --------

'Expected a single result output when using the ONLY keyword'
```

Similar to Object-based Record IDs, records in SurrealDB can store arrays of values, including arrays within arrays. Arrays can store any value stored within them, and can store different value types within the same array.

```surql
/**[test]

[[test.results]]
value = "[{ id: person:0l7qs8rfxw32q8namhnx, results: [{ date: '2017-06-18T08:00:00Z', name: 'Algorithmics', score: 76 }, { date: '2018-03-21T08:00:00Z', name: 'Concurrent Programming', score: 83 }, { date: '2018-09-17T08:00:00Z', name: 'Advanced Computer Science 101', score: 69 }, { date: '2019-04-20T08:00:00Z', name: 'Distributed Databases', score: 73 }] }]"
skip-record-id-key = true

*/

CREATE person SET results = [
  { score: 76, date: "2017-06-18T08:00:00Z", name: "Algorithmics" },
  { score: 83, date: "2018-03-21T08:00:00Z", name: "Concurrent Programming" },
  { score: 69, date: "2018-09-17T08:00:00Z", name: "Advanced Computer Science 101" },
  { score: 73, date: "2019-04-20T08:00:00Z", name: "Distributed Databases" },
];
```

A required number of items can be specified for an array.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
error = ""Couldn't coerce value for field `employees` of `team:2pjsv6kmzs0x06ortqfl`: Expected `array<record<employee>,5>` but found a collection of length `6`""

*/

DEFINE FIELD employees ON TABLE team TYPE array<record<employee>, 5>;
CREATE team SET employees = [
  employee:one, 
  employee:two, 
  employee:three, 
  employee:four, 
  employee:five, 
  employee:doesnt_belong
];
```

```surql title="Response"
"Couldn't coerce value for field `employees` of `team:2pjsv6kmzs0x06ortqfl`: Expected `array<record<employee>,5>` but found a collection of length `6`"
```

### _q004a - **Mapping and filtering on arrays**_

The `[]` operator after an array can also be used to filter the items inside an array. The parameter `$this` is used to refer to each individual item, while `WHERE` (or its alias `?`, a question mark) is used to set the condition for the item to pass the filter.

```surql
/**[test]

[[test.results]]
value = "[true, true]"

*/
[true, false, true][WHERE $this = true];
```

```surql title="Output"
[true, true]
```

If a `WHERE` or `?` clause finds an item that by itself is not equal to `true` or `false`, it will check the item's [truthiness][SurrealQL027] to determine whether to pass it on or not.

```surql
/**[test]

[[test.results]]
value = "[1, 2]"

*/

[1,2,NONE][? $this];

-- [1, 2]
```

Filtering can be repeated if desired.

```surql
/**[test]

[[test.results]]
value = "[{ first_mayor: 'Papa Smurf', name: 'Smurfville', population: 55 }]"

*/

[
    {
        name: "Boston",
        population: NONE,
        first_mayor: "John Phillips"
    },
    {
        name: "Smurfville",
        population: 55,
        first_mayor: "Papa Smurf"
    },
    {
        name: "Harrisburg",
        population: 50183,
        first_mayor: NONE
    }
][WHERE $this.population]
 [WHERE $this.first_mayor];
```

```surql title="Output"
[
  {
    first_mayor: 'Papa Smurf',
    name: 'Smurfville',
    population: 55
  }
]
```

> Available since: V2.0.0

### _q004b - **Filtering and mapping with array functions**_

SurrealDB also includes a number of methods for arrays that make it easier to filter and map. These methods take a closure (an anonymous function) that works in a similar way to the `$this` parameter above.

Here is an example of the `array::filter()` method being used in contrast to the classic `WHERE` syntax. Note that the parameter name inside the closure is named by the user, so `$val` in the example below could be `$v` or `$some_val` or anything else.

```surql
/**[test]

[[test.results]]
value = "[3, 5]"

[[test.results]]
value = "[3, 5]"

*/

[1,3,5].filter(|$val| $val > 2);
[1,3,5][WHERE $this > 2];

-- [3,5]
```

While the [array functions][SurrealQL101] section of the documentation contains the full details of each function, the following examples provide a glimpse into how they are commonly used.

The [`array::map()`](/docs/surrealql/functions/database/array#arraymap) function provides access to each item in an array, allowing an opearation to be performed on it before being passed on.

```surql
/**[test]

[[test.results]]
value = "[2, 3, 4]"

*/

[1,2,3].map(|$item| $item + 1);

-- [2,3,4]
```

If desired, a second parameter can be passed in that holds the index of the item.

```surql
/**[test]

[[test.results]]
value = "['At index 0 we got a 1!', 'At index 1 we got a 2!', 'At index 2 we got a 3!']"

*/

[1,2,3].map(|$v, $i| "At index " + <string>$i + " we got a " + <string>$v + "!");
```

```surql title="Output"
[
  'At index 0 we got a 1!',
  'At index 1 we got a 2!',
  'At index 2 we got a 3!'
]
```

Chaining these methods one after another is a convenient way to validate and modify data in a single statement. The example below removes any items with a `NONE`, checks to see if a the location data is a valid geometric point, and then returns the remaining items as objects with a different structure.

```surql
/**[test]

[[test.results]]
value = "[{ coordinates: (98, 65.7), item: 0, name: 'Some city' }, { coordinates: (0, 0.1), item: 1, name: 'Other city' }]"

*/

[
  NONE,
  {
    at: (98, 65.7),
    name: "Some city"
  },
  {
    at: (-190.7, 0),
    name: NONE
  },
    {
        name: "Other city",
        at: (0.0, 0.1)
    },
  {
        name: "Nonexistent city",
        at: (200.0, 66.5)
    }
]
    .filter(|$v| $v != NONE AND $v.name != NONE)
    .filter(|$v| $v.at.is_valid())
    .map(|$v, $i| {
        item: $i,
        name: $v.name,
        coordinates: $v.at
    });
```

```surql title="Output"
[
  {
    coordinates: (98, 65.7),
    item: 0,
    name: 'Some city'
  },
  {
    coordinates: (0, 0.1),
    item: 1,
    name: 'Other city'
  }
]
```

### _q004c - **Adding arrays**_

> Available since: V3.0.0

An array can be added to another array, resulting in a single array consisting of the items of the first followed by those of the second. This is identical to the `array::concat()` function.

```surql
/**[test]

[[test.results]]
value = "[1, 2, 3, 4]"

[[test.results]]
value = "[1, 2, 3, 4]"

*/

[1,2] + [3,4];
[1,2].concat([3,4]);
```

```surql title="Output"
[1,2,3,4]
```

---
---

## _q005 - **Booleans**_

---
---

## _q006 - **Bytes**_

---
---

## _q007 - **Casting**_

---
---

## _q008 - **Anonymous functions (closures)**_

---
---

## _q009 - **Datetimes**_

---
---

## _q010 - **Files**_

---
---

## _q011 - **Formatters**_

## _q012 - **Futures (`COMPUTED` clause)**_

## _q013 - **Geometries**_

## _q014 - **Idioms**_

## _q015 - **Literals**_

## _q016 - **None and null**_

## _q017 - **Numbers**_

## _q018 - **Objects**_

## _q019 - **Ranges**_

## _q020 - **Record IDs**_

## _q021 - **Record links**_

## _q022 - **Record references**_

## _q023 - **Regex**_

## _q024 - **Sets**_

## _q025 - **Strings**_

## _q026 - **UUIDs**_

---
---

## _q027 - **Values**_

Each of the types mentioned in the data model is a subset of an all-encompassing type called a value.

## Comparing and ordering values

While it is unsurprising that a data type can be compared with itself, it may be surprising that different types can also be compared with each other.

```surql
/**[test]

[[test.results]]
value = "true"

[[test.results]]
value = "true"

*/


RETURN 9 > 1;            // Returns true
RETURN [] > time::now(); // Also returns true
```

This comparison is possible because every type in SurrealDB is a subset of value, and a comparison of any type with another is also simply a comparison of a value with another value. The order of values from least to greatest is:

- `none`
- `null`
- `bool`
- `number`
- `string`
- `duration`
- `datetime`
- `uuid`
- `array`
- `set`
- `object`
- `geometry`
- `bytes`
- `table`
- `record`
- `file`
- `regex`
- `range`

As a result, all of the following return `true`.



```surql
/**[test]

[[test.results]]
value = "[true, true, true, true, true, true, true, true, true, true, true, true]"

*/

RETURN [
    null > none,
    true > null,
    1 > true,
    'a' > 999999999,
    1m > 'a',
    time::now() > 1m,
    rand::uuid() > time::now(),
    [ 9, 10 ] > rand::uuid(),
    { 9, 10 } > [ 9, 10 ],
    {} > { 9, 10 },
    (9.9, 9.9) > {},
    <bytes>"Aeon" > (9.9, 9.9),
    type::table("person") > <bytes>"Aeon",
    person:one > type::table("person"),
    f"file://myfile.txt" > person:one,
    <regex>"a|b" > f"file://myfile.txt",
    0..10 > <regex>"a|b",
    || > 0.. 10
];
```

Being able to compare a value with any other value is what makes SurrealDB's record range syntax possible.

```surql
/**[test]

[[test.results]]
value = "[{ id: time_data:[d'2024-07-23T00:00:00Z'] }]"

[[test.results]]
value = "[{ id: time_data:[d'2024-07-24T00:00:00Z'] }]"

[[test.results]]
value = "[{ id: time_data:[d'2024-07-25T00:00:00Z'] }]"

[[test.results]]
value = "[{ id: time_data:[d'2024-07-24T00:00:00Z'] }]"

[[test.results]]
value = "[{ id: time_data:[d'2024-07-24T00:00:00Z'] }, { id: time_data:[d'2024-07-25T00:00:00Z'] }]"

[[test.results]]
value = "[{ id: time_data:[d'2024-07-23T00:00:00Z'] }, { id: time_data:[d'2024-07-24T00:00:00Z'] }, { id: time_data:[d'2024-07-25T00:00:00Z'] }]"

*/

CREATE time_data:[d'2024-07-23T00:00:00.000Z'];
CREATE time_data:[d'2024-07-24T00:00:00.000Z'];
CREATE time_data:[d'2024-07-25T00:00:00.000Z'];
-- Records from the 24th to the 25th
SELECT * FROM time_data:[d'2024-07-24']..[d'2024-07-25'];
-- Records from the 24th
SELECT * FROM time_data:[d'2024-07-24']..;
-- All records
SELECT * FROM time_data:[NONE]..;
```

The `..` open-range syntax also represents an infinite value inside a record range query, making it the greatest possible value and the inverse of `NONE`, the lowest possible value. A part of a record range query that begins with `NONE` and ends with `..` will thus filter out nothing.

```surql
/**[test]

[[test.results]]
value = "[{ id: temperature:['London', d'2025-02-19T00:00:00Z'], val: 5.5f }]"

[[test.results]]
value = "[{ id: temperature:['London', d'2025-02-20T00:00:00Z'], val: 5.7f }]"

[[test.results]]
value = "[{ id: temperature:['London', d'2025-02-19T00:00:00Z'], val: 5.5f }, { id: temperature:['London', d'2025-02-20T00:00:00Z'], val: 5.7f }]"

*/

CREATE temperature:['London', d'2025-02-19T00:00:00.000Z'] SET val = 5.5;
CREATE temperature:['London', d'2025-02-20T00:00:00.000Z'] SET val = 5.7;

-- Return all records as long as index 0 = 'London'
SELECT * FROM temperature:['London', NONE]..=['London', ..];
```

```surql title="Output"
[
  {
    id: temperature:[
      'London',
      d'2025-02-19T00:00:00Z'
    ],
    val: 5.5f
  },
  {
    id: temperature:[
      'London',
      d'2025-02-20T00:00:00Z'
    ],
    val: 5.7f
  }
]
```

Inside a schema, the keyword `any` is used to denote any possible value.

```surql
/**[test]

[[test.results]]
value = "NONE"

*/

DEFINE FIELD anything ON TABLE person TYPE any;
```

## Values and truthiness

Any value is considered to be truthy if it is not NONE, NULL, or a default value for the data type. A data type at its default value is one that is empty, such as an empty string or array or object, or a number set to 0.

The following example shows the result of the `array::all()` method, which checks to see if all of the items inside an array are truthy or not.

```surql
/**[test]

[[test.results]]
value = "false"

[[test.results]]
value = "false"

[[test.results]]
value = "true"

*/

RETURN array::all(["", 1, 2, 3]); // false because of ""
RETURN array::all([{}, 1, 2, 3]); // false because of {}
RETURN array::all(["SurrealDB", { is_nice_database: true }, 1, 2, 3]);  // true
```

As [the ! operator](/docs/surrealql/operators) reverses the truthiness of a value, a doubling of this operator can also be used to check for truthiness.

```surql
/**[test]

[[test.results]]
value = "[true, false, true, false, true, false]"

*/

RETURN [
    !!"Has a value", !!"",             // true, false
    !!true, !!false,                   // true, false
    !!{ is_nice_database: true }, !!{} // true, false
    ];
```

---
---

## _q028 - **Statements**_

## _q029 - **`ACCESS` statement**_

## _q030 - **`ALTER` statement**_

## _q031 - **`ALTER DATABASE` statement**_

## _q032 - **`ALTER FIELD` statement**_

## _q033 - **`ALTER INDEX` statement**_

## _q034 - **`ALTER NAMESPACE` statement**_

## _q035 - **`ALTER SEQUENCE` statement**_

## _q036 - **`ALTER SYSTEM` statement**_

## _q037 - **`ALTER TABLE` statement**_

## _q038 - **`BEGIN` statement**_

## _q039 - **`BREAK` statement**_

## _q040 - **`CANCEL` statement**_

## _q041 - **`COMMIT` statement**_

## _q042 - **`CONTINUE` statement**_

## _q043 - **`CREATE` statement**_

## _q044 - **`DEFINE` statement**_

## _q045 - **`DEFINE ACCESS` statement**_

## _q046 - **`DEFINE ACCESS ... TYPE BEARER`**_

## _q047 - **`DEFINE ACCESS ... TYPE JWT`**_

## _q048 - **`DEFINE ACCESS ... TYPE RECORD`**_

## _q049 - **`DEFINE ANALYZER` statement**_

## _q050 - **`DEFINE API` statement**_

## _q051 - **`DEFINE BUCKET` statement**_

## _q052 - **`DEFINE CONFIG` statement**_

## _q053 - **`DEFINE DATABASE` statement**_

## _q054 - **`DEFINE EVENT` statement**_

## _q055 - **`DEFINE FIELD` statement**_

## _q056 - **`DEFINE FUNCTION` statement**_

## _q057 - **`DEFINE INDEX` statement**_

## _q058 - **`DEFINE MODULE` statement**_

## _q059 - **`DEFINE NAMESPACE` statement**_

## _q060 - **`DEFINE PARAM` statement**_

## _q061 - **`DEFINE SCOPE` statement**_

## _q062 - **`DEFINE SEQUENCE` statement**_

## _q063 - **`DEFINE TABLE` statement**_

## _q064 - **`DEFINE TOKEN` statement**_

## _q065 - **`DEFINE USER` statement**_

## _q066 - **`DELETE` statement**_

## _q067 - **`EXPLAIN` statement**_

## _q068 - **`FOR` statement**_

## _q069 - **`IF ELSE` statement**_

## _q070 - **`INFO` statement**_

## _q071 - **`INSERT` statement**_

## _q072 - **`KILL` statement**_

## _q073 - **`LET` statement**_

## _q074 - **`LIVE SELECT` statement**_

## _q075 - **`REBUILD` statement**_

## _q076 - **`RELATE` statement**_

## _q077 - **`REMOVE` statement**_

## _q078 - **`RETURN` statement**_

## _q079 - **`SELECT` statement**_

## _q080 - **`SHOW` statement**_

## _q081 - **`SLEEP` statement**_

## _q082 - **`THROW` statement**_

## _q083 - **`UPDATE` statement**_

## _q084 - **`UPSERT` statement**_

## _q085 - **`USE` statement**_

## _q086 - **Clauses**_

## _q087 - **`EXPLAIN` clauses**_

## _q088 - **`FETCH` clauses**_

## _q089 - **`FROM` clauses**_

## _q090 - **`GROUP BY` clauses**_

## _q091 - **`LIMIT` clauses**_

## _q092 - **`OMIT` clauses**_

## _q093 - **`ORDER BY` clauses**_

## _q094 - **`SPLIT` clauses**_

## _q095 - **`WHERE` clauses**_

## _q096 - **`WITH` clauses**_

---
---

## _q097 - **Parameters**_

---
---

## _q098 - **Functions**_

SurrealDB offers a number of functions that can be used to perform complex logic. These functions are grouped into the following categories:

- [Database functions][SurrealQL099]
- [JavaScript functions][SurrealQL127]
- [SurrealML functions][SurrealQL133]

---
---

## _q099 - **Database Functions**_

---
---

## _q100 - **API functions**_

---
---

## _q101 - **Array functions**_

These functions can be used when working with, and manipulating arrays of data.

| Function | Description |
| :--- | :--- |
| [`array::add()`][SurrealQL101_add] | Adds an item to an array if it doesn't exist |
| [`array::all()`](#arrayall) | Checks whether all array values are truthy, or equal to a condition |
| [`array::any()`](#arrayany) | Checks whether any array value is truthy, or equal to a condition |
| [`array::at()`](#arrayat) | Returns value for X index, or in reverse for a negative index |
| [`array::append()`](#arrayappend) | Appends an item to the end of an array |
| [`array::boolean_and()`](#arrayboolean_and) | Perform the AND bitwise operations on two arrays |
| [`array::boolean_or()`](#arrayboolean_or) | Perform the OR bitwise operations on two arrays |
| [`array::boolean_xor()`](#arrayboolean_xor) | Perform the XOR bitwise operations on two arrays |
| [`array::boolean_not()`](#arrayboolean_not) | Perform the NOT bitwise operations on an array |
| [`array::combine()`](#arraycombine) | Combines all values from two arrays together |
| [`array::complement()`](#arraycomplement) | Returns the complement of two arrays |
| [`array::clump()`](#arrayclump) | Returns the original array split into multiple arrays of X size |
| [`array::concat()`](#arrayconcat) | Returns the merged values from two arrays |
| [`array::difference()`](#arraydifference) | Returns the difference between two arrays |
| [`array::distinct()`](#arraydistinct) | Returns the unique items in an array |
| [`array::fill()`](#arrayfill) | Fills an existing array of the same value |
| [`array::filter()`](#arrayfilter) | Filters out values that do not match a pattern |
| [`array::filter_index()`](#arrayfilter_index) | Returns the indexes of all occurrences of all matching X value |
| [`array::find()`](#arrayfind) | Returns the first matching value |
| [`array::find_index()`](#arrayfind_index) | Returns the index of the first occurrence of X value |
| [`array::first()`](#arrayfirst) | Returns the first item in an array |
| [`array::flatten()`](#arrayflatten) | Flattens multiple arrays into a single array |
| [`array::fold()`](#arrayfold) | Applies an operation on an initial value plus every element in the array, returning the final result |
| [`array::group()`](#arraygroup) | Flattens and returns the unique items in an array |
| [`array::insert()`](#arrayinsert) | Inserts an item at the end of an array, or in a specific position |
| [`array::intersect()`](#arrayintersect) | Returns the values which intersect two arrays |
| [`array::is_empty()`](#arrayis_empty) | Checks if an array is empty |
| [`array::join()`](#arrayjoin) | Returns concatenated value of an array with a string in between |
| [`array::last()`](#arraylast) | Returns the last item in an array |
| [`array::len()`](#arraylen) | Returns the length of an array |
| [`array::logical_and()`](#arraylogical_and) | Performs the AND logical operations on two arrays |
| [`array::logical_or()`](#arraylogical_or) | Performs the OR logical operations on two arrays |
| [`array::logical_xor()`](#arraylogical_xor) | Performs the XOR logical operations on two arrays |
| [`array::map()`](#arraymap) | Applies an operation to every item in an array and passes it on |
| [`array::max()`](#arraymax) | Returns the greatest item from an array |
| [`array::matches()`](#arraymatches) | Returns an array of booleans indicating which elements of the input array contain a specified value |
| [`array::min()`](#arraymin) | Returns the least item from an array |
| [`array::pop()`](#arraypop) | Returns the last item from an array |
| [`array::prepend()`](#arrayprepend) | Prepends an item to the beginning of an array |
| [`array::push()`](#arraypush) | Appends an item to the end of an array |
| [`array::range()`](#arrayrange) | Creates a number array from a range (start to end) |
| [`array::reduce()`](#arrayreduce) | Applies an operation on every element in the array, returning the final result |
| [`array::remove()`](#arrayremove) | Removes an item at a specific position from an array |
| [`array::repeat()`](#arrayrepeat) | Creates an array a given size with a specified value used for each element |
| [`array::reverse()`](#arrayreverse) | Reverses the sorting order of an array |
| [`array::sequence()`](#arrayshuffle) | Creates an array of sequential integers |
| [`array::shuffle()`](#arrayshuffle) | Randomly shuffles the contents of an array |
| [`array::slice()`](#arrayslice) | Returns a slice of an array |
| [`array::sort()`](#arraysort) | Sorts the values in an array in ascending or descending order |
| [`array::sort_lexical()`](#arraysort_lexical) | Sorts the values in an array, with strings sorted lexically |
| [`array::sort_natural()`](#arraysort_natural) | Sorts the values in an array, with numeric strings sorted numerically |
| [`array::sort_natural_lexical()`](#arraysort_natural_lexical) | Sorts values using natural numeric and lexical ordering |
| [`array::sort::asc()`](#arraysortasc) | Sorts the values in an array in ascending order |
| [`array::sort::desc()`](#arraysortdesc) | Sorts the values in an array in descending order |
| [`array::swap()`](#arrayswap) | Swaps two items in an array |
| [`array::transpose()`](#arraytranspose) | Performs 2D array transposition |
| [`array::union()`](#arrayunion) | Returns the unique merged values from two arrays |
| [`array::windows()`](#arraywindows) | Returns arrays of length `size`, sliding across the original array |

### _q101aa - **`array::add`**_

### _q101ab - **`array::all`**_

### _q101ac - **`array::any`**_

### _q101ad - **`array::at`**_

### _q101ae - **`array::append`**_

### _q101af - **`array::boolean_and`**_

### _q101ag - **`array::boolean_or`**_

### _q101ah - **`array::boolean_xor`**_

### _q101ai - **`array::boolean_not`**_

### _q101aj - **`array::combine`**_

### _q101ak - **`array::complement`**_

### _q101al - **`array::concat`**_

### _q101am - **`array::clump`**_

### _q101an - **`array::difference`**_

### _q101ao - **`array::distinct`**_

### _q101ap - **`array::fill`**_

### _q101aq - **`array::filter`**_

### _q101ar - **`array::filter_index`**_

### _q101as - **`array::find`**_

### _q101at - **`array::find_index`**_

### _q101au - **`array::first`**_

### _q101av - **`array::flatten`**_

### _q101aw - **`array::fold`**_

### _q101ax - **`array::group`**_

### _q101ay - **`array::insert`**_

### _q101az - **`array::intersect`**_

### _q101ba - **`array::is_empty`**_

### _q101bb - **`array::join`**_

### _q101bc - **`array::last`**_

### _q101bd - **`array::len`**_

### _q101be - **`array::logical_and`**_

### _q101bf - **`array::logical_or`**_

### _q101bg - **`array::logical_xor`**_

### _q101bh - **`array::map`**_

### _q101bi - **`array::max`**_

### _q101bj - **`array::matches`**_

### _q101bk - **`array::min`**_

### _q101bl - **`array::pop`**_

### _q101bm - **`array::prepend`**_

### _q101bn - **`array::push`**_

### _q101bo - **`array::range`**_

### _q101bp - **`array::reduce`**_

### _q101bq - **`array::remove`**_

### _q101br - **`array::repeat`**_

### _q101bs - **`array::reverse`**_

### _q101bt - **`array::sequence`**_

### _q101bu - **`array::shuffle`**_

### _q101bv - **`array::slice`**_

### _q101bw - **`array::sort`**_

### _q101bx - **`array::sort_lexical`**_

### _q101by - **`array::sort_natural`**_

### _q101bz - **`array::sort_natural_lexical`**_

### _q101ca - **`array::sort::asc`**_

### _q101cb - **`array::sort::desc`**_

### _q101cc - **`array::swap`**_

### _q101cd - **`array::transpose`**_

### _q101ce - **`array::union`**_

### _q101cf - **`array::windows`**_

### _q101cg - **Method chaining**_

---
---

## _q102 - **Bytes functions**_

---
---

## _q103 - **Count function**_

---
---

## _q104 - **Crypto functions**_

---
---

## _q105 - **Duration functions**_

---
---

## _q106 - **Encoding functions**_

---
---

## _q107 - **File functions**_

---
---

## _q108 - **Geo functions**_

---
---

## _q109 - **HTTP functions**_

---
---

## _q110 - **Math functions**_

---
---

## _q111 - **Meta functions**_

---
---

## _q112 - **Not function**_

---
---

## _q113 - **Object functions**_

---
---

## _q114 - **Parse functions**_

---
---

## _q115 - **Rand functions**_

---
---

## _q116 - **Record functions**_

---
---

## _q117 - **Search functions**_

---
---

## _q118 - **Sequence functions**_

---
---

## _q119 - **Session functions**_

---
---

## _q120 - **Set functions**_

---
---

## _q121 - **Sleep function**_

---
---

## _q122 - **String Functions**_

---
---

## _q123 - **Time Functions**_

---
---

## _q124 - **Type Functions**_

---
---

## _q125 - **Value functions**_

---
---

## _q126 - **Vector functions**_

---
---

## _q127 - **Embedded scripting functions**_

---
---

## _q128 - **Arguments**_

---
---

## _q129 - **Built-in functions**_

---
---

## _q130 - **Function context**_

---
---

## _q131 - **Type conversion**_

---
---

---
---

## _q132 - **SurrealQL functions**_

---
---

## _q133 - **Machine Learning functions**_

---
---

## _q134 - **Machine Learning functions**_

---
---

## _q135 - **Transactions**_

Each statement within SurrealDB is run within its own transaction by default. If a set of changes need to be made together, then groups of statements can be run together as a single transaction. If all of the statements within a transaction succeed, and the transaction is successful, then all of the data modifications made during the transaction are committed and become a permanent part of the database. If a transaction encounters errors and must be cancelled or rolled back, then any data modification made within the transaction is rolled back, and will not become a permanent part of the database.

### _q135a - **Starting a transaction**_

The `BEGIN` or `BEGIN TRANSACTION` statement starts a transaction in which multiple statements can be run together.

```surql title="Starting a transaction"
BEGIN [ TRANSACTION ];
```

The following query shows example usage of this statement.

```surql title="Example usage of BEGIN TRANSACTION"
/**[test]

[[test.results]]
value = "[{ balance: 135605.16f, id: account:one }]"

[[test.results]]
value = "[{ balance: 91031.31f, id: account:two }]"

[[test.results]]
value = "[{ balance: 135905.16f, id: account:one }]"

[[test.results]]
value = "[{ balance: 90731.31f, id: account:two }]"

*/

-- Start a new database transaction. Transactions are a way to ensure multiple operations
-- either all succeed or all fail, maintaining data integrity.
BEGIN TRANSACTION;

-- Create a new account with the ID 'one' and set its initial balance to 135605.16
CREATE account:one SET balance = 135605.16;

-- Create another new account with the ID 'two' and set its initial balance to 91031.31
CREATE account:two SET balance = 91031.31;

-- Update the balance of account 'one' by adding 300.00 to the current balance.
-- This could represent a deposit or other form of credit on the balance property.
UPDATE account:one SET balance += 300.00;

-- Update the balance of account 'two' by subtracting 300.00 from the current balance.
-- This could represent a withdrawal or other form of debit on the balance property.
UPDATE account:two SET balance -= 300.00;

-- Finalize the transaction. This will apply the changes to the database. If there was an error
-- during any of the previous steps within the transaction, all changes would be rolled back and
-- the database would remain in its initial state.
COMMIT TRANSACTION;
```

### _q135b - **Committing a transaction**_

The [COMMIT][SurrealQL041] statement is used to commit a set of statements within a transaction, ensuring that all data modifications become a permanent part of the database.

```surql title="Committing a transaction"
COMMIT [ TRANSACTION ];
```

The following query shows example usage of this statement.

```surql title="Example usage of COMMIT TRANSACTION"
/**[test]

[[test.results]]
value = "[{ balance: 135605.16f, id: account:one }]"

[[test.results]]
value = "[{ balance: 91031.31f, id: account:two }]"

[[test.results]]
value = "[{ balance: 135905.16f, id: account:one }]"

[[test.results]]
value = "[{ balance: 90731.31f, id: account:two }]"

*/

BEGIN TRANSACTION;

-- Setup accounts
CREATE account:one SET balance = 135605.16;
CREATE account:two SET balance = 91031.31;

-- Move money
UPDATE account:one SET balance += 300.00;
UPDATE account:two SET balance -= 300.00;

-- Finalise all changes
COMMIT TRANSACTION;
```

### _q135c - **Cancelling a transaction**_

The [CANCEL][SurrealQL040] statement can be used to cancel a set of statements within a transaction, reverting or rolling back any data modification made within the transaction as a whole.

```surql title="Cancelling a transaction"
CANCEL [ TRANSACTION ];
```

The following query shows example usage of this statement.

```surql title="Example usage of CANCEL TRANSACTION"
/**[test]

[[test.results]]
error = "'Thrown error: The query was not executed due to a cancelled transaction'"

[[test.results]]
error = "'Thrown error: The query was not executed due to a cancelled transaction'"

[[test.results]]
error = "'Thrown error: The query was not executed due to a cancelled transaction'"

[[test.results]]
error = "'Thrown error: The query was not executed due to a cancelled transaction'"

*/

BEGIN TRANSACTION;

-- Setup accounts
CREATE account:one SET balance = 135605.16;
CREATE account:two SET balance = 91031.31;

-- Move money
UPDATE account:one SET balance += 300.00;
UPDATE account:two SET balance -= 300.00;

-- Rollback all changes
CANCEL TRANSACTION;
```

### _q135d - **THROW to conditionally cancel a transaction**_

While transactions are automatically rolled back if an error occurs in any of its statements, [THROW][SurrealQL082] can also be used to explicitly break out of a transaction at any point. `THROW` can be followed by any value which serves as the error message, usually a string.

```surql
BEGIN TRANSACTION;

CREATE account:one SET dollars =  100;
CREATE account:two SET dollars =  100;

LET $transfer_amount = 150;
UPDATE account:one SET dollars -= $transfer_amount;
UPDATE account:two SET dollars += $transfer_amount;
IF account:one.dollars < 0 {
    THROW "Insufficient funds, would have $" + <string>account:one.dollars + " after transfer"
};
COMMIT TRANSACTION;
SELECT * FROM account;
```

```surql title="Output when $transfer_amount set to 150"
'An error occurred: Insufficient funds, would have $-50 after transfer'
```

```surql title="Output when $transfer_amount set to 50"
[
  {
    dollars: 50,
    id: account:one
  },
  {
    dollars: 150,
    id: account:two
  }
]
```

### _q135e - **Using transactions to test code for errors**_

As failed transactions automatically roll back any changes made, a transaction with a final `THROW` statement can be used as a confirmation that no errors have taken place inside a group of queries.

Take the following example that creates a unique index and then inserts some records to make sure that the database logic is functioning as expected. However, as names are not necessarily unique, the index soon gives an error and cancels the transaction before `THROW` can be reached.

```surql
BEGIN TRANSACTION;
DEFINE INDEX unique_name ON TABLE person FIELDS name UNIQUE;

INSERT INTO person [
    { name: 'Agatha Christie', born: d'1890-09-15' },
    { name: 'Billy Billerson', born: d'1979-09-11' },
  -- Pretend there are is 10,000 more objects here
    { name: 'Agatha Christie', born: d'1955-05-15' },
];

THROW "Reached the end";
COMMIT TRANSACTION;
```

The output is not the expected 'An error occurred: Reached the end' message, showing that not all queries were successful.

```surql title="Output"
"Database index `unique_name` already contains 'Agatha Christie', with record `person:qs4bpvl96sf9x40b3567`"
```

If the index is redefined to be less strict, the statetements will work and the expected output will be reached, confirming that no errors occurred during the test.

```surql
BEGIN TRANSACTION;
DEFINE INDEX OVERWRITE unique_person ON TABLE person FIELDS name, born UNIQUE;

INSERT INTO person [
    { name: 'Agatha Christie', born: d'1890-09-15' },
    { name: 'Billy Billerson', born: d'1979-09-11' },
    { name: 'Agatha Christie', born: d'1955-05-15' },
];

THROW "Reached the end";
COMMIT TRANSACTION;
```

```surql title="Expected output"
'An error occurred: Reached the end'
```

---
---

## _q136 - **Comments**_

In SurrealQL, comments can be written in a number of different ways.

```surql
/*
In SurrealQL, comments can be written as single-line
or multi-line comments, and comments can be used and
interspersed within statements.
*/

SELECT * FROM /* get all users */ user;

# There are a number of ways to use single-line comments
SELECT * FROM user;

// Alternatively using two forward-slash characters
SELECT * FROM user;

-- Another way is to use two dash characters
SELECT * FROM user;
```

---
---
[test000][SurrealQL000]
[test001][SurrealQL001]
[test002][SurrealQL002]
[test003][SurrealQL003]
[test004][SurrealQL004]
[test005][SurrealQL005]
[test006][SurrealQL006]
[test007][SurrealQL007]
[test008][SurrealQL008]
[test009][SurrealQL009]
[test010][SurrealQL010]
[test011][SurrealQL011]
[test012][SurrealQL012]
[test013][SurrealQL013]
[test014][SurrealQL014]
[test015][SurrealQL015]
[test016][SurrealQL016]
[test017][SurrealQL017]
[test018][SurrealQL018]
[test019][SurrealQL019]
[test020][SurrealQL020]
[test021][SurrealQL021]
[test022][SurrealQL022]
[test023][SurrealQL023]
[test024][SurrealQL024]
[test025][SurrealQL025]
[test026][SurrealQL026]
[test027][SurrealQL027]
[test028][SurrealQL028]
[test029][SurrealQL029]
[test030][SurrealQL030]
[test031][SurrealQL031]
[test032][SurrealQL032]
[test033][SurrealQL033]
[test034][SurrealQL034]
[test035][SurrealQL035]
[test036][SurrealQL036]
[test037][SurrealQL037]
[test038][SurrealQL038]
[test039][SurrealQL039]
[test040][SurrealQL040]
[test041][SurrealQL041]
[test042][SurrealQL042]
[test043][SurrealQL043]
[test044][SurrealQL044]
[test045][SurrealQL045]
[test046][SurrealQL046]
[test047][SurrealQL047]
[test048][SurrealQL048]
[test049][SurrealQL049]
[test050][SurrealQL050]
[test051][SurrealQL051]
[test052][SurrealQL052]
[test053][SurrealQL053]
[test054][SurrealQL054]
[test055][SurrealQL055]
[test056][SurrealQL056]
[test057][SurrealQL057]
[test058][SurrealQL058]
[test059][SurrealQL059]
[test060][SurrealQL060]
[test061][SurrealQL061]
[test062][SurrealQL062]
[test063][SurrealQL063]
[test064][SurrealQL064]
[test065][SurrealQL065]
[test066][SurrealQL066]
[test067][SurrealQL067]
[test068][SurrealQL068]
[test069][SurrealQL069]
[test070][SurrealQL070]
[test071][SurrealQL071]
[test072][SurrealQL072]
[test073][SurrealQL073]
[test074][SurrealQL074]
[test075][SurrealQL075]
[test076][SurrealQL076]
[test077][SurrealQL077]
[test078][SurrealQL078]
[test079][SurrealQL079]
[test080][SurrealQL080]
[test081][SurrealQL081]
[test082][SurrealQL082]
[test083][SurrealQL083]
[test084][SurrealQL084]
[test085][SurrealQL085]
[test086][SurrealQL086]
[test087][SurrealQL087]
[test088][SurrealQL088]
[test089][SurrealQL089]
[test090][SurrealQL090]
[test091][SurrealQL091]
[test092][SurrealQL092]
[test093][SurrealQL093]
[test094][SurrealQL094]
[test095][SurrealQL095]
[test096][SurrealQL096]
[test097][SurrealQL097]
[test098][SurrealQL098]
[test099][SurrealQL099]
[test100][SurrealQL100]
[test101][SurrealQL101]
[test102][SurrealQL102]
[test103][SurrealQL103]
[test104][SurrealQL104]
[test105][SurrealQL105]
[test106][SurrealQL106]
[test107][SurrealQL107]
[test108][SurrealQL108]
[test109][SurrealQL109]
[test110][SurrealQL110]
[test111][SurrealQL111]
[test112][SurrealQL112]
[test113][SurrealQL113]
[test114][SurrealQL114]
[test115][SurrealQL115]
[test116][SurrealQL116]
[test117][SurrealQL117]
[test118][SurrealQL118]
[test119][SurrealQL119]
[test120][SurrealQL120]
[test121][SurrealQL121]
[test122][SurrealQL122]
[test123][SurrealQL123]
[test124][SurrealQL124]
[test125][SurrealQL125]
[test126][SurrealQL126]
[test127][SurrealQL127]
[test128][SurrealQL128]
[test129][SurrealQL129]
[test130][SurrealQL130]
[test131][SurrealQL131]
[test132][SurrealQL132]
[test133][SurrealQL133]
[test134][SurrealQL134]
[test135][SurrealQL135]
[test136][SurrealQL136]

[SurrealQL000]:            <#q000---surrealql> "SurrealQL"
[SurrealQL001]:            <#q001---demo-data> "SurrealQL 🞂 Demo data"
[SurrealQL002]:            <#q002---operators> "SurrealQL 🞂 Operators"
[SurrealQL002_and]:        <#q002aa----or-and> "`&&` or `AND`"
[SurrealQL002_or]:         <#q002ab----or-or> "`||` or `OR`"
[SurrealQL002_not]:        <#q002ac----not> "`!` (not)"
[SurrealQL002_notnot]:     <#q002ad----not-not> "`!!` (not not)"
[SurrealQL002_null]:       <#q002ae----null-coalescing> "`??` (null coalescing)"
[SurrealQL002_truthy]:     <#q002af----truthy-coalescing> "`??` (truthy coalescing)"
[SurrealQL002_equal]:      <#q002ag----or-is> "`=` or `IS`"
[SurrealQL002_notequal]:   <#q002ah----or-is-not> "`=` or `IS`"
[SurrealQL002_exact]:      <#q002ai----exact> "`==` (exact)"
[SurrealQL002_anyequal]:   <#q002aj----any-equal> "`?=` (any equal)"
[SurrealQL002_allequal]:   <#q002ak----all-equal> "`*=` (all equal)"
[SurrealQL002_similar]:    <#q002al-------similarity> "`~` `?~` `!~` `*~` (similarity)"
[SurrealQL002_less]:       <#q002am----less> "`<` (less)"
[SurrealQL002_lessequal]:  <#q002an----less-or-equal> "`<=` (less or equal)"
[SurrealQL002_more]:       <#q002ao----more> "`>` (more)"
[SurrealQL002_moreequal]:  <#q002ap----more-or-equal> "`>=` (more or equal)"
[SurrealQL002_add]:        <#q002aq----add> "`+` (add)"
[SurrealQL002_sub]:        <#q002ar-----sub> "`-` (sub)"
[SurrealQL002_mul]:        <#q002as----or--mul> "`*` or `×` (mul)"
[SurrealQL002_div]:        <#q002at----or--div> "`/` or `÷`  (div)"
[SurrealQL002_pow]:        <#q002au----pow> "`**` (pow)"
[SurrealQL002_co_equ]:     <#q002av---contains-or-> "`CONTAINS` or `∋`"
[SurrealQL002_co_not]:     <#q002aw---containsnot-or-> "`CONTAINSNOT` or `∌`"
[SurrealQL002_co_all]:     <#q002ax---containsall-or-> "`CONTAINSALL` or `⊇`"
[SurrealQL002_co_any]:     <#q002ay---containsany-or-> "`CONTAINSANY` or `⊃`"
[SurrealQL002_co_non]:     <#q002az---containsnone-or-> "`CONTAINSNONE` or `⊅`"
[SurrealQL002_in_equ]:     <#q002ba---inside-or--or-in> "`INSIDE` or `∈` or `IN`"
[SurrealQL002_in_not]:     <#q002bb---notinside-or--or-not-in> "`NOTINSIDE` or `∉` or `NOT IN`"
[SurrealQL002_in_all]:     <#q002bc---allinside-or-> "`ALLINSIDE` or `⊆`"
[SurrealQL002_in_any]:     <#q002bd---anyinside-or-> "`ANYINSIDE` or `⊂`"
[SurrealQL002_in_non]:     <#q002be---noneinside-or-> "`NONEINSIDE` or `⊄`"
[SurrealQL002_outside]:    <#q002bf---outside> "`OUTSIDE`"
[SurrealQL002_inter]:      <#q002bg---intersects> "`INTERSECTS`"
[SurrealQL002_matches]:    <#q002bh---matches> "`MATCHES`"
[SurrealQL002_knn]:        <#q002bi---knn> "`KNN`"
[SurrealQL003]:            <#q003---data-types> "SurrealQL 🞂 Data types"
[SurrealQL003_geometry]:   <#q003a---example-geometry> "Example geometry"
[SurrealQL003_bytes]:      <#q003b---example-bytes> "Example bytes"
[SurrealQL004]:            <#q004---arrays> "SurrealQL 🞂 Data type 🞂 Arrays"
[SurrealQL005]:            <#q005---booleans> "SurrealQL 🞂 Data type 🞂 Booleans"
[SurrealQL006]:            <#q006---bytes> "SurrealQL 🞂 Data type 🞂 Bytes"
[SurrealQL007]:            <#q007---casting> "SurrealQL 🞂 Data type 🞂 Casting"
[SurrealQL008]:            <#q008---anonymous-functions-closures> "SurrealQL 🞂 Data type 🞂 Anonymous functions (closures)"
[SurrealQL009]:            <#q009---datetimes> "SurrealQL 🞂 Data type 🞂 Datetimes"
[SurrealQL010]:            <#q010---files> "SurrealQL 🞂 Data type 🞂 Files"
[SurrealQL011]:            <#q011---formatters> "SurrealQL 🞂 Data type 🞂 Formatters"
[SurrealQL012]:            <#q012---futures-computed-clause> "SurrealQL 🞂 Data type 🞂 Futures (`COMPUTED` clause)"
[SurrealQL013]:            <#q013---geometries> "SurrealQL 🞂 Data type 🞂 Geometries"
[SurrealQL014]:            <#q014---idioms> "SurrealQL 🞂 Data type 🞂 Idioms"
[SurrealQL015]:            <#q015---literals> "SurrealQL 🞂 Data type 🞂 Literals"
[SurrealQL016]:            <#q016---none-and-null> "SurrealQL 🞂 Data type 🞂 None and null"
[SurrealQL017]:            <#q017---numbers> "SurrealQL 🞂 Data type 🞂 Numbers"
[SurrealQL018]:            <#q018---objects> "SurrealQL 🞂 Data type 🞂 Objects"
[SurrealQL019]:            <#q019---ranges> "SurrealQL 🞂 Data type 🞂 Ranges"
[SurrealQL020]:            <#q020---record-ids> "SurrealQL 🞂 Data type 🞂 Record IDs"
[SurrealQL021]:            <#q021---record-links> "SurrealQL 🞂 Data type 🞂 Record links"
[SurrealQL022]:            <#q022---record-references> "SurrealQL 🞂 Data type 🞂 Record references"
[SurrealQL023]:            <#q023---regex> "SurrealQL 🞂 Data type 🞂 Regex"
[SurrealQL024]:            <#q024---sets> "SurrealQL 🞂 Data type 🞂 Sets"
[SurrealQL025]:            <#q025---strings> "SurrealQL 🞂 Data type 🞂 Strings"
[SurrealQL026]:            <#q026---uuids> "SurrealQL 🞂 Data type 🞂 UUIDs"
[SurrealQL027]:            <#q027---values> "SurrealQL 🞂 Data type 🞂 Values"
[SurrealQL028]:            <#q028---statements> "SurrealQL 🞂 Statements"
[SurrealQL029]:            <#q029---access-statement> "SurrealQL 🞂 Statement 🞂 `ACCESS`"
[SurrealQL030]:            <#q030---alter-statement> "SurrealQL 🞂 Statement 🞂 `ALTER`"
[SurrealQL031]:            <#q031---alter-database-statement> "SurrealQL 🞂 Statement 🞂 `ALTER` 🞂 `DATABASE`"
[SurrealQL032]:            <#q032---alter-field-statement> "SurrealQL 🞂 Statement 🞂 `ALTER` 🞂 `FIELD`"
[SurrealQL033]:            <#q033---alter-index-statement> "SurrealQL 🞂 Statement 🞂 `ALTER` 🞂 `INDEX`"
[SurrealQL034]:            <#q034---alter-namespace-statement> "SurrealQL 🞂 Statement 🞂 `ALTER` 🞂 `NAMESPACE`"
[SurrealQL035]:            <#q035---alter-sequence-statement> "SurrealQL 🞂 Statement 🞂 `ALTER` 🞂 `SEQUENCE`"
[SurrealQL036]:            <#q036---alter-system-statement> "SurrealQL 🞂 Statement 🞂 `ALTER` 🞂 `SYSTEM`"
[SurrealQL037]:            <#q037---alter-table-statement> "SurrealQL 🞂 Statement 🞂 `ALTER` 🞂 `TABLE`"
[SurrealQL038]:            <#q038---begin-statement> "SurrealQL 🞂 Statement 🞂 `BEGIN`"
[SurrealQL039]:            <#q039---break-statement> "SurrealQL 🞂 Statement 🞂 `BREAK`"
[SurrealQL040]:            <#q040---cancel-statement> "SurrealQL 🞂 Statement 🞂 `CANCEL`"
[SurrealQL041]:            <#q041---commit-statement> "SurrealQL 🞂 Statement 🞂 `COMMIT`"
[SurrealQL042]:            <#q042---continue-statement> "SurrealQL 🞂 Statement 🞂 `CONTINUE`"
[SurrealQL043]:            <#q043---create-statement> "SurrealQL 🞂 Statement 🞂 `CREATE`"
[SurrealQL044]:            <#q044---define-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE`"
[SurrealQL045]:            <#q045---define-access-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `ACCESS`"
[SurrealQL046]:            <#q046---define-access--type-bearer> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `ACCESS` 🞂 `TYPE BEARER`"
[SurrealQL047]:            <#q047---define-access--type-jwt> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `ACCESS` 🞂 `TYPE JWT`"
[SurrealQL048]:            <#q048---define-access--type-record> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `ACCESS` 🞂 `TYPE RECORD`"
[SurrealQL049]:            <#q049---define-analyzer-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `ANALYZER`"
[SurrealQL050]:            <#q050---define-api-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `API`"
[SurrealQL051]:            <#q051---define-bucket-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `BUCKET`"
[SurrealQL052]:            <#q052---define-config-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `CONFIG`"
[SurrealQL053]:            <#q053---define-database-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `DATABASE`"
[SurrealQL054]:            <#q054---define-event-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `EVENT`"
[SurrealQL055]:            <#q055---define-field-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `FIELD`"
[SurrealQL056]:            <#q056---define-function-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `FUNCTION`"
[SurrealQL057]:            <#q057---define-index-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `INDEX`"
[SurrealQL058]:            <#q058---define-module-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `MODULE`"
[SurrealQL059]:            <#q059---define-namespace-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `NAMESPACE`"
[SurrealQL060]:            <#q060---define-param-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `PARAM`"
[SurrealQL061]:            <#q061---define-scope-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `SCOPE`"
[SurrealQL062]:            <#q062---define-sequence-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `SEQUENCE`"
[SurrealQL063]:            <#q063---define-table-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `TABLE`"
[SurrealQL064]:            <#q064---define-token-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `TOKEN`"
[SurrealQL065]:            <#q065---define-user-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `USER`"
[SurrealQL066]:            <#q066---delete-statement> "SurrealQL 🞂 Statement 🞂 `DELETE`"
[SurrealQL067]:            <#q067---explain-statement> "SurrealQL 🞂 Statement 🞂 `EXPLAIN`"
[SurrealQL068]:            <#q068---for-statement> "SurrealQL 🞂 Statement 🞂 `FOR`"
[SurrealQL069]:            <#q069---if-else-statement> "SurrealQL 🞂 Statement 🞂 `IF ELSE`"
[SurrealQL070]:            <#q070---info-statement> "SurrealQL 🞂 Statement 🞂 `INFO`"
[SurrealQL071]:            <#q071---insert-statement> "SurrealQL 🞂 Statement 🞂 `INSERT`"
[SurrealQL072]:            <#q072---kill-statement> "SurrealQL 🞂 Statement 🞂 `KILL`"
[SurrealQL073]:            <#q073---let-statement> "SurrealQL 🞂 Statement 🞂 `LET`"
[SurrealQL074]:            <#q074---live-select-statement> "SurrealQL 🞂 Statement 🞂 `LIVE SELECT`"
[SurrealQL075]:            <#q075---rebuild-statement> "SurrealQL 🞂 Statement 🞂 `REBUILD`"
[SurrealQL076]:            <#q076---relate-statement> "SurrealQL 🞂 Statement 🞂 `RELATE`"
[SurrealQL077]:            <#q077---remove-statement> "SurrealQL 🞂 Statement 🞂 `REMOVE`"
[SurrealQL078]:            <#q078---return-statement> "SurrealQL 🞂 Statement 🞂 `RETURN`"
[SurrealQL079]:            <#q079---select-statement> "SurrealQL 🞂 Statement 🞂 `SELECT`"
[SurrealQL080]:            <#q080---show-statement> "SurrealQL 🞂 Statement 🞂 `SHOW`"
[SurrealQL081]:            <#q081---sleep-statement> "SurrealQL 🞂 Statement 🞂 `SLEEP`"
[SurrealQL082]:            <#q082---throw-statement> "SurrealQL 🞂 Statement 🞂 `THROW`"
[SurrealQL083]:            <#q083---update-statement> "SurrealQL 🞂 Statement 🞂 `UPDATE`"
[SurrealQL084]:            <#q084---upsert-statement> "SurrealQL 🞂 Statement 🞂 `UPSERT`"
[SurrealQL085]:            <#q085---use-statement> "SurrealQL 🞂 Statement 🞂 `USE`"
[SurrealQL086]:            <#q086---clauses> "SurrealQL 🞂 Clauses"
[SurrealQL087]:            <#q087---explain-clauses> "SurrealQL 🞂 Clauses 🞂 `EXPLAIN`"
[SurrealQL088]:            <#q088---fetch-clauses> "SurrealQL 🞂 Clauses 🞂 `FETCH`"
[SurrealQL089]:            <#q089---from-clauses> "SurrealQL 🞂 Clauses 🞂 `FROM`"
[SurrealQL090]:            <#q090---group-by-clauses> "SurrealQL 🞂 Clauses 🞂 `GROUP BY`"
[SurrealQL091]:            <#q091---limit-clauses> "SurrealQL 🞂 Clauses 🞂 `LIMIT`"
[SurrealQL092]:            <#q092---omit-clauses> "SurrealQL 🞂 Clauses 🞂 `OMIT`"
[SurrealQL093]:            <#q093---order-by-clauses> "SurrealQL 🞂 Clauses 🞂 `ORDER BY`"
[SurrealQL094]:            <#q094---split-clauses> "SurrealQL 🞂 Clauses 🞂 `SPLIT`"
[SurrealQL095]:            <#q095---where-clauses> "SurrealQL 🞂 Clauses 🞂 `WHERE`"
[SurrealQL096]:            <#q096---with-clauses> "SurrealQL 🞂 Clauses 🞂 `WITH`"
[SurrealQL097]:            <#q097---parameters> "SurrealQL 🞂 Parameters"
[SurrealQL098]:            <#q098---functions> "SurrealQL 🞂 Functions"
[SurrealQL099]:            <#q099---database-functions> "SurrealQL 🞂 Functions 🞂 Database Functions"
[SurrealQL100]:            <#q100---api-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 API functions"
[SurrealQL101]:            <#q101---array-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Array functions"
[SurrealQL101_add]:        <#q101aa---array--add> "`array::all()`"
[SurrealQL101_all]: <#q101ab---array--all> ""
[SurrealQL101_any]: <#q101ac---array--any> ""
[SurrealQL101_at]: <#q101ad---array--at> ""
[SurrealQL101_append]: <#q101ae---array--append> ""
[SurrealQL101_boolean_and]: <#q101af---array--boolean-and> ""
[SurrealQL101_boolean_or]: <#q101ag---array--boolean-or> ""
[SurrealQL101_boolean_xor]: <#q101ah---array--boolean-xor> ""
[SurrealQL101_boolean_not]: <#q101ai---array--boolean-not> ""
[SurrealQL101_combine]: <#q101aj---array--combine> ""
[SurrealQL101_complement]: <#q101ak---array--complement> ""
[SurrealQL101_clump]: <#q101al---array--clump> ""
[SurrealQL101_concat]: <#q101am---array--concat> ""
[SurrealQL101_difference]: <#q101an---array--difference> ""
[SurrealQL101_distinct]: <#q101ao---array--distinct> ""
[SurrealQL101_fill]: <#q101ap---array--fill> ""
[SurrealQL101_filter]: <#q101aq---array--filter> ""
[SurrealQL101_filter_index]: <#q101ar---array--filter-index> ""
[SurrealQL101_find]: <#q101as---array--find> ""
[SurrealQL101_find_index]: <#q101at---array--find-index> ""
[SurrealQL101_first]: <#q101au---array--first> ""
[SurrealQL101_flatten]: <#q101av---array--flatten> ""
[SurrealQL101_fold]: <#q101aw---array--fold> ""
[SurrealQL101_group]: <#q101ax---array--group> ""
[SurrealQL101_insert]: <#q101ay---array--insert> ""
[SurrealQL101_intersect]: <#q101az---array--intersect> ""
[SurrealQL101_is_empty]: <#q101ba---array--is-empty> ""
[SurrealQL101_join]: <#q101bb---array--join> ""
[SurrealQL101_last]: <#q101bc---array--last> ""
[SurrealQL101_len]: <#q101bd---array--len> ""
[SurrealQL101_logical_and]: <#q101be---array--logical-and> ""
[SurrealQL101_logical_or]: <#q101bf---array--logical-or> ""
[SurrealQL101_logical_xor]: <#q101bg---array--logical-xor> ""
[SurrealQL101_map]: <#q101bh---array--map> ""
[SurrealQL101_max]: <#q101bi---array--max> ""
[SurrealQL101_matches]: <#q101bj---array--matches> ""
[SurrealQL101_min]: <#q101bk---array--min> ""
[SurrealQL101_pop]: <#q101bl---array--pop> ""
[SurrealQL101_prepend]: <#q101bm---array--prepend> ""
[SurrealQL101_push]: <#q101bn---array--push> ""
[SurrealQL101_range]: <#q101bo---array--range> ""
[SurrealQL101_reduce]: <#q101bp---array--reduce> ""
[SurrealQL101_remove]: <#q101bq---array--remove> ""
[SurrealQL101_repeat]: <#q101br---array--repeat> ""
[SurrealQL101_reverse]: <#q101bs---array--reverse> ""
[SurrealQL101_sequence]: <#q101bt---array--sequence> ""
[SurrealQL101_shuffle]: <#q101bu---array--shuffle> ""
[SurrealQL101_slice]: <#q101bv---array--slice> ""
[SurrealQL101_sort]: <#q101bw---array--sort> ""
[SurrealQL101_sort_lexical]: <#q101bx---array--sort-lexical> ""
[SurrealQL101_sort_natural]: <#q101by---array--sort-natural> ""
[SurrealQL101_sort_natural_lexical]: <#q101bz---array--sort-natural-lexical> ""
[SurrealQL101_sort_asc]: <#q101ca---array--sort-asc> ""
[SurrealQL101_sort_desc]: <#q101cb---array--sort-desc> ""
[SurrealQL101_swap]: <#q101cc---array--swap> ""
[SurrealQL101_transpose]: <#q101cd---array--transpose> ""
[SurrealQL101_union]: <#q101ce---array--union> ""
[SurrealQL101_windows]: <#q101cf---array--windows> ""

[SurrealQL102]:            <#q102---bytes-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Bytes functions"
[SurrealQL103]:            <#q103---count-function> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Count function"
[SurrealQL104]:            <#q104---crypto-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Crypto functions"
[SurrealQL105]:            <#q105---duration-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Duration functions"
[SurrealQL106]:            <#q106---encoding-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Encoding functions"
[SurrealQL107]:            <#q107---file-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 File functions"
[SurrealQL108]:            <#q108---geo-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Geo functions"
[SurrealQL109]:            <#q109---http-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 HTTP functions"
[SurrealQL110]:            <#q110---math-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Math functions"
[SurrealQL111]:            <#q111---meta-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Meta functions"
[SurrealQL112]:            <#q112---not-function> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Not function"
[SurrealQL113]:            <#q113---object-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Object functions"
[SurrealQL114]:            <#q114---parse-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Parse functions"
[SurrealQL115]:            <#q115---rand-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Rand functions"
[SurrealQL116]:            <#q116---record-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Record functions"
[SurrealQL117]:            <#q117---search-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Search functions"
[SurrealQL118]:            <#q118---sequence-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Sequence functions"
[SurrealQL119]:            <#q119---session-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Session functions"
[SurrealQL120]:            <#q120---set-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Set functions"
[SurrealQL121]:            <#q121---sleep-function> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Sleep function"
[SurrealQL122]:            <#q122---string-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 String Functions"
[SurrealQL123]:            <#q123---time-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Time Functions"
[SurrealQL124]:            <#q124---type-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Type Functions"
[SurrealQL125]:            <#q125---value-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Value functions"
[SurrealQL126]:            <#q126---vector-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Vector functions"
[SurrealQL127]:            <#q127---embedded-scripting-functions> "SurrealQL 🞂 Functions 🞂 Embedded scripting functions"
[SurrealQL128]:            <#q128---arguments> "SurrealQL 🞂 Functions 🞂 Scripting Functions 🞂 Arguments"
[SurrealQL129]:            <#q129---built-in-functions> "SurrealQL 🞂 Functions 🞂 Scripting Functions 🞂 Built-in functions"
[SurrealQL130]:            <#q130---function-context> "SurrealQL 🞂 Functions 🞂 Scripting Functions 🞂 Function context"
[SurrealQL131]:            <#q131---type-conversion> "SurrealQL 🞂 Functions 🞂 Scripting Functions 🞂 Type conversion"
[SurrealQL132]:            <#q132---surrealql-functions> "SurrealQL 🞂 Functions 🞂 Scripting Functions 🞂 SurrealQL functions"
[SurrealQL133]:            <#q133---machine-learning-functions> "SurrealQL 🞂 Functions 🞂 Machine Learning functions"
[SurrealQL134]:            <#q134---machine-learning-functions> "SurrealQL 🞂 Functions 🞂 ML Functions 🞂 Machine Learning functions"
[SurrealQL135]:            <#q135---transactions> "SurrealQL 🞂 Transactions"
[SurrealQL136]:            <#q136---comments> "SurrealQL 🞂 Comments"



[net__SurrealDB_Store]:    <https://surrealdb.store/>
[net__SurrealistMini]:     <https://app.surrealdb.com/mini>
[net__RFC_7946]: <https://www.rfc-editor.org/rfc/rfc7946>
[net__RFC_3339]: <https://datatracker.ietf.org/doc/html/rfc3339>
[net__wiki_float64]: <https://en.wikipedia.org/wiki/Double-precision_floating-point_format>
[net__wiki_decimal128]: <https://en.wikipedia.org/wiki/Decimal128_floating-point_format>
[net__geojson]: <https://geojson.org/>

[getSURQL_001]: <https://datasets.surrealdb.com/surreal-deal-store.surql>
[getSURQL_002]: <https://datasets.surrealdb.com/surreal-deal-store-mini.surql>

[trySURQL_001]: <https://app.surrealdb.com/mini?query=--+Query+1%3A+Using+record+links+to+select+from+the+seller+table+%0ASELECT%0A++name%2C%0A++seller.name%0AFROM+product+LIMIT+4%3B%0A%0A%0A--+Query+2%3A+Using+graph+relations+to+select+from+the+person+and+product+table%0ASELECT%0A++++time.created_at as order_date%2C%0A++++product_name%2C%0A++++%3C-person.name+as+person_name%2C%0A++++-%3Eproduct.details%0AFROM+order+LIMIT+4%3B%0A%0A%0A--+Query+3%3A+Conditional+filtering+based+on+an+embedded+object+property.%0ASELECT+%0A++name%2C%0A++email+%0AFROM+person+%0AWHERE+address.country+%3F%3D+%22England%22+LIMIT+4%3B%09%0A%0A%0A--+Query+4%3A+Conditional+filtering+using+relationships.%0ASELECT+*+FROM+review%0AWHERE+-%3Eproduct.sub_category+%3F%3D+%22Activewear%22+LIMIT+4%3B%0A%0A%0A--+Query+5%3A+Count+orders+based+on+order+status%0ASELECT+count%28%29+FROM+order%0AWHERE+order_status+IN+%5B+%22processed%22%2C+%22shipped%22%5D%0AGROUP+ALL+LIMIT+4%3B%0A%0A%0A--+Query+6%3A+Get+a+deduplicated+list+of+products+that+were+ordered%0ASELECT+%0A++++array%3A%3Adistinct%28product_name%29+as+ordered_products%0AFROM+order%0AGROUP+ALL+LIMIT+4%3B%0A%0A%0A--+Query+7%3A+Get+the+average+price+per+product+category%0ASELECT+%0A++++-%3Eproduct.category+AS+product_category%2C%0A++++math%3A%3Amean%28price%29+AS+avg_price%0AFROM+order%0AGROUP+BY+product_category%0AORDER+BY+avg_price+DESC+LIMIT+4%3B%0A%0A%0A--+Query+8%3A+encapsulating+logic+in+a+function%0ARETURN+fn%3A%3Anumber_of_unfulfilled_orders%28%29%3B%0A%0A%0A--+Query+9%3A+using+a+custom+fuction+for+currency+conversion%0ASELECT+%0A++++product_name%2C%0A++++fn%3A%3Apound_to_usd%28price%29+AS+price_usd%0AFROM+order+LIMIT+4%3B&dataset=surreal-deal-store&orientation=horizontal> "SurrealistMini"

[yt01]:              <https://www.youtube.com/watch?v=TyX45cyZ-W0> "SurrealDB: Document-Style Relationships in SurrealDB"
[icon_YT]:           <https://upload.wikimedia.org/wikipedia/commons/thumb/2/20/YouTube_2024.svg/300px-YouTube_2024.svg.webp>
[icon_SurrealQL]:    <https://surrealdb.com/docs/_astro/ql-light.70PDiXa1_Z2othTk.webp>
[img_demo_overview]: <https://surrealdb.com/docs/_astro/surreal-deal-store.C2015pX2_Z2r7lvb.webp>

[SurrealDB_cli]:           </docs/surrealdb/cli> "CLI"
[SurrealDB_cli_import]:    </docs/surrealdb/cli/import> "import"
[SurrealDB_cli_start]:     </docs/surrealdb/cli/start>


---
