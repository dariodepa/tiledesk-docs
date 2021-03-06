# Introduction

The Realtime  API provides programmatic access to ongoing activity in your Tiledesk server.

The Realtime API is available on Enterprise plan.

You can use the API to do the following:

* Display requests data
* Display agents data
* Create and display a real-time dashboard
* Predict or estimate capacity and other derived metrics

The Realtime API allows you to receive events from Tiledesk after you subscribe to one or more topics.

This API is an SSL-only API. You must be a verified user to make API requests. You can authorize against the API using JWT token. 


## Topics

| Topic | Description |
| :--- | :--- |
| /PROJECT_ID/requests | Get the last open requests of a project  |
| /PROJECT_ID/requests/REQUEST_ID | Get the requests detail  |
| /PROJECT_ID/requests/REQUEST_ID/messages | Get the request messages  |
| /PROJECT_ID/project_users/USER_ID | Get the agents info  |

## Rate Limiting
We only allow a certain number of new connections per minute. The number of new connections to the Realtime API is restricted by REST API rate limits. We also allow a certain number of concurrently running connections to the Realtime API.

We reserve the right to adjust the rate limit for given endpoints in order to provide a high quality of service for all clients. If the rate limit is exceeded, Tiledesk will respond with a body that details the reason for the rate limiter kicking in.

We also limit the total amount of data exchanged through real time APIs. For example the number of Realtime requests exchanged can’t exceed a certain number of items. If this number is exeeded you can always use REST APIs to get additional data or to make more complex queries.

## Using The API
* Establish an authenticated WebSocket connection to `wss://rtm.tiledesk.com/v2/ws/`.
* Subscribe to one or several topics.
* Process incoming events.
* Unsubscribe to topics.

## Allowed For
* Owner
* Administrator
* Agent

## Establish Connection
Connect to the wss://rtm.tiledesk.com/v2/ws/ WebSocket endpoint using your JWT token.

```
  var ws = new WebSocket("wss://rtm.tiledesk.com/v2/ws/?token=YOUR_JWT_TOKEN"); 
  
  ws.onopen = function () {
      console.log('websocket is connected.');         
  }
  
  ws.onclose = function () {
      console.log('websocket is closed.');           
  }
  
  ws.onerror = function () {
      console.log('websocket error ...')
  }               
```
## Subscribe to a topic
Once connection is established, you can send messages to subscribe to individual topics. Refer to Topics for the topic key.

```
{
   "action":"subscribe",
   "payload":{
      "topic":"/<YOUR_PROJECT_ID_HERE>/requests"
   }
}
```

To subscribe to a topic you can execute :
```
ws.send(subscriptionMessage);
 ```
 
Example:

```
var subscriptionMessage =
{
   "action":"subscribe",
   "payload":{
      "topic":"/5df26badde7e1c001743b63c/requests"
   }
}

ws.send(subscriptionMessage);
```

## Process Incoming Events
Once you have subscribed to one or several topics, listen to subsequent messages to start collecting data.
```
 ws.onmessage = function(message) {   
    console.log(message);
    try {
         var data = JSON.parse(message.data);
    } catch (e) {
       return console.log('This doesn\'t look like a valid JSON: ', message.data);
    }

   //.... ADD YOUR LOGIC HERE    
}
```

The following are sample messages received after subscribing to requests topic:
```
{
   "action":"publish",
   "payload":{
      "topic":"/5eb45fbc1f9e1f0012d62207/requests",
      "method":"CREATE",
      "message":[
         {
            "_id":"5eb4fc911f9e1f0012d62248",
            "status":200,
            "preflight":false,
            "participants":[
               "5eb45fb21f9e1f0012d62201"
            ],
            "request_id":"support-group-1a952f2f-c09a-46be-bc75-11387a95d55f",
            "requester":"5eb45fbc1f9e1f0012d62208",
            "lead":{
               ...
            },
            "first_text":"hello world",
            "department":"5eb45fbc1f9e1f0012d62209",
            ...
            "assigned_at":"2020-05-08T06:30:41.090Z",
            "id_project":"5eb45fbc1f9e1f0012d62207",
            "createdBy":"5eb45fb21f9e1f0012d62201",
            "tags":[

            ],
            "notes":[

            ],
            "channel":{
               "name":"chat21"
            },
            "createdAt":"2020-05-08T06:30:41.094Z",
            "updatedAt":"2020-05-08T06:31:00.367Z",
            "__v":0,
            "first_response_at":"2020-05-08T06:30:58.109Z",
            "waiting_time":17015,
            "id":"5eb4fc911f9e1f0012d62248",
            ....
         },
         ..
      ]
   }
}
```

## Unsubscribe
Once you stop processing some data, you can individually unsubscribe from a topic. Events will then stop being pushed on the connection.
```
{
   "action":"unsubscribe",
   "payload":{
      "topic":"/<YOUR_PROJECT_ID_HERE>/requests"
   }
}
```
