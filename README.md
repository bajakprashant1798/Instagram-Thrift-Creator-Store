# Instagram-Thrift-Creator-Store

# Thrift + Handmade Store Database Design

## About this project

This is a basic database design for a small Instagram-based store.  
The store sells two types of products:

- Thrift items (mostly single pieces)
- Handmade items (can have multiple quantities)

Initially, orders come from Instagram DMs / WhatsApp, but as the business grows, we need a proper system to manage products, orders, payments and shipping.

---
## ER Diagram
-- link for eraser: https://app.eraser.io/workspace/7Nx1gYjinvgYklLzlcWQ?origin=share

<img width="1545" height="1547" alt="Instagram-Thrift-Creator-Store_dark" src="https://github.com/user-attachments/assets/79b91aad-b40e-4bdc-ada0-b5a2d9a3ee7c" />


## What I tried to solve

- Store different types of products (thrift + handmade)
- Handle stock (single vs multiple quantity)
- Store customer details
- Manage orders with multiple products
- Track payment status
- Track shipping status

---

## Main Tables

### 1. Products
Stores all items.

- Has product_type → thrift / handmade
- Common data like name, price, description

---

### 2. Inventory
Handles stock.

- For thrift → quantity = 1  
- For handmade → quantity > 1  

---

### 3. Product Informations
Used for extra details like:

- size  
- color  
- condition (important for thrift items)

---

### 4. Categories
Simple category table for products.

---

### 5. Customers
Stores basic customer info:

- name  
- phone  
- address  

---

### 6. Orders
Stores order details.

- One customer can have multiple orders  
- Includes payment status and shipping status  

---

### 7. Order Items
This is important.

- One order can have multiple products  
- Stores quantity and price per item  

---

### 8. Payments
Linked to orders.

- One order → one payment (simple case)  
- Stores method (UPI, COD, etc.)

---

### 9. Shipping
Also linked to orders.

- One order → one shipment  
- Stores tracking info  

---

## Relationships (simple understanding)

- Customer → Orders (one to many)
- Order → Order Items (one to many)
- Product → Order Items (one to many)
- Product → Inventory (one to one)
- Order → Payment (one to many)
- Order → Shipping (one to many)

---

## Important design decisions

### Thrift vs Handmade

Instead of creating separate tables, I used:

product_type field

- thrift → usually single item  
- handmade → multiple quantity  

---

### One-to-One (Payment & Shipping)

I kept it simple:

- One order = one payment  
- One order = one shipping  

No partial payments or split delivery for now.

---

## Notes

- This is a basic version (not advanced e-commerce)
- No partial shipping
- No multiple payments
- Designed for small business use
- Have not done much thought on varchar and other types right now

---

## Future Improvements (maybe later)

- Multiple shipments per order  
- Partial payments  
- Product images table  
- Order status history  

