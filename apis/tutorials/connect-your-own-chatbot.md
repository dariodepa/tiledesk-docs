---
description: Connect your own chatbots to Tiledesk
---

# Hello World tutorial for external chatbots integration

Tiledesk is designed to allow external chatbots to easy communicate with your Agents or End users. Once a chatbot receive an authentication token from Tiledesk he can easily call many APIs to modify the state of a Request \(the support conversation\) changing Departments, inviting Agents, sending scheduled messages, use the chatbot microlanguage to simplify interaction with buttons, images, messages' timing etc.

This tutorial will show you how to create a very basic chatbot integration, allowing you to reply to specific messages sent by the End user.

## Signup a user on Tiledesk

To use Tiledesk APIs or integrate your own chatbots is mandatory to signup a new user on our **beta** environment. It's available on the following link [https://support-pre.tiledesk.com/dashboard](https://support-pre.tiledesk.com/dashboard)

**The previous APIs end-point will change as soon as the beta version will be released as Tiledesk v2. This tutorial will be updated accordingly.**

After signup please follow the proposed wizard to create your first Tiledesk project \(you can jump the last step, relative to the widget installation\).

As soon as you create the project you will be redirected to the project home.

To integrate an external bot, we'll need a web endpoint where all the chatbot's requests will be forwarded. We'll use the well-known [Repl.it](https://repl.it) service to fast create our own web endpoint.

## Create and configure external chatbot endpoint

Go on the [repl.it](https://repl.it) and press "+ new repl" button. Then select NodeJS as the programming environment and choose a unique name of you repl propject. We use _tiledeskbot_, that obviously you can't use because it was already taken for this tutorial :\)

![](https://user-images.githubusercontent.com/32564846/78982123-b5a75100-7b21-11ea-82c6-c81a4f2b6035.png)

Now push on the **examples** link in the generated code. A popup like the following will open. Choose the "Server \(Express\)" option.

![](https://user-images.githubusercontent.com/32564846/78982062-9a3c4600-7b21-11ea-8192-42e47b2bc73c.png)

Your source code will change, like the following:

![](https://user-images.githubusercontent.com/32564846/78982318-26e70400-7b22-11ea-9669-3d82c6223b90.png)

{% hint style="info" %}
We'll use **NodeJS** for this example, due to his simplicity, low cost hosting and low learning curve. But keep in mind that the concepts in this tutorial can be easily applied to every web framework of your choice.
{% endhint %}

Now we can add a new HTTP method POST to our web application, lets call this **/bot.** The new source will look like this:

![](https://user-images.githubusercontent.com/32564846/78982427-657cbe80-7b22-11ea-859e-3041a51ca09c.png)

We can reach this url using the full address \(with _HTTP POST_ method\):

[https://tiledeskbot.andreasponziell.repl.co/bot](https://tiledeskbot.andreasponziell.repl.co/bot)

This url is the **external bot endpoint**. We'll use this later.

Now open the **Settings** menù on the left panel of our Tiledesk project, selecting the **Bots** option

![](https://user-images.githubusercontent.com/32564846/78983111-d7093c80-7b23-11ea-9839-2bf132961f88.png)

Press the ADD BOT button, to create your own external bot. Choose the "External" option.

We must chose a name for the bot and placing in the Url field the **external bot endpoint** url of the repl app:

![](https://user-images.githubusercontent.com/32564846/78983158-f1dbb100-7b23-11ea-8a81-5c4141ebadf3.png)

Click the CREATE BOT button. Tolobot is now available in our summary list:

![](https://user-images.githubusercontent.com/32564846/78983199-0455ea80-7b24-11ea-9e4a-dae6748d5237.png)

Now it's time to write some code to make our bot service functional.

Go back to the repl project. In the index.js file modify the **/bot** service, copying and pasting the following code:

```text
const express = require('express');
const bodyParser = require('body-parser');
const { TiledeskClient } = 
  require('@tiledesk/tiledesk-chatbot-client');

const app = express();
app.use(bodyParser.json());

app.get('/', (req, res) => {
  res.send('Hello Express app!')
});

app.post('/bot', (req, res) => {
  const tdclient = 
    new TiledeskClient({request: req, response: res});
  console.log("You asked: " + tdclient.text)
  // immediatly reply to TILEDESK
  res.status(200).send({"success":true});

  // messaging is asynch.
  let msg = {
    "text": "Hello from Tiledesk external chatbot!",
    "type": "text",
    "senderFullname": tdclient.botName
  }
  tdclient.sendMessage(msg, function(err, res, resbody) {
      console.log("Message sent.")
  })
})

app.listen(3000, () => {
  console.log('server started');
});
```

To send messages to the current conversation \(and to do other interesting stuff on the same conversation\) we used Tiledesk Chatbot Client library, that we imported on top of the the index.js file:

```text
const { TiledeskClient } = 
  require('@tiledesk/tiledesk-chatbot-client');
```

You can find the full code of this tutorial on the repl linked here:

[https://repl.it/@andreasponziell/tiledeskwelcomebot](https://repl.it/@andreasponziell/tiledeskwelcomebot)

Here you can find an alternative version of the same code using raw calls to Tiledesk REST APIs instead of the NodeJS library.

[https://repl.it/@andreasponziell/tiledeskbot](https://repl.it/@andreasponziell/tiledeskbot)

## Configure a Route for the chatbot

Now that our code is ok, we should configure a routing rule to make this chatbot available to our users. Select the **Routing** option and configure the corresponding rules as follows, activating the Bot, selecting Tolobot and marking the **Bot only** option for this routing, so **Tolobot will be the only available Agent**.

![](https://user-images.githubusercontent.com/32564846/78983393-6a427200-7b24-11ea-9aa6-79bc08e1ae30.png)

## Live test

To test our chatbot go to the **Requests** menù and press the green "Simulate visitor" button as shown in the following figure.

![image](https://user-images.githubusercontent.com/32564846/78983453-86461380-7b24-11ea-8408-5f2a9bd7eae2.png)

A new browser Tab will open with the widget working as if it is already installed on your website.

Push the **New conversation** button on the widget. A conversation will open on the default routing. A hidden message is sent to your bot, if activated \(as in our example\). Your bot will reply with the message you previously configured in the code:

![](https://user-images.githubusercontent.com/32564846/78983508-a37ae200-7b24-11ea-90d7-29891c8612b7.png)

In the next tutorial you will learn how to interact with a Dialogflow agent directly from an external chatbot endpoint.

Do you have feedback on this article? Please send us your feedback writing an email to info@tiledesk.com

