# Terraform and Ansible
I have used Terraform as an Infrastructure as code (IaC) tool to provision my infrastructure on AWS. Provisioned infrastructure includes;
VPCs, EKS Clusters, Private and Public subnets, Internet Gateway, Routing Tables, SECURITY GROUP, etc.

# EKS Getting Started Guide Configuration

This is the full configuration from https://www.terraform.io/docs/providers/aws/guides/eks-getting-started.html

See that guide for additional information.

NOTE: This full configuration utilizes the [Terraform http provider](https://www.terraform.io/docs/providers/http/index.html) to call out to icanhazip.com to determine your local workstation external IP for easily configuring EC2 Security Group access to the Kubernetes servers. 

# Provision EKS Infrastructure on AWS using Terraform
terraform init
terraform plan
terraform apply
terraform destory

# Jenkins
Jenkins will enable us to achieve Continuous Integration and Continuous Deployment. Our Jenkins pipeline script  will ensure once the application is developed or modified it is automatically built using maven, tested using Selenium, validated using SonarQube. The build artifacts will be uploaded to Nexus Private aritifact repository. 
# GitHub

I also configured github-webhook so that once the source code is modified jenkins will srtigger a build.  
# Dockerfile
we are also using the created package (artifacts) to create a docker image for our application. Here docker is used for containerization.  
```docker
docker build -t daleyhub/springboot-app .
```
# Kubernetes Manifest files
This files will deploy a "Spring-boot-app" with a MongoDB. Our application and database is deployed using Replicat Set, ConFigMap, Ingress Controller, Secrets, PVC, StorageClass, HPA, and Cluster-Auto-Scaling.
We have also deployed Grafana and Prometheus using Helm Charts. This will monitor our applications, send alerts and as such we are going to achieve high availability.
```t
kubectl create deployment autoscaler-demo --image=nginx
kubectl get pods --all-namespaces | grep Running | wc -l
kubectl get nodes -o yaml | grep pods
kubectl scale deployment autoscaler-demo --replicas=20
```

# Build Project Using Maven

Maven is java based build tool to generate executable 

packages(jar, ear,war) for java based projects.

```bash
mvn clean package
```

## Create Docker Image
Docker is a containerization tool. Using docker we can deploy our applications as 

containers using docker images. Containers contain application code and also the software,

config files whatever is required for our application to run.

Create docker image using Dockerfile


```docker
docker build -t legah2045/springboot-app .
```

## Deploy Application Using EKS Cluster 

```kubectl apply 
kubectl apply -f spring-boot-app-deployment.yml
```

## List Docker Containers
```docker
docker ps -a
```


