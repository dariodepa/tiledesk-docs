# Activities

You can use the API to get the activity data.

{% api-method method="get" host="https://api.tiledesk.com" path="/v2/:project\_id/activities" %}
{% api-method-summary %}
Get all activities
{% endapi-method-summary %}

{% api-method-description %}
Allows an admin to list all the activities for the project.
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
{% api-method-parameter name="agent\_id" type="string" required=false %}
The agent identifier.
{% endapi-method-parameter %}

{% api-method-parameter name="activities" type="string" required=false %}
A comma separeted list of events to filter the results. Ex: "PROJECT\_USER\_DELETE,PROJECT\_USER\_INVITE"
{% endapi-method-parameter %}

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
   "perPage":40,
   "count":1,
   "activities":[
      {
         "_id":"5cbf2eec5bf27612afc0c309",
         "updatedAt":"2019-04-23T15:27:40.619Z",
         "createdAt":"2019-04-23T15:27:40.619Z",
         "actor":{
            "type":"user",
            "id":"5ac7521787f6b50014e0b592",
            "name":"Nico Lanzilotto"
         },
         "verb":"PROJECT_USER_INVITE",
         "actionObj":{
            "email":"tizio@asd.it",
            "role":"agent",
            "id_project":"5ad5bd52c975820014ba900a",
            "project_name":"Tiledesk"
         },
         "target":{
            "type":"pendinginvitation",
            "id":"5cbf2eec5bf27612afc0c308",
            "object":{
               "_id":"5cbf2eec5bf27612afc0c308",
               "createdBy":"5ac7521787f6b50014e0b592",
               "id_project":"5ad5bd52c975820014ba900a",
               "role":"agent",
               "email":"tizio@asd.it",
               "createdAt":"2019-04-23T15:27:40.519Z",
               "updatedAt":"2019-04-23T15:27:40.519Z",
               "__v":0
            }
         },
         "id_project":"5ad5bd52c975820014ba900a",
         "__v":0
      }
   ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

