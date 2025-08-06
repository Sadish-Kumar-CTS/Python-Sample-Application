# Python CI/CD Pipeline with GitHub Actions and ECR

This repository contains a Python Flask application with CI/CD pipeline that builds Docker images and pushes them to Amazon ECR.

## Setup Instructions

### 1. Create ECR Repository
```bash
aws ecr create-repository --repository-name python-app --region us-east-1
```

### 2. Configure GitHub Secrets
Add these secrets to your GitHub repository:
- `AWS_ACCESS_KEY_ID` - Your AWS access key
- `AWS_SECRET_ACCESS_KEY` - Your AWS secret key

### 3. Update Configuration
In `.github/workflows/ci.yml`, update:
- `AWS_REGION` - Your preferred AWS region
- `ECR_REPOSITORY` - Your ECR repository name

### 4. Pipeline Triggers
The pipeline runs on:
- Push to `main` or `develop` branches
- Pull requests to `main` branch

## Local Development
```bash
pip install -r requirements.txt
python app.py
```

## Docker Build
```bash
docker build -t python-app .
docker run -p 5000:5000 python-app
```

## Application Endpoints
- `/` - Hello message
- `/health` - Health check endpoint