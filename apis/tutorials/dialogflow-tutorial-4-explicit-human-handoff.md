---
description: >-
  Dialogflow external chatbot with explicit human handoff using a Dialogflow intent
---

# Dialogflow  Tutorial 4 - Explicit Human handoff with user intent

## Introduction

In the previuos tutorial we learned how to automatically switch to a human agent based on the number of consecutive fallbacks during a conversation.

What if you want the user to explicitly choose to switch to a human during a conversation?

In this case the simplest thing that you need to do is starting from any of the above tutorials, adding a specific intent to Dialogflow that will switch to a human agent.

## Train the 'talk to agent' intent

Open your Agent's Dialogflow console. Add a new intent. Let's call this intent 'talk to agent'.
We'll train this intent with a single phrase (more phrases can be added as a convenience).

![](https://user-images.githubusercontent.com/32564846/79357733-b3d5f700-7f40-11ea-89f2-a093329fd273.png)

Now the event will reply with:

'I'm putting you in touch with an operator' \agent

![](https://user-images.githubusercontent.com/32564846/79358037-07e0db80-7f41-11ea-8d3b-ea4064ea2edf.png)

As soon as this phrase reaches Tiledesk, it automatically removes the chatbot and adds a human operator - following the rules you already set up in the Routing section or in the specific department.

You can also place a button under every DF reply (i.e. using micro languge) to allow the user to ask for an agent after each reply.

![](https://user-images.githubusercontent.com/32564846/79378880-5baded80-7f5e-11ea-8bed-296904a6b986.png)

## Gracefully handling operating hours in bot-humans handoff

What happens if, while you switch to the human operator, your support team is outside of operating hours? The request will be placed in the unserved queue and will became served as soon as your team became available again. Meanwhile you should notice to the user that the request will be taken in some hours, or probably the day after. So, telling "I'm putting you in touch with an operator" is not enough.

How can you write an _handoff_ message that depends by operating hours? You can mix Dialogflow messages _fulfillment_ and Tiledesk APIs to reach your goal.

## Enable Agent fulfillment

Open Dialogflow dashboard on your agent, the in the menu fulfillment option enable "Webhook" option. In the URL field insert your heroku app url where you pubblished your app followed by _/dfwebhook_ and your project_id:

![](https://user-images.githubusercontent.com/32564846/79381311-14c1f700-7f62-11ea-84ca-f0ccbea925d5.png)

This "webhook" endpoint is already provided in the script.

```javascript
// Tutorial 4.1 - Webhook for Bot-Agent handoff message based on opening hours
app.post('/dfwebhook/:project_id', (req, res) => {
  // console.log("req.body: " , req.body)
  const fulfillmentText = req.body.queryResult.fulfillmentText
  console.log("fulfillmentText:", fulfillmentText)
  const languageCode = req.body.queryResult.languageCode
  console.log("languageCode:", languageCode)
  // replace the following with your prject id
  const project_id = req.params.project_id
  const intent = req.body.queryResult.intent.displayName.toUpperCase()
  if (intent === "TALK TO AGENT") {
    // for cloud apis initialize like the this:
    // const tdclient = new TiledeskClient()
    // for on premises installations specify your endpoint like this:
    const tdclient = new TiledeskClient({APIURL: 'https://tiledesk-server-pre.herokuapp.com'})
    tdclient.anonymauth(project_id, function(token) {
      tdclient.openNow(project_id, token, function(isopen) {
        var df_res = {}
        if (isopen) {
          df_res['fulfillmentText'] = "We are open! Switching to agent\\agent"
        }
        else {
          df_res['fulfillmentText'] = "I'm sorry but we are closed right now."
        }
        res.status(200).send(JSON.stringify(df_res));
      })
    })
  }
});
```

This endpoint uses a projeect_id int the webhook URL that you must have care to replace with your own.

## Re-train the 'talk to agent' intent to use fulfillment

Fulfillment is not automatically actvive on the intents. You must activate it for each intent that you want to reply dynamically.
We will re-train the 'talk to agent' intent to use our webhook to reply, instead of the static response.

Switch to the intent UI from Dialogflow dashboard, the go on the form bottom and switch to "on" the fulfillment button, as in the following picture:

![](https://user-images.githubusercontent.com/32564846/79383410-6a4bd300-7f65-11ea-96ac-a94670dd5c79.png)

Now go on your project in Tiledesk dashboard and activate operating hours, taking care to put offline the interval when you ask the bot to switch to human agents. If you will try to switch to human operators during offline hours you will get the following message:

![](https://user-images.githubusercontent.com/32564846/79382698-3ae89680-7f64-11ea-87b6-176205b8ecff.png)

Do you have feedback on this article? Please send us your feedback writing an email to info@tiledesk.com

Enjoy Tiledesk!

