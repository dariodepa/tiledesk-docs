---
description: >-
  Let your Dialogflow agents talk with Tiledesk human agents through an externl
  chatbot
---

# Dialogflow as external chatbot integration

## Introduction

Integrating Dialogflow agents to Tiledesk offers many advantages, first of all the possibility to handoff current chatbot's conversation to humans. This is a very common task in chatbot integration design, because a chatbot cannot always satisfy every user request or simply because the first chatbot was there just to welcome the user, get the user question, choose the right team and then forward the request to the selected team.

We just created this first toturial to allow a more customized integration experience with Dialogflow, allowing you to understand how easy is to attach an external chatbot, Dialogflow in this case, to Tiledesk and switch conversation to humans when needed.

We'll use [Heroku](https://www.heroku.com/) and [Github](https://github.com/) to crete our first integration project.

## Fork the tutorial code

The tutorial code is already available on Github [here](https://github.com/Tiledesk/tiledesk-dialogflow-proxy-tutorial).

Fork the tutorial code on your favourite repo using the Fork button. Now you have a copy of the tutorial on your own repo.

## Create the Heroku app

If you don't have a Heroku account please create one. Once you created your account you will move to the application's dashboard [here](https://dashboard.heroku.com/apps).

In the top right corner menù of the Heroku Dashboard press _New_ &gt; _Create new app_ option:

![](https://user-images.githubusercontent.com/32564846/78923546-ae883080-7a98-11ea-87fe-a3168109499e.png)

Now choose a name for your application. You can choose whatever name you prefer, we choose **my-tiledesk-proxy:**

![](https://user-images.githubusercontent.com/32564846/78923583-c069d380-7a98-11ea-8a80-76d137cf634e.png)

Leave all other settings as default and push the _Create app_ button.

## Connect Heroku app to your Github repo

Now in the "Deployment method" section select Github. In the "Connect to Github" section insert the exact name of the repo you just forked - tiledesk-dialogflow-proxy-tutorial - and press Search. If everything is correct Heroku will show your repo just below the search filed. Press "Connect".

![](https://user-images.githubusercontent.com/32564846/78923614-cd86c280-7a98-11ea-97bf-3f11fd92f62d.png)

Now that your Heroku's app is connected to Github you can enable automatic deploys, so Heroku will restart your app every time you push new code on the repo.

![image(3)](https://user-images.githubusercontent.com/32564846/78923647-da0b1b00-7a98-11ea-94f6-d1bc88fc9453.png)

In this tutorial we suppose you already set up a Dialogflow agent and you already have the credentials file. If you do not have the Google Credentials file please refer to this [tutorial](generate-dialgoflow-google-credentials-file.md).

Now that you have the credentials file on your hand open the Heroku Dashboard of your project and move to the Settings tab. Then, in the Config Vars section press the "Reveal config vars" button.

Add a new variable named GOOGLE\_CREDENTIALS and fill his value field with the content of the credentials file you already created in the previous step:

![image(4)](https://user-images.githubusercontent.com/32564846/78923682-e7c0a080-7a98-11ea-9d6e-dfe385122046.png)

Now switch to Tiledesk console and create a new project. Enter whatever name you prefer.

![image(5)](https://user-images.githubusercontent.com/32564846/78923744-fe66f780-7a98-11ea-829c-d6639fbf7986.png)

Now move to the Bots section and create a new bot pressing the ADD BOT button:

![image(6)](https://user-images.githubusercontent.com/32564846/78923774-09218c80-7a99-11ea-9b9e-567eb8125439.png)

Choose the type **External**, not the Dialogflow one. This tutorial aims to connect you with a Dialogflow agent using the "external bot" feature, allowing you to have full control over the integration.

![image(7)](https://user-images.githubusercontent.com/32564846/78923825-1a6a9900-7a99-11ea-97aa-4ad8ca83a739.png)

Choose whatever name you prefer for the bot. This name will also be the Sender name of the bot every time the bot writes something. But from the proxy code you are adding you can easily change this default name if you want.

Set in the url field the hostname of your heroku application followed by **/bot**. Every time Tiledesk will invoke you bot it will send a HTTP POST request to this url.

![image(8)](https://user-images.githubusercontent.com/32564846/78923885-2fdfc300-7a99-11ea-9930-57bd3337d15e.png)

To activate the bot you must attach it to the default routing or to a department. For semplicity we'll use the default Routing. Choose the Routing option on the left menu, the switch on Activate Bot, and choose your Dialogflow bot from the right menu. Press UPDATE ROUTING RULES.

![image(9)](https://user-images.githubusercontent.com/32564846/78923929-40903900-7a99-11ea-93c5-af85df7cbcda.png)

To test the bot, switch to the Requests option and press the **SIMULATE VISITOR** button as shown in the next figure.

![image(10)](https://user-images.githubusercontent.com/32564846/78923956-4d149180-7a99-11ea-9eaa-e6197b2ff7fd.png)

On the widget test page press "New conversation" button. The default routing will start, sending a default "hello" message through a HTTP POST call to the external url. Your Dialogflow bot will reply, as you can see in the next picture.

![image(11)](https://user-images.githubusercontent.com/32564846/78923978-59005380-7a99-11ea-8363-73658e6dd6a6.png)

You can do much more in communicating with an external url, for example sending buttons or images. We will treat these and other tools in the next tutorials.

## Chatbot handoff to Human Agents

To handoff control to Tiledesk agents the bot can simply reply \agent. So simply you can train a Dialogflow intent to reply "\agent" to a phrase like "I want to talk to an agent". As soon as Tiledesk receives the \agent command in reply to a conversation activates the human handoff and switches control to humans following the department rules.

You can also automatically activate switch to humans on a fallback \(or a fallback repeating N times\). So, if the user repeatedly triggers the fallback response \(due to questions not correctly interpreted by the Dialogflow chatbot\) the proxy passes control to a human agent.

Another approach can be to use the "confidence" of the reply to trigger the handoff if the same confidence is under a determined threshold.

Enjoy you custom Dialogflow connection!

Do you have feedback on this article? Please send us your feedback writing an email to info@tiledesk.com

