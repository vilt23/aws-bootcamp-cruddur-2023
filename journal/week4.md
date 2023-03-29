# Week 4 — Postgres and RDS
This week is dedicated to explre AWS RDS by creating a Postgres database and integrating it with our application.

## Creating Cruddur Postgres database in AWS

I created a postgres database using CLI and specifying the name, indentifier, class, region, user and password.
![create postgres db](assets/Week4/Week%204%20-%20Create%20postgres%20db.png)

![db in console](assets/Week4/Week%204%20-%20DB%20AWS%20console.png)

## Creation and manipulation of Cruddur local Postgres DB

I created a postgres user in my local environment and list the databases of that environment.

![create local user](assets/Week4/Week%204%20-%20List%20of%20databases.png)

After that I set the connection variables for the environment
![env var set](assets/Week4/Week%204%20-%20Connection%20URL.png)

Next I create a list of bash files in the bin folder of the backend allowing to manipulate postgres in the local and in the AWS production environment when use with the argument "prod" with minimal overhead: the file [db-create](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/bin/db-create) to create the cruddur database, [db-drop](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/bin/db-drop) to drop cruddur database, [db-schema-load](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/bin/db-schema-load) to load the schema into the db based on the file [schema.sql](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/db/schema.sql) in the db folder of the backend. Then modify the bash files permissions to make them executable.

![db-create bash](assets/Week4/Week%204%20-%20DB%20create%20bash.png)

![db-drop bash](assets/Week4/Week%204%20-%20DB%20drop%20bash.png)

![db-schema-load bash](assets/Week4/Week%204%20-%20DB%20schema%20load%20bash.png)

![load schema sql](assets/Week4/Week%204%20-%20Create%20tables%20users%20and%20activities.png)

![Making bash files executable](assets/Week4/Week%204%20-%20Chmod.png)

Then I create 3 other bash scripts: the file[db-connect](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/bin/db-connect) to open connection with postgres, the file [db-session]() to monitor idle and active sessions in Postgress and [db-seed](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/bin/db-seed) to load data from the file [seed.sql](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/db/seed.sql) in the tables. Without forgetting to modify the bash file permission using chmod.

![db-connect](assets/Week4/Week%204%20-%20DB%20coneect%20and%20table%20listing.png)

![db-session](assets/Week4/Week%204%20-%20DB%20session%20bash.png)

![db-seed](assets/Week4/Week%204%20-%20DB%20seed%20bash.png)

![seed.sql](assets/Week4/Week%204%20-%20Seed%20SQL.png)

To continue, I created the bash script [db-setup](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/bin/db-setup) which is a combinaition of the previous scripts allowing to set the postgres environment by creatng the cruddur databse, the user and activity tables and also loading the schema and the seeds in db.

![db-setup](assets/Week4/Week%204%20-%20DB%20setup%20bash.png)

## Setting up postgres driver

I started by adding the binary and the pool psycopg for python in the file [requirement.txt](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/requirements.txt) and installing them. Next I create the lib python file [db.py](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/lib/db.py) to manage Postgres pool.

![requirement.txt](assets/Week4/Week%204%20-%20Requierement.png)

Then I added the connection var in the file [docker-compose.yml](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/docker-compose.yml)

![docker-compose.yml](assets/Week4/Week%204%20-%20Connection%20URL%20dockerCompose.png)

Next I updated the backend service file [home_activity.py](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/services/home_activities.py) to query the seed data in home page.

![home_activity.py seed](assets/Week4/Week%204%20-%20HomeActivitiesPy%20seed%20sql.png)

![home page seed](assets/Week4/Week%204%20-%20HomePage%20Seed%20data.png)

## Configure Gitpod connection to AWS 

I set production environment variable for the connecton URL. Then I created an inbound rule in the database security group to allow connection from my gitpod. Set another environment variable to collect Gitpod IP address everything it is launch. Created a bash script in the bin folder of the backend [rds-update-sg-rule](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/bin/rds-update-sg-rule) including the SG ID and the Rule ID to automatically update the security group with the new IP of the environment. Then update the file [gitpod.yml](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/.gitpod.yml) to execute it at startup.

![SG Inbound Rule](assets/Week4/Week%204%20-%20Inbound%20Rule%20AWS%20console.png)

![RDS update SG rule](assets/Week4/Week%204%20-%20RDS%20update%20sg%20rule.png)

![gitpod.yml command](assets/Week4/Week%204%20-%20Gitpod%20Postgres%20Command.png)

Then I tested the changes by connecting and loading the schema in AWS cruddur Postgres db in gitpod.

![pro connect](assets/Week4/Week%204%20-%20Prod%20schema%20load.png)


## Set up Cognito post confirmation lambda

I started by creating a lambda function in AWS using runtime Python 3.8
Next I created the file [cruddur-post-confirrmation.py](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/aws/lambdas/cruddur-post-confirrmation.py) in the lambda directory of the aws directory of gitpod. This code will later be deployed in the recently created lambda function of AWS. In the Environment variables of the configuration of the lambda function I defined the connection URL of the postgres database. Then I added a specific ARN layer to the function.

![create_lambda_function](assets/Week4/Week%204%20-%20Create%20lambda%20function.png)

![Lambda Env Var](assets/Week4/Week%204%20-%20Lambda%20env%20var.png)

![lambda layer](assets/Week4/Week%204%20-%20Add%20layer%20to%20lambda.png)

The next step consisted in adding a trigger in Cognito to pass the signup users informations to postgres at post confirmation level.

![Cognito lambda trigger](assets/Week4/Week%204%20-%20Cognito%20lambda%20trigger.png)

I modified the execution role of the the lambda function by attaching the a permission i have created to allow network interface management. Then comeback to connect the lambda function to the VPC.

![permissions](assets/Week4/Week%204%20-%20Create%20Policy%20Json.png)

![Attach permission to role](assets/Week4/Week%204%20-%20Attach%20Permission%20policy%20to%20role.png)

![Connect lambda to VPC](assets/Week4/Week%204%20-%20Add%20VPC%20to%20Lambda.png)

Next I signup a new user in the Cruddur app and run a query on the user table of the cruddur database in AWS to verify if the information have been passed.

![user table query](assets/Week4/Week%204%20-%20Select%20all%20from%20users.png)

## Creating activities

This final part consisted of modifying the backend service file [home_activity.py](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/services/home_activities.py), [create_activity.py](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/services/create_activity.py) and the librairy [db.py](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/lib/db.py) to allow any registered user to publish activities.

I also created the sql file [create.sql](), [home.sql]() and [object.sql]() with the queries for the db. And updated the code that will be deploy in lambda function in the file [cruddur-post-confirrmation.py](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/aws/lambdas/cruddur-post-confirrmation.py)

![create.sql](assets/Week4/Week%204%20-%20Db%20sql%20activities%20CreateSql.png)

![home.sql](assets/Week4/Week%204%20-%20Db%20sql%20activities%20homeSql.png)

![object](assets/Week4/Week%204%20-%20Db%20sql%20activities%20ObjectSql.png)

Then, in the frontend, I modified the ActivityForm in the page file [HomeFeedPage.js](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/frontend-react-js/src/pages/HomeFeedPage.js) and the body of component file [ActivityForm.js](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/frontend-react-js/src/components/ActivityForm.js) to pass the user_uuid to the backend file [app.py](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/app.py)

![ActivityForm HomeFeedPage.js](assets/Week4/Week%204%20-%20Update%20activity%20form%20in%20frontend%20homefeedPageJs.png)

![Body ActivityForm.js](assets/Week4/Week%204%20-%20Update%20body%20in%20frontend%20component%20ActivityFormJs.png)

![app.py](assets/Week4/Week%204%20-%20Insert%20request%20handler%20in%20app.py%20backend.png)

Allowing users to publish crud in the App

![publish crud](assets/Week4/Week%204%20-%20Posting%20cruds.png)

