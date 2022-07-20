## JWT (JSON Web Token)

Comparing with Session-based Authentication that need to store Session on Cookie, the big advantage of Token-based Authentication is that we store the JSON Web Token (JWT) on Client side: **Local Storage** for Browser, **Keychain** for IOS and **SharedPreferences** for Android… So we don’t need to build another backend project that supports Native Apps or an additional Authentication module for Native App users.


![[Pasted image 20220620091644.png]]


There are three important parts of a JWT: Header, Payload, Signature. Together they are combined to a standard structure: `header.payload.signature`.


The Client typically attaches JWT in **x-access-token** header:

```
x-access-token: [header].[payload].[signature]
```

## React Express Authentication example

It will be a full stack, with Node.js Express for back-end and React.js for front-end. The access is verified by JWT Authentication.

-   User can signup new account, login with username & password.
-   Authorization by the role of the User (admin, moderator, user)

Let’s see the screenshots of our system:

– Anyone can access a public page before logging in:

![[Pasted image 20220620091948.png]]

– A new User can signup:

![[Pasted image 20220620092005.png]]

– Form Signup validation will be like this:

![[Pasted image 20220620092022.png]]


– After signup is successful, User can login:

![[Pasted image 20220620092035.png]]

– After login, App directs the User to **Profile** page:

![[Pasted image 20220620092050.png]]

– UI for **Moderator** login (the navigation bar will change by authorities):

![[Pasted image 20220620092112.png]]


– If a User who doesn’t have Admin role tries to access **Admin**/**Moderator Board** page:
![[Pasted image 20220620092131.png]]


## Flow for User Registration and User Login

The diagram shows flow of User Registration, User Login and Authorization process.

![[Pasted image 20220620094842.png]]

There are 2 endpoints for authentication:

-   `api/auth/signup` for User Registration
-   `api/auth/signin` for User Login

If Client wants to send request to protected data/endpoints, it add legal JWT to HTTP **x-access-token** Header.


## Back-end with Node.js Express & Sequelize

### Overview

Our Node.js Express Application can be summarized in the diagram below:

![[Pasted image 20220620094918.png]]


Via _Express_ routes, **HTTP request** that matches a route will be checked by **CORS Middleware** before coming to **Security** layer.

**Security** layer includes:

-   JWT Authentication Middleware: verify SignUp, verify token
-   Authorization Middleware: check User’s roles with record in database

If these middlewares throw any error, a message will be sent as HTTP response.

**Controllers** interact with MySQL Database via [Sequelize](https://sequelize.org/v5/) and send **HTTP response** (token, user information, data based on roles…) to client.

### Technology

-   Express 4.17.1
-   bcryptjs 2.4.3
-   jsonwebtoken 8.5.1
-   Sequelize 5.21.3
-   MySQL

### Project Structure

This is directory structure for our Node.js Express application:

![react-express-authentication-jwt-example-server-project-structure](https://bezkoder.com/wp-content/uploads/2020/03/react-express-authentication-jwt-example-server-project-structure.png)

– **config**

-   configure MySQL database & Sequelize
-   configure Auth Key

– **routes**

-   _auth.routes.js_: POST signup & signin
-   _user.routes.js_: GET public & protected resources

– **middlewares**

-   _verifySignUp.js_: check duplicate Username or Email
-   _authJwt.js_: verify Token, check User roles in database

– **controllers**

-   _auth.controller.js_: handle signup & signin actions
-   _user.controller.js_: return public & protected content

– **models** for Sequelize Models

-   _user.model.js_
-   _role.model.js_

– _server.js_: import and initialize neccesary modules and routes, listen for connections.


## Front-end with React, React Router

### Overview

Let’s look at the diagram below.

![react-express-authentication-jwt-example-react-components](https://bezkoder.com/wp-content/uploads/2020/03/react-express-authentication-jwt-example-react-components.png)

– The `App` component is a container with React Router (`BrowserRouter`). Basing on the state, the navbar can display its items.

– `Login` & `Register` components have form for data submission (with support of `react-validation` library). They call methods from `auth.service` to make login/register request.

– `auth.service` methods use `axios` to make HTTP requests. Its also store or get **JWT** from Browser Local Storage inside these methods.

– `Home` component is public for all visitor.

– `Profile` component displays user information after the login action is successful.

– `BoardUser`, `BoardModerator`, `BoardAdmin` components will be displayed by state `user.roles`. In these components, we use `user.service` to access protected resources from Web API.

– `user.service` uses `auth-header()` helper function to add JWT to HTTP header. `auth-header()` returns an object containing the JWT of the currently logged in user from Local Storage.


If you want to use HttpOnly Cookie for storing JWT, please visit:  
[React.js Login & Registration example – JWT & HttpOnly Cookie](https://www.bezkoder.com/react-login-example-jwt-hooks/)


### Technology

We’re gonna use these modules:

-   React 16
-   react-router-dom 5
-   axios 0.19.2
-   react-validation 3.0.7
-   Bootstrap 4
-   validator 12.2.0

### Project Structure

This is folders & files structure for this React application:

![react-express-authentication-jwt-example-client-project-structure](https://bezkoder.com/wp-content/uploads/2020/03/react-express-authentication-jwt-example-client-project-structure.png)

With the explanation in diagram above, you can understand the project structure easily.