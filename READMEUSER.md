Coworking Analytics Microservice (AWS + Kubernetes)

This project deploys a containerized analytics microservice to AWS using Docker, Amazon ECR, AWS CodeBuild, and Amazon EKS.
The service exposes health and readiness endpoints and periodically aggregates visit analytics data from a PostgreSQL database.

Docker images are built locally and via AWS CodeBuild, then stored in Amazon ECR.
CodeBuild is configured to automatically build and push images to ECR using a buildspec.yml file.

Kubernetes manifests define deployments and services for both the analytics application and the PostgreSQL database.
Application configuration is managed using Kubernetes ConfigMaps for non-sensitive values and Secrets for database credentials.

The PostgreSQL database runs inside the cluster and is exposed internally via a ClusterIP service.
Database tables and seed data are initialized using SQL scripts provided in the db/ directory.

The analytics service is exposed externally using a LoadBalancer service.
Liveness and readiness probes are configured to ensure proper health monitoring.

CloudWatch logs confirm that the application runs successfully and periodically outputs analytics data without errors.
The system demonstrates a complete containerized CI/CD and Kubernetes deployment workflow on AWS.
