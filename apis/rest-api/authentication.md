# Authentication

{% api-method method="post" host="https://api.tiledesk.com" path="/v2/auth/signin" %}
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
the user email address
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
   "success":true,
   "token":"JWT  XYZ",
   "user":{
      "_id":"5ab11c6b83dc240014d46095",
      "email":"andrea.leo@f21.it"
   }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.tiledesk.com" path="/v2/auth/signup" %}
{% api-method-summary %}
Signup with email and password
{% endapi-method-summary %}

{% api-method-description %}
Allows to signup an agent using email and password.
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
the user email address
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=true %}
the user password
{% endapi-method-parameter %}

{% api-method-parameter name="firstname" type="string" required=true %}
the user firstname
{% endapi-method-parameter %}

{% api-method-parameter name="lastname" type="string" required=true %}
the user lastname
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
   "success":true,
   "msg":"Successfully created new user.",
   "user":{
      "_id":"5e2593f0cf6bcc00178e75f7",
      "email":"andrea.leo@f22.it",
      "emailverified":false,
      "createdAt":"2020-01-20T11:50:08.778Z",
      "updatedAt":"2020-01-20T11:50:08.778Z",
      "__v":0
   }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.tiledesk.com/v2" path="/auth/signinAnonymously" %}
{% api-method-summary %}
Anonymous authentication for a user.
{% endapi-method-summary %}

{% api-method-description %}
Allows a user to authenticate anonymously on the system.  
**Only works for Tiledesk v2 environment \(on-premises only\).**
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
use "application/json" value
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="id\_project" type="string" required=true %}
the project to which the user belongs
{% endapi-method-parameter %}

{% api-method-parameter name="firstname" type="string" required=false %}
the user firstname
{% endapi-method-parameter %}

{% api-method-parameter name="lastname" type="string" required=false %}
the user password
{% endapi-method-parameter %}

{% api-method-parameter name="email" type="string" required=false %}
the user email
{% endapi-method-parameter %}

{% api-method-parameter name="attributes" type="object" required=false %}
the user custom attributes
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
   "success":true,
   "token":"JWT XYZ",
   "user":{
      "_id":"5e25944ecf6bcc00178e75fa",
      "email":"a0fe493b-a19b-44a0-99ce-414c65fc20b0@tiledesk.com",
      "emailverified":false,
      "createdAt":"2020-01-20T11:51:42.115Z",
      "updatedAt":"2020-01-20T11:51:42.115Z",
      "__v":0
   }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.tiledesk.com/v2" path="/auth/signinWithCustomToken" %}
{% api-method-summary %}
Custom authentication for a user.
{% endapi-method-summary %}

{% api-method-description %}
Allows to authenticate with a custom JWT token.  
**Only works for Tiledesk v2 environment \(on-premises only\).**
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Custom JWT Authorization token. See below
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=true %}
use "application/json" value
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
