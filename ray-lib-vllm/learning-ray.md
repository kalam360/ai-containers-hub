# Notes
- Ray is also flexible when it comes to heterogeneity of computations.
- All non-trivial abstractions, to some degree, leaky.
- some tasks might have to run on a GPU, while others run best on a couple of CPU cores. Ray provides you with that flexibility.
- A low-level, distributed computing framework for Python with a concise core API and tooling for cluster deployment called Ray Core.6
- A set of high-level libraries built and maintained by the creators of Ray. This includes the so-called Ray AIR to use these libraries with a unified API in common machine learning workloads.
- A growing ecosystem of integrations and partnerships with other notable projects that span many aspects of the first two layers. 
- You program against the so- called driver, the program root, which lives on the head node. The driver can run jobs, a collection of tasks, that are run on the nodes in the cluster.
- pecifically, you can run the entire Dask ecosystem on top of a Ray Cluster using the Dask-on-Ray scheduler, or you can use the Spark on Ray project to integrate your Spark workloads with Ray. Likewise, the Modin project is a distributed drop-in replacement for Pandas DataFrames that uses Ray (or Dask) as a distributed execution engine (“Pandas on Ray”).


| API Call       | Description                                                                                       |
|----------------|---------------------------------------------------------------------------------------------------|
| `ray.init()`   | Initializes your Ray Cluster. Pass in an address to connect to an existing cluster.               |
| `ray.put()`    | Puts values into Ray’s object store.                                                              |
| `.remote()`    | Runs actor methods or tasks on your Ray Cluster and is used to instantiate actors.                |
| `@ray.remote`  | Turns functions into tasks and classes into actors.                                               |
| `ray.get()`    | Gets values from the object store. Returns the values you’ve put there or that were computed by a task or actor. |
| `ray.wait()`   | Returns two lists of object references, one with finished tasks we’re waiting for and one with unfinished tasks. |


- Each worker has a unique ID, an IP address, and a port by which they can be referenced.
- But who tells them what to do and when? A worker might be busy already, it may not have the proper resources to run a task (e.g., access to a GPU), and it might not even have the values it needs to run a given task. On top of that, workers have no knowledge of what happens before or after they’ve executed their workload; there’s no coordination.
- To address these issues, each worker node has a component called Raylet. Think of Raylets as the smart components of a node that manage the worker processes. Raylets are shared between jobs and consist of two components, a task scheduler and an object store.
