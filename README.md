# Systems with multiple queues

The advantage of queuing tool has over the programs for writing queues that you wrote last week is that it can be used to model systems of queues.  In other words, we can use queuing tool to model the two connected queues that are indicated in the following diagram: 

![](seq-queue.png)

The code in `main.py` provides all the code required to set up and run a simulation of the queue shown in the figure above.  Lets go through this step by step in order to explain how we provide information on the network of queues to queuing tool.  The first thing we need to understand is this command:

```python
adj_list = {0: [1], 1: [2]}
```

This command sets the variable `adj_list` so that it provides information on the way the nodes in a graph are linked together.  The graph we have defined above has three nodes (labelled 0, 1 and 2).  Node 0 is connected to node 1 and node 1 is connected to node two.  The queues that we will define will sit on the edges in this graph.  There will thus be one queue on the edge between that connects node 0 to node 1 and a second queue that sits on the edge that connects node 1 to node 2. 
