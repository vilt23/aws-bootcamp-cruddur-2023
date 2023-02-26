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
