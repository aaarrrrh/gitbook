---
description: >-
  This guide will walk you through setting up and launching a Polygon (Matic)
  Node.
---

# How to run a Polygon Full Node

## Introduction

These are the key components for running a Polygon (Matic) Node:

1. `Proof of Stake node `- called **Heimdall**
2. `REST API server` - also called **Heimdall**
3. `EVM node` - called **Bor**.

{% hint style="info" %}
T**he following setup flow is based on Ubuntu:18.04+ version**
{% endhint %}

### Set up Flow

**00 Prerequisites** - Describes recommended and minimum hardware requirements\
**01 Install Dependencies** - Download all the necessary dependencies required to set up and launch a Polygon Node. \
**02 Build Binaries **- This section walks you through building _Heimdall_ and _Bor_ Binaries.\
**03 Run Node** - Initialize binaries\
**04 Launch Node** - Start the Polygon Node\
**05 Set up HTTPS NGINX Reverse Proxy** - Set up a proxy service to take a client request, passes it to servers, and deliver the server response back to the client.\
**06 Secure HTTP traffic** between NGINX using TLS encryption. For security reasons, it is recommended to add an encryption layer with TLS/SSL and to use HTTP. [Let’s Encrypt](https://letsencrypt.org) provides a TLS certificate at no cost and configuration of Nginx can be done easily with [Certbot](https://certbot.eff.org), a tool provided by the [EFF](https://www.eff.org).\
**07 Check your Endpoint is active **- Run a test call to check your endpoint is running.&#x20;

## 00 Prerequisites

### Hardware requirements: <a href="hardware-requirements" id="hardware-requirements"></a>

**Minimal:**\
****4 core \
8 RAM \
1.5TB SSD\
\
**Recommended:**\
****8 core \
16 RAM \
1.5TB SSD

## 01 Install Dependencies

* **Install Build Essentials **

```bash
apt-get update 

apt-get install wget build-essential make gcc git -y
```

* **Install golang v1.14.0+**

[![](https://golang.org/favicon.ico)Download and install - The Go Programming Language](https://golang.org/doc/install)

## 02 Build Binaries:

### **Heimdall:**

**1 Clone Heimdall code repository:**

```bash
git clone https://github.com/maticnetwork/heimdall.git
```

**2. Move to Heimdall directory with source code:**

```bash
cd heimdall
```

**3. Switch to the latest release branch:**

```bash
git checkout v0.2.2
```

**4. Build the source code:**

```bash
make install
```

**5. Confirm binaries were built:**

```bash
$HOME/go/bin/heimdalld version
```

The version of `Heimdall` is output.

**6. Exit the code source folder:**

```bash
cd ..
```

### **Bor:**

**1.Clone Bor code repository:**

```bash
git clone https://github.com/maticnetwork/bor
```

**2. Move to Bor directory with source code:**

```bash
cd bor
```

**3. Switch to the latest release branch:**

```bash
git checkout v0.2.8
```

**4. Build the source code:**

```bash
make bor
```

**5. Confirm binaries were built:**

```bash
$HOME/go/bin/bor version
```

The version of Bor is output

**6. Exit the code source folder:**

```bash
cd ..
```

## 03 Run node

### **Initialize Heimdall:**

Replace all the paths with the ones you prefer

**1.Create heimdall data directory:**

```bash
mkdir -p $HOME/heimdall_data
```

**2. Initialize heimdall data directory:**

```bash
heimdalld init --home $HOME/heimdall_data
```

**3. Download and replace genesis file:**

```bash
wget https://raw.githubusercontent.com/maticnetwork/launch/master/mainnet-v1/sentry/sentry/heimdall/config/genesis.json
```

```bash
cp -rf genesis.json $HOME/heimdall_data/config/genesis.json
```

**4. Modify heimdall config files:**

```bash
# edit $HOME/heimdall_data/config/config.toml

sed -i '/moniker/c\moniker = "MyPolygonNode"' $HOME/heimdall_data/config/config.toml

sed -i '/seeds/c\seeds = "f4f605d60b8ffaaf15240564e58a81103510631c@159.203.9.164:26656,4fb1bc820088764a564d4f66bba1963d47d82329@44.232.55.71:26656"' $HOME/heimdall_data/config/config.toml

sed -i '/eth_rpc_url/c\eth_rpc_url = "https://my-ethereum-mainnet-endpoint.com"' $HOME/heimdall_data/config/config.toml
```

### Initialize bor:

Replace all the paths with the ones you prefer

**1.Create bor data directory:**

```bash
mkdir -p $HOME/bor_data
```

```bash
mkdir -p $HOME/bor_data/data
```

**2. Download bor genesis file:**

```bash
wget https://raw.githubusercontent.com/maticnetwork/launch/master/mainnet-v1/sentry/sentry/bor/genesis.json
```

```bash
cp -rf genesis.json $HOME/bor_data/gensis.json
```

**3. Initialize Bor data directory and genesis:**

```bash
bor --datadir $HOME/bor_data/data init genesis.json
```

**4. Download and replace genesis file:**

```bash
cp -rf launch/mainnet-v1/sentry/sentry/bor/genesis.json $BOR_DIR/genesis.json # 
```

**5. Prepare script for running bor:**

Script to run `bor`. Modify as required.

```bash
$HOME/start_bor.sh
```

```bash
#!/usr/bin/env sh

set -x #echo on

BOR_DIR=${BOR_DIR:-~/bor_data} # data folder of bor
DATA_DIR=$BOR_DIR/data

$HOME/go/bin/bor --datadir $DATA_DIR \
  --port 30303 \
  --http --http.addr '0.0.0.0' \
  --http.vhosts '*' \
  --http.corsdomain '*' \
  --http.port 8545 \
  --ws --ws.addr '0.0.0.0' \
  --ws.port 8546 \
  --ipcpath $DATA_DIR/bor.ipc \
  --http.api 'debug,eth,net,web3,txpool,bor' \
  --syncmode 'full' \
  --gcmode 'archive' \
  --networkid '137' \
  --miner.gaslimit '200000000' \
  --miner.gastarget '20000000' \
  --txpool.nolocals \
  --txpool.accountslots '128' \
  --txpool.globalslots '20000'  \
  --txpool.lifetime '0h16m0s' \
  --maxpeers 200 \
  --metrics \
  --bootnodes "enode://0cb82b395094ee4a2915e9714894627de9ed8498fb881cec6db7c65e8b9a5bd7f2f25cc84e71e89d0947e51c76e85d0847de848c7782b13c0255247a6758178c@44.232.55.71:30303,enode://88116f4295f5a31538ae409e4d44ad40d22e44ee9342869e7d68bdec55b0f83c1530355ce8b41fbec0928a7d75a5745d528450d30aec92066ab6ba1ee351d710@159.203.9.164:30303"

```

## 04 Launch Polygon node

{% hint style="danger" %}
**!!! IMPORTANT !!!**

Before running **bor,** wait until **heimdall** is synchronized.

To check the sync status, run the following command:\
\
****`curl 127.0.0.1:26657/status`

`catching_up` should show_ **false**_
{% endhint %}

You now have two options:

:point\_right: **OPTION 1**: Run raw binaries using different terminals for each binary.

:point\_right: **OPTION 2**: Run binaries using process manager (**`systemctl`**). Replace with your own directories.

### Option 1

Run raw binaries using different terminals for each binary.

**Run heimdall:**

1.**Start `heimdalld`:**

```bash
$HOME/go/bin/heimdalld start --home $HOME/heimdall_data/ --rpc.laddr tcp://0.0.0.0:26657
```

**2. Start heimdall rest server** - bridge between **`bor`** and **`heimdalld`**:

```bash
$HOME/go/bin/heimdalld rest-server --home $HOME/heimdall_data
```

**3. Run `bor`:**

```bash
bash ~/start_bor.sh
```

### Option 2

Run binaries using process manager (systemctl). Replace with your own directories.

**1.Prepare systemctl config files:**

**heimdalld:**

```bash
/etc/systemd/system/heimdalld.service
```

```bash
[Unit]
  Description=heimdalld
  StartLimitIntervalSec=500
  StartLimitBurst=5

[Service]
  Restart=on-failure
  RestartSec=5s
  WorkingDirectory=~/
  ExecStart=~/go/bin/heimdalld start --home=~/heimdalld_data
  Type=simple
  User=root

[Install]
  WantedBy=multi-user.target
```

**heimdalld-rest-server:**

```bash
/etc/systemd/system/heimdalld-rest-server.service
```

```bash
[Unit]
  Description=heimdalld-rest-server
  StartLimitIntervalSec=500
  StartLimitBurst=5

[Service]
  Restart=on-failure
  RestartSec=5s
  WorkingDirectory=~/
  ExecStart=~/go/bin/heimdalld rest-server --home=~/heimdalld_data
  Type=simple
  User=root

[Install]
  WantedBy=multi-user.target
```

**bor:**

```bash
/etc/systemd/system/bor.service
```

```bash
[Unit]
  Description=bor
  StartLimitIntervalSec=500
  StartLimitBurst=5

[Service]
  Restart=on-failure
  RestartSec=5s
  WorkingDirectory=~/
  ExecStart=/bin/bash ~/start_bor.sh
  Type=simple
  User=root

[Install]
  WantedBy=multi-user.target
```

**2. Update systemctl config:**

```bash
systemctl daemon-reload
```

**3. Enable all the services:**

```bash
systemctl enable heimdalld
```

```bash
systemctl enable heimdalld-rest-server
```

```bash
systemctl enable bor
```

**4. Start services:**\
****

```bash
systemctl start heimdalld
```

```bash
systemctl start heimdalld-rest-server
```

```bash
systemctl start bor
```

## **05 Setup HTTPs nginx reverse proxy:**

1.**To replace the ports with required ones, run the following command:**

```bash
apt update
apt install nginx
```

2\. **Disable the default virtual host, that is pre-configured when `Nginx` is installed via Ubuntu’s packet manager apt:**

```bash
unlink /etc/nginx/sites-enabled/default
```

3.** Enter the directory `/etc/nginx/sites-available` and create a `reverse proxy` configuration file.**

```bash
cd /etc/nginx/sites-available
nano reverse-proxy.conf
```

4\. **Paste the following `Nginx` configuration in the text editor. The proxy server redirects all incoming connections on `port 80` to the `Webfsd`server, listening on `port 8000`. **\
**Edit the port value depending on the application's specific port.**

```bash
server {
        listen 80;
        listen [::]:80;

        access_log /var/log/nginx/reverse-access.log;
        error_log /var/log/nginx/reverse-error.log;

        location / {
                    proxy_pass http://127.0.0.1:8545;
  }
}
```

5.** Copy the configuration from `/etc/nginx/sites-available` to `/etc/nginx/sites-enabled` to use a symbolic link.**

```bash
ln -s /etc/nginx/sites-available/reverse-proxy.conf /etc/nginx/sites-enabled/reverse-proxy.conf
```

6\. **Test the `Nginx` configuration file**

```bash
nginx -t
```

```bash
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```

## 06 Adding TLS to your Nginx Reverse Proxy

1.**Install Certbot**

```bash
apt-get update
apt-get install software-properties-common
add-apt-repository ppa:certbot/certbot
apt-get update
apt-get install python-certbot-nginx
```

Certbot provides a plugin designed for the Nginx web server, automatizing most of the configuration work related with requesting, installing and managing the TLS certificate:

```bash
certbot --nginx
```

2\. **Request a valid** **Let’s Encrypt TLS certificate**:|\
Follow the prompts activate HTTPS.

```bash
Saving debug log to /var/log/letsencrypt/letsencrypt.log
Plugins selected: Authenticator nginx, Installer nginx

Which names would you like to activate HTTPS for?
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
1: your.domain.com
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Select the appropriate numbers separated by commas and/or spaces, or leave input
blank to select all options shown (Enter 'c' to cancel): 1
Obtaining a new certificate
Performing the following challenges:
http-01 challenge for your.domain.com
Waiting for verification...
Cleaning up challenges
Deploying Certificate to VirtualHost /etc/nginx/sites-enabled/reverse-proxy.conf

Please choose whether or not to redirect HTTP traffic to HTTPS, removing HTTP access.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
1: No redirect - Make no further changes to the webserver configuration.
2: Redirect - Make all requests redirect to secure HTTPS access. Choose this for
new sites, or if you're confident your site works on HTTPS. You can undo this
change by editing your web server's configuration.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Select the appropriate number [1-2] then [enter] (press 'c' to cancel): 2
Redirecting all traffic on port 80 to ssl in /etc/nginx/sites-enabled/reverse-proxy.conf

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Congratulations! You have successfully enabled https://your.domain.com

You should test your configuration at:
https://www.ssllabs.com/ssltest/analyze.html?d=your.domain.com
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
```

Your endpoint should be accessible now.

## 07 Check Endpoint is Accessible.

Now you should be able to access your node by an external endpoint. To check if your endpoint is accessible try the command below:

```bash
curl -H "Content-Type: application/json" -d '{"id":1, "jsonrpc":"2.0", "method": "eth_syncing","params": []}' https://your-bor-endpoint.com
```

{% hint style="success" %}
Success is indicated with a response similar to the following example:



```javascript
// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": {
    startingBlock: '0x384',
    currentBlock: '0x386',
    highestBlock: '0x454'
  }
}
// Or when not syncing
{
  "id":1,
  "jsonrpc": "2.0",
  "result": false
}
```

\

{% endhint %}
