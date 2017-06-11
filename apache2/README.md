# docker

## How to Build Image
docker build -t docker/apache2:v1 .

## Run Container (change $DIR to base dir of Git Repo)
docker run -it --name apache2 -p 80:80 -v $DIR/docker/cgi-bin:/usr/local/apache2/cgi-bin -v $DIR/docker/html:/usr/local/apache2/html docker/apache2:v1 &


## Run Interacive Shell in Separate Window
docker exec -it apache2 /bin/bash

## Testing
open page http://localhost/cgi-bin/main.cgi in browser
