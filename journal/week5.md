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

