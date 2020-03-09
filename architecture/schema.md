# Architecture overview

## Modules overview

![](../.gitbook/assets/tiledesk-architecture-design.001.jpeg)

[Chat21](http://www.chat21.org) is a messaging engine with a multi platform SDKs:  native iOS and Android mobile SDKs and Web SDKs.  

Widget, Web Chat and Native mobile apps are Chat21 modules. Chat21 relies on Google [Firebase](http://firebase.google.com/) as the backend database. 

Chat21 communicates with Tiledesk through webhooks. When a Chat21 event occurs - a new message arrives, a new member join a group, etc - a new Event is created and notified to Tiledesk Server. Chat21 then makes an HTTP POST request to send the Event to the Tiledesk webhook [endpoint](https://github.com/Tiledesk/tiledesk-server/blob/master/channels/chat21/chat21WebHook.js) .

## Components overview

![](../.gitbook/assets/image%20%2856%29.png)

