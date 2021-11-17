# Node JSON-RPC Endpoint

After successfully deploying a node on Ankr you can get the endpoint from the Application details section as seen below:

_http://app-3ca28d07-1baa-4c3b-bf46-f2ccd91a43af.cls-dec3c32b-4f06-462f-b827-dee931d39a72.ankr.com_

```
//requestcurl -X GET http://app-3a95c00b-a28c-4975-9025-8ad66f9ca142.cls-a91a7dbc-1a23-42f6-a66f-876094349f03.ankr.com/v2/status -H  "accept: application/json"​//Response{   "catchpoint":"",   "catchpoint-acquired-blocks":0,   "catchpoint-processed-accounts":0,   "catchpoint-total-accounts":0,   "catchpoint-total-blocks":0,   "catchup-time":714828252684,   "last-catchpoint":"10000#PZQCLLFYLGXE6QM7A7YN7AIUUJKHYE2UTCAIHVA74QIY3M5F4BFA",   "last-round":10308,   "last-version":"https://github.com/algorandfoundation/specs/tree/5615adc36bad610c7f165fa2967f4ecfa75125f0",   "next-version":"https://github.com/algorandfoundation/specs/tree/5615adc36bad610c7f165fa2967f4ecfa75125f0",   "next-version-round":10309,   "next-version-supported":true,   "stopped-at-unsupported-round":false,   "time-since-last-round":3390170741}
```

In the next section, you will find a detailed description of the provided Algorand APIs endpoints which can also be consulted in the [Algorand official documentation](https://developer.algorand.org/docs/reference/rest-apis/algod/v2/)
