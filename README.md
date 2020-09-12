[![aymar73](https://circleci.com/gh/aymar73/project-ml-microservice-kubernetes.svg?style=svg)](https://github.com/aymar73/project-ml-microservice-kubernetes/tree/master)

## Project Overview


In this project, a pre-trained `sklearn` model that has been trained to predict housing prices in Boston according to several features is deployed. The model is trained with the data set published in Kaggle site. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). We will operationalize a Python flask app—in file, `app.py`—that serves out predictions (inference) about housing prices through a flask python application, containerized using docker, and deployed locally using kubernetes for testing and debugging purposes. The quality of the code is tested by importing the project repo into CircleCI.

This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

## Setup the Environment

The commands used in this project have been tested in a ubuntu 18-04 based machine. You need to clone the repo, setup an isolated environment by:

* Create a virtualenv and activate it:
  1. python3 -m venv ~/.devops (or name it whatever you want)
  2. source ~/.devops/bin/activate
  
* Run `make install` to install the necessary dependencies. The Makefile includes instructions on environment setup and lint tests. The dependencies are listed in the requirements.txt.

To run the application, you have a choice between the options listed below.

### Running `app.py`

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`, to run and build a docker image.
3. Run in Kubernetes:  `./run_kubernetes.sh`

### Usage Steps

* To run the file in a Docker container, you need to setup and configure Docker locally. The Dockerfile includes the instructions of how to containerize app.py.

* To run the app in a local Kubernetes cluster you need to setup and configure Kubernetes locally through a VM and minikube. To make a prediction, you have to open a separate tab or terminal window. In this new window, navigate to the main project directory and call `./make_predictions.sh` while the app is up. In the prediction window, you should see the value of the prediction, and in your main window, where it indicates that your application is running, you should see some log statements print out. docker_out.txt and kubernetes_out.txt give a preview of the expected output of running the app in Docker and Kubernetes, respectively. Running `./upload_docker.sh` allows us to upload and share the created image in the Docker hub.

* Create Flask app in Container.

* Run via kubectl: to deploy this application using kubectl, you need to define a dockerpath, to run the docker container with kubectl by specifying a container and a port, and to forward the container port to a host port, using the same ports as those in the Dockerfile and `./make_predictions.sh`
