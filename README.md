[![CircleCI](https://circleci.com/gh/mliberato-devops/ml-microservice-api.svg?style=svg)](https://circleci.com/gh/mliberato-devops/ml-microservice-api)

## Overview

In this project we operationalize a Machine Learning Microservice API. We'll use a pre-trained `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing).

This project operationalize a Python flask app that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

### Repo structure

The list below shows a small description for each file/directory in this repo:

- `.circleci` This hidden directory stores the config.yml for CircleCI.
- `kubernetes` Stores YAML files to create kubernetes pods and deployments.
- `model_data` Classifier already trained used to make predictions.
- `output_txt_files` Some log files.
- `.gitignore` Gitignore.
- `Dockerfile` Dockerfile to create image.
- `Makefile` Makefile used to set up the development environment and tests.
- `README.md` The file you are reading.
- `app.py` Flask application.
- `make_prediction.sh` Make predictions by connecting to Machine Learning API.
- `requirements.txt` Dependencies.
- `run_docker.sh` Build, tag and run a container from Dockerfile.
- `run_kubernetes.sh` Run docker container over kubernetes cluster.
- `upload_docker.sh` Upload built image to Docker Hub.

The `kubernetes` is a special folder in this repo. As described before, this folder stores the configuration for kubernetes pods and deployments in YAML format, which has a number of advantages [[ref]](https://www.mirantis.com/blog/introduction-to-yaml-creating-a-kubernetes-deployment/) over typing all parameters in a huge command line:

**Convenience:** You’ll no longer have to add all of your parameters to the command line

**Maintenance:** YAML files can be added to source control, so you can track changes

**Flexibility:** You’ll be able to create much more complex structures using YAML than you can on the command line

## Pre-requisites

In order to running the Flask app we need first install Docker and Kubernetes locally. The instructions for that could be found [here](https://docs.docker.com/install/linux/docker-ce/debian/) and [here](https://kubernetes.io/docs/setup/learning-environment/minikube/). We also need Python3 installed.

## Setup the Environment and Running

Follow these steps to setup the local environment:

* Create a virtualenv using `make setup`
* Activate the virtualenv by type `source .devops/bin/activate`
* Run `make install` to install the necessary dependencies

### Running `app.py`

There are few options to run `app.py` application:

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh**
3. Run in Kubernetes:  `./run_kubernetes.sh**

The first option use a python installation to run `app.py`. The second option use `run_docker.sh` script to run the application into a docker container. This option first create a docker image based on the Dockerfile in current directory. Lastly, the third option use `run_kubernetes.sh` script which download a docker image from Docker Hub and deploy the application into a kubernetes cluster.

## License

**Note:** All files in this repository that were made by me, which includes scripts and configuration files, are under MIT License. However, in order to run and deploy this application we use third-party softwares each one with their own license. Please, check it out.

MIT License

Copyright (c) [2019] [[Matheus Liberato]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
