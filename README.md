# PPM - Paxos Performance Model

PPM implements paxos modeling as described in my blog: http://charap.co/do-not-blame-only-network-for-your-paxos-scalability/

Some important files:
 
* local_multipaxos.py - multipaxos model. Contains default model parameters.
* sim_local_multipaxos.py - runs the multipaxos model. 
* sim_graph.py - plots the throughput vs latency graph for different cluster sizes.

------

## Model Parameters ##
sim_local_multipaxos.py can take various parameters to override the default settings:
* -m - runs Model mode. No pipeline or round simulation. Round latency is computed with queueing theory approximation for the pipeline. 
* -t - time to simulate. By default, 60 seconds of paxos runtime is modeled. Needed only for simulation mode
* -N - number of nodes in the cluster. Default: 3
* -q - Quorum size. By default majority quorum for given cluster size N. Always keep at majority, unless modeling flexible quorums
* -r - mean network RTT time in ms. Default: 0.427 ms
* -R - standard deviation of network RTT time. Default: 0.0476 ms
* -s - mean of message serialization overhead in ms
* -S - standard deviation of message serialization overhead in ms 
* -d - mean of message deserialization/processing overhead in ms
* -D - standard deviation of message deserialization overhead in ms
* -p - number of processing pipelines. This is roughly the number of cores at the node. Default: 1
* -z - mean separation between rounds in ms. This controls the target throughput. Default: 1000/6000
* -Z - standard deviation of separation between rounds. Default: 1000/3000
