# Week 1 — App Containerization

### Docker extension installation
#### I installed the docker extension in my gitpod environment because it was missing
![Docker ext installation](assets/Week%201%20-%20Docker%20ext%20installation.png)

### Backend Containerization

#### I started by creating a docker file for backend flask app in the backend folder. I named the file [DockerFile](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/Dockerfile) 
I install the requirements for the backend flask using the command: pip3 install -r requirements.txt
![install requirements](assets/Week%201%20-%20Pip%20install%20requirements.png)

Next I set the environment variables FRONTEND_URL and BACKEND_URL then I execute the command to run the flask module on the desired port in the environment using Python 3.

![Port 4567 return](assets/Week%201%20-%20Port%204567%20return.png)

Then i build the docker backend image by running in project directory the following command : docker build -t  backend-flask ./backend-flask


### Frontend Containerization

#### I started by installing the dependencies in the frontend directory running: npm i. And follow by creating the docker file in that same directory named [DockerFile](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/frontend-react-js/Dockerfile)

### Creating the docker compose file

#### To allow me to run multiple containers at the same time, I created the docker compose file in the project directory folder and named it [docker-compose.yml](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/docker-compose.yml)
And executed docker compose by right clicking the yml file and selecting " Compose Up".

![Compose Up](assets/Week%201%20-%20Docker%20compose%20up.png)

### Creating notification feature
#### I edited the [openapi-3.0,yml](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/openapi-3.0.yml) file to insert the notification activity.
![openapi-3.0.yml](assets/Week%201%20-%20openapi.png)

I created the notification service for the backend by creating the python file [notifications_activities.py](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/services/notifications_activities.py) and imported it in the [app.py](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/backend-flask/app.py) file.
In the frontend folder I created the [NotificationsFeedPage.js](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/frontend-react-js/src/pages/NotificationsFeedPage.js) and mapped the the notification route in the [App.js](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/frontend-react-js/src/App.js) file. At the end I have been able to access the notification page in the website.

![Notification Page](assets/Week%201%20-%20Notifications%20page.png)

### Databases Installation

#### I implemented the Postgres and DynamoDB serrvices and referencing a volume in the file [docker-compose.yml](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/docker-compose.yml) in the project directory. I also installed the postgres client in the file [gitpod.yml](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/.gitpod.yml) in that same directory. Next I install the postgres client extension for vscode and tested if postgres was working.

![Postgres](assets/Week%201%20-%20PostgreSQL.png)
![DynamoDB](assets/Week%201%20-%20DynamoDB.png)


### Week Challenge

#### For the week challenge I tag the image of the backend and frontend containers in the gitpod environment and push them in my repo in DockerHub.

![Taging the containers](assets/Week%201%20-%20Docker%20tags.png)
![Pushing image in dockerhub](assets/Week%201%20-%20DockerHub.png)
