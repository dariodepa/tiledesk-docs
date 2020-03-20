You can use the API to get or set user information.

The Model 


| Key | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the user which is given by Tiledesk. |
| email | String | The user email. |
| password | String | The user password. |
| firstname | String | The user firstname. |
| lastname | String | The user lastname. |
| emailverified | Boolean | Determine if the user has a email validated. |
| createdAt | String | The time (ISO-8601 date string) when the user was created. |
| updatedAt | String |  The time (ISO-8601 date string) when the user was updated.  |
| createdBy | String | The unique identifier of the row creator |
| id_project | String | The unique identifier of the project |


{% api-method method="get" host="https://api.tiledesk.com" path="/v1/users" %}
{% api-method-summary %}
Get the current authenticated user
{% endapi-method-summary %}

{% api-method-description %}
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
authorization token. Basic Auth or JWT
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}

{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
...
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}


{% api-method method="put" host="https://api.tiledesk.com" path="/v1/users/" %}
{% api-method-summary %}
Update the current authenticated user
{% endapi-method-summary %}

{% api-method-description %}
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}

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

{% api-method-parameter name="firstname" type="string" required=false %}
The user firstname
{% endapi-method-parameter %}

{% api-method-parameter name="lastname" type="string" required=false %}
The user lastname
{% endapi-method-parameter %}


{% api-method-parameter name="attributes" type="object" required=false %}
The user custom attributes
{% endapi-method-parameter %}

{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
...
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}
