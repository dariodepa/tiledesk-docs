# Groups

{% api-method method="get" host="https://api.tiledesk.com" path="/v1/:project\_id/groups" %}
{% api-method-summary %}
Get all groups
{% endapi-method-summary %}

{% api-method-description %}
Allows an account to list all the groups of the project.
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
      "_id":"5c34b5149f22a7001681e887",
      "updatedAt":"2019-01-08T14:35:09.621Z",
      "createdAt":"2019-01-08T14:35:00.625Z",
      "name":"gruppo1",
      "trashed":false,
      "id_project":"5b55e806c93dde00143163dd",
      "createdBy":"5ab0f3fa57066e0014bfd71e",
      "__v":0,
      "members":[
         "5ad5bd40c975820014ba9009"
      ]
   },
   {
      "_id":"5c34b52a9f22a7001681e888",
      "updatedAt":"2019-01-08T14:35:29.678Z",
      "createdAt":"2019-01-08T14:35:22.489Z",
      "name":"gruppo2",
      "trashed":false,
      "id_project":"5b55e806c93dde00143163dd",
      "createdBy":"5ab0f3fa57066e0014bfd71e",
      "__v":0,
      "members":[
         "5ab0f3fa57066e0014bfd71e"
      ]
   }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example

```text
curl -v -X GET -u andrea.leo@f21.it:123456 https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/groups
```

{% api-method method="get" host="https://api.tiledesk.com" path="/v1/:project\_id/groups/:id" %}
{% api-method-summary %}
Get the group by id
{% endapi-method-summary %}

{% api-method-description %}
Fetche the group by his or her id
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
the group identifier
{% endapi-method-parameter %}

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
  {
   "_id":"5c34b52a9f22a7001681e888",
   "updatedAt":"2019-01-08T14:35:29.678Z",
   "createdAt":"2019-01-08T14:35:22.489Z",
   "name":"gruppo2",
   "trashed":false,
   "id_project":"5b55e806c93dde00143163dd",
   "createdBy":"5ab0f3fa57066e0014bfd71e",
   "__v":0,
   "members":[
      "5ab0f3fa57066e0014bfd71e"
   ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example:

```text
curl -v -X GET -u andrea.leo@f21.it:123456 https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/groups/5c34b52a9f22a7001681e888
```

{% api-method method="post" host="https://api.tiledesk.com" path="/v1/:project\_id/groups" %}
{% api-method-summary %}
Create a new group
{% endapi-method-summary %}

{% api-method-description %}
Allows to add more groups.
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
The group name
{% endapi-method-parameter %}

{% api-method-parameter name="members" type="array" required=true %}
The group members ids.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
 {
   "_id":"5c34b52a9f22a7001681e888",
   "updatedAt":"2019-01-08T14:35:29.678Z",
   "createdAt":"2019-01-08T14:35:22.489Z",
   "name":"gruppo2",
   "trashed":false,
   "id_project":"5b55e806c93dde00143163dd",
   "createdBy":"5ab0f3fa57066e0014bfd71e",
   "__v":0,
   "members":[
      "5ab0f3fa57066e0014bfd71e"
   ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example:

```text
curl -v -X POST -H 'Content-Type: application/json' -u andrea.leo@f21.it:123456  -d '{"name":"new group1", "members":["5ab0f3fa57066e0014bfd71e"]}' https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/groups
```

{% api-method method="put" host="https://api.tiledesk.com" path="/v1/:project\_id/groups/:id" %}
{% api-method-summary %}
Update a group
{% endapi-method-summary %}

{% api-method-description %}
Allows to update a group.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="project\_id" type="string" required=true %}
The project\_id is a unique code assigned to your project when you create it in Tiledesk
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
The group identifier
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
The group name
{% endapi-method-parameter %}

{% api-method-parameter name="members" type="array" required=true %}
The group members ids.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
 {
   "_id":"5c34b52a9f22a7001681e888",
   "updatedAt":"2019-01-08T14:35:29.678Z",
   "createdAt":"2019-01-08T14:35:22.489Z",
   "name":"gruppo2",
   "trashed":false,
   "id_project":"5b55e806c93dde00143163dd",
   "createdBy":"5ab0f3fa57066e0014bfd71e",
   "__v":0,
   "members":[
      "5ab0f3fa57066e0014bfd71e"
   ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example:

```text
curl -v -X PUT -H 'Content-Type: application/json' -u andrea.leo@f21.it:123456  -d '{"name":"new group1", "members":["5ab0f3fa57066e0014bfd71e"]}' https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/groups/groups/5c34b52a9f22a7001681e888
```

{% api-method method="delete" host="https://api.tiledesk.com" path="/v1/:project\_id/groups/:id" %}
{% api-method-summary %}
Delete a group
{% endapi-method-summary %}

{% api-method-description %}
Allows to delete a group.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="project\_id" type="string" required=true %}
The project\_id is a unique code assigned to your project when you create it in Tiledesk
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
The group identifier
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
   "_id":"5c34b52a9f22a7001681e888",
   "updatedAt":"2019-01-08T14:35:29.678Z",
   "createdAt":"2019-01-08T14:35:22.489Z",
   "name":"gruppo2",
   "trashed":false,
   "id_project":"5b55e806c93dde00143163dd",
   "createdBy":"5ab0f3fa57066e0014bfd71e",
   "__v":0,
   "members":[
      "5ab0f3fa57066e0014bfd71e"
   ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example:

```text
curl -v -X DELETE -H 'Content-Type: application/json' -u andrea.leo@f21.it:123456  https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/groups/5c34b52a9f22a7001681e888
```

