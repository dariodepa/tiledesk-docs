
{% api-method method="post" host="https://api.tiledesk.com" path="/v1/auth/signin" %}
{% api-method-summary %}
Authentication with email and password
{% endapi-method-summary %}

{% api-method-description %}
Allows to authenticate an agent using email and password.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}

{% endapi-method-path-parameters %}

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




{% api-method method="post" host="https://api.tiledesk.com" path="/v1/auth/signup" %}
{% api-method-summary %}
Signup with email and password
{% endapi-method-summary %}

{% api-method-description %}
Allows to signup an agent using email and password.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}

{% endapi-method-path-parameters %}

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






{% api-method method="post" host="https://api.tiledesk.com" path="/v1/auth/signinAnonymously" %}
{% api-method-summary %}
Anonymous authentication for a user. 
{% endapi-method-summary %}

{% api-method-description %}
Allows a user to authenticate anonymously on the system. It only works for Tiledesk beta version v2 environment.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}

{% endapi-method-path-parameters %}

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
the user email
{% endapi-method-parameter %}

{% api-method-parameter name="lastname" type="string" required=false %}
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












{% api-method method="post" host="https://api.tiledesk.com" path="/v1/auth/signinWithCustomToken" %}
{% api-method-summary %}
Custom authentication for a user. 
{% endapi-method-summary %}

{% api-method-description %}
Allows to authenticate with a custom JWT token. It only works for Tiledesk beta version v2 environment.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}

{% endapi-method-path-parameters %}

{% api-method-headers %}

{% api-method-parameter name="Authorization" type="string" required=true %}
Custom JWT Authorization token. See below

{% endapi-method-parameter %}

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
{  
        ...
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



## Overview ##

The Custom JWT authentication provider allows users to authenticate with an authentication system that is independent from Tiledesk. The external system must return a signed [JSON Web Token](https://jwt.io/introduction/) that contains a unique ID value for the authenticated user.

Tiledesk uses the JWT to identify your application’s users and authenticate their requests but does not impose any restrictions on the external authentication system’s requirements or authentication methods. 


You must set the following required fields of the user object :

* **_id** is the custom unique user identifier of the external authentication system.
* **subject**. JWTs describe their subject in the sub claim. sub must be equal to value `userexternal`
* **audience**. JWTs describe their audience in the aud claim. must be `https://tiledesk.com/projects/<YOUR_PROJECT_ID>`.


 Optional fields: 
 
* **firstname**. It's the user firstname
* **lastname**. It's the user lastname
* **other** jwt claims.

The external authentication system must create the JWT signing the object user with the project authentication secret code. See here to obtain a Project JWT Secret: https://developer.tiledesk.com/widget/auth#generating-a-chat-shared-secret

User object example: 

```
{_id: "123", firstname:"andrea", lastname:"leo", email: "email2@email.com",  customAttr: "c1", sub:  "userexternal",  aud:  "https://tiledesk.com/projects/5c81593adf767b0017d1aa68'}
```


