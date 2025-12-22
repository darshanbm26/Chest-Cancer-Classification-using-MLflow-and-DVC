# Chest-Cancer-Classification-using-MLflow-and-DVC

## Workflows

1. Update config.yaml
2. Update secrets.yaml[optional]
3. Update params.yaml
4. Update the entity
5. Update the configuration manager in src config
6. Update the components
7. Update the pipeline
8. Update the main.py
9. Update the dvc.yaml

## MlFlow
* Documentation:https://mlflow.org/docs/latest/index.html
* cmd:mlflow ui

## Dagshub and MLflow bash

```bash

export MLFLOW_TRACKING_URI=

export MLFLOW_TRACKING_USERNAME=

export MLFLOW_TRACKING_PASSWORD=

```

## DVC Pipeline

 1. dvc init
 2. dvc repro
 3. dvc dag

## AWS CICD Deployement with Github ACtions
 1. Login to AWS Console
 2. Create IAM user for deployement
	
    #with specific access
	1. EC2 access : It is virtual machine
	2. ECR: Elastic Container registry to save your docker image in aws

	#Description: About the deployment
	1. Build docker image of the source code
	2. Push your docker image to ECR
	3. Launch Your EC2 
	4. Pull Your image from ECR in EC2
	5. Lauch your docker image in EC2

	#Policy:
	1. AmazonEC2ContainerRegistryFullAccess
	2. AmazonEC2FullAccess

 3. Create ECR repo to store/save docker image
    - Save the URI:

 4. Create EC2 machine(ubuntu)
 5. Open EC2 and Install docker in EC2 Machine:
	#optinal
	sudo apt-get update -y
	sudo apt-get upgrade
	#required
	curl -fsSL https://get.docker.com -o get-docker.sh
	sudo sh get-docker.sh
	sudo usermod -aG docker ubuntu
	newgrp docker
	
 6. Configure EC2 as self-hosted runner:
    setting>actions>runner>new self hosted runner> choose os> then run command one by one

 7. Setup github secrets:
    AWS_ACCESS_KEY_ID=
    AWS_SECRET_ACCESS_KEY=
    AWS_REGION = us-east-1
    AWS_ECR_LOGIN_URI =
    ECR_REPOSITORY_NAME =