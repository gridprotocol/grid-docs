# FAQ

Some questions to check.

## Where is Platform running?

The platform refers to a series of service interfaces provided by the service provider to the users, and it is the responsibility of the service provider to start and maintain it.

The platform is designed to replace users in interacting with blockchain contracts. Therefore, users do not need to interact directly with the blockchain. Instead, they send their task requests to the platform, which is responsible for interacting with the blockchain and returning the final execution results to the frontend for display.

Please refer to the previous relevant sections for the interaction between the frontend and the platform.

## How to startup a gateway?

Gateway Startup

In addition to deploying the Kubernetes infrastructure, the provider also needs to start a gateway service program to respond to all user request actions. To do this, you simply need to set the necessary parameters in the configuration file, config.toml, and then execute the startup script.


## How to customize resources as a user?

When a user creates an order, they need to specify the quantity of resources they want to purchase. When deploying an application, the user first selects the YAML template for the application. Then, based on the user's order details, the backend adds the container's resource requirements and limits (requests, limits) to the container resource section of the YAML file. This allocation ensures that the application is assigned the quantity of resources purchased in the user's order.