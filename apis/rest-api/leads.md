# Leads

You can use the API to get or set lead information.

The Model

Our Lead API is a central place to gather all information and take actions on your contacts \(leads\), such as fetching, searching, creating, updating, and deleting.

| Key | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the lead which is given by Tiledesk. |
| lead\_id | String | A unique identifier for the lead which is given to Tiledesk.It's an external id |
| fullname | String | The lead name and surname. |
| attributes | Object | The custom attributes which are set for the lead. |
| createdAt | String | The time \(ISO-8601 date string\) when the lead was created. |
| updatedAt | String | The time \(ISO-8601 date string\) when the lead was updated. |
| createdBy | String | The unique identifier of the row creator |
| id\_project | String | The unique identifier of the project |

{% api-method method="get" host="https://api.tiledesk.com" path="/v2/:project\_id/leads" %}
{% api-method-summary %}
Get all leads
{% endapi-method-summary %}

{% api-method-description %}
Allows an account to list all the leads.
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

{% api-method-parameter name="email" type="string" required=false %}
search a lead by the email address
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
{
   "perPage":40,
   "count":179,
   "leads":[
      {
         "_id":"5c81593adf767b0017d1aa66",
         "updatedAt":"2019-03-07T17:47:38.393Z",
         "createdAt":"2019-03-07T17:47:38.393Z",
         "lead_id":"SRbb2PfbSFcgICv9VQBcURZeloh1",
         "fullname":"Guest",
         "attributes":{
         ...
         },
         "id_project":"5b55e806c93dde00143163dd",
         "createdBy":"system",
         "__v":0
      },
      {
         "_id":"5c81565edf767b0017d1aa35",
         "updatedAt":"2019-03-07T17:35:26.132Z",
         "createdAt":"2019-03-07T17:35:26.132Z",
         "lead_id":"WTteQpKpGZN1aElfFYCP9YPaaLN2",
         "fullname":"Guest",
         "attributes":{
          ...
         },
         "id_project":"5b55e806c93dde00143163dd",
         "createdBy":"system",
         "__v":0
      },
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
curl -v -X GET -H 'Content-Type: application/json' -u andrea.leo@f21.it:123456 https://api.tiledesk.com/v2/5b55e806c93dde00143163dd/leads
```

{% api-method method="get" host="https://api.tiledesk.com" path="/v2/:project\_id/leads/:id" %}
{% api-method-summary %}
Get a lead by id
{% endapi-method-summary %}

{% api-method-description %}
Fetches a lead by his or her Lead ID
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
the lead identifier
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
         "_id":"5c81593adf767b0017d1aa66",
         "updatedAt":"2019-03-07T17:47:38.393Z",
         "createdAt":"2019-03-07T17:47:38.393Z",
         "lead_id":"SRbb2PfbSFcgICv9VQBcURZeloh1",
         "fullname":"Guest",
         "attributes":{ ... },
         "id_project":"5b55e806c93dde00143163dd",
         "createdBy":"system",
         "__v":0
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example

```text
curl -v -X GET -H 'Content-Type: application/json' -u andrea.leo@f21.it:123456 https://api.tiledesk.com/v2/5b55e806c93dde00143163dd/leads/5c81593adf767b0017d1aa66
```

{% api-method method="post" host="https://api.tiledesk.com" path="/v2/:project\_id/leads" %}
{% api-method-summary %}
Create a new lead
{% endapi-method-summary %}

{% api-method-description %}
Allows to add more leads.
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
{% api-method-parameter name="email" type="string" required=false %}
the lead email address
{% endapi-method-parameter %}

{% api-method-parameter name="lead\_id" type="string" required=true %}
the external id of the lead
{% endapi-method-parameter %}

{% api-method-parameter name="fullname" type="string" required=false %}
The lead fullname
{% endapi-method-parameter %}

{% api-method-parameter name="attributes" type="object" required=false %}
The lead custom attributes
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{  
         "_id":"5c81593adf767b0017d1aa66",
         "updatedAt":"2019-03-07T17:47:38.393Z",
         "createdAt":"2019-03-07T17:47:38.393Z",
         "lead_id":"SRbb2PfbSFcgICv9VQBcURZeloh1",
         "fullname":"Guest",
         "attributes":{ ... },
         "id_project":"5b55e806c93dde00143163dd",
         "createdBy":"system",
         "__v":0
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example:

```text
curl -v -X POST -H 'Content-Type: application/json' -u andrea.leo@f21.it:123456  -d '{"fullanem":"andrea", "lead_id":"123456"}' https://api.tiledesk.com/v2/5b55e806c93dde00143163dd/leads
```

{% api-method method="put" host="https://api.tiledesk.com" path="/v2/:project\_id/leads/:id" %}
{% api-method-summary %}
Update a lead by id
{% endapi-method-summary %}

{% api-method-description %}
Allows to update a lead.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="project\_id" type="string" required=true %}
The project\_id is a unique code assigned to your project when you create it in Tiledesk
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
The id is the lead indentifier.
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
{% api-method-parameter name="email" type="string" required=false %}
the lead email address
{% endapi-method-parameter %}

{% api-method-parameter name="fullname" type="string" required=false %}
The lead fullname
{% endapi-method-parameter %}

{% api-method-parameter name="attributes" type="object" required=false %}
The lead custom attributes
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{  
         "_id":"5c81593adf767b0017d1aa66",
         "updatedAt":"2019-03-07T17:47:38.393Z",
         "createdAt":"2019-03-07T17:47:38.393Z",
         "lead_id":"SRbb2PfbSFcgICv9VQBcURZeloh1",
         "fullname":"Guest",
         "attributes":{ ... },
         "id_project":"5b55e806c93dde00143163dd",
         "createdBy":"system",
         "__v":0
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example:

```text
curl -v -X PUT -H 'Content-Type: application/json' -u andrea.leo@f21.it:123456  -d '{"fullanem":"andrea", "lead_id":"123456"}' https://api.tiledesk.com/v2/5b55e806c93dde00143163dd/leads/5c81593adf767b0017d1aa66
```

{% api-method method="delete" host="https://api.tiledesk.com" path="/v2/:project\_id/leads/:id" %}
{% api-method-summary %}
Delete a lead by id
{% endapi-method-summary %}

{% api-method-description %}
Allows to delete a lead.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="project\_id" type="string" required=true %}
The project\_id is a unique code assigned to your project when you create it in Tiledesk
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
The id is the lead indentifier.
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
         "_id":"5c81593adf767b0017d1aa66",
         "updatedAt":"2019-03-07T17:47:38.393Z",
         "createdAt":"2019-03-07T17:47:38.393Z",
         "lead_id":"SRbb2PfbSFcgICv9VQBcURZeloh1",
         "fullname":"Guest",
         "attributes":{ ... },
         "id_project":"5b55e806c93dde00143163dd",
         "createdBy":"system",
         "__v":0
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example:

```text
curl -v -X DELETE -H 'Content-Type: application/json' -u andrea.leo@f21.it:123456  https://api.tiledesk.com/v2/5b55e806c93dde00143163dd/leads/5c81593adf767b0017d1aa66
```

