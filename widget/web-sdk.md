# Web SDK

#### Web SDK ver 4.0

This guide will show you how to get started as quickly as possible with the Web SDK from TileDesk. The Web SDK will give businesses and developers the flexibility to build and customize a chat experience that meet their specific design/brand requirements.

## Install the Web HTML Widget

To chat with your visitors embed the widget on your site. Copy the following script and insert it in the HTML source between the HEAD tags:

```text
    <script type="application/javascript">
        window.tiledeskSettings = 
            {
                projectid: "YOUR_TILEDESK_PROJECT_ID"
            };
            (function(d, s, id) {
            var js, fjs = d.getElementsByTagName(s)[0];
            if (d.getElementById(id)) return;
            js = d.createElement(s); js.id = id; 
            js.src = "https://widget.tiledesk.com/v4/launch.js";
            fjs.parentNode.insertBefore(js, fjs);
            }(document, 'script', 'tiledesk-jssdk'));
    </script>
```

To get your TILEDESK\_PROJECT\_ID go to the TileDesk Dashboard and click on the Widget item of the menu:

![](https://raw.githubusercontent.com/chat21/chat21-web-widget/master/docs/tiledesk-dashboard-widget-screenshots.png)

### Configuration

Widget version 4.0 supports remote configuration of most parameters directly from the Widget menu of the Dashboard.

You can customize the widget passing these parameters to window.tiledeskSettings object:

* **projectid**. The TileDesk project id. Find your TileDesk ProjectID in the TileDesk Dashboard under the Widget menu.
* **preChatForm**: You can require customers to enter information like name and email before sending a chat message by enabling the Pre-Chat form. Permitted values: true, false. The default value is false.
* **align**: Make the chat available on the Right or on the Left of the screen. Permitted values: 'right', 'left'. Default value is right.
* **calloutTimer**: Proactively open the chat windows to increase the customer engagement. Permitted values: -1 \(Disabled\), 0 \(Immediatly\) or a positive integer value. For exmaple: 5 \(After 5 seconds\), 10 \(After 10 seconds\).
* **calloutTitle** : The title of the callout window.
* **calloutMsg** : The message of the callout window.
* **userFullname**: Current user fullname. Set this parameter to specify the visitor fullname.
* **userEmail**: Current user email address. Set this parameter to specify the visitor email address.
* **wellcomeTitle**: The welcome title to show on the widget home page.
* **wellcomeMsg**: Set the widget welcome message. Value type : string
* **widgetTitle**: Set the widget title label shown in the widget header. Value type : string. The default value is Tiledesk.
* **logoChat**: The url of the logo to show on the widget home page.
* **lang** : With this configuration it is possible to force the widget lang. The widget will try to get the browser lang, if it is not possible it will use the default "en" lang
* **hideHeaderCloseButton**: Hide the close button in the widget header. Permitted values: true, false. The default value is false.
* **isOpen**: if it is true, the chat window is automatically open when the widget is loaded. Permitted values: true, false. Default value : false
* **fullscreenMode**: if it is true, the chat window is open in fullscreen mode. Permitted values: true, false. Default value : false
* **themeColor**: allows you to change the main widget's color \(color of the header, color of the launcher button, other minor elements\). Permitted values: Hex color codes, e.g. \#87BC65 and RGB color codes, e.g. rgb\(135,188,101\)
* **themeForegroundColor**: allows you to change text and icons' color. Permitted values: Hex color codes, e.g. \#425635 and RGB color codes, e.g. rgb\(66,86,53\)
* **departmentID:** to skip departments selection, you can set the department ID upon which the widget must start the new conversation.
* **isShown:** If true \(default\) the widget is shown otherwise \(false\) the widget is hidden.
* **showWidgetNameInConversation**. If you want to display the widget title in the conversations, set the showWidgetNameInConversation field to true. It is advisable if you need to manage multiple projects. Value type : boolean. The default value is false.
* **allowTranscriptDownload**: allows the user to download the chat transcript. The download button appears when the chat is closed by the operator. Permittet values: true, false. Default value: false
* **marginX**: Set the side margin, left or right depending on the align property. Default value : 20px
* **marginY**: Set the distance from the page bottom margin. Default value : 20px
* **persistence**: You can specify how the Authentication state persists when using the Tiledesk JS SDK. This includes the ability to specify whether a signed in user should be indefinitely persisted until explicit sign out or cleared when the window is closed. Permittet values: local, session. Default value : local. Local value indicates that the state will be persisted even when the browser window is closed. An explicit sign out is needed to clear that state. Session value indicates that the state will only persist in the current session or tab, and will be cleared when the tab or window in which the user authenticated is closed.
* **showWaitTime**: Show the expected response time from your agents in the home widget window. Value type : boolean. The default value is true.
* **showAvailableAgents**: Show the available agents with avatar in the home widget window. Value type : boolean. The default value is true.
* **showLogoutOption**: Show the logout options in the home widget window. Value type : boolean. The default value is true.
* **isLogEnabled**: Enable the widget log. Value type: boolean. The default value is false.

#### Example 1. Widget with user fullname and email

```text
<script type="application/javascript">
      window.tiledeskSettings = 
          {
              projectid: "5b55e806c93dde00143163dd",
              userFullname: "Andrea Leo",
              userEmail: "andrea.leo@f21.it"
          };

      (function(d, s, id) {
        var js, fjs = d.getElementsByTagName(s)[0];
        if (d.getElementById(id)) return;
        js = d.createElement(s); js.id = id; //js.async=!0;
        js.src = "https://widget.tiledesk.com/v4/launch.js";
        fjs.parentNode.insertBefore(js, fjs);
      }(document, 'script', 'tiledesk-jssdk'));
    </script>
```

#### Example 2. Widget with preChatForm and left alignment:

```text
<script type="application/javascript">
  window.tiledeskSettings = 
    {
      projectid: "5b55e806c93dde00143163dd",
      preChatForm: true,
      align: 'left'
    };
    (function(d, s, id) {
      var js, fjs = d.getElementsByTagName(s)[0];
      if (d.getElementById(id)) return;
      js = d.createElement(s); js.id = id; 
      js.src = "https://widget.tiledesk.com/v4/launch.js";
      fjs.parentNode.insertBefore(js, fjs);
    }(document, 'script', 'tiledesk-jssdk'));
</script>
```

## Methods

### Open the widget

This will open the widget:

```text
window.tiledesk.open();
```

### Minimize the widget

This will minimize the widget:

```text
window.tiledesk.close();
```

### Hide the widget

This will hide the widget:

```text
window.tiledesk.hide();
```

### Show the widget

This will show the widget:

```text
window.tiledesk.show();
```

### Reinitialize the widget

If your app is characterized by very few page refreshes \(ie., content is swapped out on the client side but no page refresh happens, Angular, React, jQuery, etc..\) and lots of asynchronous JS, you'll need to update Tiledesk when your user's data changes. A reInit call simulates a page refresh, causing Tiledesk to reload the widget and all the configurations.

```text
window.tiledesk.reInit();
```

### Make a logout

This will logout the widget:

```text
window.tiledesk.logout();
```

### Show or hide the PreChatForm

This parameter configures the PreChatForm visibility:

```text
window.tiledesk.setPreChatForm(true|false);
```

### Send a message to a support conversation

This method sends a message to the current support conversation:

```text
const recipientId = window.tiledesk.angularcomponent.component.g.activeConversation
const message = 'hello';
const type = 'text';
const metadata = {};
const attributes = {};
window.tiledesk.sendSupportMessage(
    message,
    recipientId,
    type,
    metadata,
    attributes
)
```

## Events


### tileDeskAsyncInit

The function tileDeskAsyncInit is called when the basic apis of the widget are loaded. Inside the tileDeskAsyncInit function the object window.tiledesk is defined and can be used.   

### window.tiledesk.on\(event\_name, handler\)

Register an event handler to an event type.

Available events:

| event\_name | description |
| :--- | :--- |
| loadParams | Fired when the parameters are loaded. |
| beforeMessageSend | Fired before the message sending. |
| afterMessageSend | This event is generated after the message has been sent. |
| onInit | Fired when the widget is initialized |
| onOpen | Fired when the widget is open |
| onClose | Fired when the widget is closed |
| onOpenEyeCatcher | Fired when the callout box is open |
| onClosedEyeCatcher | Fired when the callout box is closed |
| onNewConversationComponentInit | Fired just after a new conversation is initialized |
| isLoggedIn | The event is generated when the user is logged in |
| onBeforeDepartmentsFormRender | Fired just before rendering Departments in the Departments view |

The handler will have the signature function\(event\_data\).

event\_data is a Javascript CustomEvent. More info about CustomEvent [here](https://developer.mozilla.org/en-US/docs/Web/API/CustomEvent/CustomEvent)

Arguments:

| Parameter | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| event\_name | String | YES | Event name to bind to |
| handler | Function | YES | Function with the signature function\(event\_data\) |

#### Example 3. Logging of widget events

```text
 <script type="application/javascript">    
      window.tileDeskAsyncInit = function() {
       window.tiledesk.on('beforeMessageSend', function(event_data) {
         var message =  event_data.detail;
         console.log("beforeMessageSend called ", message);
       });
       window.tiledesk.on('afterMessageSend', function(event_data) {
         var message =  event_data.detail;
         console.log("afterMessageSend called ", message);
       });
      }
</script>
```

[Full example here](https://github.com/chat21/chat21-web-widget/blob/master/src/test.html)

### Load Parameters event

This event will be fired before the tiledesk parameters is loaded. Use this event to change at runtime your TileDesk settings.

Important payload of event\_data:

| Parameter | Type | Description |
| :--- | :--- | :--- |
| detail.default\_settings | Object | the constructor default settings |

#### Example 4. Widget with visitor fullname and email from localStorage

```text
<script type="application/javascript">    
    //set fullname to localstorage
    localStorage.setItem("user_fullname", "Andrea from localStorage");
    localStorage.setItem("user_email", "andrea.leo@f21.it");

      window.tileDeskAsyncInit = function() {
       window.tiledesk.on('loadParams', function(event_data) {
          window.tiledeskSettings.userFullname = localStorage.getItem("user_fullname");
          window.tiledeskSettings.userEmail = localStorage.getItem("user_email");
       });
      }
</script>
```

[Full example here](https://github.com/chat21/chat21-web-widget/blob/master/src/test.html)

#### Example 5. Widget with welcome message with current date

```text
<script type="application/javascript">    
      window.tileDeskAsyncInit = function() {
       window.tiledesk.on('loadParams', function(event_data) {
         window.tiledeskSettings.wellcomeMsg = " Hello at: " + new Date().toLocaleString();
       });
      }
</script>
```

### Before sending messsage

This event will be fired before the message sending. Use this event to add user information or custom attributes to your chat message.

Important payload of event\_data:

| Parameter | Type | Description |
| :--- | :--- | :--- |
| detail | Object | the message that is being sent |

Example. Programmatic setting custom user metadata

```text
 <script type="application/javascript">    
      window.tileDeskAsyncInit = function() {
       window.tiledesk.on('beforeMessageSend', function(event_data) {
         var message =  event_data.detail;
         message.attributes.userCompany = "Frontiere21";
       });
      }
</script>
```

[Full example here](https://github.com/chat21/chat21-web-widget/blob/master/src/test.html)

Example. Add a custom attribute \(page title\) to the message.

```text
 <script type="application/javascript">    
      window.tileDeskAsyncInit = function() {
       window.tiledesk.on('beforeMessageSend', function(event_data) {
         var message =  event_data.detail;
         message.attributes.pagetitle = document.title;
       });
      }
</script>
```

[Full example here](https://github.com/chat21/chat21-web-widget/blob/master/src/test.html)

### After messsage sent

This event is generated after the message has been sent.

Important payload of event\_data:

| Parameter | Type | Description |
| :--- | :--- | :--- |
| detail | Object | the message that was sent |

Example:

```text
 <script type="application/javascript">    
      window.tileDeskAsyncInit = function() {
        window.tiledesk.on('afterMessageSend', function(event_data) {
          var message =  event_data.detail;
          console.log("afterMessageSend called ", message);
       });
      }
</script>
```

### onBeforeDepartmentsFormRender

This event is generated before rendering the Departments selection View. Use this event if you want to filter the default Departments list based on some conditions.

Important payload of event\_data:

| Parameter | Type | Description |
| :--- | :--- | :--- |
| detail.departments | Object | the array of the default Departments |

Example:

In the following example Departments are filtered based on the current widget language.
Actually a Deparment doesn't provide a specific "language" field. In this example Department language is put in the Department description field. A next update will provide specific Department "tags" (or "lables") that will be used to save specific informations into the Department resources.

```text
<script type="application/javascript">
window.tileDeskAsyncInit = function() {
  window.tiledesk.on('onBeforeDepartmentsFormRender', function(event_data) {
    var departments = event_data.detail.departments;
    var lang = window.tiledesk.angularcomponent.component.g.lang;
    if (lang && lang === 'en') {
      return departments.filter(function(dep) {
        if (dep.description.includes('English')) {
            return dep;
        }
      });
    } else {
      return departments.filter(function(dep) {
        if (dep.description.includes('French')){
            return dep;
        }
      });
    }
  });
}
</script>
```

### onNewConversationComponentInit

This event is generated as soon as a new conversation view is rendered. Use this event if you want to execute some actions on a Conversation start.

Important payload of event\_data:

| Parameter | Type | Description |
| :--- | :--- | :--- |
| detail.newConvId | Object | the id of the conversation that fired the event |

Example:

In the following example a hidden message is sent as soon as a conversation starts. Sending a hidden message is useful to fire a bot welcome message, if one is invited in the conversation.

```text
<script type="application/javascript">    
window.tileDeskAsyncInit = function() {
    window.tiledesk.on('onNewConversationComponentInit', function(event_data) {
    const message = 'hello';
    const recipientId = event_data.detail.newConvId;
    const type = 'text';
    const metadata = {};
    const attributes = {test:'test attributes', subtype: 'info'};
    window.tiledesk.sendSupportMessage(
        message,
        recipientId,
        type,
        metadata,
        attributes
    )
    });
}
</script>
```

## Enabling authenticated visitors in the Chat widget

You can configure your widget to authenticate visitors using the Javascript API and JWT token. More info [Widget Authentication](auth.md)

