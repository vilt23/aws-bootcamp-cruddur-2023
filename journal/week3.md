# Week 3 — Decentralized Authentication
#### This week is dedicated to decentralized authentication. We created AWS cognito Pools and immplemented it in the App. And experimented JWT token in the backend app. 


### Implementing Cognito in the App
#### First I created a cognito user pool in the aws console with email signin option with no MFA, making sure to include the attributes Name and preffered Username, selecting cognito email as message delivery method and set app client type to public.

![cognito poll](assets/week3/week%203%20-%20UserPool%20AWS%20Console.png)

Then I proceeded by installing aws-amplify in the environment. And making sure to import amplify or auth from aws-amplify librairy in every js file it will be used.

![amplify install](assets/week3/Week%203%20-%20Amplify%20install.png)

The next step consisted to import the librairy and configure amplify in the file [App.js](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/frontend-react-js/src/App.js) in the frontend directory 
![configure amplify in appjs](assets/week3/Week%203%20-%20Amplify%20AppJs.png)

And define the environment variables in the fille [docker-compose.yml](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/docker-compose.yml)
![docker compose env](assets/week3/Week%203%20-%20Env%20variables.png)

I also modified the authentication method using anplify in the frontend page [HomeFeedPage.js](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/frontend-react-js/src/pages/HomeFeedPage.js)
![Import auth homefeed](assets/week3/Week%203%20-%20Import%20HomeFeedJS.png)

![HomeFeedPage.js](assets/week3/Week%203%20-%20Auth%20HomeFeedJs.png)

Next I modified the authentification method to use amplify instead of the token in [ProfileInfo.js](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/frontend-react-js/src/components/ProfileInfo.js)

![Import auth ProfileInfo](assets/week3/Week%203%20-%20Import%20ProfileInfoJs.png)

![ProfileInfo.js](assets/week3/Week%203%20-%20Signout%20ProfileInfoJs.png)

I reconfigure the onsubmit function to use amplify auth in the page [signin.js](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/frontend-react-js/src/pages/SigninPage.js)
![signin.js](assets/week3/Week%203%20-%20SigninPage.png)

In the file [signup.js](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/frontend-react-js/src/pages/SignupPage.js) I modified the onsubmit function to use cognito instead of token after importing auth from aws-amplify.

![signup.js](assets/week3/Week%203%20-%20SignupJs.png)

In the file [confirmationPage.js](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/frontend-react-js/src/pages/ConfirmationPage.js) the functions resend_code and onsubmit has been modified.

![confirmationpage.js](assets/week3/Week%203%20-%20ConfirmationJS.png)

This allow the signup of the users in the app that will be store in AWS cognito pool and the signin of existing pool user.

![signuppage](assets/week3/Week%203%20-%20Signup%20page.png)

![signinpage](assets/week3/Week%203%20-%20Signin%20Error.png)

![userfeed](assets/week3/Week%203%20-%20Profile%20page.png)

And to finish, I modified the functions onsubmit_send_code and onsubmit_confirm_code in the file [recoverypage.js](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/frontend-react-js/src/pages/RecoverPage.js)

![recoverypage.js](assets/week3/Week%203%20-%20RecoveryPageJS.png)

THis allow to recover lost user password

![recoverypage](assets/week3/Week%203%20-%20Recovery%20page.png)

### Implement authentication to backendassets/week3/Week%203%20-%20BackEnd%20cognito%20id%20DockeComposeYML.png

#### To make the app more secure I need to protect the API endpoints by passing along the access token.

First I implemented the header in the backend file [homepage.js]()

![homepage.js](assets/week3/Week%203%20-%20Pass%20token%20from%20FrontEnd%20HomeFeedPageJS.png)

Then in the the file [app.py] I redefined the home section and the corse and the cognito jwt token of the backend

![home section](assets/week3/Week%203%20-%20backend%20home%20section%20AppJS.png)

![corse section](assets/week3/Week%203%20-%20Cors%20updae%20BackEnd%20AppPY.png)

![cognito jwt token](assets/week3/Week%203%20-%20CognitoJwtToken%20Backend%20AppPY.png)


Then I implemented the librairy [cognito_jwt_token.py]() in the lib directory of the backend. And insert Flask-AWSCognito in the [requirements.txt]() file to next be install in the environment.
To proceed, I integrated the nececssary backend environment variables in the file [docker-compose.yml]()

![docker-compose.yml](assets/week3/Week%203%20-%20BackEnd%20cognito%20id%20DockeComposeYML.png)
