source venv/bin/activate

building image:
docker build --help

dont run ds
docker build [OPTIONS] PATH | URL |

<!-- Desktop/local_env/docker/demos/flask-sklearn-student-starter$ docker build --tag hello-world . -->
docker build --tag hello-world .

to see a list of images:
docker images

to run docker:
<!-- docker run --help -->
docker run hello-world

check localhost

to check weda smth is running:
docker ps

docker ps -a

start docker:
docker start [name of the image]

to stop:
docker stop [name of the image]
docker ps

to remove:
docker rm [name of image]

to run docker:
docker run -p 8080:80 --name hello -d hello-world

to check if it's running:
docker ps

to check the logs:
docker logs [name of the image]

docker logs --help

docker logs -f [name of the image]

docker images

go to docker hub site and create an img and copy ds:
docker push hugb2022/hello-world:tagname

from running docker images, tag is labelled as latest, let's change it:
docker tag hello-world hugb2022/hello-world

run:
docker images


then run:
docker push hugb2022/hello-world

refresh ur docker hub pg

to pull from docker hub:
let's 1st remove d initial one
docker rmi hugb2022/hello-world

docker pull hugb2022/hello-world

docker-compose:
docker-compose.yml

version: '2'

services:
    web:
        build:
            context:
            dockerfile: Dockerfile
        container_name: web
        ports:
            - "8080:80"

run:
docker-compose up -d
<!-- need to install docker-compose -->

to stop:
docker-compose down

database:
version: '2'

services:
    web:
        build:
            context:
            dockerfile: Dockerfile
        container_name: web
        ports:
            - "8080:80"

    db:
        image: mongo:3.6.2
        container_name: db
        volumes:
            - mongodb: /data/db
            - mongodb_config: /data/configdb
        ports:
            - 27027: 27017
        command: mongod

volumes:
    mongodb:
    mongodb_config: