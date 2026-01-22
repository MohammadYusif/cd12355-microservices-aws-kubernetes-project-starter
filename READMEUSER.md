Coworking Analytics Microservice on AWS EKS

This project demonstrates deploying a containerized analytics microservice to AWS EKS using Docker, Amazon ECR, AWS CodeBuild, and Kubernetes.
The application is a Python Flask service that connects to a PostgreSQL database and exposes health and readiness endpoints for Kubernetes.

The source code is hosted on GitHub and integrated with AWS CodeBuild, which automatically builds the Docker image and pushes it to Amazon ECR upon code changes.
The Docker image is versioned and stored in ECR, then referenced by the Kubernetes deployment.

The application is deployed to an Amazon EKS cluster using Kubernetes manifests.
A Deployment manages the application pod lifecycle, while a LoadBalancer Service exposes the application externally.
Environment variables are split between a ConfigMap for non-sensitive values and a Secret for database credentials.

A separate PostgreSQL Deployment and Service are created inside the cluster to act as the application database.
The database schema and seed data are initialized using SQL scripts provided with the project.

The application implements /health_check and /readiness_check endpoints, which are used by Kubernetes liveness and readiness probes.
This ensures the service is only marked available when it can successfully communicate with the database.

Logs confirm that the application runs without errors and periodically queries the database, printing analytics results.
Application logs can be viewed using kubectl logs, and build logs are available in Amazon CloudWatch through the CodeBuild log group.

This project demonstrates a complete CI/CD workflow and a production-style Kubernetes deployment on AWS.
