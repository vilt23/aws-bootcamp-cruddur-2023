# Week 4 — Postgres and RDS
This week is dedicated to explre AWS RDS by creating a Postgres database and integrating it with our application.

## Creating Postgres database in AWS

I created a postgres database using CLI and specifying the name, indentifier, class, region, user and password.
![create postgres db](assets/Week4/Week%204%20-%20Create%20postgres%20db.png)

![db in console](assets/Week4/Week%204%20-%20DB%20AWS%20console.png)

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

Then I create 2 other bash scripts: the file[db-connect](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/bin/db-connect) to open connection with postgres and [db-seed](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/bin/db-seed) to load data from the file [seed.sql](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/db/seed.sql) in the tables. Without forgetting to modify the bash file permission using chmod.

![db-connect](assets/Week4/Week%204%20-%20DB%20coneect%20and%20table%20listing.png)

![db-seed](assets/Week4/Week%204%20-%20DB%20seed%20bash.png)

