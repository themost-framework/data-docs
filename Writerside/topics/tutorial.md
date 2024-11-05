# Create a new data application

[@themost/data](https://github.com/themost-framework/data) is a data access library for Node.js. 
It provides a simple and easy-to-use API for working with data. 
In this tutorial, you will learn how to create a new data application using the `@themost/data` module.

* Use the `@themost/data` library to create a new data application
* Create your first data model

## Before you start

Before you start this tutorial, you need to have Node.js installed on your machine.

Make sure that:
- Install @themost/data module and its dependencies
- Have a basic understanding of Node.js and JavaScript

## Install the @themost/data module and its dependencies

To install the `@themost/data` module and its dependencies, run the following command in your terminal:

```bash
npm install @themost/data @themost/query @themost/common @themost/event @themost/xml
```

1. Create index.js file

```javascript
const { DataApplication } = require("@themost/data");
const { TraceUtils } = require("@themost/common");
// assert module is used here for development purposes only
const assert = require("node:assert");
//  create data application
const app = new DataApplication(process.cwd());
assert.ok(app instanceof DataApplication);

TraceUtils.info(
`A new data application has been create under ${app.configuration.getExecutionPath()}`
);
```

2. Step with a [link](https://www.jetbrains.com)

3. Final step in part 1.

## Create your first data model

This is the second part of the tutorial:

1.Define a new data model


2. Configure data adapter

[@themost/data](https://github/com/themost-framework/data) application as a database-agnostic environment allows you to define and use different data storages like:

- SQLite [@themost/sqlite](https://github.com/themost-framework/sqlite)
- MySQL [@themost/mysql](https://github.com/themost-framework/mysql)
- PostgreSQL [@themost/postgres](https://github.com/themost-framework/pg)
- MSSQL [@themost/mssql](https://github.com/themost-framework/mssql)
- Oracle  [@themost/oracle](https://github.com/themost-framework/oracle)

Modify application and define a new data adapter:

```javascript

```


```javascript


3. Create a new data context

```javascript

```

## What you've learned {id="what-learned"}

This tutorial has shown you how to create a new data application using the `@themost/data` module.
It also showed you how to create your first data model and configure a data adapter.

<seealso>
<!--Give some related links to how-to articles-->
</seealso>
