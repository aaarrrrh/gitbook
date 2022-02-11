# Option C: Docker Compose

### OPTION C: Docker Compose&#x20;

1. Install `make`, `docker` and `docker-compose` on your local machine.\

2. Edit `docker-compose.bsc.yml` as follows:

```shell
version: '2.2'
services:
  erigon:
    #image: thorax/erigon:devel
    image: ankrnetwork/erigon-for-bsc:latest
    command: erigon --chain=bsc --datadir=/srv/svc --metrics --metrics.addr=0.0.0.0 --metrics.port=6060 --private.api.addr=0.0.0.0:9090 --pprof --pprof.addr=0.0.0.0 --pprof.port=6061
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
    #image: thorax/erigon:devel
    image: ankrnetwork/erigon-for-bsc:latest
    command: rpcdaemon --datadir=/srv/svc --private.api.addr=erigon:9090 --txpool.api.addr=erigon:9090 --http.addr=0.0.0.0 --http.vhosts=* 
    --http.corsdomain=* --http.api=eth,debug,net,trace,txpool --ws
    pid: service:erigon # Use erigon's PID namespace. It's required to open Erigon's DB from another process (RPCDaemon local-mode)
    volumes:
      - /root/svc/erigon:/srv/svc
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

3\. Run `docker-compose up` to start your node.

With your node up and running you can start to make calls.\
\
