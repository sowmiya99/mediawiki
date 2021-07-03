# Deployment of MediaWiki with MySQL to Kubernetes cluster using FluxCD and Kustomize

# Assumptions:
Kubernetes cluster is up and running (Control plane and 2 node).
Namespace called “mediawiki” is created.
Ingress controller is deployed in cluster (traefik).
Domain name is purchased "mediawiki.thoughtworks.io"
Load Balancer for mediawiki.thoughtworks.io is created.
Dockerimage built and pushed to GCR.
Sealed secrets are created with wiki_page password and mysql password.
FluCD Pod deployed in namespace and confgiured to poll this repository every 2m and pull and deploy the configurations.

# How deployment is automated ?
This repository's folder contains FluxCD/Kustomize yaml configuration files.
Flux pod deployed in cluster mediawiki namespace automatically pulls the changes from this repo and deploys the configurations.

# How to validate the configuration files using kustomize ?
cd mediawiki/workloads/
kustomize build .