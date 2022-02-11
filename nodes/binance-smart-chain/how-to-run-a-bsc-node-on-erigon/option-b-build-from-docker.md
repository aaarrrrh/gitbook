# Option B: Build from Docker

This option automatically builds from the latest docker image.&#x20;

#### 1.  Install Docker

Verify Installation&#x20;

```
docker --version
```

(Get Docker [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/))

#### 2. Create Container and run over image

```javascript
docker run -it ankrnetwork/erigon-for-bsc:latest erigon --chain=bsc --datadir=/srv/svc --metrics --metrics.addr=0.0.0.0 --metrics.port=6060 --private.api.addr=0.0.0.0:9090 --pprof --pprof.addr=0.0.0.0 --pprof.port=6061
```
