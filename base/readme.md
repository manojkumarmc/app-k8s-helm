apiVersion: apps/v1: Deployment API version.

kind: Deployment: Indicates that this is a Deployment resource.

metadata.name: Name of the Deployment.

spec.replicas: The desired number of pod replicas.

spec.selector.matchLabels: Label selector used by the Deployment.

spec.template: The pod template used to create new pod instances. It includes the pod's metadata.labels and spec, and within spec:

spec.containers: Container spec definition.

name: Container name.

image: Docker image.

ports: Container port exposure.

env: Environment variables (fetching from configmap).

readinessProbe: Example readiness probe for checking the app is up and running. You should update the path value to your api endpoint.

livenessProbe: Example liveness probe that tells the pod to be restarted when is not alive. You should update the path value to your api endpoint.

#### Key Differences from replicaset.yaml

Rolling Updates: Deployments offer rolling updates, which means you can change the image or configuration and the deployment will gracefully replace the old pods with the new ones without downtime.

Rollbacks: Deployments make it easy to rollback to a previous version if an issue is found.

Declarative Updates: With Deployments, you can simply edit the spec of the Deployment and Kubernetes will take care of the rollout automatically.

ReplicaSets: In fact, Deployments create and manage ReplicaSets behind the scenes. This adds a layer of abstraction and powerful features for your deployments.

Readiness and Liveness Probes: I've added a readiness and liveness probes as an example. You need to adjust /docs to your actual endpoints. These are critical for a production setup.

#### How to apply

- kubectl apply -f configmap.yaml
- kubectl apply -f service.yaml
- kubectl apply -f ingress.yaml
- kubectl apply -f deploy.yaml
