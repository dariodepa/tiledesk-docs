# Messages

You can use the API to get the message information.


The Model 

| Key | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the message which is given by Tiledesk. |
| sender | String | A unique identifier of the sender. It can be: the user identifier, a bot identifier or the system user |
| senderFullname | String | The sender fullname. It can be: the user fullname, the bot name o an alias |
| recipient | String | A unique identifier of the recipient. It can be: the request_id field (external id) of the request |
| status | Number | The message status: FAILED : -100, SENDING : 0, SENT : 100, DELIVERED : 150, RECEIVED : 200, RETURN_RECEIPT: 250, SEEN : 300 |
| text | String | The message text. |
| type | String | The message type. Accepted values: text (default), image |
| metadata | Object | The message metadata. |
| attributes | Object | The custom attributes which are set for the message. |
| createdAt | String | The time (ISO-8601 date string) when the message was created. |
| updatedAt | String |  The time (ISO-8601 date string) when the message was updated.  |
| createdBy | String | The unique identifier of the row creator |
| id_project | String | The unique identifier of the project |
      
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

{% api-method method="get" host="https://api.tiledesk.com" path="/v1/:project\_id/requests/:id/messages/:message\_id" %}
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

{% api-method-parameter name="message\_id" type="string" required=true %}
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

{% api-method method="post" host="YOUR\_TILEDESK\_DOMAIN" path="/:project\_id/requests/:id/messages" %}
{% api-method-summary %}
Send a message.
{% endapi-method-summary %}

{% api-method-description %}
Allows to send a message.   
**Only works for Tiledesk v2 environment \(on-premises only\).**
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="project\_id" type="string" required=true %}
The project\_id is a unique code assigned to your project when you create it in Tiledesk
{% endapi-method-parameter %}

{% api-method-parameter name="request\_id" type="string" required=true %}
The request identifier. Must follow this pattern 'support-group-UUID'
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
{% api-method-parameter name="text" type="string" required=true %}
the message text
{% endapi-method-parameter %}

{% api-method-parameter name="departmentid" type="string" required=false %}
The selected department identifier. Accepted only on the first message.
{% endapi-method-parameter %}

{% api-method-parameter name="sourcePage" type="string" required=false %}
The source page of the request. Accepted only on the first message.
{% endapi-method-parameter %}

{% api-method-parameter name="language" type="string" required=false %}
The language of the request. Accepted only on the first message.
{% endapi-method-parameter %}

{% api-method-parameter name="userAgent" type="string" required=false %}
The userAgent string of the request. Accepted only on the first message.
{% endapi-method-parameter %}

{% api-method-parameter name="attributes" type="object" required=false %}
it's the message custom attributes. Example: attributes = {"custom\_attribute1": "value1"}.
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=false %}
it's the message type. "text" value for textual message and "image" for sending image message\(you must set metadata field\). Available values: text \(default\) and image.
{% endapi-method-parameter %}

{% api-method-parameter name="metadata" type="object" required=false %}
it's the image properties: src is the absolute source path of the image, width is the image width, height is the image height. Example: metadata = { "src": "https://www.tiledesk.com/wp-content/uploads/2018/03/tiledesk-logo.png", "width": 200, "height": 200 }
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
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
      "text":"hello from api",
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
curl -v -X POST -H 'Content-Type: application/json' -u andrea.leo@f21.it:123456  -d '{"text":"hello from api"}' https://YOUR_TILEDESK_DOMAIN/5b55e806c93dde00143163dd/requests/support-group-1234/messages
```

