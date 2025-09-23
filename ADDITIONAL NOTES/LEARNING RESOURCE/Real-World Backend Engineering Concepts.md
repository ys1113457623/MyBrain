---
tags:
  - SystemDesign
created: 2025-05-18
review: 2025-05-18
---
# 🧠 Real-World Backend Engineering Concepts  

## 📅 Date:  
**Sunday, May 18th 2025**  

## 🔑 <Main />  

## Gossip Protocol

The gossip protocol is a method in distributed systems for nodes to share information with each other. Each node periodically selects another random node and shares all the information it know.s Over time , the process ensures that all nodes have the same information.

Use Cases:
- Maintaining membership lists in distributed systems.
- Detecting node failures.
- Spreading configuration updates. 
Pros:
- Scalable and fault-tolerant.
- No single point of failure. 
Cons:
- Information may take time to reach all nodes (eventual consistency).
- Can lead to redundant message transmissions.


## Backpressure
Backpressure is a mechanism used in systems to prevent overwhelming a component by controlling the flow of data. If a component can’t process incoming data quickly enough, Backpressure signals the sender to slow down or stop sending data temporarily 
**Use Cases:**
- Handling message processing failures.
- Debugging and error analysis.
- Ensuring message durability. 
**Pros:**
- Prevents message loss.
- Facilitates error handling and debugging.
**Cons:**
-  Requires additional monitoring and management.
- Can become a bottleneck if not handled properly.

## SAGA Pattern 
The SAGA Pattern is a design approach in microservices architecture to manage distributed transactions. Instead of a single transaction spanning multiple services, each service performs its own local transaction and publishes an event or message to trigger the next step. If a step fails, compensating transactions are executed to undo the previous steps.
**Use Cases:**
- Managing complex business processes across multiple services.
- Ensuring data consistency without distributed transactions. 
**Pros:**
- Improves system resilience.
- Avoids the need for distributed transactions. 
**Cons:**
- Increases complexity in handling compensating actions.
- Requires careful design and coordination.


## Dead letter queue (DLQ)
A Dead letter queue is a holding area for messages that cannot be delivered or processed successfully. Instead of losing these messages they are stored in the DLQ for further analysis or reprocessing.

**Use Cases:**
- Handling message processing failures.
- Debugging and error analysis.
- Ensuring message durability. 
**Pros:**
- Prevents message loss.
- Facilitates error handling and debugging.
**Cons:**
- Requires additional monitoring and management.
- Can become a bottleneck if not handled properly.


