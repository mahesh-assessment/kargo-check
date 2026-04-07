# kargo-check

Helm chart for deploying nginx with Kubernetes Deployment and Kargo-driven image promotions.

## Image Source

The chart is configured to pull nginx from AWS Public ECR:

`public.ecr.aws/nginx/nginx`

## Helm Install

Install with default values:

```bash
helm upgrade --install nginx-demo . -n kargo-demo --create-namespace
```

Install for a specific environment:

```bash
helm upgrade --install nginx-demo . -n kargo-demo --create-namespace -f values-dev.yaml
helm upgrade --install nginx-demo . -n kargo-demo --create-namespace -f values-itg.yaml
helm upgrade --install nginx-demo . -n kargo-demo --create-namespace -f values-pro.yaml
```

## Kargo Promotion Inputs

Kargo can update image values in the following files:

- `values.yaml`
- `values-dev.yaml`
- `values-itg.yaml`
- `values-pro.yaml`

The promoted fields are:

- `image.repository`
- `image.tag`
