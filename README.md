This repository contains logs from experiments related to the research about orphan transactions in the Bitcoin network.

The subdirectories in the top directory represent 6 nodes over 2 rounds with varying orphan pool sizes. The table below gives more details on the subdirectories.

Name | Round | Pool size
:-----:|:-------:|:----------:
011 | 1 | 100
012 | 1 | 20
013 | 1 | 50
014 | 1 | 100
015 | 1 | 20
016 | 1 | 50
017 | 2 | 100
018 | 2 | 500
019 | 2 | 1000
020 | 2 | 100
021 | 2 | 500
022 | 2 | 1000

Each subdirectory contains files for orphan transaction related events. The following table details for each file whether it represents addition or removal of transactions from the orphan pool, and what causes these events.

Name | Type | Description
-----| -----| ------------
orphanTXsAdded.txt | Addition | Transactions added to the orphan pool
orphanTXsEvicted.txt | Removal | Orphan pool full
orpanTXsNodeRemoval.txt | Removal | Peer who sent the orphan transaction disconnected
orphanTXsRemoved.txt | Removal | Orphan transactions not valid (i.e., non-standard or insufficient fee)
orphanTXsResolved.txt | Removal | Missing parents received from peers
orphanTXsResolvedByBlock.txt | Removal | Missing parents received in blocks
orphanTXsTimeout.txt | Removal | Orphan transaction timeout

Each text file contains one entry per line in the following format
```
Mon Nov 18 11:06:13 2019 1574093173509801816 : efdca90da6f24fdef6755c26932d17dff4f29f8969e5458e5257ea8bb9d5322d
```
Below is a breakdown of the entry

Item | Description
---|---
```Mon Nov 18 11:06:13 2019``` | Human readable timestamp (in EST) of when the event occured
```1574093173509801816``` | Unix timestamp with nanosecond precision of when the event occured
```efdca90da6f24fdef6755c26932d17dff4f29f8969e5458e5257ea8bb9d5322d``` | ID of the transaction involved in the event

----------
If you find this data useful, please cite
```
@inproceedings{imtiaz2020orphan,
  title={Characterizing Orphan Transactions in the Bitcoin Network},
  author={Imtiaz, Muhammad Anas and Starobinski, David and Trachtenberg, Ari},
  booktitle={2020 IEEE International Conference on Blockchain and Cryptocurrency (ICBC)},
  year={2020},
  organization={IEEE}
}
```
