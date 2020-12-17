---
description: >-
  The parsers.dev API is organized around REST with JSON request and responses
  and uses standard HTTP response codes.
---

# API Reference \(beta\)

{% hint style="danger" %}
The current **API** status is **BETA**. Minor changes are possible before leaving this status. After fixing the state, JSON-schemas will be published, with a description of the formats of requests and responses
{% endhint %}

## Authentication

The **parsers.dev API** uses API key to authenticate requests. You can view and manage your API key in the [**parsers.dev** ](https://parsers.dev/auth/login)Account Settings.

The **parsers.dev APIs** is a REST-based service. Subsequently, all requests to the APIs require this **HTTP header**:

```http
x-api-key: Your parsers.dev API key
```

## Content type

The **parsers.dev APIs** is also a JSON-based service. You have to add **Content-Type** HTTP header to all your requests:

```javascript
Content-Type: application/json
```

## URL and API versioning

Only one API version is operating at this time. Use this base URL for your requests:

> **https://api.parsers.dev/api/v1**

## Responses

All responses are JSON-based and follow one of these formats:

```javascript
// successful response
{
  "status": "OK",
  "data": {...}
  }
}
```

```javascript
// error response
{
  "status": "ERROR",
  "data": {
    "code": <http-code>,
    "message": "<error-message>",
    "details": <mixed-object(optional)>,
  }
}
```

Http codes and error message you can find at **Errors** section

{% api-method method="post" host="https://api.parsers.dev" path="/api/v1/parse/:database" %}
{% api-method-summary %}
Parse SQL \(SQL → AST\)
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get **Abstract Syntax Tree** represented in your SQL-queries. You can parse any supported syntax \(**DDL, DML, DCL, TCL**, and another specific syntax\). **:database** is database type \(**postgresql** and **snowflake** are supported\)
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="x-api-key" type="string" required=true %}
Authentication token \(your api key from parsers.dev account settings\)
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="sql" type="string" required=true %}
SQL source code, separated using semicolon
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
SQL successfully parsed \(without AST\)
{% endapi-method-response-example-description %}

```javascript
{
    "status": "OK",
    "data": {
        "compiled": {
            "ddl": {
                "relations": [
                    {
                        "type": "TABLE",
                        "names": {
                            "original": {
                                "schema": "public",
                                "name": "t"
                            }
                        },
                        "columns": [
                            {
                                "names": {
                                    "original": "a"
                                },
                                "type": {
                                    "schema": "pg_catalog",
                                    "name": "integer",
                                    "mods": [],
                                    "array": {
                                        "dimension": 0,
                                        "bounds": []
                                    }
                                },
                                "kind": "column",
                                "nullable": "yes",
                                "sequence": null
                            }
                        ],
                        "indexes": [],
                        "constraints": [
                            {
                                "type": "CONSTR_NULL",
                                "relation": {
                                    "schema": "public",
                                    "name": "t"
                                },
                                "name": null,
                                "columns": [
                                    "a"
                                ],
                                "constraint": {
                                    "ast": null,
                                    "compiled": null
                                }
                            }
                        ],
                        "partition": null,
                        "inherit": null
                    }
                ],
                "types": [],
                "functions": [],
                "operators": [],
                "sequences": [],
                "schemas": [],
                "extensions": []
            },
            "dmls": [
                [
                    {
                        "fields": [
                            {
                                "names": {
                                    "original": "a",
                                    "local": "a"
                                },
                                "type": {
                                    "schema": "pg_catalog",
                                    "name": "integer",
                                    "mods": [],
                                    "array": {
                                        "dimension": 0,
                                        "bounds": []
                                    }
                                },
                                "source": {
                                    "relation": {
                                        "schema": "public",
                                        "name": "t"
                                    },
                                    "field": "a"
                                },
                                "aggregate": false,
                                "over": null,
                                "value": null,
                                "kind": "column",
                                "expressionOf": null,
                                "nullable": "yes",
                                "sequence": null,
                                "locations": [
                                    {
                                        "action": "add",
                                        "place": "inline",
                                        "location": {
                                            "location": {
                                                "from": 16,
                                                "to": null
                                            },
                                            "id": 0,
                                            "filename": ""
                                        }
                                    }
                                ],
                                "sublink": null
                            }
                        ],
                        "constraints": [],
                        "linesCount": "MANY_OR_NONE",
                        "linkedWith": {
                            "relations": [
                                {
                                    "schema": "public",
                                    "name": "t",
                                    "type": "SELECT"
                                }
                            ],
                            "columns": []
                        },
                        "error": null
                    },
                    {
                        "fields": [
                            {
                                "names": {
                                    "original": "a",
                                    "local": "a"
                                },
                                "type": {
                                    "schema": "pg_catalog",
                                    "name": "integer",
                                    "mods": [],
                                    "array": {
                                        "dimension": 0,
                                        "bounds": []
                                    }
                                },
                                "source": {
                                    "relation": {
                                        "schema": "public",
                                        "name": "t"
                                    },
                                    "field": "a"
                                },
                                "aggregate": false,
                                "over": null,
                                "value": null,
                                "kind": "column",
                                "expressionOf": null,
                                "nullable": "yes",
                                "sequence": null,
                                "locations": [
                                    {
                                        "action": "add",
                                        "place": "inline",
                                        "location": {
                                            "location": {
                                                "from": 16,
                                                "to": null
                                            },
                                            "id": 0,
                                            "filename": ""
                                        }
                                    }
                                ],
                                "sublink": null
                            }
                        ],
                        "constraints": [],
                        "linesCount": "MANY_OR_NONE",
                        "linkedWith": {
                            "relations": [
                                {
                                    "schema": "public",
                                    "name": "t",
                                    "type": "SELECT"
                                }
                            ],
                            "columns": []
                        },
                        "error": null
                    }
                ],
                [
                    {
                        "error": {
                            "from": 6,
                            "to": null
                        }
                    }
                ],
                [
                    {
                        "fields": [
                            {
                                "names": {
                                    "original": "a",
                                    "local": "a"
                                },
                                "type": {
                                    "schema": "pg_catalog",
                                    "name": "integer",
                                    "mods": [],
                                    "array": {
                                        "dimension": 0,
                                        "bounds": []
                                    }
                                },
                                "source": {
                                    "relation": {
                                        "schema": "public",
                                        "name": "t"
                                    },
                                    "field": "a"
                                },
                                "aggregate": false,
                                "over": null,
                                "value": null,
                                "kind": "column",
                                "expressionOf": null,
                                "nullable": "no",
                                "sequence": null,
                                "locations": [
                                    {
                                        "action": "add",
                                        "place": "inline",
                                        "location": {
                                            "location": {
                                                "from": 16,
                                                "to": null
                                            },
                                            "id": 0,
                                            "filename": ""
                                        }
                                    }
                                ],
                                "sublink": null
                            }
                        ],
                        "constraints": [
                            {
                                "type": "CONSTR_NOTNULL",
                                "place": "generated-notnull",
                                "name": null,
                                "relation": null,
                                "columns": [
                                    "a"
                                ],
                                "constraint": {
                                    "ast": null,
                                    "compiled": null
                                },
                                "location": {
                                    "filename": "",
                                    "id": 0,
                                    "location": {
                                        "from": 0,
                                        "to": null
                                    }
                                }
                            }
                        ],
                        "linesCount": "MANY_OR_NONE",
                        "linkedWith": {
                            "relations": [
                                {
                                    "schema": "public",
                                    "name": "t",
                                    "type": "SELECT"
                                }
                            ],
                            "columns": []
                        },
                        "error": null
                    }
                ]
            ]
        },
        
        }
    }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
User not found
{% endapi-method-response-example-description %}

```javascript
{
    "status": "ERROR",
    "data": {
        "code": 404,
        "message": "USER_NOT_FOUND",
        "details": {
            "api": {
                "key": "..."
            }
        }
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

**Example:**

{% tabs %}
{% tab title="JSON" %}
```javascript
{
  "sql": "CREATE TABLE t(); SELECT 1; SELECT 1 FROM ; SELECT 2"
}
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const axios = require ('axios');

const api_key = '<your-api-key>';

const data = {
  sql: 'CREATE TABLE t(); SELECT 1; SELECT 1 FROM ; SELECT 2',
};

axios({
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'x-api-key': api_key,
  },
  data,
  url: `https://api.parsers.dev/api/v1/parse/postgresql/`,
}).then((response) => {
  console.log(response.data);
})
.catch(function (error) {
  console.error('api.parsers.dev error:');
  console.error(JSON.stringify(error.response.data, null, 2));
});

```
{% endtab %}

{% tab title="Bash" %}
```bash
PARSERSDEV_API_KEY="<your-api-key>" \
echo "{\"sql\": \"CREATE TABLE t(); SELECT 1; SELECT 2\"}" | \
curl \
  --header "x-api-key: $PARSERSDEV_API_KEY" \
  --header "Content-Type: application/json" \
  --request POST --data @- https://api.parsers.dev/api/v1/parse/postgresql/
```
{% endtab %}
{% endtabs %}

{% api-method method="post" host="https://api.parsers.dev" path="/api/v1/compile/:database" %}
{% api-method-summary %}
Compile SQL \(SQL → Special Object\)
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get a special object compiled based on your DDL or DML query. Because DML strictly depends on database schema \(DDL\), DML can be compiled to a special object, based on DDL only. **:database** is database type \(**postgresql** only\).
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="x-api-key" type="string" required=true %}
Authentication token \(your api key from app.holisitic.dev\)
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="ast" type="string" required=false %}
any value for AST in result
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="ddl" type="string" required=true %}
Database schema \(DDL statements\) source code, separated using semicolon
{% endapi-method-parameter %}

{% api-method-parameter name="dmls" type="array" required=true %}
An array of DML queries. Each query can consist of many statements, separated using a semicolon
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
SQL successfully compiled \(with AST\)
{% endapi-method-response-example-description %}

```javascript
{
    "status": "OK",
    "data": {
        "compiled": {
            "ddl": {
                "relations": [
                    {
                        "type": "TABLE",
                        "names": {
                            "original": {
                                "schema": "public",
                                "name": "t"
                            }
                        },
                        "columns": [
                            {
                                "names": {
                                    "original": "a"
                                },
                                "type": {
                                    "schema": "pg_catalog",
                                    "name": "integer",
                                    "mods": [],
                                    "array": {
                                        "dimension": 0,
                                        "bounds": []
                                    }
                                },
                                "kind": "column",
                                "nullable": "yes",
                                "sequence": null
                            }
                        ],
                        "indexes": [],
                        "constraints": [
                            {
                                "type": "CONSTR_NULL",
                                "relation": {
                                    "schema": "public",
                                    "name": "t"
                                },
                                "name": null,
                                "columns": [
                                    "a"
                                ],
                                "constraint": {
                                    "ast": null,
                                    "compiled": null
                                }
                            }
                        ],
                        "partition": null,
                        "inherit": null
                    }
                ],
                "types": [],
                "functions": [],
                "operators": [],
                "sequences": [],
                "schemas": [],
                "extensions": []
            },
            "dmls": [
                [
                    {
                        "fields": [
                            {
                                "names": {
                                    "original": "a",
                                    "local": "a"
                                },
                                "type": {
                                    "schema": "pg_catalog",
                                    "name": "integer",
                                    "mods": [],
                                    "array": {
                                        "dimension": 0,
                                        "bounds": []
                                    }
                                },
                                "source": {
                                    "relation": {
                                        "schema": "public",
                                        "name": "t"
                                    },
                                    "field": "a"
                                },
                                "aggregate": false,
                                "over": null,
                                "value": null,
                                "kind": "column",
                                "expressionOf": null,
                                "nullable": "yes",
                                "sequence": null,
                                "locations": [
                                    {
                                        "action": "add",
                                        "place": "inline",
                                        "location": {
                                            "location": {
                                                "from": 16,
                                                "to": null
                                            },
                                            "id": 0,
                                            "filename": ""
                                        }
                                    }
                                ],
                                "sublink": null
                            }
                        ],
                        "constraints": [],
                        "linesCount": "MANY_OR_NONE",
                        "linkedWith": {
                            "relations": [
                                {
                                    "schema": "public",
                                    "name": "t",
                                    "type": "SELECT"
                                }
                            ],
                            "columns": []
                        },
                        "error": null
                    },
                    {
                        "fields": [
                            {
                                "names": {
                                    "original": "a",
                                    "local": "a"
                                },
                                "type": {
                                    "schema": "pg_catalog",
                                    "name": "integer",
                                    "mods": [],
                                    "array": {
                                        "dimension": 0,
                                        "bounds": []
                                    }
                                },
                                "source": {
                                    "relation": {
                                        "schema": "public",
                                        "name": "t"
                                    },
                                    "field": "a"
                                },
                                "aggregate": false,
                                "over": null,
                                "value": null,
                                "kind": "column",
                                "expressionOf": null,
                                "nullable": "yes",
                                "sequence": null,
                                "locations": [
                                    {
                                        "action": "add",
                                        "place": "inline",
                                        "location": {
                                            "location": {
                                                "from": 16,
                                                "to": null
                                            },
                                            "id": 0,
                                            "filename": ""
                                        }
                                    }
                                ],
                                "sublink": null
                            }
                        ],
                        "constraints": [],
                        "linesCount": "MANY_OR_NONE",
                        "linkedWith": {
                            "relations": [
                                {
                                    "schema": "public",
                                    "name": "t",
                                    "type": "SELECT"
                                }
                            ],
                            "columns": []
                        },
                        "error": null
                    }
                ],
                [
                    {
                        "error": {
                            "from": 6,
                            "to": null
                        }
                    }
                ],
                [
                    {
                        "fields": [
                            {
                                "names": {
                                    "original": "a",
                                    "local": "a"
                                },
                                "type": {
                                    "schema": "pg_catalog",
                                    "name": "integer",
                                    "mods": [],
                                    "array": {
                                        "dimension": 0,
                                        "bounds": []
                                    }
                                },
                                "source": {
                                    "relation": {
                                        "schema": "public",
                                        "name": "t"
                                    },
                                    "field": "a"
                                },
                                "aggregate": false,
                                "over": null,
                                "value": null,
                                "kind": "column",
                                "expressionOf": null,
                                "nullable": "no",
                                "sequence": null,
                                "locations": [
                                    {
                                        "action": "add",
                                        "place": "inline",
                                        "location": {
                                            "location": {
                                                "from": 16,
                                                "to": null
                                            },
                                            "id": 0,
                                            "filename": ""
                                        }
                                    }
                                ],
                                "sublink": null
                            }
                        ],
                        "constraints": [
                            {
                                "type": "CONSTR_NOTNULL",
                                "place": "generated-notnull",
                                "name": null,
                                "relation": null,
                                "columns": [
                                    "a"
                                ],
                                "constraint": {
                                    "ast": null,
                                    "compiled": null
                                },
                                "location": {
                                    "filename": "",
                                    "id": 0,
                                    "location": {
                                        "from": 0,
                                        "to": null
                                    }
                                }
                            }
                        ],
                        "linesCount": "MANY_OR_NONE",
                        "linkedWith": {
                            "relations": [
                                {
                                    "schema": "public",
                                    "name": "t",
                                    "type": "SELECT"
                                }
                            ],
                            "columns": []
                        },
                        "error": null
                    }
                ]
            ]
        },
        "ast": {
            "ddl": [
                [
                    {
                        "query": {
                            "CreateStmt": {
                                "relation": {
                                    "RangeVar": {
                                        "relname": "t",
                                        "inh": true,
                                        "relpersistence": "p",
                                        "location": 13
                                    }
                                },
                                "tableElts": [
                                    {
                                        "ColumnDef": {
                                            "colname": "a",
                                            "typeName": {
                                                "TypeName": {
                                                    "names": [
                                                        {
                                                            "String": {
                                                                "str": "pg_catalog"
                                                            }
                                                        },
                                                        {
                                                            "String": {
                                                                "str": "int4"
                                                            }
                                                        }
                                                    ],
                                                    "typemod": -1,
                                                    "location": 18
                                                }
                                            },
                                            "is_local": true,
                                            "location": 16
                                        }
                                    }
                                ],
                                "oncommit": 0
                            }
                        },
                        "error": null
                    },
                    {
                        "query": null,
                        "sql": "CREATE",
                        "error": {
                            "location": 31
                        }
                    }
                ]
            ],
            "dmls": [
                [
                    {
                        "query": [
                            {
                                "SelectStmt": {
                                    "targetList": [
                                        {
                                            "ResTarget": {
                                                "val": {
                                                    "ColumnRef": {
                                                        "fields": [
                                                            {
                                                                "A_Star": {}
                                                            }
                                                        ],
                                                        "location": -1
                                                    }
                                                },
                                                "location": -1
                                            }
                                        }
                                    ],
                                    "fromClause": [
                                        {
                                            "RangeVar": {
                                                "relname": "t",
                                                "inh": true,
                                                "relpersistence": "p",
                                                "location": 6
                                            }
                                        }
                                    ],
                                    "op": 0
                                }
                            }
                        ],
                        "error": null
                    },
                    {
                        "query": [
                            {
                                "SelectStmt": {
                                    "targetList": [
                                        {
                                            "ResTarget": {
                                                "val": {
                                                    "ColumnRef": {
                                                        "fields": [
                                                            {
                                                                "A_Star": {}
                                                            }
                                                        ],
                                                        "location": -1
                                                    }
                                                },
                                                "location": -1
                                            }
                                        }
                                    ],
                                    "fromClause": [
                                        {
                                            "RangeVar": {
                                                "relname": "t1",
                                                "inh": true,
                                                "relpersistence": "p",
                                                "location": 6
                                            }
                                        }
                                    ],
                                    "op": 0
                                }
                            }
                        ],
                        "error": null
                    }
                ],
                [
                    {
                        "query": null,
                        "sql": "table",
                        "error": {
                            "location": 6
                        }
                    }
                ],
                [
                    {
                        "query": [
                            {
                                "SelectStmt": {
                                    "targetList": [
                                        {
                                            "ResTarget": {
                                                "val": {
                                                    "ColumnRef": {
                                                        "fields": [
                                                            {
                                                                "A_Star": {}
                                                            }
                                                        ],
                                                        "location": 7
                                                    }
                                                },
                                                "location": 7
                                            }
                                        }
                                    ],
                                    "fromClause": [
                                        {
                                            "RangeVar": {
                                                "relname": "t",
                                                "inh": true,
                                                "relpersistence": "p",
                                                "location": 14
                                            }
                                        }
                                    ],
                                    "whereClause": {
                                        "A_Expr": {
                                            "kind": 0,
                                            "name": [
                                                {
                                                    "String": {
                                                        "str": "="
                                                    }
                                                }
                                            ],
                                            "lexpr": {
                                                "ColumnRef": {
                                                    "fields": [
                                                        {
                                                            "String": {
                                                                "str": "a"
                                                            }
                                                        }
                                                    ],
                                                    "location": 22
                                                }
                                            },
                                            "rexpr": {
                                                "ParamRef": {
                                                    "number": 1,
                                                    "location": 26
                                                }
                                            },
                                            "location": 24
                                        }
                                    },
                                    "op": 0
                                }
                            }
                        ],
                        "error": null
                    }
                ]
            ]
        }
    }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
User not found
{% endapi-method-response-example-description %}

```javascript
{
    "status": "ERROR",
    "data": {
        "code": 404,
        "message": "USER_NOT_FOUND",
        "details": {
            "api": {
                "key": "..."
            }
        }
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

**Example:**

{% tabs %}
{% tab title="JSON" %}
```javascript
{
    "ddl": "CREATE TABLE t (a int); CREATE",
    "dmls": [
        "table t; table t1",
        "table",
        "select * FROM t WHERE a = $1"
    ]
}
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const axios = require ('axios');

const api_key = '<your-api-key>';

const data = {
  ddl: 'CREATE TABLE t (a int); CREATE',
  dmls: [
    'table t; table t1',
    'table',
    'select * FROM t WHERE a = $1'
  ]
};

axios({
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'x-api-key': api_key,
  },
  data,
  url: `https://api.parsers.dev/api/v1/compile/postgresql/`,
}).then((response) => {
  console.log(response.data);
})
.catch(function (error) {
  console.error('api.parsers.dev error:');
  console.error(JSON.stringify(error.response.data, null, 2));
});

```
{% endtab %}

{% tab title="Bash" %}
```bash
PARSERSDEV_API_KEY="<your-api-key>" \
echo "{\"ddl\": \"CREATE TABLE t (a int); CREATE\", dml: [\"table t; table t1\", \"table\", \"select * FROM t WHERE a = $1\"]}" | \
curl \
  --header "x-api-key: $PARSERSDEV_API_KEY" \
  --header "Content-Type: application/json" \
  --request POST --data @- https://api.parsers.dev/api/v1/compile/postgresql/
```
{% endtab %}
{% endtabs %}

