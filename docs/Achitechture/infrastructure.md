# Infrastruct on provider

Providers must prepare some local environment to become available.

## Provider Infrastructure

The provider deploys Kubernetes container orchestration software. The provider is responsible for planning the number of nodes to deploy based on its available resources and adding these nodes to the Kubernetes cluster. The applications deployed by users will run on these nodes, and the provider must ensure that all local nodes are functioning properly to ensure the smooth operation of user applications.

## Kubernetes

In the GRID project, resource nodes (CP) integrate their resources through a Kubernetes (often abbreviated as K8s) cluster.

Here is a basic introduction to Kubernetes:

Kubernetes is an open-source container orchestration platform used to automate the deployment, scaling, and management of containerized applications. It provides a highly scalable cluster management solution that can run on cloud or on-premises infrastructure.

The design goal of Kubernetes is to simplify the deployment and management of containerized applications. It offers a powerful platform that automates tasks such as container scheduling, scaling, storage management, networking, and application health monitoring. Kubernetes also provides rich features such as service discovery, load balancing, key management, and configuration management to help developers build and manage reliable distributed applications.

Kubernetes organizes the deployment units of applications using a set of containers called "Pods." Pods are a group of containers that share the same namespace, allowing them to share network and storage resources and communicate through a high-speed local network. Kubernetes also provides a robust scheduler that deploys Pods to nodes in the cluster based on resource requirements, health status, and other policies.

In addition to the basic container orchestration capabilities, Kubernetes supports Custom Resource Definitions (CRDs) and controller extension mechanisms, allowing users to customize and extend the behavior of Kubernetes. This makes Kubernetes a highly customizable and scalable platform suitable for various application scenarios of different scales and types.

In summary, Kubernetes is a popular container orchestration platform widely used for building, deploying, and managing containerized applications. It helps users achieve highly automated, elastic, and reliable application deployment and operations.

## YAML

In Kubernetes (K8s), YAML files are commonly used to define and configure Kubernetes resources. They are text files written using the YAML (YAML Ain't Markup Language) syntax. By writing appropriate YAML files, various Kubernetes resources such as Deployments, Services, ConfigMaps, PersistentVolumeClaims, and more can be created, deployed, and managed.

In a YAML file, we can specify the API version, type, metadata, and specification of Kubernetes resources.

Here's an example of a YAML file:

apiVersion: apps/v1

kind: Deployment

metadata:

name: my-deployment

spec:

replicas: 3

selector:

matchLabels:

app: my-app

template:

metadata:

labels:

app: my-app

spec:

containers:

\- name: my-container

image: my-image:latest

ports:

\- containerPort: 8080

In the example, we define a Deployment named "my-deployment" that will create three replicas. The replicas are associated with Pods using a label selector that matches Pods with the label "app: my-app." The template section of the Deployment defines the specification of the Pods to be deployed, including the image, ports, and other details of the containers.

By using YAML files, we can achieve declarative configuration, which means describing the desired state of Kubernetes resources by defining the desired state and specifications. The Kubernetes controller is responsible for ensuring that the actual state of the cluster aligns with the desired state.

Using YAML files makes it easy to create, update, and delete Kubernetes resources, enabling automated deployment and management of applications. Additionally, YAML files provide a highly readable format, simplifying the configuration and sharing of Kubernetes resources in a reliable manner.