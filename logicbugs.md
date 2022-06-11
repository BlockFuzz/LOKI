# Logic Bugs by LOKI

### The logic bugs detected by LOKI framework under the oracles of liveness and safety properties.

| Number |      project       | Description                                                  | Oracle   |
| :----- | :----------------: | ------------------------------------------------------------ | -------- |
| 1      | Hyperledger Fabric | Asynchronous sync procedures causes some proposals double processed.  | Safety |
| 2      |     FISCO-BCOS     | Bug in checking txpool limit when receive transactions from p2p | Liveness |
| 3      |     FISCO-BCOS     | The nodes change view frequently and stop generating blocks  | Liveness |
| 4      |     FISCO-BCOS     | A malicious leader may fake a proposal's header and transactions cannot be processed | Safety |
| 5      |        Diem        | Malicious nodes cause the failure of processing some transactions and stucks the chain  | Liveness   |
| 6      |    Go-Ethereum     | Section processing failed type=bloombits error="chain reorged during section processing" | Liveness |

### 

The table above shows 6 logic bugs which violate the properties of Safety and Liveness in Hyplerledger Fabric, Go-Ethereum Diem and FISCO-BCOS.

Bug#1 is assigned with a CVE id: [CVE-2022-26298](https://cve.mitre.org/cgi-bin/cvename.cgi?name=2022-26298)

Bug#2 is assigned with a CVE id: [CVE-2021-46359](https://cve.mitre.org/cgi-bin/cvename.cgi?name=2021-46359)
