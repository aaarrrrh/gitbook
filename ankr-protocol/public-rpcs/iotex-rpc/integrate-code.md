# Integrate Code

## web3 library

### ![](<../../../.gitbook/assets/Screenshot 2021-11-01 at 13.26.10.png>)clientVersion

```
https://rpc.ankr.com/iotex
```

### Example Request

```bash
curl https://rpc.ankr.com/iotex \
>   -X POST \
>   -H "Content-Type: application/json" \
>   --data '{"jsonrpc":"2.0","method":"web3_clientVersion","params":[],"id":1}'
```

### Example Response

```javascript
{"jsonrpc":"2.0","id":1,"result":"v1.6.2-rc10/go version go1.17.5 linux/amd64"}
```
