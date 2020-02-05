# Sending and receiving messages with Tiledesk APIs

## Targets

This tutorial will help you to understand how to send and receive "support messages" between Tiledesk's _End Users_ and _Agents_ using Tiledesk REST APIs and Webhooks.

### Steps

1. Signup a user on Tiledesk
2. Anonymous end-user authentication through APIs
3. Sending messages to a conversation
4. Receiving new messages notifications using Webhooks

## Signup on Tiledesk

To use Tiledesk APIs is mandatory to signup a new user on our beta environment available on [https://support-pre.tiledesk.com/dashboard](https://support-pre.tiledesk.com/dashboard)

The previous APIs end-point will change as soon as the beta version will be released as **Tiledesk v2**. This tutorial will be updated accordingly.

![](../../.gitbook/assets/image%20%2818%29.png)

After signup please follow the proposed wizard to create your first Tiledesk project.

![](../../.gitbook/assets/image%20%2829%29.png)

Get the **PROJECT\_ID** of the created project under _Project Settings_ menu. We will use this later.

![](../../.gitbook/assets/image%20%2815%29.png)

## Anonymous end-user authentication through APIs

In this tutorial we will authenticate _end-users_ through anonymous authentication \(you can find more info on anomymous authentication [here](../api/authentication.md#anonymous-authentication-for-a-user)\).

All APIs in this tutorial will use the following endpoint:

```bash
https://tiledesk-server-pre.herokuapp.com
```

The previous APIs end-point will change as soon as the beta version will be released as **Tiledesk v2**. This tutorial will be updated accordingly.

```bash
curl -v -X POST -H 'Content-Type:application/json' \
-d '{"id_project":"5e2c35c8f0dbc10017bb3aac", "firstname":"John"}' \
https://tiledesk-server-pre.herokuapp.com/auth/signinAnonymously
```

This will reply with the JWT token that we'll use to send our first message:

```bash
{
   "success":true,
   "token":"JWT eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.XYZ....",
   "user":{
      "_id":"fc43a0e1-ba85-404e-9a44-bf0050330898",
      "firstname":"John",
      "id":"fc43a0e1-ba85-404e-9a44-bf0050330898",
      "fullName":"John"
   }
}
```

## Sending messages to a conversation

You can send a message using the [Send Message API](../api/messages.md#send-a-message).

To send a message you need to choose a _unique_ **request identifier.** A _request_  is an object containing the all the metadata describing the conversation between end-user and _support team_\).

The request identifier must follow the following pattern:

**support-group-&lt;UUID&gt;**

Please consider that the first message you send to a conversation also creates request and corresponding conversation if they do not exist.

```bash
curl -v -X POST -H 'Content-Type:application/json' \
 -H "Authorization: JWT eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.XYZ...." \
 -d '{"text":"hello from anonym user"}' \
 https://tiledesk-server-pre.herokuapp.com/<PROJECT_ID>/requests/support-group-<UUID>/messages
```

Example with realistic variables instances:

```bash
curl -v -X POST -H 'Content-Type:application/json' \
 -H "Authorization: JWT eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.XYZ...." \
 -d '{"text":"hello my name is John and I need help"}' \
 https://tiledesk-server-pre.herokuapp.com/5e2c35c8f0dbc10017bb3aac/requests/support-group-27df7cbf-3946-4ca4-9b17-dc16114108f8/messages
```

Looking at the dashboard of your project you will see your first conversation in the Requests panel. The requests are updated in real time, so you don't have to manunally update the Requests' page. If you left unchanged all the default settings, the request will be assigned to you \(make sure you are "available", looking in the lower right corner of your profile image in the left menu panel\).

![](../../.gitbook/assets/image%20%2844%29.png)

The agent \(you\) can now see the same conversation in the agent chat \(first option of the menu panel will open the desktop chat\).

![](../../.gitbook/assets/image%20%2878%29.png)

## Receiving new messages notifications using Webhooks

You can subscribe to the messages events sent to a conversation using [Webhook](../webhook/)s.

You must first [create a subscription](../webhook/subscriptions.md#create-a-new-subscription) to an [event](../webhook/#webhook-events) that points to a url on your server.

In this case we will subscribe to _message creation_ event on a custom url \(/test\) on requestcatcher.com, a free, beautiful service to debug your webhooks: 

```text
curl -v -X POST -H 'Content-Type:application/json' \
-u demo@email.com:123456 \
-d '{"event":"message.create", "target":"https://tiledesk.requestcatcher.com/test"}' \
https://tiledesk-server-pre.herokuapp.com/5e2c35c8f0dbc10017bb3aac/subscriptions
```

 The subscription endpoint returns:

```text
{
   "secret":"0fd2a8a1-a3e6-443b-9fe5-49b83612cd72",
   "_id":"5e2c6a24f5b11c00175f1705",
   "target":"https://tiledesk.requestcatcher.com/test",
   "event":"message.create",
   "id_project":"5e2c35c8f0dbc10017bb3aac",
   "createdBy":"5e2c357af0dbc10017bb3aa7",
   "createdAt":"2020-01-25T16:17:40.088Z",
   "updatedAt":"2020-01-25T16:17:40.088Z",
   "__v":0
}
```

Now you are notified for each messages sent to your Tiledesk project. Now, for example, if the agent sends a message to the end user, your webhook endpoint will be notified with the message payload.  

![](../../.gitbook/assets/image%20%2874%29.png)

This is the webhook notification with the message payload. You can use this notification to create a copy of all messages sent/received in your project, generate new custom events, communicate in real time on other channels etc.

```text
{
   "timestamp":1579969429552,
   "payload":{
      "type":"text",
      "status":200,
      "_id":"5e2c6b958c9612001716bede",
      "sender":"5e2c357af0dbc10017bb3aa7",
      "senderFullname":"demo demo",
      "recipient":"support-group-27df7cbf-3946-4ca4-9b17-dc16114108f10",
      "text":"Hi I'm Rosy. How can help you?",
      "id_project":"5e2c35c8f0dbc10017bb3aac",
      "createdBy":"5e2c357af0dbc10017bb3aa7",
      "metadata":"",
      "attributes":{
         "client":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/76.0.3809.132 Safari/537.36",
         "sourcePage":"https://support-pre.tiledesk.com/chat/index.html",
         "userEmail":"aaa22@aaa22.it",
         "userFullname":"aaa22 aaa22"
      },
      "createdAt":"2020-01-25T16:23:49.394Z",
      "updatedAt":"2020-01-25T16:23:49.394Z",
      "__v":0,
      "request":{
         ....
      }
   },
   "hook":{
      "_id":"5e2c6a24f5b11c00175f1705",
      "target":"https://tiledesk.requestcatcher.com/test",
      "event":"message.create",
      "id_project":"5e2c35c8f0dbc10017bb3aac",
      "createdBy":"5e2c357af0dbc10017bb3aa7",
      "createdAt":"2020-01-25T16:17:40.088Z",
      "updatedAt":"2020-01-25T16:17:40.088Z",
      "__v":0
   }
}
```

