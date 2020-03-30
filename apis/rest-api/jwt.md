# Authentication

{% api-method method="delete" host="YOUR_TILEDESK_DOMAIN" path="/v1/jwt/history/:jti" %}
{% api-method-summary %}
Revoke a jwt token by JTI (JWT identifier)
{% endapi-method-summary %}

{% api-method-description %}
Only works for Tiledesk v2 environment (on-premises only).
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
use "application/json" value
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}

{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
..
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}
