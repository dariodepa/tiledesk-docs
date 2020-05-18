# Anonymous vs Authenticated User

By default, first time an end-user starts a conversation with Tiledesk \(generally from a chat Widget\), a new Anonymous User is created. This anonymous user has a unique UUID that is reused in next conversations. Tiledesk creates a Contact for the anonymous user if none exists and attaches the new support request to it.

With anonymous users, the Agent has no way to certificate user identity, user email, fullname and other data provided by the user itself.

This will prevent the Agent to provide to this user sensible informations.

Tiledesk provides a secure way, based on JWT, to provide a certified user profile to Agents. This secure way of providing certified identity is named authenticated visitor and is described here:

[https://developer.tiledesk.com/widget/auth](https://developer.tiledesk.com/widget/auth)

You can find an example instance of authenticated user in article \(§ Authentication\) where we describe what we did for an italian University live chat project:

[https://www.tiledesk.com/tiledesk-for-unisalento/](https://www.tiledesk.com/tiledesk-for-unisalento/)

As you can see, authenticated users differs from anonymous users by the presence of a shield in the user profile image:

![image](https://user-images.githubusercontent.com/9378770/79009344-87486680-7b5f-11ea-87df-7c3bdfe38019.png)