# Projects

The Project model

| Key | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the project which is given by Tiledesk. |
| name | String | The project name. |
| activeOperatingHours | Boolena | Determine if the operating hours option is enabled |
| operatingHours | Object | The operating hours settings. |
| settings | Object | The project settings |
| widget | Object | The widget settings. |
| profile | Object | The project profile object |
| status | Number | The project status. Permitted values: 100 active, 0 disabled |
| createdAt | String | The time \(ISO-8601 date string\) when the project was created. |
| updatedAt | String | The time \(ISO-8601 date string\) when the project was updated. |
| createdBy | String | The unique identifier of the row creator |

{% api-method method="get" host="https://api.tiledesk.com" path="/v1/projects/" %}
{% api-method-summary %}
Get a list of projects the user belongs
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
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
      "_id":"5acdc6d86fb82500141d56c9",
      "updatedAt":"2019-01-31T18:09:53.417Z",
      "createdAt":"2018-04-11T08:27:04.509Z",
      "id_project":{
         "versions":30,
         "_id":"5acba41a213ae3001451b723",
         "updatedAt":"2019-01-29T12:01:06.793Z",
         "createdAt":"2018-04-09T17:34:18.064Z",
         "name":"conversational landing page",
         "createdBy":"5aabade839db7d001477d3d5",
         "__v":0,
         "profile":{
            "name":"free",
            "trialDays":30,
            "agents":0,
            "type":"free"
         },
         "channels":[
            {
               "name":"chat21"
            }
         ],
         "trialExpired":true,
         "trialDaysLeft":680,
         "isActiveSubscription":false,
         "id":"5acba41a213ae3001451b723"
      },
      "id_user":"5aaa99024c3b110014b478f0",
      "role":"admin",
      "createdBy":"5aabade839db7d001477d3d5",
      "__v":0,
      "user_available":true,
      "id":"5acdc6d86fb82500141d56c9"
   },
...
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.tiledesk.com" path="/v1/projects/:project\_id" %}
{% api-method-summary %}
Get the project detail
{% endapi-method-summary %}

{% api-method-description %}

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
{
   "versions":30,
   "_id":"5df2240cecd41b00173a06bb",
   "name":"000000",
   "activeOperatingHours":true,
   "createdBy":"5aaa99024c3b110014b478f0",
   "profile":{
      "name":"free",
      "trialDays":30,
      "agents":0,
      "type":"free"
   },
   "channels":[
      {
         "name":"chat21"
      }
   ],
   "createdAt":"2019-12-12T11:27:08.548Z",
   "updatedAt":"2020-01-08T10:53:12.844Z",
   "__v":0,
   "operatingHours":"{\"0\":[{\"start\":\"09:00\",\"end\":\"13:00\"},{\"start\":\"14:00\",\"end\":\"18:00\"}],\"1\":[{\"start\":\"09:00\",\"end\":\"13:00\"},{\"start\":\"14:00\",\"end\":\"18:00\"}],\"tzname\":\"Europe/Rome\"}",
   "trialExpired":false,
   "trialDaysLeft":-4,
   "isActiveSubscription":false,
   "id":"5df2240cecd41b00173a06bb"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.tiledesk.com" path="/v1/projects/:project\_id/users/availables" %}
{% api-method-summary %}
Return the available agents
{% endapi-method-summary %}

{% api-method-description %}

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
      "id":"5aaa99024c3b110014b478f0",
      "firstname":"Andrea"
   },
   {
      "id":"5de9200d6722370017731969",
      "firstname":"Nuovopre"
   }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.tiledesk.com" path="/v1/projects/:project\_id/isopen" %}
{% api-method-summary %}
Return if the project is open regarding operating hours
{% endapi-method-summary %}

{% api-method-description %}

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
   {"isopen":false}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

