# Kubernetes MongoDB and Mongo Express

This project sets up MongoDB and Mongo Express on a Kubernetes cluster using Minikube with the Docker driver.

## Prerequisites

- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- Docker

## Setup

1. **Start Minikube with Docker driver:**

    ```sh
    minikube start --driver=docker
    ```

2. **Apply the MongoDB Secret:**

    ```sh
    kubectl apply -f mongo-secret.yaml
    ```

3. **Apply the MongoDB Deployment and Service:**

    ```sh
    kubectl apply -f mongo.yaml
    ```

4. **Apply the ConfigMap for Mongo Express:**

    ```sh
    kubectl apply -f mongo-configmap.yaml
    ```

5. **Apply the Mongo Express Deployment and Service:**

    ```sh
    kubectl apply -f mongo-express.yaml
    ```

## Access Mongo Express

1. **Get the URL for Mongo Express:**

    ```sh
    minikube service mongo-express-service
    ```

2. Open the URL in your web browser to access Mongo Express.

## Cleanup

To delete the resources created by this project, run:

```sh
kubectl delete -f mongo-express.yaml
kubectl delete -f mongo-configmap.yaml
kubectl delete -f mongo.yaml
kubectl delete -f mongo-secret.yaml
```

## Notes

- Ensure that Minikube is running before applying the Kubernetes manifests.
- The `mongo-secret.yaml` file contains base64 encoded credentials for MongoDB.
- The `mongo-configmap.yaml` file contains the configuration for Mongo Express to connect to MongoDB.