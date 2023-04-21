# MS-600: Implement Microsoft Identity

[Training Link](https://learn.microsoft.com/en-us/training/modules/getting-started-identity/)

## Types of tokens used in Microsoft Identity

Users can access applications from many different networks that may be internal or external and 
can also access them from a number of different devices. Using an identity provider helps simplify 
security concerns across the range of access methods. Identity providers allow you to add 
more niche permissions to your application (e.g. this resource can only be accessed internally) 

Microsoft provides 3 solutions for dealing with different types of users, Azure AD, B2B and B2C.
B2B allows authentication between different Organisations that use Azure AD.
B2C provides OAuth capabilities to allow users to sign in with an existing identity like their Microsoft account.

#### Policies

Policies allow you to set more in-depth permissions allowing for more complex logic as to how users 
can interact with your applications. This allows you to focus more on your application logic rather than 
having to manually implement complex access policies in the application.

### OpenID Connect and ID Tokens

OpenID Connect extends OAuth 2.0 and allows you to implement single sign-on in your application. 
An ID token is a security token that allows the client to verify the identity of the user. This token 
also provides some basic profile information and the claims within your application. These tokens are not 
the same as access tokens that are used for authorisation. ID Tokens use JWT with the payload containing 
the user information.

ID tokens can be obtained through the redirects flow which will send a callback to your application once 
the user has successfully authenticated. 

### Access Tokens

Access tokens allow users to access Microsoft resources from your application given their user context.
To acquire a token you should first try and acquire one silently with the MSAL library in case a token is cached or 
can be silently refreshed, in the case it can't, a **UI Required** exception will be thrown, after which 
the application should go through the interactive flow. This may also be thrown if the user hasn't consented 
to permissions or needs MFA approval.

### Application Tokens

Application tokens allow your application to authenticate with Microsoft in its own context not relying on the 
context of the user who has logged in.

## Account Types

### Single Tenant Apps 

This is for applications that will only be used by users in your tenancy, no one outside your tenancy will be 
able to login to this application.

### Multi-Tenant Apps

This is for applications that expect more than one organisation to be able to sign in to your application. 
When testing your application you should ensure testing has been completed from an organisation with conditional 
access configured as your application may or may not obtain an access token based on the outcome of conditional 
access, therefore these cases will need to be handled gracefully. Your application should follow the principal 
of minimum required access and should only request permissions that it needs. Permissions that require admin 
consent should generally be avoided as it may prevent some users from being able to use your application at all. 
Appropriate names and descriptions for the requested permissions should be provided to help users and 
admins understand what access they are agreeing to.

