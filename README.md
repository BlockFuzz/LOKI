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




# Quickstart

## LOKI for fabric

### prerequisites
Setup fabric network environment, can be found in https://hyperledger-fabric.readthedocs.io/en/release/prereqs.html.

### load LOKI-fabric image
```bash
cd fabric
docker import - smartbft/fabric-orderer:latest < LOKI-fabric.tar
```

### setup LOKI testnet & start fuzzing

```bash
cd fabric/testnet
./byfn generate
./byfn up
./byfn down
```


## LOKI for go-ethereum
### prerequisites
Setup geth network environment, can be found in https://priyalwalpita.medium.com/setting-up-the-go-ethereum-geth-environment-in-ubuntu-linux-67c09706b42.

### setup LOKI testnet & start fuzzing

```bash
cd geth/testnet
```
#### setup bootnode
```bash
../bin/bootnode -genkey bootnode.key
../bin/bootnode -nodekey bootnode.key
```
#### initialize node
```bash
for i in 1 2 3 4 5; do ../bin/geth --datadir ./node$i account new; done 
```
#### run loki-geth node

##### node1
```bash
../build/bin/geth --identity "ETH-node1" --datadir "node1" --port "30303" --maxpeers 10 --networkid 10086  --syncmode "full" --bootnodes "enode://5e49cd079bf47d4485867d4fb06a89f211b21be822a05cc8be6ce72b624aa94f4ac65e063fc4d0e62fe2342290bf5c880f6888534ae1df045f67186718d3c3f6@127.0.0.1:0?discport=30301" --mine --miner.etherbase 0xd192415624a039b24ad571f96cb438de9f0556a7 --miner.threads 1 --http --http.port 8545 console
```

##### node2
```bash
../build/bin/geth --identity "ETH-node2" --datadir "node2" --port "30304" --maxpeers 10 --networkid 10086  --syncmode "full" --bootnodes "enode://5e49cd079bf47d4485867d4fb06a89f211b21be822a05cc8be6ce72b624aa94f4ac65e063fc4d0e62fe2342290bf5c880f6888534ae1df045f67186718d3c3f6@127.0.0.1:0?discport=30301" --mine --miner.etherbase 0xd192415624a039b24ad571f96cb438de9f0556a7 --miner.threads 1 console
```

##### node3
```bash
../build/bin/geth --identity "ETH-node3" --datadir "node3" --port "30305" --maxpeers 10 --networkid 10086  --syncmode "full" --bootnodes "enode://5e49cd079bf47d4485867d4fb06a89f211b21be822a05cc8be6ce72b624aa94f4ac65e063fc4d0e62fe2342290bf5c880f6888534ae1df045f67186718d3c3f6@127.0.0.1:0?discport=30301" --mine --miner.etherbase 0xd192415624a039b24ad571f96cb438de9f0556a7 --miner.threads 1 console
```

##### node4
```bash
../build/bin/geth --identity "ETH-node4" --datadir "node4" --port "30306" --maxpeers 10 --networkid 10086  --syncmode "full" --bootnodes "enode://5e49cd079bf47d4485867d4fb06a89f211b21be822a05cc8be6ce72b624aa94f4ac65e063fc4d0e62fe2342290bf5c880f6888534ae1df045f67186718d3c3f6@127.0.0.1:0?discport=30301" --mine --miner.etherbase 0xd192415624a039b24ad571f96cb438de9f0556a7 --miner.threads 1 console
```

##### node5
```bash
../build/bin/geth --identity "ETH-node5" --datadir "node5" --port "30307" --maxpeers 10 --networkid 10086  --syncmode "full" --bootnodes "enode://5e49cd079bf47d4485867d4fb06a89f211b21be822a05cc8be6ce72b624aa94f4ac65e063fc4d0e62fe2342290bf5c880f6888534ae1df045f67186718d3c3f6@127.0.0.1:0?discport=30301" --mine --miner.etherbase 0xd192415624a039b24ad571f96cb438de9f0556a7 --miner.threads 1 console
```

#### ...

#### node_n


# Troubleshooting
Create an issue for questions and bug reports.

# Contribution
We welcome your contributions to LOKI! We aim to create an open-source project that is contributed by the open-source community. For general discussions about development, please refer to the issues. 
To contact us, please send an email to xxx.

# License
[Apache-2.0 License](https://github.com/BlockFuzz/LOKI/blob/main/LICENSE)

