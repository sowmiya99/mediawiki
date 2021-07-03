# Deployment of MediaWiki with MySQL to Kubernetes cluster using FluxCD and Kustomize

# Assumptions:
1. Kubernetes cluster is up and running (Control plane and 2 node).
2. Namespace called “mediawiki” is created.
3. Ingress controller is deployed in cluster (traefik).
4. Domain name is purchased "mediawiki.thoughtworks.io"
5. Load Balancer for mediawiki.thoughtworks.io is created.
6. Dockerimage built and pushed to GCR.
7. Sealed secrets are created with wiki_page password and mysql password.
8. FluCD Pod deployed in namespace and confgiured to poll this repository every 2m and pull and deploy the configurations.

# How deployment is automated ?
1. This repository's folder contains FluxCD/Kustomize yaml configuration files.
2. Two workloads created for mediawiki and MySQL DB deployments.
3. Flux pod deployed in cluster mediawiki namespace automatically pulls the changes from this repo workloads and deploys the configurations respectively.

# How to validate the configuration files using kustomize ?
cd mediawiki/workloads/
kustomize build .
