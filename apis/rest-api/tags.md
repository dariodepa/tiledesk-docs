You can use the API to get or set tags.

{% api-method method="get" host="YOUR\_TILEDESK\_DOMAIN" path="/:project\_id/tags" %}
{% api-method-summary %}
Get all tags
{% endapi-method-summary %}

{% api-method-description %}
Allows an account to list all the tags.
Only works for Tiledesk v2 environment (on-premises only).
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
{% api-method-parameter name="sortField" type="string" required=false %}
what field to sort the results by. _Default field is createdAt_
{% endapi-method-parameter %}

{% api-method-parameter name="direction" type="string" required=false %}
sort direction: 1 or -1. Return the results in ascending (1) or descending (-1) order. _defaults to desc_
{% endapi-method-parameter %}

{% api-method-parameter name="page" type="number" required=false %}
what page of results to fetch. defaults to first page.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
[
   {
      "_id":"5e67b8bafb930c0017aa4e42",
      "tag":"tag1",
      "color":"#66C549",
      "id_project":"5e5d40b2bd0a9b00179ff3cd",
      "createdBy":"5e09d16d4d36110017506d7f",
      "createdAt":"2020-03-10T15:56:42.374Z",
      "updatedAt":"2020-03-10T15:56:42.374Z",
      "__v":0
   },
   {
      "_id":"5e67b737fb930c0017aa4e40",
      "tag":"important",
      "color":"#43B1F2",
      "id_project":"5e5d40b2bd0a9b00179ff3cd",
      "createdBy":"5e09d16d4d36110017506d7f",
      "createdAt":"2020-03-10T15:50:15.759Z",
      "updatedAt":"2020-03-10T15:50:15.759Z",
      "__v":0
   },
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}


{% api-method method="get" host="YOUR\_TILEDESK\_DOMAIN" path="/:project\_id/tags/:id" %}
{% api-method-summary %}
Get a tag by id
{% endapi-method-summary %}


{% api-method-description %}
Only works for Tiledesk v2 environment (on-premises only).
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
the tag identifier
{% endapi-method-parameter %}

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
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
  {
      "_id":"5e67b737fb930c0017aa4e40",
      "tag":"important",
      "color":"#43B1F2",
      "id_project":"5e5d40b2bd0a9b00179ff3cd",
      "createdBy":"5e09d16d4d36110017506d7f",
      "createdAt":"2020-03-10T15:50:15.759Z",
      "updatedAt":"2020-03-10T15:50:15.759Z",
      "__v":0
   }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="YOUR\_TILEDESK\_DOMAIN" path="/:project\_id/tags" %}
{% api-method-summary %}
Create a new tag
{% endapi-method-summary %}

{% api-method-description %}
Only works for Tiledesk v2 environment (on-premises only).
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

{% api-method-parameter name="tag" type="string" required=true %}
the tag name
{% endapi-method-parameter %}

{% api-method-parameter name="color" type="string" required=false %}
the tag color
{% endapi-method-parameter %}


{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
  {
      "_id":"5e67b737fb930c0017aa4e40",
      "tag":"important",
      "color":"#43B1F2",
      "id_project":"5e5d40b2bd0a9b00179ff3cd",
      "createdBy":"5e09d16d4d36110017506d7f",
      "createdAt":"2020-03-10T15:50:15.759Z",
      "updatedAt":"2020-03-10T15:50:15.759Z",
      "__v":0
   }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}


{% api-method method="put" host="YOUR\_TILEDESK\_DOMAIN" path="/:project\_id/tags/:id" %}
{% api-method-summary %}
Update a tag by id
{% endapi-method-summary %}

{% api-method-description %}
Only works for Tiledesk v2 environment (on-premises only).
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="project\_id" type="string" required=true %}
The project\_id is a unique code assigned to your project when you create it in Tiledesk
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
The id is the tag indentifier.
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

{% api-method-parameter name="tag" type="string" required=true %}
the tag name
{% endapi-method-parameter %}

{% api-method-parameter name="color" type="string" required=false %}
the tag color
{% endapi-method-parameter %}


{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
  {
      "_id":"5e67b737fb930c0017aa4e40",
      "tag":"important",
      "color":"#43B1F2",
      "id_project":"5e5d40b2bd0a9b00179ff3cd",
      "createdBy":"5e09d16d4d36110017506d7f",
      "createdAt":"2020-03-10T15:50:15.759Z",
      "updatedAt":"2020-03-10T15:50:15.759Z",
      "__v":0
   }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="delete" host="YOUR\_TILEDESK\_DOMAIN" path="/:project\_id/tags/:id" %}
{% api-method-summary %}
Delete a tag by id
{% endapi-method-summary %}

{% api-method-description %}
Only works for Tiledesk v2 environment (on-premises only).
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="project\_id" type="string" required=true %}
The project\_id is a unique code assigned to your project when you create it in Tiledesk
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
The id is the tag indentifier.
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
...
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

