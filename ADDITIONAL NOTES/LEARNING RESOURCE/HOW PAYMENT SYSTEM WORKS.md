---
tags:
  - SystemDesign
created: 2025-05-18
review: 2025-05-18
---
p
# 🧠 HOW PAYMENT SYSTEM WORKS

## 📅 Date:  
**Sunday, May 18th 2025** 
## <MAIN />

### 🧾 Part 1: Initiating the Payment

When you click the ‘Pay’ button on a website or app the system creates a Payment Details object. This object contains all the necessary information about your order, such as the items purchases, total amount, and payment method

### 🔄 Part 2: Processing the Payment

The Payment details are then sent to a Payment Service which handle the transaction. This service communicated with various entities like banks and payment gateways to process your payment
![[Pasted image 20250518182049.png]]

### Payment Service

Payment service calls the payment handler for different order separately and store the payment information in payments Db
###   🏦 Executing the Payment
Payment Handler, which is responsible for carrying out the actual transaction. This involves debiting your account and crediting the merchant’s account.
![[Pasted image 20250518182558.png]]


### 📘 Part 4: Recording the Transaction
After the payment is executed, the system updates the Ledger and Wallet services. The ledger records the transaction details for accounting purposes, while the wallet updates the balances of the involved parties.

![[Pasted image 20250518182643.png]]