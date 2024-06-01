#Docker Hub

```
Once you have created a repository, you can start using docker push to push images.


```
## Process

```
docker logout

docker login

docker build -t <hub-user>/<repo-name>[:<tag>

docker tag <existing-image> <hub-user>/<repo-name>[:<tag>]

docker commit <existing-container> <hub-user>/<repo-name>[:<tag>]

docker push <hub-user>/<repo-name>:<tag>


```

## In Project Setup


### Create Dockerfile 

```

Dockerfile

From python:3.12.1

ENV PYTHONUNBUFFERED=1

WORKDIR /code

COPY requirement.txt .

RUN pip install -r requirement.txt

COPY . .

EXPOSE 8000

CMD python manage.py runserver 0.0.0.0:8000


```


### Create docker-compose-yaml

```
version: '3.9'

services:
  app:
    build: .
    volumes:
    - .:/django
    ports:
    - 8000:8000
    image: app:django
    container_name: container_name
    command: python manage.py runserver 0.0.0.0:8000


```


### Create docker-compose-yaml

**.dockerignore**
