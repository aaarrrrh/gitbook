# How to run a Fantom Full Node

## Introduction

This guide will walk you through setting up and launching a \*\*Fantom Full Node **that is r**ead only. \*\*

### **Set up Flow**

**00 Prerequisites** - Describes recommended and minimum hardware requirements\
**01 Install Dependencies** - Download all the necessary dependencies required to set up and launch a Fantom Full Node.\
**02. Checkout and build go-opera**\
**03 Launch your Node**\\

***

## 00 Prerequisites

**Minimal Hardware Requirements**

4 core\
8 RAM\
1.5TB SSD

**Recommended Hardware Requirements**

8 core\
16 RAM\
1.5TB SSD

Ubuntu Server 20.04 LTS (64-bit).

#### **Network Settings** <a href="#network-settings" id="network-settings"></a>

* Open up **port 22 for SSH**
* Open\*\* port 5050\*\* for both TCP and UDP traffic.

## 01 Install Dependencies

Whilst logged in as the new user via SSH

**1.Install required Build Tools**

```bash
# Install build-essentials
$ sudo apt-get install -y build-essential
```

**2. Install Go**

```bash
# Install go
$ wget https://dl.google.com/go/go1.15.10.linux-amd64.tar.gz
$ sudo tar -xvf go1.15.10.linux-amd64.tar.gz
$ sudo mv go /usr/local
```

* Export the required Go paths:

```bash
# Export go paths
$ vi ~/.bash_aliases

# Append the following lines
export GOROOT=/usr/local/go
export GOPATH=$HOME/go
export PATH=$GOPATH/bin:$GOROOT/bin:$PATH
```

* Verify your Go installation

```bash
# Verify go installation
$ go version
```

## **02. Checkout and build go-opera**

```bash
# Checkout and build go-opera
$ git clone https://github.com/Fantom-foundation/go-opera.git
$ cd go-opera/
$ git checkout release/1.0.2-rc.5
$ make
```

* Verify your Opera installation

```bash
$./build/opera help​
VERSION:1.0.2-rc.5
```

* Ensure you have the latest version of a node for the Opera Network by checking this [Fantom repo](https://github.com/Fantom-foundation/lachesis\_launch)

## 03 Launch your Node

**1.Download the Genesis file**

```bash
mkdir -p $HOME/fantom
wget https://opera.fantom.network/mainnet.g - P $HOME/fantom/
```

**2. Start a read-only node**

```bash
./build/opera --metrics  --cache 64000 --genesis
$HOME/fantom/mainnet.g --nousb --http --http.addr '0.0.0.0' --http.port 8545 --http.corsdomain "*" --http.vhosts "*" --ws --ws.addr '0.0.0.0' --ws.port 8546  --ws.origins '0.0.0.0' --graphql --graphql.corsdomain '*' --graphql.vhosts '*' --datadir "$HOME/fantom/node" --http.api "net,eth,web3" --ws.api "net,eth,web3"
```
