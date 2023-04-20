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

Policies allow you to set more in depth permissions allowing for more complex logic as to how users 
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
