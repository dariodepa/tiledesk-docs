# Messages

You can use the API to get the message information.

{% api-method method="get" host="https://api.tiledesk.com" path="/v1/:project\_id/requests/:id/messages" %}
{% api-method-summary %}
Get the messages of a request by id
{% endapi-method-summary %}

{% api-method-description %}
Fetches the messages by his or her request\_id
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
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
[
   {
      "_id":"5c81593adf767b0017d1aa68",
      "updatedAt":"2019-03-07T17:47:38.411Z",
      "createdAt":"2019-03-07T17:47:38.411Z",
      "sender":"SRbb2PfbSFcgICv9VQBcURZeloh1",
      "senderFullname":"Guest",
      "recipient":"support-group-L_OG76RYhR0XFiMf2PK",
      "text":"test56",
      "id_project":"5b55e806c93dde00143163dd",
      "createdBy":"SRbb2PfbSFcgICv9VQBcURZeloh1",
      "__v":0,
      "status":200
   },
   {
      "_id":"5c81593adf767b0017d1aa69",
      "updatedAt":"2019-03-07T17:47:38.625Z",
      "createdAt":"2019-03-07T17:47:38.625Z",
      "sender":"system",
      "senderFullname":"Bot",
      "recipient":"support-group-L_OG76RYhR0XFiMf2PK",
      "text":"La stiamo mettendo in contatto con un operatore. Attenda...",
      "id_project":"5b55e806c93dde00143163dd",
      "createdBy":"system",
      "__v":0,
      "status":200
   },
  ...
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example:

```text
curl -v -X GET -u andrea.leo@f21.it:123456 https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/requests/support-group-L_OG76RYhR0XFiMf2PK/messages
```



{% api-method method="get" host="https://api.tiledesk.com" path="/v1/:project\_id/requests/:id/messages/:message_id" %}
{% api-method-summary %}
Get the message by request id and message id
{% endapi-method-summary %}

{% api-method-description %}
Fetche the message by his or her id
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
the request identifier
{% endapi-method-parameter %}

{% api-method-parameter name="message_id" type="string" required=true %}
the message identifier
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
      "_id":"5c81593adf767b0017d1aa68",
      "updatedAt":"2019-03-07T17:47:38.411Z",
      "createdAt":"2019-03-07T17:47:38.411Z",
      "sender":"SRbb2PfbSFcgICv9VQBcURZeloh1",
      "senderFullname":"Guest",
      "recipient":"support-group-L_OG76RYhR0XFiMf2PK",
      "text":"test56",
      "id_project":"5b55e806c93dde00143163dd",
      "createdBy":"SRbb2PfbSFcgICv9VQBcURZeloh1",
      "__v":0,
      "status":200
   }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example:

```text
curl -v -X GET -u andrea.leo@f21.it:123456 https://api.tiledesk.com/v1/5b55e806c93dde00143163dd/requests/support-group-L_OG76RYhR0XFiMf2PK/messages/5c81593adf767b0017d1aa68
```

