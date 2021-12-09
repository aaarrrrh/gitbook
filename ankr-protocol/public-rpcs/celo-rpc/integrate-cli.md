# Integrate CLI

## Celo

## web3 library

### ![](<../../../.gitbook/assets/Screenshot 2021-11-01 at 13.26.10.png>)clientVersion

```
https://rpc.ankr.com/celo
```

### Example Request

```shell
curl https://rpc.ankr.com/celo \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{"jsonrpc":"2.0","method":"web3_clientVersion","params":[],"id":1}'
```

### Example Response

```javascript
{"jsonrpc":"2.0","id":1,"result":"celo/v1.4.1-stable-0a6286b2/linux-amd64/go1.17.3"
```
