[![Build Status](https://api.travis-ci.org/DigiKlausur/docker-stacks.svg?branch=master)](https://travis-ci.org/DigiKlausur/docker-stacks)

## Single user images
The minimal single user image `minimal-notebook` is based on [jupyter/minimal-notebook](https://github.com/jupyter/docker-stacks/blob/master/minimal-notebook/Dockerfile).
* `notebook` image is used for teaching environment
* `restricted-notebook` is used for examination environment

## Run the image locally
```
docker run -it --name notebook --rm -p 8888:8888 digiklausur/notebook:latest
``` 
* Attach host host directory to the container
  ```
  docker run -it --name notebook -v /home/myhome:/home/jovyan/myhome --rm -p 8888:8888 digiklausur/notebook:latest

  ```
* Run the container in the background
  ```
  docker run -it --name notebook -v /home/myhome:/home/jovyan/myhome --rm -d -p 8888:8888 digiklausur/notebook:latest
  ```

* Open browser and go to localhost:8888
* Enter the notebook token if asked
  
  If you run docker in the background, you can get the log and the notebook token by

  ```
  docker logs --follow notebook
  ```
