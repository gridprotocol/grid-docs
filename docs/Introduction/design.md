# Architechture Description

The architechture is constructed by 3 layers:

<img src="/img/Module.png">

## User Layer

The user layer is made up of the frontend and the backend, it is responsible for offering most of the operating APIs for all kind of nodes, including user nodes and provider nodes.
The frontend works as a webui, it provides a web based user interface to interact with users, and sends corresponding requests to backend on behalf of users.

The backend deals with all the requests sent by users on the frontend, and when all the jobs are done, the response will be sent back to the frontend to show the results.

## Settlement Layer

The settlement layer mainly contains several smart contracts on blockchain, inculding the register contract, the market contract, the erc20 contract.

The register contract is used to manage all prvoders' infomation, including resources and prices and other basic infomation.

The market contract is used to manage all orders created between users and providers. Except recording all the orders, it completes the settlement task which is the core function of the market cotract. The settlement procedure calculates the amount of credit left in the order which should be refound to users, and the amount of credit the providers can get from this order, and pay to both of them.

## Computing Layer

The computing layer works on providers. It contains 2 parts, the gateway and the k8s cluster on providers.
The gateway is a daemon application running by providers, dealing with the greeting and the computing requests. It interact with the local k8s cluster to achieve the app management, such as app deploying, visiting, and deleting.

The k8s cluster is used to integrate all computing resources, and run user's application images in containers automatively.

