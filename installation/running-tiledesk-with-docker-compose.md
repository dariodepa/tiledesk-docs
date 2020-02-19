---
description: >-
  This guide is still in beta. The docker images is nightly build so can
  contains bugs and instability.
---

# Running Tiledesk with Docker Compose

Note that you need to know a bit of [Docker](https://docs.docker.com/) and [Docker Compose](https://docs.docker.com/compose/) to follow these instructions.

Tiledesk uses [Chat21](http://www.chat21.org) as messaging platform. Refer to [Architecture overview](../architecture/schema.md) to undestand the product's modules.

**Please help us improving this documentation**: if you encounter a problem, something you don’t understand or a typo, use [this link](https://github.com/Tiledesk/tiledesk-server/issues) to ask a question. You could also open a PR to directly fix the documentation on Github, if you want.

## 1. Run Docker Compose services

Run the following code:

```bash
mkdir tiledesk && cd tiledesk
curl https://raw.githubusercontent.com/Tiledesk/tiledesk-server/master/docker-compose.yml --output docker-compose.yml
```

Start all the Tiledesk services just typing:

```text
docker-compose up -d
```

If docker is installed with root user run: sudo docker-compose up -d

Ensure the [required tiledesk ports](open-the-ports.md) are open.

Verify the installation to

{% embed url="http://localhost:3000/" caption="" %}

You should see the message "Hello from Tiledesk server. It's UP."

To see the log run:

```text
docker-compose logs -t -f --tail 5
```

## 2. Firebase setup

### **2.1 Create a Firebase project**

Sign up on Firebase and create a project. Please refer to [our guide](create-a-firebase-project.md) or directly to Firebase [https://firebase.google.com](https://firebase.google.com/) to accomplish and better understand this task.

Tiledesk uses [Chat21](http://www.chat21.org) and Chat21 relies on Firebase as the backend, so it's really important for you to acquire familiarity with Firebase and all of his services.

## 3. Chat21 Cloud Functions installation and setup

### 3.1 Install Chat21 Cloud Functions

Start chat21-cloud-function service command line interface \(CLI\) typing:

```text
docker-compose run --service-ports cloud-functions
```

Use sudo if you installed docker with root privilege.

![](../.gitbook/assets/image%20%2827%29.png)

More info here: [Detailed Chat21 Cloud Function installation](detailed-chat21-cloud-function-installation.md).

Authenticate to Firebase running :

```text
firebase login
```

Select the firebase project where you want to install Chat21 Cloud Functions

```text
firebase use --add
```

Deploy the Chat21 Cloud Functions:

```text
firebase deploy
```

Exit from the Chat21 Cloud Functions CLI with :

```text
exit
```

### 3.2 Configure the Chat21 webhooks

Chat21 communicates with Tiledesk through webhooks. When a Chat21 event occurs - a new message arrives, a new member join a group, etc - a new Event is created and notified to Tiledesk Server. Chat21 then makes an HTTP POST request to send the Event to the Tiledesk webhook endpoint.

Chat21 needs a public Tiledesk endpoint to work properly.

Firebase requires an active billing project to perform external call. It is necessary to do **external HTTP requests** and since Tiledesk Server lives outside Google’s servers we need to switch to the **Blaze** **plan**, which is [surprisingly cheap](https://firebase.google.com/pricing/).

#### 3.2.1 Make the Tiledesk server endpoint public

If you have a public URL \(public IP\) of your Tiledesk server installation please skip this paragraph.

To expose Tiledesk server endpoint as public resource, we use **ngrok**. This simple tool allows you to create a public URLs of your local Tiledesk installation. Tiledesk docker installation has a built-in ngrok service.

Open the the following URL:

[localhost:4040](http://localhost:4040)

![](../.gitbook/assets/image%20%2866%29.png)

At this point, you have a tunnel to your local Tiledesk server. It means your development server is exposed to the outside world. Try making requests to your tunnel URLs – you will see that they hit your local server.

#### 3.2.2 Setting up the webhook endpoint

If not already in use, start cloud-function service command line interface \(CLI\) typing:

```text
docker-compose run --service-ports cloud-functions
```

Enable the webhook with :

```text
firebase functions:config:set webhook.enabled=true
```

Configure the webhook endpoint with:

```text
firebase functions:config:set webhook.url=<PUBLIC_TILEDESK_URL_EXPOSED_BY_NGROK>/chat21/requests
```

Example: firebase functions:config:set webhook.url=[https://cf988f60.ngrok.io/chat21/requests](https://cf988f60.ngrok.io/chat21/requests)

Exit from the Chat21 Cloud Functions CLI with :

```text
exit
```

## 4. Configure the clients

Tiledesk is composed by different clients \(web widget, web chat, dashboard, etc..\).

You must set the following properties:

* FIREBASE\_PRIVATE\_KEY. Get it [here](create-a-firebase-project.md#create-an-sdk-firebase-admin-account). More info about firebase private key [here](https://firebase.google.com/docs/admin/setup#initialize_the_sdk).
* FIREBASE\_CLIENT\_EMAIL. Get it [here](create-a-firebase-project.md#create-an-sdk-firebase-admin-account).
* FIREBASE\_PROJECT\_ID. Get it [here](create-a-firebase-project.md#create-an-app).
* FIREBASE\_APIKEY. Get it [here](create-a-firebase-project.md#create-an-app).
* FIREBASE\_AUTHDOMAIN. Get it [here](create-a-firebase-project.md#create-an-app).
* FIREBASE\_DATABASEURL. Get it [here](create-a-firebase-project.md#create-an-app).
* FIREBASE\_STORAGEBUCKET
* FIREBASE\_MESSAGINGSENDERID. Get it [here](create-a-firebase-project.md#create-an-app). A unique numerical value created when you create your Firebase project, available in the [Cloud Messaging](https://console.firebase.google.com/project/_/settings/cloudmessaging/) tab of the Firebase console **Settings** pane. 
* CHAT21\_ENABLED. Enable Chat21 channel with **true** value. 
* CHAT21\_URL. Get it [here](create-a-firebase-project.md#get-the-cloud-function-url).
* CHAT21\_APPID. Enter the value **tilechat**
* CHAT21\_ADMIN\_TOKEN. The Chat21 admin token. The default value is `chat21-secret-orgAa,`. See [here](https://github.com/chat21/chat21-cloud-functions/blob/master/docs/setup_options.md#admin-token) to change it.

To configure the parameters run the following command:

```text
docker-compose run server nano ./confenv/.env
```

Open the the following URL:

{% embed url="https://localhost/dashboard" caption="" %}

