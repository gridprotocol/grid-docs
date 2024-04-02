# Terminology

## PROVIDER

Also known as CP, computational power node, is a role in the GRID system that provides computational resources and earns corresponding rewards.

## USER

User node, in the GRID system, is the consumer of computational power who needs to pay a certain fee to obtain the right to use computational resources.

## Smart Contract

It refers to computer code executed on a blockchain. In GRID, smart contracts mainly include node registration contracts and market contracts, which are responsible for managing computational power node information and automating order settlements.

## Kubernetes

It is a container orchestration software deployed as infrastructure on local servers by computational nodes. It serves as the actual runtime environment for user applications. User applications are provided to Kubernetes in the form of YAML files for deployment and create services for external access.

## GATEWAY

The gateway is the core software used by computational nodes to provide computational services externally. It is operated by computational nodes and provides HTTP API interfaces for various verification and deployment functions. It interacts with the local Kubernetes cluster to deploy user-provided resource description YAML files into the cluster and create services as access entry points (endpoints) for user applications.

## ReverseProxy

By introducing reverse proxy functionality, computational nodes forward user access requests to the deployed application services and return the application's response data back to the frontend through the gateway, completing the request forwarding process.

## Platform

The platform is operated by the GRID official and primarily provides various API services for all participants. This includes the registration of computational power providers, order creation and querying, token payment, credits recharge and querying, confirmation of token payments, and other interfaces.
