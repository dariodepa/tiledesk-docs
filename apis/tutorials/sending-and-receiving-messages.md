# Sending and receiving messages

## Targets

This tutorial aims to send and receive support messages between end users and agents using Tiledesk REST APIs and Webhooks.

### Steps

1. Signup on Tiledesk
2. Anonymous end user authentication through APIs
3. Send message to a conversation 
4. Receiving messages notification using Webhooks

## Signup on Tiledesk

For this tutorial you must signup on our beta environment available on [https://support-pre.tiledesk.com/dashboard](https://support-pre.tiledesk.com/dashboard)

![](../../.gitbook/assets/image%20%2810%29.png)

After signup please follow the wizard to create your first Tiledesk project.

![](../../.gitbook/assets/image%20%2816%29.png)

Get your **PROJECT\_ID** under Project Settings menu, we will use this later.

![](../../.gitbook/assets/image%20%288%29.png)

## Anonymous end-user authentication through APIs

We will authenticate the end user through anonymous authentication. Described [here](../api/authentication.md#anonymous-authentication-for-a-user).

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

## Send message to a conversation 

You can send a message using the [Send Message API](../api/messages.md#send-a-message).

To send a message you need to choose a **unique request identifier** \(your conversation\) like the following:

**support-group-&lt;UUID&gt;**

Please consider that the first message also creates the request conversation if it doesn't exist.

```bash
curl -v -X POST -H 'Content-Type:application/json' \
 -H "Authorization: JWT eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.XYZ...." \
 -d '{"text":"hello from anonym user"}' \
 https://tiledesk-server-pre.herokuapp.com/<PROJECT_ID>/requests/support-group-<UUID>/messages
```

For example:

```bash
curl -v -X POST -H 'Content-Type:application/json' \
 -H "Authorization: JWT eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.XYZ...." \
 -d '{"text":"hello my name is John and I need help"}' \
 https://tiledesk-server-pre.herokuapp.com/5e2c35c8f0dbc10017bb3aac/requests/support-group-27df7cbf-3946-4ca4-9b17-dc16114108f8/messages
```

Now you can see your first conversation in the Requests panel.

![](../../.gitbook/assets/image%20%2822%29.png)

The agent can see the same conversation in the agent chat.

![](../../.gitbook/assets/image%20%2837%29.png)

## Receiving messages notification using Webhooks

You can subscribe to the messages events using [Webhook](../webhook/). To do it you must first [create a subscription](../webhook/subscriptions.md#create-a-new-subscription) to an [event](../webhook/#webhook-events). In this case we will subscribe to message creation: 

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



















