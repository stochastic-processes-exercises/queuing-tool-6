# Systems with multiple queues

The advantage of queuing tool has over the programs for writing queues that you wrote last week is that it can be used to model systems of queues.  In other words, we can use queuing tool to model the two connected queues that are indicated in the following diagram: 

![](seq-queue.png)

The code in `main.py` provides all the code required to set up and run a simulation of the queue shown in the figure above.  Lets go through this step by step in order to explain how we provide information on the network of queues to queuing tool.  The first thing we need to understand is this command:

```python
adj_list = {0: [1], 1: [2]}
```

This command sets the variable `adj_list` so that it provides information on the way the nodes in a graph are linked together.  The graph we have defined above has three nodes (labelled 0, 1 and 2).  Node 0 is connected to node 1 and node 1 is connected to node two.  The Queue servers that we will define will sit on the edges in this graph.  There will thus be one queue server on the edge between that connects node 0 to node 1 and a second queue server that sits on the edge that connects node 1 to node 2.  We tell queuing tool about the queue servers that are on each edge by defining the variable called `edge_list` as follows:

```python
edge_list = {0: {1: 1}, 1: {2: 2}}
```

This command tells queuing tool that the queue server on the edge that connects node 0 and node 1 is of type 1 and that the queue server on the edge that connects nodes 1 and 2 is of type 2.  These two types of queue server objects are then defined in the following code:

```python
q_classes = { 1: qt.QueueServer, 2: qt.QueueServer }
q_args = {
    1: {
        'num_servers': 1,
        'arrival_f': arr_f,
        'serivce_f': ser_order
    },
    2: {
        'num_servers': 1,
        'serivce_f': ser_tea
    },
}
```

Notice how the functions we have written and looked at in previous exercises are used to determine when customers arrive in the queue and how long it takes to server customers.  Notice, furthermore, that no `arrival_f` function is defined for the second queue as agents arrive in this queue when they have finished being served by the first queue server.
