# Algorithm formalization for algorithm 1 & 2

### The review

- Algorithms 1 and 2: Please formalise the approaches to update the state model and target states better. As it stands, the description of the algorithm resembles pseudocode that calls many functions whose behaviour is not clear.

### Formalization of the algorithms



##### In Algorithm 1 State Model updating:

- Function **checkNewMsgType(msg)** means verifying whether the “msg” is a new message that's never been observed before.

- Function **checkNewMsgId(msg)** means checking if the sender ID of the “msg” is a new ID that's never been observed before. 

- Function **getChainById(ID)** means getting a state chain from the state model according to the sender ID.

- Function **record(msg)** means recording this new “msg” to the message pool. 

- Function **root.newchild(chain)** means creating a new state chain and appending it to the root node. 

- Function **root.** **removeChild(chain)** means deleting a new state chain from the root node.



#####  In Algorithm 2 Target state determination: 

- Function **root.getchainStateById (peer.Id)** means getting a state chain from the state model according to the peer’s ID.

- Function **chain.transfer(p)** means given a random number p, return a target next type according to the state model.

- Function **mutate(msg)** means given a msg, call a related mutator to mutate the msg, and return the new mutated msg.

- Function **p2p.send(msg)** means utilizing the p2p network to send msg to the target nodes.

- Function **isNewState** **(feedback))** means checking whether the feedback information contains new state found. 

- Function **isnewTransition** **(feedback)** means checking whether the feedback information contains new state transition found. 

- Function **chain.updateProbability** **(p)** means updating related state transition probability in the state chain.
