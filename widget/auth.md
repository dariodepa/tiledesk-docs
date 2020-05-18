# Widget Authentication

## Enabling authenticated visitors

Require Widget Javascript API v4

### Overview

You can configure your widget to authenticate visitors using the Javascript API and JWT token.

When you configure the Chat widget to use authenticated visitors, you get the following benefits:

* Ability to have higher confidence and security that the visitor/customer you or your agents are talking to is the real deal
* Support for cross device/browser identification. The visitor can be viewed as the same person if or when they choose to use a different device or browser when the custom ID is specified in the authentication call.

### Generating a Chat shared secret

To configure your widget for visitor authentication, you need a shared secret. A shared secret is a security setting, intended to be generated, copied, and pasted into a communication with your engineering team, or directly into your codebase, in a single sitting. It should not be entered into a browser.

Only Chat administrators can configure visitor authentication settings.

To generate the shared secret required for authenticated visitors

* Open the Dashboard and go to Project Name &gt; Project Settings.
* Scroll down to the Visitor Authentication section and click the Generate button.

![](https://raw.githubusercontent.com/Tiledesk/tiledesk-docs/master/docs/tiledesk-project-settings2.png)

Note:The shared secret is intended to remain secure. As a result, it will only appear in full one time. If you don’t have access to the shared secret and need the full secret to create your token, you can reset the secret by clicking the 'Generate' button. Regenerating a new shared secret will revoke the previous token. If you have concerns the shared secret has been compromised, you should regenerate a new one. If you need to rotate the keys, you should schedule it when Chat is offline because regenerating the secret cause visitors to be disconnected from the widget.

Once you have generated the shared secret, use it to create a JWT token that you'll add to your Web Widget snippet.

### Creating a JWT token

To create a JWT token and add the code to the Chat snippet

1\) Construct a server-side payload of data for the JWT token. Your token needs to be dynamically generated from the server-side on page load. Please follow this guide to [create a JWT token](../apis/authentication/README.md). 


2\) Use the **window.tiledesk.signInWithCustomToken** Javascript API to provide a function which supplies a fresh JWT every time it is invoked. Below is a code example:

```text
window.tiledesk.signInWithCustomToken("<JWT_TOKEN_HERE_GENERATED_SERVER_SIDE>");
```

Example:

```text
window.tiledesk.signInWithCustomToken("JWT 12345678...");
```

See an [example here](https://github.com/chat21/chat21-web-widget/blob/master/src/test.html).



## About the agent experience with authenticated visitors

A few things are updated in the Chat dashboard when an agent starts chatting with an authenticated visitor.

First, the agent will be able to tell the visitor is authenticated by the authenticated checkmark overlay on the visitor's avatar.

![](https://raw.githubusercontent.com/Tiledesk/tiledesk-docs/master/docs/authuser.png)

