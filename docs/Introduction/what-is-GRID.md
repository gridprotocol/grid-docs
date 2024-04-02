# Introduction

GRID is a comprehensive system that provides a trading marketplace for computing nodes and users, enabling automated settlement of service fees. It allows computing nodes to utilize the GRID gateway for order verification, application deployment, and other functionalities, while registering their resource information for users to select and utilize.

Nodes need to deploy a local service cluster (such as Kubernetes) to integrate their local computing resources. Then, they start the gateway service locally and register their node resource information through the platform's node registration functionality. The platform presents the registered nodes to users, who can choose suitable nodes to provide services according to their needs.

Users can select nodes that meet their requirements from the platform, create orders with the nodes, and make corresponding payments. Afterward, they can start using the node resources and deploy specific applications through the gateway API. Once the application is successfully deployed, users can access the deployed application services directly by accessing the node gateway.