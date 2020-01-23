# Running Tiledesk from Source Code

Applicable to Tiledesk version 2

Tiledesk uses [Chat21](http://www.chat21.org) as messaging platform. Refer to [Architecture overview](../architecture/schema.md) to undestand the product's modules.

Chat21 relies on Firebase as the backend, so it's really important for you to acquire familiarity with Firebase and all of his services.

**Please help us improving this documentation**: if you encounter a problem, something you don’t understand or a typo, use [this link](https://github.com/Tiledesk/tiledesk-server/issues) to ask a question. You could also open a PR to directly fix the documentation on Github, if you want.

Tiledesk is composed by the following components:

* tiledesk-server
* tiledesk-dashboard
* chat21-cloud-functions
* chat21-web-widget
* chat21-ionic

## Installation tips

* Enable https to front-end and backend endpoints. Https is required for receiving web push notifications;
* Create a DNS entries for:
  * tiledesk-server. Create a DNS entry like this: api.YOURDOMAIN.COM. Then configure a virtualhost for it.
  * chat21-web-widget. Create a DNS entry like widget.YOURDOMAIN.COM. 
  * tiledesk-dashboard and chat21-ionic are suggested to by under the same domain to share the authentications tokens. Create a DNS entry like support.YOURDOMAIN.COM. You must be able to access :
    * /dashboard -&gt; Tiledesk dashboard component
    * /chat -&gt; Chat21 ionic component
  * Install the latest stable release versions of the components. Check the last release under Releases tab of every Github components pages.

## Overview

Please follow this guide in order to install all the Tiledesk components.

## 1. Create and configure a Firebase project

Chat21 relies on Firebase as the backend, so it's really important for you to acquire familiarity with Firebase and all of his services.

Sign up on Firebase and create a project. Please refer to our [guide](create-a-firebase-project.md) or directly to Firebase [https://firebase.google.com](https://firebase.google.com) to accomplish and better understand this task.

## 2. Install chat21-cloud-functions

To install and configure chat21-cloud-functions follow this README: [https://github.com/chat21/chat21-cloud-functions](https://github.com/chat21/chat21-cloud-functions)

Also you can find the detailed configuration steps of chat21-cloud-functions [here](detailed-chat21-cloud-function-installation.md).

## 3. Install and configure tiledesk-server 

To install tiledesk-server version 2 please use the **dev** branch of Github project and follow this guide: [https://github.com/Tiledesk/tiledesk-server/tree/dev\#install-from-source-code](https://github.com/Tiledesk/tiledesk-server/tree/dev#install-from-source-code)

## 4. Configure the webhook module of chat21-cloud-functions

Chat21 communicates with Tiledesk through webhooks. When a Chat21 event occurs - a new message arrives, a new member join a group, etc - a new Event is created and notified to Tiledesk Server. Chat21 then makes an HTTP POST request to send the Event to the Tiledesk webhook endpoint.

Chat21 needs a public Tiledesk server endpoint to work properly.

Firebase requires an active billing project to perform external call. It is necessary to do **external HTTP requests** and since Tiledesk Server lives outside Google’s servers we need to switch to the **Blaze** **plan**, which is [surprisingly cheap](https://firebase.google.com/pricing/).

Enable the webhook with :

```text
$ firebase functions:config:set webhook.enabled=true
```

Configure the webhook endpoint with:

```text
$ firebase functions:config:set webhook.url=<PUBLIC_TILEDESK_URL_EXPOSED_BY_NGROK>/chat21/requests
```

Example: firebase functions:config:set webhook.url=[https://YOUR\_TILEDESK\_DOMAIN/chat21/requests](https://YOUR_TILEDESK_DOMAIN/chat21/requests)



You can find other info on this guide: [https://github.com/chat21/chat21-cloud-functions/blob/master/docs/setup\_options.md\#webhook](https://github.com/chat21/chat21-cloud-functions/blob/master/docs/setup_options.md#webhook)

## Install and configure tiledesk-dashboard

Follow this guide to install and configure Tiledesk-Dasboard: [https://github.com/Tiledesk/tiledesk-dashboard](https://github.com/Tiledesk/tiledesk-dashboard)

## Install and configure chat21-web-widget

Follow this guide to install and configure the Web Widget: [https://github.com/chat21/chat21-web-widget](https://github.com/chat21/chat21-web-widget)

## Configure push notification

Follow this guide to configure push notification for chat21-cloud-functions: [https://github.com/chat21/chat21-cloud-functions/blob/master/docs/setup\_options.md\#push-notification](https://github.com/chat21/chat21-cloud-functions/blob/master/docs/setup_options.md#push-notification) 

Configure Chat21-ionic following this guide: [https://github.com/chat21/chat21-ionic\#push-notification](https://github.com/chat21/chat21-ionic#push-notification)

