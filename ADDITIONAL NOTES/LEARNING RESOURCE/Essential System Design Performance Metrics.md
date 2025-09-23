## **1 - Availability**

**Availability** refers to the percentage of time your system is operational and accessible. It answers the question: _“Can users access the service when they need it?”_

Availability is usually measured in **“nines”**:
- **99%** availability = ~3.65 days of downtime per year
- **99.9%** = ~8.76 hours/year
- **99.99%** = ~52 minutes/year
- **99.999% (five nines)** = ~5.26 minutes/year

Achieving higher availability requires:
- **Load balancing** across instances
- **Health checks** and failover mechanisms
- **Redundancy and isolation** in infrastructure
- **Disaster recovery strategies**

## **2 - Throughput**

**Throughput** measures the amount of work your system can handle in a given time. It’s often measured in:
- **RPS** (Requests per Second)
- **QPS** (Queries per Second)
- **TPS** (Transactions per Second)

But throughput is not just a raw number—it reflects:
- **Concurrency**: how many users or processes can your system handle at once?
- **Efficiency**: are operations optimized, or is the system wasting time/resources?

To increase throughput:
- Optimize database queries and indexes
- Use distributed systems and sharding
- Implement asynchronous processing
- Remove performance bottlenecks (like blocking I/O or unnecessary API calls)

## **3 - Latency**

**Latency** is the time delay between a request and the system’s response. In simple terms: _How long does the system take to respond to a user or service?_

Latency can be broken down into:
- **Propagation Delay**: Time taken for the request to travel over the network
- **Processing Delay**: Time taken by servers to compute and generate a response
- **Round-Trip Time (RTT)**: Total time for a request to go to the server and come back

To reduce latency:

- Use **CDNs** to serve content closer to the user
- Implement **caching** to avoid repeated computation or DB hits
- Use **load balancing** to route requests to the nearest or fastest server
- Keep APIs and services lean—reduce unnecessary processing steps

## **4 - Scalability**

**Scalability** refers to how well your system can handle an increase in load, users, or data volume.

There are two primary ways to scale:

- **Vertical Scaling**: Add more power (CPU, RAM) to your existing servers. This is simple but has physical and cost limits.    
- **Horizontal Scaling**: Add more servers to distribute the load. This is more complex but highly effective for large-scale systems.

Scalable systems often embrace:

- **Stateless design** for easy horizontal scaling
- **Distributed storage and databases**
- **Event-driven architecture** for async workloads
- **Container orchestration** using tools like Kubernetes

## **5 - Redundancy**

**Redundancy** is the practice of duplicating critical components to avoid a single point of failure.

Two common redundancy strategies:
- **Active-Passive**: A backup system is on standby, ready to take over if the main one fails.
- **Active-Active**: Multiple instances operate in parallel, providing both load distribution and high availability.