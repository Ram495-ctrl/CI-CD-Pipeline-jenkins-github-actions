# Jenkins CI/CD Pipeline for Flask Application
This repository demonstrates the setup of a Continuous Integration and Continuous Deployment (CI/CD) pipeline for a Python Flask web application using Jenkins. The pipeline automates the stages of building, testing, and deploying the application.

Table of Contents
- Project Overview
- Prerequisites
- Pipeline Workflow
- Project Structure
- Setup Guide
### Project Overview
This project uses Jenkins to build a CI/CD pipeline that automates testing and deployment for a simple Flask application. The pipeline performs the following steps:

1. Build - Installs dependencies.
2. Test - Runs unit tests for the application.
3. Deploy - Deploys the application to a production server or local environment.
Prerequisites
To run this pipeline, ensure you have the following:

Jenkins installed and configured.
- Python 3.8+ installed.
- Git installed for repository management.
- Flask installed as the application framework.
- A configured Jenkins Job with access to this repository.
- An EKS Cluster to Deploy the Application.
- Domain to To access the Loadbalancer endpoint securily.
- Pipeline Workflow
 The pipeline consists of the following stages:

1. Clone Repository - Clones this GitHub repository.
2. Install Dependencies - Uses pip to install dependencies specified in requirements.txt.
3. Run Tests - Executes unit tests to validate application integrity.
4. Build and Deploy - Deploys the Flask application on a target environment.
5. Install Dependencies
6. pip install -r requirements.txt

Coming Features:
- SMS / Email code verification
- QR code authentication sync
## Demo
![login](https://github.com/user-attachments/assets/aee32a0c-331a-4e05-98e6-580737d389eb)

![verify](https://github.com/user-attachments/assets/d166b7cb-fa55-4a34-9b78-a8ede86f2c05)

![2facode](https://github.com/user-attachments/assets/75e7017a-619c-45ed-9dc2-5133af53ec9d)


## Flask
### Localhost
```python -m flask run```
```http://127.0.0.1:5000```
