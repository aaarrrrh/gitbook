---
description: How to deploy a Stafi Validator Node on Ankr
---

# Tutorial

### **Set up your** Stafi Validator Node on Ankr  <a href="#2e0e" id="2e0e"></a>

### Introduction:&#x20;

Stafi protocol is the first decentralized protocol unlocking liquidity of Staked assets.Stafi aims to solve the contradiction between Mainnet security and token liquidity in PoS consensus. The token holders are staking through staking contracts built in Stafi protocol, and then get alternative tokens(rToken ,such as rXTZ, rAtom, rDot, etc.), rTokens are tradable and it can get staking rewards from original chain at the same time. \_

1\. Head to [app.ankr.com](http://app.ankr.com) to deploy and click the **Deploy A Node** button.

![](<../../.gitbook/assets/image (84).png>)

2\. Search or scroll down to find the Stafi card, hover over it, select Validator Node and press **Deploy.**

![](<../../.gitbook/assets/image (49).png>)

3\. Now you are taken to the configuration page. The hardware configuration is set at the recommended system requirements, but you can choose to increase the specifications if you wish to do so, by using **Advanced** button.

4\. The platform also recommends a cluster, which is usually the one that has the most freely available resources. In this particular case, the recommended cluster is the United Kingdom cluster, but another cluster may be recommended for you, depending on your location.

![](<../../.gitbook/assets/image (77).png>)

5\. The **Project Name / Node Name** for use in the Ankr application is pre-filled. You can change it if you want (please note that only a small set of special characters are allowed in this name).

![](<../../.gitbook/assets/image (28).png>)

6\. Select Payment Method, choose number of months you want to run the node by moving the slider. The price and discount will increase when you extend the run time.

If later on you want to extend the node’s run time, you can add funds at any time.

![](<../../.gitbook/assets/image (48).png>)

7\. Click **Proceed to payment**

![](<../../.gitbook/assets/image (66).png>)

8\. Select payment method (USDT, ANKR erc20 or add your credit card)

![](<../../.gitbook/assets/image (80).png>)

9\. For this tutorial we will choose **Add New Credit Card**

![](<../../.gitbook/assets/image (79).png>)

10\. Provide all requested information and click **Pay with Credit Card**

![](<../../.gitbook/assets/image (25).png>)

11\. If all information is provided successfully the deployment will of the node will start

![](<../../.gitbook/assets/image (36).png>)

12\. Your node is now deployed and will sync with the network

13\. On the information tab you will find\*\* Status \*\*of your node, the **Name** of your node and the **Session Key**

![](<../../.gitbook/assets/image (62).png>)

Your node is up and running, now we need to get validator status.\
All details can be found using the following link: [https://docs.stafi.io/](https://docs.stafi.io)\
\
Below some high level steps to become a validator.

14\. When your node is fully synced, you can set the session keys. Your node is running in validator mode.

You need to tell the chain your Session keys . This is what associates your validator with your Controller account.

15\. In the Stafi Portal ([https://apps.stafi.io/#/explorer](https://apps.stafi.io/#/explorer)) go to **Staking > Account** **Actions**, and click "Set Session Key" on the bonding account. Copy the Session Key from the Ankr app in the field and click "Set Session Key".

Ankr:

![](<../../.gitbook/assets/image (85) (1).png>)

Stafi Portal:

![](<../../.gitbook/assets/image (32).png>)

16\. Now you are reading for validating.

Verify that your node is live and synchronized, head to Telemetry in Stafi Portal and find your node. Note that this will show all nodes on the Stafi network, which is why it is important to select a unique name in the Ankr app.

If everything looks good, go ahead and click on "Validate" in Stafi-apps.

* Payment preferences - You can specify the percentage of the rewards that will get paid to you. The remaining will be split among your nominators.

Click "Validate".

If you go to the "Staking" tab, you will see a list of active validators currently running on the network. At the top of the page, it shows the number of validator slots that are available as well as the number of nodes that have signaled their intention to be a validator. You can go to the "Waiting" tab to double check to see whether your node is listed there.

The validator set is refreshed every era. In the next era, if there is a slot available and your node is selected to join the validator set, your node will become an active validator. Until then, it will remain in the waiting queue. If your validator is not selected to become part of the validator set, it will remain in the waiting queue until it is. There is no need to re-start if you are not selected for the validator set in a particular era. However, it may be necessary to increase the number of FIS tokens staked or seek out nominators for your validator in order to join the validator set.

Congratulations! If you have followed all of these steps, and been selected to be a part of the validator set, you are now running a Stafi validator and start earning rewards!
