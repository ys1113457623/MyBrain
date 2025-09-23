---
tags: #learning #{{title}}  
created: 2025-02-08  
review: 2025-02-08  
---

# 🧠 GRPC  

## 📅 Date:  
**Saturday, February 8th 2025**  

## 🎯 Learning Objective:  
**What’s the goal for learning this concept?**  
- [ ] Understand core principles  
- [ ] Apply to project/work  
- [ ] Teach someone else  

---

## 🔑 CORE PRINCIPLES  

#### **WHAT IS GRPC ?**
- GOOGLE REMOTE PROCEDURE CALL
- ALLOWS DIFFERENT MACHINES TO COMMUNICATE WITH EACH OTHER
- USES PROTOCOL BUFFER AS A DATA FORMAT
- SUPPORTS BIDIRECTIONAL STEAMING

#### **REALTIME STREAMING IN GRPC**

| **Type**                    | **Request** | **Response** | **Use Case Example**             |
| --------------------------- | ----------- | ------------ | -------------------------------- |
| **Unary**                   | 1           | 1            | Place an order                   |
| **Server Streaming**        | 1           | Stream       | Track order delivery             |
| **Client Streaming**        | Stream      | 1            | Upload a large video file        |
| **Bidirectional Streaming** | Stream      | Stream       | Live chat between user & support |

