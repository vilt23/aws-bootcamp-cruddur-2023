# Week 3 — Decentralized Authentication
####This week is dedicated to decentralized authentication. We created AWS cognito Pools and immplemented it in the App. And experimented JWT token in the backend app. 


### Implementing Cognito in the App
#### First I created a cognito user pool in the aws console with email signin option with no MFA, making sure to include the attributes Name and preffered Username, selecting cognito email as message delivery method and set app client type to public.

![cognito poll](assets/week3/week%203%20-%20UserPool%20AWS%20Console.png)

Then I proceeded by installing aws-amplify in the environment. And making sure to import the amplify librairy in every js file it will be used.

![amplify install](assets/week3/Week%203%20-%20Amplify%20install.png)

![import amplify]()

The next step consisted to import the librairy and configure amplify in the file [App.js]() in the frontend directory 
![configure amplify in appjs](assets/week3/Week%203%20-%20Amplify%20AppJs.png)

And define the environment variables in the fille [docker-compose.yml]()
![docker compose env](assets/week3/Week%203%20-%20Env%20variables.png)

I also implemented anplify in the frontend page [HomeFeedPage.js]()
![HomeFeedPage.js](assets/week3/Week%203%20-%20Auth%20HomeFeedJs.png)

