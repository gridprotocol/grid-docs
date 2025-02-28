# Grid CP Installation Process

## Prerequisites

Before installing CP, ensure the following prerequisites are met:

- A **public IP address** is available
- The IP address has a **bound domain name**
- **Go version 1.21+** is installed
- Multiple hosts with **NVIDIA GPUs** are prepared

---

## Install Kubernetes

To deploy Kubernetes v1.25.3, follow this guide:  
<https://blog.csdn.net/m0_43445928/article/details/130524917>

_Alternative_: Deploy Kubernetes using your preferred method.

---

## Register CP on Web Interface

1. Access Grid's official portal:  
   <https://grid.metamemo.one/>
2. Navigate to **Grid Provider** section
3. Click **Become A Provider**
4. Complete registration form with:
   - Provider name
   - Public IP address
   - Service port
   - Domain name

---

## Add Nodes via Web Interface

1. Go to **Add Node** page
2. Configure node parameters:

   ```plaintext
   Node Name Format: node-[number] (e.g., node-1)
   Pricing Strategy: Set your price per compute unit
   ```

3. **Node ID Assignment Rule**:  
   `Node ID = Node Name Number - 1`  
   Example:  
   `node-1` → ID `0`  
   `node-5` → ID `4`

---

## Configure Kubernetes Node Labels

### Step 1: Retrieve Node ID

Check node ID in web interface's node details page.

### Step 2: Apply Labels

```bash
kubectl label node <NODE_NAME> id=<NODE_ID>
```

Example for node `gpu-server-1` with ID `3`:

```bash
kubectl label node gpu-server-1 id=3
```

---

## Build & Configure CP Backend

### 1. Compile from Source

```bash
git clone https://github.com/gridprotocol/computing-api.git
cd computing-api/bin
make clean && make
```

### 2. Wallet Management

#### Import Existing Wallet

```bash
./computing-api wallet import \
  --sk=234fe73f5154570065a202f185dca074f1d7482a5e08ce093a92ed96807a6cf0 \
  --pw=123123
```

#### Create New Wallet

```bash
./computing-api wallet init --pw=STRONG_PASSWORD
```

---

## Gas Fee Recharge

Contact Grid administrators for blockchain gas fee top-up:  
`admin@grid.metamemo.one`

---

## Configuration File Setup

Edit `computing-api/bin/config.toml`:

```toml
# Network Configuration
[Grpc]
  Listen = "0.0.0.0:12345"  # gRPC service port

[Http]
  Listen = "0.0.0.0:12346"  # HTTP service port
  HSKey = "memo.io"          # Session encryption key
  CookieExpire = 86400       # 24h session validity

# Wallet Settings
[Remote]
  KeyStore = "./.keystore"    # Wallet storage path
  Wallet = "0xEf95c72C836605203F7f66788E450Af2a4141957"  # Your wallet address

# Infrastructure Endpoints
[Platform]
  Url = "http://183.240.197.189:18002"  # Production database URL

[Validator]
  Url = "http://validator.grid.io:8081"  # Validation service endpoint
```

---

## Service Startup

### Start Backend Service

```bash
# Syntax: ./restart.sh [chain_type]
./restart.sh test    # Testnet
./restart.sh dev     # Development
./restart.sh prod    # Production
```

### Monitor Logs

```bash
tail -f log/computing-api.log | grep -E 'ERROR|WARN'
```

### Verify Service Status

```bash
curl http://localhost:12346/healthcheck
# Expected response: {"status":"ok"}
```

---

## Troubleshooting

| Issue                      | Solution                          |
|----------------------------|-----------------------------------|
| Wallet import failure      | Verify SK format and file permissions |
| Node label mismatch        | Confirm kubectl context is correct |
| Blockchain RPC errors      | Check network connectivity        |
