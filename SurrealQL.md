# _q000 - **SurrealQL**_

- [📓][surrealdb_docs_3x_surrealql]

![SurrealQL🖼️][ico__SurrealQL]

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

To start using [SurrealQL][SurrealQL038_Statement_BEGIN], refer to the documentation on the various statement types and their syntax. The statements page provides comprehensive examples and explanations for each statement type, helping you understand how to construct queries and interact with SurrealDB effectively.

SurrealQL empowers you to leverage the full potential of SurrealDB and enables you to build robust and scalable applications. Let's dive into the world of SurrealQL and unlock the capabilities of SurrealDB together!

[**go to YouTube**▶️][yt01]

---
---

## _q001 - **Demo data**_

- [📓][surrealdb_docs_3x_surrealql_demo]

To quickly test out SurrealDB and SurrealQL functionality, we've included two demo datasets here in `.surql` files which you can download and [`import`🚫][SurrealDB_cli_import] into SurrealDB using the [CLI🚫][SurrealDB_cli].

### _q001a - **Surreal Deal Store - there is a lot in store for you!**_

Surreal Deal Store is our new and improved demo dataset based on our [SurrealDB Store🚀][net__SurrealDB_Store].
The dataset is made up of 12 tables using both [graph relations][SurrealQL076_Statement_RELATE] and [record links][SurrealQL021_DataTypes_RecordLinks].

In the diagram below, the nodes in pink are the [standard tables][SurrealQL063_Statement_DEFINE_TABLE], the ones in purple represent the [edge tables][SurrealQL076_Statement_RELATE] which shows relationships between records and SurrealDB as a graph database. The nodes in grey are the [pre-computed table views][SurrealQL063_Statement_DEFINE_TABLE].

![Surreal Deal Data Mode🖼️][img__demo_overview]

#### _q001a1 - **Download**_

| Dataset | URL |
| --- | --- |
| [Surreal Deal Store💾][getSURQL_001] | [https://datasets.surrealdb.com/surreal-deal-store.surql][getSURQL_001] |
| [Surreal Deal Store (mini)💾][getSURQL_002] | [https://datasets.surrealdb.com/surreal-deal-store-mini.surql][getSURQL_002] |

#### _q001a2 - **Import**_

Once one of the datasets has been downloaded, it's now time to [start the server🚫][SurrealDB_cli_start].

```bash
# Create a new in-memory server
surreal start --user root --pass secret --allow-all
```

Lastly, use the [import command🚫][SurrealDB_cli_import] to add the dataset.

Use the command below to import the [surreal deal store dataset💾][getSURQL_001]:

```bash
surreal import --conn http://localhost:8000 --user root --pass secret --ns main --db main surreal-deal-store.surql
```

To import the surreal downloaded the [Surreal Deal store (mini)💾][getSURQL_002] use the command below:

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

Here are some sample queries you can run on the Surreal Deal Store dataset. We've also included a [App Surrealist Mini🚀][net__SurrealistMini] below to help you run these queries.

> [!NOTE]
> The query results below have been limited to 4 rows for brevity. If you remove the `LIMIT 4` clause from the queries, you'll see the full results.

[Try in App Surrealist Mini][trySURQL_001]

---
---

## _q002 - **Operators**_

- [📓][surrealdb_docs_3x_surrealql_operators]

A variety of operators in SurrealQL allow for complex manipulation of data, and advanced logic.

| Operator | Description |
| :--- | :--- |
| [`&&`][SurrealQL002aa_OperatorAND] [`AND`][SurrealQL002aa_OperatorAND] | Checks whether both of two values are truthy |
| [`\|\|`][SurrealQL002ab_OperatorOR] [`OR`][SurrealQL002ab_OperatorOR] | Checks whether either of two values is truthy |
| [`!`][SurrealQL002ac_OperatorNOT] | Reverses the truthiness of a value |
| [`!!`][SurrealQL002ad_OperatorNotNOT] | Determines the truthiness of a value |
| [`??`][SurrealQL002ae_OperatorCoalescingNULL] | Check whether either of two values are truthy and not NULL |
| [`?:`][SurrealQL002af_OperatorCoalescingTRUTHY] | Check whether either of two values are truthy |
| [`=`][SurrealQL002ag_OperatorEQUAL] [`IS`][SurrealQL002ag_OperatorEQUAL] | Check whether two values are equal |
| [`!=`][SurrealQL002ah_OperatorNOTEQUAL] [`IS NOT`][SurrealQL002ah_OperatorNOTEQUAL] | Check whether two values are not equal |
| [`==`][SurrealQL002ai_OperatorEXACT] | Check whether two values are exactly equal |
| [`?=`][SurrealQL002ai_OperatorANYEQUAL] | Check whether any value in a set is equal to a value |
| [`*=`][SurrealQL002ak_OperatorALLEQUAL] | Check whether all values in a set are equal to a value |
| [`~`][SurrealQL002al_OperatorSIMILARITY] | Compare two values for equality using fuzzy matching |
| [`!~`][SurrealQL002al_OperatorSIMILARITY] | Compare two values for inequality using fuzzy matching |
| [`?~`][SurrealQL002al_OperatorSIMILARITY] | Check whether any value in a set is equal to a value using fuzzy matching |
| [`*~`][SurrealQL002al_OperatorSIMILARITY] | Check whether all values in a set are equal to a value using fuzzy matching |
| [`<`][SurrealQL002am_OperatorLESS] | Check whether a value is less than another value |
| [`<=`][SurrealQL002an_OperatorLESSEQUAL] | Check whether a value is less than or equal to another value |
| [`>`][SurrealQL002ao_OperatorMORE] | Check whether a value is greater than another value |
| [`>=`][SurrealQL002ap_OperatorMOREEQUAL] | Check whether a value is greater than or equal to another value |
| [`+`][SurrealQL002aq_OperatorADD] | Add two values together |
| [`-`][SurrealQL002ar_OperatorSUB] | Subtract a value from another value |
| [`*`][SurrealQL002as_OperatorMUL] [`×`][SurrealQL002as_OperatorMUL] | Multiply two values together |
| [`/`][SurrealQL002at_OperatorDIV] [`÷`][SurrealQL002at_OperatorDIV] | Divide a value by another value |
| [`**`][SurrealQL002au_OperatorPOW] | Raises a base value by another value |
| [`CONTAINS`][SurrealQL002av_OperatorCoEQU] [`∋`][SurrealQL002av_OperatorCoEQU] | Checks whether a value contains another value |
| [`CONTAINSNOT`][SurrealQL002aw_OperatorCoNOT] [`∌`][SurrealQL002aw_OperatorCoNOT] | Checks whether a value does not contain another value |
| [`CONTAINSALL`][SurrealQL002ax_OperatorCoALL] [`⊇`][SurrealQL002ax_OperatorCoALL] | Checks whether a value contains all other values |
| [`CONTAINSANY`][SurrealQL002ay_OperatorCoANY] [`⊃`][SurrealQL002ay_OperatorCoANY] | Checks whether a value contains any other value |
| [`CONTAINSNONE`][SurrealQL002az_OperatorCoNON] [`⊅`][SurrealQL002az_OperatorCoNON] | Checks whether a value contains none of the following values |
| [`INSIDE`][SurrealQL002ba_OperatorInEQU] [`IN`][SurrealQL002ba_OperatorInEQU] [`∈`][SurrealQL002ba_OperatorInEQU] | Checks whether a value is contained within another value |
| [`NOTINSIDE`][SurrealQL002bb_OperatorInNOT] [`NOT IN`][SurrealQL002bb_OperatorInNOT] [`∉`][SurrealQL002bb_OperatorInNOT] | Checks whether a value is not contained within another value |
| [`ALLINSIDE`][SurrealQL002bc_OperatorInALL] [`⊆`][SurrealQL002bc_OperatorInALL] | Checks whether all values are contained within other values |
| [`ANYINSIDE`][SurrealQL002bd_OperatorInANY] [`⊂`][SurrealQL002bd_OperatorInANY] | Checks whether any value is contained within other values |
| [`NONEINSIDE`][SurrealQL002be_OperatorInNON] [`⊄`][SurrealQL002be_OperatorInNON] | Checks whether no value is contained within other values |
| [`OUTSIDE`][SurrealQL002bf_OperatorOUTSIDE] | Checks whether a geometry type is outside of another geometry type |
| [`INTERSECTS`][SurrealQL002bg_OperatorINTERSECTS] | Checks whether a geometry type intersects another geometry type |
| [`@@`][SurrealQL002bh_OperatorMATCHES] [`@[ref]@`][SurrealQL002bh_OperatorMATCHES] | Checks whether the terms are found in a full-text indexed field |
| [`<\|4\|>`][SurrealQL002bi_OperatorKNN] [`<\|3,HAMMING\| >`][SurrealQL002bi_OperatorKNN] | Performs a K-Nearest Neighbors (KNN) search to find a specified number of records closest to a given data point, optionally using a defined distance metric. Supports customizing the number of results and choice of distance calculation method. |

### _q002aa - **`&&` or `AND`**_

The `and` operator checks whether both of two values are [truthy][SurrealQL027_DataTypes_Values].

```surql
/**[test]

[[test.results]]
value = "30"

*/

SELECT * FROM 10 AND 20 AND 30;

-- 30
```

### _q002ab - **`||` or `OR`**_

The `or` operator checks whether either of two values are [truthy][SurrealQL027_DataTypes_Values].

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

The `null coalescing operator` checks whether either of two values are [truthy][SurrealQL027_DataTypes_Values] and not `NONE` or `NULL`.

```surql
/**[test]

[[test.results]]
value = "[0]"

*/

SELECT * FROM NULL ?? 0 ?? false ?? 10;

-- 0
```

### _q002af - **`?:` (truthy coalescing)**_

The `truthy coalescing operator` checks whether either of two values are [truthy][SurrealQL027_DataTypes_Values].

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

This operator can also be used to check for the existence of a key inside an [object][SurrealQL018_DataTypes_Objects]. To do so, precede `IN` with the field name as a string.

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
| `Cast` | The `Cast` operator is `<type_name>`, with `type_name` a stand in for the type to cast into. For example, `<string>` or `<number>`. |
| `Power` | The only `Power` operator is `**`. |
| `MulDiv` | The `MulDiv` (multiplication and division) operators are `*`, `/`, `÷`, and `%`. |
| `AddSub` | The `AddSub` (addition and subtraction) operators are `+` and `-`. |
| `Relation` | The `Relation` operators are `<=`, `>=`, `∋`, `CONTAINS`, `∌`, `CONTAINSNOT`, `∈`, `INSIDE`, `∉`, `NOTINSIDE`, `⊇`, `CONTAINSALL`, `⊃`, `CONTAINSANY`, `⊅`, `CONTAINSNONE`, `⊆`, `ALLINSIDE`, `⊂`, `ANYINSIDE`, `⊄`, `NONEINSIDE`, `OUTSIDE`, `INTERSECTS`, `NOT`, and `IN`. |
| `Equality` | The `Equality` operators are `=`, `IS`, `==`, `!=`, `*=`, `?=`, and `@`. |
| `And` | The `And` operators are `&&` and `AND`. |
| `Or` | The `Or` operators are `\|\|` and `OR`. |

### _q002bl - **Examples of binding power**_

The following samples show examples of basic operations of varying binding power. The original example is followed by the same example with the parts with higher binding power in parentheses, then the final expression after the first bound portion is calculated, and finally the output.

#### **MulDiv first, then AddSub**

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

#### **Power first, then MulDiv**

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

#### **Unary first, then cast**

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

#### **Cast first, then Power**

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

#### **AddSub first, then Relation**

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

#### **And first, then Or**

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

#### **Unary, then Cast, then Power, then AddSub**

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

- [📓][surrealdb_docs_3x_surrealql_datamodel]

SurrealQL allows you to describe data with specific data types. These data types are used to validate data and to generate the appropriate database schema.

| Type | Description |
| :--- | :--- |
| `option` | Makes types optional and guarantees the field to be either empty (NONE) or some other type.  `option<number>` |
| `any` | Use this when you explicitly don't want to specify the field's data type. The field will allow any data type supported by SurrealDB. |
| `bool` | Describes whether something is truthy or not. |
| `string` | Describes a text-like value. |
| `regex` | A compiled regular expression that can be used for matching strings. |
| | |
| `int` | Store a value in a 64 bit signed integer. Values can range between `-9223372036854775808` and `9223372036854775807` (inclusive). Larger values should be stored as a float or a decimal. |
| `decimal` | Data type for storing [decimal floating point🚀][net__wiki_decimal128] numbers. |
| `float` | Data type for storing [floating point🚀][net__wiki_float64] numbers. Larger or extremely precise values should be stored as a decimal. |
| `number` | Store numbers without specifying the type. SurrealDB will detect the type of number and store it using the minimal number of bytes. |
| | |
| `datetime` | An [RFC 3339🚀][net__RFC_3339] compliant data type that stores a date with time and time zone. |
| `duration` | Store a value representing a length of time. Can be added or subtracted from datetimes or other durations. |
| | |
| `range` | A range of possible values. Lower and upper bounds can be set, in the absence of which the range becomes open-ended. A range of integers can be used in a FOR loop.  `0..10`, `0..=10`, `..10`, `‘a’..‘z’` |
| `object` | Store formatted objects containing values of any supported type including nested objects or arrays. |
| [`literal`][SurrealQL015_DataTypes_Literals] | A value that may have multiple representations or formats, similar to an enum or a union type. Can be composed of strings, numbers, objects, arrays, or durations.  `”a” \| “b”`, `[number, “abc”]`, `123 \| 456 \| string \| 1y1m1d` |
| `set` | A set of items. The set type also allows you to define which types can be stored in the set and the required length. Items are automatically deduplicated and orderd. `set`, `set<string>`, `set<string, 10>` |
| `array` | An array of items. The array type also allows you to define which types can be stored in the array and the required length.  `array`, `array<string>`, `array<string, 10>` |
| [`geometry`][SurrealQL003_geometry] | [RFC 7946🚀][net__RFC_7946] compliant data type for storing geometry in the [GeoJson format🚀][net__geojson].  `geometry<feature>`, `geometry<point>`, `geometry<line>`, `geometry<polygon>`, `geometry<multipoint>`, `geometry<multiline>`, `geometry<multipolygon>`, `geometry<collection>` |
| [`bytes`][SurrealQL003_bytes] | Stores a value in a byte array. `<bytes>value`, `bytes` |
| | |
| `record` | Store a reference to another record. The value must be a Record ID. Add the record name inside angle brackets to restrict the reference to only certain record names.  `record`,`record<user>`,`record<user \| administrator>` |

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

- [📓][surrealdb_docs_3x_surrealql_datamodel_arrays]

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

Working with arrays is one of the most important skills when working with SurrealDB, as [`SELECT`][SurrealQL079_Statement_SELECT] statements return an array of values by default unless the `ONLY` keyword is used on an array that contains a single item.

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

If a `WHERE` or `?` clause finds an item that by itself is not equal to `true` or `false`, it will check the item's [truthiness][SurrealQL027_DataTypes_Values] to determine whether to pass it on or not.

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

While the [array functions][SurrealQL101_FunctionsDatabase_Array] section of the documentation contains the full details of each function, the following examples provide a glimpse into how they are commonly used.

The [`array::map()`][SurrealQL101bh_FunctionsDatabase_Array_map] function provides access to each item in an array, allowing an opearation to be performed on it before being passed on.

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

- [📓][surrealdb_docs_3x_surrealql_datamodel_booleans]

Boolean values can be used to mark whether a field is `true` or `false`.

```surql
CREATE person SET newsletter = false, interested = true;
```

Many SurrealDB operators and functions return booleans.

```surql
/**[test]

[[test.results]]
value = "[{ id: person:jhn1rlhusqypyyyy0gjg, name: 'Billy', name_is_billy: true, name_is_long: false }]"
skip-record-id-key = true

*/


CREATE person SET 
  name = "Billy", 
  name_is_billy = name = "Billy",
  name_is_long = string::len(name) > 10;
```

```surql title="Response"
[
  {
    id: person:7j4t4higwb141v1v2xum,
    name: 'Billy',
    name_is_billy: true,
    name_is_long: false
  }
]
```

Boolean values can be written in anycase.

```surql
/**[test]

[[test.results]]
value = "[{ id: person:1vyseg5ig08xn1ie3h43, interested: true, newsletter: false, very_interested: true }]"
skip-record-id-key = true

*/

CREATE person SET 
    newsletter = FALSE,
    interested = True,
    very_interested = trUE;
```

### _q005a - **Booleans in `WHERE` clauses**_

When performing a query on the database, accessing a record's ID directly or using a [record range][SurrealQL020c_DataTypes_RecordIDs_Ranges] allows performance to be significantly sped up by avoiding the table scan which is used when a `WHERE` clause is included.

However, if a `WHERE` clause is unavoidable, performance can still be improved by simplifying the portion after the clause as much as possible. As a boolean is the simplest possible datatype, having a boolean field that can be used in a `WHERE` clause can significantly improve performance compared to a more complex operation.

```surql
/**[test]

[[test.results]]
value = "[]"

[[test.results]]
value = "[]"

[[test.results]]
value = "[{ data_length: 3, id: person:one, is_short: true, random_data: 'HI!' }]"

[[test.results]]
value = "[{ data_length: 3, id: person:one, is_short: true, random_data: 'HI!' }]"

[[test.results]]
value = "[{ data_length: 3, id: person:one, is_short: true, random_data: 'HI!' }]"

[[test.results]]
value = "[{ data_length: 3, id: person:one, is_short: true, random_data: 'HI!' }]"

*/

DEFINE FIELD data_length ON person VALUE random_data.len();
DEFINE FIELD is_short ON person VALUE random_data.len() < 10;

-- Fill up the database a bit with 10,000 records
CREATE |person:10000| SET random_data = rand::string(1000) RETURN NONE;
-- Add one outlier with short random_data
CREATE person:one SET random_data = "HI!" RETURN NONE;

-- Function call + compare operation: slowest
SELECT * FROM person WHERE random_data.len() < 10;
-- Compare operation: much faster
SELECT * FROM person WHERE data_length < 10;
-- Boolean check: even faster
SELECT * FROM person WHERE is_short;
-- Direct record access: almost instantaneous
SELECT * FROM person:one;
```

---
---

## _q006 - **Bytes**_

- [📓][surrealdb_docs_3x_surrealql_datamodel_bytes]

Bytes can be created by casting from a string, and are displayed using hexidecimal encoding.

```surql
/**[test]

[[test.results]]
value = "b"4920616D20736F6D65206279746573""

*/

<bytes>"I am some bytes";
```

```surql title="Output"
b"4920616D20736F6D65206279746573"
```

### _q006a - **Conversion from other types**_

> Available since: V2.3.0

Since SurrealDB 2.3.0, conversions can be performed between bytes, strings, and arrays.

```surql
/**[test]

[[test.results]]
value = "'cellar door'"

[[test.results]]
value = "[72, 111, 98, 98, 105, 116, 115]""

*/

-- array<int> to bytes to string
<string><bytes>[ 99, 101, 108, 108, 97, 114, 32, 100, 111, 111, 114 ];
-- string to bytes to array<int>
<array><bytes>"Hobbits";
```

```surql title="Output"
-------- Query --------

'cellar door'

-------- Query --------

[ 72, 111, 98, 98, 105, 116, 115 ]
```

### _q006b - **Byte strings**_

> Available since: V3.0.0

A string preceded by a `b` prefix can be turned into bytes as long as the string represents a hexidecimal value.

```surql
b"486F6262697473";

<string>b"486F6262697473";

<string>b"This won't work though";
```

```surql title="Output"
-------- Query --------

b"486F6262697473";

-------- Query --------

'Hobbits'

-------- Query --------

"There was a problem with the database: Parse error: Unexpected character `T` expected hexidecimal digit
--> [1:11]
  |
1 | <string>b\"This won't work though\";
  |           ^ 
"
```

---
---

## _q007 - **Casting**_

- [📓][surrealdb_docs_3x_surrealql_datamodel_casting]

In the SurrealDB type system, values can be converted to other values efficiently. This is useful if input is specified in a query which must be of a certain type, or if a user may have provided a parameter with an incorrect type.

| Type | Description |
| :--- | :--- |
| [`<bool>`][SurrealQL007c_DataTypes_Casting_bool] | Casts the subsequent value into a boolean |
| [`<string>`][SurrealQL007m_DataTypes_Casting_string] | Casts the subsequent value into a string |
| [`<regex>`][SurrealQL007n_DataTypes_Casting_regex] | Casts the subsequent value into a regular expression |
| [`<uuid>`][SurrealQL007o_DataTypes_Casting_uuid] | Casts the subsequent value into a UUID |
| | |
| [`<int>`][SurrealQL007h_DataTypes_Casting_int] | Casts the subsequent value into an int |
| [`<decimal>`][SurrealQL007e_DataTypes_Casting_decimal] | Casts the subsequent value into a decimal |
| [`<float>`][SurrealQL007g_DataTypes_Casting_float] | Casts the subsequent value into a float |
| [`<number>`][SurrealQL007i_DataTypes_Casting_number] | Casts the subsequent value into a decimal |
| | |
| [`<datetime>`][SurrealQL007d_DataTypes_Casting_datetime] | Casts the subsequent value into a datetime |
| [`<duration>`][SurrealQL007f_DataTypes_Casting_duration] | Casts the subsequent value into a duration |
| | |
| [`<set>`][SurrealQL007l_DataTypes_Casting_set_setT] | Casts the subsequent value into a set |
| [`<array>`][SurrealQL007a_DataTypes_Casting_array] | Casts the subsequent value into an array |
| [`<array<T>>`][SurrealQL007b_DataTypes_Casting_arrayT] | Casts the subsequent value into an array of `T` (some indicated type) |
| | |
| [`<record>`][SurrealQL007j_DataTypes_Casting_record] | Casts the subsequent value into a record |
| [`<record<T>>`][SurrealQL007k_DataTypes_Casting_recordT] | Casts the subsequent value into a record of `T` (some indicated type) |

### _q007a - **`<array>`**_

The `<array>` casting function converts a range into an array.

```surql
/**[test]

[[test.results]]
value = "[1, 2, 3]"

*/

<array>1..=3;
-- Output:
[1, 2, 3]
```

### _q007b - **`<array<T>>`**_

The `<array<T>>` casting function converts a value into an array of the specified type.

>[!NOTE]
>When using this casting function, the value must be an array and each element in the array will be cast to the specified type.

```surql
/**[test]

[[test.results]]
value = "[42, 314, 271, 137, 141]"

*/

<array<int>>["42", "314", "271", "137", "141"];
-- Output:
[42, 314, 271, 137, 141]
```

```surql
/**[test]

[[test.results]]
value = "['42', '314', '271', '137', '141']"

*/

<array<string>> [42, 314, 271, 137, 141];
-- Output:
['42', '314', '271', '137', '141']
```

A cast into an array of more than one possible type can also be used. In this case, the cast will attempt to cast into the possible types in order. As such, the `string` in the first query below will be cast into a `datetime` but not in the second.

```surql
/**[test]

[[test.results]]
value = "[[d'2020-09-09T00:00:00Z', '21 Jan 2020'], ['2020-09-09', '21 Jan 2020']]"

*/

[
  <array<datetime|string>>["2020-09-09", "21 Jan 2020"],
  <array<string|datetime>>["2020-09-09", "21 Jan 2020"]
];
```

```surql title="Output"
[
  [
    d'2020-09-09T00:00:00Z',
    '21 Jan 2020'
  ],
  [
    '2020-09-09',
    '21 Jan 2020'
  ]
]
```

An example of even more complex casting which attempts to cast each item in the input array into a `record<user>`, then `record<person>`, then `array<record<user>>`, and finally `string`.

```surql
/**[test]

[[test.results]]
value = "['person:one', 'user:two', "['user:three', 'user:four']", 'not_a_person_or_user']"

*/

<array<record<user | person> | array<record<user>> | string>> [
  'person:one',
  'user:two',
  [
    'user:three',
    'user:four'
  ],
  'not_a_person_or_user'
];
```

```surql title="Output"
[
  person:one,
  user:two,
  [
    user:three,
    user:four
  ],
  'not_a_person_or_user'
]
```

### _q007c - **`<bool>`**_

The `<bool` casting function converts a value into a boolean.

```surql
/**[test]

[[test.results]]
value = "true"

*/

<bool>"true";
-- Output:
true
```

```surql
/**[test]

[[test.results]]
value = "false"

*/

<bool>"false";
-- Output:
false
```

### _q007d - **`<datetime>`**_

The `<datetime>` casting function converts a value into a datetime.

```surql
/**[test]

[[test.results]]
value = "d'2025-06-07T00:00:00Z'"

*/

<datetime>"2025-06-07";
-- Output:
d'2025-06-07T00:00:00Z'
```

### _q007e - **`<decimal>`**_

The `<decimal>` casting function converts a value into a decimal which allows for 128 bits of precision.

```surql
<decimal>"13.5729484672938472938410938456";
-- Output:
13.572948467293847293841093846dec
```

Decimal casting should generally not be used to convert from floats with a large number of digits after the decimal point, because the input to the right will first be turned into a less precise float before the cast is performed.

```surql
<decimal>13.572948467293847293841093845679289;
-- Output:
13.57294846729385dec

<decimal>1.193847193847193847193487E11;
-- Output:
119384719384.7194dec
```

In this case, the `dec` suffix is preferable as it will instruct the database to treat the **input** as a decimal, rather than create a float to then cast into a decimal.

```surql
13.572948467293847293841093845679289dec;
-- Output:
13.572948467293847293841093846dec

1.193847193847193847193487E11dec;
-- Output:
1.193847193847193847193487E11dec;
```

### _q007f - **`<duration>`**_

The `<duration>` casting function converts a value into a duration.

```surql
/**[test]

[[test.results]]
value = "1h30m"

*/

<duration>"1h30m";
-- Output:
1h30m
```

### _q007g - **`<float>`**_

The `<float>` casting function converts a value into a floating point number. Floating point numbers by nature have a limited amount of precision.

```surql
/**[test]

[[test.results]]
value = "13.572948467293847f"

*/

<float>13.572948467293847293841093845679289;
-- Output:
13.572948467293847f
```

```surql
/**[test]

[[test.results]]
value = "13.572948467293847f"

*/

<float>"13.572948467293847293841093845679289";
-- Output:
13.572948467293847
```

### _q007h - **`<int>`**_

The `<int>` casting function converts a value into an integer.

```surql
/**[test]

[[test.results]]
value = "53"

*/

<int>53;
-- Output:
53
```

### _q007i - **`<number>`**_

The `<number>` casting function converts a value into a `number`.

```surql
<number>13.572948467293847293841093845679289;
-- Output:
"13.572948467293847293841093845679289"
```

```surql
<number>"13.572948467293847293841093845679289";
-- Output:
"13.572948467293847293841093845679289"
```

```surql
<number>1.193847193847193847193487E11;
-- Output:
"119384719384.7193847193487"
```

### _q007j - **`<record>`**_

The `<record>` casting function converts a value into a record.

Keep in mind when using this casting function that if the equivalent record id does not exist, it will not return anything.

```surql
SELECT id FROM <record>"person:hrebrffwm4sr2yifglta";
```

```surql title="Output"
{ id: person:hrebrffwm4sr2yifglta }
```

### _q007k - **`<record<T>>`**_

The `<record<T>>` casting function converts a value into a record.

Keep in mind when using this casting function that if the equivalent record id does not exist, it will not return anything.

```surql
SELECT id FROM <record>"person:hrebrffwm4sr2yifglta";
-- Output:
{ id: person:hrebrffwm4sr2yifglta }
```

A cast into a number of possible record types can also be used.

```surql
/**[test]

[[test.results]]
value = "[user:one, [person:one, user:two]]"

*/

[
  <record<user|person>>"user:one",
  <array<record<user|person>>>["person:one", "user:two"]
];
```

```surql title="Output"
[
  user:one,
  [
    person:one,
    user:two
  ]
]
```

### _q007l - **`<set>` and `<set<T>>`**_

The `<set>` casting function converts a value into a set.

```surql
/**[test]

[[test.results]]
value = "[{'21 Jan 2020', d'2020-09-09T00:00:00Z'}, {'2020-09-09', '21 Jan 2020'}]"

*/

[
  <set<datetime|string>>["2020-09-09", "21 Jan 2020"],
  <set<string|datetime>>["2020-09-09", "21 Jan 2020"]
];
```

```surql title="Output"
[
  [
    d'2020-09-09T00:00:00Z',
    '21 Jan 2020'
  ],
  [
    '2020-09-09',
    '21 Jan 2020'
  ]
]
```

### _q007m - **`<string>`**_

The `<string>` casting function converts a value into a string.

```surql
/**[test]

[[test.results]]
value = "'true'"

*/

<string>true;
-- Output:
'true'
```

```surql
/**[test]

[[test.results]]
value = "'1.3463f'"

*/

<string>1.3463;
-- Output:
'1.3463f'
```

```surql
/**[test]

[[test.results]]
value = "'false'"

*/

<string>false;
-- Output:
"false"
```

### _q007n - **`<regex>`**_

The `<regex>` casting function converts a value into a regular expression.

```surql
/**[test]

[[test.results]]
value = "true"

*/

<regex> "a|b" = "a";
-- Output:
true
```

```surql
/**[test]

[[test.results]]
value = "false"

*/

<regex> "a|b" = "c";
-- Output:
false
```

### _q007o - **`<uuid>`**_

The `<uuid>` casting function converts a value into a UUID.

```surql
SELECT id FROM <uuid> "a8f30d8b-db67-47ec-8b38-ef703e05ad1b";
-- Output:
[ u'a8f30d8b-db67-47ec-8b38-ef703e05ad1b' ]
```

### _q007p - **General notes on casting**_

#### _q007p1 - **Syntax and order**_

As the parser ignores spaces and new lines, casting syntax can include spaces or new lines as desired.

```surql
/**[test]

[[test.results]]
value = "['9.1', true, '15h']"

[[test.results]]
value = "['9.1', true, '15h']"

*/

-- Surrealist formatted syntax
 <array<bool | string | float>> [
  '9.1',
  'true',
  15h
];

-- Maybe someone's preferred syntax?
<array
        <bool | string | float>
      >
[ '9.1', 'true', 15h ];
```

When more than one cast type is specified, SurrealDB will attempt to convert into the type in the order specified. In the example above, while the input `'9.1'` could have been converted to a float, the type `string` comes first in the cast syntax and thus `'9.1'` remains as a string.

```surql title="Output"
[
  '9.1',
  true,
  '15h'
]
```

#### _q007p2 - **Casting vs. affixes**_

SurrealDB uses a number of affixes to force the parser to treat an input as a certain type instead of another. These affixes may seem at first glance to be identical to casts, as the following queries show.

```surql
/**[test]

[[test.results]]
value = "person:one"

[[test.results]]
value = "person:one"

[[test.results]]
value = "person:one"

[[test.results]]
value = "'person:one'"

[[test.results]]
value = "98dec"

[[test.results]]
value = "98dec"

[[test.results]]
value = "98"

*/

-- All return a record person:one
r"person:one";
<record>"person:one";
<record<person>>"person:one";
-- Returns a string 'person:one'
'person:one';

-- Both return a decimal 98dec
98dec;
<decimal>98;

-- Returns an int 98
98;
```

However, casts and affixes work in different ways:

- A cast is a way to convert from one type into another.
- An affix is an instruction to the parser to treat an input as a certain type.

These differences become clear when working with input that is less than ideal or does not work with a certain type. For example, floats by nature become imprecise after a certain number of digits.

```surql
/**[test]

[[test.results]]
value = "[8.888f, 8.88888888888889f]"

*/

[
  8.888,
  8.8888888888888888
];
```

```surql title="Output"
[
  8.888f,
  8.88888888888889f
]
```

In this case, a `decimal` can be used which will allow a greater number of digits after the decimal point. However, casting the above numbers into a `decimal` will result in the same inaccurate output.

```surql
/**[test]

[[test.results]]
value = "[8.888dec, 8.88888888888889dec]"

*/

[
  <decimal>8.888,
  <decimal>8.888888888888888
];
```

```surql title="Output"
[
  8.888dec,
  8.88888888888889dec
]
```

This is because the parser will first treat the number as a float and then cast it into a `decimal`.

However, using the `dec` suffix will inform the parser that the entire input is to be treated as a `decimal` and it will never pass through a stage in which it is a float.

```surql
/**[test]

[[test.results]]
value = "[8.888dec, 8.888888888888888dec]"

*/

[
  8.888dec,
  8.888888888888888dec
];
```

```surql title="Output"
[
  8.888dec,
  8.888888888888888dec
]
```

Similarly, an attempt to cast a number that is too large for an `int` into a `decimal` will not work, as the parser will first attempt to handle the number on the right before moving on to the cast.

```surql
/**[test]

[test.results]
parsing-error = """Failed to parse number: number cannot fit within a 64bit signed integer'
 --> [1:10]
  |
1 | <decimal>9999999999999999999;
  |          ^^^^^^^^^^^^^^^^^^^"""

*/

<decimal>9999999999999999999;
```

```surql title="Output"
'Failed to parse number: number cannot fit within a 64bit signed integer'
```

However, if the same number is followed by the `dec` suffix, the parser will be aware that the input is meant to be treated as a `decimal` from the outset and the query will succeed.

```surql
/**[test]

[[test.results]]
value = "9999999999999999999dec"

*/

9999999999999999999dec;
```

---
---

## _q008 - **Anonymous functions (closures)**_

- [📓][SurrealQL008_original][surrealdb_docs_3x_surrealql_datamodel_closures]

> Available since: V2.0.0

```syntax title="SurrealQL Syntax"
LET $parameter = |@parameters| @expression;
```

One of the powerful features now available in SurrealDB is the ability to define anonymous functions. These functions can be used to encapsulate reusable logic and can be called from within your queries. Below are some examples demonstrating their capabilities:

### _q008a - **Basic function definitions**_

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "4"

[[test.results]]
value = "NONE"

[[test.results]]
value = "'Hello, World!'"

*/

-- Define an anonymous function that doubles a number
LET $double = |$n: number| $n * 2;
RETURN $double(2);  -- Returns 4

-- Define a function that concatenates two strings
LET $concat = |$a: string, $b: string| $a + $b;
RETURN $concat("Hello, ", "World!");  -- Returns "Hello, World!"
```

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "'Hello, Alice!'"

*/

-- Define a function that greets a person
LET $greet = |$name: string| -> string { "Hello, " + $name + "!" };
RETURN $greet("Alice");   -- Returns "Hello, Alice!"
```

### _q008b - **Error Handling and Type Enforcement**_

You can also enforce type constraints within your functions to prevent type mismatches:

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "'HELLO'"

[[test.results]]
error = "'Incorrect arguments for function ANONYMOUS(). Expected a value of type 'string' for argument $text'"

[[test.results]]
value = "NONE"

[[test.results]]
value = "16"

[[test.results]]
error = "'Incorrect arguments for function ANONYMOUS(). Expected a value of type 'number' for argument $num'"

*/

-- Define a function with a return type
LET $to_upper = |$text: string| -> string { string::uppercase($text) };
RETURN $to_upper("hello");  -- Returns "HELLO"
RETURN $to_upper(123);      -- Error: type mismatch

-- Define a function that accepts only numbers
LET $square = |$num: number| $num * $num;
RETURN $square(4);    -- Returns 16
RETURN $square("4");  -- Error: type mismatch
```

### _q008c - **Closures in functions**_

Many of SurrealDB's functions allow a closure to be passed in, making it easy to use complex logic on a value or the elements of an array.

The `chain` function which performs an operation on a value before passing it on:

```surql
/**[test]

[[test.results]]
value = "2000"

*/

"Two"
  .replace("Two", "2")
  .chain(|$num| <number>$num * 1000);
```

```surql title="Response"
2000
```

We can see that the input to the `.chain()` method is indeed a closure by creating our own that is assigned to a parameter. This closure can be passed into `.chain()`, returning the same output as above.

```surql
LET $my_func = |$num| <number>$num * 1000;

"Two"
  .replace("Two", "2")
  .chain($my_func);
```

The following example shows a chain of array functions used to remove useless data, followed by a check to see if all items in the array match a certain condition, and then a cast into another type. The [`array::filter`][SurrealQL101aq_FunctionsDatabase_Array_filter] call in the middle ensures that the [`string::len`🚫][brakuje_func_db_string#stringlen] function that follows is being called on string values.

```surql
/**[test]

[[test.results]]
value = "'true'"

*/

[NONE, NONE, "good data", "Also good", "important", NULL]
  .filter(|$v| $v.is_string())
  .all(|$s| $s.len() > 5)
  .chain(|$v| <string>$v);
```

```surql title="Response"
'true'
```

### _q008d - **Closure limitations**_

Closures work inside a read-only context, and cannot be used to modify database resources.

```surql
-- 1. Create a test table and function
DEFINE TABLE test_table SCHEMAFULL;
DEFINE FIELD name ON test_table TYPE string;

DEFINE FUNCTION fn::test_create($name: string) -> object {
    CREATE test_table CONTENT { name: $name };
    { created: true, name: $name };
};

-- 2. Call the function directly - works
fn::test_create("direct_call");

-- 3. Call the function inside .map() - fails
LET $names = ["Alice", "Bob", "Charlie"];
$names.map(|$n| fn::test_create($n));
-- Error: "Couldn't write to a read only transaction"
```

In many cases, a closure can be substituted by another operation such as a `FOR` loop or a regular `SELECT` statement.

```surql
DEFINE TABLE test_table SCHEMAFULL;
DEFINE FIELD name ON test_table TYPE string;

DEFINE FUNCTION fn::test_create($name: string) -> object {
    CREATE test_table CONTENT { name: $name };
    { created: true, name: $name };
};

-- Function to create a record called for each name
SELECT VALUE fn::test_create($this) FROM ["Alice", "Bob", "Charlie"];
```

### _q008e - **Capturing parameters**_

> Available since: V3.0.0

The original implementation of closures did not allow them to capture parameters (variables) in their scope. Strictly speaking, this made them simple anonymous functions as closures did not "enclose" anything.

```surql
LET $okay_nums = [1,2,3];

-- Returns [] because $okay_nums not present inside the closure
[1,5,6,7,0].filter(|$n| $n IN $okay_nums);
```

This has since been resolved, allowing a parameter declared outside a closure to be recognized inside it.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "[[1]]"

*/

LET $okay_nums = [1,2,3];

[1,5,6,7,0].filter(|$n| $n IN $okay_nums);
```

### _q008f - **Conclusion**_

These anonymous functions provide a flexible way to define small, reusable pieces of logic that can be used throughout your queries. By leveraging them, you can write more modular and maintainable SurrealQL code.

---
---

## _q009 - **Datetimes**_

- [📓][surrealdb_docs_3x_surrealql_datamodel_datetimes]

SurrealDB has native support for datetimes with nanosecond precision. SurrealDB automatically parses and understands datetimes which are written as strings in the SurrealQL language. Times must also be formatted in [RFC 3339][net__RFC_3339] format.

> [!NOTE]
> As of `v2.0.0`, SurrealDB no longer eagerly converts a string into a datetime. An implicit `d` prefix or cast using `<datetime>` is required instead.

```surql
/**[test]

[[test.results]]
value = "[{ id: event:s9mfw7f45qhlzs0ogche, time: d'2025-07-03T07:18:52Z' }]"
skip-record-id-key = true

*/

CREATE event SET time = d"2025-07-03T07:18:52Z";
```

SurrealDB handles all datetimes with nanosecond precision.

```surql
/**[test]

[[test.results]]
value = "[{ id: event:g7cdb2ny6qozzsrlp9qj, time: d'2025-07-03T07:18:52.841147Z' }]"
skip-record-id-key = true

*/

CREATE event SET time = d"2025-07-03T07:18:52.841147Z";
```

SurrealDB handles all timezones, and automatically converts and stores datetimes as a UTC date.

```surql
/**[test]

[[test.results]]
value = "[{ id: event:wieqqme8hybzpnh043d2, time: d'2025-07-03T05:18:52.841147Z' }]"
skip-record-id-key = true

*/

CREATE event SET time = d"2025-07-03T07:18:52.841147+02:00";
```

A `datetime` can also be created by using `<datetime>` to cast from a string.

With correct input:

```surql
/**[test]

[[test.results]]
value = "[{ id: event:9r69r6c6ovkky3pg7oko, time: d'2025-07-03T07:18:52.841147Z' }]"
skip-record-id-key = true

*/

CREATE event SET time = <datetime>"2025-07-03T07:18:52.841147Z";
```

```surql title="Response"
[{ id: event:jwm8ncmfi30nrxdf24ws, time: d'2025-07-03T07:18:52.841147Z' }]
```

With incorrect input (missing final Z):

```surql
/**[test]

[[test.results]]
error = "'"Expected `datetime` but found a `'2025-07-03T07:18:52.841147'`"'"

*/

CREATE event SET time = <datetime>"2025-07-03T07:18:52.841147";
```

```surql title="Response"
"Expected a datetime but cannot convert '2025-07-03T07:18:52.841147' into a datetime"
```

As a convenience, a date containing a year, month and day but no time will also parse correctly as a datetime.

```surql
/**[test]

[[test.results]]
value = "[{ id: event:ob9p04agl2aoqipet339, time: d'2024-04-03T00:00:00Z' }]"
skip-record-id-key = true

*/

CREATE event SET time = <datetime>"2024-04-03";
```

```surql title="Response"
[{ id: event:4t50wjjlne9v8km2qcwq, time: d'2024-04-03T00:00:00Z' }]
```

### _q009a - **Datetime types in `DEFINE FIELD` statements**_

Defining a field with a set `datetime` type will ensure that datetimes are properly formatted and not passed on as simple strings.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
error = ""Couldn't coerce value for field `time` of `event:qv8qcjf0w9oowekl36w6`: Expected `datetime` but found `'2025-07-03T07:18:52.841147'`""

*/

DEFINE FIELD time ON event TYPE datetime;
// highlight-next-line
CREATE event SET time = "2025-07-03T07:18:52.841147";
```

```surql title="Response"
"Couldn't coerce value for field `time` of `event:qv8qcjf0w9oowekl36w6`: Expected `datetime` but found `'2025-07-03T07:18:52.841147'`"
```

The above query will fail because the datetime is not cast as a datetime type. The correct query is:

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "[{ id: event:w2lhv58f7c9z7xo4nqkq, time: d'2025-07-03T07:18:52.841140Z' }]"
skip-record-id-key = true

*/

DEFINE FIELD time ON event TYPE datetime;
// highlight-next-line
CREATE event SET time = d"2025-07-03T07:18:52.84114Z";
```

```surql title="Response"
[
    { 
        id: event:w2lhv58f7c9z7xo4nqkq, 
        time: d'2025-07-03T07:18:52.841140Z' 
    }
]
```

#### _q009a1 - **Datetime comparison**_

A datetime can be compared with another using the advanced SurrealDB operators.

```surql
d"2025-07-03T07:18:52Z" < d"2025-07-03T07:18:52.84114Z";
```

```surql title="Response"
true
```

### _q009b - **Durations and datetimes**_

A duration can be used to alter a datetime.

```surql
/**[test]

[[test.results]]
value = "[{ id: event:nyk8onbwm2e1n8z32rj9, time: d'2025-07-17T07:18:52Z' }]"
skip-record-id-key = true

*/

CREATE event SET time = d"2025-07-03T07:18:52Z" + 2w;
```

```surql title="Response"
[{ id: event:`9ey7v8r0fd46xblf9dsf`, time: d'2025-07-17T07:18:52Z' }]
```

Multi-part durations can also be used to modify datetimes.

```surql
/**[test]

[[test.results]]
value = "[{ id: event:5uuzy32t48yutxyszi7p, time: d'2025-07-03T08:49:14.191147Z' }]"
skip-record-id-key = true

*/

CREATE event SET time = d"2025-07-03T07:18:52.841147Z" + 1h30m20s1350ms;
```

```surql title="Response"
[{ id: event:5uuzy32t48yutxyszi7p, time: d'2025-07-03T08:49:14.191147Z' }]
```

#### _q009b1 - **Duration units**_

Durations can be specified in any of the following units:

| Unit | Description |
| :--- | :--- |
| **`ns`** | Nanoseconds |
| **`us`** | Microseconds, alternative: µs |
| **`ms`** | Milliseconds |
| **`s`** | Seconds |
| **`m`** | Minutes |
| **`h`** | Hours |
| **`d`** | Days |
| **`w`** | Weeks |
| **`y`** | Years |

### _q009c - **Next steps**_

You've now seen how to store, modify, and handle dates and times in SurrealDB. For more advanced functionality, take a look at the [time🚫][brakuje_func_db_time] functions, which enable extracting, altering, rounding, and grouping datetimes into specific time intervals.

---
---

## _q010 - **Files**_

- [📓][surrealdb_docs_3x_surrealql_datamodel_files]

> Available since: V3.0.0

Files are accessed by a path, which is prefixed with an `f` to differentiate it from a regular string.

Some examples of file pointers:

```surql
/**[test]

[[test.results]]
value = "f"bucket:/some/key/to/a/file.txt""

*/

f"bucket:/some/key/to/a/file.txt";
f"bucket:/some/key/with\ escaped";
```

To work with the files that can be accessed through these pointers, use the following:

- A [`DEFINE BUCKET`🚫][brakuje_stat_def_bucket] statement to set up the bucket to hold the files
- [Files functions🚫][brakuje_func_db_file] such as `file::put()` and `file::get()`

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "NONE"

[[test.results]]
value = "b"536F6D65207465787420696E73696465""

[[test.results]]
value = "'Some text inside'"

*/

DEFINE BUCKET my_bucket BACKEND "memory";
f"my_bucket:/some_file.txt".put("Some text inside");
f"my_bucket:/some_file.txt".get();
<string>f"my_bucket:/some_file.txt".get();
```

```surql title="Output"
-------- Query --------

b"536F6D65207465787420696E73696465"

-------- Query --------

'Some text inside'
```

### _q010a - **Using files for ad-hoc memory storage**_

A combination of files and SurrealDB's [encoding functions🚫][brakuje_func_db_encoding#encodingcbordecod] can be used to set up ad-hoc memory storage. This can be convenient when running an instance that saves data to disk but prefers to keep certain items in memory.

The following example shows how this pattern might be used for temporary storage such as a user's shopping cart during a single session.

```surql
-- Set up the in-memory backend
DEFINE BUCKET shopping_carts BACKEND "memory";

-- Convenience functions to save, decode back into
-- SurrealQL type, and delete
DEFINE FUNCTION fn::save_file($file_name: string, $input: any) {
    LET $file = type::file("shopping_carts", $file_name);
    $file.put(encoding::cbor::encode($input));
};

DEFINE FUNCTION fn::get_file($file_name: string) {
    encoding::cbor::decode(type::file("shopping_carts", $file_name).get())
};

DEFINE FUNCTION fn::delete_file($file_name: string) {
    type::file("shopping_carts", $file_name).delete();
};

-- Save current shoppingcart
fn::save_file("temp_cart_user_24567", {
    items: ["shirt1"],
    last_updated: time::now()
});

fn::get_file("temp_shopping_cart_user_24567");
-- Returns { items: ['shirt1', 'deck_of_cards'], last_updated: d'2025-11-20T01:03:24.141080Z' }

-- User adds item, save over file with newer information
fn::save_file("temp_cart_user_24567", {
    items: ["shirt1", "deck_of_cards"],
    last_updated: time::now()
});

fn::get_file("temp_cart_user_24567");
-- Returns { items: ['shirt1', 'deck_of_cards'], last_updated: d'2025-11-20T01:06:02.752429Z' }

-- Session is over, delete temp file
fn::delete_file("temp_cart_user_24567");
```

---
---

## _q011 - **Formatters**_

- [📓][surrealdb_docs_3x_surrealql_datamodel_formatters]

The [string::is_datetime🚫][brakuje_func_db_string#stringisdatetime]: and [time::format🚫][brakuje_func_db_time#timeformat] functions in SurrealQL accept certain text formats for date/time formatting. The possible formats are listed below.

### _q011a - **formatters for date and time**_

#### _q011a1 - **Date formatters**_

| Specifier | Example | Description |
| :--- | :--- | :--- |
| %Y | 2001 | The full proleptic Gregorian year, zero-padded to 4 digits. |
| %C | 20 | The proleptic Gregorian year divided by 100, zero-padded to 2 digits. |
| %y | 01 | The proleptic Gregorian year modulo 100, zero-padded to 2 digits. |
| %m | 07 | Month number (01 to 12), zero-padded to 2 digits. |
| %b | Jul | Abbreviated month name. Always 3 letters. |
| %B | July | Full month name. |
| %h | Jul | Same as %b. |
| %d | 08 | Day number (01 to 31), zero-padded to 2 digits. |
| %e | 8 | Same as %d but space-padded. Same as %_d. |
| %a | Sun | Abbreviated weekday name. Always 3 letters. |
| %A | Sunday | Full weekday name. |
| %w | 0 | Day of the week. Sunday = 0, Monday = 1, ..., Saturday = 6. |
| %u | 7 | Day of the week. Monday = 1, Tuesday = 2, ..., Sunday = 7. ([RFC 3339][net__RFC_3339]) |
| %U | 28 | Week number starting with Sunday (00 to 53), zero-padded to 2 digits. |
| %W | 27 | Same as %U, but week 1 starts with the first Monday in that year instead. |
| %G | 2001 | Same as %Y but uses the year number in [RFC 3339][net__RFC_3339] week date. |
| %g | 01 | Same as %y but uses the year number in [RFC 3339][net__RFC_3339] week date. |
| %V | 27 | Same as %U but uses the week number in [RFC 3339][net__RFC_3339] week date (01 to 53). |
| %j | 189 | Day of the year (001 to 366), zero-padded to 3 digits. |
| %D | 07/08/01 | Month-day-year format. Same as %m/%d/%y. |
| %x | 07/08/01 | Locale's date representation. |
| %F | 2001-07-08 | Year-month-day format ([RFC 3339][net__RFC_3339]). Same as %Y-%m-%d. |
| %v | 8-Jul-2001 | Day-month-year format. Same as %e-%b-%Y. |

#### _q011a2 - **Time formatters**_

| Specifier | Example | Description |
| :--- | :--- | :--- |
| %H | 00 | Hour number (00 to 23), zero-padded to 2 digits. |
| %k | 0 | Same as %H but space-padded. Same as %_H. |
| %I | 12 | Hour number in 12-hour clocks (01 to 12), zero-padded to 2 digits. |
| %l | 12 | Same as %I but space-padded. Same as %_I. |
| %P | am | am or pm in 12-hour clocks. |
| %p | AM | AM or PM in 12-hour clocks. |
| %M | 34 | Minute number (00 to 59), zero-padded to 2 digits. |
| %S | 60 | Second number (00 to 60), zero-padded to 2 digits. |
| %f | 026490000 | The fractional seconds (in nanoseconds) since last whole second. |
| %.f | .026490 | Similar to %f but left-aligned. |
| %.3f | .026 | Similar to .%f but left-aligned but fixed to a length of 3. |
| %.6f | .026490 | Similar to .%f but left-aligned but fixed to a length of 6. |
| %.9f | .026490000 | Similar to .%f but left-aligned but fixed to a length of 9. |
| %3f | 026 | Similar to %.3f but without the leading dot. |
| %6f | 026490 | Similar to %.6f but without the leading dot. |
| %9f | 026490000 | Similar to %.9f but without the leading dot. |
| %R | 00:34 | Hour-minute format. Same as %H:%M. |
| %T | 00:34:59 | Hour-minute-second format. Same as %H:%M:%S. |
| %X | 00:34:59 | Locale's time representation. |
| %r | 12:34:59 AM | Hour-minute-second format in 12-hour clocks. Same as %I:%M:%S %p. |
| %x | 07/08/01 | Locale's date representation. |
| %F | 2001-07-08 | Year-month-day format [net__RFC_3339]. Same as %Y-%m-%d. |
| %v | 8-Jul-2001 | Day-month-year format. Same as %e-%b-%Y. |

#### _q011a3 - **Timezones formatters**_

| Specifier | Example | Description |
| :--- | :--- | :--- |
| %Z | ACST | Local time zone name. |
| %z | +0930 | Offset from the local time to UTC (with UTC being +0000). |
| %:z | +09:30 | Same as %z but with a colon. |

#### _q011a4 - **Date & time formatters**_

| Specifier | Example | Description |
| :--- | :--- | :--- |
| %c | Sun Jul 8 00:34:59 2001 | Locale's date and time. |
| %+ | 2001-07-08T00:34:59.026490+09:30 | RFC 3339 / RFC 3339 date & time format. |
| %s | 994518299 | UNIX timestamp, the number of seconds since 1970-01-01T00:00:00. |

#### _q011a5 - **Other formatters**_

| Specifier | Example | Description |
| :--- | :--- | :--- |
| %t | - | Literal tab (\t). |
| %n | - | Literal newline (\n). |
| %% | - | Literal percent sign. |

### _q011b - **Examples**_

Seeing if an input with a date and time conforms to an expected format:

```surql
/**[test]

[[test.results]]
value = "true"

*/

string::is_datetime("5sep2024pm012345.6789", "%d%b%Y%p%I%M%S%.f");
```

```surql title="Response"
true
```

Another example with a different format:

```surql
/**[test]

[[test.results]]
value = "false"

*/

string::is_datetime("23:56:00 2015-09-05", "%Y-%m-%d %H:%M");
```

```surql title="Response"
false
```

Using a formatter to generate a string from a datetime:

```surql
/**[test]

[[test.results]]
value = "'2021-11-01'"

*/

time::format(d"2021-11-01T08:30:17+00:00", "%Y-%m-%d");
```

```surql title="Response"
"2021-11-01"
```

---
---

## _q012 - **Futures (`COMPUTED` clause)**_

- [📓][surrealdb_docs_3x_surrealql_datamodel_futures]

> [!NOTE]
> The `future` type is only available up to SurrealDB 2.x. Since version 3.0.0-beta, it has been replaced by [defined fields using the `COMPUTED` clause🚫][brakuje_stat_def_field#computed-fields]. Most examples in this page include an equivalent `COMPUTED` clause to aid in migrating to the new implementation.

Futures are values which are only computed when the data is selected and returned to the client. Futures can be stored inside records, to enable dynamic values which are always calculated when queried.

### _q012a - **Simple futures**_

Any value or expression can be used inside a future. This value will be dynamically computed on every access to the record.

#### _q012a1 - **Legacy future type**

```surql
CREATE person SET accessed_date = <future> { time::now() };
```

#### _q012a2 - **With COMPUTED clause**

```surql
-- Only used inside a DEFINE FIELD statement
DEFINE FIELD accessed_date ON person COMPUTED time::now();
```

### _q012b - **Futures inside schema definitions

A future can be added to a schema definition as well.

#### _q012b1 - **Legacy future type**

```surql
DEFINE FIELD accessed_at ON TABLE user VALUE <future> { time::now() };

CREATE user:one;
SELECT * FROM ONLY user:one;
-- Sleep for one second
SLEEP 1s;
-- `accessed_at` is a different value now
SELECT * FROM ONLY user:one;
```

#### _q012b2 - **With COMPUTED clause**

```surql
DEFINE FIELD accessed_at ON TABLE user COMPUTED time::now();

CREATE user:one;
SELECT * FROM ONLY user:one;
-- Sleep for one second
SLEEP 1s;
-- `accessed_at` is a different value now
SELECT * FROM ONLY user:one;
```

This differs from a `VALUE` clause which is only calculated when it is modified (created or updated), but is not recalculated during a `SELECT` query which does not modify a record.

```surql
DEFINE FIELD updated ON TABLE user VALUE time::now();

CREATE user:one;
SELECT * FROM ONLY user:one;
-- Sleep for one second
SLEEP 1s;
-- `updated` is still the same
SELECT * FROM ONLY user:one;
```

### _q012c - **Futures depending on statements**_

If the value of a future is the result of a statement, it must be wrapped in parentheses.

#### _q012c1 - **Legacy future type**

```surql
DEFINE FIELD random_movie
    ON app_screen
    VALUE <future> { (SELECT * FROM ONLY movie ORDER BY RAND() LIMIT 1) };
```

#### _q012c2 - **With COMPUTED clause**

```surql
-- No need for parentheses
DEFINE FIELD random_movie
    ON app_screen
    COMPUTED SELECT * FROM ONLY movie ORDER BY RAND() LIMIT 1;
```

If your statement is wrapped in parentheses, you need to access the fields using the $parent variable.

```surql
DEFINE FIELD OVERWRITE followers
    ON user
    VALUE <future> { (SELECT VALUE count FROM ONLY follower_count WHERE user = $parent.id LIMIT 1) ?? 0 };
```

### _q012d - **Avoiding infinite recursion**_

When defining a future on a field, be sure to avoid any statements that would cause infinite recursion. In the following example, the `random_friend` field is defined by a statement that uses a `SELECT` statement on all the fields of the same `person` table, one of which will also use the same `future` to compute its value.

```surql
CREATE |person:10| SET name = "Person " + <string>id.id() RETURN NONE;

DEFINE FIELD random_friend
    ON person
    VALUE <future> { (SELECT * FROM ONLY person ORDER BY RAND() LIMIT 1) };

CREATE person;
```

```surql title="Output"
'Reached excessive computation depth due to functions, subqueries, or futures'
```

A `SELECT` query that does not access the field defined by a future will avoid the infinite recursion.

```surql
CREATE |person:10| SET name = "Person " + <string>id.id() RETURN NONE;

DEFINE FIELD random_friend
    ON person
    VALUE <future> { (SELECT VALUE name FROM ONLY person ORDER BY RAND() LIMIT 1) };

CREATE person;
```

```surql title="Output"
[
  {
    id: person:4o973bouhd6xrj8l2x69,
    random_friend: 'Person imoy71qbhnsgjtczybiq'
  }
]
```

### _q012e - **Next steps**_

You've now seen how to create dynamically computed properties on records, using either simple values, and values which depend on local and remote record fields. Take a look at the next chapter to get into SurrealDB's geospatial types.

---
---

## _q013 - **Geometries**_

- [📓][surrealdb_docs_3x_surrealql_datamodel_geometries]

A `geometry` is a type based on the GeoJSON spec that is optimised for working with data pertaining to locations on Earth.

SurrealDB makes working with GeoJSON easy, with support for `Point`, `LineString`, `Polygon`, `MultiPoint`, `MultiLineString`, `MultiPolygon`, and `Collection` values. SurrealQL automatically detects GeoJSON objects converting them into a single data type.

| Type | Description |
| :--- | :--- |
| [`Point`][SurrealQL013b_DataTypes_Geometries_Point] | A geolocation point with longitude and latitude |
| [`LineString`][SurrealQL013c_DataTypes_Geometries_LineString] | A GeoJSON LineString value for storing a geometric path |
| [`Polygon`][SurrealQL013d_DataTypes_Geometries_Polygon] | A GeoJSON Polygon value for storing a geometric area |
| [`MultiPoint`][SurrealQL013e_DataTypes_Geometries_MultiPoint] | A value which contains multiple geometry points |
| [`MultiLineString`][SurrealQL013f_DataTypes_Geometries_MultiLineString] | A value which contains multiple geometry lines |
| [`MultiPolygon`][SurrealQL013g_DataTypes_Geometries_MultiPolygon] | A value which contains multiple geometry polygons |
| [`Collection`][SurrealQL013h_DataTypes_Geometries_Collection] | A value which contains multiple different geometry types |

### _q013a - **The GeoJSON spec**_

There are two main points to keep in mind when creating a `geometry` type in SurrealDB. They are:

- Points are defined according to the GeoJSON spec, which specificies longitude before latitude. Many sites - including Google Maps - provide location data in the opposite order, so be sure to confirm that any data being used to create a `Point` is in the order `(longitude, latitude)`, and not the other way around.
- A `geometry` created from an object must contain a `type` field and a `coordinates` field, no more and no less.

This can be shown by calling the [`type::is_geometry()`🚫][brakuje_func_db_type#typeis_geometry] function on some sample objects.

```surql
-- true: has `type` and `coordinates` field with valid data
{ type: "Point", coordinates: [-0.118092, 51.509865] }.is_geometry();

-- false: lacks 'type' field
{ coordinates: [-0.118092, 51.509865] }.is_geometry();

-- false: has an extra field
{ type: "Point", coordinates: [-0.118092, 51.509865], unnecessary: "data" }.is_geometry();
```

### _q013b - **`Point`**_

The simplest form of GeoJSON that SurrealDB supports is a geolocation point. These can be written using two different formats. The first format is that of an object that matches the GeoJSON spec.

```surql
/**[test]

[[test.results]]
value = "[{ centre: (-0.118092, 51.509865), id: city:london }]"

*/

CREATE city:london SET centre = {
    type: "Point",
    coordinates: [-0.118092, 51.509865],
};
```

The other format is a simple 2-element tuple containing the longitude and the latitude of a location. This output for this format is no different from the above, and is simply a convenience due to the frequency of use of the `Point` type.

```surql
/**[test]

[[test.results]]
value = "[{ centre: (-0.118092, 51.509865), id: city:london }]"

*/

CREATE city:london SET centre = (-0.118092, 51.509865);
```

### _q013c - **`LineString`**_

A GeoJSON LineString value for storing a geometric path.

```surql
/**[test]

[[test.results]]
value = "[{ distance: { type: 'LineString', coordinates: [[-0.118092, 51.509865], [0.1785278, 51.37692386]] }, id: city:london }]"

*/

CREATE city:london SET distance = {
    type: "LineString",
    coordinates: [[-0.118092, 51.509865],[0.1785278, 51.37692386]],
};
```

### _q013d - **`Polygon`**_

A GeoJSON Polygon value for storing a geometric area.

```surql
/**[test]

[[test.results]]
value = "[{ boundary: { type: 'Polygon', coordinates: [[[-0.38314819, 51.37692386], [0.1785278, 51.37692386], [0.1785278, 51.6146057], [-0.38314819, 51.6146057], [-0.38314819, 51.37692386]]] }, id: city:london }]"

*/

CREATE city:london SET boundary = {
  type: "Polygon",
  coordinates: [[
    [-0.38314819, 51.37692386], [0.1785278, 51.37692386],
    [0.1785278, 51.61460570], [-0.38314819, 51.61460570],
    [-0.38314819, 51.37692386]
  ]]
};
```

### _q013e - **`MultiPoint`**_

MultiPoints can be used to store multiple geometry points in a single value.

```surql
/**[test]

[[test.results]]
value = "[{ id: person:tobie, locations: { type: 'MultiPoint', coordinates: [[10, 11.2], [10.5, 11.9]] } }]"

*/

CREATE person:tobie SET locations = {
  type: "MultiPoint",
  coordinates: [
    [10.0, 11.2],
    [10.5, 11.9]
  ],
};
```

### _q013f - **`MultiLineString`**_

A MultiLineString can be used to store multiple geometry lines in a single value.

```surql
/**[test]

[[test.results]]
value = "[{ id: travel:yellowstone, routes: { type: 'MultiLineString', coordinates: [[[10, 11.2], [10.5, 11.9]], [[11, 12.2], [11.5, 12.9], [12, 13]]] } }]"

*/

CREATE travel:yellowstone SET routes = {
  type: "MultiLineString",
  coordinates: [
    [ [10.0, 11.2], [10.5, 11.9] ],
    [ [11.0, 12.2], [11.5, 12.9], [12.0, 13.0] ]
  ]
}
```

### _q013g - **`MultiPolygon`**_

MultiPolygons can be used to store multiple geometry polygons in a single value.

```surql
/**[test]

[[test.results]]
value = "[{ id: university:oxford, locations: { type: 'MultiPolygon', coordinates: [[[[10, 11.2], [10.5, 11.9], [10.8, 12], [10, 11.2]]], [[[9, 11.2], [10.5, 11.9], [10.3, 13], [9, 11.2]]]] } }]"

*/

CREATE university:oxford SET locations = {
  type: "MultiPolygon",
  coordinates: [
    [
      [ [10.0, 11.2], [10.5, 11.9], [10.8, 12.0], [10.0, 11.2] ]
    ],
    [
      [ [9.0, 11.2], [10.5, 11.9], [10.3, 13.0], [9.0, 11.2] ]
    ]
  ]
};
```

### _q013h - **`Collection`**_

Collections can be used to store multiple different geometry types in a single value.

```surql
/**[test]

[[test.results]]
value = "[{ buildings: { type: 'GeometryCollection', geometries: [{ type: 'MultiPoint', coordinates: [[10, 11.2], [10.5, 11.9]] }, { type: 'Polygon', coordinates: [[[-0.38314819, 51.37692386], [0.1785278, 51.37692386], [0.1785278, 51.6146057], [-0.38314819, 51.6146057], [-0.38314819, 51.37692386]]] }, { type: 'MultiPolygon', coordinates: [[[[10, 11.2], [10.5, 11.9], [10.8, 12], [10, 11.2]]], [[[9, 11.2], [10.5, 11.9], [10.3, 13], [9, 11.2]]]] }] }, id: university:oxford }]"

*/

CREATE university:oxford SET buildings = {
  type: "GeometryCollection",
  geometries: [
    {
      type: "MultiPoint",
      coordinates: [
        [10.0, 11.2],
        [10.5, 11.9]
      ],
    },
    {
      type: "Polygon",
      coordinates: [[
        [-0.38314819, 51.37692386], [0.1785278, 51.37692386],
        [0.1785278, 51.61460570], [-0.38314819, 51.61460570],
        [-0.38314819, 51.37692386]
      ]]
    },
    {
      type: "MultiPolygon",
      coordinates: [
        [
          [ [10.0, 11.2], [10.5, 11.9], [10.8, 12.0], [10.0, 11.2] ]
        ],
        [
          [ [9.0, 11.2], [10.5, 11.9], [10.3, 13.0], [9.0, 11.2] ]
        ]
      ]
    }
  ]
};
```

### _q013i - **Example**_

The following example includes five records from [an open database][net__opendatasoft_geonames] with cities worldwide that have of a population of at least 1000. The queries below create a `city` record from each entry that includes their name, location, and name. Next, it uses the [`geo::distance`🚫][brakuje_func_db_geo#geodistance] function to find their two closest neighbours, relating them via the `close_to` relation table. The final query can be viewed in traditional form to see each city's neighbours, or on Surrealist's [graph view🚫][brakuje_blog_visualisationGraphView] to see a visual representation of the network of closely linked cities.

```surql
DEFINE TABLE city SCHEMAFULL;
DEFINE FIELD name ON city TYPE string;
DEFINE FIELD location ON city TYPE point;

FOR $city IN [{"geoname_id": "5881639", "name": "100 Mile House", "ascii_name": "100 Mile House", "feature_class": "P", "feature_code": "PPL", "country_code": "CA", "cou_name_en": "Canada", "country_code_2": null, "admin1_code": "02", "admin2_code": "5941", "admin3_code": "5941005", "admin4_code": null, "population": 1980, "elevation": null, "dem": 928, "timezone": "America/Vancouver", "modification_date": "2019-11-26", "label_en": "Canada", "coordinates": {"lon": -121.28594, "lat": 51.64982}},{"geoname_id": "5896969", "name": "Beaverlodge", "ascii_name": "Beaverlodge", "feature_class": "P", "feature_code": "PPL", "country_code": "CA", "cou_name_en": "Canada", "country_code_2": null, "admin1_code": "01", "admin2_code": "4819009", "admin3_code": null, "admin4_code": null, "population": 2219, "elevation": null, "dem": 723, "timezone": "America/Edmonton", "modification_date": "2024-02-28", "label_en": "Canada", "coordinates": {"lon": -119.43605, "lat": 55.21664}},{"geoname_id": "5911606", "name": "Burnaby", "ascii_name": "Burnaby", "feature_class": "P", "feature_code": "PPLA3", "country_code": "CA", "cou_name_en": "Canada", "country_code_2": null, "admin1_code": "02", "admin2_code": "5915", "admin3_code": "5915025", "admin4_code": null, "population": 202799, "elevation": null, "dem": 87, "timezone": "America/Vancouver", "modification_date": "2019-02-26", "label_en": "Canada", "coordinates": {"lon": -122.95263, "lat": 49.26636}},{"geoname_id": "5920996", "name": "Chertsey", "ascii_name": "Chertsey", "feature_class": "P", "feature_code": "PPL", "country_code": "CA", "cou_name_en": "Canada", "country_code_2": null, "admin1_code": "10", "admin2_code": "14", "admin3_code": "62047", "admin4_code": null, "population": 4836, "elevation": null, "dem": 251, "timezone": "America/Toronto", "modification_date": "2016-06-22", "label_en": "Canada", "coordinates": {"lon": -73.89095, "lat": 46.07109}},{"geoname_id": "5941905", "name": "Dorset Park", "ascii_name": "Dorset Park", "alternate_names": null, "feature_class": "P", "feature_code": "PPLX", "country_code": "CA", "cou_name_en": "Canada", "country_code_2": null, "admin1_code": "08", "admin2_code": "3520", "admin3_code": null, "admin4_code": null, "population": 25003, "elevation": null, "dem": 164, "timezone": "America/Toronto", "modification_date": "2020-05-02", "label_en": "Canada", "coordinates": {"lon": -79.28215, "lat": 43.75386}}]

{
    CREATE type::record("city", <int>$city.geoname_id) SET
    location = <point>[$city.coordinates.lon, $city.coordinates.lat],
    name = $city.name;        
};

FOR $city IN SELECT * FROM city {
    LET $this_location = $city.location;
    LET $closest = 
    (SELECT id, location, geo::distance($this_location, location) AS distance FROM city
  ORDER BY distance ASC
  LIMIT 3
    ).filter(|$c| $c.distance != 0);
    FOR $closest IN $closest {
      RELATE $city->close_to->$closest SET
      distance = geo::distance($city.location, $closest.location);
    };
};

SELECT name, id, ->close_to->city AS neighbours FROM city;
```

### _q013j - **Next steps**_

You've now seen how to use geometries to store locations, paths, and polygonal areas in SurrealDB. For more advanced functionality, take a look at the [operators][SurrealQL002_Operators] and [geo🚫][brakuje_func_db_geo] functions, which enable area, distance, and bearing geometric calculations, and the ability to detect whether geometries contain or intersect other geometry types.

---
---

## _q014 - **Idioms**_

- [📓][surrealdb_docs_3x_surrealql_datamodel_idioms]

Idioms in SurrealQL provide a powerful and flexible way to access and manipulate data within records using paths. They allow you to navigate through nested data structures, access fields, array elements, call methods, and perform complex queries with ease. Idioms are similar to expressions in other query languages that provide a path to data within documents or records.

An idiom is composed of a sequence of **parts** that define the path to a value within a record or data structure. Each part specifies how to navigate to the next piece of data. Idioms can be used in various parts of SurrealQL. The most common usecase is in data retrival queries such as `SELECT` statements, but they can also be used in the `WHERE` clause, `SET` clause, and more.

An idiom is made up of one or more **parts**, each of which can be one of several types:

- [**Field**][SurrealQL014a_DataTypes_Idioms_Field]: Access a field by name.
- [**Index**][SurrealQL014b_DataTypes_Idioms_Index]: Access an element of an array by its index.
- [**All**][SurrealQL014c_DataTypes_Idioms_AllElements]: Access all elements or fields.
- [**Last**][SurrealQL014d_DataTypes_Idioms_LastElements]: Access the last element of an array.
- [**Where**][SurrealQL014c1_DataTypes_Idioms_Where]: Filter elements based on a condition.
- [**Method**][SurrealQL014e_DataTypes_Idioms_MethodChaining]: Call a method on the current data.
- [**Graph**][SurrealQL014f_DataTypes_Idioms_GraphNavigation]: Navigate through graph relationships.
- [**Destructure**][SurrealQL014g_DataTypes_Idioms_Destructuring]: Destructure nested objects.
- [**Optional**][SurrealQL014h_DataTypes_Idioms_OptionalPart]: Indicate that the following part is optional.
- [**Recurse**][SurrealQL014j_DataTypes_Idioms_RecursivePaths]: Recursively traverse paths such as graph and record links.

In this section, we'll explore each part in detail with examples to help you understand how to use idioms in SurrealQL.

### _q014a - **Field Access**_

Since SurrealDB is a document database at its core, each record is stored on an underlying key-value store storage engine with the ability to store arbitrary arrays, objects, and many other types of data. To access a field in an object, use a dot `.` followed by the field name.

This is mostly helpful when accessing fields within a record, but can also be used to access fields within an array.

For example, using the `CREATE` statement to add a record into the `person` table:

```surql title="Query"
/**[test]

[[test.results]]
value = "[{ address: { city: 'New York', country: 'USA' }, age: 30, id: person:oakmq2g0njddr5ysmils, name: 'John Doe' }]"
skip-record-id-key = true

*/

CREATE person CONTENT {
    name: "John Doe",
    age: 30,
    address: {
      city: "New York",
      country: "USA"
    }
};
```

```surql title="Response"
[
  {
    address: {
      city: 'New York',
      country: 'USA'
    },
    age: 30,
    id: person:g87bnds1gcgrnoj4p5q3,
    name: 'John Doe'
  }
]
```

To access the `city` field within the `address` object, you can use the following idiom:

```surql title="Query"
SELECT address.city FROM person;
```

```surql title="Response"
[
  {
    "address": {
      "city": "New York"
    }
  }
]
```

In this example, `person.name` is an idiom that accesses the `name` field of the `person` record.

### _q014b - **Index Access**_

To access an element in an array by its index, use square brackets `[]` with the index inside. For example, let's say we have a `school` record with some student results.

```surql title="Query"
/**[test]

[[test.results]]
value = "[{ id: student:m1rdvvs0el37kiifume4, results: [{ date: '2017-06-18T08:00:00Z', name: 'Algorithmics', score: 76 }, { date: '2018-03-21T08:00:00Z', name: 'Concurrent Programming', score: 83 }, { date: '2018-09-17T08:00:00Z', name: 'Advanced Computer Science 101', score: 69 }, { date: '2019-04-20T08:00:00Z', name: 'Distributed Databases', score: 73 }] }]"
skip-record-id-key = true

*/

CREATE student SET results = [
  { score: 76, date: "2017-06-18T08:00:00Z", name: "Algorithmics" },
  { score: 83, date: "2018-03-21T08:00:00Z", name: "Concurrent Programming" },
  { score: 69, date: "2018-09-17T08:00:00Z", name: "Advanced Computer Science 101" },
  { score: 73, date: "2019-04-20T08:00:00Z", name: "Distributed Databases" },
];
```

```surql title="Response"
[
  {
    id: student:urxaykt4qkbr8rs2o68j,
    results: [
      {
        date: '2017-06-18T08:00:00Z',
        name: 'Algorithmics',
        score: 76
      },
      {
        date: '2018-03-21T08:00:00Z',
        name: 'Concurrent Programming',
        score: 83
      },
      {
        date: '2018-09-17T08:00:00Z',
        name: 'Advanced Computer Science 101',
        score: 69
      },
      {
        date: '2019-04-20T08:00:00Z',
        name: 'Distributed Databases',
        score: 73
      }
    ]
  }
]
```

To access the first student in the `results` array, you can use the following idiom:

```surql
SELECT results[0].score FROM student;
```

```surql title="Response"
[
  {
    results: [
      { score: 76 }
    ]
  }
]
```

Here, `results[0].score` accesses the score of the first student in the `results` array.

### _q014c - **All Elements**_

To access all elements in an array or all fields in an object, use `.*`. This is useful when you want to access all the elements in an array or all the fields in an object.

```surql
SELECT results.* FROM student;
```

```surql title="Response"
{
  results: [
    {
      date: '2017-06-18T08:00:00Z',
      name: 'Algorithmics',
      score: 76
    },
    {
      date: '2018-03-21T08:00:00Z',
      name: 'Concurrent Programming',
      score: 83
    },
    {
      date: '2018-09-17T08:00:00Z',
      name: 'Advanced Computer Science 101',
      score: 69
    },
    {
      date: '2019-04-20T08:00:00Z',
      name: 'Distributed Databases',
      score: 73
    }
  ]
};
```

This idiom selects all elements in the `score` array.

The `.*` idiom is often seen in definitions and error messages.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "{ events: {  }, fields: { friends: 'DEFINE FIELD friends ON person TYPE array<record<person>> PERMISSIONS FULL', "friends.*": 'DEFINE FIELD friends.* ON person TYPE record<person> PERMISSIONS FULL' }, indexes: {  }, lives: {  }, tables: {  } }"

*/

DEFINE FIELD friends ON TABLE person TYPE array<record<person>>;
INFO FOR TABLE person;
```

The output for `INFO FOR TABLE person` includes an automatically generated definition for `friends.*`, namely every item inside the `friends` field.

```surql
{
  events: {},
  fields: {
    friends: 'DEFINE FIELD friends ON person TYPE array<record<person>> PERMISSIONS FULL',
    "friends.*": 'DEFINE FIELD friends.* ON person TYPE record<person> PERMISSIONS FULL'
  },
  indexes: {},
  lives: {},
  tables: {}
};
```

#### _q014c1 - **Using `.*` to return values**_

> Available since: v2.1.0

The `.*` idiom in SurrealDB allows you to target all values in an object or all entries in an array. It can be used in various contexts such as querying, field definitions, and data manipulation. This section explains the behavior of `.*` with practical examples.

#### _q014c2 - **Accessing all values in an object**_

When applied to an object, `.*` returns an array containing all the values of the object's properties.

```surql
/**[test]

[[test.results]]
value = "{ a: 1, b: 2 }"

*/
 { a: 1, b: 2 }.*;
```

##### **SurrealDB 2.x**

```surql title="Response"
[1, 2]
```

##### **SurrealDB 3.x**

```surql title="Response"
{ a: 1, b: 2 }
```

To see just the values of this object, the [`object::values()`🚫][brakuje_func_db_object#objectvalues] function can be used.

```surql
/**[test]

[[test.results]]
value = "[1, 2]"

*/

{ a: 1, b: 2 }.values();

-- [1, 2]
```

##### _q014c1a - **Defining Fields with `.*`**_

You can define fields using `.*` to specify constraints or types for all properties within an object field.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "NONE"

*/

DEFINE FIELD obj ON test TYPE object;
DEFINE FIELD obj.* ON test TYPE number;
```

Here, we define a field `obj` of type `object` on the `test` table, and then specify that all properties within `obj` (`obj.*`) must be of type `number`.

With this done, attempting to insert a non-number value into any property of `obj` will result in an error.

```surql
CREATE test:1 SET obj.a = 'a';

// Error
"Couldn't coerce value for field `obj.*` of `test:1`: Expected `number` but found `'a'`"
```

##### _q014c1b - **Using `.*` in Different Contexts**_

Depending on where `.*` is used, it can have different effects on the order of operations.

For example, if we want to return all the properties of the `person:tobie` record, we can do the following:

```surql
/**[test]

[[test.results]]
value = "{ id: person:tobie, name: 'Tobie' }"

[[test.results]]
value = "{ id: person:tobie, name: 'Tobie' }"

[[test.results]]
value = "{ id: person:tobie, name: 'Tobie' }"

[[test.results]]
value = "{ id: person:tobie, name: 'Tobie' }"

[[test.results]]
value = "{ id: person:tobie, name: 'Tobie' }"

*/

CREATE ONLY person:tobie SET name = 'Tobie';
SELECT * FROM ONLY person:tobie.*;    -- This works
SELECT * FROM ONLY (person:tobie.*);  -- Equivalent to above
SELECT * FROM ONLY { id: person:tobie, name: 'tobie' }; -- Equivalent to above
(SELECT * FROM ONLY person:tobie).*; -- Equivalent to above
```

```surql title="Output"
{
  id: person:tobie,
  name: 'tobie'
}
```

### _q014d - **Last Element**_

Addionally to access the last element of an array, use `[$]`. Refereing to the `student` record above, we can access the last element of the `results` array using the following idiom:

```surql
SELECT results[$].score FROM student;
```

```surql title="Response"
[
  {
    results: {
      score: 73
    }
  }
]
```

This idiom accesses the last element of the `score` array.

### _q014e - **Method chaining**_

> Available since: v2.0.0

To call a method on the current data, use a dot `.` followed by the method name and parentheses `()` with arguments. SurrealDB supports method chaining, so you can call multiple methods (functions) on the same data. Learn more about [method chaining🚫][brakuje_func_db#method-syntax] in the functions section.

For example, let's create a new `person` record and then call `uppercase()` on its name field.

```surql
/**[test]

[[test.results]]
value = "[{ address: { city: 'New York', country: 'USA' }, age: 30, id: person:hfmq0ckvi2u842jqqx9w, name: 'John Doe' }]"
skip-record-id-key = true

[[test.results]]
value = "[{ address: { city: 'New York', country: 'USA' }, age: 30, id: person:hfmq0ckvi2u842jqqx9w, name: 'JOHN DOE' }]"
skip-record-id-key = true

*/

CREATE person CONTENT {
    name: "John Doe",
    age: 30,
    address: {
      city: "New York",
      country: "USA"
    }
};

SELECT *, name.uppercase() FROM person;
```

```surql title="Response"
[
  {
    "person": {
      "name": "John Doe",
      "age": 30,
      "address": {
        "city": "New York",
        "country": "USA"
      }
    }
  }
]
```

In the example above, `uppercase()` is a method called on `person.name` to convert it to uppercase. Although this method is called as `.uppercase()`, it is actually the [`string::uppercase()`🚫][brakuje_func_db_string#stringuppercase] function that is called.

SurrealDB will automatically recognize that the idiom part `.uppercase()` refers to the `string::uppercase()` function and call this function when the query is executed. What this means is that the following two queries are equivilent:

```surql title="Using method chaining"
SELECT *, name.uppercase() FROM person;
```

```surql title="Using function"
SELECT *, string::uppercase(name) FROM person;
```

To learn more about string method chaining in SurrealQL, see the [string functions🚫][brakuje_func_db_string#method-chaining] section.

### _q014f - **Graph Navigation**_

SurrealDB can also be used in the context of graph databases, where data is stored and navigated using graph traversal idioms. The [`RELATE` statement🚫][brakuje_stat_relate] is used to create relationships between records. This allows you to traverse related records efficiently without needing to pull data from multiple tables and merging that data together using SQL JOINs.

For example, let's consider the following data:

```surql title="Create a new planet, city, and explorer records"
/**[test]

[[test.results]]
value = "[{ id: planet:unknown_planet }]"

[[test.results]]
value = "[{ id: city:el_dorado, name: 'El Dorado' }]"

[[test.results]]
value = "[{ id: explorer:drake, name: 'Drake' }]"

[[test.results]]
value = "[{ id: explorer:local_guide, name: 'Local Guide' }]"

[[test.results]]
value = "[{ id: discovered:4y6p19onn8a0zlgf80rg, in: explorer:drake, out: planet:unknown_planet }]"
skip-record-id-key = true

[[test.results]]
value = "[{ id: visited:lnjo8yonp28501y75slq, in: explorer:drake, out: city:el_dorado }]"
skip-record-id-key = true

[[test.results]]
value = "[{ id: assisted:5cr7hphseo7t2m87yhwd, in: explorer:local_guide, out: explorer:drake }]"
skip-record-id-key = true

*/

CREATE planet:unknown_planet;
CREATE city:el_dorado          SET name = "El Dorado";
CREATE explorer:drake          SET name = "Drake";
CREATE explorer:local_guide    SET name = "Local Guide";

RELATE explorer:drake->discovered->planet:unknown_planet;
RELATE explorer:drake->visited->city:el_dorado;
RELATE explorer:local_guide->assisted->explorer:drake;

```

```surql title="Retrieve all relationships from Drake"
SELECT 
    *,
    ->? AS actions,
    <-? AS was,
    <->? AS involved_in
FROM explorer:drake;
```

```surql title="Response"
[
  {
    actions: [
      discovered:sh9zbsz5u705cxv6qgoi,
      visited:hmtttiqqfa4mt9is1a7j
    ],
    involved_in: [
      assisted:1pv8k3p1wpuf0guf5bvm,
      discovered:sh9zbsz5u705cxv6qgoi,
      visited:hmtttiqqfa4mt9is1a7j
    ],
    id: explorer:drake,
    was: [
      assisted:1pv8k3p1wpuf0guf5bvm
    ],
    name: 'Drake'
  }
]
```

Explanation:

- `*`: Selects all fields of `explorer:drake`.
- `->? AS actions`: Retrieves all outgoing relationships from Drake and aliases them as actions.
- `<-? AS was`: Retrieves all incoming relationships to Drake and aliases them as was.
- `<->? AS involved_in`: Retrieves all relationships connected to Drake, regardless of direction, and aliases them as `involved_in`.

### _q014g - **Destructuring**_

> Available since: v2.0.0

When working with nested data, you can destructure objects using the `.` and `{ ... }` idioms.

For example,

```surql title="Create a new person record"
/**[test]

[[test.results]]
value = "[{ age: 21, id: person:1, name: 'John', obj: { a: 1, b: 2, c: { d: 3, e: 4, f: 5 } } }]"

*/


CREATE person:1 SET name = 'John', age = 21, obj = { a: 1, b: 2, c: { d: 3, e: 4, f: 5 } };
```

```surql title="Response"
[
  {
    age: 21,
    id: person:1,
    name: 'John',
    obj: {
      a: 1,
      b: 2,
      c: {
        d: 3,
        e: 4,
        f: 5
      }
    }
  }
]
```

```surql
SELECT obj.{ a, c.{ e, f } } FROM ONLY person:1;
```

```surql title="Response"
{
  obj: {
    a: 1,
    c: {
      e: 4,
      f: 5
    }
  }
}
```

You can also OMIT fields that you don't want to destructure using the `OMIT` clause.

```surql
SELECT * OMIT obj.c.{ d, f } FROM ONLY person:1;
```

```surql title="Response"
[
  {
    age: 21,
    id: person:1,
    name: 'John',
    obj: {
      a: 1,
      b: 2,
      c: {
        e: 4
      }
    }
  }
]
```

Extending the example in the [Graph Navigation][SurrealQL014f_DataTypes_Idioms_GraphNavigation] section, we can use the `->` idiom to navigate through the graph and destructure the `city` field.

```surql
SELECT ->visited->city.{name, id}
FROM explorer:drake;
```

```surql title="Response"
[
  {
    "->visited": {
      "->city": [
        {
          id: city:el_dorado,
          name: 'El Dorado'
        }
      ]
    }
  }
]
```

#### _q014g1 - **Using aliases when destructuring**_

The keyword `AS` is necessary inside `SELECT` statements when [using an alias🚫][brakuje_stat_select#basic-usage] (a new name for a field).

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "{ location: (50, -5.4), num_people: 500 }"

*/


LET $town = {
    location: (50.0, -5.4),
    population: 500
};

SELECT 
  location,
  population AS num_people
FROM ONLY $town;
```

```surql title="Output"
{
  location: (50, -5.4),
  num_people: 500
}
```

However, as destructuring involves defining the output shape of a new object, no `AS` keyword is needed. Instead, only the names of the fields are needed. Aliasing is done by choosing a new name, a `:` (colon) and the path to the value.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "{ location: (50, -5.4), num_people: 500 }"

*/

LET $town = {
    location: (50.0, -5.4),
    population: 500
};

RETURN $town.{
    location,
    num_people: population
};
```

Conceptually, this is somewhat close to a `RETURN` statement.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "{ location: (50, -5.4), num_people: 500 }"

*/

LET $town = {
    location: (50.0, -5.4),
    population: 500
};

RETURN {
    location: $town.location,
    num_people: $town.population,
};
```

#### _q014g2 - **Destructuring the current item in a SELECT query**_

> Available since: v2.1.0

The current record in a `SELECT` query can be accessed and destructured using the `@` operator.

```surql
/**[test]

[[test.results]]
value = "[{ id: star:sun, name: 'The Sun' }]"

[[test.results]]
value = "[{ id: planet:earth, name: 'Earth' }]"

[[test.results]]
value = "[{ id: planet:earth, name: 'Earth', orbits: [star:sun] }]"
skip-record-id-key = true

[[test.results]]
value = "[{ id: planet:earth, name: 'Earth', orbits: [star:sun] }]"

[[test.results]]
value = "[{ id: planet:earth, name: 'Earth', orbits: [star:sun] }]"

*/

, [{ id: planet:earth, name: 'Earth', orbits: [star:sun] }]]
CREATE star:sun SET name = "The Sun";
CREATE planet:earth SET name = "Earth";
RELATE planet:earth->orbits->star:sun;

-- Regular SELECT query
SELECT 
    name,
    id,
    ->orbits->star AS orbits
FROM planet;

-- SELECT query using `@` and destructuring
SELECT @.{
    name,
    id,
    orbits: ->orbits->star
} FROM planet;
```

While the difference between the two methods is often cosmetic - aside from the note on aliases mentioned just above - using `@` to access the current record does lead to a different style of query that may be preferable. While a regular `SELECT` query first returns an array of results that can then be operated on, a `SELECT` query that uses `@` to access the current record can perform these operations first.

```surql
-- Use the .values() method to turn each record into
-- an array of values, then return all inside an array
SELECT @.{
    name,
    id,
    orbits: ->orbits->star
}.values()
    FROM planet;

-- Grab all records first, then use .map() to convert
-- each one into an array of values
(SELECT 
    name,
    id,
    ->orbits->star AS orbits
FROM planet)
    .map(|$obj| $obj.values());
```

Most importantly, however, the `@` operator is often necessary when using [recursive paths][SurrealQL014j_DataTypes_Idioms_RecursivePaths].

#### _q014g3 - **Using expressions while destructuring**_

> Available since: v3.0.0

While the fields inside a destructuring operation have always been accessible, expressions were not. As of version `3.0.0.beta`, this limitation no longer exists.

```surql
/**[test]

[[test.results]]
value = "[{ id: person:one, name: 'Aeon' }]"

[[test.results]]
value = "{ accessed_at: d'2025-10-02T06:18:26.751462Z', name: 'Aeon', name_length: 4 }"
skip-datetime = true

*/

CREATE person:one SET name = "Aeon";

person:one.{
    name,
  -- worked because 'name' can be accessed
    name_length: name.len(),
  -- an expression: did not work before, works now
    accessed_at: time::now()
};
```

```surql title="Output"
{
  accessed_at: d'2025-04-24T05:11:20.101Z',
  name: 'Aeon',
  name_length: 4
}
```

Expressions inside a destructuring operation have the same [predefined parameters🚫][brakuje_parameters#parent-this] as any other expression, such as `$this` to the current object and `$parent` to the previous one.

```surql
/**[test]

[[test.results]]
value = "[{ age: 18, id: person:one }]"

[[test.results]]
value = "[{ age: 40, id: person:two }]"

[[test.results]]
value = "[{ age: 18, id: person:three }]"

[[test.results]]
value = "{ age: 18, id: person:one, same_age: [{ age: 18, id: person:one }, { age: 18, id: person:three }] }"

[[test.results]]
value = "{ age: 18, id: person:one, same_age: [{ age: 18, id: person:three }] }"

*/

CREATE person:one SET age = 18;
CREATE person:two SET age = 40;
CREATE person:three SET age = 18;

-- Find all 'person' records of the same age as 'person:one'
-- Here 'person:one' is the $parent of the inner operation
person:one.{
  id,
    age,
    same_age: SELECT * FROM person WHERE age = $parent.age
};

-- Now use array::complement to filter out the 'person:one' current record,
-- which is the parameter $this
person:one.{
  id,
    age,
    same_age: array::complement(SELECT * FROM person WHERE age = $parent.age, [$this])
};
```

```surql title="Output"
-------- Query --------

{
  age: 18,
  id: person:one,
  same_age: [
    {
      age: 18,
      id: person:one
    },
    {
      age: 18,
      id: person:three
    }
  ]
}

-------- Query --------

{
  age: 18,
  id: person:one,
  same_age: [
    {
      age: 18,
      id: person:three
    }
  ]
}
```

### _q014h - **Optional Parts**_

> Available since: v2.0.0

---

> [!NOTE]
> Until SurrealDB 3.0.0-beta, this operator was a single `?` question mark. Since this version, it was changed to `.?` to avoid conflicts with the `??` operator when parsing.

The `.?` operator is used to indicate that a part is optional (it may not exist) it also allows you to safely access nested data without having to check if the nested data exists and exit an idiom path early when the result is NONE.

```surql
SELECT person.spouse.?.name FROM person;
```

This idiom safely accesses `person.spouse.name` if `spouse` exists; otherwise, it returns `NONE`.

### _q014i - **Using Optional Parts**_

If some `person` records have a `spouse` field and others do not:

```surql
SELECT name, spouse.?.name AS spouse_name FROM person;
```

This idiom will return `NONE` for `spouse_name` if the `spouse` field is not present.

### _q014j - **Recursive paths**_

> Available since: v2.1.0

A recursive path allows record link or graph traversal down to a specified depth, as opposed to manually putting together a query to navigate down each level.

Using recursive graph traversal can be thought of as the equivalent of "show me all the third-generation descendants of Mr. Brown" as opposed to "show me the children and children's children and children's children's children of Mr. Brown".

The following shows a recursive query that returns the names of people known by records that the record `person:tobie` knows.

```surql
-- Get all names of people second to Tobie
person:tobie.{2}(->friends_with->person).name;
```

As the syntax of recursive queries tends to be complex to the untrained eye, this section will explain them in order of difficulty, beginning with what queries were necessary before recursive paths were added in SurrealDB version 2.1.

#### _q014j1 - **Overview**_

Take the following example that creates one planet, two countries, two states/provinces in each of these countries, and two cities in each of those states/provinces. The `CREATE` statements are followed by `UPDATE` statements to set record links between them, and `RELATE` to create bidirectional graph relations between them.

```surql
CREATE
  // One planet
  planet:earth,
  // Two countries
  country:us, country:canada,
  // Four states/provinces
  state:california, state:texas,
  province:ontario, province:bc,
  // Eight cities
  city:los_angeles, city:san_francisco,
  city:houston,     city:dallas,
  city:vancouver,   city:victoria,
  city:toronto,     city:ottawa
  // Give them each names like 'earth', 'us', 'bc', etc.
  SET name = id.id();

// Record and graph links from planet to country
UPDATE planet:earth     SET next = [country:us, country:canada];
RELATE planet:earth     ->has->    [country:us, country:canada];

// Record and graph links from country to state/province
UPDATE country:us       SET next = [state:california, state:texas];
UPDATE country:canada   SET next = [province:ontario, province:bc];
RELATE country:us       ->has->    [state:california, state:texas];
RELATE country:canada   ->has->    [province:bc, province:ontario];

// Record and graph links from state/province to city
UPDATE state:california SET next = [city:los_angeles, city:san_francisco];
UPDATE state:texas      SET next = [city:houston, city:dallas];
UPDATE province:ontario SET next = [city:toronto, city:ottawa];
UPDATE province:bc      SET next = [city:vancouver, city:victoria];
RELATE state:california ->has->    [city:los_angeles, city:san_francisco];
RELATE state:texas      ->has->    [city:houston, city:dallas];
RELATE province:bc      ->has->    [city:vancouver, city:victoria];
RELATE province:ontario ->has->    [city:toronto, city:ottawa];
```

While traversing each of these paths can be done manually, it requires a good deal of typing and knowing the exact depth to traverse.

Here is an example using record links:

```surql
SELECT 
  next AS countries,
  next.next AS states_provinces,
  next.next.next AS cities
FROM planet:earth;
```

```surql title="Response"
[
  {
    cities: [
      [
        [
          city:los_angeles,
          city:san_francisco
        ],
        [
          city:houston,
          city:dallas
        ]
      ],
      [
        [
          city:toronto,
          city:ottawa
        ],
        [
          city:vancouver,
          city:victoria
        ]
      ]
    ],
    countries: [
      country:us,
      country:canada
    ],
    states_provinces: [
      [
        state:california,
        state:texas
      ],
      [
        province:ontario,
        province:bc
      ]
    ]
  }
]
```

And here is an example using graph links.

```surql
SELECT 
  -- Show all `country` records located at `out`
  ->has->country AS countries,
  -- Show all `province` or `state` records located at `out`  
  ->has->country->has->(province, state) AS state_provinces,
  -- Or use (?) to show any type of record located at `out`
  ->has->(?)->has->(?)->has->(?) AS cities
FROM planet:earth;
```

```surql title="Output"
[
  {
    cities: [
      city:toronto,
      city:ottawa,
      city:vancouver,
      city:victoria,
      city:dallas,
      city:houston,
      city:los_angeles,
      city:san_francisco
    ],
    countries: [
      country:canada,
      country:us
    ],
    state_provinces: [
      province:ontario,
      province:bc,
      state:texas,
      state:california
    ]
  }
]
```

#### _q014j2 - **Basics of recursive paths**_

Using a recursive path allows you to instead set the number of steps to follow instead of manually typing. A recursive path is made by isolating `{}` braces in between two dots, inside which the number of steps is indicated.

```surql
-- Two steps down the record links at the `next` field
planet:earth.{2}.next;
-- Two steps down the `has` graph relation
planet:earth.{2}->has->(?);
```

```surql title="Output"
[
  state:california,
  state:texas,
  province:ontario,
  province:bc
]
```

The number of steps can be any integer from 1 to 256.

```surql
-- 'Found 0 for bound but expected at least 1.'
planet:earth.{0}->has->(?);
-- 'Found 500 for bound but expected 256 at most.'
planet:earth.{500}->has->(?);
```

A range can be inserted into the braces to indicate a desired minimum and maximum depth.

```surql
-- Returns [] because no 4th-level relations exist
planet:earth.{4}->has->(?);
-- Returns `city` records located at depth 3
planet:earth.{1..4}->has->(?);
-- Open-ended range: also returns `city` records at depth 3
planet:earth.{..}->has->(?);
```

```surql title="Output"
[
  city:toronto,
  city:ottawa,
  city:vancouver,
  city:victoria,
  city:dallas,
  city:houston,
  city:los_angeles,
  city:san_francisco
]
```

#### _q014j3 - **Using () to provide instructions at each depth**_

Parentheses can be added to a recursive query. To explain their use, consider the following example that attempts to traverse up to a depth of 3 and return the `name` of the records at that level.

```surql
planet:earth.{1..3}->has->(?).name;
```

Unfortunately, the output shows that the query stopped at a depth of one. This is because the query is instructing the database to recurse the entire `->has->(?).name` path between 1 and 3 times, but after the first recursion it has reached a string. And a string on its own is of no use in a `->has->(?)` graph query which expects a record ID.

```surql title="Output"
[
  'canada',
  'us'
]
```

In fact, the above query is equivalent to the following statement which encloses `->has->(?).name` in parentheses.

```surql
planet:earth.{1..3}(->has->(?).name);
```

To make the query work, we can shrink the area enclosed in the parentheses to `->has->(?)`, isolating the part to recurse before moving on to `.name`. It will repeat as many times as instructed and only then move on to the `name` field.

```surql
planet:earth.{1..3}(->has->(?)).name;
```

```surql title="Output"
[
  'toronto',
  'ottawa',
  'vancouver',
  'victoria',
  'dallas',
  'houston',
  'los_angeles',
  'san_francisco'
]
```

The syntax for the query above can be broken down as follows.

```surql
-- starting point
planet:earth
-- desired depth
  .{1..3}
-- instructions for current document
  (->has->(?))
-- leftover idiom path
  .{name, id};
```

#### _q014j4 - **Using `@` to refer to the current record**_

The `@` symbol is used in recursive queries to refer to the current document. This is needed in recursive `SELECT` queries, as without it there is no way to know the context.

```surql title="Unparsable queries"
-- Parse error: what is the `.` referring to?
-- DB: "Call recursive query on a `planet`? Its `name` field? Something else?"
SELECT .{1..3}(->has->(?)) FROM planet;

-- A similar query that can't be parsed
-- DB: "Call .len() on what?"
SELECT .len() FROM planet;
```

Adding `@` allows the parser to know that the current `planet` record is the starting point for the rest of the query.

```surql title="Parsable queries"
-- Will now call `.{1..3}(has->(?))` on every planet record it finds
SELECT @.{1..3}(->has->(?)) AS cities FROM planet;
-- Will now call `.len()` on every `name` field it finds
SELECT name.len()           AS length FROM planet;
```

#### _q014j5 - **Using `{}` and `.@` to combine results**_

Inside the structure of a recursive graph query, the `@` symbol is used in the form of `.@` at the end of a path to inform the database that this is the path to be repeated during the recursion. This allows not just the fields on the final depth of the query to be returned, but each one along the way as well.

```surql
planet:earth
  .{1..2}
  .{
    name, 
    id,
-- Query with ->has->(?) on the current record
    contains: ->has->(?).@
  };
```

```surql title="Output"
{
  contains: [
    {
      contains: [
        province:ontario,
        province:bc
      ],
      id: country:canada,
      name: 'canada'
    },
    {
      contains: [
        state:texas,
        state:california
      ],
      id: country:us,
      name: 'us'
    }
  ],
  id: planet:earth,
  name: 'earth'
}
```

The following two rules of thumb are a good way to understand how the syntax inside the structure of the query.

- The individual fields inside a recursive query are simply populated at each point,
- The field with `.@` is used as the gateway to the next depth.

To see this visually, here is the unfolded output of the query above. The `name` and `id` fields appear at each point, while `contains` is used to move on to the next depth.

```surql
-- Original query
planet:earth.{1..2}.{ name, id, contains: ->has->(?).@ };

-- Unfolds to:
planet:earth
  .{
    name, 
    id,
    contains: ->has->(?).{
      name, 
      id,
      contains: ->has->(?)
      }
  };
```

Similarly, only one `.@` can be present inside such a query, as this is the path that is used to follow the recursive query until the end.

```surql
planet:earth
  .{1..2}
  .{
    name, 
    id,
-- Query with ->has->(?) on the current record
    contains: ->has->(?).@,
        contains2: ->has->(?).@
  };
```

```surql
'Tried to use a `@` repeat recurse symbol in a position where it is not supported'
```

Here are some more simple examples of recursive queries and notes on the output they generate.

```surql
/**[test]

[[test.results]]
value = "[{ friends: [person:jaime, person:micha], id: person:tobie, name: 'Tobie' }, { friends: [person:mary], id: person:jaime, name: 'Jaime' }, { friends: [person:john], id: person:micha, name: 'Micha' }, { id: person:john, name: 'John' }, { id: person:mary, name: 'Mary' }, { id: person:tim, name: 'Tim' }]"

[[test.results]]
value = "[{ id: knows:1, in: person:tobie, out: person:jaime }, { id: knows:2, in: person:tobie, out: person:micha }, { id: knows:3, in: person:micha, out: person:john }, { id: knows:4, in: person:jaime, out: person:mary }, { id: knows:5, in: person:mary, out: person:tim }]"

[[test.results]]
value = "['Tim']"

[[test.results]]
value = "['Tim']"

[[test.results]]
value = "['Tim']"

[[test.results]]
value = "['Tim']"

[[test.results]]
value = "{ connections: [{ connections: [{ connections: [{ connections: [], id: person:tim, name: 'Tim' }], id: person:mary, name: 'Mary' }], id: person:jaime, name: 'Jaime' }, { connections: [{ connections: [], id: person:john, name: 'John' }], id: person:micha, name: 'Micha' }], id: person:tobie, name: 'Tobie' }"

[[test.results]]
value = "[{ names_2nds: ['Tim'] }, { names_2nds: [] }, { names_2nds: ['Tim'] }, { names_2nds: ['John'] }, { names_2nds: [] }, { names_2nds: ['Tim'] }]]"

[[test.results]]
value = ""

*/

INSERT INTO person [
  { id: person:tobie, name: 'Tobie', friends: [person:jaime, person:micha] },
  { id: person:jaime, name: 'Jaime', friends: [person:mary] },
  { id: person:micha, name: 'Micha', friends: [person:john] },
  { id: person:john, name: 'John' },
  { id: person:mary, name: 'Mary' },
  { id: person:tim, name: 'Tim' },
];

INSERT RELATION INTO knows [
  { id: knows:1, in: person:tobie, out: person:jaime },
  { id: knows:2, in: person:tobie, out: person:micha },
  { id: knows:3, in: person:micha, out: person:john },
  { id: knows:4, in: person:jaime, out: person:mary },
  { id: knows:5, in: person:mary, out: person:tim },
];

-- Any depth
person:tobie.{..}(->knows->person).name;

-- Minimum 2, maximum 5 iterations of recursion (or either)
person:tobie.{2..6}(->knows->person).name;
person:tobie.{2..}(->knows->person).name;
person:tobie.{..6}(->knows->person).name;

-- Generate complex recursive tree structures:
-- Fetches connections up to 3 levels deep, 
-- collecting their name, id, and connections along the way
-- 3 levels, because the first iteration is used to collect
-- the details for person:tobie
person:tobie.{..4}.{ id, name, connections: ->knows->person.@ };

-- @ is a shortcut to the current document, and acts as a shorthand to start an idiom path.
-- The "." can optionally be omitted
SELECT @{1..4}(->knows->person).name AS names_2nds FROM person;

-- Recursive idioms work with any idiom parts, not limited to graphs
-- Here, we recursively fetch friends and then collect their names
person:tobie.{1..5}(.friend).name;
```

#### _q014j6 - **Behaviour of recursive queries**_

Recursive queries follow a few rules to determine how far to traverse and what to return. They are:

- `NONE`, `NULL`, and arrays which are empty or contain only `NONE` and/or `NULL` are considered a dead end.
- An iteration with the same value as the previous one is also considered a dead end.
- If an iteration with a dead end does not reach the minimum depth, it returns `NONE`.
- If it has already passed the minimum depth, it returns the last valid value.
- During each iteration, if it encounters an array value, all dead end values are automatically filtered out, ensuring no empty paths are included.

#### _q014j7 - **Filtering recursive fields**_

Recursive syntax is not just useful in creating recursive queries, but parsing them as well. Take the following example that creates some `person` records, gives each of them two friends, and then traverses the `friends_with` graph for the first `person` records to find its friends, friends of friends, and friends of friends of friends. Since every level except the last contains another `connections` field, adding a `.{some_number}.connections` to a `RETURN` statement is all that is needed to drill down to a certain depth.

```surql
CREATE |person:1..21| SET name = id.id() RETURN NONE;
FOR $person IN SELECT * FROM person {
    LET $friends = (SELECT * FROM person WHERE id != $person.id ORDER BY rand() LIMIT 2);
    RELATE $person->friends_with->$friends;
};

LET $third_degree = person:1.{..3}.{ id, connections: ->friends_with->person.@ };
// Object containing array of arrays of arrays of 'person'
RETURN $third_degree;
// All connections: an array of arrays of arrays of 'person'
RETURN $third_degree.connections;
// Secondary connections: an array of arrays of 'person'
RETURN $third_degree.{2}.connections;
// Tertiary connections: an array of 'person'
RETURN $third_degree.{3}.connections;
// Tertiary connections with aliased fields and original 'person' info
RETURN $third_degree.{
    original_person: id, 
    third_degree_friends: connections.{2}.connections
};
```

Possible output of the final query:

```surql title="Output for third_degree_friends query"
{
  original_person: person:1,
  third_degree_friends: [
    person:13,
    person:3,
    person:14,
    person:10,
    person:8,
    person:3,
    person:3,
    person:14
  ]
}
```

#### _q014j8 - **Path and unique node collection, shortest path**_

> Available since: v2.2.0

SurrealDB has a number of built-in algorithms that allow recursive queries to collect all paths, all unique nodes, and to find the shortest path to a record. These can be used by adding the following keywords to the part of the recursive syntax that specifies the depth to recurse:

- `{..+path}`: used to collect all walked paths.
- `{..+collect}`: used to collect all unique nodes walked.
- `{..+shortest=record:id}`: used to find the shortest path to a specified record id, such as `person:tobie` or `person:one`.

The originating (first) record is excluded from these paths by default. However, it can be included by adding `+inclusive` to the syntax above.

- `{..+path+inclusive}`
- `{..+collect+inclusive}`
- `{..+shortest=record:id+inclusive}`

To demonstrate the output of these three algorithms, take the following example showing a small network of friends. The network begins with `person:you`, followed by two friends (`person:friend1`, `person:friend2`), then three acquaintances known by these friends (`person:acquaintance1`, `person:acquaintance2`, `person:acquaintance3`), and finally a movie star (`person:star`) who is known by only one of the acquaintances.

```surql
/**[test]

[[test.results]]
value = "[{ id: person:you, name: 'you' }, { id: person:friend1, name: 'friend1' }, { id: person:friend2, name: 'friend2' }, { id: person:acquaintance1, name: 'acquaintance1' }, { id: person:acquaintance2, name: 'acquaintance2' }, { id: person:acquaintance3, name: 'acquaintance3' }, { id: person:star, name: 'star' }]"

[[test.results]]
value = "[{ id: knows:i8twxf1ghl053391z54j, in: person:you, out: person:friend1 }, { id: knows:071ho0yn3tol4kgwu0fn, in: person:you, out: person:friend2 }]"
skip-record-id-key = true

[[test.results]]
value = "[{ id: knows:8fnyab57dotlu2572uc8, in: person:friend1, out: person:friend2 }]"
skip-record-id-key = true

[[test.results]]
value = "[{ id: knows:0u34elv08i9ci7igim0f, in: person:friend2, out: person:acquaintance1 }, { id: knows:hgosmpddbv6nuohsgj8p, in: person:friend2, out: person:acquaintance2 }, { id: knows:c04oc5168ubocheihbtu, in: person:friend2, out: person:acquaintance3 }]"
skip-record-id-key = true

[[test.results]]
value = "[{ id: knows:d0s3lq6ynweqaryh567o, in: person:acquaintance3, out: person:star }]"
skip-record-id-key = true

*/

CREATE 
  person:you, 
  person:friend1, person:friend2, 
  person:acquaintance1, person:acquaintance2, person:acquaintance3, 
  person:star
-- Give each of them a name like 'you', 'friend1', etc.
SET name = id.id();

-- You have two friends
RELATE person:you->knows->[person:friend1, person:friend2];
-- The first friend is shy and only knows one other person
RELATE person:friend1->knows->person:friend2;
-- The second friend is very social and knows many people you barely know
RELATE person:friend2->knows->[person:acquaintance1, person:acquaintance2, person:acquaintance3];
-- One of those people knows the movie star
RELATE person:acquaintance3->knows->person:star;
```

This representation of this small network of friends allows us to visualize the issues that these three algorithms solve. Using `+path` will output all of the possible paths from `person:you`, `+collect` will collect all of the records in this network, and `+shortest=person:star` will find the shortest path.

```text

                  ┌───────►  person:friend1  
     ┌───►person:acquaintance1    │                                                                    
     │                │           │                                                
     │                │           ┼───►person:acquaintance2    person:star   
person:you            │           │                                 ▲        
     │                ▼           │                                 │        
     └────────► person:friend2────┤                                 │        
                                  └───►person:acquaintance3─────────┘                      

```

After specifying an algorithm to use, such as `{..+path}`, add the path that should be followed, in this case `->knows->person`.

#### _q014j9 - **+path**_

Adding `+path` will output all of the possible paths starting from `person:you`.

```surql
person:you.{..+path}->knows->person;
```

```surql title="Output"
[
  [
    person:friend2,
    person:acquaintance2
  ],
  [
    person:friend2,
    person:acquaintance1
  ],
  [
    person:friend1,
    person:friend2,
    person:acquaintance2
  ],
  [
    person:friend1,
    person:friend2,
    person:acquaintance1
  ],
  [
    person:friend2,
    person:acquaintance3,
    person:star
  ],
  [
    person:friend1,
    person:friend2,
    person:acquaintance3,
    person:star
  ]
]
```

##### _q014j9a - **+shortest**_

As the output of the previous example is fairly short, we can see that there are two ways to get from `person:one` to the movie star at `person:star`, one of which is one step shorter than the other.

To get the database to find the shortest path instead, change the algorithm to `+shortest=person:star`.

```surql
person:you.{..+shortest=person:star}->knows->person;
```

```surql title="Output"
[
  person:friend2,
  person:acquaintance3,
  person:star
]
```

The part after `+shortest` can also take a parameter if it is a record ID. The following example will return the same result as the previous one.

```surql
LET $you = SELECT VALUE id FROM ONLY person WHERE name = 'you' LIMIT 1;
LET $star = SELECT VALUE id FROM ONLY person WHERE name = 'star' LIMIT 1;
$you.{..+shortest=$star}->knows->person;
```

##### _q014j9b - **+collect**_

Using `+collect` will collect all of the unique collected records. As this collection is created by moving recursively one level at a time, the output will show the closest connections first and least close connections at the end.

```surql
person:you.{..+collect}->knows->person;
```

```surql title="Output"
[
  person:friend1,
  person:friend2,
  person:acquaintance2,
  person:acquaintance1,
  person:acquaintance3,
  person:star
]
```

##### _q014j9c - **+inclusive**_

Adding `+inclusive` will show the same output, except that the original `person:one` record will also be present.

```surql
person:you.{..+shortest=person:star+inclusive}->knows->person;
person:you.{..+collect+inclusive}->knows->person;
```

```surql title="Output"
-------- Query --------

[
  person:you,
  person:friend2,
  person:acquaintance3,
  person:star
]

-------- Query --------

[
  person:you,
  person:friend1,
  person:friend2,
  person:acquaintance2,
  person:acquaintance1,
  person:acquaintance3,
  person:star
]
```

##### _q014j9d - **Other notes**_

The unbounded syntax `..` can be replaced with a bounded range to ensure that the recursive query only goes down to a certain depth. For example, using `..2` with `+collect` will show all first- and second-degree relations starting from `person:you`:

```surql
person:you.{..2+collect}->knows->person;
```

```surql title="All first- and second-degree relations"
[
  person:friend1,
  person:friend2,
  person:acquaintance2,
  person:acquaintance1,
  person:acquaintance3
]
```

Doing the same with `+shortest=person:star` will return an empty array, because there is no path from `person:you` to `person:star` that only requires two hops.

```surql
person:you.{..2+shortest=person:star}->knows->person;
```

```surql title="Output"
[]
```

As shown in [a previous section][SurrealQL014j3_DataTypes_Idioms_RecursivePathsProvideInstructions], parentheses can be used to show which path should be repeated during the recursion. After the path inside the parentheses, the destructuring operator, methods and so on can be used to modify the output. The query can also be written over multiple lines if desired.

```surql
-- Start with you
person:you
-- Get the shortest path
  .{..+shortest=person:star+inclusive}
-- by following ->knows->person
  (->knows->person)
-- then grab the names
  .name
-- and capitalize each one
  .map(|$n| $n.uppercase());
```

```surql title="Output"
[
  'YOU',
  'FRIEND2',
  'ACQUAINTANCE3',
  'STAR'
]
```

##### _q014j9e - **Do not use `.@` with algorithms**_

As these three methods use their own algorithms to follow a path, any attempt to construct your own path using `.@` will result in an error. For example, choosing `+path` along with a field `connections: ->knows->person.@` will return an error because `+path` on its own will use its own recursive planner to output every possible path as an array of arrays, while `->knowns->person.@` is an instruction to put together arrays of each record and the next result from the `->knows->person` path at any possible depth.

```surql
person:you.{..+path}.{
    id,
    connections: ->knows->person.@
};
```

```surql
'Can not construct a recursion plan when an instruction is provided'
```

Here is the output of both of these queries at a single depth to show the difference in output.

```surql
person:you.{..1}.{
    id,
    connections: ->knows->person.@
};

person:you.{..1+path}->knows->person;
```

```surql title="Output"
-------- Query --------

{
  connections: [
    person:friend2,
    person:friend1
  ],
  id: person:you
}

-------- Query --------

[
  [
    person:friend2
  ],
  [
    person:friend1
  ]
]
```

##### _q014j9f - **Example using record links**_

As is the case with other recursive queries, these three algorithms can be used in the same way with any other path that can be repeated, such as record links. The following example shows the same network of friends as the one above, except that it uses record links instead of graph queries. To traverse these paths, a simple `.knows` is all that is required.

```surql
/**[test]

[[test.results]]
value = "[{ id: person:you, knows: [person:friend1, person:friend2] }]"

[[test.results]]
value = "[{ id: person:friend1, knows: [person:friend2] }]"

[[test.results]]
value = "[{ id: person:friend2, knows: [person:acquaintance1, person:acquaintance2, person:acquaintance3] }]"

[[test.results]]
value = "[{ id: person:acquaintance1 }, { id: person:acquaintance2 }, { id: person:star }]"

[[test.results]]
value = "[{ id: person:acquaintance3, knows: [person:star] }]"

[[test.results]]
value = "[person:friend2, person:acquaintance3, person:star]"

[[test.results]]
value = "[[person:friend2, person:acquaintance1], [person:friend2, person:acquaintance2], [person:friend1, person:friend2, person:acquaintance1], [person:friend1, person:friend2, person:acquaintance2], [person:friend2, person:acquaintance3, person:star], [person:friend1, person:friend2, person:acquaintance3, person:star]]"

[[test.results]]
value = "[person:friend1, person:friend2, person:acquaintance1, person:acquaintance2, person:acquaintance3, person:star]"

*/

CREATE person:you SET knows = [person:friend1, person:friend2];
CREATE person:friend1 SET knows = [person:friend2];
CREATE person:friend2 SET knows = [person:acquaintance1, person:acquaintance2, person:acquaintance3];
CREATE person:acquaintance1, person:acquaintance2, person:star;
CREATE person:acquaintance3 SET knows = [person:star];

person:you.{..+shortest=person:star}.knows;
person:you.{..+path}.knows;
person:you.{..+collect}.knows;
```

### _q014k - **Combining Idiom Parts**_

Idioms can combine multiple parts to navigate complex data structures seamlessly.

Suppose we have the following data:

```surql title="Create a new person record"
/**[test]

[[test.results]]
value = "[{ friends: [{ age: 25, id: 'person:6', name: 'Frank' }, { age: 19, id: 'person:7', name: 'Grace' }, { age: 17, id: 'person:8', name: 'Heidi' }], id: person:5, name: 'Eve' }]"

*/

CREATE person:5 CONTENT {
    name: "Eve",
    friends: [
        {
            id: "person:6",
            name: "Frank",
            age: 25
        },
        {
            id: "person:7",
            name: "Grace",
            age: 19
        },
        {
            id: "person:8",
            name: "Heidi",
            age: 17
        }
    ]
};
```

```surql title="Response"
[
  {
    friends: [
      {
        age: 25,
        id: 'person:6',
        name: 'Frank'
      },
      {
        age: 19,
        id: 'person:7',
        name: 'Grace'
      },
      {
        age: 17,
        id: 'person:8',
        name: 'Heidi'
      }
    ],
    id: person:5,
    name: 'Eve'
  }
]
```

To get the names of friends who are over 18:

```surql
SELECT friends[WHERE age > 18].name FROM person WHERE id = person:5;
```

```surql title="Response"
[
  {
    friends: {
      name: [
        'Frank',
        'Grace'
      ]
    }
  }
]
```

### _q014l - **Notes on Idioms**_

- **Chaining**: Idioms can be chained to traverse deeply nested structures.
- **Performance**: Be mindful of performance when using complex idioms; indexing fields can help.
- **NONE Safety**: Use optional parts (`?`) to handle `NONE` or missing data gracefully.
- **Methods**: Leverage built-in methods for data manipulation within idioms.
- **Type Casting**: Use type casting if necessary to ensure data is in the correct format.

### _q014m - **Best Practices**_

- **Use Destructuring**: When selecting multiple fields, destructuring improves readability.
- **Limit Optional Parts**: Use optional parts judiciously to avoid masking data issues.
- **Validate Data**: Ensure data conforms to expected structures, especially when dealing with optional fields.
- **Index Fields**: Index fields that are frequently accessed or used in `WHERE` clauses for better performance.

### _q014n - **Summary**_

Idioms in SurrealQL are a powerful tool for navigating and manipulating data within your database. By understanding and effectively using idiom parts, you can write expressive and efficient queries that handle complex data structures with ease. Whether you're accessing nested fields, filtering arrays, or traversing graph relationships, idioms provide the flexibility you need to interact with your data seamlessly.

---
---

## _q015 - **Literals**_

- [📓][surrealdb_docs_3x_surrealql_datamodel_literals]

> Available since: V2.0.0

A literal is a value that may have multiple representations or formats, similar to an enum or a union type. A literal can be composed of strings, numbers, objects, arrays, or durations.

### _q015a - **Examples**_

A literal can be as simple as a declaration that a parameter must be a certain value.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
error = ""Tried to set `$nine`, but couldn't coerce value: Expected `9` but found `10`""

*/

LET $nine: 9 = 9;
LET $nine: 9 = 10;
```

```surql title="Response"
-------- Query --------

NONE

-------- Query --------

"Tried to set `$nine`, but couldn't coerce value: Expected `9` but found `10`"
```

Using `|` allows a literal to be a number of possible options.

```surql
/**[test]

[[test.results]]
error = ""Tried to set `$nine`, but couldn't coerce value: Expected `9 | '9' | 'nine'` but found `'Nein'`""

*/

LET $nine: 9 | "9" | "nine" = "Nein";
```

```surql title="Response"
"Tried to set `$nine`, but couldn't coerce value: Expected `9 | '9' | 'nine'` but found `'Nein'`"
```

A literal can contain possible types in addition to possible values.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "NONE"

*/

LET $flexible_param: datetime | uuid | "N/A" = "N/A";
LET $flexible_param: datetime | uuid | "N/A" = <datetime>"2024-09-01";
```

Literals that include the option to be an array or an object can contain rich data.

```surql
/**[test]

[[test.results]]
value = "NONE"

*/

LET $status: "Ok" | { err: string } = { err: "Forgot to plug it in" };
```

### _q015b - **Literals in database schema**_

Literals can be defined inside a database schema by using a [DEFINE FIELD🚫][brakuje_stat_def_field] statement.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "[{ error_info: { error: 'Deprecated', message: "You shouldn't use this anymore" }, id: information:obqulsqif466kp1t3agq }]"
skip-record-id-key = true

[[test.results]]
error = ""Couldn't coerce value for field `error_info` of `information:qbohn4wu4l2t81wj2fb3`: Expected `{ error: 'Continue' } | { error: 'RetryWithId', id: string } | { error: 'Deprecated', message: string }` but found `\"You shouldn't use this anymore\"`""

*/

DEFINE FIELD error_info ON TABLE information TYPE
      { error: "Continue" }
    | { error: "RetryWithId", id: string }
    | { error: "Deprecated", message: string };

CREATE information SET
  error_info = { error: "Deprecated", message: "You shouldn't use this anymore" };
-- Doesn't conform to definition, will not work
CREATE information SET
  error_info = "You shouldn't use this anymore";
```

```surql title="Response"
-------- Query --------

[
  {
    error_info: {
      error: 'Deprecated',
      message: "You shouldn't use this anymore"
    },
    id: info:pkckjrri8q1pg12unyuo
  }
]

-------- Query --------

"Couldn't coerce value for field `error_info` of `information:qbohn4wu4l2t81wj2fb3`: Expected `{ error: 'Continue' } | { error: 'RetryWithId', id: string } | { error: 'Deprecated', message: string }` but found `\"You shouldn't use this anymore\"`"
```

### _q015c - **Matching on literals**_

While SurrealQL does not have a `match` or `switch` operator, `IF ELSE` statements can be used to match on a literal, particularly if each possible type is an object. The following shows a similar example to the above except that each object begins with a field containing the name of the type of error.

```surql
/**[test]

[[test.results]]
value = "NONE"

*/

DEFINE FIELD error_info ON TABLE information TYPE
  { Continue:    { message: "" }} |
  { Retry: { error: "Retrying", after: duration }} |
  { Deprecated:  { message: string }};
```

Next, we will [define a function🚫][brakuje_stat_def_function] to handle this field and return a certain type of message depending on the error. Note the following:

- The `LET` statement in the first line is simply to shorten the path to the information contained inside `error_info`
- `IF ELSE` statement works here because [IF🚫][brakuje_stat_throw] involves a check for [truthiness][SurrealQL027b_DataTypes_ValuesTruthiness], returning `true` as long as it finds a value that is not none, empty, or zero.

```surql
/**[test]

[[test.results]]
value = "NONE"

*/

DEFINE FUNCTION fn::handle_error($data: record<information>) -> string {
  LET $err = $data.error_info;
  RETURN IF $err.Continue {
    "Continue"
  }
  ELSE IF $err.Retry {
    sleep($err.Retry.after);
    "Now retrying again"
  }
  ELSE IF $err.Deprecated {
    $err.Deprecated.message
  }
};
```

With the function set up, the `info` records can be inserted and run one at a time through the function.

```surql
LET $info = INSERT INTO information [
  { error_info: { Continue: { message: "" } }},
  { error_info: { Retry: { error: "Retrying", after: 1s } }},
  { error_info: { Deprecated: { message: "Thought I said you shouldn't use this anymore" } }}
];

fn::handle_error($info[0].id);
fn::handle_error($info[1].id);
fn::handle_error($info[2].id);
```

```surql title="Output"
-------- Query --------

'Continue'

-------- Query --------

-- After waiting 1 second
'Now retrying again'

-------- Query --------

"Thought I said you shouldn't use this anymore"
```

---
---

## _q016 - **None and null**_

- [📓][surrealdb_docs_3x_surrealql_datamodel_none-and-null]

SurrealDB uses two types called `None` and `Null` to represent two different ways in which data may not exist. While these may appear similar, they have different meanings and are used in different contexts.

### _q016a - **None values**_

`None` is used to denote that "something does not exist", for example, a field which is not present on a record.
Because of this, values of `None` can not be stored within records, meaning uses of `None` are typically limited to SurrealQL statements
where it is used to denote a value or response that does not exist.

#### _q016a1 - **Example**_

Setting a record field to `None` is analogous to using `UNSET` to remove the field entirely. While inside the query it may appear that `None` is being written to the `children` field, what is actually happening is that the `children` field is being removed from the record.

```surql
/**[test]

[[test.results]]
value = "[{ id: person:two }]"

[[test.results]]
value = "[{ children: [person:two], id: person:one }]"

[[test.results]]
value = "[{ id: person:one }]"

[[test.results]]
value = "[{ id: person:one }, { id: person:two }]"

*/

CREATE person:two;
CREATE person:one SET children = [person:two];
UPDATE person:one SET children = NONE;
SELECT * FROM person;
```

```surql title="Output"
[
  { id: person:one },
  { id: person:two }
]
```

### _q016b - **Null values**_

`Null` values are used to denote that "something exists, but has no value". This is useful when a field is present on a record, but the value of that field is unknown or not applicable. Unlike `None`, `Null` is written into records and can be stored as a value.

#### _q016b1 - **Example**_

Setting a record field to `Null` will create the field on the record, but denotes that the field is considered empty. In this example, the `children` field is present on the record, but the value of that field is `null`.

```surql
/**[test]

[[test.results]]
value = "[{ children: NULL, id: person:dgwjn0ldg8ep3e8y39jw }]"
skip-record-id-key = true

*/

CREATE person SET children = null;
```

```surql title="Output"
[
  { 
    children: NULL, 
    id: person:dgwjn0ldg8ep3e8y39jw
  }
]
```

### _q016c - **When to use None or Null**_

How you use `None` or `Null` is largely dependent on the context in which you are working.

If you are writing SurrealQL and need to denote something that does not exist, such as the absence of a field, use `None`.

If you are working with data and need to represent a value which is empty, use `Null`. This is particularly useful when needing to deserialize SurrealQL output into a type in another programming language that requires a field name to be present.

### _q016d - **NONE as a datatype**_

> Available since: V3.0.0

Since SurrealDB 3.0, NONE has been usable as a datatype of its own. This allows syntax like the following to be used without returning a parsing error.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "NONE"

[[test.results]]
value = "NONE"

*/

DEFINE FUNCTION fn::do_stuff() -> NONE {
  // Code that should return nothing
};

DEFINE FIELD middle_name ON TABLE user TYPE string | NONE; // Equivalent to option<string>

DEFINE FIELD value ON temperature TYPE float | decimal | NONE; // Equivalent to option<float|decimal>
```

---
---

## _q017 - **Numbers**_

- [📓][surrealdb_docs_3x_surrealql_datamodel_numbers]

In SurrealDB, numbers can be one of three types: 64-bit integers, 64-bit floating point numbers, or 128-bit decimal numbers.

### _q017a - **Integer numbers**_

If a numeric value is specified without a decimal point and is within the range `-9223372036854775808` to `9223372036854775807` then the value will be parsed, stored, and treated as a 64-bit integer.

```surql
/**[test]

[[test.results]]
value = "[{ id: event:j3tdh7wrm2kv1ymbbsek, year: 2022 }]"
skip-record-id-key = true

*/

CREATE event SET year = 2022;
```

### _q017b - **Floating point numbers**_

If a number value is specified with a decimal point, or is outside of the maximum range specified above, then the number will automatically be parsed, stored, and treated as a 64-bit floating point value. This ensures efficiency when performing mathematical calculations within SurrealDB.

```surql
/**[test]

[[test.results]]
value = "[{ id: event:5h756te17xakgdzfbghe, temperature: 41.5f }]"
skip-record-id-key = true

*/

CREATE event SET temperature = 41.5;
```

### _q017c - **Decimal numbers**_

To opt into 128-bit decimal numbers when specifying numeric values, you can use the `dec` suffix.

```surql
/**[test]

[[test.results]]
value = "[{ id: product:64vljvh12gdfwolgfhux, price: 99.99dec }]"
skip-record-id-key = true

*/

CREATE product SET price = 99.99dec;
```

The `dec` suffix is an instruction to the parser and not a cast, and is thus preferred when making a decimal.

```surql
/**[test]

[[test.results]]
value = "3.888888888888889dec"

[[test.results]]
value = "3.8888888888888888dec"

*/

-- Creates the imprecise float 3.888888888888889 and casts it into a decimal as 3.888888888888889dec
RETURN <decimal>3.8888888888888888;
-- Uses the input 3.8888888888888888 to directly create a decimal
RETURN 3.8888888888888888dec;
```

### _q017d - **Using a specific numeric type**_

To use a specific type when specifying numeric values, you can cast the value to a specific numeric type or use the appropriate suffix.

```surql
/**[test]

[[test.results]]
value = "[{ horizon: 34dec, id: event:8vpjsysxnskyfuh9ve87, temperature: 46.5f, year: 2022 }]"
skip-record-id-key = true

*/

CREATE event SET
  year = <int> 2022,
  temperature = <float> 41.5 + 5f,
  horizon = <decimal> 31 + 3dec
;
```

### _q017e - **Numeric precision**_

Different numeric types can be compared and used together in calculations.

The benefits of floating point numeric values are speed and storage size, but there is a limit to the numeric precision.

```surql
/**[test]

[[test.results]]
value = "13.571938471938472f"

*/

RETURN 13.5719384719384719385639856394139476937756394756;

-- 13.571938471938472f
```

In addition, when using floating point numbers specifically, mathematical operations can result in a loss of precision (as is normal with other databases).

```surql
/**[test]

[[test.results]]
value = "0.9999999999999999f"

*/

RETURN 0.3 + 0.3 + 0.3 + 0.1;

-- 0.9999999999999999f
```

Common rounding errors can be avoided by performing calculations using decimals.

```surql
/**[test]

[[test.results]]
value = "1.0dec"

*/

RETURN 0.3dec + 0.3dec + 0.3dec + 0.1dec;

-- 1.0dec
```

### _q017f - **Underscores**_

As a convenience, underscores are ignored when using a number. This allows input to be more readable than it would otherwise. Because underscores are ignored, they will not display in the output.

```surql
RELATE dr:evil->bribes->other:character SET dollars = 1_000_000.99;
-- [{ dollars: 1000000.99, id: bribes:4bfld2ukwnja24dzrpw9, in: dr:evil, out: other:character }]

-- Input Korean currency counted in units of 10000, not 1000
RELATE korean:purchaser->buys_house_from->korean:seller
              -- 10억 4천만 5천
    SET amount = 10_4000_5000;
-- [{ amount: 1040005000, id: buys_house_from:9070t2ctgwwg202cpw1z, in: korean:purchaser, out: korean:seller }]
```

### _q017g - **Mathematical constants**_

A set of floating point numeric constants are available in SurrealDB. Constant names are case insensitive, and can be specified with either lowercase or capital letters, or a mixture of both.

```surql
/**[test]

[[test.results]]
value = "[{ circumference: 10, id: circle:uvw3g4dli4x77xejcjej }]"
skip-record-id-key = true

[[test.results]]
value = "[{ circumference: 10, id: circle:uvw3g4dli4x77xejcjej, radius: 15.707963267948966f }]"
skip-record-id-key = true

*/

CREATE circle SET circumference = 10;
UPDATE circle SET radius = circumference / ( 2 * MATH::PI );
```

| Constant | Description | Value |
| :--- | :--- | :--- |
| `MATH::E` | Euler’s number (e) | 2.718281828459045 |
| `MATH::FRAC_1_PI` | 1/π | 0.3183098861837907 |
| `MATH::FRAC_1_SQRT_2` | 1/sqrt(2) | 0.7071067811865476 |
| `MATH::FRAC_2_PI` | 2/π | 0.6366197723675814 |
| `MATH::FRAC_2_SQRT_PI` | 2/sqrt(π) | 1.1283791670955126 |
| `MATH::FRAC_PI_2` | π/2 | 1.5707963267948966 |
| `MATH::FRAC_PI_3` | π/3 | 1.0471975511965979 |
| `MATH::FRAC_PI_4` | π/4 | 0.7853981633974483 |
| `MATH::FRAC_PI_6` | π/6 | 0.5235987755982989 |
| `MATH::FRAC_PI_8` | π/8 | 0.39269908169872414 |
| `MATH::INF` | Positive infinity | inf |
| `MATH::LN_10` | ln(10) | 2.302585092994046 |
| `MATH::LN_2` | ln(2) | 0.6931471805599453 |
| `MATH::LOG10_2` | log₁₀(2) | 0.3010299956639812 |
| `MATH::LOG10_E` | log₁₀(e) | 0.4342944819032518 |
| `MATH::LOG2_10` | log₂(10) | 3.321928094887362 |
| `MATH::LOG2_E` | log₂(e) | 1.4426950408889634 |
| `MATH::NEG_INF` | Negative infinity | -inf |
| `MATH::PI` | Archimedes’ constant (π) | 3.141592653589793 |
| `MATH::SQRT_2` | sqrt(2) | 1.4142135623730951 |
| `MATH::TAU` | The full circle constant (τ) | 6.283185307179586 |

### _q017h - **Next steps**_

You've now seen how to use numeric values in SurrealDB. For more advanced functionality, take a look at the operators and math functions, which enable advanced calculations on numeric values and sets of numeric values.

---
---

## _q018 - **Objects**_

- [📓][surrealdb_docs_3x_surrealql_datamodel_objects]

An object is a collection of named fields and values.

As a record is essentially an object with a required [`id` field][SurrealQL020_DataTypes_RecordIDs] that can be created, updated, or deleted, they can be worked with in almost exactly the same way as a standalone object.

A field of an object can be of any value type, including another object or array at multiple levels of depth. This allows objects and arrays to be stored within each other in order to model complex data scenarios.

```surql
/**[test]

[[test.results]]
value = "[{ id: person:ix25bwtvcx5s543eejrk, metadata: { activities: ['clicked link', 'contact form', 'read email', 'viewed website', 'viewed website', 'viewed website', 'read email'], information: { age: 23, gender: 'm' }, interest_level: 83.67f, marketing: true } }]"
skip-record-id-key = true

*/

CREATE person SET metadata = {
  interest_level: 83.67,
  information: {
    age: 23,
    gender: 'm',
  },
  marketing: true,
  activities: [
    "clicked link",
    "contact form",
    "read email",
    "viewed website",
    "viewed website",
    "viewed website",
    "read email",
  ]
};
```

### _q018a - **Field names**_

#### _q018a1 - **Valid field names**_

Similar to record IDs, field names can be constructed from ASCII characters, underscores, and numbers. To create a field name with complex characters, backticks can be used.

```surql
/**[test]

[[test.results]]
value = "{ id: user:3lgc83vechgblizli263, my_name: 'name' }"
skip-record-id-key = true

[[test.results]]
value = "{ id: user:nyzy7aeyup2ygt33ci95, "mi_nómine😊": 'name' }"
skip-record-id-key = true

*/

CREATE ONLY user SET my_name = 'name';
CREATE ONLY user SET `mi_nómine😊` = 'name';
```

```surql title="Output"
-------- Query --------

{
  id: user:nronupvxvdm7r1n5hlzm,
  my_name: 'name'
}

-------- Query 2 --------

{
  id: user:eb5pu7u9g67dy773hsv9,
  "mi_nómine😊": 'name'
}
```

Inside a standalone object, non-ASCII field names can also be set by using a string.

```surql
/**[test]

[[test.results]]
value = "{ "mi nómine": 'Edgar' }"

*/

SELECT * FROM ONLY {
    "mi nómine": "Edgar"
};
```

```surql title="Output"
{
  "mi nómine": 'Edgar'
}
```

#### _q018a2 - **Automatically generated field names**_

A field created from an operation will have a field name that represents the operation(s) used to construct it.

```surql
/**[test]

[[test.results]]
value = "[{ "[math::min(temps), math::max(temps)]": [-5, 9], "math::mean": 4f }]"

*/

SELECT
    math::mean(temps),
    [ math::min(temps), math::max(temps) ]
FROM { temps: [-5, 8, 9] };
```

```surql title="Output"
[
    {
        "[math::min(temps), math::max(temps)]": [
            -5,
            9
        ],
        "math::mean": 4f
    }
]
```

Using `AS` allows these automatically calculated field names to be replaced with custom names.

```surql
/**[test]

[[test.results]]
value = "[{ avg_temps: [-5, 9], mean_temps: 4f }]"

*/

SELECT
    math::mean(temps) AS mean_temps,
    [ math::min(temps), math::max(temps) ] AS avg_temps
FROM { temps: [-5, 8, 9] };
```

```surql title="Output"
[
    {
        "avg_temps": [
            -5,
            9
        ],
        "mean_temps": 4
    }
]
```

### _q018b - **Extending objects and removing fields**_

> Available since: V3.0.0

Two objects can be merged by using either the `+` operator or the `object::extend()` function. Any fields in the second object will be added to the first object, thereby updating any existing fields and adding new fields to those that were not present.

```surql
/**[test]

[[test.results]]
value = "{ name: 'Venus', orbital_period: 1y31w1d22h, radius: 6051.8f }"

[[test.results]]
value = "{ name: 'Venus', orbital_period: 1y31w1d22h, radius: 6051.8f }"

*/

{ name: "Venus", radius: 6000 } + { radius: 6051.8, orbital_period: 1y31w1d22h };
{ name: "Venus", radius: 6000 }.extend({ radius: 6051.8, orbital_period: 1y31w1d22h });
```

```surql title="Output"
-------- Query 1 --------

{
  name: 'Venus',
  orbital_period: 1y31w1d22h,
  radius: 6051.8f
}

-------- Query 2 --------

{
  name: 'Venus',
  orbital_period: 1y31w1d22h,
  radius: 6051.8f
}
```

Fields of an object can be removed with the `object::remove()` function, which takes either a single string or an array of strings of the field names to remove.

```surql
/**[test]

[[test.results]]
value = "{ name: 'Venus', orbital_period: 1y31w1d22h }"

[[test.results]]
value = "{ name: 'Venus' }"

*/
{ name: 'Venus', orbital_period: 1y31w1d22h, radius: 6051.8 }.remove("radius");
{ name: 'Venus', orbital_period: 1y31w1d22h, radius: 6051.8 }.remove(["radius", "orbital_period"]);
```

```surql title="Output"
-------- Query 1 --------

{
  name: 'Venus',
  orbital_period: 1y31w1d22h
}

-------- Query 2 --------

{
  name: 'Venus'
}
```

### _q018c - **See also**_

- [Object functions🚫][brakuje_func_db_object]
- [Destructuring nested objects🚫][brakuje_model_idioms#destructuring]

---
---

## _q019 - **Ranges**_

- [📓][surrealdb_docs_3x_surrealql_datamodel_ranges]

> Available since: V2.0.0

A range is composed of `..` and possible delimiters to set the maximum and minimum possible values. The default syntax includes the lower limit and excludes the upper limit. A `=` can be used to make the upper limit inclusive, and `>` can be used to make the lower limit exclusive.

```surql
/**[test]

[[test.results]]
value = "0..10"

[[test.results]]
value = "0..=10"

[[test.results]]
value = "0>..10"

[[test.results]]
value = "0>..=10"

*/

-- From 0 up to 9
0..10;
-- From 0 up to 10
0..=10;
-- From 1 to 9
0>..10;
-- From 1 to 10
0>..=10;
```

A range becomes open ended if a delimiter is not specified.

```surql
/**[test]

[[test.results]]
value = "0.."

[[test.results]]
value = "0>.."

[[test.results]]
value = "..10"

[[test.results]]
value = "..=100"

[[test.results]]
value = ".."

*/

-- Anything from 0 and up
0..;
-- Anything from 1 and up
0>..;
-- Anything up to 99
..100;
-- Anything up to 100
..=100;
-- An infinite range
..;
```

A range can be constructed from any type of value. This is most useful when comparing one value to another.

```surql
/**[test]

[[test.results]]
value = "true"

[[test.results]]
value = "true"

[[test.results]]
value = "true"

[[test.results]]
value = "false"

[[test.results]]
value = "false"

[[test.results]]
value = "false"

*/


-- All true
'g' IN 'a'..'z';
d"2024-01-01" IN d"2020-01-01"..=d"2025-01-01";
['London', d"2022-02-02", 5.7] IN ['London', d"2020-01-01"]..=['London', d"2024-12-31"];

-- All false
"ㅋㅋㅋ" IN "a".."z";
d"2028-01-01" IN d"2020-01-01"..=d"2025-01-01";
['Philadelphia', d"2022-02-02", 5.7] IN ['London', d"2020-01-01"]..=['London', d"2024-12-31"];
```

### _q019a - **Ranges in FOR loops**_

Ranges of integers have the added convenience of being able to be used in a [FOR loop🚫][brakuje_stat_for].

```surql
/**[test]

[[test.results]]
value = "NONE"

*/

FOR $year IN 0..=2024 {
    CREATE historical_events SET
        for_year = $year,
        events = "To be added";
}
```

### _q019b - **Ranges in WHERE clauses**_

A range can be used in a `WHERE` clause in place of operators like `<` and `>`. This is especially useful when checking for a number that must be within a certain range. Using a range carries two main benefits. One is that it produces shorter code that is easier to read and maintain.

```surql
SELECT * FROM person WHERE age >= 18 AND age <= 65;
SELECT * FROM person WHERE age IN 18..=65;
```

Another benefit is performance. The following code should show a modest but measurable improvement in performance between the first and second `SELECT` statement, as only one condition needs to be checked instead of two.

```surql
CREATE |person:20000| SET age = (rand::float() * 120).round() RETURN NONE;

-- Assign output to a parameter so the SELECT output is not displayed
LET $_ = SELECT * FROM person WHERE age > 18 AND age < 65;
LET $_ = SELECT * FROM person WHERE age in 18..=65;
```

### _q019c - **Casting and functional usage**_

A range can be cast into an array.

```surql
/**[test]

[[test.results]]
value = "[1, 2]"

*/

<array> 1..3;
```

```surql title="Output"
[
  1,
  2
]
```

This opens up a range of functional programming patterns that are made possible by SurrealDB's [array functions][SurrealQL101_FunctionsDatabase_Array], many of which can use [anonymous functions][SurrealQL008_DataTypes_ClosuresAnonymousFunctions] (closures) to perform an operation on each item in the array.

```surql
/**[test]

[[test.results]]
value = "[{ original: 130, square_root: 11.40175425099138f }, { original: 140, square_root: 11.832159566199232f }]"

*/

-- Construct an array
(<array> 1..=100)
-- Turn it into an array that increments by 10
    .map(|$v| $v * 10)
-- Turn each number into a object with original and square root value
    .map(|$v| { original: $v, square_root: math::sqrt($v) })
-- Keep only those with square roots in between 11 and 12
    .filter(|$obj| $obj.square_root IN 11..12);
```

```surql title="Output"
[
  {
    original: 130,
    square_root: 11.40175425099138f
  },
  {
    original: 140,
    square_root: 11.832159566199232f
  }
]
```

### _q019d - **Ranges in mock syntax for `CREATE` statements**_

> Available since: V3.0.0

`CREATE` statements have always been able to work on more than one record by enclosing either a single number or a range-like operator between two `||` bars.

```surql title="Before 3.0.0"
-- Create 10 person records with random IDs
CREATE |person:10|;
-- Create `person` records from person:1 to person:10
CREATE |person:1..10|;
```

Originally an internal syntax for mock testing, this syntax become known to the user community and is now commonly used. However, the original syntax differed from true ranges in always being inclusive, in that `1..10` was treated as "from 1 up to and including 10". A change has since been made to have the mock syntax take a true range with a syntax equivalent to that demonstrated in this page.

```surql title="Since 3.0.0"
-- All of these create ten records from person:1 to person:10
CREATE |person:1..=10|;
CREATE |person:1..11|;
CREATE |person:0>..11|;
CREATE |person:0>..=10|;
```

---
---

## _q020 - **Record IDs**_

- [📓][surrealdb_docs_3x_surrealql_datamodel_ids]

> [!NOTE]
> As of `v2.0.0`, SurrealDB no longer eagerly converts a string into a record. An [implicit `r` prefix or cast][SurrealQL007p2_DataTypes_CastingVaAffixes] is required instead.

SurrealDB record IDs are composed of a table name and a record identifier separated by a `:` in between, allowing for a simple and consistent way to reference records across the database. Record IDs are used to uniquely identify records within a table, to [query🚫][brakuje_stat_select], [update🚫][brakuje_stat_update], and [delete🚫][brakuje_stat_delete] records, and serve as [links][SurrealQL021_DataTypes_RecordLinks] from one record to another.

Record IDs can be constructed from a number of ways, including [alphanumeric text][SurrealQL020a2_DataTypes_RecordIDs_Text], complex Unicode text and symbols, [numbers][SurrealQL020a3_DataTypes_RecordIDs_Numeric], arrays, objects, [built-in ID generation functions][SurrealQL020a1_DataTypes_RecordIDs_Random], and [a function to generate an ID from values🚫][brakuje_func_db_type#typeis_record].

All of the following are examples of valid record IDs in SurrealQL.

```surql
company:surrealdb
company:w6xb3izpgvz4n0gow6q7
reaction:`🤪`
weather:['London', d'2025-02-14T01:52:50.375Z']
```

As all record IDs are unique, trying to create a new record with an existing record ID will return an error. To create a record or modify it if the ID already exists, use an [`UPSERT`🚫][brakuje_stat_upsert] statement or an [`INSERT`🚫][brakuje_stat_insert#example-usage] statement with an `ON DUPLICATE KEY UPDATE` clause.

### _q020a - **Types of Record IDs**_

#### _q020a1 - **Random IDs**_

When you [create a record🚫][brakuje_stat_create] without specifying the full ID, a random identifier is assigned after the table name. This differs from the traditional default of auto-increment or serial IDs that many developers are used to.

```surql
/**[test]

[[test.results]]
value = "[{ id: company:igtjgekhxfbd9km14j7t }]"
skip-record-id-key = true

*/


CREATE company;
```

```surql title="Output"
[
  {
    id: company:ezs644u19mae2p68404j
  }
]
```

Record IDs can be generated with a number of built-in ID generation functions, which are cryptographically secure and suitable for dispersion across a distributed datastore. These include a 20 digit alphanumeric ID (the default), sequentially incrementing and temporally sortable ULID Record identifiers, and UUID version 7 Record identifiers.

```surql
/**[test]

[[test.results]]
value = "[{ celsius: 37.5f, id: temperature:f8xh13smeqhbg7h9o1rw, time: d'2025-10-03T01:03:27.756064Z' }]"
skip-record-id-key = true

[[test.results]]
value = "[{ celsius: 37.5f, id: temperature:a5wxgrluu3n0qxrgkfb9, time: d'2025-10-03T01:03:27.756317Z' }]"
skip-record-id-key = true

[[test.results]]
value = "[{ celsius: 37.5f, id: temperature:01K6KSGTGCZ631S0325WPW3KF1, time: d'2025-10-03T01:03:27.756405Z' }]"
skip-record-id-key = true

[[test.results]]
value = "[{ celsius: 37.5f, id: temperature:u'0199a798-6a0c-7f51-8b87-e856013f98ec', time: d'2025-10-03T01:03:27.756501Z' }]"
skip-record-id-key = true

*/


// Generate a random record ID 20 characters in length
// Charset: `abcdefghijklmnopqrstuvwxyz0123456789`
CREATE temperature:rand() SET time = time::now(), celsius = 37.5;
// Identical to the above CREATE statement, because
// :rand() is the default random ID format
CREATE temperature SET time = time::now(), celsius = 37.5;

// Generate a ULID-based record ID
CREATE temperature:ulid() SET time = time::now(), celsius = 37.5;
// Generate a UUIDv7-based record ID
CREATE temperature:uuid() SET time = time::now(), celsius = 37.5;
```

#### _q020a2 - **Text Record IDs**_

Text record IDs can contain letters, numbers and `_` characters.

```surql
/**[test]

[[test.results]]
value = "[{ id: company:surrealdb, name: 'SurrealDB' }]"

[[test.results]]
value = "[{ id: user_version_2025:aajz3qh1nk0b27tztsa7, name: 'Alucard' }]"
skip-record-id-key = true

*/

CREATE company:surrealdb SET name = 'SurrealDB';
CREATE user_version_2025 SET name = 'Alucard';
```

To create a record ID with complex characters, use `\`` (backticks) around the table name and/or record identifier.

```surql
/**[test]

[[test.results]]
value = "[{ author: person:tobie, id: article:⟨8424486b-85b3-4448-ac8d-5d51083391c7⟩, time: d'2025-10-03T01:06:17.050210Z' }]"

[[test.results]]
value = "[{ author: person:⟨Lech_Wałęsa⟩, id: ⟨Artykuł⟩:100 }]"

*/

CREATE article:`8424486b-85b3-4448-ac8d-5d51083391c7` SET
    time = time::now(),
    author = person:tobie;

CREATE `Artykuł`:100 SET
    author = person:`Lech_Wałęsa`;
```

The parts of record IDs with complex characters will display enclosed by `\`` backticks.

```surql title="Output"
-------- Query --------

[
  {
    author: person:tobie,
    id: article:`8424486b-85b3-4448-ac8d-5d51083391c7`,
    time: d'2025-02-18T01:48:46.364Z'
  }
]

-------- Query --------

[
  {
    author: person:`Lech_Wałęsa`,
    id: `Artykuł`:100
  }
]
```

#### _q020a3 - **Numeric Record IDs**_

If you create a record ID with a number as a string, it will be stored with `\`` backticks to differentiate it from a number.

```surql
/**[test]

[[test.results]]
value = "[{ id: article:10 }]"

[[test.results]]
value = "[{ id: article:⟨10⟩ }]"

[[test.results]]
value = "[{ id: article:article10 }]"

[[test.results]]
value = "[article:10, article:⟨10⟩, article:article10]"

*/

CREATE article SET id = 10;
CREATE article SET id = "10";
CREATE article SET id = "article10";
SELECT VALUE id FROM article;
```

As the record ID `article:10` is different from ```article:`10` ```, no errors are returned when creating and both records turn up in the output of the `SELECT` statement. Meanwhile, the article with the identifier `article10` does not use backticks as there is no `article10` number to differentiate it from.

```surql title="Output"
[
  article:10,
  article:`10`,
    article:article10
]
```

If a numeric value is specified without any decimal point suffix and is within the range `-9223372036854775808` to `9223372036854775807` then the value will be parsed, stored, and treated as a 64-bit signed integer.

Any numeric numbers outside of the range of a signed 64-bit integer will be stored as a string.

```surql
/**[test]

[[test.results]]
value = "[{ celsius: 37.5f, id: temperature:17493, time: d'2025-10-03T01:09:50.155406Z' }]"

[[test.results]]
value = "[{ events: ['Galactic senate convenes', 'Mr. Bean still waits in a field'], id: year:⟨29878977097987987979232⟩ }]"

*/

CREATE temperature:17493 SET time = time::now(), celsius = 37.5;
CREATE year:29878977097987987979232 SET
    events = [
        "Galactic senate convenes",
        "Mr. Bean still waits in a field"
    ];
```

```surql title="Output"
-------- Query --------

[
  {
    celsius: 37.5f,
    id: temperature:17493,
    time: d'2025-02-17T06:21:08.911Z'
  }
]

-------- Query s--------

[
  {
    events: [
      'Galactic senate convenes',
      'Mr. Bean still waits in a field'
    ],
    id: year:`29878977097987987979232`
  }
]
```

#### _q020a4 - **Array-based Record IDs**_

Record IDs can be constructed out of arrays and even objects. This sort of record ID is most used when you have a field or two that will be used to look up records inside a [record range][SurrealQL020c_DataTypes_RecordIDs_Ranges], which is extremely performant. This is in contrast to using a `WHERE` clause to filter, which involves a table scan.

Records in SurrealDB can store arrays of values, including other nested arrays or objects within them. Different types of values can be stored within the same array, unless defined otherwise.

```surql
/**[test]

[[test.results]]
value = "[{ conditions: 'cloudy', id: weather:['London', d'2025-02-13T05:00:00Z'], temperature: 5.7f }]"

*/

CREATE weather:['London', d'2025-02-13T05:00:00Z'] SET
    temperature = 5.7,
    conditions = "cloudy";
```

```surql title="Output"
[
  {
    conditions: 'cloudy',
    id: weather:[
      'London',
      d'2025-02-13T05:00:00Z'
    ],
    temperature: 5.7f
  }
]
```

#### _q020a5 - **Why record ranges are performant**_

The main reason why record ranges are so performant is simply because the database knows ahead of time in which area to look for records in a query, and therefore has a smaller "surface area" to work in.

This can be demonstrated by seeing what happens when a single record range query encompasses all of the records in a database. The example below creates 10,000 `player` records that have an array-based record ID that begins with `'mage'`, allowing them to be used in a record range query, as well as a field called `class` that is also `'mage'`, which will be used in a `WHERE` clause to compare performance.

Interestingly, in this case a record range query is only somewhat more performant. This is because both queries end up iterating over 10,000 records, with the only difference being that the query with a `WHERE` clause also checks to see if the value of the `class` field is equal to `'mage'`.

```surql
FOR $_ IN 0..10000 {
    CREATE player:['mage', rand::id()] SET class = 'mage';
};

LET $_ = SELECT * FROM player:['mage', NONE]..['mage', ..];
LET $_ = SELECT * FROM player WHERE class = 'mage';
```

If the number of `player` records is extended to a larger number of classes, however, the difference in performance will be much larger. In this case the record range query is still only iterating a relatively small surface area of 10,000 records, while the second one has ten times this number to go through in addition to the `WHERE` clause on top.

```surql
FOR $_ IN 0..10000 {
  CREATE player:['mage', rand::id()] SET class = 'mage';
  CREATE player:['barbarian', rand::id()] SET class = 'barbarian';
  CREATE player:['rogue', rand::id()]     SET class = 'rogue';
  CREATE player:['bard', rand::id()]      SET class = 'bard';
  CREATE player:['sage', rand::id()]      SET class = 'sage';
  CREATE player:['psionic', rand::id()]   SET class = 'psionic';
  CREATE player:['thief', rand::id()]     SET class = 'thief';
  CREATE player:['paladin', rand::id()]   SET class = 'paladin';
  CREATE player:['ranger', rand::id()]    SET class = 'ranger';
  CREATE player:['cleric', rand::id()]    SET class = 'cleric';
};

LET $_ = SELECT * FROM player:['mage', NONE]..['mage', ..];
LET $_ = SELECT * FROM player WHERE class = 'mage';
```

#### _q020a6 - **IDs made with parameters and function calls**_

Parameters and function calls can be used inside array- and object-based record IDs in the same way as on standalone arrays and objects.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "[{ conditions: 'cloudy', id: weather:['Seoul', d'2025-10-03T01:11:38.204589Z'], temperature: -2.3f }]"
skip-datetime = true

[[test.results]]
value = "[{ conditions: 'cloudy', id: weather:['London', d'2025-10-03T01:11:38.204961Z'], temperature: 5.3f }]"
skip-datetime = true

*/

LET $now = time::now();

CREATE weather:['Seoul', $now] SET
    temperature = -2.3,
    conditions = "cloudy";

CREATE weather:['London', time::now()] SET
    temperature = 5.3,
    conditions = "cloudy";
```

To create a record that uses a parameter or function call as its entire record identifier, the [`type::record()`🚫][brakuje_func_db_type#typerecord] function can be used. (Note: this function was known as `type::thing()` before SurrealDB 3.0)

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "[{ city: 'London', id: weather:⟨2025-10-03T01:13:14.238633Z⟩ }]"
skip-record-id-key = true

*/

LET $now = time::now();

CREATE type::record("weather", $now) SET city = 'London';
```

```surql title="Output"
[
  {
    city: 'London',
    id: weather:`2025-02-18T02:30:08.563Z`
  }
]
```

### _q020b - **Defining record IDs in a schema**_

The type name of a record ID is `record`, which by default allows any sort of record. This type can be set inside a [`DEFINE FIELD`🚫][brakuje_stat_def_field] statement.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "NONE"

[[test.results]]
value = "[{ friends: [person:one, person:two], id: person:663uogu8gnw31irybeer, possessions: [book:one, house:one] }]"
skip-record-id-key = true

*/

DEFINE FIELD possessions ON TABLE person TYPE option<array<record>>;
DEFINE FIELD friends ON TABLE person TYPE option<array<record<person>>>;

CREATE person SET
    possessions = [ book:one, house:one],
    friends = [ person:one, person:two ];
```

Be sure to use just `record` instead of `record<any>`, as `<any>` here would imply actual records of a table called `any`.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
match = "$error = "Couldn't coerce value for field `possessions` of `person:*`: Expected `none | array<record<any>>` but found `[book:one, house:one]`""
error = true

[[test.results]]
value = "[{ id: person:u6qd2t4ij2h45bkf2gk4, possessions: [any:one, any:two] }]"
skip-record-id-key = true

*/

DEFINE FIELD possessions ON TABLE person TYPE option<array<record<any>>>;

-- Won't work, 'book' and 'house' are not of table 'any'
CREATE person SET
    possessions = [ book:one, house:one ];

-- Actually expects this, which is probably
-- not what the DEFINE FIELD intended
CREATE person SET
    possessions = [ any:one, any:two ];
```

### _q020c - **Record ranges**_

SurrealDB supports the ability to query a range of records, using the record ID. Record ID range queries retrieve records using the natural sorting order of the record IDs, making a table scan unnecessary. These range queries can be used to query a range of records in a timeseries context.

```surql
-- Select all person records with IDs between the given range
SELECT * FROM person:1..1000;

-- Select all records for a particular location, inclusive
SELECT * FROM temperature:['London', NONE]..=['London', ..];

-- Select all temperature records with IDs less than a maximum value
SELECT * FROM temperature:..['London', '2022-08-29T08:09:31'];

-- Select all temperature records with IDs greater than a minimum value
SELECT * FROM temperature:['London', '2022-08-29T08:03:39']..;

-- Select all temperature records with IDs between the specified range
SELECT * FROM temperature:['London', '2022-08-29T08:03:39']..['London', '2022-08-29T08:09:31'];
```

The following example shows the difference in performance between a regular query that uses a `WHERE` clause and a record range scan.

```surql
FOR $num IN 0..=100000 {
  CREATE person SET id = $num, num = $num  
};

-- Assign the output to an unused parameter
-- to avoid excessive output
LET $_ = SELECT * FROM person WHERE num IN 0..=1000;
LET $_ = SELECT * FROM person:0..=1000;
```

### _q020d - **Tips and best practices for record IDs**_

#### _q020d1 - **Why choose the right record ID format**_

Choosing an apt record ID format is especially important because record IDs is SurrealQL are immutable. Take the following `user` records for example:

```surql
FOR $i IN 0..5 {
    CREATE user SET user_num = $i, name = "User number " + <string>user_num;
};
```

Each of these `user` records will have a random ID, such as `user:wvjqjc5ebqvfg3aw7g61`. If a decision is made to move away from random IDs to some other form, such as an incrementing number, this will have to be done manually.

```surql
FOR $user IN SELECT * FROM user {
    -- Use type::record to make a record ID
    -- from the user_num field
    CREATE type::record("user", $user.user_num);
    -- Then delete the old user
    DELETE $user;
};

SELECT * FROM user;
```

The final query returning just the IDs shows that they have been recreated with new IDs.

```surql title="Output"
[
  {
    id: user:0,
    name: 'User number 0'
  },
  {
    id: user:1,
    name: 'User number 1'
  },
  {
    id: user:2,
    name: 'User number 2'
  },
  {
    id: user:3,
    name: 'User number 3'
  },
  {
    id: user:4,
    name: 'User number 4'
  }
]
```

However, record IDs are also used as [record links][SurrealQL021_DataTypes_RecordLinks] and to create [graph relations🚫][brakuje_stat_relate]. If this is the case, more work will have to be done in order to recreate the former state.

The following example shows five `user` records, which each have a 50% chance of liking each of the other users.

```surql
FOR $i IN 0..5 {
    CREATE user SET user_num = $i, name = "User number " + <string>user_num;
};

LET $users = SELECT * FROM user;
FOR $user IN $users {
    LET $others = array::complement($users, [$user.id]);
    FOR $counterpart IN $others {
        IF rand::bool() {
            RELATE $user->likes->$counterpart;
        }
    }
};
```

Finding out the current relational state can be done with a query like the following which shows all of the graph tables in which a record is located at the `in` or `out` point. The `?` is a wildcard operator, returning any and all tables found at this point of the graph query.

```surql
SELECT
    id,
    ->?->? AS did, 
    <-?<-? AS done_to
FROM user;
```

```surql title="Output"
[
  {
    did: [
      user:zwfnk4by9gmopf6eeqm0
    ],
    done_to: [
      user:d6bx6sch5li8qmhq3ljl,
      user:ekovipptanvmgr8f48v6
    ],
    id: user:6ycb63zr0k3cpzwel1ga
  },
  {
    did: [
      user:ekovipptanvmgr8f48v6,
      user:6ycb63zr0k3cpzwel1ga,
      user:zk7tpaduzaiuswll58sg
    ],
    done_to: [],
    id: user:d6bx6sch5li8qmhq3ljl
  }
    -- and so on..
]
```

Surrealist's [graph visualization view🚫][brakuje_blog_visualisation] can help as well.

![Surrealist's graph view showing possible output from the previous randomized query in which each of the five user records may or may not like another user. In this case, the output resembles a rhombus with an extra line jutting out from the top left.🖼️][img__graph_view]

With this in mind, here are some of the items to keep in mind when deciding what sort of record ID format to use.

#### _q020d2 - **Meaningful sortable IDs are faster to query**_

Records are returned in ascending record ID order by default. As the following query shows, a `SELECT` statement on a large number of `user` records with random IDs will show those with record identifiers starting with a large number of zeroes. While the IDs are sortable, the IDs themselves are completely random.

```surql
CREATE |user:200000| RETURN NONE;
SELECT VALUE id FROM user LIMIT 4;
```

```surql title="Output"
[
  user:0001th0nnywnczi7mrvk,
  user:000t5r3y7u8stqtecvht,
  user:000tjk1nbi1it1bedplc,
  user:001dfral92ltbdznypcd
]
```

For a large number of records, pagination can be used to retrieve a certain amount of records at a time.

```surql
-- Returns the same four records as above
SELECT VALUE id FROM user START 0 LIMIT 2;
SELECT VALUE id FROM user START 2 LIMIT 2;
```

```surql title="Output"
-------- Query --------

[
  user:0001th0nnywnczi7mrvk,
  user:000t5r3y7u8stqtecvht
]

-------- Query --------

[
  user:001dfral92ltbdznypcd,
  user:001hv9g1uzh32nophrpo
]
```

As record ranges are very performant, consider moving any fields that may be used in a `WHERE` clause into the ID itself.

In the following example, a number of `user` records are created using the default random ID, plus a `num` field that tracks in which order the user was created.

```surql
FOR $num IN 0..100 {
    CREATE user SET num = $num;
    sleep(1ms); -- Simulate a bit of time between user creation
};

SELECT * FROM user WHERE num IN 50..=51;
SELECT * FROM user START 50 LIMIT 2;
```

As the output from the `SELECT` statements show, a `WHERE` clause is needed to find two users starting at a `num` of 50, as `START 50` starts based on the user of the record ID, which is entirely random.

```surql
-------- Query --------

[
  {
    id: user:pqpeg0edt8kpda907o01,
    num: 50
  },
  {
    id: user:ty6qr7zyob5dh882it08,
    num: 51
  }
]

-------- Query --------

[
  {
    id: user:hvfp5m5ty7n2k95dbamv,
    num: 70
  },
  {
    id: user:hvfumcmmveuolg4e2h26,
    num: 36
  }
]
```

Using a ULID in this case will allow the IDs to remain random, but still sorted by date of creation.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "[{ id: user:01K6KTHCCJW7ZA6NWBZEFEVDC9, num: 50 }, { id: user:01K6KTHCCNRMN565T2H6JW70D6, num: 51 }]"
skip-record-id-key = true

[[test.results]]
value = "[{ id: user:01K6KTHCCJW7ZA6NWBZEFEVDC9, num: 50 }, { id: user:01K6KTHCCNRMN565T2H6JW70D6, num: 51 }]"
skip-record-id-key = true

*/

FOR $num IN 0..100 {
    CREATE user:ulid() SET num = $num;
    sleep(1ms);
};

SELECT * FROM user WHERE num IN 50..=51;
SELECT * FROM user START 50 LIMIT 2;
```

Not only is the `START 50 LIMIT 2` query more performant, but the entire `num` field could be removed if its only use is to return records by order of creation.

```surql title="Same record IDs for both queries this time"
-------- Query --------

[
  {
    id: user:01JM1AHN7DDN7XM5KZ2RR2YM1S,
    num: 50
  },
  {
    id: user:01JM1AHN7FS4A3B6RNFCF64H90,
    num: 51
  }
]

-------- Query --------

[
  {
    id: user:01JM1AHN7DDN7XM5KZ2RR2YM1S,
    num: 50
  },
  {
    id: user:01JM1AHN7FS4A3B6RNFCF64H90,
    num: 51
  }
]
```

#### _q020d3 - **Move exact matches in array-based record IDs to the front**_

Take the following `event` records which can be queried as a perfomant record range.

```surql
/**[test]

[[test.results]]
value = "[{ id: event:[d'2025-05-05T08:00:00Z', user:one, 'debug'], info: 'Logged in' }]"

[[test.results]]
value = "[{ id: event:[d'2025-05-05T08:10:00Z', user:one, 'debug'], info: 'Logged out' }]"

[[test.results]]
value = "[{ id: event:[d'2025-05-05T08:01:00Z', user:two, 'debug'], info: 'Logged in' }]"

*/

CREATE event:[d'2025-05-05T08:00:00Z', user:one, "debug"] SET info = "Logged in";
CREATE event:[d'2025-05-05T08:10:00Z', user:one, "debug"] SET info = "Logged out";
CREATE event:[d'2025-05-05T08:01:00Z', user:two, "debug"] SET info = "Logged in";
```

The ordering of the ID in this case is likely not ideal, because the first item in the array, a `datetime`, will be the first to be evaluated in a range scan. A query such as the one below on a range of dates will effectively ignore the second and third parts of the ID.

```surql
SELECT * FROM event:[d'2025-05-05', user:one, "debug"]..[d'2025-05-06', user:one, "debug"];

-- Same result! user name and "debug" are irrelevant
-- SELECT * FROM event:[d'2025-05-05']..[d'2025-05-06'];
```

```surql title="Output"
[
  {
    id: event:[
      d'2025-05-05T08:00:00Z',
      user:one,
      'debug'
    ],
    info: 'Logged in'
  },
  {
    id: event:[
      d'2025-05-05T08:01:00Z',
      user:two,
      'debug'
    ],
    info: 'Logged in'
  },
  {
    id: event:[
      d'2025-05-05T08:10:00Z',
      user:one,
      'debug'
    ],
    info: 'Logged out'
  }
]
```

Instead, the parts of the array that are more likely to be exactly matched (such as `user:one` and `"debug"`) should be moved to the front.

```surql
/**[test]

[[test.results]]
value = "[{ id: event:[user:one, 'debug', d'2025-05-05T08:00:00Z'], info: 'Logged in' }]"

[[test.results]]
value = "[{ id: event:[user:one, 'debug', d'2025-05-05T08:10:00Z'], info: 'Logged out' }]"

[[test.results]]
value = "[{ id: event:[user:two, 'debug', d'2025-05-05T08:01:00Z'], info: 'Logged in' }]"

*/


CREATE event:[user:one, "debug", d'2025-05-05T08:00:00Z'] SET info = "Logged in";
CREATE event:[user:one, "debug", d'2025-05-05T08:10:00Z'] SET info = "Logged out";
CREATE event:[user:two, "debug", d'2025-05-05T08:01:00Z'] SET info = "Logged in";
```

Using this format, queries can now be performed for a certain user and logging level, over a range of datetimes.

```surql
-- Only returns events for user:one and "debug"
SELECT * FROM event:[user:one, "debug", d'2025-05-05']..[user:one, "debug", d'2025-05-06'];
```

```surql title="Output"
[
  {
    id: event:[
      user:one,
      'debug',
      d'2025-05-05T08:00:00Z'
    ],
    info: 'Logged in'
  },
  {
    id: event:[
      user:one,
      'debug',
      d'2025-05-05T08:10:00Z'
    ],
    info: 'Logged out'
  }
]
```

#### _q020d4 - **Auto-incrementing IDs**_

While SurrealDB does not use auto-incrementing IDs by default, this behaviour can be achieved in a number of ways. One is to use the [`record::id()`🚫][brakuje_func_db_record#recordid] function on the latest record, which returns the latter part of a record ID (the '1' in the record ID `person:1`). This can then be followed up with the [`type::record()`🚫][brakuje_func_db_type#typerecord] function to create a new record ID.

```surql
-- Create records from person:1 to person:10
CREATE |person:1..11|;
LET $latest = SELECT VALUE id FROM ONLY person ORDER BY id DESC LIMIT 1;
CREATE type::record("person", $latest.id() + 1);
```

```surql title="Output"
[
  {
    id: person:11
  }
]
```

When dealing with a large number of records, a more performant option is to use a separate record that holds a single value representing the latest ID. An [`UPSERT`🚫][brakuje_stat_upsert] statement is best here, which will allow the counter to be initialized if it does not yet exist, and updated otherwise. This is best done [inside a manual transaction🚫][brakuje_stat_begin] so that the latest ID will be rolled back if any failures occur when creating the next record.

```surql
/**[test]

[[test.results]]
value = "[{ id: person_id:counter, num: 1 }]"

[[test.results]]
value = "[{ id: person:1 }]"

[[test.results]]
error = "'The query was not executed due to a failed transaction'"

[[test.results]]
error = ""Expected `datetime` but found a `'2025_01+01'`""

[[test.results]]
value = "1"

*/

BEGIN TRANSACTION;
UPSERT person_id:counter SET num += 1;
-- Creates a person:1
CREATE type::record("person", person_id:counter.num);
COMMIT TRANSACTION;

BEGIN TRANSACTION;
-- Latest ID is now 2
UPSERT person_id:counter SET num += 1;
-- Whoops, invalid datetime format
-- Transaction fails and all changes are rolled back
CREATE type::record("person", person_id:counter.num) SET created_at = <datetime>'2025_01+01';
COMMIT TRANSACTION;

-- Latest ID is still 1
RETURN person_id:counter.num;
```

#### _q020d5 - **Record IDs are record links**_

As a record ID is a pointer to all of the data of a record, a single record ID is enough to access all of a record's fields. This behaviour is the key to the convenience of [record links][SurrealQL021_DataTypes_RecordLinks] in SurrealDB, as holding a record ID is all that is needed for one record to have a link to another.

When using a standalone record ID as a record pointer, be sure to use the record ID itself.

```surql
/**[test]

[[test.results]]
value = "[{ data: { data: 'for', demonstration: 'purposes', some: 'demo' }, id: person:1 }]"

[[test.results]]
value = "NONE"

[[test.results]]
value = "[{ id: person:1 }]"

*/

CREATE person:1 SET data = {
    some: "demo",
    data: "for",
    demonstration: "purposes"
};

LET $record = SELECT id FROM person:1;
SELECT * FROM $record;
```

The output of the above query is just the `id` field on its own, as the `$record` parameter is an object with an `id` field, not the `id` field (the pointer) itself.

```surql title="Output"
[
  {
    id: person:1
  }
]
```

To rectify this, `id.*` can be used to follow the pointer to the entire data for the record.

```surql
SELECT id.* FROM $record;
```

```surql title="Output"
[
  {
    id: {
      data: {
        data: 'for',
        demonstration: 'purposes',
        some: 'demo'
      },
      id: person:1
    }
  }
]
```

### _q020e - **Limitations**_

At present, the `VALUE` clause cannot be used inside a [`DEFINE FIELD`🚫][brakuje_stat_def_field]: statement.

```surql
/**[test]

[[test.results]]
error = "'Cannot use the `VALUE` keyword on the `id` field.'"

*/

DEFINE FIELD id ON user VALUE rand::int(1, 1000000000) READONLY;
```

```surql title="Output"
[
  {
    id: user:9ixn3oei6o532c2qyixa
  }
]
```

To achieve the desired behaviour, the `id` field can be set inside the statement to create the record.

```surql
/**[test]

[[test.results]]
value = "[{ id: user:639167349 }]"
skip-record-id-key = true

*/


CREATE user SET id = rand::int(1, 1000000000);
```

### _q020f - **Learn more**_

Learn more about record IDs [in this blogpost🚫][brakuje_blog_recordIDS] and on this [**youtube video**▶️][yt02].

---
---

## _q021 - **Record links**_

- [📓][surrealdb_docs_3x_surrealql_datamodel_records]

One of the most powerful features of SurrealDB is the ability to traverse from record-to-record without the need for traditional SQL JOINs. Each record ID points directly to a specific record in the database, without needing to run a table scan query. Record IDs can be stored within other records, allowing them to be linked together.

### _q021a - **Creating a record**_

When you create a record without specifying the id, then a randomly generated id is created and used for the record id.

```surql
/**[test]

[[test.results]]
value = "[{ id: person:lva0fwhgqxuk0m88ktn1, name: 'Tobie' }]"
skip-record-id-key = true

*/

CREATE person SET name = 'Tobie';

-- person:aio58g22n3upq16hsani
```

It's also possible to specify a specific record id when creating or updating records.

```surql
/**[test]

[[test.results]]
value = "[{ id: person:tester, name: 'Tobie' }]"

*/

CREATE person:tester SET name = 'Tobie';

-- person:tester
```

### _q021b - **Select directly off of Record IDs**_

Because Record IDs are their own datatype in SurrealQL, you are able to select directly off of them.

```surql
/**[test]

[[test.results]]
value = "[{ email: 'tobie@surrealdb.com', id: person:tobie, name: 'Tobie', opts: { enabled: true } }]"

[[test.results]]
value = "{ email: 'tobie@surrealdb.com', id: person:tobie, name: 'Tobie', opts: { enabled: true } }"

[[test.results]]
value = "{ email: 'tobie@surrealdb.com', name: 'Tobie' }"

*/

CREATE person:tobie SET name = 'Tobie', email = 'tobie@surrealdb.com', opts.enabled = true;

-- Select the whole record
person:tobie.*;

-- Select specific fields
person:tobie.{ name, email };
```

### _q021c - **Storing record links within records**_

Records ids can be stored directly within other records, either as top-level properties, or nested within objects or arrays.

```surql
/**[test]

[[test.results]]
value = "[{ friends: [person:tobie, person:simon], id: person:jaime, name: 'Jaime' }]"

[[test.results]]
value = "[{ friends: [person:simon, person:marcus], id: person:tobie, name: 'Tobie' }]"

[[test.results]]
value = "[{ friends: [person:jaime, person:tobie], id: person:simon, name: 'Simon' }]"

[[test.results]]
value = "[{ friends: [person:tobie], id: person:marcus, name: 'Marcus' }]"

*/

CREATE person:jaime SET name = 'Jaime', friends = [person:tobie, person:simon];
CREATE person:tobie SET name = 'Tobie', friends = [person:simon, person:marcus];
CREATE person:simon SET name = 'Simon', friends = [person:jaime, person:tobie];
CREATE person:marcus SET name = 'Marcus', friends = [person:tobie];
```

### _q021d - **Fetching remote records from within records**_

Nested field traversal can be used to fetch the properties from the remote records, as if the record was embedded within the record being queried.

```surql
SELECT friends.name FROM person:tobie;
[
  {
    friends: {
      name: ["Simon", "Marcus"]
    }
  }
]
```

There is no limit to the number of remote traversals that can be performed in a query. Using `.` dot notation, SurrealDB does not differentiate between nested object properties, or remote records, and will fetch remote records asynchronously when needed for a query.

```surql
SELECT friends.friends.friends.name FROM person:tobie;
[
  {
    friends: {
      friends: {
        friends: {
          name: [
            [ ["Tobie", "Simon"], ["Simon", "Marcus"] ],
            [ ["Simon", "Marcus"] ]
          ]
        }
      }
    }
  }
]
```

### _q021e - **Next steps**_

You've now seen how to create records using randomly generated ids, or specific record ids. This is just the beginning! The power and flexibility which is possible with the remote record fetching functionality within queries opens up a whole new set of possibilities for storing and querying traditional data, and connected datasets. The next page follows up with a feature available in SurrealDB since version 2.2.0: the ability to use record links in a bidirectional manner thanks to reference tracking.

Also check out this explainer video on using record links in SurrealDB:

[**go to YouTube**▶️][yt01]

---
---

## _q022 - **Record references**_

- [📓][surrealdb_docs_3x_surrealql_datamodel_references]

> Available since: V2.2.0

### _q022a - **Basic concepts**_

Reference tracking begins by adding a `REFERENCE` clause to any `DEFINE FIELD` statement, as long as the field is a top-level field of type `record` or array of records.

```surql
/**[test]

[[test.results]]
value = "NONE"

*/

DEFINE FIELD comics ON person TYPE option<array<record<comic_book>>> REFERENCE;
-- Also works as `option` desugars to this syntax
DEFINE FIELD comics ON person TYPE array<record<comic_book>> | NONE REFERENCE;

-- `comics` field might not be a record, does not work
DEFINE FIELD comics ON person TYPE array<record<comic_book>> | string REFERENCE;
-- Not top-level field, does not work
DEFINE FIELD metadata.comics ON person TYPE array<record<comic_book>> REFERENCE;
```

This incoming record can then be picked up with the `<~` syntax that works in the same way that graph queries do.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "[{ comics: [comic_book:one], id: person:mat, name: 'Mat' }]"

[[test.results]]
value = "[{ comics: [comic_book:one], id: person:nynaeve, name: 'Nynaeve' }]"

[[test.results]]
value = "[{ id: comic_book:one, title: 'Loki, God of Stories' }]"

[[test.results]]
value = "[{ id: comic_book:one, owners: [person:mat, person:nynaeve], title: 'Loki, God of Stories' }]"

[[test.results]]
value = "[{ id: comic_book:one, owners: [{ id: person:mat, name: 'Mat' }, { id: person:nynaeve, name: 'Nynaeve' }], title: 'Loki, God of Stories' }]"

*/

DEFINE FIELD comics ON person TYPE option<array<record<comic_book>>> REFERENCE;
CREATE person:mat SET 
  name = "Mat", 
  comics = [comic_book:one];
CREATE person:nynaeve SET 
  name = "Nynaeve", 
  comics = [comic_book:one];
CREATE comic_book:one SET title = "Loki, God of Stories";

SELECT 
  *, 
  <~person AS owners
FROM comic_book;

SELECT 
  *, 
  <~person.{ id, name } AS owners
FROM comic_book;
```

```surql title="Output"
-------- Query --------

[
  {
    id: comic_book:one,
    owners: [
      person:mat,
      person:nynaeve
    ],
    title: 'Loki, God of Stories'
  }
]

-------- Query --------

[
  {
    id: comic_book:one,
    owners: [
      {
        id: person:mat,
        name: 'Mat'
      },
      {
        id: person:nynaeve,
        name: 'Nynaeve'
      }
    ],
    title: 'Loki, God of Stories'
  }
]
```

### _q022b - **Specifying linking tables**_

Incoming references can also be declared in a schema.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "NONE"

[[test.results]]
value = "NONE"

[[test.results]]
value = "NONE"

[[test.results]]
value = "[{ comics: [comic_book:one], id: person:one }, { comics: [comic_book:one], id: person:two }]"

[[test.results]]
value = "[{ id: publisher:one, products: [comic_book:one, book:one] }]"

[[test.results]]
value = "[{ id: comic_book:one, owners: [person:one, person:two], publishers: [publisher:one], title: 'Loki, God of Stories' }]"

[[test.results]]
value = "[{ id: comic_book:one, owners: [person:one, person:two], publishers: [publisher:one], title: 'Loki, God of Stories' }]"

*/

DEFINE FIELD comics ON person TYPE option<array<record<comic_book>>> REFERENCE;
DEFINE FIELD products ON publisher TYPE option<array<record<comic_book|book>>> REFERENCE;
DEFINE FIELD owners ON comic_book COMPUTED <~person;
DEFINE FIELD publishers ON comic_book COMPUTED <~publisher;

CREATE person:one, person:two SET comics = [comic_book:one];
CREATE publisher:one SET products = [comic_book:one, book:one];
CREATE comic_book:one SET title = "Loki, God of Stories";
SELECT * FROM comic_book;
```

```surql title="Output"
[
  {
    id: comic_book:one,
    owners: [
      person:one,
      person:two
    ],
    publishers: [
      publisher:one
    ],
    title: 'Loki, God of Stories'
  }
]
```

A field of type `references` can be further narrowed down to specify not just the table name, but also the field name of the referencing record. This can be done by enclosing the part after `<~` in parentheses, adding the `FIELD` keyword and naming the field or fields via which incoming references will be shown.

```surql
DEFINE FIELD comics ON person TYPE option<array<record<comic_book>>> REFERENCE;
DEFINE FIELD borrowed_comics ON person TYPE option<array<record<comic_book>>> REFERENCE;
DEFINE FIELD owned_by ON comic_book COMPUTED <~(person FIELD comics);
DEFINE FIELD borrowed_by ON comic_book COMPUTED <~(person FIELD borrowed_comics);
DEFINE FIELD all_readers ON comic_book COMPUTED <~(person FIELD comics borrowed_comics);

CREATE person:one SET comics = [comic_book:one];
CREATE person:two SET borrowed_comics = [comic_book:one];
CREATE comic_book:one SET title = "Loki, God of Stories";
SELECT * FROM comic_book;
```

```surql title="Output"
[
  {
    all_readers: [ person:one, person:two ],
    borrowed_by: [ person:two ],
    id: comic_book:one,
    owned_by: [ person:one ],
    title: 'Loki, God of Stories'
  }
]
```

### _q022c - **Specifying deletion behaviour**_

When working with record links, it is very likely that you will want some behaviour to happen when a referencing link is deleted. Take the following example of a `person` who owns a `comic_book`, which is later deleted. Despite the deletion, a follow-up `SELECT * FROM person` still shows the comic book.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "NONE"

[[test.results]]
value = "[{ id: comic_book:one, owned_by: [], title: 'Loki, God of Stories' }]"

[[test.results]]
value = "[{ comics: [comic_book:one], id: person:one }]"

[[test.results]]
value = "[]"

[[test.results]]
value = "[{ comics: [comic_book:one], id: person:one }]"

*/

DEFINE FIELD comics ON person TYPE option<array<record<comic_book>>> REFERENCE;
DEFINE FIELD owned_by ON comic_book COMPUTED <~person;

CREATE comic_book:one SET title = "Loki, God of Stories";
CREATE person:one SET comics = [comic_book:one];
DELETE comic_book:one;
SELECT * FROM person;
```

```surql title="Output"
[
  {
    comics: [
      comic_book:one
    ],
    id: person:one
  }
]
```

A query using `INFO FOR TABLE person` shows that the actual statement created using `REFERENCE` does not finish at this point, but includes the clause `ON DELETE IGNORE`. This is the default behaviour for references.

```surql
{
  events: {},
  fields: {
    comics: 'DEFINE FIELD comics ON person TYPE none | array<record<comic_book>> REFERENCE ON DELETE IGNORE PERMISSIONS FULL',
    "comics.*": 'DEFINE FIELD comics.* ON person TYPE record<comic_book> REFERENCE ON DELETE IGNORE PERMISSIONS FULL'
  },
  indexes: {},
  lives: {},
  tables: {}
}
```

This `ON DELETE` clause can be modified to have some other behaviour when a reference is deleted.

#### _q022c1 - **ON DELETE IGNORE**_

As shown in the previous section, `ON DELETE IGNORE` is the default behaviour for references and this clause will be added automatically if not specified. It can be added manually to a statement to hint to others reading the code that this behaviour is desired.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "NONE"

[[test.results]]
value = "[{ friended_by: [], friends: [person:two], id: person:one }]"

[[test.results]]
value = "[{ friended_by: [person:one], id: person:two }]"

[[test.results]]
value = "[]"

[[test.results]]
value = "{ friended_by: [], id: person:two }"

*/

-- Default, behaviour, so identical to:
-- DEFINE FIELD friends ON person TYPE option<array<record<person>>> REFERENCE;
DEFINE FIELD friends ON person TYPE option<array<record<person>>> REFERENCE ON DELETE IGNORE;
DEFINE FIELD friended_by ON person COMPUTED <~person;

CREATE person:one SET friends = [person:two];
CREATE person:two;
DELETE person:one;
person:two.*;
```

As the deletion of `person:one` is ignored when calculating the `friended_by` field, it will still show `person:one` even though the record itself has been deleted.

```surql
{
  friended_by: [
    person:one
  ],
  id: person:two
}
```

#### _q022c2 - **ON DELETE UNSET**_

`ON DELETE UNSET` will unset (remove) any linked records that are deleted. This can be thought of as the opposite of `ON DELETE IGNORE`.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "NONE"

[[test.results]]
value = "[{ id: person:one }], [{ comments: [comment:rkvpjc0l9iruy21k89su], id: person:one }]"

[[test.results]]
value = "NONE"

[[test.results]]
value = "[{ comments: [comment:rkvpjc0l9iruy21k89su, comment:tu5f72ouuydjvycg41st], id: person:one }]"

[[test.results]]
value = "NONE"

[[test.results]]
value = "[]"

[[test.results]]
value = "[{ author: [person:one], id: comment:rkvpjc0l9iruy21k89su, text: 'Estonia is bigger than I expected!' }]"

*/

DEFINE FIELD comments ON person TYPE option<array<record<comment>>> REFERENCE ON DELETE UNSET;
DEFINE FIELD author ON comment COMPUTED <~person;

CREATE person:one;
UPDATE person:one SET comments += (CREATE ONLY comment SET text = "Estonia is bigger than I expected!").id;
-- Give this one a parameter name so it can be deleted later
LET $comment = CREATE ONLY comment SET text = "I don't get the joke here?";
UPDATE person:one SET comments += $comment.id;
-- Now delete it
DELETE $comment;
-- Only one comment shows up for person:one now
person:one.comments.*.*;
```

```surql title="Output of person:one queries"
-------- Query --------

[
  {
    comments: [
      comment:gj1kb2e3tedn7kjcxxja,
      comment:6sztlhd6fhgc91dg2lby
    ],
    id: person:one
  }
]

-------- Query --------

[
  {
    author: [
      person:one
    ],
    id: comment:gj1kb2e3tedn7kjcxxja,
    text: 'Estonia is bigger than I expected!'
  }
]
```

#### _q022c3 - **ON DELETE CASCADE**_

The `ON DELETE CASCADE` will cause a record to be deleted if any record it references is deleted. This is useful for records that should not exist if a record that links to them no longer exists.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "NONE"

[[test.results]]
value = "[{ comments: [], id: person:one }]"

[[test.results]]
value = "[{ author: person:one, id: comment:4u9gw4bl2q63zuos3v1y, text: '5/10 for this blog post. The problems I have with it are...' }]"

[[test.results]]
value = "[{ author: person:one, id: comment:em2543ghwy9k921eob3d, text: 'WOW! I never knew you could cut a rope with an arrow.' }]"

[[test.results]]
value = "[{ author: person:one, id: comment:4u9gw4bl2q63zuos3v1y, text: '5/10 for this blog post. The problems I have with it are...' }, { author: person:one, id: comment:em2543ghwy9k921eob3d, text: 'WOW! I never knew you could cut a rope with an arrow.' }]"

[[test.results]]
value = "[]"

[[test.results]]
value = "[]"

*/

DEFINE FIELD author ON comment TYPE record<person> REFERENCE ON DELETE CASCADE;
DEFINE FIELD comments ON person COMPUTED <~comment;

CREATE person:one;
CREATE comment SET author = person:one, text = "5/10 for this blog post. The problems I have with it are...";
CREATE comment SET author = person:one, text = "WOW! I never knew you could cut a rope with an arrow.";

-- Show all the details of comments for 'person:one'
person:one.comments.*.*;
DELETE person:one;
-- Comments no longer exist
SELECT * FROM comment;
```

```surql title="Output"
-------- Query --------

[
  {
    author: person:one,
    id: comment:8msvp0egg8cdlyu4vvn9,
    text: 'WOW! I never knew you could cut a rope with an arrow.'
  },
  {
    author: person:one,
    id: comment:i72qfjy59vbn81hk6lrm,
    text: '5/10 for this blog post. The problems I have with it are...'
  }
]

-------- Query --------

[]

-------- Query --------

[]
```

#### _q022c4 - **ON DELETE REJECT**_

`ON DELETE REJECT` will outright make it impossible to delete a record that is referenced from somewhere else. For example, consider the case in which a house should not be demolished (deleted) until it has been disconnected from utilities such as gas, water, electricity, and so on. This can be simulated in a schema by adding a `REFERENCE ON DELETE REJECT` to the `utility` table, making it impossible for any `house` to be deleted if they link to it.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "NONE"

[[test.results]]
value = "[{ id: house:one, using: [] }]"

[[test.results]]
value = "[{ connected_to: [house:one], id: utility:gas }, { connected_to: [house:one], id: utility:water }]"

*/

DEFINE FIELD connected_to ON utility TYPE option<array<record<house>>> REFERENCE ON DELETE REJECT;
DEFINE FIELD using ON house COMPUTED <~utility;

CREATE house:one;
CREATE utility:gas, utility:water SET connected_to = [house:one];
```

At this point, the `using` field on `house:one` automatically picks up the two references. Due to these references, the `house` record cannot be deleted.

```surql
house:one.*;
DELETE house:one;
```

```surql title="Output"
-------- Query --------

{
  id: house:one,
  using: [
    utility:gas,
    utility:water
  ]
}

-------- Query --------

'Cannot delete `house:one` as it is referenced by `utility:gas` with an ON DELETE REJECT clause'
```

To delete the `house`, the `connected_to` references will first have to be removed.

```surql
UPDATE utility:gas   SET connected_to -= house:one;
UPDATE utility:water SET connected_to -= house:one;

DELETE house:one;
```

Note that an `ON DELETE UNSET` for a required field is effectively the same as an `ON DELETE REJECT`. In both of the following two cases, a `person` that has any referencing `comment` records will not be able to be deleted.

```surql
-- Non-optional field that attempts an UNSET when referencing 'person' is deleted
DEFINE FIELD author ON comment TYPE record<person> REFERENCE ON DELETE UNSET;
LET $person = CREATE ONLY person;
CREATE comment SET text = "Cats are so much better at climbing UP a tree than down! Lol", author = $person.id;
DELETE person;

-- Optional field which rejects the deletion of a referencing 'person'
DEFINE FIELD author ON comment TYPE option<record<person>> REFERENCE ON DELETE REJECT;
LET $person = CREATE ONLY person;
CREATE comment SET text = "Cats are so much better at climbing UP a tree than down! Lol", author = $person.id;
DELETE person;
```

The error message in these two cases will differ, but the behaviour is the same.

```surql
-------- Query --------

"An error occured while updating references for `person:97sfkadd56hqhimbf69m`: Couldn't coerce value for field `author` of `comment:kkigvk5knsoeg53p08n1`: Expected `record<person>` but found `NONE`"

-------- Query --------

'Cannot delete `person:3fm76xztvfab99eq780l` as it is referenced by `comment:ig0ogusbm64cier5ovv9` with an ON DELETE REJECT clause'
```

#### _q022c5 - **ON DELETE THEN**_

The `ON DELETE THEN` clause allows for custom logic when a reference is deleted. This clause includes a parameters called `$this` to refer to the record in question, and `$reference` for the reference.

In the following example, a `person` record's `comments` field will remove any comments when they are deleted, but also add the same comment to a different field called `deleted_comments`.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "NONE"

[[test.results]]
value = "[{ comments: [comment:7g857mbox5rdqvjuezxf], id: person:one }]"

[[test.results]]
value = "NONE"

[[test.results]]
value = "[{ comments: [comment:7g857mbox5rdqvjuezxf, comment:o7qgd26uruvf3hracvrh], id: person:one }]"

[[test.results]]
value = "[]"

[[test.results]]
value = "[{ comments: [comment:7g857mbox5rdqvjuezxf], deleted_comments: [comment:o7qgd26uruvf3hracvrh], id: person:one }]"

*/

DEFINE FIELD comments ON person TYPE option<array<record<comment>>> REFERENCE ON DELETE THEN {
    UPDATE $this SET
        deleted_comments += $reference,
        comments -= $reference;
};
DEFINE FIELD author ON comment COMPUTED <~person;

CREATE person:one SET comments += (CREATE ONLY comment SET text = "Estonia is bigger than I expected!").id;
LET $comment = CREATE ONLY comment SET text = "I don't get the joke here?";
UPDATE person:one SET comments += $comment.id;
DELETE $comment;
SELECT * FROM person:one;
```

```surql title="person:one before and after comment is deleted"
-------- Query --------

[
  {
    comments: [
      comment:lbeyh2icushpwo0ak5ux,
      comment:90tdnyoa14cge2ocmep7
    ],
    id: person:one
  }
]

-------- Query --------

[
  {
    comments: [
      comment:lbeyh2icushpwo0ak5ux
    ],
    deleted_comments: [
      comment:90tdnyoa14cge2ocmep7
    ],
    id: person:one
  }
]
```

---
---

## _q023 - **Regex**_

- [📓][surrealdb_docs_3x_surrealql_datamodel_regex]

> Available since: V3.0.0

A `regex` can be created by casting from a string.

The following examples all return `true`.

```surql
/**[test]

[[test.results]]
value = "true"

[[test.results]]
value = "true"

[[test.results]]
value = "true"

*/

-- Either 'a' or 'b'
<regex> "a|b" = "a";

-- Either color or colour
<regex> "col(o|ou)r" = "colour";

-- Case-insensitive match on English color, colour, or French couleur
<regex> "((?i)col(o|ou)r|couleur)" = "COULEUR";
```

While `regex` was added as a standalone type in version 2.3.0, regex matching has always been available via the [`string::matches()`🚫][brakuje_func_db_string#stringmatches] function.

```surql
/**[test]

[[test.results]]
value = "true"

[[test.results]]
value = "true"

[[test.results]]
value = "true"

*/

string::matches("a", "a|b");
string::matches("colour", "col(o|ou)r");
string::matches("COULEUR", "((?i)col(o|ou)r|couleur)");
```

---
---

## _q024 - **Sets**_

- [📓][surrealdb_docs_3x_surrealql_datamodel_sets]

> [!NOTE]
> Before version 3.0.0-beta, sets were simply arrays that deduplicated their items. To emulate the former behaviour, add the clause `VALUE $value.distinct()` to a `DEFINE FIELD` definition.

A set is similar to an array, but with two key differences:

- The values in a set are automatically deduplicated.
- The values in a set are automatically ordered.

A set can be created using the literal syntax `{}`.

```surql
/**[test]

[[test.results]]
value = "{1, 2, 6}"

*/

RETURN {1, 6, 6, 2};
-- {1, 2, 6}
```

To create a set with zero items or a single item, add a comma.

```surql
/**[test]

[[test.results]]
value = "true"

[[test.results]]
value = "true"

[[test.results]]
value = "false"

[[test.results]]
value = "false"

*/
{,}.is_set();  -- true
{9,}.is_set(); -- true

{}.is_set();   -- false
{9}.is_set();  -- false
```

In addition to the `{}` literal syntax, an array can be cast into a set.

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "NONE"

[[test.results]]
value = "[{ bank_accounts: [55555, 55555, 98787], id: customer:q57ltnsy4rnpwtica0qa, languages: {'en', 'ja', 'kr'} }]"

*/

DEFINE FIELD bank_accounts ON TABLE customer TYPE array<int>;
DEFINE FIELD languages ON TABLE customer TYPE set<string>;

CREATE customer SET
    bank_accounts = [
      55555,
      55555,
      98787
    ],
    languages = <set>[
        "en",
        "ja",
        "kr",
        "kr"
    ];
```

```surql title="Output"
[
  {
    bank_accounts: [
      55555,
      98787
    ],
    id: customer:uv6mn62t8td9vzvfogh4,
    languages: {
      'en',
      'ja',
      'kr'
    }
  }
]
```

Casting into a `set` and back into an array can be a convenient way to deduplicate items in the same way that the [`array::distinct()`][SurrealQL101ao_FunctionsDatabase_Array_distinct] and [`array::sort()`][SurrealQL101bw_FunctionsDatabase_Array_sort] functions are used.

```surql
/**[test]

[[test.results]]
value = "[3, 4, 5, 6, 7, 9, 18]"

[[test.results]]
value = "[3, 4, 5, 6, 7, 9, 18]"

*/

<array><set>[18,7,6,6,6,6,5,4,3,9];
[18,7,6,6,6,6,5,4,3,9].distinct().sort();
```

```surql title="Output"
[3, 4, 5, 6, 7, 9, 18]
```

---
---

## _q025 - **Strings**_

- [📓][surrealdb_docs_3x_surrealql_datamodel_strings]

Strings can be used to store text values. All string values can include Unicode values, emojis, tab characters, and line breaks.

```surql
/**
[test]

[[test.results]]
value = "[{ id: person:95uvwaw161b9qqquxixf, text: 'Lorem ipsum dolor sit amet' }]"
skip-record-id-key = true

**/

CREATE person SET text = 'Lorem ipsum dolor sit amet';
```

Strings can be created using single quotation marks, or double quotation marks.

```surql
/**
[test]

[[test.results]]
value = "[{ id: person:7qrqr6tyodgwngpx73b1, text: 'Lorem ipsum dolor sit amet' }]"
skip-record-id-key = true

**/

CREATE person SET text = "Lorem ipsum dolor sit amet";
```

Any string in SurrealDB can include Unicode text.

```surql
/**
[test]

[[test.results]]
value = "[{ id: person:6tazjj7yko5ot2lujpfk, text: 'I ❤️ SurrealDB' }]"
skip-record-id-key = true

**/

CREATE person SET text = "I ❤️ SurrealDB";
```

Strings can also include line breaks.

```surql
/**
[test]

[[test.results]]
value = "[{ id: person:v4lgc1sfs4xegf86gfcv, text: 'This
is
over
multiple
lines' }]"
skip-record-id-key = true

**/

CREATE person SET text = "This
is
over
multiple
lines";
```

### _q025a - **Specifying data type literal values using string prefixes**_

#### _q025a1 - **Overview**_

In SurrealQL, there are several data types for which literal values are specified using string values, with a prefix indicating the intended type for the value to be interpreted as.

Previously, in SurrealQL version `1.0`, literal values of these types were simply specified using a string without any prefix, and SurrealDB would eagerly convert the strings into the relevant data type in any case where the string matched the format expected for that type. However, since SurrealQL version `2.0`, strings are no longer eagerly converted into other data types. Instead, if you want to specify a literal value of one of these data types, you must explicitly use a string with the appropriate prefix.

#### _q025a2 - **Record ID literal values using the `r` prefix**_

The `r` prefix tells the parser that the contents of the string represent a [`record ID`][SurrealQL020_DataTypes_RecordIDs]. The parser expects record IDs to have the following format: `table_name:record ID`.

> [!NOTE]
> All strings since SurrealDB 2.0 without the `r` prefix are of type `string` and are not parsed as records unless the prefix is present.

Here is an example of a record ID literal value, specified using a string with the `r` prefix.

```surql
/**
[test]

[[test.results]]
value = "person:john"

**/

RETURN r"person:john";
```

```surql title="Response"
-------- Query 1 --------

person:john
```

In the example below, using the [`type::is_string()`🚫][brakuje_func_db_type#typeis_string] and [`type::is_record()`🚫][brakuje_func_db_type#typeis_record] functions respectively, you can check the type of the string.

```surql
/**
[test]

[[test.results]]
value = "true"

[[test.results]]
value = "false"

[[test.results]]
value = "true"

**/

RETURN type::is_string("person:john");
RETURN type::is_record("person:john");
RETURN type::is_record(r"person:john");
```

```surql title="Response"
-------- Query 1 --------

true

-------- Query 2 --------

false

-------- Query 3 --------

true
```

#### _q025a3 - **Datetime literal values using the `d` prefix**_

The `d` prefix tells the parser that the contents of the string represent a [`datetime`][SurrealQL009_DataTypes_Datetimes]. The parser expects `datetime` values to have a valid [RFC 3339][net__RFC_3339] format. Here are a few examples:

```surql
/**
[test]

[[test.results]]
value = "d'2025-11-28T11:41:20.262Z'"

[[test.results]]
value = "d'2025-11-28T07:41:20.262Z'"

[[test.results]]
value = "d'2025-11-28T15:41:20.262Z'"

[[test.results]]
value = "d'2025-11-28T11:41:20Z'"

[[test.results]]
value = "d'2025-11-28T07:41:20Z'"

**/

RETURN d"2025-11-28T11:41:20.262Z";       --- Sub-second precision included, timezone defaulted to UTC
RETURN d"2025-11-28T11:41:20.262+04:00";  --- Sub-second precision included, timezone specified as UTC + 4:00
RETURN d"2025-11-28T11:41:20.262-04:00";  --- Sub-second precision included, timezone specified as UTC - 4:00
RETURN d"2025-11-28T11:41:20Z";           --- Sub-second precision excluded, timezone defaulted to UTC
RETURN d"2025-11-28T11:41:20+04:00";      --- Sub-second precision excluded, timezone specified as UTC + 4:00
```

```surql title="Response"
-------- Query 1 --------

d'2025-11-28T11:41:20.262Z'

-------- Query 2 --------

d'2025-11-28T07:41:20.262Z'

-------- Query 3 --------

d'2025-11-28T15:41:20.262Z'

-------- Query 4 --------

d'2025-11-28T11:41:20Z'

-------- Query 5 --------

d'2025-11-28T07:41:20Z'
```

#### _q025a4 - **UUID literal values with the `u` prefix**_

The `u` prefix tells the parser that the contents of the string represent a [`uuid`][SurrealQL026_DataTypes_UUIDs]. The parser expects `uuid` values to follow the format of an UUID, `ffffffff-ffff-ffff-ffff-ffffffffffff`, where each non-hyphen character can be a digit (0-9) or a letter between `a` and `f` (representing a single hexadecimal digit).

```surql
/**
[test]

[[test.results]]
value = "u'8c54161f-d4fe-4a74-9409-ed1e137040c1'"

**/

RETURN u"8c54161f-d4fe-4a74-9409-ed1e137040c1";
```

```surql title="Response"
-------- Query 1 --------

u'8c54161f-d4fe-4a74-9409-ed1e137040c1'
```

#### _q025a5 - **Byte values using the `b` prefix**_

```surql
/**
[test]

[[test.results]]
value = "b"0099AAFF""

**/

b"0099aaff"
```

#### _q025a6 - **File paths using the `f` prefix**_

```surql
f"bucket:/some/key/to/a/file.txt";
f"bucket:/some/key/with\ escaped";
f"bucket:/some/key".put(b"00aa");
f"bucket:/some/key".get();
```

#### _q025a7 - **String prefixes vs. casting**_

String prefixes seem outwardly similar to casting, but differ in behaviour. A string prefix is an instruction to the parser to treat an input in a certain way, whereas a cast is an instruction to the database to convert one type into another.

As a result, incorrect input with a cast will generate an error:

```surql
// Change _ to - in both examples to fix the input
RETURN <uuid>"018f0e6a_9b95-7ecc-8a38-aea7bf3627dd";
RETURN <datetime>"2024_06-06T12:00:00Z";
```

```surql title="Response"
-------- Query 1 --------

"Expected a uuid but cannot convert '018f0e6a-9b95-7ecc-8a38-aea7bf3627d' into a uuid"

-------- Query 2 --------

"Expected a datetime but cannot convert '2024-06-06T12:00:00' into a datetime"
```

But the same input using a string prefix will not even parse until the input is valid.

```surql
// Will not parse in either case until _ is changed to -
RETURN u"018f0e6a_9b95-7ecc-8a38-aea7bf3627dd";
RETURN d"2024_06-06T12:00:00Z";
```

This also allows for immediate error messages on which part of the input is incorrect. As seen in the image below, the parser is able to inform the user that an underscore at column 18 is the issue.

![A screenshot showing how a string prefix allows incorrect UUID input to be identified before a query can be run. In this case, the parser is able to inform the user that an underscore at column 18 is the issue.🖼️][img__parse_error]

---
---

## _q026 - **UUIDs**_

- [📓][surrealdb_docs_3x_surrealql_datamodel_uuid]

UUIDs represent UUID v4 and v7 values. They can be obtained via either the:

- [`rand::uuid::*` functions🚫][brakuje_func_db_rand#randuuidv4]
- [casted from strings][SurrealQL007o_DataTypes_Casting_uuid]
- or via [string prefixes][SurrealQL025a4_DataTypes_Strings_UUID]

> [!NOTE]
> As of `v2.0.0`, SurrealDB no longer eagerly converts a string into a UUID. An implicit `u` prefix or cast using `<uuid>` is required instead.

```surql
/**[test]

[[test.results]]
value = "u'4048a7ac-9c1a-486e-9a12-e39d76670eac'"
skip-uuid = true

[[test.results]]
value = "u'0199a85c-5e24-7901-9053-9d898d881d9e'"
skip-uuid = true

[[test.results]]
value = "u'a8f30d8b-db67-47ec-8b38-ef703e05ad1b'"

[[test.results]]
value = "u'a8f30d8b-db67-47ec-8b38-ef703e05ad1b'"

*/

rand::uuid::v4();
rand::uuid::v7();
<uuid> "a8f30d8b-db67-47ec-8b38-ef703e05ad1b";
u"a8f30d8b-db67-47ec-8b38-ef703e05ad1b";
```

---
---

## _q027 - **Values**_

- [📓][surrealdb_docs_3x_surrealql_datamodel_values]

Each of the types mentioned in the data model is a subset of an all-encompassing type called a value.

### _q027a - **Comparing and ordering values**_

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

### _q027b - **Values and truthiness**_

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

As [the ! operator][SurrealQL002_Operators] reverses the truthiness of a value, a doubling of this operator can also be used to check for truthiness.

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

---
---

## _q029 - **`ACCESS` statement**_

---
---

## _q030 - **`ALTER` statement**_

---
---

## _q031 - **`ALTER DATABASE` statement**_

---
---

## _q032 - **`ALTER FIELD` statement**_

---
---

## _q033 - **`ALTER INDEX` statement**_

---
---

## _q034 - **`ALTER NAMESPACE` statement**_

---
---

## _q035 - **`ALTER SEQUENCE` statement**_

---
---

## _q036 - **`ALTER SYSTEM` statement**_

---
---

## _q037 - **`ALTER TABLE` statement**_

---
---

## _q038 - **`BEGIN` statement**_

---
---

## _q039 - **`BREAK` statement**_

---
---

## _q040 - **`CANCEL` statement**_

---
---

## _q041 - **`COMMIT` statement**_

---
---

## _q042 - **`CONTINUE` statement**_

---
---

## _q043 - **`CREATE` statement**_

---
---

## _q044 - **`DEFINE` statement**_

---
---

## _q045 - **`DEFINE ACCESS` statement**_

---
---

## _q046 - **`DEFINE ACCESS ... TYPE BEARER`**_

---
---

## _q047 - **`DEFINE ACCESS ... TYPE JWT`**_

---
---

## _q048 - **`DEFINE ACCESS ... TYPE RECORD`**_

---
---

## _q049 - **`DEFINE ANALYZER` statement**_

---
---

## _q050 - **`DEFINE API` statement**_

---
---

## _q051 - **`DEFINE BUCKET` statement**_

---
---

## _q052 - **`DEFINE CONFIG` statement**_

---
---

## _q053 - **`DEFINE DATABASE` statement**_

---
---

## _q054 - **`DEFINE EVENT` statement**_

---
---

## _q055 - **`DEFINE FIELD` statement**_

---
---

## _q056 - **`DEFINE FUNCTION` statement**_

---
---

## _q057 - **`DEFINE INDEX` statement**_

---
---

## _q058 - **`DEFINE MODULE` statement**_

---
---

## _q059 - **`DEFINE NAMESPACE` statement**_

---
---

## _q060 - **`DEFINE PARAM` statement**_

---
---

## _q061 - **`DEFINE SCOPE` statement**_

---
---

## _q062 - **`DEFINE SEQUENCE` statement**_

---
---

## _q063 - **`DEFINE TABLE` statement**_

---
---

## _q064 - **`DEFINE TOKEN` statement**_

---
---

## _q065 - **`DEFINE USER` statement**_

---
---

## _q066 - **`DELETE` statement**_

---
---

## _q067 - **`EXPLAIN` statement**_

---
---

## _q068 - **`FOR` statement**_

---
---

## _q069 - **`IF ELSE` statement**_

---
---

## _q070 - **`INFO` statement**_

---
---

## _q071 - **`INSERT` statement**_

---
---

## _q072 - **`KILL` statement**_

---
---

## _q073 - **`LET` statement**_

---
---

## _q074 - **`LIVE SELECT` statement**_

---
---

## _q075 - **`REBUILD` statement**_

---
---

## _q076 - **`RELATE` statement**_

---
---

## _q077 - **`REMOVE` statement**_

---
---

## _q078 - **`RETURN` statement**_

---
---

## _q079 - **`SELECT` statement**_

---
---

## _q080 - **`SHOW` statement**_

---
---

## _q081 - **`SLEEP` statement**_

---
---

## _q082 - **`THROW` statement**_

---
---

## _q083 - **`UPDATE` statement**_

---
---

## _q084 - **`UPSERT` statement**_

---
---

## _q085 - **`USE` statement**_

---
---

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

- [📓][surrealdb_docs_3x_surrealql_functions]

SurrealDB offers a number of functions that can be used to perform complex logic. These functions are grouped into the following categories:

- [Database functions][SurrealQL099_FunctionsDatabase]
- [JavaScript functions][SurrealQL127_FunctionsEmbedded]
- [SurrealML functions][SurrealQL133_FunctionsML]

---
---

## _q099 - **Database Functions**_

---
---

## _q100 - **API functions**_

---
---

## _q101 - **Array functions**_

- [📓][surrealdb_docs_3x_surrealql_functions_database_array]

These functions can be used when working with, and manipulating arrays of data.

| Function | Description |
| :--- | :--- |
| [`array::add()`][SurrealQL101aa_FunctionsDatabase_Array_add] | Adds an item to an array if it doesn't exist |
| [`array::all()`][SurrealQL101ab_FunctionsDatabase_Array_all] | Checks whether all array values are truthy, or equal to a condition |
| [`array::any()`][SurrealQL101ac_FunctionsDatabase_Array_any] | Checks whether any array value is truthy, or equal to a condition |
| [`array::at()`][SurrealQL101ad_FunctionsDatabase_Array_at] | Returns value for X index, or in reverse for a negative index |
| [`array::append()`][SurrealQL101ae_FunctionsDatabase_Array_append] | Appends an item to the end of an array |
| [`array::boolean_and()`][SurrealQL101af_FunctionsDatabase_Array_booleanAND] | Perform the [AND bitwise operations🚀][net__mdn_Bitwise_AND] on two arrays |
| [`array::boolean_or()`][SurrealQL101ag_FunctionsDatabase_Array_booleanOR] | Perform the [OR bitwise operations🚀][net__mdn_Bitwise_OR] on two arrays |
| [`array::boolean_xor()`][SurrealQL101ah_FunctionsDatabase_Array_booleanXOR] | Perform the [XOR bitwise operations🚀][net__mdn_Bitwise_XOR] on two arrays |
| [`array::boolean_not()`][SurrealQL101ai_FunctionsDatabase_Array_booleanNOT] | Perform the [NOT bitwise operations🚀][net__mdn_Bitwise_NOT] on an array |
| [`array::combine()`][SurrealQL101aj_FunctionsDatabase_Array_combine] | Combines all values from two arrays together |
| [`array::complement()`][SurrealQL101ak_FunctionsDatabase_Array_complement] | Returns the complement of two arrays |
| [`array::clump()`][SurrealQL101am_FunctionsDatabase_Array_clump] | Returns the original array split into multiple arrays of X size |
| [`array::concat()`][SurrealQL101al_FunctionsDatabase_Array_concat] | Returns the merged values from two arrays |
| [`array::difference()`][SurrealQL101an_FunctionsDatabase_Array_difference] | Returns the difference between two arrays |
| [`array::distinct()`][SurrealQL101ao_FunctionsDatabase_Array_distinct] | Returns the unique items in an array |
| [`array::fill()`][SurrealQL101ap_FunctionsDatabase_Array_fill] | Fills an existing array of the same value |
| [`array::filter()`][SurrealQL101aq_FunctionsDatabase_Array_filter] | Filters out values that do not match a pattern |
| [`array::filter_index()`][SurrealQL101ar_FunctionsDatabase_Array_filterIndex] | Returns the indexes of all occurrences of all matching X value |
| [`array::find()`][SurrealQL101as_FunctionsDatabase_Array_find] | Returns the first matching value |
| [`array::find_index()`][SurrealQL101at_FunctionsDatabase_Array_findIndex] | Returns the index of the first occurrence of X value |
| [`array::first()`][SurrealQL101au_FunctionsDatabase_Array_first] | Returns the first item in an array |
| [`array::flatten()`][SurrealQL101av_FunctionsDatabase_Array_flatten] | Flattens multiple arrays into a single array |
| [`array::fold()`][SurrealQL101aw_FunctionsDatabase_Array_fold] | Applies an operation on an initial value plus every element in the array, returning the final result |
| [`array::group()`][SurrealQL101ax_FunctionsDatabase_Array_group] | Flattens and returns the unique items in an array |
| [`array::insert()`][SurrealQL101ay_FunctionsDatabase_Array_insert] | Inserts an item at the end of an array, or in a specific position |
| [`array::intersect()`][SurrealQL101az_FunctionsDatabase_Array_intersect] | Returns the values which intersect two arrays |
| [`array::is_empty()`][SurrealQL101ba_FunctionsDatabase_Array_isEmpty] | Checks if an array is empty |
| [`array::join()`][SurrealQL101bb_FunctionsDatabase_Array_join] | Returns concatenated value of an array with a string in between |
| [`array::last()`][SurrealQL101bc_FunctionsDatabase_Array_last] | Returns the last item in an array |
| [`array::len()`][SurrealQL101bd_FunctionsDatabase_Array_len] | Returns the length of an array |
| [`array::logical_and()`][SurrealQL101be_FunctionsDatabase_Array_logicalAND] | Performs the [AND logical operations🚀][net__mdn_Logical_AND] on two arrays |
| [`array::logical_or()`][SurrealQL101bf_FunctionsDatabase_Array_logicalOR] | Performs the [OR logical operations🚀][net__mdn_Logical_OR] on two arrays |
| [`array::logical_xor()`][SurrealQL101bg_FunctionsDatabase_Array_logicalXOR] | Performs the [XOR logical operations🚀][net__mdn_Logical_XOR] on two arrays |
| [`array::map()`][SurrealQL101bh_FunctionsDatabase_Array_map] | Applies an operation to every item in an array and passes it on |
| [`array::max()`][SurrealQL101bi_FunctionsDatabase_Array_max] | Returns the greatest item from an array |
| [`array::matches()`][SurrealQL101bk_FunctionsDatabase_Array_matches] | Returns an array of booleans indicating which elements of the input array contain a specified value |
| [`array::min()`][SurrealQL101bj_FunctionsDatabase_Array_min] | Returns the least item from an array |
| [`array::pop()`][SurrealQL101bl_FunctionsDatabase_Array_pop] | Returns the last item from an array |
| [`array::prepend()`][SurrealQL101bm_FunctionsDatabase_Array_prepend] | Prepends an item to the beginning of an array |
| [`array::push()`][SurrealQL101bn_FunctionsDatabase_Array_push] | Appends an item to the end of an array |
| [`array::range()`][SurrealQL101bo_FunctionsDatabase_Array_range] | Creates a number array from a range (start to end) |
| [`array::reduce()`][SurrealQL101bp_FunctionsDatabase_Array_reduce] | Applies an operation on every element in the array, returning the final result |
| [`array::remove()`][SurrealQL101bq_FunctionsDatabase_Array_remove] | Removes an item at a specific position from an array |
| [`array::repeat()`][SurrealQL101br_FunctionsDatabase_Array_repeat] | Creates an array a given size with a specified value used for each element |
| [`array::reverse()`][SurrealQL101bs_FunctionsDatabase_Array_reverse] | Reverses the sorting order of an array |
| [`array::sequence()`][SurrealQL101bt_FunctionsDatabase_Array_sequence] | Creates an array of sequential integers |
| [`array::shuffle()`][SurrealQL101bu_FunctionsDatabase_Array_shuffle] | Randomly shuffles the contents of an array |
| [`array::slice()`][SurrealQL101bv_FunctionsDatabase_Array_slice] | Returns a slice of an array |
| [`array::sort()`][SurrealQL101bw_FunctionsDatabase_Array_sort] | Sorts the values in an array in ascending or descending order |
| [`array::sort_lexical()`][SurrealQL101bx_FunctionsDatabase_Array_sortLexical] | Sorts the values in an array, with strings sorted lexically |
| [`array::sort_natural()`][SurrealQL101by_FunctionsDatabase_Array_sortNatural] | Sorts the values in an array, with numeric strings sorted numerically |
| [`array::sort_natural_lexical()`][SurrealQL101bz_FunctionsDatabase_Array_sortNaturalLexical] | Sorts values using natural numeric and lexical ordering |
| [`array::sort::asc()`][SurrealQL101ca_FunctionsDatabase_Array_sortASC] | Sorts the values in an array in ascending order |
| [`array::sort::desc()`][SurrealQL101cb_FunctionsDatabase_Array_sortDESC] | Sorts the values in an array in descending order |
| [`array::swap()`][SurrealQL101cc_FunctionsDatabase_Array_swap] | Swaps two items in an array |
| [`array::transpose()`][SurrealQL101cd_FunctionsDatabase_Array_transpose] | Performs 2D array transposition |
| [`array::union()`][SurrealQL101ce_array_union] | Returns the unique merged values from two arrays |
| [`array::windows()`][SurrealQL101cf_array_windows] | Returns arrays of length `size`, sliding across the original array |

### _q101aa - **`array::add`**_

The `array::add` function adds an item to an array only if it doesn't exist.

```surql title="API DEFINITION"
array::add(array, $new_val: value) -> array
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "['one', 'two', 'three']"

*/


RETURN array::add(["one", "two"], "three");

-- ['one', 'two', 'three']
```

### _q101ab - **`array::all`**_

When called on an array without any extra arguments, the `array::all` function checks whether all array values are [truthy][SurrealQL027_DataTypes_Values].

```surql title="API DEFINITION"
array::all(array) -> bool
array::all(array, $predicate: value) -> bool
array::all(array, $predicate: closure) -> bool
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "false"

[[test.results]]
value = "true"

*/

RETURN array::all([ 1, 2, 3, NONE, 'SurrealDB', 5 ]);
-- false

RETURN ["all", "clear"].all();
-- true
```

The `array::all` function can also be followed with a value or a [closure][SurrealQL008_DataTypes_ClosuresAnonymousFunctions] to check if all elements conform to a condition.

```surql
/**[test]

[[test.results]]
value = "true"

[[test.results]]
value = "true"

[[test.results]]
value = "false"

*/

RETURN ["same", "same", "same"].all("same");
-- true

[
  "What's",
  "it",
  "got",
  "in",
  "its",
  "pocketses??"
].all(|$s| $s.len() > 1);
-- true

[1, 2, "SurrealDB"].all(|$var| $var.is_string());
-- false
```

The `array::all` function can also be called using its alias `array::every`.

```surql
[1, 2, 3].every(|$num| $num > 0);
-- true
```

### _q101ac - **`array::any`**_

The `array::any` function checks whether any array values are [truthy][SurrealQL027_DataTypes_Values].

```surql title="API DEFINITION"
array::any(array) -> bool
array::any(array, $predicate: value) -> bool
array::any(array, $predicate: closure) -> bool
```

When called on an array without any extra arguments, the `array::any` function checks whether any array values are [truthy][SurrealQL027_DataTypes_Values].

```surql
/**[test]

[[test.results]]
value = "true"

[[test.results]]
value = "false"

*/

RETURN array::any([ 1, 2, 3, NONE, 'SurrealDB', 5 ]);
-- true

["", 0, NONE, NULL, [], {}].any();
-- false
```

The `array::any` function can also be followed with a value or a [closure][SurrealQL008_DataTypes_ClosuresAnonymousFunctions] to check if any elements conform to a condition.

```surql
/**[test]

[[test.results]]
value = "true"

[[test.results]]
value = "false"

[[test.results]]
value = "true"

*/

RETURN ["same", "same?", "Dude, same!"].any("same");
-- true

[
  "What's",
  "it",
  "got",
  "in",
  "its",
  "pocketses??"
].any(|$s| $s.len() > 15);
-- false

[1, 2, "SurrealDB"].any(|$var| $var.is_string());
-- true
```

The `array::any` function can also be called using the aliases `array::some` and `array::includes`.

```surql
/**[test]

[[test.results]]
value = "true"

[[test.results]]
value = "false"

*/

[1, 2, 3].some(|$num| $num > 2);
-- true

[1999, 2001, 2002].includes(2000);
-- false
```

### _q101ad - **`array::at`**_

The `array::at` function returns the value at the specified index, or in reverse for a negative index.

```surql title="API DEFINITION"
array::at(array, $index: int) -> any
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "'r'"

*/

RETURN array::at(['s', 'u', 'r', 'r', 'e', 'a', 'l'], 2);

-- 'r'
```

You can also pass a negative index. This will perform the lookup in reverse:

```surql
/**[test]

[[test.results]]
value = "'e'"

*/

RETURN array::at(['s', 'u', 'r', 'r', 'e', 'a', 'l'], -3);

-- 'e'
```

### _q101ae - **`array::append`**_

The `array::append` function appends a value to the end of an array.

```surql title="API DEFINITION"
array::append(array, $new_val: value) -> array
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[1, 2, 3, 4, 5]"

*/

RETURN array::append([1, 2, 3, 4], 5);

-- [1, 2, 3, 4, 5]
```

### _q101af - **`array::boolean_and`**_

The `array::boolean_and` function performs the [`AND` `bitwise operations`🚀][net__mdn_Logical_AND] on the input arrays per-element based on the element's truthiness.
If one array is shorter than the other it is considered null and thus false.

```surql title="API DEFINITION"
array::boolean_and($lh: array, $rh: array)
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "true"

[[test.results]]
value = "true"

[[test.results]]
value = "false"

[[test.results]]
value = "true"

*/

RETURN array::boolean_and(["true", "false", 1, 1], ["true", "true", 0, "true"]);

-- [true, true, false, true]
```

For those that take two arrays, missing elements (if one array is shorter than the other) are considered `null` and thus false.

```surql
/**[test]

[[test.results]]
value = "false"

[[test.results]]
value = "false"

*/

RETURN array::boolean_and([true, true], [false]);

-- [ false, false ]
```

### _q101ag - **`array::boolean_or`**_

The `array::boolean_or` function performs the [OR bitwise operations🚀][net__mdn_Bitwise_OR] on the input arrays per-element based on the element's truthiness.
It takes two arrays and if one array is shorter than the other or missing, the output is considered null and thus false.

```surql title="API DEFINITION"
array::boolean_or($lh: array, $rh: array)
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "false"

[[test.results]]
value = "true"

[[test.results]]
value = "true"

[[test.results]]
value = "true"

*/

RETURN array::boolean_or([false, true, false, true], [false, false, true, true]);

-- [false, true, true, true]
```

### _q101ah - **`array::boolean_xor`**_

The `array::boolean_xor` function performs the [XOR bitwise operations🚀][net__mdn_Logical_OR].

```surql title="API DEFINITION"
array::boolean_xor($lh: array, $rh: array)
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "false"

[[test.results]]
value = "true"

[[test.results]]
value = "true"

[[test.results]]
value = "false"

*/

RETURN array::boolean_xor([false, true, false, true], [false, false, true, true]);

-- [false, true, true, false]
```

### _q101ai - **`array::boolean_not`**_

The `array::boolean_not` function performs the [`NOT bitwise operations`🚀][net__mdn_Bitwise_NOT] on the input array(s) per-element based on the element's truthiness.
It takes in one array and it returns false if its single operand can be converted to true.

```surql title="API DEFINITION"
array::boolean_not(array)
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "true"

[[test.results]]
value = "false"

[[test.results]]
value = "true"

[[test.results]]
value = "false"

*/
RETURN array::boolean_not([ false, true, 0, 1 ]);

-- [true, false, true, false]
```

### _q101aj - **`array::combine`**_

The `array::combine` function combines all values from two arrays together, returning an array of arrays.

```surql title="API DEFINITION"
array::combine(array, $other: array) -> array
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[[[1, 2], [1, 3], [2, 2], [2, 3]]]"

*/

RETURN array::combine([1, 2], [2, 3]);

-- [ [1, 2], [1, 3], [2, 2], [2, 3] ]
```

### _q101ak - **`array::complement`**_

The `array::complement` function returns the complement of two arrays, returning a single array containing items which are not in the second array.

```surql title="API DEFINITION"
array::complement(array, $other: array) -> array
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[1, 2]"

*/

RETURN array::complement([1, 2, 3, 4], [3, 4, 5, 6]);

-- [1, 2]
```

### _q101al - **`array::concat`**_

The `array::concat` function merges two arrays together, returning an array which may contain duplicate values. If you want to remove duplicate values from the resulting array, then use the [`array::union()`][SurrealQL101ce_array_union] function.

```surql title="API DEFINITION"
array::concat(array, $other: array) -> array
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[1, 2, 3, 4, 3, 4, 5, 6]"

*/

RETURN array::concat([1, 2, 3, 4], [3, 4, 5, 6]);

-- [ 1, 2, 3, 4, 3, 4, 5, 6 ]
```

As of SurrealDB 3.0.0-beta, the behaviour of this function can also be achieved using the `+` operator.

```surql
/**[test]

[[test.results]]
value = "[1, 2, 3, 4, 3, 4, 5, 6]"

*/

RETURN [1, 2, 3, 4] + [3, 4, 5, 6];

-- [ 1, 2, 3, 4, 3, 4, 5, 6 ]
```

### _q101am - **`array::clump`**_

The `array::clump` function returns the original array split into sub-arrays of `size`. The last sub-array may have a length less than the length of `size` if `size` does not divide equally into the original array.

```surql title="API DEFINITION"
array::clump(array, $size: int) -> array
```

The following examples show this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = "[[1, 2], [3, 4]]"

[[test.results]]
value = "[[1, 2, 3], [4]]"

*/

LET $array = [1, 2, 3, 4];
RETURN array::clump($array, 2);
RETURN array::clump($array, 3);
```

```surql title="Response"
-- [ [ 1, 2], [3, 4] ]
-- [ [1, 2, 3], [4] ]
```

### _q101an - **`array::difference`**_

The `array::difference` function determines the difference between two arrays, returning a single array containing items which are not in both arrays.

```surql title="API DEFINITION"
array::difference(array, $other: array) -> array
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[1, 2, 5, 6]"

*/

RETURN array::difference([1, 2, 3, 4], [3, 4, 5, 6]);

-- [ 1, 2, 5, 6 ]
```

### _q101ao - **`array::distinct`**_

The `array::distinct` function calculates the unique values in an array, returning a single array.

```surql title="API DEFINITION"
array::distinct(array) -> array
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[1, 2, 3, 4]"

*/

RETURN array::distinct([ 1, 2, 1, 3, 3, 4 ]);

-- [ 1, 2, 3, 4 ]
```

### _q101ap - **`array::fill`**_

> Available since: V2.0.0

The `array::fill` function replaces all values of an array with a new value.

```surql title="API DEFINITION"
array::fill(array, $with: any) -> array
```

The function also accepts a third and a fourth parameter which allows you to replace only a portion of the source array.

```surql title="API DEFINITION"
array::fill(array, $with: any, $start: int, $end: int) -> array
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[10, 10, 10, 10, 10]"

*/

RETURN array::fill([ 1, 2, 3, 4, 5 ], 10);

-- [ 10, 10, 10, 10, 10 ]
```

The following example shows how you can use this function with a starting position, and an ending position, which in this example will replace one item from the array:

```surql
/**[test]

[[test.results]]
value = "[1, 10, 3, 4, 5]"

*/

RETURN array::fill([ 1, NONE, 3, 4, 5 ], 10, 1, 2);

-- [ 1, 10, 3, 4, 5 ]
```

The following example shows how you can use this function with starting and ending negative positions, which in this example will replace one item from the array:

```surql
/**[test]

[[test.results]]
value = "[1, 2, 10, 4, 5]"

*/

RETURN array::fill([ 1, 2, NONE, 4, 5 ], 10, -3, -2);

-- [ 1, 2, 10, 4, 5 ]
```

### _q101aq - **`array::filter`**_

The `array::filter` function filters out values in an array that do not match a pattern, returning only the ones that do match.

```surql title="API DEFINITION"
array::filter(array, $predicate: value) -> array
array::filter(array, $predicate: closure) -> array
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[1, 1]"

[[test.results]]
value = "[true, true, true]"

*/

RETURN array::filter([ 1, 2, 1, 3, 3, 4 ], 1);
-- [ 1, 1 ]

RETURN [true, false, false, false, true, true].filter(true);
-- [ true, true, true ]
```

The `array::filter` function can also take a [closure][SurrealQL008_DataTypes_ClosuresAnonymousFunctions] for more customized filtering.

```surql
/**[test]

[[test.results]]
value = "[{ importance: 10, message: 'I need some help with this query...' }, { importance: 100, message: 'Stuck on an island with two hours of battery life left. Can you...' }]"

*/

[
    { importance: 10, message: "I need some help with this query..." },
    { importance: 0, message: "TEST Is this thing on?" },
    { importance: 5, message: "I have an idea. What if we..."},
    { importance: 100, message: "Stuck on an island with two hours of battery life left. Can you..."}
].filter(|$v| $v.importance > 5);
```

```surql title="Response"
[
  {
    importance: 10,
    message: 'I need some help with this query...'
  },
  {
    importance: 100,
    message: 'Stuck on an island with two hours of battery life left. Can you...'
  }
]
```

Note that the function checks whether the output of the inner closure [is truthy][SurrealQL027_DataTypes_Values], as opposed to only expecting a `bool`. As any and all values can be checked for truthiness, simply passing the closure argument as its output is enough to filter out values that are not truthy, such as `NONE` values and empty arrays.

```surql
/**[test]

[[test.results]]
value = "[1, 2, 3]"

*/

[1,2,3,NONE,0,"",{},[]].filter(|$v| $v);

-- [1, 2, 3]
```

A more real-life example of this pattern in which only the `person` records that have been seen by another are returned:

```surql
/**[test]

[[test.results]]
value = "[{ id: person:one }, { id: person:two }]"

[[test.results]]
value = "[{ id: sees:1906dfpey5ho324ot0if, in: person:one, out: person:two }]"

[[test.results]]
value = "[{ id: person:two, is_seen_by: [person:one] }]"

*/

CREATE person:one, person:two;
RELATE person:one->sees->person:two;

(SELECT 
  id, 
  <-sees<-person AS is_seen_by
FROM person)
    .filter(|$person| $person.is_seen_by);
```

```surql title="Response"
[
  {
    id: person:two,
    is_seen_by: [
      person:one
    ]
  }
]
```

### _q101ar - **`array::filter_index`**_

The `array::filter_index` function returns the indexes of all occurrences of all matching values.

```surql title="API DEFINITION"
array::filter_index(array, $predicate: value) -> array
array::filter_index(array, $predicate: closure) -> array
```

The following examples show this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[1, 3]"

[[test.results]]
value = "[0, 1, 3, 4]"

*/

RETURN array::filter_index(['a', 'b', 'c', 'b', 'a'], 'b');
-- [ 1, 3 ]

RETURN [0, 0, 1, 0, 0, 5, 1].filter_index(0);
-- [ 0, 1, 3, 4 ]
```

The `array::filter_index` function can also take a [closure][SurrealQL008_DataTypes_ClosuresAnonymousFunctions] for more customized filtering.

```surql
/**[test]

[[test.results]]
value = "[0, 3]"

*/

[
    { importance: 10, message: "I need some help with this query..." },
    { importance: 0, message: "TEST Is this thing on?" },
    { importance: 5, message: "I have an idea. What if we..."},
    { importance: 100, message: "Stuck on an island with two hours of battery life left. Can you..."}
].filter_index(|$v| $v.importance > 5);
```

```surql title="Response"
[0, 3]
```

### _q101as - **`array::find`**_

The `array::find` function returns the first occurrence of `value` in the array or `NONE` if `array` does not contain `value`.

```surql title="API DEFINITION"
array::find(array, $predicate: value)   -> value | NONE
array::find(array, $predicate: closure) -> value | NONE
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "'b'"

[[test.results]]
value = "NONE"

*/

RETURN array::find(['a', 'b', 'c', 'b', 'a'], 'b');
-- b

RETURN [1, 2, 3].find(4);
-- [NONE]
```

The `array::find` function is most useful when a [closure][SurrealQL008_DataTypes_ClosuresAnonymousFunctions] is passed in which allows for customized searching.

```surql
/**[test]

[[test.results]]
value = "5"

[[test.results]]
value = "{ intelligence: 15, name: 'Mardine', strength: 10 }"

*/

-- Find one number 3 or greater
RETURN [1, 2, 5].find(|$num| $num >= 3);

-- Find the first adventurer good enough for the task
[
    { strength: 15, intelligence: 6,  name: "Dom the Magnificent" },
    { strength: 10, intelligence: 15, name: "Mardine"             },
    { strength: 20, intelligence: 3,  name: "Gub gub"             },
    { strength: 10, intelligence: 18, name: "Lumin695"            }
].find(|$c| $c.strength > 9 AND $c.intelligence > 9);
```

```surql title="Response"
-------- Query --------

5

-------- Query --------

{
  intelligence: 15,
  name: 'Mardine',
  strength: 10
}
```

### _q101at - **`array::find_index`**_

The `array::find_index` function returns the index of the first occurrence of `value` in the array or `NONE` if `array` does not contain `value`.

```surql title="API DEFINITION"
array::find_index(array, $predicate: value)   -> number | NONE
array::find_index(array, $predicate: closure) -> number | NONE
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "1"

[[test.results]]
value = "NONE"

*/

RETURN array::find_index(['a', 'b', 'c', 'b', 'a'], 'b');
-- 1

RETURN [1, 2, 3].find_index(4);
-- NONE
```

The `array::find_index` function can also take a [closure][SurrealQL008_DataTypes_ClosuresAnonymousFunctions] for more customized searching.

```surql
/**[test]

[[test.results]]
value = "2"

*/

RETURN [1, 2, 3].find_index(|$num| $num > 2);
-- 2
```

The `array::find_index` function also be called using the alias `array::index_of`.

```surql
/**[test]

[[test.results]]
value = "3"

*/

["cat", "badger", "dog", "octopus"].index_of("octopus");
-- 3
```

### _q101au - **`array::first`**_

The `array::first` function returns the first value from an array.

```surql title="API DEFINITION"
array::first(array) -> any
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "'s'"

*/


RETURN array::first([ 's', 'u', 'r', 'r', 'e', 'a', 'l' ]);

-- 's'
```

### _q101av - **`array::flatten`**_

The `array::flatten` function flattens an array of arrays, returning a new array with all sub-array elements concatenated into it.

```surql title="API DEFINITION"
array::flatten(array) -> array
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[1, 2, 3, 4, 'SurrealDB', 5, 6, [7, 8]]"

*/

RETURN array::flatten([ [1, 2], [3, 4], 'SurrealDB', [5, 6, [7, 8]] ]);
```

```surql title="Response"
[ 1, 2, 3, 4, 'SurrealDB', 5, 6, [7, 8] ]
```

### _q101aw - **`array::fold`**_

> Available since: V2.1.0

The `array::fold` function returns a final value from the elements of an array by allowing an operation to be performed at each step of the way as each subsequent item in the array is encountered. To use `array::fold`, pass in an initial value, followed by parameter names for the current value and the next value and an operation to perform on them. If you only want to perform an operation on each item and do not need an initial value, use the [`array::reduce`][SurrealQL101bp_FunctionsDatabase_Array_reduce] function instead.

```surql title="API DEFINITION"
array::fold(array, $initial_value: value, $operator: closure) -> value
```

This function is commonly used to sum or subtract the items in an array from an initial value.

```surql
/**[test]

[[test.results]]
value = "53"

*/

-- Returns 53
[10,12,10,15].fold(100, |$a, $b| $a - $b);
```

The function will then perform the following operation for each step of the way.

- `$a` = 100 (initial value), `$b` = 10 (first item in the array). Operation `$a - $b` = 90. 90 is passed on.
- `$a` = 90, `$b` = 12. Operation `$a - $b` = 78. 78 is passed on.
- `$a` = 84, `$b` = 10. Operation `$a - $b` = 74. 68 is passed on.
- `$a` = 74, `$b` = 15. Operation `$a - $b` = 53. No more items to operate on in the array, 53 is returned.

Another example showing `array::fold()` used to reverse a `string`:

```surql
/**[test]

[[test.results]]
value = "'gnirts sdrawrof a ma I'"

*/

"I am a forwards string"
  .split('')
  .fold("", |$one, $two| $two + $one);
```

```surql title="Output"
'gnirts sdrawrof a ma I'
```

Or to modify a string in some other way.

```surql
/**[test]

[[test.results]]
value = ""_I_don't_like_whitespace""

*/

"I don't like whitespace"
  .split(" ")
  .fold("", |$one, $two| $one + "_" + $two);
```

```surql title="Output"
"_I_don't_like_whitespace"
```

As the output above shows, it is often nice to know which item of the array one is working with. This function allows a third parameter to be passed in that keeps track of the index of the current item.

```surql
/**[test]

[[test.results]]
value = ""I_don't_like_whitespace""

*/

"I don't like whitespace"
  .split(" ")
  .fold("", |$one, $two, $index| IF $index = 0 { $one + $two } ELSE { $one + "_" + $two });
```

```surql title="Output"
"I_don't_like_whitespace"
```

The `array::fold()` function can be used to generate an array of values that can then be passed on to statements like [`INSERT`][SurrealQL071_Statement_INSERT] for bulk insertion.

```surql
INSERT INTO person (
  -- Create 1000 objects with a random ULID and incrementing number
    (<array>0..1000).fold([], |$v, $_, $i| {
    $v.append( { 
      id: rand::ulid(),
      person_num: $i
      });
    })
) RETURN NONE;
```

This function is also useful for aggregating the results of graph queries. The following shows a graph table called `to` that holds the distance from one city to another. The `array::fold()` function can then be used to pass an object along that tracks the first and last city, while accumulating the distance and number of trips along the way.

```surql
CREATE city:one, city:two, city:three;
RELATE city:one -> to -> city:two SET distance = 25.5;
RELATE city:two -> to -> city:three SET distance = 4.1;
[
  city:one,
  city:two,
  city:three
].map(|$v| { {
  city: $v,
  distance: 0,
  from: NONE,
  to: NONE,
  trips: 0
} }).fold({
  city: NONE,
  distance: 0,
  from: NONE,
  to: NONE,
  trips: 0
}, |$acc, $val, $i| {
  RETURN IF $i = 0 {
    {
      city: $val.city,
      distance: 0,
      from: $val.city,
      to: NONE,
      trips: $acc.trips + 1
    }
  }
  ELSE {
    {
      city: $val.city,
      distance: (SELECT VALUE distance FROM ONLY to WHERE in = $acc.city AND out = $val.city LIMIT 1) + $acc.distance,
      from: $acc.from,
      to: $val.city,
      trips: $acc.trips + 1
    }
  };
}).chain(|$v| { {
  distance: $v.distance,
  from: $v.from,
  to: $v.to,
  trips: $v.trips
} });
```

Final result:

```surql
{
  distance: 29.6f,
  from: city:one,
  to: city:three,
  trips: 3
}
```

### _q101ax - **`array::group`**_

The `array::group` function flattens and returns the unique items in an array.

```surql title="API DEFINITION"
array::group(array) -> array
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[1, 2, 3, 4, 5, 6, 7, 8, 9]"

*/

RETURN array::group([1, 2, 3, 4, [3, 5, 6], [2, 4, 5, 6], 7, 8, 8, 9]);

-- [ 1, 2, 3, 4, 5, 6, 7, 8, 9 ]
```

### _q101ay - **`array::insert`**_

The `array::insert` function inserts a value into an array.

```surql title="API DEFINITION"
array::insert(array, $insert: value) -> array
array::insert(array, $insert: value, $position: int) -> array
```

When only a value is used as the second argument, it will be appended to the end of the array.

```surql
/**[test]

[[test.results]]
value = "[1, 2, 5, 3, 'and me']"

*/

array::insert([1, 2, 3, 4], 'and me');
-- [1, 2, 3, 4, 'and me']
```

If the value to append is followed by an index, this will be used as the location for the new value. A negative index can also be used to index from the end instead of from the beginning of an array.

```surql
/**[test]

[[test.results]]
value = "[1, 2, 3, 4, 5]"

*/

array::insert([1, 2, 3, 4], 'and me', 0);
-- ['and me', 1, 2, 3, 4]

array::insert([1, 2, 3, 4], 'and me', -1);
-- [1, 2, 3, 'and me', 4]
```

A negative index can be provided to specify a position relative to the end of the array.

### _q101az - **`array::intersect`**_

The `array::intersect` function calculates the values which intersect two arrays, returning a single array containing the values which are in both arrays.

```surql title="API DEFINITION"
array::intersect(array, $other: array) -> array
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = [3, 4]""

*/

RETURN array::intersect([1, 2, 3, 4], [3, 4, 5, 6]);

-- [ 3, 4 ]
```

### _q101ba - **`array::is_empty`**_

> Available since: V2.0.0

The `array::is_empty` function checks whether the array contains values.

```surql title="API DEFINITION"
array::is_empty(array) -> bool
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql title="An array that contain values"
/**[test]

[[test.results]]
value = "false"

*/

RETURN array::is_empty([1, 2, 3, 4]);

-- false
```

```surql title="An empty array"
/**[test]

[[test.results]]
value = "true"

*/

RETURN array::is_empty([]);

-- true
```

### _q101bb - **`array::join`**_

The `array::join` function takes an array and a string as parameters and returns a concatenated string.

```surql title="API DEFINITION"
array::join(array, $concat_with: string) -> string
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "'again and again and again'"

*/

RETURN array::join(["again", "again", "again"], " and ");

-- "again and again and again"
```

### _q101bc - **`array::last`**_

The `array::last` function returns the last value from an array.

```surql title="API DEFINITION"
array::last(array) -> any
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "'l'"

*/

RETURN array::last([ 's', 'u', 'r', 'r', 'e', 'a', 'l' ]);

-- 'l'
```

### _q101bd - **`array::len`**_

The `array::len` function calculates the length of an array, returning a number. This function includes all items when counting the number of items in the array. If you want to only count [truthy][SurrealQL027_DataTypes_Values] values, then use the [count()][SurrealQL103_FunctionsDatabase_Count] function.

```surql title="API DEFINITION"
array::len(array) -> number
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "9"

*/

RETURN array::len([ 1, 2, 1, null, "something", 3, 3, 4, 0 ]);

-- 9
```

### _q101be - **`array::logical_and`**_

The `array::logical_and` function performs the [`AND` logical operation🚀][net__mdn_Logical_AND] element-wise between two arrays.
The resulting array will have a length of the longer of the two input arrays, where each element is the result of the logical `AND` operation performed between an element from the left hand side array and an element from the right hand side array.

When both of the compared elements are truthy, the resulting element will have the type and value of one of the two truthy values, prioritizing the value and type of the element from the left hand side (the first array).

When one or both of the compared elements are not truthy, the resulting element will have the type and value of one of the non-truthy value(s), prioritizing the value and type of the element from the left hand side (the first array).

```surql title="API DEFINITION"
array::logical_and($lh: array, $rh: array)
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "true"

[[test.results]]
value = "false"

[[test.results]]
value = "false"

[[test.results]]
value = "false"

*/

RETURN array::logical_and([true, false, true, false], [true, true, false, false]);

-- [ true, false, false, false ]
```

For those that take two arrays, missing elements (if one array is shorter than the other) are considered `null` and thus false.

```surql
/**[test]

[[test.results]]
value = "0"

[[test.results]]
value = "NULL"

*/

RETURN array::logical_and([0, 1], [])

-- [ 0, NULL ]
```

### _q101bf - **`array::logical_or`**_

The `array::logical_or` function performs the [`OR` logical operations🚀][net__mdn_Logical_OR] element-wise between two arrays.

The resulting array will have a length of the longer of the two input arrays, where each element is the result of the logical `OR` operation performed between an element from the left hand side array and an element from the right hand side array.

When one or both of the compared elements are truthy, the resulting element will have the type and value of one of the two truthy value(s), prioritizing the value and type of the element from the left hand side (the first array).

When both of the compared elements are not truthy, the resulting element will have the type and value of one of the non-truthy values, prioritizing the value and type of the element from the left hand side (the first array).

```surql title="API DEFINITION"
array::logical_or($lh: array, $rh: array)
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "true"

[[test.results]]
value = "true"

[[test.results]]
value = "true"

[[test.results]]
value = "false"

*/

RETURN array::logical_or([true, false, true, false], [true, true, false, false]);

-- [ true, true, true, false ]
```

If one of the arrays is empty, the first array is returned.

```surql
RETURN array::logical_or([0, 1], []);

[ 0, 1 ]
```

### _q101bg - **`array::logical_xor`**_

The `array::logical_xor` function performs the [`XOR` logical operations🚀][net__mdn_Logical_OR] element-wise between two arrays.

The resulting array will have a length of the longer of the two input arrays, where each element is the result of the logical `XOR` operation performed between an element from the left hand side array and an element from the right hand side array.

When exactly one of the compared elements is truthy, the resulting element will have the type and value of the truthy value.

When both of the compared elements are truthy, the resulting element will be the `bool` value `false`.

When neither of the compared elements are truthy, the resulting element will have the type and value of one of the non-truthy values, prioritizing the value and type of the element from the left hand side (the first array).

```surql title="API DEFINITION"
array::logical_xor($lh: array, $rh: array)
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql

/**[test]

[[test.results]]
value = "false"

[[test.results]]
value = "true"

[[test.results]]
value = "true"

[[test.results]]
value = "false"

*/

RETURN array::logical_xor([true, false, true, false], [true, true, false, false]);

-- [ false, true, true, false ]
```

If one of the array is empty, the first array is returned.

```surql

/**[test]

[[test.results]]
value = "[0, 1]"

*/

RETURN array::logical_xor([0, 1], [])

-- [ 0, 1 ]
```

### _q101bh - **`array::map`**_

The `array::map` function allows the user to call an [anonymous function][SurrealQL008_DataTypes_ClosuresAnonymousFunctions] (closure) that is performed on every item in the array before passing it on.

```surql title="API DEFINITION"
array::map(array, $operator: closure) -> array;
```

The most basic use of `array::map` involves choosing a parameter name for each item in the array and a desired output. The following example gives each item the parameter name `$v`, which can then be used to double the value.

```surql

/**[test]

[[test.results]]
value = "[2, 4, 6]"

*/

[1, 2, 3].map(|$v| $v * 2);
```

```surql title="Response"
[
  2,
  4,
  6
]
```

An example of a longer operation that uses `{}` to allow the closure to take multiple lines of code:

```surql

/**[test]
[[test.results]]
value = "[{ is_even: false, value: 1 }, { is_even: true, value: 2 }, { is_even: false, value: 3 }]"

*/

["1", "2", "3"].map(|$val| {
  LET $num = <number>$val;
  LET $is_even = IF $num % 2 = 0 { true } ELSE { false };
  {
    value: $num,
    is_even: $is_even
  }
});
```

```surql title="Response"
[
  {
    is_even: false,
    value: 1
  },
  {
    is_even: true,
    value: 2
  },
  {
    is_even: false,
    value: 3
  }
]

```

The types for the closure arguments and output can be annotated for extra type safety. Take the following simple closure:

```surql

/**[test]
[[test.results]]
value = "[2.1f, 3.1f, 4.1f]"

*/

[1, 2, 3].map(|$num| $num + 1.1);
```

The output is `[2.1f, 3.1f, 4.1f]`.

However, if the `1.1` inside the function was actually a typo and should have been the integer 11, the following would have prevented it from running.

```surql

/**[test]
[[test.results]]
error = ""Couldn't coerce return value from function `ANONYMOUS`: Expected `int` but found `2.1f`""

*/

[1, 2, 3].map(|$num: int| -> int { $num + 1.1 });
```

```surql title="Response"
"Couldn't coerce return value from function `ANONYMOUS`: Expected `int` but found `2.1f`"
```

The `array::map` function also allows access to the index of each item if a second parameter is added.

```surql

/**[test]
[[test.results]]
value = "['0: first used in the year 876', '1: the number of moons in the sky', '2: also called a pair']"

*/

[
  ": first used in the year 876",
  ": the number of moons in the sky",
  ": also called a pair"
]
  .map(|$item, $index| <string>$index + $item);
```

```surql title="Response"
[
  '0: first used in the year 876',
  '1: the number of moons in the sky',
  '2: also called a pair'
]
```

The `array::map()` function can be used to generate an array of values that can then be passed on to statements like [`INSERT`][SurrealQL071_Statement_INSERT] for bulk insertion.

```surql
INSERT INTO person ((<array>0..=1000).map(|| {id: rand::ulid()}));
```

For a similar function that allows using a closure on entire values instead of each item in an array, see the [chain🚫][brakuje_func_db_value#chain] method.

### _q101bi - **`array::max`**_

The `array::max` function returns the greatest value from an array of values.

```surql title="API DEFINITION"
array::max(array<any>) -> any
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql

/**[test]
[[test.results]]
value = "2"

*/

RETURN array::max([0, 1, 2]);

-- 2
```

As any value can be compared with another value, the array can be an array of any SurrealQL value.

```surql

/**[test]

[[test.results]]
value = "9.9f"

*/

array::max([NONE, NULL, 9, 9.9]);

-- 9.9f
```

See also:

- [`math::max`🚫][brakuje_func_db_math#mathmax], which extracts the greatest number from an array of numbers
- [`time::max`🚫][brakuje_func_db_time#timemax], which extracts the greatest datetime from an array of datetimes
- [How values are compared and ordered in SurrealDB🚫][SurrealQL027a_DataTypes_Values_ComparingOrdering]

### _q101bj - **`array::min`**_

The `array::min` function returns the least value from an array of values.

```surql title="API DEFINITION"
array::min(array<any>) -> any
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql

/**[test]
[[test.results]]
value = "0"

*/

RETURN array::min([0, 1, 2]);

-- 0
```

As any value can be compared with another value, the array can be an array of any SurrealQL value.

```surql
/**[test]

[[test.results]]
value = "NONE"

*/

array::min([NONE, NULL, 9, 9.9]);

NONE
```

See also:

- [`math::min`🚫][brakuje_func_db_math#mathmin], which extracts the least number from an array of numbers
- [`time::min`🚫][brakuje_func_db_time#timemin], which extracts the least datetime from an array of datetimes
- [How values are compared and ordered in SurrealDB🚫][SurrealQL027a_DataTypes_Values_ComparingOrdering]

### _q101bk - **`array::matches`**_

The `array::matches` function returns an array of booleans indicating which elements of the input array contain a specified value.

```surql title="API DEFINITION"
array::matches(array, $predicate: value) -> array<bool>
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql

/**[test]

[[test.results]]
value = "false"

[[test.results]]
value = "true"

[[test.results]]
value = "false"

*/

RETURN array::matches([0, 1, 2], 1);

-- [false, true, false]
```

The following example shows this function when the array contains objects.

```surql

/**[test]

[[test.results]]
value = "false"

[[test.results]]
value = "true"

*/

RETURN array::matches([{id: r"ohno:0"}, {id: r"ohno:1"}], {id: r"ohno:1"});

-- [false, true]
```

### _q101bl - **`array::pop`**_

The `array::pop` function removes a value from the end of an array and returns it. If the array is empty, NONE is returned.

```surql title="API DEFINITION"
array::pop(array) -> value
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "4"

*/

RETURN array::pop([ 1, 2, 3, 4 ]);

-- 4
```

### _q101bm - **`array::prepend`**_

The `array::prepend` function prepends a value to the beginning of an array.

```surql title="API DEFINITION"
array::prepend(array, $new_val: value) -> array
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[5, 1, 2, 3, 4]"

*/

RETURN array::prepend([1, 2, 3, 4], 5);

-- [ 5, 1, 2, 3, 4 ]
```

### _q101bn - **`array::push`**_

The `array::push` function prepends a value to the end of an array.

```surql title="API DEFINITION"
array::push(array, $new_val: value) -> array
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[1, 2, 3, 4, 5]"

*/

RETURN array::push([1, 2, 3, 4], 5);

-- [ 1, 2, 3, 4, 5 ]
```

### _q101bo - **`array::range`**_

> Available since: V2.0.0

The `array::range` function creates an array of numbers from a given range.

```surql title="API DEFINITION"
array::range($start: int, $count: int) -> array
-- Also since 3.0.0-beta
array::range(range) -> array;
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[1, 2, 3, 4, 5, 6, 7, 8, 9]"

*/

RETURN array::range(1, 10);

-- [ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 ]
```

```surql
/**[test]

[[test.results]]
value = "[1, 2, 3, 4, 5]"

*/

RETURN array::range(1..=5);

[ 1, 2, 3, 4, 5 ]
```

### _q101bp - **`array::reduce`**_

> Available since: V2.1.0

The `array::reduce` function reduces the elements of an array to a single final value by allowing an operation to be performed at each step of the way as each subsequent item in the array is encountered. To use `array::reduce`, pass in parameter names for the current value and the next value and an operation to perform on them. If you need an initial value to pass in before the other items are operated on, use the [`array::fold`][SurrealQL101aw_FunctionsDatabase_Array_fold] function instead.

```surql title="API DEFINITION"
array::reduce(array, $operator: closure) -> value
```

This function is commonly used to sum or perform some other mathematical operation on the items in an array.

```surql
/**[test]

[[test.results]]
value = "100"

*/

[10,20,30,40].reduce(|$a, $b| $a + $b);
```

The function will then perform the following operation for each step of the way.

- `$a` = 10, `$b` = 20. Operation `$a + $b` = 30. 30 is passed on.
- `$a` = 30, `$b` = 30. Operation `$a + $b` = 60. 60 is passed on.
- `$a` = 60, `$b` = 40. Operation `$a + $b` = 100. No more items to operate on in the array, 100 is returned.

Another example showing `array::reduce()` used to reverse a `string`:

```surql
/**[test]

[[test.results]]
value = "'gnirts sdrawrof a ma I'"

*/

"I am a forwards string"
  .split('')
  .reduce(|$one, $two| $two + $one);
```

```surql title="Output"
'gnirts sdrawrof a ma I'
```

Or to modify a string in some other way.

```surql
/**[test]

[[test.results]]
value = ""I_don't_like_whitespace""

*/

"I don't like whitespace"
  .split(" ")
  .reduce(|$one, $two| $one + "_" + $two);
```

```surql title="Output"
"I_don't_like_whitespace"
```

It is often nice to know which item of the array one is working with. The following example shows a reduce operation performed on an array, but only up to index 2. For any further indexes, the value is simply passed on.

```surql
/**[test]

[[test.results]]
value = "{ money: 11650, name: 'Daughter and Father and Grandfather and Great-grandmother' }"

*/

[
    {
        name: "Daughter",
        money: 100
    },
    {
        name: "Father",
        money: 1000
    },
    {
        name: "Grandfather",
        money: 550
    },
    {
        name: "Great-grandmother",
        money: 10000
    }
].reduce(|$one, $two, $index| IF $index > 2 { $one } ELSE {
    {
        name: $one.name + " and " + $two.name,
        money: $one.money + $two.money
    }
});
```

```surql title="Output"
{
  money: 1650,
  name: 'Daughter and Father and Grandfather'
}
```

### _q101bq - **`array::remove`**_

The `array::remove` function removes an item from a specific position in an array. A negative index can be provided to specify a position relative to the end of the array.

```surql title="API DEFINITION"
array::remove(array, $index: number) -> array
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[1, 2, 4, 5]"

*/

RETURN array::remove([1, 2, 3, 4, 5], 2);

-- [ 1, 2, 4, 5 ]
```

The following examples shows this function using a negative index.

```surql
/**[test]

[[test.results]]
value = "[1, 2, 3, 5]"

*/

RETURN array::remove([1, 2, 3, 4, 5], -2);

-- [ 1, 2, 3, 5 ]
```

### _q101br - **`array::repeat`**_

> Available since: V2.0.0

The `array::repeat` function creates an array of a given size contain the specified value for each element.

```surql title="API DEFINITION"
array::repeat(any, $count: int) -> array
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[1, 1, 1, 1, 1, 1, 1, 1, 1, 1]"

*/

RETURN array::repeat(1, 10);

-- [ 1, 1, 1, 1, 1, 1, 1, 1, 1, 1 ]
```

```surql
/**[test]

[[test.results]]
value = "['hello', 'hello']"

*/

RETURN array::repeat("hello", 2);

-- [ "hello", "hello" ]
```

### _q101bs - **`array::reverse`**_

The `array::reverse` function reverses the sorting order of an array.

```surql title="API DEFINITION"
array::reverse(array) -> array
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[5, 4, 3, 2, 1]"

*/

RETURN array::reverse([ 1, 2, 3, 4, 5 ]);

-- [ 5, 4, 3, 2, 1 ]
```

### _q101bt - **`array::sequence`**_

> Available since: V3.0.0

The `array::sequence` function creates an array of sequential integers.

```surql title="API DEFINITION"
array::sequence($length: int) -> array
array::sequence($start: int, $length: int) -> array
```

A single number passed in as an argument will create an array beginning at 0 with a length of the number indicated.

```surql
array::sequence(5);
-- [0, 1, 2, 3, 4]
```

If a second argument is passed into this function, the first argument will be used as the starting point for the array and the second for the length.

```surql
array::sequence(-5, 6);
-- [-5, -4, -3, -2, -1, 0]
```

### _q101bu - **`array::shuffle`**_

> Available since: V2.0.0

The `array::shuffle` function randomly shuffles the items of an array.

```surql title="API DEFINITION"
array::shuffle(array) -> array
```

The following example shows this function, and its possible output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[3, 5, 4, 1, 2]"

*/

RETURN array::shuffle([ 1, 2, 3, 4, 5 ]);

-- [ 2, 1, 4, 3, 5 ]
```

### _q101bv - **`array::slice`**_

The `array::slice` function returns a slice of an array, based on a starting position, and a length or negative position.

```surql title="API DEFINITION"
array::slice(array, $start: int, $len: int) -> array
-- Also since 3.0.0-beta
array::slice(array, $slice: range) -> array;
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[2, 3]"

*/

RETURN array::slice([ 1, 2, 3, 4, 5 ], 1, 3);

-- [2, 3]
```

The following example shows how you can use this function with a starting position, and a negative position, which will slice off the first and last element from the array:

```surql
/**[test]

[[test.results]]
value = "[2, 3, 4]"

*/

RETURN array::slice([ 1, 2, 3, 4, 5 ], 1, -1);

[ 2, 3, 4 ]
```

The following example shows how you can use this function with just a starting position, which will only slice from the beginning of the array:

```surql
/**[test]

[[test.results]]
value = "[3, 4, 5]"

*/

RETURN array::slice([ 1, 2, 3, 4, 5 ], 2);

-- [ 3, 4, 5 ]
```

The following example shows how you can use this function with just a negative position, which will only slice from the end of the array:

```surql
/**[test]

[[test.results]]
value = "[4, 5]"

*/

RETURN array::slice([ 1, 2, 3, 4, 5 ], -2);

-- [ 4, 5 ]
```

The following example shows how you can use this function with a negative position, and a length of the slice:

```surql
RETURN array::slice([ 1, 2, 3, 4, 5 ], -3, 2);

[ 3, 4 ]
```

An example of post SurrealDB 3.0 syntax in which the function can also take a range:

```surql
/**[test]

[[test.results]]
value = "['c', 'd']"

*/

['a', 'b', 'c', 'd', 'e'].slice(2..=3);

-- [ 'c', 'd' ]
```

### _q101bw - **`array::sort`**_

The `array::sort` function sorts the values in an array in ascending or descending order.

```surql title="API DEFINITION"
array::sort(array) -> array
```

The function also accepts a second boolean parameter which determines the sorting direction. The second parameter can be `true` for ascending order, or `false` for descending order.

```surql title="API DEFINITION"
array::sort(array, $asc: bool) -> array
```

The function also accepts a second string parameter which determines the sorting direction. The second parameter can be `'asc'` for ascending order, or `'desc'` for descending order.

```surql title="API DEFINITION"
array::sort(array, $order: string) -> array
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[NULL, 0, 1, 1, 2, 3, 3, 4, 'something']"

*/

RETURN array::sort([ 1, 2, 1, null, "something", 3, 3, 4, 0 ]);

-- [ null, 0, 1, 1, 2, 3, 3, 4, "something" ]
```

```surql
/**[test]

[[test.results]]
value = "['something', 4, 3, 3, 2, 1, 1, 0, NULL]"

*/

RETURN array::sort([1, 2, 1, null, "something", 3, 3, 4, 0], false);

-- [ "something", 4, 3, 3, 2, 1, 1, 9, null ]
```

```surql
/**[test]

[[test.results]]
value = "[NULL, 0, 1, 1, 2, 3, 3, 4, 'something']"

*/

RETURN array::sort([1, 2, 1, null, "something", 3, 3, 4, 0], "asc");

-- [ null, 0, 1, 1, 2, 3, 3, 4, "something" ]
```

```surql
/**[test]

[[test.results]]
value = "['something', 4, 3, 3, 2, 1, 1, 0, NULL]"

*/

RETURN array::sort([1, 2, 1, null, "something", 3, 3, 4, 0], "desc");

[ "something", 4, 3, 3, 2, 1, 1, 9, null ]
```

### _q101bx - **`array::sort_lexical`**_

The `array::sort_natural_lexical` function sorts the values in an array in ascending or descending order, with alphabetical strings sorted in lexical order instead of unicode list order.

```surql title="API DEFINITION"
array::sort_lexical(array) -> array
```

The function also accepts a second boolean parameter which determines the sorting direction. The second parameter can be `true` for ascending order, or `false` for descending order.

```surql title="API DEFINITION"
array::sort_lexical(array, $asc: bool) -> array
```

The function also accepts a second string parameter which determines the sorting direction. The second parameter can be `'asc'` for ascending order, or `'desc'` for descending order.

```surql title="API DEFINITION"
array::sort_lexical(array, $order: string) -> array
```

The following example shows that `array::sort_lexical` will sort strings in lexical (alphabetical) order instead of Unicode list order. As an accented 'Á' is listed later in Unicode than regular ASCII letters, the function `array::sort` will show the name 'Álvares' listed after the word 'senhor', but `array::sort_lexical` will show the name at the front of the array instead.

```surql
/**[test]

[[test.results]]
value = "['Obrigado', 'senhor', 'Álvares']"

[[test.results]]
value = "['Álvares', 'Obrigado', 'senhor']"

*/

['Obrigado', 'senhor', 'Álvares'].sort();
['Obrigado', 'senhor', 'Álvares'].sort_lexical();
```

```surql title="Output"
-------- Query 1 (443.209µs) --------

[ 'Obrigado', 'senhor', 'Álvares' ]

-------- Query 2 (457.542µs) --------

[ 'Álvares', 'Obrigado', 'senhor' ]
```

### _q101by - **`array::sort_natural`**_

The `array::sort_natural` function sorts the values in an array in ascending or descending order, with numeric strings sorted in numeric order instead of regular string order.

```surql title="API DEFINITION"
array::sort_natural(array) -> array
```

The function also accepts a second boolean parameter which determines the sorting direction. The second parameter can be `true` for ascending order, or `false` for descending order.

```surql title="API DEFINITION"
array::sort_natural(array, $asc: bool) -> array
```

The function also accepts a second string parameter which determines the sorting direction. The second parameter can be `'asc'` for ascending order, or `'desc'` for descending order.

```surql title="API DEFINITION"
array::sort_natural(array, $order: string) -> array
```

The following example shows that `array::sort_natural` will sort numeric strings as if they were numbers. The `array::sort` function, on the other hand, treats a string like '3' as greater than '11' due to the first character in '3' being greater than '1'.

Note that strings sorted in numeric order will still appear after actual numbers, as [a string will always be greater than a number][SurrealQL027_DataTypes_Values].

```surql
/**[test]

[[test.results]]
value = "[8, 9, 10, '11', '2.2', '3']"

[[test.results]]
value = "[8, 9, 10, '2.2', '3', '11']"

*/

[8, 9, 10, '3', '2.2', '11'].sort();
[8, 9, 10, '3', '2.2', '11'].sort_natural();
```

```surql title="Output"
-------- Query --------

[ 8, 9, 10, '11', '2.2', '3' ]

-------- Query 2 (332.667µs) --------

[ 8, 9, 10, '2.2', '3', '11' ]
```

### _q101bz - **`array::sort_natural_lexical`**_

The `array::sort_natural_lexical` function sorts the values in an array in ascending or descending order, while sorting numeric strings in numeric order and alphabetical strings in lexical order.

```surql title="API DEFINITION"
array::sort_natural_lexical(array) -> array
```

The function also accepts a second boolean parameter which determines the sorting direction. The second parameter can be `true` for ascending order, or `false` for descending order.

```surql title="API DEFINITION"
array::sort_natural_lexical(array, $asc: bool) -> array
```

The function also accepts a second string parameter which determines the sorting direction. The second parameter can be `'asc'` for ascending order, or `'desc'` for descending order.

```surql title="API DEFINITION"
array::sort_natural_lexical(array, $order: string) -> array
```

The following example shows that `array::sort_natural_lexical` will sort numeric strings as if they were numbers, and alphabetical strings in lexical order instead of Unicode order. The `array::sort` function, on the other hand, treats a string like '3' as greater than '11' due to the first character in '3' being greater than '1', and sorts the name 'Álvares' after the string 'senhor' because the 'Á' character comes after regular ASCII characters in Unicode.

```surql
/**[test]

[[test.results]]
value = "[8, 9, 10, '11', '2.2', '3', 'Obrigado', 'senhor', 'Álvares']"

[[test.results]]
value = "[8, 9, 10, '2.2', '3', '11', 'Álvares', 'Obrigado', 'senhor']"

*/

['Obrigado', 'senhor', 'Álvares', 8, 9, 10, '3', '2.2', '11'].sort();
['Obrigado', 'senhor', 'Álvares', 8, 9, 10, '3', '2.2', '11'].sort_natural_lexical();
```

```surql title="Output"
-------- Query --------

[ 8, 9, 10, '11', '2.2', '3', 'Obrigado', 'senhor', 'Álvares' ]

-------- Query 2 (332.667µs) --------

[ 8, 9, 10, '2.2', '3', '11', 'Álvares', 'Obrigado', 'senhor' ]
```

### _q101ca - **`array::sort::asc`**_

The `array::sort::asc` function is a shorthand convenience function for the `array::sort` function, to sort values in an array in ascending order.

```surql title="API DEFINITION"
array::sort::asc(array) -> array
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[NULL, 0, 1, 1, 2, 3, 3, 4, 'something']"

*/

RETURN array::sort::asc([ 1, 2, 1, null, "something", 3, 3, 4, 0 ]);

-- [ null, 0, 1, 1, 2, 3, 3, 4, "something" ]
```

### _q101cb - **`array::sort::desc`**_

The `array::sort::desc` function is a shorthand convenience function for the `array::sort` function, to sort values in an array in descending order.

```surql title="API DEFINITION"
array::sort::desc(array) -> array
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "['something', 4, 3, 3, 2, 1, 1, 0, NULL]"

*/

RETURN array::sort::desc([ 1, 2, 1, null, "something", 3, 3, 4, 0 ]);

-- [ "something", 4, 3, 3, 2, 1, 1, 9, null ]
```

### _q101cc - **`array::swap`**_

> Available since: V2.0.0

The `array::swap` function swaps two values of an array based on indexes.

```surql title="API DEFINITION"
array::swap(array, $from: int, $to: int) -> array
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "["What's", 'it', 'got', 'in', 'its', 'pocketses?']"

*/

RETURN array::swap(["What's", "its", "got", "in", "it", "pocketses?"], 1, 4);
```

```surql title="Output"
[
  "What's",
  'it',
  'got',
  'in',
  'its',
  'pocketses?'
]
```

The following example shows how you can use this function with a positive index, and a negative index, which will swap the first and last element from the array:

```surql
/**[test]

[[test.results]]
value = "[5, 2, 3, 4, 1]"

*/

RETURN array::swap([ 1, 2, 3, 4, 5 ], 0, -1);

-- [ 5, 2, 3, 4, 1 ]
```

An error will be returned if any of the indexes are invalid that informs of range of possible indexes that can be used.

```surql
/**[test]

[[test.results]]
error = "'Incorrect arguments for function array::swap(). Argument 1 is out of range. Expected a number between -2 and 2'"

*/

RETURN array::swap([0, 1], 100, 1000000);
```

```surql title="Output"
'Incorrect arguments for function array::swap(). Argument 1 is out of range. Expected a number between -2 and 2'
```

### _q101cd - **`array::transpose`**_

The `array::transpose` function is used to perform 2d array transposition but its behavior in cases of arrays of differing sizes can be best described as taking in multiple arrays and 'layering' them on top of each other.

```surql title="API DEFINITION"
array::transpose(array<array>) -> array<array>
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[[0, 2], [1, 3]]"

*/

RETURN array::transpose([[0, 1], [2, 3]]);

-- [ [0, 2], [1, 3] ]
```

The layering of the above example can be visualized as follows.

```text
0 1
2 3
↓ ↓ 
0 1   
2 3
```

Imagining a Rubik's Cube is another easy way to conceptualize this function.

```surql
/**[test]

[[test.results]]
value = "[['🟦', '⬜', '🟧'], ['🟥', '🟦', '🟧'], ['🟩', '🟨', '🟥']]"

*/

RETURN array::transpose([
    ['🟦', '🟥', '🟩'],
    ['⬜', '🟦', '🟨'],
    ['🟧', '🟧', '🟥']
]);
```

The output shows the same blocks, but lined up top to bottom instead of left to right.

```surql
[
  [
    '🟦',
    '⬜',
    '🟧'
  ],
  [
    '🟥',
    '🟦',
    '🟧'
  ],
  [
    '🟩',
    '🟨',
    '🟥'
  ]
]
```

Another example of the function used for the statistics of two people:

```surql
/**[test]

[[test.results]]
value = "[['Name', 'Billy', 'Alice'], ['Age', 25, 30]]"

*/

[["Name", "Age"], ["Billy", 25], ["Alice", 30]].transpose();
```

```surql title="Output"
[
  [
    'Name',
    'Billy',
    'Alice'
  ],
  [
    'Age',
    25,
    30
  ]
]
```

The logic of this function for arrays of differing length was improved in SurrealDB 2.2, in which `NONE` is now added at points in which no item is found at an index. Take the following movies for example, in which one — Groundhog Day — does not have a bad guy.

```surql
/**[test]

[[test.results]]
value = "[['Movie', 'Avengers: Infinity War', 'Groundhog Day', 'Star Wars'], ['Bad guy', 'Thanos', NONE, 'Palpatine']]"

*/

[
    ['Movie', 'Bad guy'], 
    ['Avengers: Infinity War', 'Thanos'], 
    ['Groundhog Day'],
    ['Star Wars', 'Palpatine']
].transpose();
```

> Output since: V2.2.0

```surql
[
  [
    'Movie',
    'Avengers: Infinity War',
    'Groundhog Day',
    'Star Wars'
  ],
  [
    'Bad guy',
    'Thanos',
    NONE,
    'Palpatine'
  ]
]
```

> Output before: V2.2.0

```surql
[
  [
    'Movie',
    'Avengers: Infinity War',
    'Groundhog Day',
    'Star Wars'
  ],
  [
    'Bad guy',
    'Thanos',
    'Palpatine'
  ]
]
```

This new behaviour allows transposed arrays to be transposed once more to restore the original output, except with `NONE` added in all the indexes that lack in any array.

```surql
/**[test]

[[test.results]]
value = "[['Movie', 'Bad guy'], ['Avengers: Infinity War', 'Thanos'], ['Groundhog Day', NONE], ['Star Wars', 'Palpatine']]"

*/

[
  [
    'Movie',
    'Bad guy'
  ],
  [
    'Avengers: Infinity War',
    'Thanos'
  ],
  [
    'Groundhog Day'
  ],
  [
    'Star Wars',
    'Palpatine'
  ]
].transpose().transpose();
```

```surql title="Output"
[
  [
    'Movie',
    'Bad guy'
  ],
  [
    'Avengers: Infinity War',
    'Thanos'
  ],
  [
    'Groundhog Day',
    NONE
  ],
  [
    'Star Wars',
    'Palpatine'
  ]
]
```

### _q101ce - **`array::union`**_

The `array::union` function combines two arrays together, removing duplicate values, and returning a single array.

```surql title="API DEFINITION"
array::union(array, $other: array) -> array
```

The following example shows this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "[1, 2, 6, 3, 4, 5]"

*/

RETURN array::union([1, 2, 1, 6], [1, 3, 4, 5, 6]);

-- [ 1, 2, 6, 3, 4, 5 ]
```

### _q101cf - **`array::windows`**_

> Available since: V2.0.0

```surql title="API DEFINITION"
array::windows(array, $window_size: int) -> array
```

The `array::windows` function returns a number of arrays of length `size` created by moving one index at a time down the original array. The arrays returned are guaranteed to be of length `size`. As a result, the function will return an empty array if the length of the original array is not large enough to create a single output array.

The following examples show this function, and its output, when used in a [`RETURN`][SurrealQL078_Statement_RETURN] statement:

```surql
/**[test]

[[test.results]]
value = "NONE"

[[test.results]]
value = ""[[1, 2], [2, 3], [3, 4]]

[[test.results]]
value = "[]"

*/

LET $array = [1, 2, 3, 4];
RETURN array::windows($array, 2);
RETURN array::windows($array, 5);
```

```surql title="Response"
[ [1, 2], [2, 3], [3, 4] ];
[];
```

An example of the same function used in a `RELATE` statement:

```surql
/**[test]

[[test.results]]
value = "[{ id: person:grandfather }, { id: person:father }, { id: person:son }]"

[[test.results]]
value = "NONE"

[[test.results]]
value = "[{ grandsons: [], id: person:father, sons: [person:son] }, { grandsons: [person:son], id: person:grandfather, sons: [person:father] }, { grandsons: [], id: person:son, sons: [] }]"

*/

CREATE person:grandfather, person:father, person:son;

FOR $pair IN array::windows(["grandfather", "father", "son"], 2) {
    LET $first = type::record("person", $pair[0]);
    LET $second = type::record("person", $pair[1]);
    RELATE $first->father_of->$second;
};

SELECT 
  id, 
  ->father_of->person AS sons,
  ->father_of->person->father_of->person AS grandsons
FROM person;
```

### _q101cg - **Method chaining**_

> Available since: V2.0.0

Method chaining allows functions to be called using the `.` dot operator on a value of a certain type instead of the full path of the function followed by the value.

```surql
/**[test]

[[test.results]]
value = "['Again', 'again', 'again']"

[[test.results]]
value = "['Again', 'again', 'again']"

*/

-- Traditional syntax
array::push(["Again", "again"], "again");

-- Method chaining syntax
["Again", "again"].push("again");
```

```surql title="Response"
["Again", "again", "again"]
```

This is particularly useful for readability when a function is called multiple times.

```surql
/**[test]

[[test.results]]
value = "'Again and again and again'"

[[test.results]]
value = "'Again and again and again'"

*/

-- Traditional syntax
array::join(array::push(["Again", "again"], "again"), " and ");

-- Method chaining syntax
["Again", "again"].push("again").join(" and ");
```

```surql title="Response"
"Again and again and again"
```

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

- [📓][surrealdb_docs_3x_surrealql_transactions]

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

The [COMMIT][SurrealQL041_Statement_COMMIT] statement is used to commit a set of statements within a transaction, ensuring that all data modifications become a permanent part of the database.

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

The [CANCEL][SurrealQL040_Statement_CANCEL] statement can be used to cancel a set of statements within a transaction, reverting or rolling back any data modification made within the transaction as a whole.

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

While transactions are automatically rolled back if an error occurs in any of its statements, [THROW][SurrealQL082_Statement_THROW] can also be used to explicitly break out of a transaction at any point. `THROW` can be followed by any value which serves as the error message, usually a string.

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

- [📓][surrealdb_docs_3x_surrealql_comments]

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

[SurrealQL000_SurrealQL]: <#q000---surrealql> "SurrealQL"

[SurrealQL001_DemoData]: <#q001---demo-data> "SurrealQL 🞂 Demo data"

[SurrealQL002_Operators]: <#q002---operators> "SurrealQL 🞂 Operators"

[SurrealQL002aa_OperatorAND]: <#q002aa----or-and> "`&&` or `AND`"

[SurrealQL002ab_OperatorOR]: <#q002ab----or-or> "`||` or `OR`"

[SurrealQL002ac_OperatorNOT]: <#q002ac----not> "`!` (not)"

[SurrealQL002ad_OperatorNotNOT]: <#q002ad----not-not> "`!!` (not not)"

[SurrealQL002ae_OperatorCoalescingNULL]: <#q002ae----null-coalescing> "`??` (null coalescing)"

[SurrealQL002af_OperatorCoalescingTRUTHY]: <#q002af----truthy-coalescing> "`??` (truthy coalescing)"

[SurrealQL002ag_OperatorEQUAL]: <#q002ag----or-is> "`=` or `IS`"

[SurrealQL002ah_OperatorNOTEQUAL]: <#q002ah----or-is-not> "`!=` or `IS NOT`"

[SurrealQL002ai_OperatorEXACT]: <#q002ai----exact> "`==` (exact)"

[SurrealQL002ai_OperatorANYEQUAL]: <#q002aj----any-equal> "`?=` (any equal)"

[SurrealQL002ak_OperatorALLEQUAL]: <#q002ak----all-equal> "`*=` (all equal)"

[SurrealQL002al_OperatorSIMILARITY]: <#q002al-------similarity> "`~` `?~` `!~` `*~` (similarity)"

[SurrealQL002am_OperatorLESS]: <#q002am----less> "`<` (less)"

[SurrealQL002an_OperatorLESSEQUAL]: <#q002an----less-or-equal> "`<=` (less or equal)"

[SurrealQL002ao_OperatorMORE]: <#q002ao----more> "`>` (more)"

[SurrealQL002ap_OperatorMOREEQUAL]: <#q002ap----more-or-equal> "`>=` (more or equal)"

[SurrealQL002aq_OperatorADD]: <#q002aq----add> "`+` (add)"

[SurrealQL002ar_OperatorSUB]: <#q002ar-----sub> "`-` (sub)"

[SurrealQL002as_OperatorMUL]: <#q002as----or--mul> "`*` or `×` (mul)"

[SurrealQL002at_OperatorDIV]: <#q002at----or--div> "`/` or `÷` (div)"

[SurrealQL002au_OperatorPOW]: <#q002au----pow> "`**` (pow)"

[SurrealQL002av_OperatorCoEQU]: <#q002av---contains-or-> "`CONTAINS` or `∋`"

[SurrealQL002aw_OperatorCoNOT]: <#q002aw---containsnot-or-> "`CONTAINSNOT` or `∌`"

[SurrealQL002ax_OperatorCoALL]: <#q002ax---containsall-or-> "`CONTAINSALL` or `⊇`"

[SurrealQL002ay_OperatorCoANY]: <#q002ay---containsany-or-> "`CONTAINSANY` or `⊃`"

[SurrealQL002az_OperatorCoNON]: <#q002az---containsnone-or-> "`CONTAINSNONE` or `⊅`"

[SurrealQL002ba_OperatorInEQU]: <#q002ba---inside-or--or-in> "`INSIDE` or `∈` or `IN`"

[SurrealQL002bb_OperatorInNOT]: <#q002bb---notinside-or--or-not-in> "`NOTINSIDE` or `∉` or `NOT IN`"

[SurrealQL002bc_OperatorInALL]: <#q002bc---allinside-or-> "`ALLINSIDE` or `⊆`"

[SurrealQL002bd_OperatorInANY]: <#q002bd---anyinside-or-> "`ANYINSIDE` or `⊂`"

[SurrealQL002be_OperatorInNON]: <#q002be---noneinside-or-> "`NONEINSIDE` or `⊄`"

[SurrealQL002bf_OperatorOUTSIDE]: <#q002bf---outside> "`OUTSIDE`"

[SurrealQL002bg_OperatorINTERSECTS]: <#q002bg---intersects> "`INTERSECTS`"

[SurrealQL002bh_OperatorMATCHES]: <#q002bh---matches> "`MATCHES`"

[SurrealQL002bi_OperatorKNN]: <#q002bi---knn> "`KNN`"

[SurrealQL003_DataTypes]: <#q003---data-types> "SurrealQL 🞂 Data types"

[SurrealQL003_geometry]: <#q003a---example-geometry> "Example geometry"

[SurrealQL003_bytes]: <#q003b---example-bytes> "Example bytes"

[SurrealQL004_DataTypes_Arrays]: <#q004---arrays> "SurrealQL 🞂 Data type 🞂 Arrays"

[SurrealQL005_DataTypes_Booleans]: <#q005---booleans> "SurrealQL 🞂 Data type 🞂 Booleans"

[SurrealQL006_DataTypes_Bytes]: <#q006---bytes> "SurrealQL 🞂 Data type 🞂 Bytes"

[SurrealQL007_DataTypes_Casting]: <#q007---casting> "SurrealQL 🞂 Data type 🞂 Casting"

[SurrealQL007a_DataTypes_Casting_array]: <#q007a---array> "`<array>`"

[SurrealQL007b_DataTypes_Casting_arrayT]: <#q007b---arrayt> "`<array<T>>`"

[SurrealQL007c_DataTypes_Casting_bool]: <#q007c---bool> "`<bool>`"

[SurrealQL007d_DataTypes_Casting_datetime]: <#q007d---datetime> "`<datetime>`"

[SurrealQL007e_DataTypes_Casting_decimal]: <#q007e---decimal> "`<decimal>`"

[SurrealQL007f_DataTypes_Casting_duration]: <#q007f---duration> "`<duration>`"

[SurrealQL007g_DataTypes_Casting_float]: <#q007g---float> "`<float>`"

[SurrealQL007h_DataTypes_Casting_int]: <#q007h---int> "`<int>`"

[SurrealQL007i_DataTypes_Casting_number]: <#q007i---number> "`<number>`"

[SurrealQL007j_DataTypes_Casting_record]: <#q007j---record> "`<record>`"

[SurrealQL007k_DataTypes_Casting_recordT]: <#q007k---recordt> "`<record<T>>`"

[SurrealQL007l_DataTypes_Casting_set_setT]: <#q007l---set-and-sett> "`<set>` and `<set<T>>`"

[SurrealQL007m_DataTypes_Casting_string]: <#q007m---string> "`<string>`"

[SurrealQL007n_DataTypes_Casting_regex]: <#q007n---regex> "`<regex>`"

[SurrealQL007o_DataTypes_Casting_uuid]: <#q007o---uuid> "`<uuid>`"

[SurrealQL007p_DataTypes_CastingGeneral]: <#q007p---general-notes-on-casting> "General notes on casting"

[SurrealQL007p1_DataTypes_CastingSyntaxOrder]: <#q007p1---syntax-and-order> "Syntax and order"

[SurrealQL007p2_DataTypes_CastingVaAffixes]: <#q007p2---casting-vs-affixes> "Casting vs. affixes"

[SurrealQL008_DataTypes_ClosuresAnonymousFunctions]: <#q008---anonymous-functions-closures> "SurrealQL 🞂 Data type 🞂 Anonymous functions (closures)"

[SurrealQL009_DataTypes_Datetimes]: <#q009---datetimes> "SurrealQL 🞂 Data type 🞂 Datetimes"

[SurrealQL010_DataTypes_Files]: <#q010---files> "SurrealQL 🞂 Data type 🞂 Files"

[SurrealQL011_DataTypes_Formatters]: <#q011---formatters> "SurrealQL 🞂 Data type 🞂 Formatters"

[SurrealQL012_DataTypes_FuturesComputed]: <#q012---futures-computed-clause> "SurrealQL 🞂 Data type 🞂 Futures (`COMPUTED` clause)"

[SurrealQL013_DataTypes_Geometries]: <#q013---geometries> "SurrealQL 🞂 Data type 🞂 Geometries"

[SurrealQL013a_DataTypes_Geometries_GeoJSON]: <#q013a---the-geojson-spec> "The GeoJSON spec"

[SurrealQL013b_DataTypes_Geometries_Point]: <#q013b---point> "`Point`"

[SurrealQL013c_DataTypes_Geometries_LineString]: <#q013c---linestring> "`LineString`"

[SurrealQL013d_DataTypes_Geometries_Polygon]: <#q013d---polygon> "`Polygon`"

[SurrealQL013e_DataTypes_Geometries_MultiPoint]: <#q013e---multipoint> "`MultiPoint`"

[SurrealQL013f_DataTypes_Geometries_MultiLineString]: <#q013f---multilinestring> "`MultiLineString`"

[SurrealQL013g_DataTypes_Geometries_MultiPolygon]: <#q013g---multipolygon> "`MultiPolygon`"

[SurrealQL013h_DataTypes_Geometries_Collection]: <#q013h---collection> "`Collection`"

[SurrealQL013i_DataTypes_Geometries_Example]: <#q013i---example> "Example"

[SurrealQL014_DataTypes_Idioms]: <#q014---idioms> "SurrealQL 🞂 Data type 🞂 Idioms"

[SurrealQL014a_DataTypes_Idioms_Field]:<#q014a---field-access> "Field Access"

[SurrealQL014b_DataTypes_Idioms_Index]:<#q014b---index-access> "Index Access"

[SurrealQL014c_DataTypes_Idioms_AllElements]:<#q014c---all-elements> "All Elements"

[SurrealQL014c1_DataTypes_Idioms_Where]:<#q014c1---using--to-return-values> "Using `.*` to return values"

[SurrealQL014c2_DataTypes_Idioms_AllValues]:<#q014c2---accessing-all-values-in-an-object> "Accessing all values in an object"

[SurrealQL014d_DataTypes_Idioms_LastElements]:<#q014d---last-element> "Last Element"

[SurrealQL014e_DataTypes_Idioms_MethodChaining]:<#q014e---method-chaining> "Method chaining"

[SurrealQL014f_DataTypes_Idioms_GraphNavigation]:<#q014f---graph-navigation> "Graph Navigation"

[SurrealQL014g_DataTypes_Idioms_Destructuring]:<#q014g---destructuring> "Destructuring"

[SurrealQL014h_DataTypes_Idioms_OptionalPart]:<#q014h---optional-parts> "Optional Parts"

[SurrealQL014i_DataTypes_Idioms_UsingOptionalPart]:<#q014i---using-optional-parts> "Using Optional Parts"

[SurrealQL014j_DataTypes_Idioms_RecursivePaths]:<#q014j---recursive-paths> "Recursive paths"
[SurrealQL014j3_DataTypes_Idioms_RecursivePathsProvideInstructions]:<#q014j3---using--to-provide-instructions-at-each-depth> "Using `()` to provide instructions at each depth"

[SurrealQL014k_DataTypes_Idioms_CombiningIdiomParts]:<#q014k---combining-idiom-parts> "Combining Idiom Parts"

[SurrealQL014l_DataTypes_Idioms_NotesIdioms]:<#q014l---notes-on-idioms> "Notes on Idioms"

[SurrealQL014m_DataTypes_Idioms_BestPractices]:<#q014m---best-practices> "Best Practices"

[SurrealQL015_DataTypes_Literals]: <#q015---literals> "SurrealQL 🞂 Data type 🞂 Literals"

[SurrealQL016_DataTypes_NoneNull]: <#q016---none-and-null> "SurrealQL 🞂 Data type 🞂 None and null"

[SurrealQL017_DataTypes_Numbers]: <#q017---numbers> "SurrealQL 🞂 Data type 🞂 Numbers"

[SurrealQL018_DataTypes_Objects]: <#q018---objects> "SurrealQL 🞂 Data type 🞂 Objects"

[SurrealQL019_DataTypes_Ranges]: <#q019---ranges> "SurrealQL 🞂 Data type 🞂 Ranges"

[SurrealQL020_DataTypes_RecordIDs]: <#q020---record-ids> "SurrealQL 🞂 Data type 🞂 Record IDs"

[SurrealQL020a_DataTypes_RecordIDs_Types]: <#q020a---types-of-record-ids> "Types of Record IDs"

[SurrealQL020a1_DataTypes_RecordIDs_Random]: <#q020a1---random-ids> "Random IDs"

[SurrealQL020a2_DataTypes_RecordIDs_Text]: <#q020a2---text-record-ids> "Text Record IDs"

[SurrealQL020a3_DataTypes_RecordIDs_Numeric]: <#q020a3---numeric-record-ids> "Numeric Record IDs"

[SurrealQL020a4_DataTypes_RecordIDs_Array]: <#q020a4---array-based-record-ids> "Array-based Record IDs"

[SurrealQL020a5_DataTypes_RecordIDs_Performant]: <#q020a5---why-record-ranges-are-performant> "Why record ranges are performant"

[SurrealQL020a6_DataTypes_RecordIDs_Parameters]: <#q020a6---ids-made-with-parameters-and-function-calls> "IDs made with parameters and function calls"

[SurrealQL020b_DataTypes_RecordIDs_DefiningSchema]: <#q020b---defining-record-ids-in-a-schema> "Defining record IDs in a schema"

[SurrealQL020c_DataTypes_RecordIDs_Ranges]: <#q020c---record-ranges> "Record ranges"

[SurrealQL020d_DataTypes_RecordIDs_BestPractices]: <#q020d---tips-and-best-practices-for-record-ids> "Tips and best practices for record IDs"

[SurrealQL020d1_DataTypes_RecordIDs_ChooseRight]: <#q020d1---why-choose-the-right-record-id-format> "Why choose the right record ID format"

[SurrealQL020d2_DataTypes_RecordIDs_MeaningfulQuery]: <#q020d2---meaningful-sortable-ids-are-faster-to-query> "Meaningful sortable IDs are faster to query"

[SurrealQL020d3_DataTypes_RecordIDs_MatchesArray]: <#q020d3---move-exact-matches-in-array-based-record-ids-to-the-front> "Move exact matches in array-based record IDs to the front"

[SurrealQL020d4_DataTypes_RecordIDs_Incrementing]: <#q020d4---auto-incrementing-ids> "Auto-incrementing IDs"

[SurrealQL020d5_DataTypes_RecordIDs_RecordLinks]: <#q020d5---record-ids-are-record-links> "Record IDs are record links"

[SurrealQL020e_DataTypes_RecordIDs_Limitations]: <#q020e---limitations> "Limitations"

[SurrealQL020f_DataTypes_RecordIDs_LearnMore]: <#q020f---learn-more> "Learn more"

[SurrealQL021_DataTypes_RecordLinks]: <#q021---record-links> "SurrealQL 🞂 Data type 🞂 Record links"

[SurrealQL022_DataTypes_RecordReferences]: <#q022---record-references> "SurrealQL 🞂 Data type 🞂 Record references"

[SurrealQL023_DataTypes_Regex]: <#q023---regex> "SurrealQL 🞂 Data type 🞂 Regex"

[SurrealQL024_DataTypes_Sets]: <#q024---sets> "SurrealQL 🞂 Data type 🞂 Sets"

[SurrealQL025_DataTypes_Strings]: <#q025---strings> "SurrealQL 🞂 Data type 🞂 Strings"

[SurrealQL025a_DataTypes_Strings_Specifying]: <#q025a---specifying-data-type-literal-values-using-string-prefixes> "Specifying data type literal values using string prefixes"

[SurrealQL025a1_DataTypes_Strings_Overview]: <#q025a1---overview> "Overview"

[SurrealQL025a2_DataTypes_Strings_Record]: <#q025a2---record-id-literal-values-using-the-r-prefix> "Record ID literal values using the `r` prefix"

[SurrealQL025a3_DataTypes_Strings_Datetime]: <#q025a3---datetime-literal-values-using-the-d-prefix> "Datetime literal values using the `d` prefix"

[SurrealQL025a4_DataTypes_Strings_UUID]: <#q025a4---uuid-literal-values-with-the-u-prefix> "UUID literal values with the `u` prefix"

[SurrealQL025a5_DataTypes_Strings_Bytes]: <#q025a5---byte-values-using-the-b-prefix> "Byte values using the `b` prefix"

[SurrealQL025a6_DataTypes_Strings_Files]: <#q025a6---file-paths-using-the-f-prefix> "File paths using the `f` prefix*"

[SurrealQL025a7_DataTypes_Strings_Casting]: <#q025a7---string-prefixes-vs-casting> "String prefixes vs. casting"

[SurrealQL026_DataTypes_UUIDs]: <#q026---uuids> "SurrealQL 🞂 Data type 🞂 UUIDs"

[SurrealQL027_DataTypes_Values]: <#q027---values> "SurrealQL 🞂 Data type 🞂 Values"

[SurrealQL027a_DataTypes_Values_ComparingOrdering]: <#q027a---comparing-and-ordering-values> "Comparing and ordering values"

[SurrealQL027b_DataTypes_ValuesTruthiness]: <#q027b---values-and-truthiness> "Values and truthiness"

[SurrealQL028_Statements]: <#q028---statements> "SurrealQL 🞂 Statements"

[SurrealQL029_Statement_ACCESS]: <#q029---access-statement> "SurrealQL 🞂 Statement 🞂 `ACCESS`"

[SurrealQL030_Statement_ALTER]: <#q030---alter-statement> "SurrealQL 🞂 Statement 🞂 `ALTER`"

[SurrealQL031_Statement_ALTER_DATABASE]: <#q031---alter-database-statement> "SurrealQL 🞂 Statement 🞂 `ALTER` 🞂 `DATABASE`"

[SurrealQL032_Statement_ALTER_FIELD]: <#q032---alter-field-statement> "SurrealQL 🞂 Statement 🞂 `ALTER` 🞂 `FIELD`"

[SurrealQL033_Statement_ALTER_INDEX]: <#q033---alter-index-statement> "SurrealQL 🞂 Statement 🞂 `ALTER` 🞂 `INDEX`"

[SurrealQL034_Statement_ALTER_NAMESPACE]: <#q034---alter-namespace-statement> "SurrealQL 🞂 Statement 🞂 `ALTER` 🞂 `NAMESPACE`"

[SurrealQL035_Statement_ALTER_SEQUENCE]: <#q035---alter-sequence-statement> "SurrealQL 🞂 Statement 🞂 `ALTER` 🞂 `SEQUENCE`"

[SurrealQL036_Statement_ALTER_SYSTEM]: <#q036---alter-system-statement> "SurrealQL 🞂 Statement 🞂 `ALTER` 🞂 `SYSTEM`"

[SurrealQL037_Statement_ALTER_TABLE]: <#q037---alter-table-statement> "SurrealQL 🞂 Statement 🞂 `ALTER` 🞂 `TABLE`"

[SurrealQL038_Statement_BEGIN]: <#q038---begin-statement> "SurrealQL 🞂 Statement 🞂 `BEGIN`"

[SurrealQL039_Statement_BREAK]: <#q039---break-statement> "SurrealQL 🞂 Statement 🞂 `BREAK`"

[SurrealQL040_Statement_CANCEL]: <#q040---cancel-statement> "SurrealQL 🞂 Statement 🞂 `CANCEL`"

[SurrealQL041_Statement_COMMIT]: <#q041---commit-statement> "SurrealQL 🞂 Statement 🞂 `COMMIT`"

[SurrealQL042_Statement_CONTINUE]: <#q042---continue-statement> "SurrealQL 🞂 Statement 🞂 `CONTINUE`"

[SurrealQL043_Statement_CREATE]: <#q043---create-statement> "SurrealQL 🞂 Statement 🞂 `CREATE`"

[SurrealQL044_Statement_DEFINE]: <#q044---define-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE`"

[SurrealQL045_Statement_DEFINE_ACCESS]: <#q045---define-access-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `ACCESS`"

[SurrealQL046_Statement_DEFINE_ACCESSTYPEBEARER]: <#q046---define-access--type-bearer> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `ACCESS` 🞂 `TYPE BEARER`"

[SurrealQL047_Statement_DEFINE_ACCESSTYPEJWT]: <#q047---define-access--type-jwt> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `ACCESS` 🞂 `TYPE JWT`"

[SurrealQL048_Statement_DEFINE_ACCESSTYPERECORD]: <#q048---define-access--type-record> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `ACCESS` 🞂 `TYPE RECORD`"

[SurrealQL049_Statement_DEFINE_ANALYZER]: <#q049---define-analyzer-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `ANALYZER`"

[SurrealQL050_Statement_DEFINE_API]: <#q050---define-api-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `API`"

[SurrealQL051_Statement_DEFINE_BUCKET]: <#q051---define-bucket-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `BUCKET`"

[SurrealQL052_Statement_DEFINE_CONFIG]: <#q052---define-config-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `CONFIG`"

[SurrealQL053_Statement_DEFINE_DATABASE]: <#q053---define-database-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `DATABASE`"

[SurrealQL054_Statement_DEFINE_EVENT]: <#q054---define-event-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `EVENT`"

[SurrealQL055_Statement_DEFINE_FIELD]: <#q055---define-field-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `FIELD`"

[SurrealQL056_Statement_DEFINE_FUNCTION]: <#q056---define-function-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `FUNCTION`"

[SurrealQL057_Statement_DEFINE_INDEX]: <#q057---define-index-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `INDEX`"

[SurrealQL058_Statement_DEFINE_MODULE]: <#q058---define-module-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `MODULE`"

[SurrealQL059_Statement_DEFINE_NAMESPACE]: <#q059---define-namespace-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `NAMESPACE`"

[SurrealQL060_Statement_DEFINE_PARAM]: <#q060---define-param-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `PARAM`"

[SurrealQL061_Statement_DEFINE_SCOPE]: <#q061---define-scope-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `SCOPE`"

[SurrealQL062_Statement_DEFINE_SEQUENCE]: <#q062---define-sequence-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `SEQUENCE`"

[SurrealQL063_Statement_DEFINE_TABLE]: <#q063---define-table-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `TABLE`"

[SurrealQL064_Statement_DEFINE_TOKEN]: <#q064---define-token-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `TOKEN`"

[SurrealQL065_Statement_DEFINE_USER]: <#q065---define-user-statement> "SurrealQL 🞂 Statement 🞂 `DEFINE` 🞂 `USER`"

[SurrealQL066_Statement_DELETE]: <#q066---delete-statement> "SurrealQL 🞂 Statement 🞂 `DELETE`"

[SurrealQL067_Statement_EXPLAIN]: <#q067---explain-statement> "SurrealQL 🞂 Statement 🞂 `EXPLAIN`"

[SurrealQL068_Statement_FOR]: <#q068---for-statement> "SurrealQL 🞂 Statement 🞂 `FOR`"

[SurrealQL069_Statement_IF_ELSE]: <#q069---if-else-statement> "SurrealQL 🞂 Statement 🞂 `IF ELSE`"

[SurrealQL070_Statement_INFO]: <#q070---info-statement> "SurrealQL 🞂 Statement 🞂 `INFO`"

[SurrealQL071_Statement_INSERT]: <#q071---insert-statement> "SurrealQL 🞂 Statement 🞂 `INSERT`"

[SurrealQL072_Statement_KILL]: <#q072---kill-statement> "SurrealQL 🞂 Statement 🞂 `KILL`"

[SurrealQL073_Statement_LET]: <#q073---let-statement> "SurrealQL 🞂 Statement 🞂 `LET`"

[SurrealQL074_Statement_LIVE_SELECT]: <#q074---live-select-statement> "SurrealQL 🞂 Statement 🞂 `LIVE SELECT`"

[SurrealQL075_Statement_REBUILD]: <#q075---rebuild-statement> "SurrealQL 🞂 Statement 🞂 `REBUILD`"

[SurrealQL076_Statement_RELATE]: <#q076---relate-statement> "SurrealQL 🞂 Statement 🞂 `RELATE`"

[SurrealQL077_Statement_REMOVE]: <#q077---remove-statement> "SurrealQL 🞂 Statement 🞂 `REMOVE`"

[SurrealQL078_Statement_RETURN]: <#q078---return-statement> "SurrealQL 🞂 Statement 🞂 `RETURN`"

[SurrealQL079_Statement_SELECT]: <#q079---select-statement> "SurrealQL 🞂 Statement 🞂 `SELECT`"

[SurrealQL080_Statement_SHOW]: <#q080---show-statement> "SurrealQL 🞂 Statement 🞂 `SHOW`"

[SurrealQL081_Statement_SLEEP]: <#q081---sleep-statement> "SurrealQL 🞂 Statement 🞂 `SLEEP`"

[SurrealQL082_Statement_THROW]: <#q082---throw-statement> "SurrealQL 🞂 Statement 🞂 `THROW`"

[SurrealQL083_Statement_UPDATE]: <#q083---update-statement> "SurrealQL 🞂 Statement 🞂 `UPDATE`"

[SurrealQL084_Statement_UPSERT]: <#q084---upsert-statement> "SurrealQL 🞂 Statement 🞂 `UPSERT`"

[SurrealQL085_Statement_USE]: <#q085---use-statement> "SurrealQL 🞂 Statement 🞂 `USE`"

[SurrealQL086_Clauses]: <#q086---clauses> "SurrealQL 🞂 Clauses"

[SurrealQL087_Clauses_EXPLAIN]: <#q087---explain-clauses> "SurrealQL 🞂 Clauses 🞂 `EXPLAIN`"

[SurrealQL088_Clauses_FETCH]: <#q088---fetch-clauses> "SurrealQL 🞂 Clauses 🞂 `FETCH`"

[SurrealQL089_Clauses_FROM]: <#q089---from-clauses> "SurrealQL 🞂 Clauses 🞂 `FROM`"

[SurrealQL090_Clauses_GROUP_BY]: <#q090---group-by-clauses> "SurrealQL 🞂 Clauses 🞂 `GROUP BY`"

[SurrealQL091_Clauses_LIMIT]: <#q091---limit-clauses> "SurrealQL 🞂 Clauses 🞂 `LIMIT`"

[SurrealQL092_Clauses_OMIT]: <#q092---omit-clauses> "SurrealQL 🞂 Clauses 🞂 `OMIT`"

[SurrealQL093_Clauses_ORDER_BY]: <#q093---order-by-clauses> "SurrealQL 🞂 Clauses 🞂 `ORDER BY`"

[SurrealQL094_Clauses_SPLIT]: <#q094---split-clauses> "SurrealQL 🞂 Clauses 🞂 `SPLIT`"

[SurrealQL095_Clauses_WHERE]: <#q095---where-clauses> "SurrealQL 🞂 Clauses 🞂 `WHERE`"

[SurrealQL096_Clauses_WITH]: <#q096---with-clauses> "SurrealQL 🞂 Clauses 🞂 `WITH`"

[SurrealQL097_Parameters]: <#q097---parameters> "SurrealQL 🞂 Parameters"

[SurrealQL098_Functions]: <#q098---functions> "SurrealQL 🞂 Functions"

[SurrealQL099_FunctionsDatabase]: <#q099---database-functions> "SurrealQL 🞂 Functions 🞂 Database Functions"

[SurrealQL100_FunctionsDatabase_API]: <#q100---api-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 API functions"

[SurrealQL101_FunctionsDatabase_Array]: <#q101---array-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Array functions"

[SurrealQL101aa_FunctionsDatabase_Array_add]: <#q101aa---arrayadd> "`array::add`"

[SurrealQL101ab_FunctionsDatabase_Array_all]: <#q101ab---arrayall> "`array::all`"

[SurrealQL101ac_FunctionsDatabase_Array_any]: <#q101ac---arrayany> "`array::any`"

[SurrealQL101ad_FunctionsDatabase_Array_at]: <#q101ad---arrayat> "`array::at`"

[SurrealQL101ae_FunctionsDatabase_Array_append]: <#q101ae---arrayappend> "`array::append`"

[SurrealQL101af_FunctionsDatabase_Array_booleanAND]: <#q101af---arrayboolean_and> "`array::boolean_and`"

[SurrealQL101ag_FunctionsDatabase_Array_booleanOR]: <#q101ag---arrayboolean_or> "`array::boolean_or`"

[SurrealQL101ah_FunctionsDatabase_Array_booleanXOR]: <#q101ah---arrayboolean_xor> "`array::boolean_xor`"

[SurrealQL101ai_FunctionsDatabase_Array_booleanNOT]: <#q101ai---arrayboolean_not> "`array::boolean_not`"

[SurrealQL101aj_FunctionsDatabase_Array_combine]: <#q101aj---arraycombine> "`array::combine`"

[SurrealQL101ak_FunctionsDatabase_Array_complement]: <#q101ak---arraycomplement> "`array::complement`"

[SurrealQL101al_FunctionsDatabase_Array_concat]: <#q101al---arrayconcat> "`array::concat`"

[SurrealQL101am_FunctionsDatabase_Array_clump]: <#q101am---arrayclump> "`array::clump`"

[SurrealQL101an_FunctionsDatabase_Array_difference]: <#q101an---arraydifference> "`array::difference`"

[SurrealQL101ao_FunctionsDatabase_Array_distinct]: <#q101ao---arraydistinct> "`array::distinct`"

[SurrealQL101ap_FunctionsDatabase_Array_fill]: <#q101ap---arrayfill> "`array::fill`"

[SurrealQL101aq_FunctionsDatabase_Array_filter]: <#q101aq---arrayfilter> "`array::filter`"

[SurrealQL101ar_FunctionsDatabase_Array_filterIndex]: <#q101ar---arrayfilter_index> "`array::filter_index`"

[SurrealQL101as_FunctionsDatabase_Array_find]: <#q101as---arrayfind> "`array::find`"

[SurrealQL101at_FunctionsDatabase_Array_findIndex]: <#q101at---arrayfind_index> "`array::find_index`"

[SurrealQL101au_FunctionsDatabase_Array_first]: <#q101au---arrayfirst> "`array::first`"

[SurrealQL101av_FunctionsDatabase_Array_flatten]: <#q101av---arrayflatten> "`array::flatten`"

[SurrealQL101aw_FunctionsDatabase_Array_fold]: <#q101aw---arrayfold> "`array::fold`"

[SurrealQL101ax_FunctionsDatabase_Array_group]: <#q101ax---arraygroup> "`array::group`"

[SurrealQL101ay_FunctionsDatabase_Array_insert]: <#q101ay---arrayinsert> "`array::insert`"

[SurrealQL101az_FunctionsDatabase_Array_intersect]: <#q101az---arrayintersect> "`array::intersect`"

[SurrealQL101ba_FunctionsDatabase_Array_isEmpty]: <#q101ba---arrayis_empty> "`array::is_empty`"

[SurrealQL101bb_FunctionsDatabase_Array_join]: <#q101bb---arrayjoin> "`array::join`"

[SurrealQL101bc_FunctionsDatabase_Array_last]: <#q101bc---arraylast> "`array::last`"

[SurrealQL101bd_FunctionsDatabase_Array_len]: <#q101bd---arraylen> "`array::len`"

[SurrealQL101be_FunctionsDatabase_Array_logicalAND]: <#q101be---arraylogical_and> "`array::logical_and`"

[SurrealQL101bf_FunctionsDatabase_Array_logicalOR]: <#q101bf---arraylogical_or> "`array::logical_or`"

[SurrealQL101bg_FunctionsDatabase_Array_logicalXOR]: <#q101bg---arraylogical_xor> "`array::logical_xor`"

[SurrealQL101bh_FunctionsDatabase_Array_map]: <#q101bh---arraymap> "`array::map`"

[SurrealQL101bi_FunctionsDatabase_Array_max]: <#q101bi---arraymax> "`array::max`"

[SurrealQL101bj_FunctionsDatabase_Array_min]: <#q101bj---arraymin> "`array::min`"

[SurrealQL101bk_FunctionsDatabase_Array_matches]: <#q101bk---arraymatches> "`array::matches`"

[SurrealQL101bl_FunctionsDatabase_Array_pop]: <#q101bl---arraypop> "`array::pop`"

[SurrealQL101bm_FunctionsDatabase_Array_prepend]: <#q101bm---arrayprepend> "`array::prepend`"

[SurrealQL101bn_FunctionsDatabase_Array_push]: <#q101bn---arraypush> "`array::push`"

[SurrealQL101bo_FunctionsDatabase_Array_range]: <#q101bo---arrayrange> "`array::range`"

[SurrealQL101bp_FunctionsDatabase_Array_reduce]: <#q101bp---arrayreduce> "`array::reduce`"

[SurrealQL101bq_FunctionsDatabase_Array_remove]: <#q101bq---arrayremove> "`array::remove`"

[SurrealQL101br_FunctionsDatabase_Array_repeat]: <#q101br---arrayrepeat> "`array::repeat`"

[SurrealQL101bs_FunctionsDatabase_Array_reverse]: <#q101bs---arrayreverse> "`array::reverse`"

[SurrealQL101bt_FunctionsDatabase_Array_sequence]: <#q101bt---arraysequence> "`array::sequence`"

[SurrealQL101bu_FunctionsDatabase_Array_shuffle]: <#q101bu---arrayshuffle> "`array::shuffle`"

[SurrealQL101bv_FunctionsDatabase_Array_slice]: <#q101bv---arrayslice> "`array::slice`"

[SurrealQL101bw_FunctionsDatabase_Array_sort]: <#q101bw---arraysort> "`array::sort`"

[SurrealQL101bx_FunctionsDatabase_Array_sortLexical]: <#q101bx---arraysort_lexical> "`array::sort_lexical`"

[SurrealQL101by_FunctionsDatabase_Array_sortNatural]: <#q101by---arraysort_natural> "`array::sort_natural`"

[SurrealQL101bz_FunctionsDatabase_Array_sortNaturalLexical]: <#q101bz---arraysort_natural_lexical> "`array::sort_natural_lexical`"

[SurrealQL101ca_FunctionsDatabase_Array_sortASC]: <#q101ca---arraysortasc> "`array::sort::asc`"

[SurrealQL101cb_FunctionsDatabase_Array_sortDESC]: <#q101cb---arraysortdesc> "`array::sort::desc`"

[SurrealQL101cc_FunctionsDatabase_Array_swap]: <#q101cc---arrayswap> "`array::swap`"

[SurrealQL101cd_FunctionsDatabase_Array_transpose]: <#q101cd---arraytranspose> "`array::transpose`"

[SurrealQL101ce_array_union]: <#q101ce---arrayunion> "`array::union`"

[SurrealQL101cf_array_windows]: <#q101cf---arraywindows> "`array::windows`"

[SurrealQL102_FunctionsDatabase_Bytes]: <#q102---bytes-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Bytes functions"

[SurrealQL103_FunctionsDatabase_Count]: <#q103---count-function> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Count function"

[SurrealQL104_FunctionsDatabase_Crypto]: <#q104---crypto-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Crypto functions"

[SurrealQL105_FunctionsDatabase_Duration]: <#q105---duration-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Duration functions"

[SurrealQL106_FunctionsDatabase_Encoding]: <#q106---encoding-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Encoding functions"

[SurrealQL107_FunctionsDatabase_File]: <#q107---file-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 File functions"

[SurrealQL108_FunctionsDatabase_Geo]: <#q108---geo-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Geo functions"

[SurrealQL109_FunctionsDatabase_HTTP]: <#q109---http-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 HTTP functions"

[SurrealQL110_FunctionsDatabase_Math]: <#q110---math-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Math functions"

[SurrealQL111_FunctionsDatabase_Meta]: <#q111---meta-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Meta functions"

[SurrealQL112_FunctionsDatabase_Not]: <#q112---not-function> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Not function"

[SurrealQL113_FunctionsDatabase_Object]: <#q113---object-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Object functions"

[SurrealQL114_FunctionsDatabase_Parse]: <#q114---parse-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Parse functions"

[SurrealQL115_FunctionsDatabase_Rand]: <#q115---rand-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Rand functions"

[SurrealQL116_FunctionsDatabase_Record]: <#q116---record-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Record functions"

[SurrealQL117_FunctionsDatabase_Search]: <#q117---search-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Search functions"

[SurrealQL118_FunctionsDatabase_Sequence]: <#q118---sequence-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Sequence functions"

[SurrealQL119_FunctionsDatabase_Session]: <#q119---session-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Session functions"

[SurrealQL120_FunctionsDatabase_Set]: <#q120---set-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Set functions"

[SurrealQL121_FunctionsDatabase_Sleep]: <#q121---sleep-function> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Sleep function"

[SurrealQL122_FunctionsDatabase_String]: <#q122---string-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 String Functions"

[SurrealQL123_FunctionsDatabase_Time]: <#q123---time-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Time Functions"

[SurrealQL124_FunctionsDatabase_Type]: <#q124---type-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Type Functions"

[SurrealQL125_FunctionsDatabase_Value]: <#q125---value-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Value functions"

[SurrealQL126_FunctionsDatabase_Vector]: <#q126---vector-functions> "SurrealQL 🞂 Functions 🞂 Database Functions 🞂 Vector functions"

[SurrealQL127_FunctionsEmbedded]: <#q127---embedded-scripting-functions> "SurrealQL 🞂 Functions 🞂 Embedded scripting functions"

[SurrealQL128_FunctionsEmbedded_Arguments]: <#q128---arguments> "SurrealQL 🞂 Functions 🞂 Scripting Functions 🞂 Arguments"

[SurrealQL129_FunctionsEmbedded_BuiltIn]: <#q129---built-in-functions> "SurrealQL 🞂 Functions 🞂 Scripting Functions 🞂 Built-in functions"

[SurrealQL130_FunctionsEmbedded_Context]: <#q130---function-context> "SurrealQL 🞂 Functions 🞂 Scripting Functions 🞂 Function context"

[SurrealQL131_FunctionsEmbedded_TypeConversion]: <#q131---type-conversion> "SurrealQL 🞂 Functions 🞂 Scripting Functions 🞂 Type conversion"

[SurrealQL132_FunctionsEmbedded_SurrealQL]: <#q132---surrealql-functions> "SurrealQL 🞂 Functions 🞂 Scripting Functions 🞂 SurrealQL functions"

[SurrealQL133_FunctionsML]: <#q133---machine-learning-functions> "SurrealQL 🞂 Functions 🞂 Machine Learning functions"

[SurrealQL134_FunctionsML_Extended]: <#q134---machine-learning-functions> "SurrealQL 🞂 Functions 🞂 ML Functions 🞂 Machine Learning functions"

[SurrealQL135_Transactions]: <#q135---transactions> "SurrealQL 🞂 Transactions"

[SurrealQL136_Comments]: <#q136---comments> "SurrealQL 🞂 Comments"

[surrealdb_docs_3x_surrealql]: <https://surrealdb.com/docs/3.x/surrealql>

[surrealdb_docs_3x_surrealql_demo]: <https://surrealdb.com/docs/3.x/surrealql/demo>

[surrealdb_docs_3x_surrealql_operators]: <https://surrealdb.com/docs/3.x/surrealql/operators>

[surrealdb_docs_3x_surrealql_datamodel]: <https://surrealdb.com/docs/3.x/surrealql/datamodel>

[surrealdb_docs_3x_surrealql_datamodel_arrays]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/arrays>

[surrealdb_docs_3x_surrealql_datamodel_booleans]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/booleans>

[surrealdb_docs_3x_surrealql_datamodel_bytes]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/bytes>

[surrealdb_docs_3x_surrealql_datamodel_casting]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/casting>

[surrealdb_docs_3x_surrealql_datamodel_closures]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/closures>

[surrealdb_docs_3x_surrealql_datamodel_datetimes]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/datetimes>

[surrealdb_docs_3x_surrealql_datamodel_files]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/files>

[surrealdb_docs_3x_surrealql_datamodel_formatters]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/formatters>

[surrealdb_docs_3x_surrealql_datamodel_futures]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/futures>

[surrealdb_docs_3x_surrealql_datamodel_geometries]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/geometries>

[surrealdb_docs_3x_surrealql_datamodel_idioms]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/idioms>

[surrealdb_docs_3x_surrealql_datamodel_literals]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/literals>

[surrealdb_docs_3x_surrealql_datamodel_none-and-null]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/none-and-null>

[surrealdb_docs_3x_surrealql_datamodel_numbers]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/numbers>

[surrealdb_docs_3x_surrealql_datamodel_objects]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/objects>

[surrealdb_docs_3x_surrealql_datamodel_ranges]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/ranges>

[surrealdb_docs_3x_surrealql_datamodel_ids]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/ids>

[surrealdb_docs_3x_surrealql_datamodel_records]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/records>

[surrealdb_docs_3x_surrealql_datamodel_references]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/references>

[surrealdb_docs_3x_surrealql_datamodel_regex]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/regex>

[surrealdb_docs_3x_surrealql_datamodel_sets]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/sets>

[surrealdb_docs_3x_surrealql_datamodel_strings]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/strings>

[surrealdb_docs_3x_surrealql_datamodel_uuid]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/uuid>

[surrealdb_docs_3x_surrealql_datamodel_values]: <https://surrealdb.com/docs/3.x/surrealql/datamodel/values>

[surrealdb_docs_3x_surrealql_functions]: <https://surrealdb.com/docs/3.x/surrealql/functions>

[surrealdb_docs_3x_surrealql_functions_database_array]: <https://surrealdb.com/docs/3.x/surrealql/functions/database/array>

[surrealdb_docs_3x_surrealql_transactions]: <https://surrealdb.com/docs/3.x/surrealql/transactions>

[surrealdb_docs_3x_surrealql_comments]: <https://surrealdb.com/docs/3.x/surrealql/comments>

[getSURQL_001]: <https://datasets.surrealdb.com/surreal-deal-store.surql>

[getSURQL_002]: <https://datasets.surrealdb.com/surreal-deal-store-mini.surql>

[trySURQL_001]: <https://app.surrealdb.com/mini?query=--+Query+1%3A+Using+record+links+to+select+from+the+seller+table+%0ASELECT%0A++name%2C%0A++seller.name%0AFROM+product+LIMIT+4%3B%0A%0A%0A--+Query+2%3A+Using+graph+relations+to+select+from+the+person+and+product+table%0ASELECT%0A++++time.created_at as order_date%2C%0A++++product_name%2C%0A++++%3C-person.name+as+person_name%2C%0A++++-%3Eproduct.details%0AFROM+order+LIMIT+4%3B%0A%0A%0A--+Query+3%3A+Conditional+filtering+based+on+an+embedded+object+property.%0ASELECT+%0A++name%2C%0A++email+%0AFROM+person+%0AWHERE+address.country+%3F%3D+%22England%22+LIMIT+4%3B%09%0A%0A%0A--+Query+4%3A+Conditional+filtering+using+relationships.%0ASELECT+*+FROM+review%0AWHERE+-%3Eproduct.sub_category+%3F%3D+%22Activewear%22+LIMIT+4%3B%0A%0A%0A--+Query+5%3A+Count+orders+based+on+order+status%0ASELECT+count%28%29+FROM+order%0AWHERE+order_status+IN+%5B+%22processed%22%2C+%22shipped%22%5D%0AGROUP+ALL+LIMIT+4%3B%0A%0A%0A--+Query+6%3A+Get+a+deduplicated+list+of+products+that+were+ordered%0ASELECT+%0A++++array%3A%3Adistinct%28product_name%29+as+ordered_products%0AFROM+order%0AGROUP+ALL+LIMIT+4%3B%0A%0A%0A--+Query+7%3A+Get+the+average+price+per+product+category%0ASELECT+%0A++++-%3Eproduct.category+AS+product_category%2C%0A++++math%3A%3Amean%28price%29+AS+avg_price%0AFROM+order%0AGROUP+BY+product_category%0AORDER+BY+avg_price+DESC+LIMIT+4%3B%0A%0A%0A--+Query+8%3A+encapsulating+logic+in+a+function%0ARETURN+fn%3A%3Anumber_of_unfulfilled_orders%28%29%3B%0A%0A%0A--+Query+9%3A+using+a+custom+fuction+for+currency+conversion%0ASELECT+%0A++++product_name%2C%0A++++fn%3A%3Apound_to_usd%28price%29+AS+price_usd%0AFROM+order+LIMIT+4%3B&dataset=surreal-deal-store&orientation=horizontal> "SurrealistMini"

[yt01]: <https://www.youtube.com/watch?v=TyX45cyZ-W0> "SurrealDB: Document-Style Relationships in SurrealDB"

[yt02]: <https://www.youtube.com/watch?v=c0cqmWRYP8c> "SurrealDB Stream #4: Record IDs with Tobie & Alex"

[net__SurrealDB_Store]: <https://surrealdb.store/>

[net__SurrealistMini]: <https://app.surrealdb.com/mini>

[net__RFC_7946]: <https://www.rfc-editor.org/rfc/rfc7946>

[net__RFC_3339]: <https://datatracker.ietf.org/doc/html/rfc3339>

[net__wiki_float64]: <https://en.wikipedia.org/wiki/Double-precision_floating-point_format>

[net__wiki_decimal128]: <https://en.wikipedia.org/wiki/Decimal128_floating-point_format>

[net__mdn_Logical_AND]: <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_AND>

[net__mdn_logical_OR]: <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_OR>

[net__mdn_logical_XOR]: <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_XOR>

[net__mdn_Bitwise_AND]: <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_AND>

[net__mdn_Bitwise_OR]: <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_OR>

[net__mdn_Bitwise_XOR]: <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_XOR>

[net__mdn_Bitwise_NOT]: <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_NOT>

[net__geojson]: <https://geojson.org/>

[net__opendatasoft_geonames]: <https://public.opendatasoft.com/explore/dataset/geonames-all-cities-with-a-population-1000/export/?disjunctive.cou_name_en&sort=name>

[ico__SurrealQL]: <https://surrealdb.com/docs/_astro/ql-light.70PDiXa1_Z2othTk.webp>

[img__demo_overview]: <https://surrealdb.com/docs/_astro/surreal-deal-store.C2015pX2_Z2r7lvb.webp>
[img__parse_error]: <https://surrealdb.com/docs/_astro/surrealql-parse-error.g1VFFr3O_1ncJQv.webp>
[img__graph_view]: <https://surrealdb.com/docs/_astro/graph_view.B3oQAj0s_Z12bT6L.webp>

[SurrealDB_cli]: </docs/surrealdb/cli> "CLI"
[SurrealDB_cli_import]: </docs/surrealdb/cli/import> "import"
[SurrealDB_cli_start]: </docs/surrealdb/cli/start>

[brakuje_func_db#method-syntax]:  </docs/surrealql/functions/database#method-syntax>
[brakuje_func_db_encoding#encodingcbordecod]: </docs/surrealql/functions/database/encoding#encodingcbordecode>
[brakuje_func_db_file]:           </docs/surrealql/functions/database/file>
[brakuje_func_db_geo]: </docs/surrealql/functions/database/geo>
[brakuje_func_db_geo#geodistance]: </docs/surrealql/functions/database/geo#geodistance>
[brakuje_func_db_math#mathmax]:  </docs/surrealql/functions/database/math#mathmax>
[brakuje_func_db_math#mathmin]:  </docs/surrealql/functions/database/math#mathmin>
[brakuje_func_db_object]:           </docs/surrealql/functions/database/object>
[brakuje_func_db_object#objectvalues]:</docs/surrealql/functions/database/object#objectvalues>
[brakuje_func_db_record#recordid]:   </docs/surrealql/functions/database/record#recordid>
[brakuje_func_db_rand#randuuidv4]: </docs/surrealql/functions/database/rand#randuuidv4>
[brakuje_func_db_string#stringlen]: </docs/surrealql/functions/database/string#stringlen>
[brakuje_func_db_string#stringuppercase]: </docs/surrealql/functions/database/string#stringuppercase>
[brakuje_func_db_string#stringuppercase]: </docs/surrealql/functions/database/string#stringuppercase>
[brakuje_func_db_string#stringisdatetime]: </docs/surrealql/functions/database/string#stringisdatetime>
[brakuje_func_db_time]:          </docs/surrealql/functions/database/time>
[brakuje_func_db_time#timemax]:  </docs/surrealql/functions/database/time#timemax>
[brakuje_func_db_time#timemin]:  </docs/surrealql/functions/database/time#timemin>
[brakuje_func_db_time#timeformat]:  </docs/surrealql/functions/database/time#timeformat>
[brakuje_func_db_type#typeis_geometry]:  </docs/surrealql/functions/database/type#typeis_geometry>
[brakuje_func_db_type#typeis_string]:  </docs/surrealql/functions/database/type#typeis_strin>
[brakuje_func_db_type#typeis_record]:  </docs/surrealql/functions/database/type#typeis_record>
[brakuje_func_db_type#typerecord]:  </docs/surrealql/functions/database/type#typerecord>
[brakuje_func_db_value#chain]:   </docs/surrealql/functions/database/value#chain>

[brakuje_model_idioms#destructuring]:   </docs/surrealql/datamodel/idioms#destructuring>

[brakuje_stat_def_bucket]: </docs/surrealql/statements/define/bucket>
[brakuje_stat_def_field]: </docs/surrealql/statements/define/field>
[brakuje_stat_def_field#computed-fields]: </docs/surrealql/statements/define/field#computed-fields>
[brakuje_stat_def_function]: </docs/surrealql/statements/define/function>
[brakuje_stat_select]: </docs/surrealql/statements/selectt>
[brakuje_stat_select#basic-usage]: </docs/surrealql/statements/selectt#basic-usage>
[brakuje_stat_for]: </docs/surrealql/statements/for>
[brakuje_stat_begin]: </docs/surrealql/statements/begin>
[brakuje_stat_create]: </docs/surrealql/statements/create>
[brakuje_stat_update]: </docs/surrealql/statements/update>
[brakuje_stat_relate]: </docs/surrealql/statements/relate>
[brakuje_stat_upsert]: </docs/surrealql/statements/upsert>
[brakuje_stat_delete]: </docs/surrealql/statements/delete>
[brakuje_stat_throw]: </docs/surrealql/statements/throw>
[brakuje_stat_insert#example-usage]: </docs/surrealql/statements/insert#example-usage>

[brakuje_parameters#parent-this]: </docs/surrealql/parameters#parent-this>

[brakuje_blog_recordIDS]: </blog/the-life-changing-magic-of-surrealdb-record-ids#the-performance-at-scale>
[brakuje_blog_visualisation]: </blog/whats-new-in-surrealist-3-2#graph-visualisation>
[brakuje_blog_visualisationGraphView]: </blog/visualising-your-data-with-surrealists-graph-view>
