# k8-node-deployment-example

This repository serves as a clear, practical example of how to containerize a simple Node.js application and deploy it to a Kubernetes (k8s) cluster. It's designed for developers and DevOps engineers who are new to Kubernetes and want to understand the core concepts of **Deployments** and **Services**.

## Why This Example?

This project breaks down the essential steps of a cloud-native workflow:
* **Containerization**: Using a `Dockerfile` to package a Node.js application.
* **Deployment**: Defining an application's desired state using `Deployment` manifests.
* **Service Exposure**: Making the application accessible using a `Service` and a `LoadBalancer`.

## Project Structure

```
├── Dockerfile                  # Instructions to build the Docker image
├── .dockerignore               # Files to exclude from the Docker image
├── kubernetes/
│   ├── deployment.yaml         # Defines the Pods and replica count (the "what")
│   └── service.yaml            # Defines how to access the application (the "how")
├── package.json                # Node.js project metadata and dependencies
└── server.js                   # The simple Node.js (Express) application
```

### Getting Started

1.  **Prepare the Node.js Application**
    Install the project dependencies:
    ```bash
    npm install
    ```

2.  **Build the Docker Image**
    Turn the application into a Docker image. Be sure to replace `tolgafiratoglu` with your own Docker Hub username:
    ```bash
    docker build -t tolgafiratoglu/k8-node-deployment-example:1.0 .
    ```

3.  **Push the Image to Docker Hub**
    Upload the image to a public registry:
    ```bash
    docker push tolgafiratoglu/k8-node-deployment-example:1.0
    ```

4.  **Deploy to Kubernetes**
    Ensure the `image` path in your `kubernetes/deployment.yaml` file is updated, then apply the manifest files:
    ```bash
    kubectl apply -f kubernetes/
    ```

5.  **Access the Application**
    If you're using a local cluster like **Minikube**, use this command to access your service:
    ```bash
    minikube service nodejs-app-service
    ```
    If you're using a cloud-based cluster (GKE, EKS, AKS, etc.), you can get the external IP address with this command:
    ```bash
    kubectl get service nodejs-app-service
    ```
    After that, navigate to the IP address in your browser or Postman.