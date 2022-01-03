# Initial testing of the Erigon BSC Testnet Archive Node

This is a description of our process and initial results running Erigon BSC for Testnet. The Mainnet is still being synchronized and details will be published shortly.

{% hint style="info" %}
**NOTE:**

We intentionally ran a low spec server from Digital Ocean to demonstrate the high performance of Erigon for BSC.&#x20;
{% endhint %}

## 00 Hardware Setup

* Processor: 4 vCPU
* Memory: 8 GB
* OS: 160 GB
* Storage: 1TB disk for BSC Testnet Archive Data

## 01 Synchronization Process

The Testnet synchronization process starts from the very beginning:

![](<../../.gitbook/assets/Screenshot 2021-12-08 at 16.01.57.png>)

and proceeds all the way to the latest height at:

![](<../../.gitbook/assets/Screenshot 2021-12-08 at 16.02.03.png>)

{% hint style="success" %}
The synchronization process took **25 hours and 10 minutes.** \
\
:tada:It is worth considering that Erigon for BSC was only using a single CPU processor. \
We estimate that the sync process could 4-5 times faster than our trial. \
\
:thumbsup:It is also worth considering that this synchronization speed is still significantly faster than currrent Geth based clients.&#x20;
{% endhint %}

## 02 RPC Benchmarking

We used `ethspam` and `versus` to benchmark performance of the Erigon Client. We conducted tests with **100**, **200**, **300** requests concurrently. \
\
Erigon displayed results that outperformed Geth clients every time AND without a single **** error**.**\


If you compare the results below wit

#### 1. Erigon with 100 concurrent requests

![](<../../.gitbook/assets/Screenshot 2021-12-08 at 16.17.37 (1).png>)

![](<../../.gitbook/assets/Screenshot 2021-12-08 at 16.26.38.png>)

#### 2. Erigon with 200 concurrent requests

![](<../../.gitbook/assets/Screenshot 2021-12-08 at 16.27.17.png>)

#### 3. Erigon with 300 concurrent requests

![](<../../.gitbook/assets/Screenshot 2021-12-08 at 16.28.49.png>)

![](<../../.gitbook/assets/Screenshot 2021-12-08 at 16.29.26.png>)

#### 4. GETH Goerli Testnet with 100 concurrent requests

![](<../../.gitbook/assets/Screenshot 2021-12-08 at 16.32.13.png>)

## 03 Future Work&#x20;

Our focus going forward is to progress our collaboration with the Binance Smart Chain team with the following aims:\
\
1\. Continue to improve the performance of Erigon for BSC by utilizing full multi-core CPU capacity.

2\. Enable Validator mode
