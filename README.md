# API Reference \(beta\)

{% api-method method="post" host="https://api.cakes.com" path="/api/v1/parse/" %}
{% api-method-summary %}
Parse AST
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get free cakes.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="x-api-key" type="string" required=true %}
Authentication token \(your api key from app.holistic.dev\)
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="db" type="string" required=false %}
Database type \('pg' or 'snowflake'\)
{% endapi-method-parameter %}

{% api-method-parameter name="sql" type="string" required=false %}
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
                    ...
                },
                "error": null
            },
            ...
            {
                "query": null,
                "sql": "...",
                "error": 1
            },
            ...
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
  "sql": "CREATE TABLE t();SELECT 1; SELECT 1 FROM ; SELECT 2"
}
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

