[![CircleCI](https://circleci.com/gh/blackMkey/project-ml-microservice-kubernetes/tree/master.svg?style=svg)](https://circleci.com/gh/blackMkey/project-ml-microservice-kubernetes/tree/master)

## Project Overview

In this project, you will apply the skills you have acquired in this course to operationalize a Machine Learning Microservice API. 

You are given a pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). This project tests your ability to operationalize a Python flask app—in a provided file, `app.py`—that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

## Setup the Environment

* Create a virtualenv with Python 3.7 and activate it. Refer to this link for help on specifying the Python version in the virtualenv. 
```bash
python3 -m pip install --user virtualenv
# You should have Python 3.7 available in your host. 
# Check the Python path using `which python3`
# On windows
python3 -m venv ~/.devops
source ~/.devops/Scripts/activate
```
* Run `make install` to install the necessary dependencies

## install scoop and Hadolint
```bash
# install scoop on Powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
iwr get.scoop.sh | iex
# install hadolint
scoop install hadolint
```
## Setup docker, kubernetes, minikube
```bash
# install docker windows on https://docs.docker.com/desktop/windows/install/
# install kubernetes (require hyper-v) on page https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/
# install minikube using chocolatey (https://chocolatey.org/install)
choco install minikube
minikube start
minikube dashboard
```
## Explanation of some file in the repository
```
# App.py
simple flask app and it responsible for
 - Accepting an input JSON payload, and converting that into a DataFrame.
 - Scaling the DataFrame payload.
 - Passing the scaled data to a pre-trained model and getting back a prediction.

# run_docker.sh
build and run docker in local

# make_prediction.sh
open a separate tab or terminal window, then run it. 
it is responsible for sending some input data to your containerized application.
and in your main window, where it indicates that your application is running, you should see some log statements print out

#upload_docker.sh
upload your built image to docker

#run_kubernetes.sh
deploy your application on the Kubernetes cluster


```

### Running `app.py`

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
3. Run in Kubernetes:  `./run_kubernetes.sh`


