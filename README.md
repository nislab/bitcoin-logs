This repository contains logs from experiments related to the research about churn in the Bitcoin network.

### Structure ###
```logNode_*.txt``` are the main log files for the experiment. The folder named ```logger``` contains information on session lengths for churning nodes.

### How to read the log files? ###
The listing below shows a sample log for a block received by a node.

```
Sat May 23 13:16:36 2020 1590254196802837823 : CMPCTRECIVED - compact block received
Sat May 23 13:16:36 2020 1590254196802837823 : CMPCTBLKHASH - 000000000000000000019629b45e48b6b3b8c1bb689f8601892f6a8b21c9caa1
Sat May 23 13:16:36 2020 1590254196806174539 : CMPCTSAVED - /home/ubuntu/.bitcoin/expLogFiles/86_cmpctblock.txt file created
Sat May 23 13:16:36 2020 1590254196806183064 : DMPMEMPOOL --- Dumping mempool to file: /home/ubuntu/.bitcoin/expLogFiles/86_mempoolFile.txt
Sat May 23 13:16:36 2020 1590254196860362567 : SUCCESSCMPCT - no missing transactions for cmpctblock #86
Sat May 23 13:16:36 2020 1590254196862389213 : TXNFILLSUCCESS - blocktxn message recived and successfully filled missing TXN: 000000000000000000019629b45e48b6b3b8c1bb689f8601892f6a8b21c9caa1
Sat May 23 13:16:36 2020 1590254196871963279 : CMPCTBLKACCPT - 000000000000000000019629b45e48b6b3b8c1bb689f8601892f6a8b21c9caa1
Sat May 23 13:16:51 2020 1590254211799459221 : PINGSENT --- ping requested for node abc.def.ghi.jkl:mnopq
Sat May 23 13:17:06 2020 1590254226799988893 : TRIGGER --- starting sync
Sat May 23 13:17:06 2020 1590254226800213651 : PINGSUCCSS --- node reachable: abc.def.ghi.jkl:mnopq, nonce: 0
Sat May 23 13:17:07 2020 1590254227159278817 : TXCOUNT --- tx in mempool: 26221 --- tx sync count: 1000 --- txs synced: 119
Sat May 23 13:17:07 2020 1590254227159311182 : VECGEN --- generated std::vector of tx to sync
Sat May 23 13:17:07 2020 1590254227159311182 : VECSAVED --- saved file of tx std::vector: /home/ubuntu/.bitcoin/expLogFiles/72_vecFile_invsent.txt
Sat May 23 13:17:07 2020 1590254227159704185 : SYNCSENT --- sync message sent to: abc.def.ghi.jkl:mnopq
Sat May 23 13:17:07 2020 1590254227159722571 : ENDTRIG --- sync ended
```

Each line in the log starts with the time at which the event was triggered. The time is divided in a human readable string and a UNIX timestamp (generated with the C++ ```steady_clock```). The following table defines what different events mean and what information is provided.

Event                | Meaning | Information provided
-------------------- | ------- | --------------------
```CMPCTRECIVED```   | A compact block was received from a peer |
```CMPCTBLKHASH```   | Hash of the compact block that was just received | Hash of the compact block
```CMPCTSAVED```     | Transactions in the compact block are saved to a text file | Path of the text file containing transactions in the compact block
```DMPMEMPOOL```     | A snapshot of the mempool after the compact block is received is saved to a text file | Path of the text file containg the snapshof of the mempool
```FAILCMPCT```      | The compact block could not be successfully reconstructed |
```REQSENT```        | Request for missing transactions is sent to the sending peer | Number of missing transactions
```REQSAVED```       | Information about the missing transactions that have been requested from the peer is saved to a text file | Path of the text file containing the information about the missing transactions
```TXNFILLSUCCESS``` | Missing transactions have been received from the peer |
```PINGSENT```       | Ping requested for a node | IP address of node for which ping is requested
```TRIGGER```        | Start synchronization |
```PINGSUCCSS```     | Node is reachable | IP address of node which is reachable
```TXCOUNT```        | Number of transactions to be synced | Number of transactions in the mempool when sync is triggered, minimum number of transactions preferred in a sync message, number of transactions actually synced
```VECGEN```         | Vector of transactions to sync is created successfully
```VECSAVED```       | Transactions to sync are saved to a file | Path of the text file containing the transactions to be synced
```SYNCSENT```       | MempoolSync message is sent to node | IP of node to whom MempoolSync message is sent
```ENDTRIG```        | End of syncrhonization round

### Control nodes ###
1. ```logNode_C1.txt```
2. ```logNode_C2.txt```
3. ```logNode_C3.txt```
4. ```logNode_C4.txt```

### Churning nodes (without MempoolSync) ###
1. ```logNode_X1.txt```
2. ```logNode_X2.txt```
3. ```logNode_X3.txt```
4. ```logNode_X4.txt```

### Churning nodes (with MempoolSync) ###
1. ```logNode_M1.txt```
2. ```logNode_M2.txt```
3. ```logNode_M3.txt```
4. ```logNode_M4.txt```
