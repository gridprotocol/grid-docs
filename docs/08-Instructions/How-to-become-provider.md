# Becoming a Grid Trading Market Provider

To become a provider in the grid trading market, you need to register your provider information, deploy and configure a local Kubernetes cluster, and start the backend program. Here is the step-by-step process:

## 1. Register Provider Information

- Navigate to the frontend provider page and register by clicking the "Become A Provider" button.
- Fill in the required information such as name, IP address, port, and domain name.

<img src="/img/provider1.png">

## 2. Deploy Local Kubernetes Cluster and Node Registration/Configuration

After completing the provider information registration, you need to configure your local Kubernetes cluster and set labels for each cluster node with the following steps:

### 2.1 Deploy Local Kubernetes Cluster

- Refer to the deployment method here: [CSDN Blog Post](https://blog.csdn.net/m0_43445928/article/details/130524917).
- Alternatively, you can deploy based on your own deployment experience.

### 2.2 Register Nodes through the Frontend Interface

- On the frontend interface's "addnode" page, enter the node configuration and unit price information to complete the node registration.
- A unique node ID will be automatically assigned for identifying this node within the provider.

<img src="/img/provider2.png">

### 2.3 Configure Labels for Each Node Using Node ID

- Node IDs start incrementing from 0.
- First, check the node ID on the frontend interface's node details page, then set labels for each node using the ID as the label. For example:

```sh
  kubectl label node nodename id=0
```

Replace nodename with the actual node name, and 0 with the actual node ID.

## Backend Program Startup Process

### 3.1 Download the Backend Program, Startup Script, and Configuration Files Locally

- Download the backend program, startup script, and configuration files to your local machine.

### 3.2 Import or Create a Wallet

- Navigate to the directory where the backend program is located.
- Import an existing wallet using the private key (`sk`) with the following command:

  ```sh
  ./computing-api wallet import --sk=234fe73f5154570065a202f185dca074f1d7482a5e08ce093a92ed96807a6cf0 --pw=123123
  ```

Here, sk represents the provider wallet private key, and pw represents the wallet repository password.

Alternatively, you can create a new wallet using the init command.

### 3.3 Fund the Provider Wallet with Gas Fees and Credits

- Contact the official administrator to top up the provider wallet with gas fees and credits.

### 3.4 Modify the Configuration File

- Update the `http listen` port in the `config.toml` file to the desired port for startup. For example, set it to 12347.
This completes the specified sections of the backend program startup process in English within a Markdown document.

<img src="/img/provider3.png">

### 3.5 Start the Backend

- Execute the backend startup script with the following command:

  ```sh
  ./restart test
  ```

Here, test indicates the use of a test chain contract; the specific value should be set according to the actual situation.

The operation logs are stored in the log file.
