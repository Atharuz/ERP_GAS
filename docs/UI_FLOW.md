# ERP User Interface Flow v1.1

## Overview

Dokumen ini menjelaskan alur navigasi dan proses utama pengguna dalam ERP Ciluba.

Flow dirancang mengikuti siklus bisnis:

```text
Master Data
↓
Purchasing
↓
Inventory
↓
Production
↓
Assembly
↓
Packaging
↓
Sales
↓
Shipping
↓
Reporting
```

---

# Main Navigation

```text
Dashboard

Master Data
├── Materials
├── Produced Components
├── Purchased Components
├── Products
├── Suppliers
├── Customers
├── Sales Channels
├── Categories
└── Units of Measure

Purchasing
├── Purchase Orders
├── Goods Receipts
└── Supplier Price History

Inventory
├── Stock Overview
├── Stock Movements
├── Stock Opname
└── Stock Adjustments

Production
├── Production Recipes
├── Work Orders

Assembly
├── Assembly Recipes
├── Assembly Orders

Packaging
├── Packaging Recipes
├── Packaging Execution

Sales
├── Sales Orders
├── Shipments
├── Customer History
└── Sales History

Reports
├── Dashboard Reports
├── Inventory Reports
├── Purchasing Reports
├── Production Reports
├── Assembly Reports
├── Packaging Reports
├── Sales Reports
└── Profitability Reports

System
├── Audit Logs
├── Activity Logs
└── Settings
```

---

# Dashboard Flow

```text
Dashboard
├── Revenue Summary
├── Gross Profit Summary
├── Inventory Value
├── Open Purchase Orders
├── Open Work Orders
├── Open Assembly Orders
├── Pending Shipments
├── Low Stock Alerts
└── Recent Activities
```

---

# Master Data Flow

## Materials

```text
Materials
↓
Material List
↓
Create Material
↓
Save
```

---

## Produced Components

```text
Produced Components
↓
Component List
↓
Create Component
↓
Save
```

---

## Purchased Components

```text
Purchased Components
↓
Component List
↓
Create Component
↓
Save
```

---

## Products

```text
Products
↓
Product List
↓
Create Product
↓
Save
```

---

## Suppliers

```text
Suppliers
↓
Supplier List
↓
Create Supplier
↓
Save
```

---

## Customers

```text
Customers
↓
Customer List
↓
View History
```

Customer juga dapat dibuat otomatis melalui Sales Order.

---

# Purchasing Flow

## Purchase Order Flow

```text
Purchase Orders
↓
Create Purchase Order
↓
Save Draft
↓
Issue PO
↓
Receive Goods
↓
Inventory Updated
```

---

## Goods Receipt Flow

```text
Goods Receipts
↓
Select Purchase Order
↓
Receive Goods
↓
Save Receipt
↓
Update Inventory
↓
Update Supplier Price History
```

---

# Inventory Flow

## Inventory Monitoring

```text
Stock Overview
↓
View Stock
↓
Filter
↓
Export
```

---

## Stock Movement

```text
Stock Movements
↓
View Transactions
↓
Filter
↓
Export
```

---

## Stock Opname

```text
Stock Opname
↓
Create Session
↓
Count Stock
↓
Save Result
```

No inventory changes.

---

## Stock Adjustment

```text
Stock Adjustment
↓
Review Opname Result
↓
Adjust Stock
↓
Inventory Updated
```

---

# Production Flow

## Recipe Setup

```text
Production Recipes
↓
Create Recipe
↓
Recipe Builder
↓
Save Draft
↓
Activate Version
```

---

## Work Order Flow

```text
Work Orders
↓
Create Work Order
↓
Select Recipe
↓
Released
↓
In Progress
↓
Completed
↓
Consume Materials
↓
Create Produced Components
```

---

# Assembly Flow

## Recipe Setup

```text
Assembly Recipes
↓
Create Recipe
↓
Recipe Builder
↓
Save Draft
↓
Activate Version
```

---

## Assembly Order Flow

```text
Assembly Orders
↓
Create Assembly Order
↓
Select Recipe
↓
Released
↓
In Progress
↓
Completed
↓
Consume Components
↓
Create Product
```

---

# Packaging Flow

## Recipe Setup

```text
Packaging Recipes
↓
Create Recipe
↓
Recipe Builder
↓
Save Draft
↓
Activate Version
```

---

## Packaging Execution Flow

```text
Packaging Execution
↓
Create Execution
↓
Select Product
↓
Released
↓
In Progress
↓
Completed
↓
Consume Packaging Material
↓
Add Packaging Cost
↓
Mark Ready To Ship
```

---

# Sales Flow

## Sales Order Flow

```text
Sales Orders
↓
Create Sales Order
↓
Customer Lookup
↓
Auto Create Customer (If Needed)
↓
Add Products
↓
Save Draft
↓
Confirm Order
↓
Reserve Inventory
```

---

## Reservation Logic

```text
Ready To Ship
-
Reserved
=
Available
```

---

## Validation

```text
Order Qty
≤
Available Qty
```

---

## Cancel Sales Order

```text
Sales Order
↓
Cancel
↓
Release Reservation
```

---

# Shipping Flow

## Shipment Flow

```text
Shipments
↓
Create Shipment
↓
Select Sales Order
↓
Generate Shipment
↓
Ship Order
↓
Release Reservation
↓
Reduce Inventory
↓
Recognize Revenue
↓
Recognize HPP
```

---

# Customer History Flow

```text
Customer
↓
Open Customer
↓
View Orders
↓
View Revenue
↓
View Purchase History
```

---

# Sales History Flow

```text
Sales History
↓
Filter
↓
Analyze Sales
↓
Export
```

---

# Reporting Flow

## Inventory Reports

```text
Reports
↓
Inventory Reports
├── Stock Balance
├── Stock Movement
└── Low Stock
```

---

## Purchasing Reports

```text
Reports
↓
Purchasing Reports
├── Purchase Orders
└── Supplier Price History
```

---

## Production Reports

```text
Reports
↓
Production Reports
├── Work Order History
└── Production Cost Analysis
```

---

## Assembly Reports

```text
Reports
↓
Assembly Reports
├── Assembly History
└── Product Cost Analysis
```

---

## Packaging Reports

```text
Reports
↓
Packaging Reports
└── Packaging History
```

---

## Sales Reports

```text
Reports
↓
Sales Reports
├── Sales History
├── Product Performance
├── Channel Performance
└── Customer Performance
```

---

## Profitability Reports

```text
Reports
↓
Profitability Reports
├── Gross Profit
└── Product Profitability
```

---

# Audit Flow

## Audit Logs

```text
Audit Logs
↓
Filter
↓
View Changes
```

---

## Activity Logs

```text
Activity Logs
↓
Filter
↓
View Activities
```

---

# End-to-End Business Flow

```text
Materials Purchased
↓
Goods Receipt
↓
Inventory

Raw Materials
↓
Work Order
↓
Produced Components

Produced Components
+
Purchased Components
↓
Assembly Order
↓
Products (Assembled)

Products
+
Packaging Materials
↓
Packaging Execution
↓
Ready To Ship Products

Sales Order
↓
Inventory Reservation

Shipment
↓
Inventory Reduction
↓
Revenue Recognition
↓
HPP Recognition
```

---

# MVP Exclusions

Tidak termasuk dalam MVP:

```text
Purchase Request

Approval Workflow

Invoice Management

Accounts Receivable

Payment Tracking

POS Module

Multi Warehouse

Multi Company
```
