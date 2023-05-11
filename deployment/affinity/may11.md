###  Create 1 master node and 2 worker nodes – run app on node1 and db on  * node2 by using

*        Node selector
         Affinity
         Taints and tolerances


* first we create three t2 large instances  one is master and  another two instances working as a node

 * affinity is used to shedule the pods into node

 * taint is aused to can't shedule the pods into nodes

 * tolarance means we match the key value into node id

 * shedule select the node where we shedule the pods(works)

 



