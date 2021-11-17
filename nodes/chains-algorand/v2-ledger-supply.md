# /v2/ledger/supply

Get the current supply reported by the ledger.

## Parameters  <a href="parameters" id="parameters"></a>

None

## Returns <a href="returns" id="returns"></a>

Supply represents the current supplies of MicroAlgos in the system

## Example <a href="example" id="example"></a>

```
//Requestcurl -X GET http://.ankr.com/v2/ledger/supply -H  "accept: application/json"​//Response{   "current_round":58341,   "online-money":981165186795720,   "total-money":981165186795720}​
```
