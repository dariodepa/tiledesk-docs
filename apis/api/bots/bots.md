# Bots

{% api-method method="get" host="https://api.tiledesk.com" path="/v1/:project\_id/faq_kb" %}
{% api-method-summary %}
Get all bots
{% endapi-method-summary %}

{% api-method-description %}
Allows an account to list all the bots of the project.
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
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
[
   {
      "_id":"5be9b2ecc72a050015e14951",
      "updatedAt":"2018-11-12T17:05:50.616Z",
      "createdAt":"2018-11-12T17:05:48.544Z",
      "name":"bot1",
      "id_project":"5b55e806c93dde00143163dd",
      "trashed":false,
      "createdBy":"5ab0f3fa57066e0014bfd71e",
      "__v":0,
      "external":false
   },
   {
      "_id":"5ce265596438e40017e3610d",
      "updatedAt":"2019-05-20T08:29:14.524Z",
      "createdAt":"2019-05-20T08:29:13.286Z",
      "name":"bot2",
      "id_project":"5b55e806c93dde00143163dd",
      "trashed":false,
      "createdBy":"5ab0f3fa57066e0014bfd71e",
      "__v":0,
      "external":false
   }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example

```text
curl -v -X GET -u andrea.leo@f21.it:123456 https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/faq_kb
```

{% api-method method="get" host="https://api.tiledesk.com" path="/v1/:project\_id/faq_kb" %}
{% api-method-summary %}
Get a bot by id
{% endapi-method-summary %}

{% api-method-description %}
Allows an account to get a bot of the project.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="project\_id" type="string" required=true %}
the Project Id is a unique code assigned to your project when you create it in Tiledesk.
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
  {
      "_id":"5be9b2ecc72a050015e14951",
      "updatedAt":"2018-11-12T17:05:50.616Z",
      "createdAt":"2018-11-12T17:05:48.544Z",
      "name":"bot1",
      "id_project":"5b55e806c93dde00143163dd",
      "trashed":false,
      "createdBy":"5ab0f3fa57066e0014bfd71e",
      "__v":0,
      "external":false
   }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example

```text
curl -v -X GET -u andrea.leo@f21.it:123456 https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/faq_kb/5be9b2ecc72a050015e14951
```

{% api-method method="post" host="https://api.tiledesk.com" path="/v1/:project\_id/faq_kb" %}
{% api-method-summary %}
Create a new bot
{% endapi-method-summary %}

{% api-method-description %}
Allows to add more bots.
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
{% api-method-parameter name="name" type="string" required=true %}
The bot name
{% endapi-method-parameter %}

{% api-method-parameter name="url" type="string" required=false %}
The bot external endpoint
{% endapi-method-parameter %}

{% api-method-parameter name="external" type="boolean" required=false %}
True if external otherwise false for internal bot
{% endapi-method-parameter %}

{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
 {
      "_id":"5be9b2ecc72a050015e14951",
      "updatedAt":"2018-11-12T17:05:50.616Z",
      "createdAt":"2018-11-12T17:05:48.544Z",
      "name":"bot1",
      "id_project":"5b55e806c93dde00143163dd",
      "trashed":false,
      "createdBy":"5ab0f3fa57066e0014bfd71e",
      "__v":0,
      "external":false
   }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example:

```text
curl -v -X POST -H 'Content-Type: application/json' -u andrea.leo@f21.it:123456  -d '{"name":"bot1"}' https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/faq_kb
```

{% api-method method="put" host="https://api.tiledesk.com" path="/v1/:project\_id/faq_kb/:id" %}
{% api-method-summary %}
Update a bot
{% endapi-method-summary %}

{% api-method-description %}
Allows to update a bot.
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

{% api-method-parameter name="Content-Type" type="string" required=true %}
use "application/json" value
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="name" type="string" required=true %}
The bot name
{% endapi-method-parameter %}

{% api-method-parameter name="url" type="string" required=false %}
The bot external endpoint
{% endapi-method-parameter %}

{% api-method-parameter name="external" type="boolean" required=false %}
True if external otherwise false for internal bot
{% endapi-method-parameter %}

{% endapi-method-body-parameters %}

{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
      "_id":"5be9b2ecc72a050015e14951",
      "updatedAt":"2018-11-12T17:05:50.616Z",
      "createdAt":"2018-11-12T17:05:48.544Z",
      "name":"bot1",
      "id_project":"5b55e806c93dde00143163dd",
      "trashed":false,
      "createdBy":"5ab0f3fa57066e0014bfd71e",
      "__v":0,
      "external":false
   }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example:

```text
curl -v -X PUT -H 'Content-Type: application/json' -u andrea.leo@f21.it:123456  -d '{"name":"bot1"}' https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/faq_kb/5be9b2ecc72a050015e14951
```

{% api-method method="delete" host="https://api.tiledesk.com" path="/v1/:project\_id/faq_kb/:id" %}
{% api-method-summary %}
Delete a bot
{% endapi-method-summary %}

{% api-method-description %}
Allows to delete a bot.
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
      "_id":"5be9b2ecc72a050015e14951",
      "updatedAt":"2018-11-12T17:05:50.616Z",
      "createdAt":"2018-11-12T17:05:48.544Z",
      "name":"bot1",
      "id_project":"5b55e806c93dde00143163dd",
      "trashed":false,
      "createdBy":"5ab0f3fa57066e0014bfd71e",
      "__v":0,
      "external":false
   }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example:

```text
curl -v -X DELETE -H 'Content-Type: application/json' -u andrea.leo@f21.it:123456  https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/faq_kb/5be9b2ecc72a050015e14951
```
