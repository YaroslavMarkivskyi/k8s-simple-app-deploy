# DEPLOYMENT WITH KUBERNETES
A RESTful API Built with FastAPI.
It features six key endpoints that facilitate interaction with a PostgreSQL database:

- GET **/**: Returns a simple text response.
- GET **/items/**: Retrieves a list of items from the database.
- POST **/items/**: Creates a new item in the database.
- PUT **/items/{item_id}**: Updates an existing item in the database.
- DELETE **/items/{item_id}**: Deletes an item from the database.
# Deployment Configuration
To support the Simple-App, several Kubernetes configuration files are utilized:
- **configmap.yaml**: Defines the configuration data required for connecting to the PostgreSQL database.
- **secret.yaml**: Stores sensitive information such as the database user and password.
- **api-deployment.yaml**: Specifies the deployment settings for the RESTful API.
- **hpa.yaml**: Configures Horizontal Pod Autoscaling to manage resource allocation.
- **ingress.yaml**: Manages external access to the API.
- **postgres-pv.yaml**: Defines the persistent volume for the PostgreSQL database.
- **postgres-deployment.yaml**: Configures the deployment of database pods.
- **service.yaml**: Establishes an internal service using Cluster IP for API and database connectivity via an ingress (NGINX load balancer).
- **values.yaml**: Outlines the properties necessary for deployment.
# Autoscaling Configuration
The API is designed to scale dynamically based on demand:

- **Minimum Pods**: 2
- **Maximum Pods**: 10

Resource Requests:

- **Memory**: 256Mi
- **CPU**: 250m

Resource Limits:

- **Memory**: 512Mi
- **CPU**: 500m

# Local Environment Setup
```bash
minikube start --cpus=4 --memory=8192 --driver=virtualbox
helm install app ./app
minikube addons enable ingress
minikube ip
```
