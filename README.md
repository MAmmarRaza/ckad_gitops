Concepts:

config maps
secrets
deployment
stateful sets
readiness probes
liveness probe
services
- headless service
- NodePort service
- Cluster IP
PV
PVC

# Kubernetes Blog Project

This project sets up a Kubernetes environment for a blog application using MongoDB as the database. It includes the necessary configurations for deploying MongoDB, MongoDB Express, and the blog application itself.

## Project Structure

```
kubernetes-project
├── manifests
│   ├── statefulset-mongodb.yaml       # StatefulSet configuration for MongoDB
│   ├── persistent-volume.yaml          # Persistent Volume configuration
│   ├── persistent-volume-claim.yaml    # Persistent Volume Claim configuration
│   ├── mongodb-express.yaml            # Deployment for MongoDB Express
│   ├── headless-service.yaml           # Headless service for MongoDB
│   ├── deployment-blog.yaml            # Deployment for the blog application
│   ├── service-blog.yaml               # Service for the blog application
│   ├── configmap.yaml                  # ConfigMap for application configuration
│   └── secret.yaml                     # Secret for sensitive information
└── README.md                           # Project documentation
```

## Setup Instructions

1. **Prerequisites**
   - Ensure you have a Kubernetes cluster running.
   - Install `kubectl` to interact with your Kubernetes cluster.

2. **Deploy MongoDB**
   - Apply the Persistent Volume and Persistent Volume Claim:
     ```
     kubectl apply -f persistent-volume.yaml
     kubectl apply -f persistent-volume-claim.yaml
     ```
   - Deploy MongoDB using the StatefulSet:
     ```
     kubectl apply -f statefulset-mongodb.yaml
     ```
   - Create the headless service for MongoDB:
     ```
     kubectl apply -f headless-service.yaml
     ```

3. **Deploy MongoDB Express**
   - Deploy MongoDB Express:
     ```
     kubectl apply -f mongodb-express.yaml
     ```

4. **Deploy the Blog Application**
   - Create the ConfigMap and Secret:
     ```
     kubectl apply -f configmap.yaml
     kubectl apply -f secret.yaml
     ```
   - Deploy the blog application:
     ```
     kubectl apply -f deployment-blog.yaml
     ```
   - Create the service for the blog application:
     ```
     kubectl apply -f service-blog.yaml
     ```

## Components Description

- **StatefulSet for MongoDB**: Manages the deployment and scaling of a set of Pods, providing guarantees about the ordering and uniqueness of these Pods.
- **Persistent Volume (PV)**: Represents a piece of storage in the cluster that has been provisioned by an administrator.
- **Persistent Volume Claim (PVC)**: A request for storage by a user.
- **MongoDB Express**: A web-based MongoDB admin interface.
- **Headless Service**: Allows direct access to the MongoDB Pods for service discovery.
- **Blog Application Deployment**: Manages the deployment of the blog application.
- **Service for Blog Application**: Exposes the blog application to the network.
- **ConfigMap**: Provides a way to inject configuration data into Pods.
- **Secret**: Used to store sensitive information securely.

## Accessing the Applications

After deploying the applications, you can access MongoDB Express through the service created for it. The blog application can be accessed via the service defined for it as well.