# k8s-helm-portfolio
k8d Deployment of helm using helm

Sure! Here’s a `README.md` file for your Helm chart and Kubernetes deployment:

```markdown
# WebApp1 Helm Chart

This Helm chart deploys a Kubernetes application with a service and deployment for a web app called `portfolio`.

## Chart Details

This chart deploys a basic Kubernetes setup for the `portfolio` web application with the following components:

- **Deployment**: A Kubernetes Deployment to manage the application's containers and replicas.
- **Service**: A Kubernetes Service to expose the application to the outside world using a LoadBalancer.

## Prerequisites

- Kubernetes 1.16+
- Helm 3.x+

## Installation

To install the `portfolio` application using this Helm chart, follow the steps below:

### 1. Clone the Repository

If you haven't already, clone the repository that contains the Helm chart.

```bash
git clone <repository-url>
cd <repository-directory>
```

### 2. Install the Chart

You can install the chart into your Kubernetes cluster using the following Helm command:

```bash
helm install <release-name> ./path/to/your/chart
```

Example:

```bash
helm install portfolio-webapp ./charts/webapp1
```

This will deploy the `portfolio` application to your Kubernetes cluster using the values specified in `values.yaml`.

### 3. Verify the Deployment

You can verify the deployment by checking the pods and services in your Kubernetes cluster:

```bash
kubectl get pods
kubectl get svc
```

## Configuration

The values for this Helm chart can be configured in the `values.yaml` file.

### Key Values:

#### Deployment

- `kind`: The type of Kubernetes resource, usually `Deployment`.
- `deploymentname`: The name of the deployment (e.g., `portfolio-deployment`).
- `replicas`: The number of replicas to create for the application (e.g., `2`).
- `appname`: The name of the app (e.g., `portfolio`).
- `container.name`: The name of the container (e.g., `portfolio-container`).
- `container.image`: The container image to use (e.g., `arzian/dockerhub:portfolio`).
- `container.ports.containerport`: The port the container listens on (e.g., `3000`).

#### Service

- `service.kind`: The kind of Kubernetes resource for the service (e.g., `Service`).
- `service.metadata.name`: The name of the service (e.g., `portfolio-service`).
- `service.spec.selector.app`: The label selector for the service to match the deployment (e.g., `portfolio`).
- `service.spec.type`: The type of the service (e.g., `LoadBalancer`).
- `service.spec.ports.protcol`: The protocol for the service (e.g., `TCP`).
- `service.spec.ports.port`: The port on which the service is exposed (e.g., `3000`).
- `service.spec.ports.targetPort`: The port to route traffic to inside the container (e.g., `3000`).
- `service.spec.ports.nodePort`: The node port exposed on the cluster (e.g., `31110`).

## Example Values File

```yaml
kind: Deployment
deploymentname: portfolio-deployment
namespace: default
spec:
  replicas: 2
  selector:
    appname: portfolio
  template:
    appname: portfolio
container:
  name: portfolio-container
  image: arzian/dockerhub:portfolio
  ports:
    containerport: 3000
service:
  kind: Service
  metadata:
    name: portfolio-service
  spec:
    selector:
      app: portfolio
    type: LoadBalancer
    ports:
      protocol: TCP
      port: 3000
      targetPort: 3000
      nodePort: 31110
```

## Uninstallation

To uninstall the chart and remove the deployed application from your Kubernetes cluster, use the following command:

```bash
helm uninstall <release-name>
```

Example:

```bash
helm uninstall portfolio-webapp
```

This will remove the deployment and service from your cluster.

## License

This Helm chart is open-source and available under the MIT License. See the [LICENSE](LICENSE) file for details.
```
