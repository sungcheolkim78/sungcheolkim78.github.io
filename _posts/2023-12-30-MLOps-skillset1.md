---
title: 'MLOps Engineer Skillset'
date: 2023-12-30
category: ML
tags:
  - mlops
---

[Original article](https://medium.com/marvelous-mlops/mlops-roadmap-2024-ff4216b8bc62)

## Programming

### Python

Python is the primary language for machine learning and is essential for an MLOps engineer. To learn Python:

- Read "Python Crash Course, 3rd Edition: A Hands-On, Project-Based Introduction to Programming 3rd Edition" by Eric Matthes.
- Practice with LeetCode problems.
- Learn from courses like "Learn Python 3" and tracks like "Python fundamentals" and "Python programming".
- Understand installing Python, using virtual environments, and working with an IDE.

### Bash Basics & Command Line Editors

Familiarity with bash basics is necessary for adding steps to CI/CD pipelines and creating Dockerfiles.

- Read "The Linux Command Line, 2nd Edition" by William E. Shotts.
- Enroll in the Bash mastery course.
- Learn VIM, a widely used command-line editor, through the VIM beginners guide.

## Containerization and Kubernetes

### Docker

Docker is crucial for code development, model training, and endpoint deployment.

- Follow the Docker roadmap: [https://roadmap.sh/docker](https://roadmap.sh/docker).
- Learn Docker with tutorials like "Full docker tutorial by Techworld by Nana".

### Kubernetes

Kubernetes is essential for machine learning model training, model endpoint deployment, and serving dashboards.

- Follow the Kubernetes roadmap: [https://roadmap.sh/kubernetes](https://roadmap.sh/kubernetes).
- Learn Kubernetes with courses like "Kubernetes course by freecodecamp.com" and "Kubernetes mastery".

## Machine Learning Fundamentals

An MLOps engineer should have a basic understanding of machine learning models to work effectively with machine learning engineers and data scientists.

- Enroll in courses like [https://mlcourse.ai/](https://mlcourse.ai/) and read "Applied Machine Learning and AI for Engineers" by Jeff Prosise.

## MLOps Principles

MLOps engineers must understand MLOps principles and factors contributing to MLOps maturity.

- Read "Designing Machine Learning Systems" by Chip Huyen and "Introducing MLOps" by Mark Treveil 𝖺𝗇𝖽 Dataiku.
- Check out the MLOps maturity assessment.

## MLOps Components

MLOps platforms consist of various components, such as version control, CI/CD, orchestration, compute, serving, and feature stores.

- Read "ML Engineering with Python" by Andy McMahon.
- Enroll in suggested courses like the "Made with ML MLOps course" and "The full stack 7-steps MLOps framework".

### Version Control & CI/CD Pipelines

Git is the most popular version control system, and GitLab and GitHub are popular version control services.

- Read "Learning GitHub Actions" by Brent Laster and "Learning Git" by Anna Skoulikari.
- Enroll in tutorials and courses like "Git & GitHub for beginners" and "Taking Python to Production: A Professional Onboarding Guide".
- Learn about pre-commit hooks, which are essential for keeping your code neat and a part of your CI pipeline.

### Orchestration

Orchestration systems like Mage, Airflow, Kubeflow, and Metaflow are popular in machine learning engineering.

- Enroll in the "Introduction to Airflow in Python" course.
 
### Experiment Tracking and Model Registries

Experiment tracking is crucial for comparing model training runs. MLflow is the most popular tool for experiment tracking and model registry.

- Enroll in the MLflow Udemy course and the "End-to-end machine learning" course (MLflow piece).
 
### Data Lineage and Feature Stores

Feature stores help keep track of feature use and allow sharing of features across models. Use cloud providers' feature stores or open-source solutions like Feast.

- Enroll in the "Creating a feature store with Feast part 1, part 2, part 3" tutorial series.

### Model Training & Serving

Cloud-native solutions like AWS Sagemaker, Azure ML, and Vertex AI are popular for model training and serving. Consider using Kubernetes for model deployment if your organization supports it.

- Enroll in the "ML deployment k8s FastAPI" repository and "How to build machine learning app with FastAPI" tutorial series.

### Monitoring & Observability

Monitoring and observability are crucial parts of an MLOps platform. Use Prometheus and Grafana for ML system observability, and consider cloud providers' solutions or open-source tools like Evidently.ai or NannyML for ML-specific monitoring.

- Enroll in the "Mastering Prometheus and Grafana" course.

### Infrastructure as Code: Terraform

Terraform is a powerful IaC tool that makes your MLOps framework reproducible.

- Learn Terraform by following its roadmap and enrolling in relevant courses.