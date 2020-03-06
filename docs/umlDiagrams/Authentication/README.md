# Authentication in Bot Framework
How authentication is integrated into the Bot Framework.

- [High Level Authorization Flow](#high-level-authorization-flow)
- [Diagrams of Adding Authentication to Your Bot](#diagrams-of-adding-authentication-to-your-bot)
- [Authentication within the SDK](#authentication-within-the-sdk)
- [OAuthPrompt Flow Charts](#oauthprompt-flow-charts)

___

## **High Level Authorization Flow**

Within Bot Framework, an OAuth flow typically boils down to your **bot** wanting to access a **protected resource** on behalf of the **user** (i.e. the **resource owner**). In order to do this, we must verify that the user is someone who has the authority to access the protected resource and can, in turn, also delegate part of their authority to the bot to access the resource.

The protected resource accepts an access *token* as "proof" that the bot has been delegated permission to access it. The token acts as a limited-access key. 

The access token is used, because:
- It does not expose the user's log-in credentials for the protected resource to the bot
    - Bot cannot impersonate user
- Provides scopes (subset of functions or permissions) that the user allows the bot to perform
    - This thus allows the user to limit the actions the bot can do on his/her behalf
    - For example, a bot may be allowed to read your social media contacts, but it cannot send messages to them or delete any of them

**Giving Bot Access to the Proteced Resource**

![Giving Bot Access to Protected Resource](./HighLevelAuthFlow/GiveBotAccessToProtectedResource.svg "Giving Bot Access to Protected Resource")

Another participant in the OAuth flow is the **authorization server (AS)** or identity provider (IdP). An Azure Active Directory (AAD) app is an example of an identity provider in the cloud. AAD:
- Authenticates users
- Provides access tokens to authorized clients

You can register AS/IdP to your bot from within Azure Bot Service.

![Authorization Server Authenticates User](./HighLevelAuthFlow/AuthServer)

The protected resource trusts tokens issued from a specified authorization server(s). (OAuth protocol does not specify how the trust is established between the protected resource and the authorization server, only that it does happen--allowing for flexibility at the same time as mandating what is necessary for security.)
When a user wants the bot to access the protected resource, the bot sends the user to the authorization server to allow the user to authorize the bot to access the resource. Once authorized, the authorization server sends the acess token to the bot. The bot can now use the external service, making sure to include the token in its calls to the resrouce's API.

___

## Adding Authentication to Your Bot
Contains diagrams of adding authentication as described by examples in Bot Framework documentation.

Click to view diagrams of the following articles
- *[Authentication]()*
- *[Add authentciation to your bot via Azure Bot Service]()*

___

## Authentication within the SDK

___

## `OAuthPrompt` Flow Charts

___

## Authentication in the Bot Framework

Class diagrams, showing the hierarchies involved in authentication within the Bot Framework.