# The procedure of seed selection 

All messages in the seed pool are categorized by their message types. Once the Message Guider determines which type to use in the next iteration, for example, a “preprepare” message, then the seed selector will dequeue the “preprepare” message queue for mutation, generate a new “preprepare” message, and send it to the target node. If there are any new bugs or new state/state transitions found in the target node, the new “preprepare” message will be regarded as interesting and saved to the seed pool for the next iteration.

![](./seed-selection.pdf)
