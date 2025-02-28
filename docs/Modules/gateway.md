# Gateway

What is the GRID gateway?

The GRID gateway is a daemon program run by computing nodes responsible for providing core services to implement project functionalities, including the greet service and process service.

Greet Service:

It handles order verification and application deployment. The GRID gateway is deployed on each resource node (CP) to receive user requests and perform tasks related to the local Kubernetes cluster of the node. This enables the deployment of user applications to the node's Kubernetes cluster.

Process Service:

It forwards user requests to the Kubernetes computational cluster deployed on the computing node and returns the response data from the user's application back to the frontend for display.

## Verification

Type 0 request of the Greet interface: Order resource and fee validation

This request verifies whether the quantity of ordered resources can be provided by the node and if the payment for the order is sufficient.

Type 1 request of the Greet interface: Payee validation for the order

This request sets and validates the payee for the order. Once the validation is successful, the order is saved locally on the node, and the order information is locked in the contract, completing the validation process.

## Authorization

Type 2 request of the Greet interface: User identity verification and cookie issuance

After the validation of the order payee is successful, the user needs to sign the request to prove their identity. Once the verification is successful, an authorization cookie is issued to the user. Upon receiving the cookie, the user can proceed with application deployment and usage.

## App Deployment

Once the previous validation steps have been completed and the authorization token (cookie) has been obtained, the application deployment functionality of the gateway can be used.

In the deployment request, it is necessary to provide the YAML file URL corresponding to the application to determine the image information to be used by the application. The deployment functionality will download and parse the YAML file, deploy the application described in the YAML file, and generate a corresponding service for the application after successful deployment. Finally, the service will be registered in the corresponding application entry point for the user. The entry point will be obtained in the forwarding functionality and used as the target URL for request forwarding by the reverse proxy.

## Request Forward

The GRID gateway does not directly handle user application access requests. Instead, it forwards user requests to the application entry point (entrance) through the reverse proxy provided by the gateway and retrieves the response.

The process is as follows:

The gateway receives a Process request.

It retrieves the application entrance address registered by the user during application deployment.

The gateway uses the reverse proxy to forward the incoming request to the application's entrance point and retrieves the application's response.

Finally, the reverse proxy returns the response data obtained from the request to the frontend, completing the forwarding process.
