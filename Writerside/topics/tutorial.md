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

### Define a new data model

A data model is a JSON schema which represents an entity type like User, Product, Order etc.
[@themost/data](https://github.com/themost-framework/data) introduces an extensible schema which describes both data
structure and data access requirements like relationships, constraints, privileges etc.

The following example shows how to define a new simple data model for a Customer entity:

This schema is a presentation of a Customer entity as it is already defined
in [W3Schools SQL examples](https://www.w3schools.com/sql/default.asp).

```json
{
  "$schema": "https://themost-framework.github.io/themost/models/2018/2/schema.json",
  "@id": "https://www.w3schools.com/Customer",
  "name": "Customer",
  "title": "A customer entity",
  "source": "Customers",
  "view": "Customers",
  "version": "1.0.0",
  "fields": [
    {
      "name": "customerID",
      "type": "Integer",
      "nullable": false,
      "primary": true,
      "value": "javascript:return this.newid();"
    },
    {
      "name": "customerName",
      "type": "Text",
      "nullable": false,
      "size": 255
    },
    {
      "name": "contactName",
      "type": "Text",
      "size": 255
    },
    {
      "name": "address",
      "type": "Text",
      "size": 255
    },
    {
      "name": "city",
      "type": "Text",
      "size": 255
    },
    {
      "name": "postalCode",
      "type": "Text",
      "size": 255
    },
    {
      "name": "country",
      "type": "Text",
      "size": 255
    }
  ],
  "constraints": [],
  "eventListeners": [],
  "privileges": [
    {
      "mask": 15,
      "type": "global",
      "account": "Administrators"
    },
    {
      "mask": 15,
      "type": "global",
      "account": "Contributors"
    }
  ]
}
```

### Include data model schema

By default, any data application looks for data models in the `config/models` directory relative to the current execution path.
Move the Customer.json file to the `config/models` directory to make it available to the application.

```bash
workspace ✗ ls config/models 
    Customer.json
```

## Configure data adapter

[@themost/data](https://github/com/themost-framework/data) application as a database-agnostic environment allows you to
define and use different data storages like:

- SQLite [@themost/sqlite](https://github.com/themost-framework/sqlite)
- MySQL [@themost/mysql](https://github.com/themost-framework/mysql)
- PostgreSQL [@themost/pg](https://github.com/themost-framework/pg)
- MSSQL [@themost/mssql](https://github.com/themost-framework/mssql)
- Oracle  [@themost/oracle](https://github.com/themost-framework/oracle)

Modify application and define a new data adapter:

```javascript
const { SqliteAdapter } = require("@themost/sqlite");
/**
 * get data configuration
 * @type {import('@themost/data').DataConfigurationStrategy}
 */
const conf = app.configuration.getStrategy(DataConfigurationStrategy);

conf.adapterTypes.set("sqlite", {
  name: "SQLite",
  invariantName: "sqlite",
  type: SqliteAdapter,
});

// add default data adapter
conf.adapters.push({
  name: "development", // set name
  default: true, // set as default
  invariantName: "sqlite", // set type
  options: {
    database: "db/local_dev.db", // define sqlite database path
  },
});
```


## Create data context

Before accessing data, you need to create a new data context instance:

```javascript
const { DataContext } = require("@themost/data");
const context = app.createContext();
const customer = await context.model('Customer')
    .where('customerName').equal('Alfreds Futterkiste').getItem();
```

## What you've learned {id="what-learned"}

This tutorial has shown you how to create a new data application using the `@themost/data` module.
It also showed you how to create your first data model, configure a data adapter and finally access data provided by the application.

<seealso>
<!--Give some related links to how-to articles-->
</seealso>
