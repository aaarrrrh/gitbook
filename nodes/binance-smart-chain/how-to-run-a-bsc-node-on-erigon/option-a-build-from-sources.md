# Option A: Build from Sources

This option involves compiling and building from the latest development code.&#x20;

{% hint style="danger" %}
**BE AWARE:**&#x20;

**This section is still being tested. We recommend the Docker options whilst this is under review. 11th Feb 2022**
{% endhint %}



### **01 Install Dependencies**

1. Check you have **Go** installed. It should be at least version 1.16&#x20;

```go
go version 
```

```go
wget https://go.dev/dl/go1.17.6.linux-amd64.tar.gz
sudo tar -xvf go1.17.6.linux-amd64.tar.gz
sudo mv go /usr/local
export PATH=$PATH:/usr/local/go/bin && echo "export PATH=$PATH:/usr/local/go/bin" >> ~/.profile
```

2\. Install **Build Essentials**

```bash
sudo apt update && sudo apt install build-essential
```

#### **1. Create an /srv/svc Directory and move into it.**

```shell
# -p flag ensures all files are included. 
mkdir -p /srv/svc
cd /srv/svc
```

#### **2. Clone BSC Erigon Repo and Launch the Node**

{% hint style="info" %}
Binance Smart Chain mode is available on the **develop** branch
{% endhint %}

```bash
git clone https://github.com/ledgerwatch/erigon --recursive
```

```
git checkout devel
```

```
make all
```

You can see the sequence of updates as follows:\
_Builds erigon_\
_Builds hack_\
_Builds rpctest_\
_Builds state_\
_Builds pics_\
_Builds rpcdaemon_\
_Builds integration tests_\
_Builds MDBX DB File_\
_Builds Sentry_\
_Builds txpool_

To view all commands run the following\
`erigon --help`

#### 2. Run Erigon in BSC mode using binaries:

```javascript
# for the node
erigon --chain=bsc --datadir=/srv/svc --metrics --metrics.addr=0.0.0.0 --metrics.port=6060 --private.api.addr=0.0.0.0:9090 --pprof --pprof.addr=0.0.0.0 --pprof.port=6061

# for rpcdaemon
rpcdaemon --datadir=/srv/svc --private.api.addr=erigon:9090 --txpool.api.addr=erigon:9090 --http.addr=0.0.0.0 --http.vhosts=* --http.corsdomain=* --http.api=eth,debug,net,trace,txpool --ws
```

You should see something like this:

```shell
$ erigon --chain=bsc --datadir=~/datadir --metrics --metrics.addr=0.0.0.0 --metrics.port=6060 --private.api.addr=0.0.0.0:9090 --pprof --pprof.addr=0.0.0.0 --pprof.port=6061
INFO[02-04|12:44:08.488] Starting metrics server                  addr=http://0.0.0.0:6060/debug/metrics/prometheus
INFO[02-04|12:44:08.491] Starting pprof server                    cpu="go tool pprof -lines -http=: http://0.0.0.0:6061/debug/pprof/profile?seconds=20" heap="go tool pprof -lines -http=: http://0.0.0.0:6061/debug/pprof/heap"
INFO[02-04|12:44:08.492] Build info                               git_branch=devel git_tag=v2021.12.03 git_commit=502e933029b6d9b8b06e13f2561109434ddb8a35
INFO[02-04|12:44:08.492] Starting Erigon on                       devnet=bsc
INFO[02-04|12:44:08.502] Maximum peer count                       ETH=100 total=100
INFO[02-04|12:44:08.504] Set global gas cap                       cap=50000000
```

