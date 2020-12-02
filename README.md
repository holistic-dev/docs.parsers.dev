# API Reference \(beta\)

{% api-method method="post" host="https://api.parsers.dev" path="/api/v1/parse/" %}
{% api-method-summary %}
Parse SQL \(SQL-&gt;AST\)
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get **Abstract Syntax Tree** represented in your SQL-queries. You can parse any supported syntax \(**DDL, DML, DCL, TCL**, and another specific syntax\)
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="x-api-key" type="string" required=true %}
Authentication token \(your api key from app.holistic.dev\)
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="db" type="string" required=true %}
Database type \('pg' or 'snowflake'\)
{% endapi-method-parameter %}

{% api-method-parameter name="sql" type="string" required=true %}
SQL source code, separated using semicolon
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
AST successfully parsed.
{% endapi-method-response-example-description %}

```javascript
{
    "status": "OK",
    "data": {
        "ast": [
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
                        "oncommit": 0
                    }
                },
                "error": null
            },
            {
                "query": {
                    "SelectStmt": {
                        "targetList": [
                            {
                                "ResTarget": {
                                    "val": {
                                        "A_Const": {
                                            "val": {
                                                "Integer": {
                                                    "ival": 1
                                                }
                                            },
                                            "location": 7
                                        }
                                    },
                                    "location": 7
                                }
                            }
                        ],
                        "op": 0
                    }
                },
                "error": null
            },
            {
                "query": null,
                "sql": "SELECT 1 FROM ",
                "error": {
                    "location": 15
                }
            },
            {
                "query": {
                    "SelectStmt": {
                        "targetList": [
                            {
                                "ResTarget": {
                                    "val": {
                                        "A_Const": {
                                            "val": {
                                                "Integer": {
                                                    "ival": 2
                                                }
                                            },
                                            "location": 7
                                        }
                                    },
                                    "location": 7
                                }
                            }
                        ],
                        "op": 0
                    }
                },
                "error": null
            }
        ]
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
	"db": "pg",
  "sql": "CREATE TABLE t(); SELECT 1; SELECT 1 FROM ; SELECT 2"
}
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const axios = require ('axios');

const api_key = '<your-api-key>';

const data = {
  db: 'pg',
  sql: 'CREATE TABLE t(); SELECT 1; SELECT 1 FROM ; SELECT 2',
};

axios({
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'x-api-key': api_key,
  },
  data,
  url: `https://api.parsers.dev/api/v1/parse/`,
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
HOLISTICDEV_API_KEY="<your-api-key>" \
echo "{\"db\":\"pg\", \"sql\": \"CREATE TABLE t(); SELECT 1; SELECT 2\"}" | \
curl \
  --header "x-api-key: $HOLISTICDEV_API_KEY" \
  --header "Content-Type: application/json" \
  --request POST --data @- https://api.parsers.dev/api/v1/parse/
```
{% endtab %}
{% endtabs %}

{% api-method method="post" host="https://api.parsers.dev" path="/api/v1/compile/" %}
{% api-method-summary %}
Compile SQL \(SQL-&gt;Special Object\)
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

