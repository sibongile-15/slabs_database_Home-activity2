# Home Activity 2 - The Cost of Data Redundancy

## 1. The Dangers of Data Redundancy
When a company stores a customer's physical address in three different tables instead of referencing a single normalized customers table, it creates data redundancy which directly destroys data integrity because the same address now exists in multiple places with no single source of truth, so the database can easily hold different versions of the truth at the same time, and when the customer updates their address the update must be made in all three tables and if even one table is missed, forgotten, or fails to update, the database becomes inconsistent, leading to update anomalies where orders are shipped to the old address, invoices go to a different address, and customer service sees yet another address, causing confusion, wasted costs, and loss of trust in the data.

## 2. Primary vs. Foreign Key Enforcement
A Primary Key uniquely identifies each row in a parent table, while a Foreign Key in a child table is a reference to that Primary Key, and the Foreign Key constraint acts as a guardrail by forcing the database to check that reference before it allows any insert, update, or delete, which prevents orphan records - child records that point to a parent that does not exist. Concrete Example: In a Customers table, CustomerID is the Primary Key. In an Orders table, CustomerID is the Foreign Key. If you try to create an order for CustomerID = 999 and customer 999 does not exist in Customers, the database will reject it. If you try to delete a customer who still has orders, the database will block the delete so you don't end up with orders that belong to nobody.
EOF 
git add .
git commit -m "feat: The Cost of Data Redundancy homework submitted"
git push origin main 
