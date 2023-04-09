# DevOps-Assignment

This DevOps Assignment represents exactly the type of tasks which you might have to do as a DevOps Engineer at SmartCow. In this repo, you will find a simple Python - Flask Web App, which reads the current RAM and CPU usage and a React frontend which shows the statistics in the browser.

![](./img/readme.jpg)

## How to run?

The app is setup in a pretty standard way, just like most Python-React Apps.

### Python Backend
In the api directory, do the following. 
1. `pip install -r requirements.txt`
2. `python app.py`
3. Visit `http://localhost:8000/stats`



### React Frontend
In the sys-stats directory, do the following.
1. `npm install`
2. `npm start`

## Task 1 - Dockerize the Application

The first task is to dockerise this application - as part of this task you will have to get the application to work with Docker and Docker Compose. 


Hint/Optional - Create separate containers for different services like api and react-ui (static files served by nginx )  

It is expected that you create another small document/walkthrough or readme which helps us understand your thinking process behind all of the decisions you made. 

The only strict requirement is that the application should spin up with `docker-compose up --build` command. 

You will be evaluated based on the
* best practices
* ease of use
* quality of the documentation provided with the code
* Docker Compose files 




## Task 2 - Deploy on Cloud

Next step is to deploy this application to absolutely any cloud of your choice ( You can use the free-tier provided by the Cloud Providers and use the smallest instance available on free-tier ) . 

> Use IaC (Infrastructure as code) to spinup an instance ( e.g Ec2 in case of AWS ) . If you are comfortable with other Clouds like Azure / Google . 
please feel free to variabilize your terraform code as given in below example to achieve the instance creation . 



### Create EC2 Instance

Create an EC2 instance with a Linux based OS that is accessible over the internet via SSH.

### Inputs
The following inputs should be accepted:

- **Region**: AWS region where the instance will be deployed
- **KeyName**: Name of the SSH key to be installed on the instance
- **InstanceType**: EC2 instance type (i.e size of the instance)
- **SubnetId**: ID of the subnet where the instance will be deployed
- **VpcId**: ID of the VPC where the instance will be deployed

### Outputs
The following outputs should be produced:

- **InstanceId**: ID of the newly created instance
- **PublicIpAddress**: publicly accessible ip address as an output

### Example

```sh
# Reformat Terraform configuration to follow a consistent standard
$ terraform fmt -check=true -diff

# Initialize the terraform working directory
$ terraform init

# Validate terraform
$ terraform validate

# Dry-run
$ terraform plan \
    -var region=${AWS_REGION} \
    -var key_name=${AWS_KEY_NAME} \
    -var instance_type=${AWS_INSTANCE_TYPE} \
    -var subnet_id=${AWS_SUBNET_ID} \
    -var vpc_id=${AWS_VPC_ID} \
    -out=plan.tfplan

# Apply
$ terraform apply -auto-approve \
    -var region=${AWS_REGION} \
    -var key_name=${AWS_KEY_NAME} \
    -var instance_type=${AWS_INSTANCE_TYPE} \
    -var subnet_id=${AWS_SUBNET_ID} \
    -var vpc_id=${AWS_VPC_ID}

...

Outputs:

InstanceId = xxxxx
PublicIpAddress = x.x.x.x
```


### Deploy App

- It's important to remember here that the application is already containerize, maybe you could deploy it to the instance created running them on docker or any containerization platform .

- There could be challenges with the Api being not reachable from UI because the sys-stats UI code is compiled with localhost references . 
Please review the (sys-stats/src/App.js) code and make appropriate changes and recreate the UI images before  deploying in cloud.



The React App should be accessible on a public URL, that's the only hard requirement. 




Use the best practices for exposing the cloud VM to the internet, block access to unused ports, add a static IP (elastic IP for AWS),  Write a small document to explain your approach.

You will be evaluated based on the

* best practices
* terraform code
* Working Public Url serving the app.
* quality of the documentation provided with the code







### Task 3 - Get it to work with Kubernetes ( Optional )

Next step is completely separate from step 2. Go back to the application you built in Stage 1 and get it to work with Kubernetes.

Separate out the two containers into separate pods, communicate between the two containers, add a load balancer (or equivalent), expose the final App over port 80 to the final user (and any other tertiary tasks you might need to do)

Add all the deployments, services and volume (if any) yaml files in the repo.

The only hard-requirement is to get the app to work with `minikube`

## Summary

This documentation is supposed to be very high-level, you will be evaluated on the basis of the low level decisions you make while implementing it and your thought process behind them. If you have any questions at all feel free to reach out and ask for help.

Best of luck!

PS Please package your code up in a Github repo and share the link



