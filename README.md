Saga Pattern within a single microservice

Saga Coordinator - manages the transaction.
1. Payment Service - processes payments and refunds.
2. Inventory Service - reserves stock and releases it.
3. Shipping Service - ships orders and cancels them.

Transaction Flow
1. Process Payment -> Success -> Move to Step 2
2. Reserve Inventory -> Success -> Move to Step 3
3. Ship Order -> Success -> Order Completed
If any step fails, previous steps are rolled back.

Failure Handling

Failure Scenario                           Compensate                  
Payment Service --- -- Card declined-----No action needed
Inventory Service ---- Out of stock------Refund payment 
Shipping Service ----- No couriers-------Refund + release stock

