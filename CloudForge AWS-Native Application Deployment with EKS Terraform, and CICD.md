# AWS Cloud Engineering Practice Project

## Project Overview

This project deploys a containerized FastAPI application to Amazon EKS. The Docker image is stored in Amazon ECR. The app connects to Amazon RDS PostgreSQL using a connection pool. Infrastructure is managed with Terraform, and deployments are automated using GitHub Actions.

The purpose of this project is to practice core cloud engineering skills, including:

* CI/CD pipeline design
* Infrastructure as Code with Terraform
* Containerization with Docker
* Kubernetes deployment on Amazon EKS
* Database connectivity with Amazon RDS PostgreSQL
* Load balancing with AWS Application Load Balancer
* Troubleshooting Kubernetes, IAM, networking, and database issues

## Architecture Diagram

```text
Developer Laptop / GitHub Repository
            |
            v
GitHub Actions CI/CD Pipeline
            |
            v
Docker Image Build
            |
            v
Amazon Elastic Container Registry (ECR)
            |
            v
Amazon Elastic Kubernetes Service (EKS)
            |
            v
Kubernetes Deployment
            |
            v
Kubernetes Service
            |
            v
AWS Load Balancer Controller
            |
            v
Application Load Balancer (ALB)
            |
            v
FastAPI Application Pods
            |
            v
Amazon RDS PostgreSQL
```

## AWS Services Used

| AWS Service            | Purpose                                                  |
| ---------------------- | -------------------------------------------------------- |
| Amazon EKS             | Runs the Kubernetes cluster                              |
| Amazon ECR             | Stores the Docker image                                  |
| Amazon RDS PostgreSQL  | Hosts the application database                           |
| Amazon VPC             | Provides the network environment                         |
| Public Subnets         | Host internet-facing resources such as the load balancer |
| Security Groups        | Control inbound and outbound traffic                     |
| IAM                    | Manages permissions for users, nodes, and controllers    |
| Elastic Load Balancing | Exposes the application publicly through an ALB          |
| CloudWatch             | Stores logs and supports monitoring                      |
| AWS CLI                | Used to interact with AWS from PowerShell                |

## Technologies Used

| Tool           | Purpose                                                                   |
| -------------- | ------------------------------------------------------------------------- |
| FastAPI        | Python web framework for the API                                          |
| Docker         | Packages the application into a container image                           |
| Terraform      | Provisions AWS infrastructure as code                                     |
| Kubernetes     | Runs and manages containers                                               |
| kubectl        | Manages Kubernetes resources                                              |
| Helm           | Installs Kubernetes applications such as the AWS Load Balancer Controller |
| GitHub Actions | Automates build and deployment                                            |
| PostgreSQL     | Stores task data                                                          |
| PowerShell     | Windows terminal used for project commands                                |

## Application Description

The application is a simple Task API built with FastAPI.

Main endpoints:

```text
GET /health
GET /tasks
POST /tasks/{title}
```

The `/health` endpoint checks whether the application is running.

The `/tasks` endpoints test database connectivity by writing and reading task records from PostgreSQL.

## Containerization

The application is packaged using Docker.

The Dockerfile starts from a Python base image, installs the required dependencies, copies the application code, exposes port `8000`, and starts the FastAPI app with Uvicorn.

Example Docker workflow:

```powershell
docker build -t task-api:v1 .\app

$AWS_ACCOUNT_ID = (aws sts get-caller-identity --query Account --output text).Trim()
$ECR_REPO = "$AWS_ACCOUNT_ID.dkr.ecr.us-east-1.amazonaws.com/task-api"

docker tag task-api:v1 "${ECR_REPO}:v1"
docker push "${ECR_REPO}:v1"
```

Why this matters:

Containers make the application portable. The same application image can run on a developer laptop, in CI/CD, or inside Kubernetes.

## Infrastructure as Code

Terraform is used to create AWS infrastructure.

The infrastructure includes:

* VPC
* Subnets
* EKS cluster
* EKS managed node group
* RDS PostgreSQL database
* Security groups
* IAM roles
* CloudWatch log group

The project uses a structure that separates environment-specific configuration from reusable infrastructure logic.

```text
infra/
  modules/
    network/
    ecr/
    eks/
    rds/

  environments/
    dev/
      main.tf
      variables.tf
      terraform.tfvars
      outputs.tf

    prod/
      main.tf
      variables.tf
      terraform.tfvars
      outputs.tf
```

Why this matters:

This structure helps avoid repeating infrastructure code. Dev and prod environments can use the same infrastructure pattern but different values.

For example:

```text
dev = smaller and cheaper
prod = larger and more production-ready
```

## Terraform Commands

From the dev environment folder:

```powershell
Set-Location C:\Users\hp\Downloads\aws-cloud-practice-project\infra\environments\dev

terraform init
terraform fmt
terraform validate
terraform plan
terraform apply
```

Why each command matters:

| Command            | Purpose                                              |
| ------------------ | ---------------------------------------------------- |
| terraform init     | Downloads providers and modules                      |
| terraform fmt      | Formats Terraform files                              |
| terraform validate | Checks syntax and configuration                      |
| terraform plan     | Shows what Terraform will create, change, or destroy |
| terraform apply    | Creates or updates the infrastructure                |

## Kubernetes Objects Used

| Kubernetes Object | Purpose                                                  |
| ----------------- | -------------------------------------------------------- |
| Namespace         | Groups the application resources                         |
| ConfigMap         | Stores non-sensitive app configuration                   |
| Secret            | Stores sensitive values such as the database password    |
| Deployment        | Runs and manages the FastAPI pods                        |
| Service           | Provides a stable internal endpoint for the pods         |
| Ingress           | Defines how external HTTP traffic reaches the service    |
| IngressClass      | Connects the Ingress to the AWS Load Balancer Controller |

## Kubernetes Deployment Flow

The application is deployed to EKS using Kubernetes YAML files stored in the `k8s` folder.

```text
k8s/
  namespace.yaml
  configmap.yaml
  secret.yaml
  deployment.yaml
  service.yaml
  ingress.yaml
```

Deployment commands:

```powershell
Set-Location C:\Users\hp\Downloads\aws-cloud-practice-project

kubectl apply -f k8s\namespace.yaml
kubectl apply -f k8s\configmap.yaml
kubectl apply -f k8s\secret.yaml
kubectl apply -f k8s\deployment.yaml
kubectl apply -f k8s\service.yaml
kubectl apply -f k8s\ingress.yaml
```

Useful verification commands:

```powershell
kubectl get nodes
kubectl get pods -n task-api
kubectl get svc -n task-api
kubectl get ingress -n task-api
kubectl describe ingress task-api-ingress -n task-api
kubectl logs deployment/task-api -n task-api
```

## Load Balancer Setup

The AWS Load Balancer Controller is installed with Helm.

It watches Kubernetes Ingress resources and creates AWS Application Load Balancers.

Helm repository setup:

```powershell
helm repo add eks https://aws.github.io/eks-charts
helm repo update eks
```

Controller verification:

```powershell
kubectl get deployment -n kube-system aws-load-balancer-controller
kubectl logs deployment/aws-load-balancer-controller -n kube-system
```

Why this matters:

The Kubernetes Ingress by itself does not create an AWS load balancer. The AWS Load Balancer Controller connects Kubernetes to AWS Elastic Load Balancing.

## Application Testing

After the Ingress receives an ALB address, the application can be tested publicly.

Health check:

```powershell
curl.exe http://YOUR_ALB_DNS_NAME/health
```

Create a task:

```powershell
curl.exe -X POST http://YOUR_ALB_DNS_NAME/tasks/learn-aws
```

List tasks:

```powershell
curl.exe http://YOUR_ALB_DNS_NAME/tasks
```

PowerShell note:

Use `curl.exe` instead of `curl` because PowerShell may treat `curl` as an alias for `Invoke-WebRequest`.

## CI/CD Workflow

GitHub Actions is used to automate the build and deployment process.

The pipeline is designed to:

1. Check out the repository
2. Build the Docker image
3. Authenticate to AWS
4. Push the image to Amazon ECR
5. Update the Kubernetes deployment in Amazon EKS
6. Wait for the rollout to complete

CI/CD concept:

```text
CI = Continuous Integration
- Build the application
- Run checks
- Create the Docker image

CD = Continuous Delivery or Continuous Deployment
- Push the image to ECR
- Deploy the new image to EKS
```

Why this matters:

CI/CD reduces manual deployment steps, improves consistency, and makes deployments easier to repeat.

## Database and Connection Pooling

The FastAPI app connects to Amazon RDS PostgreSQL.

The application uses a database connection pool.

Why pooling matters:

Opening a new database connection for every request is inefficient. A connection pool keeps reusable database connections available.

Example concept:

```text
Request arrives
        |
        v
App borrows connection from pool
        |
        v
App runs query
        |
        v
Connection returns to pool
```

Connection pool settings used by the app:

```text
POOL_MIN=1
POOL_MAX=5
```

Important lesson:

```text
Total possible database connections = number of pods × max pool size per pod
```

Example:

```text
5 pods × 5 max connections = 25 possible database connections
```

This is important because setting the pool size too high can overwhelm the database, while setting it too low can cause slow requests or connection timeouts.

## Troubleshooting Scenarios Practiced

### Docker Desktop Not Running

Problem:

```text
failed to connect to the docker API
```

Cause:

Docker Desktop was not running or the Docker engine was unavailable.

Fix:

Start Docker Desktop and confirm:

```powershell
docker version
docker run hello-world
```

### Missing ECR Repository

Problem:

```text
Repository task-api does not exist
```

Cause:

The Docker image was pushed before the ECR repository was created.

Fix:

```powershell
aws ecr create-repository --repository-name task-api --region us-east-1
```

### Terraform Not Recognized

Problem:

```text
terraform is not recognized
```

Cause:

Terraform was not installed or not added to Windows PATH.

Fix:

Install Terraform using winget:

```powershell
winget install HashiCorp.Terraform
```

Then restart PowerShell and verify:

```powershell
terraform version
```

### ECR Repository Already Exists

Problem:

```text
RepositoryAlreadyExistsException
```

Cause:

The ECR repository was created manually, then Terraform tried to create it again.

Fix:

Remove or comment out the Terraform ECR resource, or import the existing repository into Terraform state.

### Unsupported Kubernetes Version

Problem:

```text
unsupported Kubernetes version
```

Cause:

The Terraform configuration used an EKS Kubernetes version that was no longer supported.

Fix:

Update the EKS cluster version in Terraform to a currently supported version.

### kubectl Authentication Error

Problem:

```text
You must be logged in to the server
```

Cause:

The local kubeconfig existed, but the IAM user was not authorized inside the EKS cluster.

Fix:

Use EKS access entries and associate an EKS access policy.

### Helm Not Recognized

Problem:

```text
helm is not recognized
```

Cause:

Helm was not installed or not in PATH.

Fix:

```powershell
winget install Helm.Helm
```

Then restart PowerShell and verify:

```powershell
helm version
```

### Ingress Address Blank

Problem:

```text
kubectl get ingress -n task-api
ADDRESS column is blank
```

Cause:

The AWS Load Balancer Controller could not create the load balancer.

Troubleshooting steps:

```powershell
kubectl describe ingress task-api-ingress -n task-api
kubectl logs deployment/aws-load-balancer-controller -n kube-system
```

### AWS Load Balancer Controller AccessDenied

Problem:

```text
AccessDenied: not authorized to perform elasticloadbalancing:DescribeLoadBalancers
```

Cause:

The AWS Load Balancer Controller did not have the required IAM permissions.

Fix:

Attach the AWS Load Balancer Controller IAM policy to the IAM role being used by the controller.

### PowerShell curl Error

Problem:

```text
A parameter cannot be found that matches parameter name 'X'
```

Cause:

PowerShell interpreted `curl` as `Invoke-WebRequest`.

Fix:

Use:

```powershell
curl.exe -X POST http://YOUR_ALB_DNS_NAME/tasks/learn-aws
```

## Lessons Learned

This project helped reinforce several important cloud engineering concepts.

### CI/CD

CI/CD automates the process of building, testing, and deploying applications. CI focuses on validating and building code, while CD focuses on delivering or deploying that code to an environment.

### Infrastructure as Code

Terraform makes infrastructure repeatable and easier to manage. Instead of manually creating cloud resources through the AWS Console, infrastructure can be defined, reviewed, version-controlled, and recreated using code.

### Containers vs Virtual Machines

Containers package an application and its dependencies while sharing the host operating system kernel. This makes containers lighter and faster than virtual machines, which include a full guest operating system.

### Kubernetes

Kubernetes manages containerized applications using objects such as Deployments, Services, ConfigMaps, Secrets, and Ingress. It helps with scaling, self-healing, service discovery, and rolling updates.

### AWS IAM

IAM is a major part of cloud troubleshooting. A Kubernetes resource may be configured correctly, but AWS actions can still fail if the controller or node role does not have the required IAM permissions.

### Database Troubleshooting

Database issues can come from wrong credentials, network rules, security groups, slow queries, or poor connection pool configuration. Connection pools must be sized carefully across all running application pods.

### Windows-Specific Learning

PowerShell commands sometimes differ from Linux/macOS commands. Important differences included:

```text
$env:AWS_REGION instead of $AWS_REGION
curl.exe instead of curl
New-Item instead of touch
Set-Location instead of cd
Backslashes in file paths
```

## Future Improvements

Possible improvements for this project include:

* Add automated tests to the GitHub Actions pipeline
* Use AWS Secrets Manager instead of Kubernetes Secrets
* Use IAM Roles for Service Accounts for the AWS Load Balancer Controller
* Add HTTPS with AWS Certificate Manager
* Add Route 53 DNS
* Add CloudWatch dashboards and alarms
* Add Horizontal Pod Autoscaler
* Add separate dev and prod environments
* Use private subnets for worker nodes and database
* Add Terraform remote state using S3 and DynamoDB locking
* Add database migrations with Alembic
* Add Prometheus and Grafana monitoring

## Interview Summary

This project demonstrates hands-on cloud engineering experience with AWS, Docker, Terraform, Kubernetes, CI/CD, and database troubleshooting.

A strong interview explanation:

```text
I built and deployed a containerized FastAPI application on AWS. I used Docker to package the app, Amazon ECR to store the image, Terraform to provision the infrastructure, Amazon EKS to run the application, and Amazon RDS PostgreSQL as the database. I exposed the application using Kubernetes Ingress and the AWS Load Balancer Controller. I also practiced troubleshooting issues related to Docker, Terraform, EKS authentication, IAM permissions, Kubernetes Ingress, and database connection pooling.
```

## Cleanup

To avoid ongoing AWS charges, delete Kubernetes resources and destroy the Terraform infrastructure when finished.

Delete Kubernetes resources:

```powershell
kubectl delete -f k8s\
```

Destroy Terraform infrastructure:

```powershell
Set-Location C:\Users\hp\Downloads\aws-cloud-practice-project\infra\environments\dev
terraform destroy
```

After cleanup, check the AWS Console for leftover resources such as:

* EKS clusters
* EC2 instances
* Load balancers
* Target groups
* RDS databases
* ECR repositories
* CloudWatch logs
* NAT gateways
* Elastic IPs
* EBS volumes
