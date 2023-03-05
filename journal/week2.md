# Week 2 — Distributed Tracing

### HoneyComb Configuration

#### I started by updating in the backend directory the file [requirement.txt](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/requirements.txt) with the prerequisite for honeycomb and execute them to set the environment for the upcoming work.
![requirement installation](assets/Week2/Week%202%20-%20requirement%20install.png)

Next in the python file [app.py](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/app.py) I imported the honeycomb librairies, iInitialize tracing and an exporter to send data to Honeycomb and initialize automatic instrumentation with Flask. Then I configured the environment variables in the file [docker-compose.yml](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/docker-compose.yml) after modifying the file [gitpod.yml](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/.gitpod.yml) to automatically open the necessary port when docker compose is up.

At last, I set the HoneyComb API_KEY and SERVICE_NAME and started receiving the date in my honeycomb account.

![honeycomb data](assets/Week2/Week%202%20-%20Honeycomb%20data.png)
