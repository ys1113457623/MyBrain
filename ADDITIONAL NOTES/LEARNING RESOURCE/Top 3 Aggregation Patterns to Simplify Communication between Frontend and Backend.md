---
tags:
  - SystemDesign
created:
  - 2025-01-12
review: 2025-01-12
---
## 📅 Date:  
**Sunday, January 12th 2025**  

## 🎯 Learning Objective:  
**What’s the goal for learning this concept?**  
- [ ] What is Central Aggregating Gateway
- [ ] Backend for frontend  
- [ ] GraphQL

---

## 🔑 Key Points (Dynamic):  

## **Central Aggregating Gateway 

**How it works**
Instead of calling multiple api's from the frontend, the gateway fetches data from sources, aggregates it, and delivers a unified response to the client.

**Benefits**
1. Simplifies the frontend
2. Centralised Logic
3. Better User Experience 

**Challenges**
1. Potential Bottleneck
2. Complex Middleware

## **Backend for Frontend ( BFF )
The BFF pattern takes aggregation to the next level by providing UI-specific backend tailored to each frontend application
**How it works**

Each frontend has its own backend service that fetches and aggregates data from various API's tailored to the specific needs of that platform 

**Benefits**
- Reduced Over fetching
- Improved Developer
- Simplified Frontend logic

**Challenges**
- Increased Maintenance
- Potential Duplications

## **GraphQL**
It is a flexible query language that has revolutionised data fetching by enabling clients to request precisely the data they need

**How it works**
Clients send queries to a single GraphQL endpoint, specifying exactly what data they require. The server then aggregates and fetches data from multiple sources to fulfil the request

**Benefits**
- Eliminates over-fetchning and under fetching 
- Dynamic querying 
- Single endpoint 

**Challenges**
- Complex schema design
- Performance Considerations
- Learning curve
 