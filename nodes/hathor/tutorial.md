# /version

### Parameters <a href="#parameters" id="parameters"></a>

None

### Returns <a href="#returns" id="returns"></a>

Information about the connected node

### Example <a href="#example" id="example"></a>

```
//Request
curl "http://<your-app-id>.ankr.com/v1a/version" 

//Response
{
    "version": "0.38.4",
    "network": "mainnet",
    "min_weight": 14,
    "min_tx_weight": 14,
    "min_tx_weight_coefficient": 1.6,
    "min_tx_weight_k": 100,
    "token_deposit_percentage": 0.01,
    "reward_spend_min_blocks": 300,
    "max_number_inputs": 255,
    "max_number_outputs": 255

```

