# Trufla-Intern
## Keycloak
- It is type of SSO. SSO is a is a property of access control for multiple related and independent software systems where user login with single ID and password to gain access to a connected system/s without different usernames or passwords.
- It is an open source identity and access management solution which mainly aims at applications and services.
- Users can auhenticate with keycloak rather than indvudual apps. So the apps do not have to deal with login forms and all work with the authentication.
- Users do nt have to login again to access different app, same for the logout.

## Common words in Keycloak
- Users: They are entties that are able to log in. They can have attributes associated with themselves like email, username, address, phone number, and birth day. They can be assigned group membership and have specific roles assigned to them.

- Athentication: The process of identifying and validating a user

- Authorization: The process of granting access to a user.

- Roles: Roles identify a type or category of user. Admin, user, manager, and employee are all typical roles that may exist in an organization.

- User role mapping: A user role mapping defines a mapping between a role and a user. A user can be associated with zero or more roles.

- Groups: Groups manage groups of users. Attributes can be defined for a group. You can map roles to a group as well. Users that become members of a group inherit the attributes and role mappings that group defines.

- Realms: A realm manages a set of users, credentials, roles, and groups. A user belongs to and logs into a realm. Realms are isolated from one another and can only manage and authenticate the users that they control. One Keycloak deployment can define, store, and manage as many realms as there is space for in the database. Also, There exists two types of realms, the master realm and the other realms The master realm contains the adminstrative account created when first loging in to keycloak.

- Clients: Clients are entities that can request Keycloak to authenticate a user. 
Most often, clients are applications and services that want to use Keycloak to secure themselves and provide a single sign-on solution.

- Identity token: A token that provides identity information about the user. Part of the OpenID Connect specification.

- Access token: A token that can be provided as part of an HTTP request that grants access to the service being invoked on. 
This is part of the OpenID Connect and OAuth 2.0 specification

- Service account: Each client has a built-in service account which allows it to obtain an access token.

- Themes: Every screen provided by Keycloak is backed by a theme. Themes define HTML templates and stylesheets which you can override as needed.


## How keycloak works?
 A user clicks from a public page to navigate to protected area within the application
 1) The user will be redirected to the keycloak authentication page. After providing username and password, keycloak redirects the user back to the application again with a code that is valid to a very short span of time.
 2) The application communicates this code to keycloak along with the application ID and the application secret, then keycloak replies with the Access token, ID token, and a Refresh token.
 The application will need only one of these tokens to see which claims the user has, and according to the claims, the user will be granted or denied access to the requested protected URL(s)
 .
 ## Keycloak With OpenID Connect(OIDC)
 OIDC is an authentication protocol that is an extension of OAuth 2.0. OAuth 3.0 is only a framework for building authorisation protocols, but OIDC is a full-fledged authentication and authorisation protocol. OIDC authentication flow when integrated with keycloak:

1) Browser visits application. The application notices the user is not logged in, so it redirects the browser to keycloak to be authenticated. The application passes along a call-back URL(a redirect URL) as a query parameter in this browser redirect that keycloak will use when it finishes authentication.

2) Keycloak authenticates the user and creates a one-time, very short lived, temporary code. Keycloak redirects back to the application using the call-back URL provided earlier and additionally adds the temporary code as a query parameter in the call-back URL.

3) The application extracts the temporary code and makes a background out of band REST invocation to keycloak to exchange the code for an identity, access and refresh token. Once this temporary code has been used to obtain the tokens, it can never be used again. This prevents potential replay attacks.
![image2](https://user-images.githubusercontent.com/108682254/177343175-802d0096-2bec-4ff9-9448-44401549f250.png)
