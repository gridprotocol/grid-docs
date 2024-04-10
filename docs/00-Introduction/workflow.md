# WorkFlow Description

The work flow diagram shows how users interact with all parts of GRID system, including platform, gateway, blockchain and kubernetes on providers.

<img src="/img/Workflow.png">

The onchain operations are done by requesting to the platform, including provider register/list and lease(order) creation. 

The core operations are done by the gateway daemon on each providers, including all greets request and process request. Greet requests are in charge of order verification, caller authentication, and app deployment. Only the verification and authentication both passed, a cookie will be sent to the caller. Both deploy and process operations need cookie to proceed.

When deploy request is received, gateway will interact with local k8s cluster, and deploy the corresponding container with the app image set in the YAML file.

After a successful deployment, a service will be create for this app, and the service address will be record as the entrance for this user's application. 

The process request is used for user to access his deployed application. When process request received on gateway, the request for the url path will be forward to the entrance recorded after the deployment, and finially, the response from app entrance will be sent back to the frontend for user.