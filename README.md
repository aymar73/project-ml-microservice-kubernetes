[![aymar73](https://circleci.com/gh/aymar73/project-ml-microservice-kubernetes.svg?style=svg)](https://github.com/aymar73/project-ml-microservice-kubernetes/tree/master)

## Project Overview


In this project, a pre-trained `sklearn` model that has been trained to predict housing prices in Boston according to several features is deployed. The model is trained with the data set published in Kaggle site. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). We will operationalize a Python flask app in file `app.py` that serves out predictions (inference) about housing prices through a flask python application, containerized using docker, and deployed locally using kubernetes for testing and debugging purposes. The quality of the code is tested by importing the project repo into CircleCI.

This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.
  
## Cloning the repository
  
* To get the starting project files, it is recommended that you clone the Github repository, then work locally and push your complete project to a new, Github repository of your own. Alternatively, you could download the code as a zip file.
To clone this repository from a command line or terminal, you should navigate to a directory where you want to save this repository and then copy-paste this command:

git clone git@github.com:aymar73/project-ml-microservice-kubernetes.git

Then navigate to the downloaded project directory using the following command:

cd project-ml-microservice-kubernetes.git

This should get you into the main working project directory that has all the files. You can test that you are in the correct directory by seeing if you can access one of the project files from the command line. You can type cat Makefile to see the starting Makefile in the project directory, for example.

The yaml file in the CircleCI directory tests your code.

These instructions assume you have git installed for working with Github from a terminal window, but if you do not, you can download that first from this [Github installation page](https://www.atlassian.com/git/tutorials/install-git).

## Creating and activating an Environment

The commands used in this project have been tested in a ubuntu 18-04 based machine. After cloning the repo, you need to setup an isolated environment by:

  1. python3 -m venv ~/.devops (or name it whatever you want)
  2. source ~/.devops/bin/activateWhile you still have your environment activated, you will still need to install:

### Installing dipendencies

Run `make install` while on your project directory on the terminal to install the necessary dependencies. The Makefile includes instructions on environment setup and lint tests. The dependencies are listed in the requirements.txt; these can be installed using pip commands in the provided Makefile

There are a couple of other libraries that you'll be using, which can be downloaded as specified, below.

## Other libraries

While you still have your environment activated, you will still need to install:

* Docker
* Hadolint
* Kubernetes (Minikube)

## Docker

You will need to use Docker to build and upload a containerized application. 

  1. you will need to create [a free docker account](https://hub.docker.com/), where you’ll choose a unique username and link your email to a docker account. Your username is your unique docker ID.
  2. To install the latest version of docker, choose the Community Edition (CE) for your operating system, [on docker’s installation site](https://docs.docker.com/get-docker/). It is also recommended that you install the latest, stable release.
  3. After installation, you can verify that you’ve successfully installed docker by printing its version in your terminal:
  
                                                   ![](C:\Users\aymar\Desktop\Aymar\Jenkins-project\Jenkins-Project\docker--version.png)
  
### Usage Steps

* To run the file in a Docker container, you need to setup and configure Docker locally. The Dockerfile includes the instructions of how to containerize app.py.

* To run the app in a local Kubernetes cluster you need to setup and configure Kubernetes locally through a VM and minikube. To make a prediction, you have to open a separate tab or terminal window. In this new window, navigate to the main project directory and call `./make_predictions.sh` while the app is up. In the prediction window, you should see the value of the prediction, and in your main window, where it indicates that your application is running, you should see some log statements print out. docker_out.txt and kubernetes_out.txt give a preview of the expected output of running the app in Docker and Kubernetes, respectively. Running `./upload_docker.sh` allows us to upload and share the created image in the Docker hub.

* Create Flask app in Container.

* To run via kubectl and deploy this application, you need to define a dockerpath, to run the docker container with kubectl by specifying a container and a port, and to forward the container port to a host port, using the same ports as those in the Dockerfile and `./make_predictions.sh`.

 The directory .circleci has config.yml, a configuration file that includes the necessary instructions to setup a CICD pipeline to fully automate the process.
