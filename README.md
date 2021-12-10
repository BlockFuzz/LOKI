# LOKI

Blockchain consensus protocols are responsible for coordinating the nodes to make agreements on the transaction results, and bugs in their implementations may pose serious threats. Fuzzing is a promising technique for protocol vulnerability detection. However, existing fuzzers cannot deal with complex consensus states of distributed nodes, thus generating a large number of useless packets, inhibiting its effectiveness in reaching the deep logic of consensus protocols.

LOKI is a blockchain consensus protocol fuzzing framework which senses consensus states in real-time by masquerading as a node. First, LOKI dynamically builds a state model that records the state transition of each node. After that, LOKI adaptively generates the input targets, types and contents according to the state model. We implemented LOKI on four widely used commercial blockchain systems, including Go-Ethereum, Facebook Diem, IBM Fabric and WeBank FISCO-BCOS.

Compared with state-of-the-art tools such as Peach and Fluffy, LOKI improves the branch coverage by an average of 35.35% and 181.91%. Furthermore, LOKI has detected 14 serious previously unknown vulnerabilities with 4 CVEs assigned, while Peach and Fluffy can only detect 1 of them respectively.

* Code coverage

![geth_branch](https://github.com/BlockFuzz/LOKI/files/7681788/geth_branch.pdf)

![diem_branch](https://github.com/BlockFuzz/LOKI/files/7681791/diem_branch.pdf)

![fabric_branch](https://github.com/BlockFuzz/LOKI/files/7681792/fabric_branch.pdf)

![fisco_branch](https://github.com/BlockFuzz/LOKI/files/7681793/fisco_branch.pdf)


* Throughput

![tps_ethereum.pdf](https://github.com/BlockFuzz/LOKI/files/7681797/tps_ethereum.pdf)

![tps_diem.pdf](https://github.com/BlockFuzz/LOKI/files/7681798/tps_diem.pdf)

![tps_fabric.pdf](https://github.com/BlockFuzz/LOKI/files/7681799/tps_fabric.pdf)

![tps_fisco.pdf](https://github.com/BlockFuzz/LOKI/files/7681800/tps_fisco.pdf)

