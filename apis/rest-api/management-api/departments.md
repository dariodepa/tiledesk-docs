# Departments

{% api-method method="get" host="https://api.tiledesk.com" path="/v1/:project\_id/departments" %}
{% api-method-summary %}
Get all active departments.
{% endapi-method-summary %}

{% api-method-description %}
Allows an account to list all the active departments of the project.
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
[
   {
      "_id":"5b55e806c93dde00143163df",
      "updatedAt":"2019-08-02T08:08:22.292Z",
      "createdAt":"2018-07-23T14:36:54.410Z",
      "name":"Default Department",
      "id_project":"5b55e806c93dde00143163dd",
      "createdBy":"5aaa99024c3b110014b478f0",
      "online_msg":"Describe shortly your problem, you will be contacted by an agent..",
      "offline_msg":"",
      "__v":0,
      "bot_only":false,
      "id_bot":"5be9b2ecc72a050015e14951",
      "status":1,
      "default":true,
      "routing":"assigned"
   }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example

```text
curl -v -X GET https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/departments
```

{% api-method method="get" host="https://api.tiledesk.com" path="/v1/:project\_id/departments/allstatus" %}
{% api-method-summary %}
Get all departments \(active or hidden\).
{% endapi-method-summary %}

{% api-method-description %}
Allows an account to list all the departments of the project.
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
      "_id":"5b55e806c93dde00143163df",
      "updatedAt":"2019-08-02T08:08:22.292Z",
      "createdAt":"2018-07-23T14:36:54.410Z",
      "name":"Default Department",
      "id_project":"5b55e806c93dde00143163dd",
      "createdBy":"5aaa99024c3b110014b478f0",
      "online_msg":"Describe shortly your problem, you will be contacted by an agent..",
      "offline_msg":"",
      "__v":0,
      "bot_only":false,
      "id_bot":"5be9b2ecc72a050015e14951",
      "status":1,
      "default":true,
      "routing":"assigned"
   }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example

```text
curl -v -X GET -u andrea.leo@f21.it:123456 https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/departments/allstatus
```

{% api-method method="get" host="https://api.tiledesk.com" path="/v1/:project\_id/departments" %}
{% api-method-summary %}
Get a department by id
{% endapi-method-summary %}

{% api-method-description %}
Allows an account to get a department of the project.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="project\_id" type="string" required=true %}
the Project Id is a unique code assigned to your project when you create it in Tiledesk.
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
The department identifier
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
      "_id":"5b55e806c93dde00143163df",
      "updatedAt":"2019-08-02T08:08:22.292Z",
      "createdAt":"2018-07-23T14:36:54.410Z",
      "name":"Default Department",
      "id_project":"5b55e806c93dde00143163dd",
      "createdBy":"5aaa99024c3b110014b478f0",
      "online_msg":"Describe shortly your problem, you will be contacted by an agent..",
      "offline_msg":"",
      "__v":0,
      "bot_only":false,
      "id_bot":"5be9b2ecc72a050015e14951",
      "status":1,
      "default":true,
      "routing":"assigned"
   }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example

```text
curl -v -X GET -u andrea.leo@f21.it:123456 https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/departments/5b55e806c93dde00143163df
```

{% api-method method="post" host="https://api.tiledesk.com" path="/v1/:project\_id/departments" %}
{% api-method-summary %}
Create a new department
{% endapi-method-summary %}

{% api-method-description %}
Allows to add more departments.
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
The department name
{% endapi-method-parameter %}

{% api-method-parameter name="routing" type="string" required=false %}
The department routing type. Permitted values: 'assigned', 'pooled' \(default\)
{% endapi-method-parameter %}

{% api-method-parameter name="id\_group" type="string" required=false %}
The group of users assigned to the department.
{% endapi-method-parameter %}

{% api-method-parameter name="id\_bot" type="string" required=false %}
The bot assigned to the department.
{% endapi-method-parameter %}

{% api-method-parameter name="bot\_only " type="boolean" required=false %}
Specify if the visitor can talk only with a bot or even with an agent. Default value: false
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
 {
      "_id":"5b55e806c93dde00143163df",
      "updatedAt":"2019-08-02T08:08:22.292Z",
      "createdAt":"2018-07-23T14:36:54.410Z",
      "name":"Default Department",
      "id_project":"5b55e806c93dde00143163dd",
      "createdBy":"5aaa99024c3b110014b478f0",
      "online_msg":"Describe shortly your problem, you will be contacted by an agent..",
      "offline_msg":"",
      "__v":0,
      "bot_only":false,
      "id_bot":"5be9b2ecc72a050015e14951",
      "status":1,
      "default":true,
      "routing":"assigned"
   }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example:

```text
curl -v -X POST -H 'Content-Type: application/json' -u andrea.leo@f21.it:123456  -d '{"name":"new department1", "routing":"pooled"}' https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/departments
```

{% api-method method="put" host="https://api.tiledesk.com" path="/v1/:project\_id/departments/:id" %}
{% api-method-summary %}
Update a department
{% endapi-method-summary %}

{% api-method-description %}
Allows to update a department.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="project\_id" type="string" required=true %}
The project\_id is a unique code assigned to your project when you create it in Tiledesk
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
The department identifier
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
The department name
{% endapi-method-parameter %}

{% api-method-parameter name="routing" type="string" required=false %}
The department routing type. Permitted values: 'assigned', 'pooled' \(default\)
{% endapi-method-parameter %}

{% api-method-parameter name="id\_group" type="string" required=false %}
The group of users assigned to the department.
{% endapi-method-parameter %}

{% api-method-parameter name="id\_bot" type="string" required=false %}
The bot assigned to the department.
{% endapi-method-parameter %}

{% api-method-parameter name="bot\_only " type="boolean" required=false %}
Specify if the visitor can talk only with a bot or even with an agent. Default value: false
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
 {
      "_id":"5b55e806c93dde00143163df",
      "updatedAt":"2019-08-02T08:08:22.292Z",
      "createdAt":"2018-07-23T14:36:54.410Z",
      "name":"Default Department",
      "id_project":"5b55e806c93dde00143163dd",
      "createdBy":"5aaa99024c3b110014b478f0",
      "online_msg":"Describe shortly your problem, you will be contacted by an agent..",
      "offline_msg":"",
      "__v":0,
      "bot_only":false,
      "id_bot":"5be9b2ecc72a050015e14951",
      "status":1,
      "default":true,
      "routing":"assigned"
   }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example:

```text
curl -v -X PUT -H 'Content-Type: application/json' -u andrea.leo@f21.it:123456  -d '{"name":"new department1", "routing":"pooled"}' https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/departments/5b55e806c93dde00143163df
```

{% api-method method="delete" host="https://api.tiledesk.com" path="/v1/:project\_id/departments/:id" %}
{% api-method-summary %}
Delete a department
{% endapi-method-summary %}

{% api-method-description %}
Allows to delete a department.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="project\_id" type="string" required=true %}
The project\_id is a unique code assigned to your project when you create it in Tiledesk
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
The department identifier
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
      "_id":"5b55e806c93dde00143163df",
      "updatedAt":"2019-08-02T08:08:22.292Z",
      "createdAt":"2018-07-23T14:36:54.410Z",
      "name":"Default Department",
      "id_project":"5b55e806c93dde00143163dd",
      "createdBy":"5aaa99024c3b110014b478f0",
      "online_msg":"Describe shortly your problem, you will be contacted by an agent..",
      "offline_msg":"",
      "__v":0,
      "bot_only":false,
      "id_bot":"5be9b2ecc72a050015e14951",
      "status":1,
      "default":true,
      "routing":"assigned"
   }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example:

```text
curl -v -X DELETE -H 'Content-Type: application/json' -u andrea.leo@f21.it:123456  https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/departments/5b55e806c93dde00143163df
```

