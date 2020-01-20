# django-mongo
mkdir django-mongo
cd django-mongo
mkdir mongo-database

---------------------------------
django-mongo --> is the main project folder
---------------------------------
vim .dockerignore
---------------------------------
	.dockerignore
	mongo-database/
	Dockerfile
---------------------------------
vim Dockerfile
---------------------------------
	FROM django
	MAINTAINER Omkar Yadav <omkarsyadav26@gmail.com>
	ADD . /django-app
	WORKDIR /django-app
	RUN pip install -r requirements.txt
	CMD [ "python", "./app.py runserver 0.0.0.0:8000" ]
---------------------------------
	
	docker network create container-connect

	docker run -d -v ~/home/ec2-user/django-mongo/mongo-database:/data/db --network container-connect --name mongo-server mongo:latest

	docker run -d --network container-connect -e ME_CONFIG_MONGODB_SERVER=mongo-server -p 8081:8081 mongo-express

	docker build -t django-app .

	docker run --name django-app --network container-connect -e ME_CONFIG_MONGODB_SERVER=mongo-server -p 8000:8000 -d django-app
----------------------------------
port --> 8080 to connect django app

port --> 8081 to connect to mongo-express ui
