# Faq

{% api-method method="get" host="https://api.tiledesk.com" path="/v1/:project\_id/faq" %}
{% api-method-summary %}
Get all faqs of a bot
{% endapi-method-summary %}

{% api-method-description %}
Allows an account to list all the faqs of the bot.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="project\_id" type="string" required=true %}
the Project Id is a unique code assigned to your project when you create it in Tiledesk.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
authorization token. Basic Auth or JWT
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="id\_faq\_kb" type="string" required=true %}
the bot id
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example

```text
curl -v -X GET -u andrea.leo@f21.it:123456 https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/faq?id_faq_kb=5be9b2ecc72a050015e14951
```

{% api-method method="get" host="https://api.tiledesk.com" path="/v1/:project\_id/faq/" %}
{% api-method-summary %}
Get a faq by id
{% endapi-method-summary %}

{% api-method-description %}
Allows an account to get a faq of a bot.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="project\_id" type="string" required=true %}
the Project Id is a unique code assigned to your project when you create it in Tiledesk.
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
The faq identifier
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
authorization token. Basic Auth or JWT
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example

```text
curl -v -X GET -u andrea.leo@f21.it:123456 https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/faq/5be9b2ecc72a050015e14951
```

{% api-method method="post" host="https://api.tiledesk.com" path="/v1/:project\_id/faq" %}
{% api-method-summary %}
Create a new faq
{% endapi-method-summary %}

{% api-method-description %}
Allows to add more faqs.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="project\_id" type="string" required=true %}
The project\_id is a unique code assigned to your project when you create it in Tiledesk
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
authorization token. Basic Auth or JWT
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=true %}
use "application/json" value
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="id\_faq\_kb" type="string" required=true %}
The bot id
{% endapi-method-parameter %}

{% api-method-parameter name="question" type="string" required=true %}
The faq question
{% endapi-method-parameter %}

{% api-method-parameter name="answer" type="string" required=true %}
The faq answer
{% endapi-method-parameter %}

{% api-method-parameter name="topic" type="string" required=false %}
The faq topic
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example:

```text
curl -v -X POST -H 'Content-Type: application/json' -u andrea.leo@f21.it:123456  -d '{"id_faq_kb":"123321", "question":"question", "answer":"answer"}' https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/faq
```

{% api-method method="put" host="https://api.tiledesk.com" path="/v1/:project\_id/faq/:id" %}
{% api-method-summary %}
Update a faq
{% endapi-method-summary %}

{% api-method-description %}
Allows to update a faq.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="project\_id" type="string" required=true %}
The project\_id is a unique code assigned to your project when you create it in Tiledesk
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
The faq identifier
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
authorization token. Basic Auth or JWT
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=true %}
use "application/json" value
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="id\_faq\_kb" type="string" required=true %}
The bot id
{% endapi-method-parameter %}

{% api-method-parameter name="question" type="string" required=true %}
The faq question
{% endapi-method-parameter %}

{% api-method-parameter name="answer" type="string" required=true %}
The faq answer
{% endapi-method-parameter %}

{% api-method-parameter name="topic" type="string" required=false %}
The faq topic
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example:

```text
curl -v -X PUT -H 'Content-Type: application/json' -u andrea.leo@f21.it:123456  -d '{"name":"bot1"}' https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/faq/5be9b2ecc72a050015e14951
```

{% api-method method="delete" host="https://api.tiledesk.com" path="/v1/:project\_id/faq/:id" %}
{% api-method-summary %}
Delete a faq
{% endapi-method-summary %}

{% api-method-description %}
Allows to delete a faq.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="project\_id" type="string" required=true %}
The project\_id is a unique code assigned to your project when you create it in Tiledesk
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
The bot identifier
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
authorization token. Basic Auth or JWT
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example:

```text
curl -v -X DELETE -H 'Content-Type: application/json' -u andrea.leo@f21.it:123456  https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/faq/5be9b2ecc72a050015e14951
```

