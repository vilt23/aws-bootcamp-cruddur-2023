# Week 4 — Postgres and RDS
This week is dedicated to explre AWS RDS by creating a Postgres database and integrating it with our application.

## Creating Cruddur Postgres database in AWS

I created a postgres database using CLI and specifying the name, indentifier, class, region, user and password.
![create postgres db](assets/Week4/Week%204%20-%20Create%20postgres%20db.png)

![db in console](assets/Week4/Week%204%20-%20DB%20AWS%20console.png)

## Creation and manipulation of Cruddur local Postgres DB

Then I created a postgres user in my local environment and list the databases in that environment.
![create local user](assets/Week4/Week%204%20-%20List%20of%20databases.png)

After that I set the connection variables for the environment
![env var set](assets/Week4/Week%204%20-%20Connection%20URL.png)

Next I create a list of bash files in the bin folder of the backend allowing to manipulate postgres in the local and in the AWS production environment with minimal overhead: the file [db-create](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/bin/db-create) to create the cruddur database, [db-drop](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/bin/db-drop) to drop cruddur database, [db-schema-load](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/bin/db-schema-load) to load the schema into the db based on the file [schema.sql](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/db/schema.sql) in the db folder of the backend. Then modify the bash files permissions to make them executable.

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

To proceed, I set production environment variable for the connecton URL. Then I created an inbound rule in the database security group to allow connection from my gitpod. Set another environment variable to collect Gitpod IP address everything it is launch. Created a bash script in the bin folder of the backend [rds-update-sg-rule](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/bin/rds-update-sg-rule) including the SG ID and the Rule ID to automatically update the security group with the new IP of the environment. Then update the file [gitpod.yml](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/.gitpod.yml) to execute it at startup.

![SG Inbound Rule](assets/Week4/Week%204%20-%20Inbound%20Rule%20AWS%20console.png)

![RDS update SG rule](assets/Week4/Week%204%20-%20RDS%20update%20sg%20rule.png)

![gitpod.yml command](assets/Week4/Week%204%20-%20Gitpod%20Postgres%20Command.png)

Then I tested the changes by connecting and loading the schema in AWS cruddur Postgres db in gitpod.

![pro connect](assets/Week4/Week%204%20-%20Prod%20schema%20load.png)


