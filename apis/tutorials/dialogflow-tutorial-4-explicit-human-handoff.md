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

Now the intent will reply with:

'I'm putting you in touch with an operator' \agent

![](https://user-images.githubusercontent.com/32564846/79358037-07e0db80-7f41-11ea-8d3b-ea4064ea2edf.png)

As soon as this phrase reaches Tiledesk, it automatically removes the chatbot and adds a human operator - following the rules you already set up in the Routing section or in the specific department.

To test the new talk-to-agent intent we also place a button under every DF reply (using micro languge) to allow the user to ask for an agent after each reply.
Let's train for instance the defaultWelcome Intent to show this optional button (using microlanguage to add the buttons)

![](https://user-images.githubusercontent.com/32564846/79684433-956a4700-8231-11ea-80a4-3db147559f57.png)

On every welcome intent reply the widget will show the "Talk to agent" button

![](https://user-images.githubusercontent.com/32564846/79378880-5baded80-7f5e-11ea-8bed-296904a6b986.png)

If we tap the button the "Talk to agent" intent will be invoked and the user will be routed to an agent on the current department (compatibly with the routing rules, opening hours and agents availability).

![](https://user-images.githubusercontent.com/32564846/79684581-e7f83300-8232-11ea-9aec-a34134a3cd4d.png)

Do you have feedback on this article? Please send us your feedback writing an email to info@tiledesk.com

Enjoy Tiledesk!

