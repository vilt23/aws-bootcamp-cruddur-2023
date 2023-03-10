# Week 2 — Distributed Tracing

### HoneyComb Configuration

#### I started by updating in the backend directory the file [requirement.txt](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/requirements.txt) with the prerequisite for honeycomb and execute them to set the environment for the upcoming work.
![requirement installation](assets/Week2/Week%202%20-%20requirement%20install.png)

Next in the python file [app.py](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/app.py) I imported the honeycomb librairies, iInitialize tracing and an exporter to send data to Honeycomb and initialize automatic instrumentation with Flask. Then I configured the environment variables in the file [docker-compose.yml](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/docker-compose.yml) after modifying the file [gitpod.yml](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/.gitpod.yml) to automatically open the necessary port when docker compose is up.

At last, I set the HoneyComb API_KEY and SERVICE_NAME and started receiving the date in my honeycomb account.

![honeycomb data](assets/Week2/Week%202%20-%20Honeycomb%20data.png)

### Instrument X-Ray

#### First I set the environment variable AWS-REGION in gitpod. Next I inserted the command to install x-ray sdk in the file [requierement.txt](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/requirements.txt) in the backend directory and installe the requierment for the environment.
Then of importing the necessary python librairies and defining the segment in the file [app.py](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/app.py).
The next step consisted of creating the file [xray.json](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/aws/json/xray.json) in the aws/json directory that will be use to create the cruddur sampling rule. Then creating the x-ray trace group in aws using the cli.

![xray group](assets/Week2/Week%202%20-%20create%20aws%20service%20group.png)

![xray group console](assets/Week2/Week%202%20-%20AWS%20xray%20trace%20group.png)

Right after i created the xray sampling group using the cli.

![sampling group](assets/Week2/Week%202%20-%20Sample%20group.png)

![consolo sampling group](assets/Week2/Week%202%20-%20Console%20Sample%20group.png)

 And to finish I added the Deamon Service to file [docker-compose.yml](https://github.com/omenking/aws-bootcamp-cruddur-2023/blob/week-2-rollbar/docker-compose.yml). Then I imported xray recorder and set up the segment recorder for the home page and the user activities section in the file [app.py](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/app.py)to capture events.In the python file [user_activities.py](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/services/user_activities.py) of the backend's services I implemented the segment and the mock-data subsegment of the activity page while making sure to close the subsegment. After this I run a compose up to launch the updated version of the app and started to log traces activities in my console.
 
 ![traces](assets/Week2/Week%202%20-%20Console%20xray%20traces.png)
 
 
 ![subsegment](assets/Week2/Week%202%20-%20xray%20user%20activity%20sub%20segment.png)
 
 

