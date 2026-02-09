# Flask Web Application Deployment to AWS ECS (CI/CD with Jenkins)

## Overview
This project demonstrates a CI/CD pipeline for deploying a Flask web application to AWS ECS using Docker and Jenkins.

Due to AWS account suspension, the pipeline currently covers:
- Application containerization
- Docker image build automation using Jenkins
- CI best practices
- Deployment preparation for ECS and ECR

The architecture and pipeline are designed to be easily extended to AWS when credentials are available.

## Project Architecture
- Flask web application
- Docker for containerization
- Jenkins for CI automation
- Intended deployment target: AWS ECS (Fargate)
- Intended container registry: AWS ECR


## CI/CD Workflow (Current)
1. Developer pushes code to GitHub
2. Jenkins pipeline triggers automatically
3. Jenkins:
   - Checks out the repository
   - Builds the Docker image using a Dockerfile
   - Verifies the image build
4. Workspace is cleaned after execution


## Intended Deployment Workflow (AWS – Planned)
Once AWS access is restored, the pipeline will be extended to:
1. Authenticate Jenkins to AWS using IAM credentials
2. Push Docker image to AWS ECR
3. Register or update ECS task definition
4. Deploy updated task to ECS Fargate service
5. Serve application via Application Load Balancer

## Future Improvements

1.Push image to AWS ECR

2.  ECS task definition (YAML/JSON)

3. Blue/Green deployment

4. Terraform for infrastructure provisioning

5.  Secrets management via AWS SSM


## How to Run Locally
```bash
docker build -t flask-ecs-app -f docker/Dockerfile .
docker run -p 5000:5000 flask-ecs-app
