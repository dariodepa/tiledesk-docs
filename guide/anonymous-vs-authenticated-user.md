By default, first time an end-user starts a conversation with Tiledesk (generally from a chat Widget), a new Anonymous user is created. This anonymous user has a unique UUID that is reused in next conversations. Tiledesk creates a Contact for the anon-user if none exists and  attaches the new support request to it.

With anonymous users, the Agent has no way to certificate user identity, user email, fullname and other data provided by the user itself.

This will prevent the Agent to provide to this user sensible informations without risk.

Tiledesk provides a secure way, based on JWT, to provide a certified user profile to Agents.
This secure way of providing certified identity is named authenticated visitor and is described here:

https://developer.tiledesk.com/widget/auth

You can find an example instance of authenticated user in article  (§ Authentication) where we describe what we did for an italian University live chat project:

https://www.tiledesk.com/tiledesk-for-unisalento/

As you can see, authenticated users differs from anonymous users by the presence of a shield in the user profile image:



All the details about authentication are always available to Agents in the senderAuthInfo section in the Contact and Request panel:


