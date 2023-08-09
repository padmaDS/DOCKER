**Let us discuss about how to create docker images and containers practically..**

First of all we need to download Docker desktop application in our local system and need to login there.

Now we need to perform all the operations from VSCode IDE.

First we need to create any project completely. (Which contains every folders and files like source folder, config folder, __init__, logging, exception, DataIngestion,Datavalidation, Model building, Model evaluation,Artifacts, Training pipeline, testing pipeline, app.py / main.py, yaml file, requirements.txt .....etc.)

After successful excution of our project, now we need to create on Dockerfile. It consists of some commands

.....> FROM python:3.8-alpine              ##(it creates a base image for our docker from dockerhub using python:3.8-alpine)

.....> COPY ./app                          ##(it will copy all the folders and files of our current project to **app** folder, where we need to run our entire project)

.....> WORKDIR /app                        ##(Here we have to confirm that our working directory now is **app**)

.....> RUN pip install -r requirements.txt ##(it will install all the necessary libraries / dependencis)

.....> CMD python app.py                   ##(Using this command we can run our application)


**Some important commands we can rememeber while creating the docker image n container and pushing it to docker hub.**

Building the Docker image  -------------->>>  docker build -t welcome.app (for example we can take the name of our docker image as welcome.app)

To check whether our docker image is built / not  ------------>>>  docker images

Now we need to run our docker image on 2 ports mainly. Those are host port 5000 and container port 5000 ------->> docker run -p 5000:5000

To check how many containers are running          ---------------------->>> docker ps

If we want to stop the container             --------------->>> docker stop "container id"

Now we need to push this docker container into docker hub        ---------->>>>   docker login   (Remember that, we always logging in Docker Destop app while creating the docker image and container)

We can rename our docker image name[here, we took as welcome.app]

Here we have 2 ways are there to rename our docker image

**1st way**

first we need to remove current docker image and again building of docker image using this below command

for removing ------->>>      docker image rm -f welcome.app (our docker image name, what ever docker image we want to remove, we can use that name)

Again building ---------->>> docker build -t padmaDS/welcome.app  (here we need to specify in this format user name/docker image name, in order to identify, whom had created)

Now we can check our docker images as usual command -------->>>>>>>> docker images

**2nd way**  : using tag

docker tag padmaDS/welcome.app

We can also rename of docker image name if we want to rename.

docker tag padmaDS/welcome.app padmaDS/welcome.app1

**Finally we need to push our docker image**

docker push padmaDS/welcome.app:latest           (here latest represents the version of our docker image)





















