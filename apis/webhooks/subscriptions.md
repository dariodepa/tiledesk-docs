# Subscriptions

{% api-method method="post" host="https://api.tiledesk.com" path="/v2/:project\_id/subscriptions" %}
{% api-method-summary %}
Create a new subscription
{% endapi-method-summary %}

{% api-method-description %}
Allows to add more subscriptions.
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
{% api-method-parameter name="event" type="string" required=true %}
the event method
{% endapi-method-parameter %}

{% api-method-parameter name="target" type="string" required=true %}
the target url
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
   {
   "__v":0,
   "updatedAt":"2019-03-12T12:01:56.462Z",
   "createdAt":"2019-03-12T12:01:56.462Z",
   "target":"https://webhook.site/c312005b-5042-49e9-a769-0f3ba4245b51",
   "event":"request.create",
   "id_project":"5b55e806c93dde00143163dd",
   "createdBy":"5ab11c6b83dc240014d46095",
   "_id":"5c879fb4f1ae6600173b8c75",
   "secret":"56c189c8-33ae-4930-bd98-410a12aa45ce"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example

```text
curl -v -X POST -H 'Content-Type:application/json' -u andrea.leo@f21.it:123456 -d '{"event":"request.create", "target":"https://webhook.site/c312005b-5042-49e9-a769-0f3ba4245b51"}' https://api.tiledesk.com/v2/5b55e806c93dde00143163dd/subscriptions
```

{% api-method method="get" host="https://api.tiledesk.com" path="/v2/:project\_id/subscriptions" %}
{% api-method-summary %}
Get all subscriptions
{% endapi-method-summary %}

{% api-method-description %}
Allows an account to list all active subscriptions.
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
   {
   "__v":0,
   "updatedAt":"2019-03-12T12:01:56.462Z",
   "createdAt":"2019-03-12T12:01:56.462Z",
   "target":"https://webhook.site/c312005b-5042-49e9-a769-0f3ba4245b51",
   "event":"request.create",
   "id_project":"5b55e806c93dde00143163dd",
   "createdBy":"5ab11c6b83dc240014d46095",
   "_id":"5c879fb4f1ae6600173b8c75"
},
...
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.tiledesk.com" path="/v2/:project\_id/subscriptions/:id" %}
{% api-method-summary %}
Get a subscription by id
{% endapi-method-summary %}

{% api-method-description %}
Fetches a subscription by his or her ID
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
the subscription identifier
{% endapi-method-parameter %}

{% api-method-parameter name="project\_id" type="string" required=true %}
The project\_id is a unique code assigned to your project when you create it in Tiledesk
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
   {
   "__v":0,
   "updatedAt":"2019-03-12T12:01:56.462Z",
   "createdAt":"2019-03-12T12:01:56.462Z",
   "target":"https://webhook.site/c312005b-5042-49e9-a769-0f3ba4245b51",
   "event":"request.create",
   "id_project":"5b55e806c93dde00143163dd",
   "createdBy":"5ab11c6b83dc240014d46095",
   "_id":"5c879fb4f1ae6600173b8c75"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="delete" host="https://api.tiledesk.com" path="/v2/:project\_id/subscriptions/:id" %}
{% api-method-summary %}
Delete a subscription by id
{% endapi-method-summary %}

{% api-method-description %}
Delete a subscription by his or her ID
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
the subscription identifier
{% endapi-method-parameter %}

{% api-method-parameter name="project\_id" type="string" required=true %}
The project\_id is a unique code assigned to your project when you create it in Tiledesk
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

{% api-method method="get" host="https://api.tiledesk.com/v2" path="/:project\_id/subscriptions/history" %}
{% api-method-summary %}
Get the subscriptions history
{% endapi-method-summary %}

{% api-method-description %}
Receive subscription call history.  
**Experimental. Only works for Tiledesk v2 environment \(on-premises only\).**
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
{% api-method-parameter name="page" type="number" required=false %}
what page of results to fetch. default to first page.
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
      "_id":"5e3ae8309ae7ee0017d91609",
      "event":"message.create",
      "target":"https://tiledesk.requestcatcher.com/test",
      "response":"{\"statusCode\":200,\"body\":\"request caught\",\"headers\":{\"date\":\"Wed, 05 Feb 2020 16:07:11 GMT\",\"content-length\":\"14\",\"content-type\":\"text/plain; charset=utf-8\",\"connection\":\"close\"},\"request\":{\"uri\":{\"protocol\":\"https:\",\"slashes\":true,\"auth\":null,\"host\":\"tiledesk.requestcatcher.com\",\"port\":443,\"hostname\":\"tiledesk.requestcatcher.com\",\"hash\":null,\"search\":null,\"query\":null,\"pathname\":\"/test\",\"path\":\"/test\",\"href\":\"https://tiledesk.requestcatcher.com/test\"},\"method\":\"POST\",\"headers\":{\"Content-Type\":\"application/json\",\"x-hook-secret\":\"0060287d-9486-4f00-a4db-a254f998dbd1\",\"accept\":\"application/json\",\"content-length\":6005}}}",
      "body":"\"request caught\"",
      "err":null,
      "id_project":"5e37f45c4d82de00178b96ad",
      "createdAt":"2020-02-05T16:07:12.089Z",
      "updatedAt":"2020-02-05T16:07:12.089Z",
      "__v":0
    }
    .....
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

