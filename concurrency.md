When determining the appropriate corePoolSize for a thread pool on a system with 10 CPU cores, you should consider several factors:

Number of Cores: You have 10 physical CPU cores, so setting the corePoolSize close to this value can allow your application to make full use of the available CPU resources.

Type of Tasks: If your tasks are CPU-bound (they involve significant computational work), setting the corePoolSize closer to the number of CPU cores can help maximize CPU utilization.

Task Duration: If your tasks are short-lived, you might be able to have a larger thread pool size without encountering excessive context-switching overhead. However, if your tasks are long-running, having too many threads might lead to contention and inefficiency due to frequent context switching.

Concurrency Level: Consider the expected level of concurrency in your application. If you anticipate a high degree of parallelism and many tasks being executed simultaneously, you might set the corePoolSize closer to the number of CPU cores.

Resource Constraints: Keep in mind that each thread consumes system resources, including memory. Having too many threads can lead to memory exhaustion and decreased performance due to excessive context switching.

Workload: Consider the overall workload of your application. If your application is running on a dedicated server with little other activity, you can afford to allocate more threads. However, if your application shares resources with other applications, be mindful of resource contention.

As a starting point, you could set the corePoolSize to a value between 8 and 10, which would allow each core to be actively utilized. This value would ensure that you have a thread available for each core while leaving room for other system tasks and preventing excessive thread contention.

Remember that tuning thread pool size is often an iterative process. Monitor the performance and resource utilization of your application under different workloads, and adjust the corePoolSize as needed. Additionally, consider benchmarking and testing your application to find the optimal corePoolSize that balances concurrency, resource utilization, and system performance.
