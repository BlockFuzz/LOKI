# Concepts descriptions

### The review

- The concept of "leader", "non-leader" and "follower" nodes are used in the text but not explained. Overall the explanation of how a (Byzantine) consensus protocol operates is rather rudimentary. It leaves out the complex parts of the protocol, such as handling view changes etc.

- Section 3.2: What are "Envelope" messages? Where are the "red bars" being referred to in the text? This explanation is confusing to follow without a description of what the implementation tries to achieve and how it works.

### The concepts and procedures explanation

The descriptions of these concepts are as follows:

- **Leader in PBFT**: the concept of ‘leader’ in a PBFT protocol is the same as the concept of ‘primary replica’ in the paper of PBFT [1]. In each round of the consensus, a leader is responsible for receiving the requests from the clients and multicasts the requests to other replicas. A leader is elected based on the equation: p = v mod |R|, where v represents the current view of the system while |R| means the number of all the replicas.
- **Non-leader**: the concept of ‘non-leader’ is in contrast to the ‘leader’ concept. In a PBFT system, the nodes which are not elected as the leader in each round are named a non-leader node.
- **Leader in Raft**: the concept of ‘leader’ in a Raft protocol is introduced from the Raft paper [2]. The leader can receive the transactions from the clients and broadcast them to other nodes. Only if a leader fails, a new leader will be elected in the Raft protocol.
- **Follower**: the concept of ‘follower’ is in contrast to the ‘leader’ in a Raft system. Nodes are named as ‘followers’ if they are not the current leader. In the leader election period, a follower can make a proposal and become a ‘candidate’ of the next leader.
- **Envelope messages**: the concept of the ‘envelope messages’ represents a specific message type named ‘Envelope’ in the Raft protocol of Hyperledger Fabric. This type of messages is used to pass transactions among blockchain nodes and clients. This message type contains the transactions content and the signature. 
- **red bars**: the concept of the ‘red bars’ refers to three bars with a red background in Figure 3. In particular, this concept represents the bar ‘process_message’, the bar ‘decrypt&validate’ and the bar ‘Channel_header’. 

#### The complex part of (Byzantine) consensus protocol: viewchanging

As for the complex part of (Byzantine) consensus protocol, such as handling view changes, a PBFT protocol carries out a view change when the primary replica has failed. When the timer of a replica expires, it suspects something is wrong with the current leader and starts a view change to move the system to view + 1. If a replica receives more than `2f + 1` view change messages, it will switch itself to the new view and calculate the new leader. 



#### What the implementation of the workflow in Figure 3 tries to achieve

The implementation of the workflow in Figure 3 tries to forward a message of Envelope type from a former leader to a new elected leader. In a Raft protocol, an Envelope message is forwarded from the clients to the leader. However, when a leader switching process is triggered, there are possibilities that some of the Envelope messages have already been received by the former leader. In that situation, it should send the messages to the new leader for processing. This process works like that: First, the former leader calls the function `process_message` and generates a new submit with `generate_submit`. Then, it calls the function `forward_to_leader` to send these messages to the new leader. After that, the new leader receives these messages with the function ‘ordered’ and processes them directly by the function `Channel_header` without validation.
[1] Practical byzantine fault tolerance. Castro M, Liskov B. 

[2] The raft consensus algorithm. Ongaro D, Ousterhout J.
