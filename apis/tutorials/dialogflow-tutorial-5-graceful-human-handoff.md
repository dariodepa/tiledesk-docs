---
description: >-
  Dialogflow  Tutorial 4 - Gracefully handling operating hours in bot-humans handoff
---

# Dialogflow  Tutorial 4 - Gracefully handling operating hours in bot-humans handoff

## Introduction

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

This endpoint uses a *projeect_id* in the webhook URL that you must have care to replace with your own.

## Re-train the 'talk to agent' intent to use fulfillment

Fulfillment is not automatically actvive on the intents. You must activate it for each intent that you want to reply dynamically.
We will re-train the 'talk to agent' intent to use our webhook to reply, instead of the static response.

Switch to the intent UI from Dialogflow dashboard, the go on the form bottom and switch to "on" the fulfillment button, as in the following picture:

![](https://user-images.githubusercontent.com/32564846/79383410-6a4bd300-7f65-11ea-96ac-a94670dd5c79.png)

Now go on your project in Tiledesk dashboard and activate operating hours, taking care to put offline the interval when you ask the bot to switch to human agents. If you will try to switch to human operators during offline hours you will get the following message:

![](https://user-images.githubusercontent.com/32564846/79382698-3ae89680-7f64-11ea-87b6-176205b8ecff.png)

Do you have feedback on this article? Please send us your feedback writing an email to info@tiledesk.com

Enjoy Tiledesk!