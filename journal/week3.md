# Week 3 — Decentralized Authentication
#### This week is dedicated to decentralized authentication. We created AWS cognito Pools and immplemented it in the App. And experimented JWT token in the backend app. 


### Implementing Cognito in the App
#### First I created a cognito user pool in the aws console with email signin option with no MFA, making sure to include the attributes Name and preffered Username, selecting cognito email as message delivery method and set app client type to public.

![cognito poll](assets/week3/week%203%20-%20UserPool%20AWS%20Console.png)

Then I proceeded by installing aws-amplify in the environment. And making sure to import amplify or auth from aws-amplify librairy in every js file it will be used.

![amplify install](assets/week3/Week%203%20-%20Amplify%20install.png)

The next step consisted to import the librairy and configure amplify in the file [App.js]() in the frontend directory 
![configure amplify in appjs](assets/week3/Week%203%20-%20Amplify%20AppJs.png)

And define the environment variables in the fille [docker-compose.yml]()
![docker compose env](assets/week3/Week%203%20-%20Env%20variables.png)

I also modified the authentication method using anplify in the frontend page [HomeFeedPage.js]()
![Import auth homefeed](assets/week3/Week%203%20-%20Import%20HomeFeedJS.png)

![HomeFeedPage.js](assets/week3/Week%203%20-%20Auth%20HomeFeedJs.png)

Next I modified the authentification method to use amplify instead of the token in [ProfileInfo.js]()

![Import auth ProfileInfo](/assets/week3/Week%203%20-%20Import%20ProfileInfoJs.png)

![ProfileInfo.js](assets/week3/Week%203%20-%20Signout%20ProfileInfoJs.png)

I reconfigure the onsubmit function to use amplify auth in the page [signin.js]()
![signin.js](assets/week3/Week%203%20-%20SigninPage.png)

In the file [signup.js]() I modified the onsubmit function to use cognito instead of token after importing auth from aws-amplify.

![signup.js](assets/week3/Week%203%20-%20SignupJs.png)

In the file [confirmationPage.js]() the functions resend_code and onsubmit has been modified.

![confirmationpage.js](assets/week3/Week%203%20-%20ConfirmationJS.png)

This allow the signup of the users in the app that will be store in AWS cognito pool and the signin of existing pool user.

![signuppage](assets/week3/Week%203%20-%20Signup%20page.png)

![userfeed](assets/week3/Week%203%20-%20Profile%20page.png)

![signinpage](assets/week3/Week%203%20-%20Signin%20Error.png)

And to finish, I modified the functions onsubmit_send_code and onsubmit_confirm_code in the file [recoverypage.js]()

![recoverypage.js](assets/week3/Week%203%20-%20RecoveryPageJS.png)

THis allow to recover lost user password

![recoverypage](assets/week3/Week%203%20-%20Recovery%20page.png)
