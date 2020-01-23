# Projects

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

