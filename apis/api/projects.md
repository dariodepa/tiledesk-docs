
{% api-method method="get" host="https://api.tiledesk.com" path="/v1/:project\_id/isopen" %}
{% api-method-summary %}
Return if the project is open regarding operating hours
{% endapi-method-summary %}

{% api-method-description %}
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="project\_id" type="string" required=true %}
the Project Id is a unique code assigned to your project when you create it in Tiledesk.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=false %}
authorization token. Basic Auth or JWT
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
   ...
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}
