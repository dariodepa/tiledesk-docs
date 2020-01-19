# Requests

You can use the API to get the request information.

{% api-method method="get" host="https://api.tiledesk.com" path="/v1/:project\_id/requests" %}
{% api-method-summary %}
Get all requests
{% endapi-method-summary %}

{% api-method-description %}
Allows an account to list all the requests for the project.
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
what field to sort the results by.
{% endapi-method-parameter %}

{% api-method-parameter name="direction" type="string" required=false %}
sort direction: 1 or -1. Return the results in ascending or descending order. _defaults to desc_
{% endapi-method-parameter %}

{% api-method-parameter name="page" type="string" required=false %}
what page of results to fetch. defaults to first page.
{% endapi-method-parameter %}


{% api-method-parameter name="full\_text" type="string" required=false %}
make a fulltext search query
{% endapi-method-parameter %}

{% api-method-parameter name="status" type="string" required=false %}
filter by request status. Values: 100 for assigned requests, 200 for pooled requests, 1000 for closed requests
{% endapi-method-parameter %}

{% api-method-parameter name="dept\_id" type="string" required=false %}
filter by department id
{% endapi-method-parameter %}

{% api-method-parameter name="lead" type="string" required=false %}
filter by lead id
{% endapi-method-parameter %}

{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
   "perPage":40,
   "count":179,
   "requests":[
      {
            "_id":"5c81593adf767b0017d1aa67",
            "updatedAt":"2019-03-07T17:48:05.934Z",
            "createdAt":"2019-03-07T17:47:38.405Z",
            "request_id":"support-group-L_OG76RYhR0XFiMf2PK",
            "requester_id":"5c81593adf767b0017d1aa66",
            "first_text":"first text message",
            "department":"5c34ba232c62730016da250e",
            "sourcePage":"https://www.tiledesk.com",
            "language":"it",
            "userAgent":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/72.0.3626.119 Safari/537.36",
            "id_project":"5b55e806c93dde00143163dd",
            "createdBy":"5c81593adf767b0017d1aa66",
            "__v":2,
            "waiting_time":21709,
            "agents":[
               {
                  "__v":0,
                  "createdBy":"5aaa99024c3b110014b478f0",
                  "user_available":true,
                  "role":"admin",
                  "id_user":"5ab0f3fa57066e0014bfd71e",
                  "id_project":"5b55e806c93dde00143163dd",
                  "createdAt":"2018-10-03T14:40:19.521Z",
                  "updatedAt":"2019-03-07T17:47:38.405Z",
                  "_id":"5bb4d4d39214830015742b00"
               }
            ],
            "tags":[
            ],
            "messages_count":7,
            "participants":[
               "5aaa99024c3b110014b478f0"
            ],
            "status":200,
            "lead":{..}
         }
      ...
   ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example

```text
curl -v -X GET -u andrea.leo@f21.it:123456 https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/requests
```

{% api-method method="get" host="https://api.tiledesk.com" path="/v1/:project\_id/requests/:id" %}
{% api-method-summary %}
Get a request by id
{% endapi-method-summary %}

{% api-method-description %}
Fetches a request by his or her request\_id
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
the request identifier
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

{% api-method-query-parameters %}
{% api-method-parameter name="sortField" type="string" required=false %}
what field to sort the results by.
{% endapi-method-parameter %}

{% api-method-parameter name="direction" type="string" required=false %}
sort direction: 1 or -1. Return the results in ascending or descending order. _defaults to desc_
{% endapi-method-parameter %}

{% api-method-parameter name="page" type="string" required=false %}
what page of results to fetch. defaults to first page.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
   "_id":"5c81593adf767b0017d1aa67",
   "updatedAt":"2019-03-07T17:48:05.934Z",
   "createdAt":"2019-03-07T17:47:38.405Z",
   "request_id":"support-group-L_OG76RYhR0XFiMf2PK",
   "requester_id":"5c81593adf767b0017d1aa66",
   "first_text":"first text message",
   "department":"5c34ba232c62730016da250e",
   "sourcePage":"https://www.tiledesk.com",
   "language":"it",
   "userAgent":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/72.0.3626.119 Safari/537.36",
   "id_project":"5b55e806c93dde00143163dd",
   "createdBy":"5c81593adf767b0017d1aa66",
   "__v":2,
   "waiting_time":21709,
   "agents":[
      {
         "__v":0,
         "createdBy":"5aaa99024c3b110014b478f0",
         "user_available":true,
         "role":"admin",
         "id_user":"5ab0f3fa57066e0014bfd71e",
         "id_project":"5b55e806c93dde00143163dd",
         "createdAt":"2018-10-03T14:40:19.521Z",
         "updatedAt":"2019-03-07T17:47:38.405Z",
         "_id":"5bb4d4d39214830015742b00"
      }
   ],
   "tags":[
   ],
   "messages_count":7,
   "participants":[
      "5aaa99024c3b110014b478f0"
   ],
   "status":200,
   "lead":{..}
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example:

```text
curl -v -X GET -u andrea.leo@f21.it:123456 https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/requests/support-group-L_OG76RYhR0XFiMf2PK
```







{% api-method method="put" host="https://api.tiledesk.com" path="/v1/:project\_id/requests/:id/close" %}
{% api-method-summary %}
Close a request by id.
It only works for Tiledesk beta version v2 environment.
{% endapi-method-summary %}

{% api-method-description %}
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
the request identifier
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

{% api-method-query-parameters %}
{% endapi-method-query-parameters %}

{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
   "_id":"5c81593adf767b0017d1aa67",
   "updatedAt":"2019-03-07T17:48:05.934Z",
   "createdAt":"2019-03-07T17:47:38.405Z",
   "request_id":"support-group-L_OG76RYhR0XFiMf2PK",
   "requester_id":"5c81593adf767b0017d1aa66",
   "first_text":"first text message",
   "department":"5c34ba232c62730016da250e",
   "sourcePage":"https://www.tiledesk.com",
   "language":"it",
   "userAgent":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/72.0.3626.119 Safari/537.36",
   "id_project":"5b55e806c93dde00143163dd",
   "createdBy":"5c81593adf767b0017d1aa66",
   "__v":2,
   "waiting_time":21709,
   "agents":[
      {
         "__v":0,
         "createdBy":"5aaa99024c3b110014b478f0",
         "user_available":true,
         "role":"admin",
         "id_user":"5ab0f3fa57066e0014bfd71e",
         "id_project":"5b55e806c93dde00143163dd",
         "createdAt":"2018-10-03T14:40:19.521Z",
         "updatedAt":"2019-03-07T17:47:38.405Z",
         "_id":"5bb4d4d39214830015742b00"
      }
   ],
   "tags":[
   ],
   "messages_count":7,
   "participants":[
      "5aaa99024c3b110014b478f0"
   ],
   "status":1000,
   "lead":{..}
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}







{% api-method method="put" host="https://api.tiledesk.com" path="/v1/:project\_id/requests/:id/reopen" %}
{% api-method-summary %}
Reopen a request by id.
It only works for Tiledesk beta version v2 environment.
{% endapi-method-summary %}

{% api-method-description %}
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
the request identifier
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

{% api-method-query-parameters %}
{% endapi-method-query-parameters %}

{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
   "_id":"5c81593adf767b0017d1aa67",
   "updatedAt":"2019-03-07T17:48:05.934Z",
   "createdAt":"2019-03-07T17:47:38.405Z",
   "request_id":"support-group-L_OG76RYhR0XFiMf2PK",
   "requester_id":"5c81593adf767b0017d1aa66",
   "first_text":"first text message",
   "department":"5c34ba232c62730016da250e",
   "sourcePage":"https://www.tiledesk.com",
   "language":"it",
   "userAgent":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/72.0.3626.119 Safari/537.36",
   "id_project":"5b55e806c93dde00143163dd",
   "createdBy":"5c81593adf767b0017d1aa66",
   "__v":2,
   "waiting_time":21709,
   "agents":[
      {
         "__v":0,
         "createdBy":"5aaa99024c3b110014b478f0",
         "user_available":true,
         "role":"admin",
         "id_user":"5ab0f3fa57066e0014bfd71e",
         "id_project":"5b55e806c93dde00143163dd",
         "createdAt":"2018-10-03T14:40:19.521Z",
         "updatedAt":"2019-03-07T17:47:38.405Z",
         "_id":"5bb4d4d39214830015742b00"
      }
   ],
   "tags":[
   ],
   "messages_count":7,
   "participants":[
      "5aaa99024c3b110014b478f0"
   ],
   "status":100,
   "lead":{..}
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}










{% api-method method="put" host="https://api.tiledesk.com" path="/v1/:project\_id/requests/:id/departments" %}
{% api-method-summary %}
Route a request to a department
{% endapi-method-summary %}

{% api-method-description %}
Route a request to a department 
It only works for Tiledesk beta version v2 environment.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
the request identifier
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

{% api-method-body-parameters %}
{% api-method-parameter name="departmentid" type="string" required=true %}
the department identifier
{% endapi-method-parameter %}

{% api-method-parameter name="nobot" type="boolean" required=false %}
esclude a bot for the assignment
{% endapi-method-parameter %}

{% endapi-method-body-parameters %}

{% api-method-query-parameters %}
{% endapi-method-query-parameters %}

{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
   "_id":"5c81593adf767b0017d1aa67",
   "updatedAt":"2019-03-07T17:48:05.934Z",
   "createdAt":"2019-03-07T17:47:38.405Z",
   "request_id":"support-group-L_OG76RYhR0XFiMf2PK",
   "requester_id":"5c81593adf767b0017d1aa66",
   "first_text":"first text message",
   "department":"5c34ba232c62730016da250e",
   "sourcePage":"https://www.tiledesk.com",
   "language":"it",
   "userAgent":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/72.0.3626.119 Safari/537.36",
   "id_project":"5b55e806c93dde00143163dd",
   "createdBy":"5c81593adf767b0017d1aa66",
   "__v":2,
   "waiting_time":21709,
   "agents":[
      {
         "__v":0,
         "createdBy":"5aaa99024c3b110014b478f0",
         "user_available":true,
         "role":"admin",
         "id_user":"5ab0f3fa57066e0014bfd71e",
         "id_project":"5b55e806c93dde00143163dd",
         "createdAt":"2018-10-03T14:40:19.521Z",
         "updatedAt":"2019-03-07T17:47:38.405Z",
         "_id":"5bb4d4d39214830015742b00"
      }
   ],
   "tags":[
   ],
   "messages_count":7,
   "participants":[
      "5aaa99024c3b110014b478f0"
   ],
   "status":100,
   "lead":{..}
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}












{% api-method method="patch" host="https://api.tiledesk.com" path="/v1/:project\_id/requests/:id/" %}
{% api-method-summary %}
Update a request by id
{% endapi-method-summary %}

{% api-method-description %}
It only works for Tiledesk beta version v2 environment.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
the request identifier
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

{% api-method-body-parameters %}
{% api-method-parameter name="lead" type="string" required=false %}
the lead identifier
{% endapi-method-parameter %}

{% api-method-parameter name="status" type="number" required=false %}
the request status
{% endapi-method-parameter %}


{% api-method-parameter name="tags" type="array" required=false %}
the request tags
{% endapi-method-parameter %}

{% api-method-parameter name="rating" type="number" required=false %}
the request rating
{% endapi-method-parameter %}

{% api-method-parameter name="rating_message" type="string" required=false %}
the request rating message
{% endapi-method-parameter %}

{% api-method-parameter name="language" type="string" required=false %}
the request language
{% endapi-method-parameter %}


{% api-method-parameter name="sourcePage" type="string" required=false %}
the request source page
{% endapi-method-parameter %}



{% endapi-method-body-parameters %}

{% api-method-query-parameters %}
{% endapi-method-query-parameters %}

{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
   "_id":"5c81593adf767b0017d1aa67",
   "updatedAt":"2019-03-07T17:48:05.934Z",
   "createdAt":"2019-03-07T17:47:38.405Z",
   "request_id":"support-group-L_OG76RYhR0XFiMf2PK",
   "requester_id":"5c81593adf767b0017d1aa66",
   "first_text":"first text message",
   "department":"5c34ba232c62730016da250e",
   "sourcePage":"https://www.tiledesk.com",
   "language":"it",
   "userAgent":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/72.0.3626.119 Safari/537.36",
   "id_project":"5b55e806c93dde00143163dd",
   "createdBy":"5c81593adf767b0017d1aa66",
   "__v":2,
   "waiting_time":21709,
   "agents":[
      {
         "__v":0,
         "createdBy":"5aaa99024c3b110014b478f0",
         "user_available":true,
         "role":"admin",
         "id_user":"5ab0f3fa57066e0014bfd71e",
         "id_project":"5b55e806c93dde00143163dd",
         "createdAt":"2018-10-03T14:40:19.521Z",
         "updatedAt":"2019-03-07T17:47:38.405Z",
         "_id":"5bb4d4d39214830015742b00"
      }
   ],
   "tags":[
   ],
   "messages_count":7,
   "participants":[
      "5aaa99024c3b110014b478f0"
   ],
   "status":100,
   "lead":{..}
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}









{% api-method method="post" host="https://api.tiledesk.com" path="/v1/:project\_id/requests/:id/participants" %}
{% api-method-summary %}
Add a participant to a request
{% endapi-method-summary %}

{% api-method-description %}
Add a participant (agent or bot) to a request
It only works for Tiledesk beta version v2 environment.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
the request identifier
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

{% api-method-body-parameters %}
{% api-method-parameter name="member" type="string" required=true %}
the participant (agent or bot) identifier
{% endapi-method-parameter %}



{% endapi-method-body-parameters %}

{% api-method-query-parameters %}
{% endapi-method-query-parameters %}

{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
   "_id":"5c81593adf767b0017d1aa67",
   "updatedAt":"2019-03-07T17:48:05.934Z",
   "createdAt":"2019-03-07T17:47:38.405Z",
   "request_id":"support-group-L_OG76RYhR0XFiMf2PK",
   "requester_id":"5c81593adf767b0017d1aa66",
   "first_text":"first text message",
   "department":"5c34ba232c62730016da250e",
   "sourcePage":"https://www.tiledesk.com",
   "language":"it",
   "userAgent":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/72.0.3626.119 Safari/537.36",
   "id_project":"5b55e806c93dde00143163dd",
   "createdBy":"5c81593adf767b0017d1aa66",
   "__v":2,
   "waiting_time":21709,
   "agents":[
      {
         "__v":0,
         "createdBy":"5aaa99024c3b110014b478f0",
         "user_available":true,
         "role":"admin",
         "id_user":"5ab0f3fa57066e0014bfd71e",
         "id_project":"5b55e806c93dde00143163dd",
         "createdAt":"2018-10-03T14:40:19.521Z",
         "updatedAt":"2019-03-07T17:47:38.405Z",
         "_id":"5bb4d4d39214830015742b00"
      }
   ],
   "tags":[
   ],
   "messages_count":7,
   "participants":[
      "5aaa99024c3b110014b478f0"
   ],
   "status":100,
   "lead":{..}
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}








{% api-method method="put" host="https://api.tiledesk.com" path="/v1/:project\_id/requests/:id/participants" %}
{% api-method-summary %}
Set the request participants
{% endapi-method-summary %}

{% api-method-description %}
Set the request participants (agent or bot)
It only works for Tiledesk beta version v2 environment.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
the request identifier
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

{% api-method-body-parameters %}
{% api-method-parameter name="members" type="array" required=true %}
the participant (agent or bot) identifier array
{% endapi-method-parameter %}



{% endapi-method-body-parameters %}

{% api-method-query-parameters %}
{% endapi-method-query-parameters %}

{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
   "_id":"5c81593adf767b0017d1aa67",
   "updatedAt":"2019-03-07T17:48:05.934Z",
   "createdAt":"2019-03-07T17:47:38.405Z",
   "request_id":"support-group-L_OG76RYhR0XFiMf2PK",
   "requester_id":"5c81593adf767b0017d1aa66",
   "first_text":"first text message",
   "department":"5c34ba232c62730016da250e",
   "sourcePage":"https://www.tiledesk.com",
   "language":"it",
   "userAgent":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/72.0.3626.119 Safari/537.36",
   "id_project":"5b55e806c93dde00143163dd",
   "createdBy":"5c81593adf767b0017d1aa66",
   "__v":2,
   "waiting_time":21709,
   "agents":[
      {
         "__v":0,
         "createdBy":"5aaa99024c3b110014b478f0",
         "user_available":true,
         "role":"admin",
         "id_user":"5ab0f3fa57066e0014bfd71e",
         "id_project":"5b55e806c93dde00143163dd",
         "createdAt":"2018-10-03T14:40:19.521Z",
         "updatedAt":"2019-03-07T17:47:38.405Z",
         "_id":"5bb4d4d39214830015742b00"
      }
   ],
   "tags":[
   ],
   "messages_count":7,
   "participants":[
      "5aaa99024c3b110014b478f0"
   ],
   "status":100,
   "lead":{..}
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}










{% api-method method="delete" host="https://api.tiledesk.com" path="/v1/:project\_id/requests/:id/participants" %}
{% api-method-summary %}
Delete a participant from the request
{% endapi-method-summary %}

{% api-method-description %}
Delete a participant (agent or bot) from the request
It only works for Tiledesk beta version v2 environment.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
the request identifier
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

{% api-method-body-parameters %}
{% api-method-parameter name="member" type="string" required=true %}
the participant (agent or bot) identifier
{% endapi-method-parameter %}



{% endapi-method-body-parameters %}

{% api-method-query-parameters %}
{% endapi-method-query-parameters %}

{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
   "_id":"5c81593adf767b0017d1aa67",
   "updatedAt":"2019-03-07T17:48:05.934Z",
   "createdAt":"2019-03-07T17:47:38.405Z",
   "request_id":"support-group-L_OG76RYhR0XFiMf2PK",
   "requester_id":"5c81593adf767b0017d1aa66",
   "first_text":"first text message",
   "department":"5c34ba232c62730016da250e",
   "sourcePage":"https://www.tiledesk.com",
   "language":"it",
   "userAgent":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/72.0.3626.119 Safari/537.36",
   "id_project":"5b55e806c93dde00143163dd",
   "createdBy":"5c81593adf767b0017d1aa66",
   "__v":2,
   "waiting_time":21709,
   "agents":[
      {
         "__v":0,
         "createdBy":"5aaa99024c3b110014b478f0",
         "user_available":true,
         "role":"admin",
         "id_user":"5ab0f3fa57066e0014bfd71e",
         "id_project":"5b55e806c93dde00143163dd",
         "createdAt":"2018-10-03T14:40:19.521Z",
         "updatedAt":"2019-03-07T17:47:38.405Z",
         "_id":"5bb4d4d39214830015742b00"
      }
   ],
   "tags":[
   ],
   "messages_count":7,
   "participants":[
      "5aaa99024c3b110014b478f0"
   ],
   "status":100,
   "lead":{..}
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}











{% api-method method="patch" host="https://api.tiledesk.com" path="/v1/:project\_id/requests/:id/attributes" %}
{% api-method-summary %}
Update the request attributes
{% endapi-method-summary %}

{% api-method-description %}
Update the request custom attributes
It only works for Tiledesk beta version v2 environment.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
the request identifier
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

{% api-method-body-parameters %}
{% api-method-parameter name="attributes" type="object" required=true %}
the request attributes
{% endapi-method-parameter %}



{% endapi-method-body-parameters %}

{% api-method-query-parameters %}
{% endapi-method-query-parameters %}

{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
   "_id":"5c81593adf767b0017d1aa67",
   "updatedAt":"2019-03-07T17:48:05.934Z",
   "createdAt":"2019-03-07T17:47:38.405Z",
   "request_id":"support-group-L_OG76RYhR0XFiMf2PK",
   "requester_id":"5c81593adf767b0017d1aa66",
   "first_text":"first text message",
   "department":"5c34ba232c62730016da250e",
   "sourcePage":"https://www.tiledesk.com",
   "language":"it",
   "userAgent":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/72.0.3626.119 Safari/537.36",
   "id_project":"5b55e806c93dde00143163dd",
   "createdBy":"5c81593adf767b0017d1aa66",
   "__v":2,
   "waiting_time":21709,
   "agents":[
      {
         "__v":0,
         "createdBy":"5aaa99024c3b110014b478f0",
         "user_available":true,
         "role":"admin",
         "id_user":"5ab0f3fa57066e0014bfd71e",
         "id_project":"5b55e806c93dde00143163dd",
         "createdAt":"2018-10-03T14:40:19.521Z",
         "updatedAt":"2019-03-07T17:47:38.405Z",
         "_id":"5bb4d4d39214830015742b00"
      }
   ],
   "tags":[
   ],
   "messages_count":7,
   "participants":[
      "5aaa99024c3b110014b478f0"
   ],
   "status":100,
   "lead":{..}
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



