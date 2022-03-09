# Logic Bugs by LOKI



### The logic bugs detected by LOKI framework under the oracles of liveness and safety properties.

| Number |      project       | Description                                                  | Oracle   |
| :----- | :----------------: | ------------------------------------------------------------ | -------- |
| 1      | Hyperledger Fabric | panic: Node 9's in flight proposal sequence is 18 while its last decision sequence is 19 | Liveness |
| 2      | Hyperledger Fabric | ERRO 07d config currently at sequence 4, cannot validate config at sequence 2 | Safety   |
| 3      | Hyperledger Fabric | Repeatedly creating same channel quickly cause unrecoverable orderer panic | Liveness |
| 4      |    Go-Ethereum     | Section processing failed type=bloombits error="chain reorged during section processing" | Liveness |
| 5      |    Go-Ethereum     | Failed to journal state snapshot err="snapshot [*] missing"  | Liveness |
| 6      |     FISCO-BCOS     | The nodes change view frequently and stop generating blocks  | Liveness |
| 7      |     FISCO-BCOS     | A malicious node sends an invalid transaction to other nodes when they send a proposal to it | Liveness |
| 8      |     FISCO-BCOS     | Multi-thread bugs and the trsancations cannot be processed anymore | Safety   |
| 9      |     FISCO-BCOS     | Some transactions cannot be processed due to deadlock        | Safety   |
| 10     |     FISCO-BCOS     | Bug in checking txpool limit when receive transactions from p2p | Liveness |
| 11     |     FISCO-BCOS     | block not be executed if the synchronization and consensus execute it before the `addExecutor` | Liveness |

### 

The table above shows 11 logic bugs which violate the properties of Safety and Liveness in Hyplerledger Fabric, Go-Ethereum and FISCO-BCOS

Bug#10 is assigned with a CVE id: [CVE-2021-46359](https://cve.mitre.org/cgi-bin/cvename.cgi?name=2021-46359)
