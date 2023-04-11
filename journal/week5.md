# Week 5 — DynamoDB and Serverless Caching



I started by re organizing the bash script in the bin folder of the backend. I created 3 folders: the rds folder containg the update-sg-rule script, the db folder containing the postgres scripts and ddb folder where I will place the dynamoDB scripts. I also rename of the previous scrpits and modify their paths in the setup script and the gitpod.yml file. 

![re organize](assets/Week5/Week%205%20-%20v1%20re%20organize%20bin%20script.png)

![gitpod.yml](assets/Week5/Week%205%20-%20v1%20up%20rds%20script%20path%20in%20gitpod.png)

## Manage DynamoDB in the Gitpod Environment

I started by adding requirement boto in the backend file [requirements.txt](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/requirements.txt) and installed it using the command: pip install -r requirement.txt

![requirement.txt](assets/Week5/Week%205%20-%20v1%20boto3%20backend%20requierement.png)

I have installed the dynamoDB during week 1, the second week, of the bootcamp and referenced it the [docker-compose.yml]() file.This week, I created in the ddb folder of the bin folder in the backend the bash scripts [schema-load](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/bin/ddb/schema-load), [list-tables](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/bin/ddb/list-tables) and [drop](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/bin/ddb/drop). And made them executable. 

![schema-load](assets/Week5/Week%205%20-%20v1%20ddb%20schema%20load.png)

![list-tables](assets/Week5/Week%205%20-%20v1%20ddb%20list%20tables.png)

![drop](assets/Week5/Week%205%20-%20v1%20ddb%20drop%20script.png)

![chmod drop schema load](assets/Week5/Week%205%20-%20v1%20ddb%20schema%20load.png)

Next I executed the schema load and the list table bash scripts. And proceeded by running the drop bash script.

![load schema](assets/Week5/Week%205%20-%20v1%20ddb%20load%20schema.png)

![list tables](assets/Week5/Week%205%20-%20v1%20ddb%20list%20tables%20cli.png)

![drop tables](assets/Week5/Week%205%20-%20v1%20ddb%20drop%20table%20cli.png)

The next step consisted in modifying the backend /db/sql file [seed.sql]() to add the email colunm, create the bash script [seed]() to insert data in the database and also the bash script [scan]() to scan the local dynamoDB. Then I executed them.

![seed.sql](assets/Week5/Week%205%20-%20v1%20db%20update%20postgres%20seed%20run%20setup.png)

![scan](assets/Week5/Week%205%20-%20v1%20ddb%20scan%20bash%20script.png)

![seed cli](assets/Week5/Week%205%20-%20v1%20ddb%20see%20data%20cli.png)

![scan cli](assets/Week5/Week%205%20-%20v1%20ddb%20scan%20data%20cli.png)

Then after creating the folder pattern in the backend /bin/ddb directory, I implemented the bash scripts [get-conversation]() and modify some function to pass the needed parameter the other created script [list-conversations](). Then I made them executable and run the scripts.

![def funct db.py](assets/Week5/Week%205%20-%20v1%20db%20lib%20dbPy%20def%20function.png)

![print funct db.py](assets/Week5/Week%205%20-%20v1%20db%20lib%20dbPy%20update%20print%20function.png)

![querry array db.py](assets/Week5/Week%205%20-%20v1%20db%20lib%20dbPy%20update%20querry%20array%20func.png)

![querry object db.py](assets/Week5/Week%205%20-%20v1%20db%20lib%20dbPy%20update%20querry%20object.png)

![get-conversation](assets/Week5/Week%205%20-%20v1%20ddb%20pattern%20get%20conv%20cli.png)

![list-conversations](assets/Week5/Week%205%20-%20v1%20ddb%20pattern%20list%20conv%20cli.png)


## Implement conversations with DynamoDB

To start I created the librairy file [ddb.py](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/lib/ddb.py) with the dynamoDB functions and queries that will be needed. And in  the [aap.py](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/app.py) of the backend, I updated the sections messages groups, message_group_uuid and messages to use handles instead of hard coded values.

Then in the bin of the backend, I created the script [list-users](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/bin/cognito/list-users) in the cognito folder and the file [update_cognito_user_ids](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/bin/db/update_cognito_user_ids) in the db folder to populate the users. Then set the gitpod environment variable cognito pool ID and updated the setup script with the script [update_cognito_user_ids](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/bin/db/update_cognito_user_ids).

I updated the [docke-compose.yml]() file to run against local dynamoDB instead of the prod.

Next I updated the backend service [message_groups.py](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/services/message_groups.py) and [messages.py](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/services/messages.py) to use data in the database instead of mock data. And create the user query [uuid_from_cognito_user_id.sql](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/db/sql/users/uuid_from_cognito_user_id.sql) in the sql folder of db in the backend.

Then I updated the frontend pages [MessageGroupsPage.js](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/frontend-react-js/src/pages/MessageGroupsPage.js) and [MessageGroupPage.jsMessageGroupPage.js](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/frontend-react-js/src/pages/MessageGroupPage.js), and the frontend component [MessageForm.js ](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/frontend-react-js/src/components/MessageForm.js) with the bearer to handle page authentication.




