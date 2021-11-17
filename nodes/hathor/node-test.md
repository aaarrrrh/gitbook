---
description: How to check if the node is working properly
---

# Node Test

## Check if the node is working properly

The first test would be to see if rewards are sent. This can be seen be accessing: [https://stake-nu.nucypher.community/](https://stake-nu.nucypher.community)\
\
After connecting with Metamask, you can go on the History tab to see if any transactions / rewards are made by the worker node. A succesful worker node should look like this:

![](broken-reference)



If Worker activity is not confirmed / rewards are not sent, we can look into the Prometheus Endpoint:

![](broken-reference)

In the Prometheus link, you can observe this address:

![](broken-reference)

Using that address you can access this page for giving the status report about the worker node, in my example, it would be:\
[https://23.19.61.172:9151/status](https://23.19.61.172:9151/status)

![](broken-reference)

In the next version, we will expose that website directly from the Ankr UI for a fast debugging of the node.\
\
Last, but not least, the fastest way to see if the node is working properly is to look for the transactions made by the worker, using etherescan and the worker eth address, in my example, a working node would have the following transactions:

![](broken-reference)

If I click on one outgoing transactions, we should see the following Function being called (commitToNextPeriod()):

![](broken-reference)

That function tells the NuCypher Smartcontract that the NuCypher Worker node is working properly.
