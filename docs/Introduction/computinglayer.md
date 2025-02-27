# ComputingLayer Description

The computing layer is the core of how providers have the ability of offering service.

Two core acpects make up of the computing layer: Gateway and k8s cluster:

<img src="/img/ComputingLayer.png">

## Gateway

As mentioned above, the gateway is a daemon programe maintained by each provider. It receives all requests and perform tasks related with each request. When the result comes out, it then response the result back to the caller of the request.

## Kubernetes cluster

Some kind of core tasks performed by gateway must interact with the local k8s cluster in order to be successful. Such as the deploy task and the compute task, both of which need the k8s cluster to engage in and do it's job. 

For the deploy scenario, the gateway will handle the YAML file inside the deploy request to the k8s cluster. Then the k8s cluster will create the application resource using this YAML file, such as a deployment or a pod etc. When the application is online, a service of it will be created for the outer world to access the user application. And finially, the service address(we call also it entrance) of this application will be registered in the local db of  the provider for the later query.

A computing(we can call it visiting as well) request reachs the gateway daemon, a reverse proxy will be aquired for this request, and the target URL of this reverse proxy will set to the entrance of the user's deployed application. As we mentioned above, the entrance of this applicatioin can be queried in the provider's local db.

When the reverse proxy is ready, it will handle this request, forward it to the application entrance, and finally return the response from the application to the request caller.

At this point, both the deploying task and the serving task are completed within the computing layer.