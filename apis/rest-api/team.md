# Team

The Model 

| Key | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the teammate which is given by Tiledesk. |
| role | String | The teammate role.  Values: owner, agent, admin, user, guest |
| user_available | Boolean | Dermine if the teammate is available or unavailable to accept requests |
| id_user | Object | The user object referenced by the teammate |
| max_served_chat | Number | Number of chats that agent is allowed to take at one time |
| attributes | Object | The custom attributes which are set for the teammate. |
| createdAt | String | The time (ISO-8601 date string) when the teammate was created. |
| updatedAt | String |  The time (ISO-8601 date string) when the teammate was updated.  |
| createdBy | String | The unique identifier of the row creator |
| id_project | String | The unique identifier of the project |
      
      
{% api-method method="get" host="https://api.tiledesk.com" path="/v1/:project\_id/project\_users" %}
{% api-method-summary %}
Get the team
{% endapi-method-summary %}

{% api-method-description %}
Return the team members and availability
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
      "_id":"5df2240cecd41b00173a06bc",
      "id_project":"5df2240cecd41b00173a06bb",
      "id_user":{
         "_id":"5aaa99024c3b110014b478f0",
         "email":"andrea.leo@frontiere21.it",
         "firstname":"Andrea",
         "lastname":"Leo",
         "emailverified":true,
         "__v":0,
         "resetpswrequestid":""
      },
      "role":"owner",
      "user_available":true,
      "createdBy":"5aaa99024c3b110014b478f0",
      "createdAt":"2019-12-12T11:27:08.581Z",
      "updatedAt":"2019-12-12T11:27:08.581Z",
      "__v":0
   },
   {
      "_id":"5df34ab80bc923001792e274",
      "id_project":"5df2240cecd41b00173a06bb",
      "id_user":{
         "_id":"5de9200d6722370017731969",
         "email":"nuovopre@f21test.it",
         "firstname":"Nuovopre",
         "lastname":"Pre",
         "emailverified":false,
         "createdAt":"2019-12-05T15:19:41.296Z",
         "updatedAt":"2019-12-05T15:19:41.296Z",
         "__v":0
      },
      "role":"admin",
      "user_available":true,
      "createdBy":"5aaa99024c3b110014b478f0",
      "createdAt":"2019-12-13T08:24:24.586Z",
      "updatedAt":"2020-01-04T09:45:26.331Z",
      "__v":0
   },
   {
      "_id":"5e09e36d3030640017718ee2",
      "id_project":"5df2240cecd41b00173a06bb",
      "id_user":{
         "_id":"5e09e36d3030640017718edf",
         "email":"magnegerki@enayu.com",
         "firstname":"magnegerki",
         "lastname":"magnegerki",
         "emailverified":false,
         "createdAt":"2019-12-30T11:45:49.123Z",
         "updatedAt":"2019-12-30T11:45:49.123Z",
         "__v":0
      },
      "role":"agent",
      "user_available":false,
      "createdBy":"5aaa99024c3b110014b478f0",
      "createdAt":"2019-12-30T11:45:49.419Z",
      "updatedAt":"2020-01-04T09:45:27.207Z",
      "__v":0
   }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



{% api-method method="get" host="https://api.tiledesk.com" path="/v1/:project\_id/project\_users/:project\_user\_id" %}
{% api-method-summary %}
Get a teammate by id
{% endapi-method-summary %}

{% api-method-description %}
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="project\_id" type="string" required=true %}
the Project Id is a unique code assigned to your project when you create it in Tiledesk.
{% endapi-method-parameter %}

{% api-method-parameter name="project\_user\_id" type="string" required=true %}
The teammate identifier.
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
      "_id":"5df2240cecd41b00173a06bc",
      "id_project":"5df2240cecd41b00173a06bb",
      "id_user":{
         "_id":"5aaa99024c3b110014b478f0",
         "email":"andrea.leo@frontiere21.it",
         "firstname":"Andrea",
         "lastname":"Leo",
         "emailverified":true,
         "__v":0,
         "resetpswrequestid":""
      },
      "role":"owner",
      "user_available":true,
      "createdBy":"5aaa99024c3b110014b478f0",
      "createdAt":"2019-12-12T11:27:08.581Z",
      "updatedAt":"2019-12-12T11:27:08.581Z",
      "__v":0
   }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}





{% api-method method="get" host="https://api.tiledesk.com" path="/v1/:project\_id/project\_users/users/:user\_id" %}
{% api-method-summary %}
Get a teammate by user id
{% endapi-method-summary %}

{% api-method-description %}
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="project\_id" type="string" required=true %}
the Project Id is a unique code assigned to your project when you create it in Tiledesk.
{% endapi-method-parameter %}

{% api-method-parameter name="user\_id" type="string" required=true %}
The user identifier.
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
      "_id":"5df2240cecd41b00173a06bc",
      "id_project":"5df2240cecd41b00173a06bb",
      "id_user":{
         "_id":"5aaa99024c3b110014b478f0",
         "email":"andrea.leo@frontiere21.it",
         "firstname":"Andrea",
         "lastname":"Leo",
         "emailverified":true,
         "__v":0,
         "resetpswrequestid":""
      },
      "role":"owner",
      "user_available":true,
      "createdBy":"5aaa99024c3b110014b478f0",
      "createdAt":"2019-12-12T11:27:08.581Z",
      "updatedAt":"2019-12-12T11:27:08.581Z",
      "__v":0
   }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}







{% api-method method="post" host="https://api.tiledesk.com" path="/v1/:project\_id/project\_users" %}
{% api-method-summary %}
Invite an agent
{% endapi-method-summary %}

{% api-method-description %}
Invite an agent to a project.
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
{% api-method-parameter name="email" type="string" required=true %}
the agent email address
{% endapi-method-parameter %}

{% api-method-parameter name="role" type="string" required=true %}
the agent role. Accepted values: agent, admin
{% endapi-method-parameter %}

{% api-method-parameter name="firstname" type="string" required=false %}
the firstname of the agent
{% endapi-method-parameter %}

{% api-method-parameter name="lastname" type="string" required=false %}
the lastname of the agent
{% endapi-method-parameter %}

{% api-method-parameter name="user_available" type="boolean" required=false %}
the initial agent status. Available (true) or unavailable (false).
{% endapi-method-parameter %}


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




{% api-method method="put" host="https://api.tiledesk.com" path="/v1/:project\_id/project\_users/:project\_user\_id" %}
{% api-method-summary %}
Update a teammate by id
{% endapi-method-summary %}

{% api-method-description %}
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="project\_id" type="string" required=true %}
The project\_id is a unique code assigned to your project when you create it in Tiledesk
{% endapi-method-parameter %}

{% api-method-parameter name="project\_user\_id" type="string" required=true %}
The teammate identifier.
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
{% api-method-parameter name="role" type="string" required=false %}
The teammate role. Permitted values: admin, agent.
{% endapi-method-parameter %}

{% api-method-parameter name="user_available" type="boolean" required=false %}
The teammate availability. True for available, false for unavailable. _Default is true_
{% endapi-method-parameter %}

{% api-method-parameter name="max_served_chat" type="number" required=false %}
The number of concurrent chats the teammate can take at once.
{% endapi-method-parameter %}


{% api-method-parameter name="attributes" type="object" required=false %}
The teammate custom attributes
{% endapi-method-parameter %}

{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{  
         ..
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}






{% api-method method="delete" host="https://api.tiledesk.com" path="/v1/:project\_id/project\_users/:project\_user\_id" %}
{% api-method-summary %}
Leave a project
{% endapi-method-summary %}

{% api-method-description %}
Leave an agent from a project.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="project\_id" type="string" required=true %}
The project\_id is a unique code assigned to your project when you create it in Tiledesk
{% endapi-method-parameter %}

{% api-method-parameter name="project\_user\_id" type="string" required=true %}
The teammate identifier.
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
        ...
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

