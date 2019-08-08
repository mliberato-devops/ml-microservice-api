[![CircleCI](https://circleci.com/gh/mliberato-devops/ml-microservice-api.svg?style=svg)](https://circleci.com/gh/mliberato-devops/ml-microservice-api)

## Project Overview

In this project, you will apply the skills you have acquired in this course to operationalize a Machine Learning Microservice API.

You are given a pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). This project tests your ability to operationalize a Python flask app—in a provided file, `app.py`—that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

### Project Tasks

Your project goal is to operationalize this working, machine learning microservice using [kubernetes](https://kubernetes.io/), which is an open-source system for automating the management of containerized applications. In this project you will:
* Test your project code using linting
* Complete a Dockerfile to containerize this application
* Deploy your containerized application using Docker and make a prediction
* Improve the log statements in the source code for this application
* Configure Kubernetes and create a Kubernetes cluster
* Deploy a container using Kubernetes and make a prediction
* Upload a complete Github repo with CircleCI to indicate that your code has been tested

**The final implementation of the project will showcase your abilities to operationalize production microservices.**

### Repo structure
The list below shows a small description for each file/directory in this repo:

- `.circleci` This hidden directory stores the config.yml for CircleCI.
- `kubernetes` Stores YAML files to create pods and deployments
- `model_data` Classifier already trained used to make predictions.
- `output_txt_files` Some log files
- `.gitignore` Gitignore
- `Dockerfile` Dockerfile to create image
- `Makefile` Makefile used to set up the development environment and tests.
- `README.md` The file you are reading
- `app.py` Flask application
- `make_prediction.sh` Make predictions by connecting to Machine Learning API
- `requirements.txt` Dependencies
- `run_docker.sh` Build, tag and run a container from Dockerfile
- `run_kubernetes.sh` Run docker container over kubernetes cluster
- `upload_docker.sh` Upload built image to Docker Hub

The `kubernetes` is a special folder in this repo. As described before, this folder stores the configuration for kubernetes pods and deployments in YAML format, which has a number of advantages [[ref]](https://www.mirantis.com/blog/introduction-to-yaml-creating-a-kubernetes-deployment/) over typing all parameters in a huge command line:

**Convenience:** You’ll no longer have to add all of your parameters to the command line

**Maintenance:** YAML files can be added to source control, so you can track changes

**Flexibility:** You’ll be able to create much more complex structures using YAML than you can on the command line

---

## Setup the Environment

* Create a virtualenv and activate it
* Run `make install` to install the necessary dependencies

### Running `app.py`

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
3. Run in Kubernetes:  `./run_kubernetes.sh`

### Kubernetes Steps

* Setup and Configure Docker locally
* Setup and Configure Kubernetes locally
* Create Flask app in Container
* Run via kubectl
