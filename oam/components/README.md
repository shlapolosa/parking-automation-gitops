# OAM Components

This directory contains generated OAM Component definitions created by ApplicationClaims.

## Generated Components

When you add components to , the system automatically:

1. Creates ApplicationClaims in the vCluster
2. Generates OAM Component definitions here
3. Creates Kubernetes manifests in 
4. Updates ArgoCD applications for deployment

## Component Types

- **microservice-with-db**: Full-featured microservice with database and cache
- **react-frontend**: React TypeScript frontend with Material-UI
- **static-site**: Static website hosting
- **kafka-service**: Event streaming service
- **data-pipeline**: ETL and data processing workflows

## Example Generated Component

```yaml
apiVersion: core.oam.dev/v1beta1
kind: Component
metadata:
  name: user-service
  namespace: parking-automation
spec:
  workload:
    apiVersion: serving.knative.dev/v1
    kind: Service
    metadata:
      name: user-service
    spec:
      template:
        spec:
          containers:
          - name: user-service
            image: docker.io/socrates12345/user-service:latest
  parameters:
  - name: image
    fieldPaths: ["spec.template.spec.containers[0].image"]
```
