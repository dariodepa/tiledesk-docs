---
description: >-
  Dialogflow external chatbot with automatic human handoff using fallback intent
---

# Dialogflow  Tutorial 3 - Automatic human handoff with fallback intent

We'll start from [Dialogflow Tutorial 1](apis/tutorials/dialogflow-as-external-chatbot-integration), just adding a small library to our original endpoint.

## Fork the tutorial code

You must use the code in *Tutorial 1*. The code is available on Github [here](https://github.com/Tiledesk/tiledesk-dialogflow-proxy-tutorial).

**Fork the tutorial** code using the Fork button. Now you have a copy of the tutorial on your own repo.

## Introduction

This time we'll give a try to the second endpoint already embedded into our _nodejs_ app:

```javascript
// Tutorial 3 - Automatic human handhoff based on fallback intent
var consecutive_fallback_count = {};
const MAX_FALLBACKS = 4;
app.post("/bot-fallback-handoff/:botid", (req, res) => {
  const tdclient = new TiledeskChatbotClient({request: req});
  console.log("tdclient", tdclient)
  const botid = req.params.botid;
  const supportRequest = tdclient.supportRequest
  // immediately reply back
  res.status(200).send({"success":true});
  // reply messages are sent asynchronously
  const dialogflow_session_id = supportRequest.request_id
  const lang = 'en-EN' // lang must be the same of the Dialogflow Agent
  const credentials = JSON.parse(process.env[botid])
  runDialogflowQuery(tdclient.text, dialogflow_session_id, lang, credentials)
  .then(function(result) {
    if (result.intent.isFallback) {
      if (!consecutive_fallback_count[dialogflow_session_id]) {
        consecutive_fallback_count[dialogflow_session_id] = 1
      }
      else {
        consecutive_fallback_count[dialogflow_session_id]++
        console.log("fallback of", dialogflow_session_id, "is", consecutive_fallback_count[dialogflow_session_id])
      }
    }
    if(res.statusCode === 200) {
      let msgs = [];
      if (consecutive_fallback_count[dialogflow_session_id] == MAX_FALLBACKS) {
        consecutive_fallback_count[dialogflow_session_id] = 0
        msgs.push({
          "text": "We are putting you in touch with an operator..."
        })
        msgs.push({
          "text": "\\agent",
          "attributes" : {subtype: "info"} // this message is hidden in the widget
        }) 
      }
      else {
        msgs.push({
          "text": result['fulfillmentText']
        })
      }
      msgs.forEach( m => {
        tdclient.sendMessage(m, function (err) {
          console.log("Message", m.text, "sent.");
        })
      })
    }
  })
  .catch(function(err) {
    console.log('Error: ', err);
  })
})
```

As in [Dialogflow Tutorial 1](apis/tutorials/dialogflow-as-external-chatbot-integration) you have to create a Dialogflow agent, train the same Agent following the instructions in this tutorial, then go to Tiledesk and create an external bot and connect it to Routing (or to a Department).

## How this code works

As you can see this new end point starts with thse two lines of code

```javascript
// Tutorial 3 - Automatic human handhoff based on fallback intent
var consecutive_fallback_count = {};
const MAX_FALLBACKS = 4;
```

The first variable *consecutive_fallback_count* saves the current number of fallbacks for every conversation.
The second variable *MAX_FALLBACKS* represents the maximum number of consecutive fallbacks in a conversation.

In this tutorial, every time there is a fallback the number of consecutive fallbacks for the same conversation in incrememnted by one unit.

As soon as the total number of consecutive fallbacks reaches *MAX_FALLBACKS* a couple of messages is sent back to the client.
The first message is shown to the client and is a custom message that you can send to indicate that the conversation is switching to humans.
The second message *\agent* is intercepted by Tiledesk and drives the system to remove the bot and invite an agent to the conversation, following the Department rules.

```javascript
msgs.push({
  "text": "We are putting you in touch with an operator..."
})
msgs.push({
  "text": "\\agent",
  "attributes" : {subtype: "info"} // this message is hidden in the widget
})
```

To hide a message simply add a sub-property *subtype: 'info'* to the *attributes* property of a message.

Enjoy Tiledesk!

Do you have feedback on this article? Please send us your feedback writing an email to info@tiledesk.com
