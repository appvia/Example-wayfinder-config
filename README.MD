# Wayfinder Configuration and Setup Guide

Welcome to the **Wayfinder Configuration and Setup Guide**! This documentation serves as a comprehensive resource for users seeking a seamless configuration of Wayfinder. Whether you are a seasoned administrator or a newcomer exploring Wayfinder's capabilities, this guide provides a structured approach to the configuration process.

## Assumptions:

1. You've already installed Wayfinder.
2. You have an admin user.

Let's embark on a journey to unlock the full potential of Wayfinder by following this guide's well-organized structure and leveraging the included examples for a smoother setup experience.
---  

## Guide Structure

Below is the structured approach we will follow in this comprehensive Wayfinder Configuration and Setup Guide. This organized layout simplifies the configuration process, offering clear steps and examples within each respective folder. Whether you are focusing on access configurations, RBAC policies, or reusable components, this guide ensures a systematic and user-friendly experience.

## 1. Stages
- A stage is used to isolate and test resources at the infrastructure level such as production or development. Internally, resources provisioned under these stages are labelled accordingly and can be used when you apply a configuration such as policy, compliance, user permissions, estimated costs, network peering, and more. Wayfinder ships with two default stages, namely Non-Production and Production. Administrators can optionally create additional stages.
- You can find out more [here](https://docs.appvia.io/wayfinder/admin/stages).
- [Examples of stages](wayfinder/1.stages)

## 2. Cloud

### 2.1. Cloud Access Configurations
- Grant Wayfinder with cloud access (AWS cloud account, Azure subscription, or GCP project) to enable it to manage specific cloud resources and provide cloud automation.
- Step-by-step instructions for configuring cloud access can be found [here](https://docs.appvia.io/wayfinder/admin/cloud/access/connect-clouds).
- [Examples of Cloud Access Configurations](wayfinder/2.cloud/2.1.cloudaccessconfigs)

### 2.2 Cloud Resource Plan
- Cloud Resource Plans act as templates for Terraform modules. These plans serve as guardrails that let Wayfinder administrators shape the options and configuration for cloud resource components that developers use during the [Application](https://docs.appvia.io/wayfinder/workspaces/applications/application-app) self-service process.

- Step-by-step instructions for configuring Cloud Resource Plan can be found [here](https://docs.appvia.io/wayfinder/admin/cloud/resources/cloud-resource-plans).

- [Examples of global cluster policies configurations](wayfinder/2.cloud/2.2.cloudresourceplans)

### 2.3 Global DNS Zones

- Wayfinder automatically installs and configures the [ExternalDNS](https://github.com/kubernetes-sigs/external-dns) application in each managed Kubernetes cluster. ExternalDNS automatically creates DNS records in managed DNS zones when a domain is configured on Kubernetes [Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/) objects. With ExternalDNS, Wayfinder can control DNS records dynamically via Kubernetes resources in a DNS provider-agnostic way. For more information, see the [kubernetes-sigs/external-dns](https://github.com/kubernetes-sigs/external-dns) GitHub project.

- Step-by-step instructions for configuring Global DNS Zones can be found [here](https://docs.appvia.io/wayfinder/admin/dns-zones).

- [Examples of global cluster policies configurations](wayfinder/2.cloud/2.3.DNS)

## 3. kubernetes

### 3.1. Cluster Networking

- When creating clusters for workspaces, Wayfinder creates networks and assigns network ranges. This can be controlled and enhanced to provide private clusters, managed network ranges, and peering between networks within a single cloud provider.

- Step-by-step instructions for configuring Cluster networking can be found [here](https://docs.appvia.io/wayfinder/admin/kubernetes/clusters/networking-overview).

- [Examples of Cluster networking configurations](wayfinder/3.kubernetes/3.1.networking)

### 3.2. Cluster Plan

- Cluster plans function as templates for self-serve clusters, serving as guardrails that enable Wayfinder administrators to customize available options and configurations for developers (as workspace members) to independently provision their environments.

- Step-by-step instructions for configuring Cluster Plan can be found [here](https://docs.appvia.io/wayfinder/admin/kubernetes/cluster-plans).

- [Examples of Cluster Plan Configurations](wayfinder/3.kubernetes/3.2.clusterplans)

### 3.3. Packages

- Packages provide a delivery method for installing and/or bootstrapping multiple clusters with software. Wayfinder uses packages to maintain its own package installations. Wayfinder administrators can also use packages as building blocks to install software in clusters to achieve standardization, ensure company security policies, and save DevOps time.

- Step-by-step instructions for configuring Packages can be found [here](https://docs.appvia.io/wayfinder/admin/kubernetes/packages/package-installations).

- [Examples of Packages Configurations](wayfinder/3.kubernetes/3.3.packages)

### 3.4. Global Cluster Policies

- This section provides an overview of the security policies used in Wayfinder. The policies described here are implemented using **Kyverno**, a Kubernetes policy engine that can validate, mutate, and generate Kubernetes resources based on custom policies. The policies aim to ensure that the Kubernetes cluster is secure, efficient, and in compliance with best practices.

- Step-by-step instructions for configuring Cluster Plan can be found [here](https://docs.appvia.io/wayfinder/admin/access/security-policies/wf-security-policies).

- [Examples of global cluster policies configurations](wayfinder/3.kubernetes/3.4.globalclusterpolicies)

## 4.Wayfinder Groups

-  `Wayfinder Groups` represent a collection of Wayfinder platform users.

- [Examples of Wayfinder Groups](wayfinder/4.WayfinderGroups)

## 5. Workspace

- A workspace is a way to group users and cloud infrastructure so that only members of a workspace have access to the infrastructure associated with that workspace. Within a workspace, members may have different access permissions to that infrastructure depending on the policies in place.

- Step-by-step instructions for configuring Workspace can be found [here](https://docs.appvia.io/wayfinder/admin/cloud/access/connect-clouds).

- [Examples of Workspace Configurations](wayfinder/5.workspaces)
  
## 6. CI/CD Pipeline

To integrate Wayfinder into your CI/CD pipeline, follow these steps:
1. Obtain a platform access token by referring to the [step-by-step instructions here](https://docs.appvia.io/wayfinder/admin/access/tokens/access-tokens).
2. Set the following environment variables as secrets in your CI system:
-  `WAYFINDER_TOKEN`
-  `WAYFINDER_SERVER`
3. Utilize the Wayfinder CLI Docker image: `quay.io/appvia-wayfinder/wftoolbox`
4. Explore provided examples for integration:
- GitHub Actions: [ci.yaml](.github/workflows/ci.yaml)

- Azure DevOps: [azure-pipelines.yaml](azure-pipelines.yaml)

---
Navigate through each section following the outlined structure and leverage the included examples to facilitate a smooth and effective setup of Wayfinder. Happy configuring!