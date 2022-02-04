# How to run a BSC Node on Erigon

## Introduction&#x20;

This guide will walk you through setting up and launching a BSC Node on Erigon. Here are the main benefits of running BSC on Erigon:

* Drastically reduced disk storage - 1.2TB for Archive Node, 430GB for Pruned Node.&#x20;
* Faster sync speed > 10 blocks per second&#x20;
* Fully bootstrapped archive node in <3days.&#x20;
* Crash resilience - Erigon’s database can withstand power failures. Modularity - P2P and web3 RPC services can be run as components.

If you want to be able to run a node without buying vast disk space then Erigon is going to make a massive difference.

### **00 Prerequisites**

**Storage:** 2TB on a single partition, 1.6TB state 200GB temp files (can symlink or mount folder \<datadir>/etl-tmp to another disk).

**RAM:** 16GB\
****\
******OS:** 64-bit

**Network Settings:**\
****Open up port 22 for SSH

Open port 5050 for both TCP and UDP traffic.

### **01 Install Dependencies**

Check you have Go installed. It should be at least version 1.16&#x20;

`go version` \
\
([https://go.dev/doc/install](https://go.dev/doc/install) if you don’t have the latest version)

## OPTION 1: Build from Sources

### **1. Clone BSC Erigon Repo and Launch the Node**

{% hint style="info" %}
Binance Smart Chain mode is available on the **develop** branch
{% endhint %}

```bash
git clone https://github.com/ledgerwatch/erigon --recursive
cd erigon
git checkout devel
make all
```

### 2. Run Erigon in BSC mode using binaries:

```
# for the node
erigon --chain=bsc --datadir=/datadir --metrics --metrics.addr=0.0.0.0 --metrics.port=6060 --private.api.addr=0.0.0.0:9090 --pprof --pprof.addr=0.0.0.0 --pprof.port=6061

# for rpcdaemon
rpcdaemon --datadir=/datadir --private.api.addr=erigon:9090 --txpool.api.addr=erigon:9090 --http.addr=0.0.0.0 --http.vhosts=* --http.corsdomain=* --http.api=eth,debug,net,trace,txpool --ws
```

## OPTION 2: Docker

### 1.  Install Docker

Verify Installation&#x20;

```
docker --version
```

(Get Docker [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/))

### 2. Run Instance

```
docker run -it thorax/erigon:devel erigon --chain=bsc --datadir=/datadir --metrics --metrics.addr=0.0.0.0 --metrics.port=6060 --private.api.addr=0.0.0.0:9090 --pprof --pprof.addr=0.0.0.0 --pprof.port=6061
```

### 3. Docker Compose&#x20;

```
version: '2.2'
services:
  erigon:
    #image: thorax/erigon:devel
    image: ankrnetwork/erigon-for-bsc:latest
    command: erigon --chain=bsc --datadir=/datadir --metrics --metrics.addr=0.0.0.0 --metrics.port=6060 --private.api.addr=0.0.0.0:9090 --pprof --pprof.addr=0.0.0.0 --pprof.port=6061
    #command: "sh /datadir/check.bash"
    volumes:
      - /root/svc/erigon:/datadir
    ports:
      - "30303:30303/tcp"
      - "30303:30303/udp"
      - "30304:30304/tcp"
      - "30304:30304/udp"
      - "9090:9090"
    restart: unless-stopped
  rpcdaemon:
    image: thorax/erigon:devel
    command: rpcdaemon --datadir=/datadir --private.api.addr=erigon:9090 --txpool.api.addr=erigon:9090 --http.addr=0.0.0.0 --http.vhosts=* --http.corsdomain=* --http.api=eth,debug,net,trace,txpool --ws
    pid: service:erigon # Use erigon's PID namespace. It's required to open Erigon's DB from another process (RPCDaemon local-mode)
    volumes:
      - /root/svc/erigon:/datadir
    ports:
      - "8545:8545"
      - "8546:8546"
    restart: unless-stopped
  nginx:
    image: nginx
    volumes:
      - /root/.acme.sh/:/root/.acme.sh/
      - ./nginx.conf:/etc/nginx/conf.d/00-default.conf
    ports:
      - "443:443"
    restart: always
```

\
\
\
