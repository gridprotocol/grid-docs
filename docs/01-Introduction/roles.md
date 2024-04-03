# Roles in GRID

Provier is a node with computing resources and willing to serve users to gain profit.

User is the consumer of computing resources, and the amount of tokens paid to providers is according to the number of resources and the duration of the order accepted by a provider. 

## Provider

The computing nodes serve as the suppliers of computational power in the computing marketplace. They utilize container orchestration software to organize existing hardware resources, including processors, memory, storage, and graphics cards. Subsequently, they start the gateway service to provide various API interfaces externally, enabling node functionalities such as identity authentication, application deployment, and application access.

During application deployment, the resource description file is downloaded from the provided YAML file URL in the deployment request. The node then interacts with the container orchestration software to deploy the application described in the resource description file to the local environment, thereby completing the provision of computational power services.

After deploying the local infrastructure and starting the gateway service, the computing nodes also need to register their node information on the blockchain through the GRID platform service. This allows for the public exposure of the nodes. User nodes can access all registered computing nodes through the API interfaces provided by the platform.

## User

As a user, you act as a consumer of computational power. To begin, you need to purchase tokens used for paying for computational services. Based on the availability of resources and their prices, you can choose the most suitable computing node to create an order with and make the corresponding payment according to the market rate. Once the order is activated, you can start deploying applications on the computing node to actually utilize the purchased computational resources.

The token payment made by the user for the order will be settled based on the actual duration of service provided to the user. The calculated fee amount will be paid to the computing node upon completion or cancellation of the order. Any remaining amount will be refunded to the user.