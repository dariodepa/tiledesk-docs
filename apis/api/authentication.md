

{% api-method method="post" host="https://api.tiledesk.com" path="/v1/auth/signin" %}
{% api-method-summary %}
Authentication with email and password
{% endapi-method-summary %}

{% api-method-description %}
Allows to authenticate an agent using email and password.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-headers %}

{% api-method-parameter name="Content-Type" type="string" required=true %}
use "application/json" value
{% endapi-method-parameter %}


{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="email" type="string" required=true %}
the user email
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=true %}
the user password
{% endapi-method-parameter %}

{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
 {
      
   }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}




{% api-method method="post" host="https://api.tiledesk.com" path="/v1/auth/signinAnonymously" %}
{% api-method-summary %}
Anonymous authentication for a visitor. 

It only works for Tiledesk beta version v2 environment.
{% endapi-method-summary %}

{% api-method-description %}
Allows a user to authenticate anonymously on the system
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-headers %}

{% api-method-parameter name="Content-Type" type="string" required=true %}
use "application/json" value
{% endapi-method-parameter %}


{% endapi-method-headers %}

{% api-method-body-parameters %}

{% api-method-parameter name="id_project" type="string" required=true %}
the project to which the user belongs
{% endapi-method-parameter %}


{% api-method-parameter name="firstname" type="string" required=false %}
the visitor email
{% endapi-method-parameter %}

{% api-method-parameter name="lastname" type="string" required=false %}
the user password
{% endapi-method-parameter %}


{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}


