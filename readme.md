# k8-node-deployment-example

This repository serves as a clear, practical example of how to containerize a simple Node.js application and deploy it to a Kubernetes (k8s) cluster. It's designed for developers and DevOps engineers who are new to Kubernetes and want to understand the core concepts of **Deployments** and **Services**.

## Why This Example?

This project breaks down the essential steps of a cloud-native workflow:
* **Containerization**: Using a `Dockerfile` to package a Node.js application.
* **Deployment**: Defining an application's desired state using `Deployment` manifests.
* **Service Exposure**: Making the application accessible using a `Service` and a `LoadBalancer`.

## Project Structure