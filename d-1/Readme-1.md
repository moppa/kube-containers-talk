docker build -t d-1 .

docker run -it --rm d-1

docker run -d -p 1234:80 d-1

--name mycontainer

docker stop 
docker stop -t 0

docker ps -a

docker rm

docker run -it --rm -p 1234:80 -e MY_VAR="My Custom VAR" d-1


docker run -d --rm --name mycontainer -p 1234:80 -v $PWD/custom:/usr/share/nginx/html d-1

docker exec -it mycontainer /bin/bash

docker pull ubuntu:jammy

docker rmi 
docker image prune -a


