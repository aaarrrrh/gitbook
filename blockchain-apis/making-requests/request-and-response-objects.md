# Request & Response Objects

#### THE REQUEST OBJECT&#x20;

The Request object has the following attributes:

{% tabs %}
{% tab title="Request Object Attributes" %}
```javascript
	"jsonrpc":"2.0",
	"method":"eth_protocolVersion",
	"params":[],
	"id":67
```
{% endtab %}
{% endtabs %}

**jsonrpc: **A String specifying the version of the JSON-RPC protocol. MUST be exactly “2.0”.

**method: **A String containing the name of the method to be invoked. \
Method names that begin with the word rpc followed by a period character (U+002E or ASCII 46) are reserved for rpc-internal methods and extensions and MUST NOT be used for anything else.

**params: **A Structured value that holds the parameter values to be used during the invocation of the method. This member MAY be omitted.

**id: **An identifier established by the Client that MUST contain a String, Number, or NULL value if included. If it is not included it is assumed to be a notification. The value SHOULD normally not be Null and Numbers SHOULD NOT contain fractional parts.

When an RPC call is made, the Server MUST reply with a Response object.&#x20;

#### THE RESPONSE OBJECT

The Response object has the following attributes:

{% tabs %}
{% tab title="Example Request Object" %}
```bash
{
  "jsonrpc":"2.0",
  "id":"1",
  "result":"0x60e"
}
```
{% endtab %}
{% endtabs %}

**jsonrpc: **A String specifying the version of the JSON-RPC protocol. MUST be exactly “2.0”.&#x20;

**result: **This member is REQUIRED on success. This member MUST NOT exist if there was an error invoking the method. The value of this member is determined by the method invoked on the Server.

**error: **This member is REQUIRED on error. This member MUST NOT exist if there was no error triggered during invocation. The value for this member MUST be an Object including `code` field and `message` field.

**id: **This member is REQUIRED. It MUST be the same as the value of the id member in the Request Object. If there was an error in detecting the id in the Request object (e.g. Parse error/Invalid Request), it MUST be Null.

