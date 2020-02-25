This repository contains logs from experiments related to the research about churn in the Bitcoin network.

### How to read the log files? ###
The listing below shows a sample log for a block received by a node.

```
Fri Nov  9 18:32:11 2018 1225883205020776 : CMPCTRECIVED - compact block received from 142.4.211.170:8333
Fri Nov  9 18:32:11 2018 1225883205020776 : CMPCTBLKHASH - 00000000000000000009636519364378c1db859d41f20f476bca69702360a1fe
Fri Nov  9 18:32:11 2018 1225883218437226 : CMPCTSAVED - /home/node/.bitcoin/expLogFiles/1806_cmpctblock.txt file created
Fri Nov  9 18:32:11 2018 1225883218469440 : DMPMEMPOOL --- Dumping mempool to file: /home/node/.bitcoin/expLogFiles/1806_mempoolFile.txt
Fri Nov  9 18:32:11 2018 1225883302280494 : FAILCMPCT - getblocktxn message sent for cmpctblock #1806
Fri Nov  9 18:32:11 2018 1225883302280494 : REQSENT - cmpctblock #1806 is missing 1238 tx
Fri Nov  9 18:32:11 2018 1225883302280494 : REQSAVED -  /home/node/.bitcoin/expLogFiles/1806_getblocktxn.txt file created
Fri Nov  9 18:32:11 2018 1225883459205249 : TXNFILLSUCCESS - blocktxn message recived and successfully filled missing TXN
```

Each line in the log starts with the time at which the event was triggered. The time is divided in a human readable string and a UNIX timestamp (generated with the C++ ```steady_clock```). The following table defines what different events mean and what information is provided.

Event                | Meaning | Information provided
-------------------- | ------- | --------------------
```CMPCTRECIVED```   | A compact block was received from a peer | IP address of the sending peer
```CMPCTBLKHASH```   | Hash of the compact block that was just received | Hash of the compact block
```CMPCTSAVED```     | Transactions in the compact block are saved to a text file | Path of the text file containing transactions in the compact block
```DMPMEMPOOL```     | A snapshot of the mempool after the compact block is received is saved to a text file | Path of the text file containg the snapshof of the mempool
```FAILCMPCT```      | The compact block could not be successfully reconstructed |
```REQSENT```        | Request for missing transactions is sent to the sending peer | Number of missing transactions
```REQSAVED```       | Information about the missing transactions that have been requested from the peer is saved to a text file | Path of the text file containing the information about the missing transactions
```TXNFILLSUCCESS``` | Missing transactions have been received from the peer |

### Control nodes ###
1. logNode_node011.txt
2. logNode_node012.txt

### Churning nodes ###
1. logNode_node014.txt
2. logNode_node015.txt
3. logNode_node016.txt

----------
If you find this data useful, please cite
```
@inproceedings{imtiaz2019churn,
  title={Churn in the Bitcoin Network: Characterization and impact},
  author={Imtiaz, Muhammad Anas and Starobinski, David and Trachtenberg, Ari and Younis, Nabeel},
  booktitle={2019 IEEE International Conference on Blockchain and Cryptocurrency (ICBC)},
  pages={431--439},
  year={2019},
  organization={IEEE}
}
```
