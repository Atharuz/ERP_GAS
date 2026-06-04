# Ciluba ERP - UI Flow Design v1.0

## Purpose

Dokumen ini mendefinisikan alur penggunaan aplikasi ERP Ciluba.

Dokumen ini menjadi dasar:

* UI Design
* UX Design
* Navigation
* Apps Script Pages
* Permission Design

---

# User Roles

## Owner

Hak akses penuh.

Fokus:

* Monitoring
* Purchasing
* Reports
* Master Data

---

## Production

Fokus:

* Inventory
* Production
* Assembly
* Packaging
* Shipping

---

## Admin

Fokus:

* Sales Order
* Customer
* Shipping

---

# Main Navigation

Dashboard

Master Data

Purchasing

Inventory

Production

Assembly

Sales

Shipping

Reports

Settings

---

# Dashboard Flow

Login

↓

Dashboard

↓

View Business Summary

Widgets:

* Revenue Today
* Orders Today
* Low Stock
* Open Work Orders
* Open Assembly Orders
* Pending Shipment

---

# Master Data Flow

Master Data

↓

Select Master Type

↓

List View

↓

Create / Edit

---

Available Masters

* Material
* Purchased Component
* Produced Component
* Product
* Packaging
* Supplier
* Customer
* Channel
* Courier
* UoM

---

# Purchasing Flow

Purchasing

↓

Purchase Request

↓

Create Request

↓

Approve

↓

Purchase Order

↓

Receive Goods

↓

Inventory Updated

---

# Purchase Order Flow

Purchase Order List

↓

Create Purchase Order

↓

Select Supplier

↓

Add Items

↓

Save

↓

Approve

↓

Receive

↓

Inventory Updated

---

# Inventory Flow

Inventory

↓

Stock List

↓

View Stock

↓

Select Item

↓

View Movement History

---

# Stock Opname Flow

Inventory

↓

Stock Opname

↓

Create Opname

↓

Input Physical Count

↓

Variance Generated

↓

Approve Adjustment

↓

Inventory Updated

---

# Production Flow

Purpose:

Raw Material

↓

Produced Component

---

Production

↓

Production Recipe

↓

Recipe List

↓

Create Recipe

OR

Copy Recipe

↓

Recipe Builder

↓

Save Recipe

---

# Recipe Builder Flow

Select Component

↓

Add Materials

↓

Set Quantity

↓

Cost Preview

↓

Save

---

# Work Order Flow

Production

↓

Work Orders

↓

Create Work Order

↓

Select Recipe

↓

Input Quantity

↓

System Calculates Material Requirement

↓

Start Production

↓

Input Actual Usage

↓

Input Output Quantity

↓

Close Work Order

↓

Inventory Updated

---

# Production Variance Flow

Work Order Closed

↓

Compare Planned vs Actual

↓

Generate Variance

↓

Review Recipe

---

# Assembly Flow

Purpose:

Produced Component

*

Purchased Component

↓

Finished Goods

---

Assembly

↓

Assembly Recipe

↓

Create Recipe

OR

Copy Recipe

↓

Save Recipe

---

# Assembly Order Flow

Assembly

↓

Assembly Orders

↓

Create Order

↓

Select Product

↓

Select Recipe

↓

Input Quantity

↓

System Calculates Components

↓

Assemble Product

↓

Input Actual Output

↓

Close Assembly Order

↓

Inventory Updated

---

# Packaging Flow

Packaging

↓

Packaging Recipe

↓

Packaging Builder

↓

Save Recipe

---

# Packaging Execution Flow

Packaging

↓

Ready To Pack

↓

Select Product

↓

Input Quantity

↓

Consume Packaging Materials

↓

Mark Ready To Ship

---

# Sales Flow

Sales

↓

Sales Order

↓

Create Order

↓

Select Customer

↓

Select Channel

↓

Add Products

↓

Calculate Total

↓

Save Order

---

# Custom Order Flow

Sales

↓

Create Order

↓

Enable Custom Order

↓

Input Custom Notes

↓

Additional Cost

↓

Save

---

# Shipping Flow

Shipping

↓

Ready To Ship Orders

↓

Create Shipment

↓

Select Courier

↓

Input Resi

↓

Mark Shipped

---

# Delivery Update Flow

Shipment

↓

Update Status

↓

Delivered

Catatan:

Tracking masih manual.

---

# Reporting Flow

Reports

↓

Select Report

↓

Select Period

↓

Generate Report

---

Available Reports

Sales

Inventory

Purchasing

Production

Assembly

Channel

Profitability

Dead Stock

Best Seller

---

# Audit Log Flow

Settings

↓

Audit Log

↓

Search Activity

↓

View Changes

---

# Recipe Revision Flow

Production Recipe

OR

Assembly Recipe

↓

Open Recipe

↓

Create New Version

↓

Edit Components

↓

Save Version

↓

Old Version Archived

---

# Low Stock Alert Flow

Inventory

↓

System Detects Minimum Stock

↓

Generate Alert

↓

Owner Reviews

↓

Create Purchase Request

---

# Daily Operational Flow

Production User

Login

↓

Check Open Work Orders

↓

Produce Components

↓

Close Work Orders

↓

Check Open Assembly Orders

↓

Assemble Products

↓

Package Products

↓

Create Shipment

↓

Logout

---

# Owner Daily Flow

Login

↓

Dashboard

↓

Review Sales

↓

Review Stock Alerts

↓

Review Purchases

↓

Review Production

↓

Review Profitability

↓

Logout

---

# MVP Pages

Dashboard

Materials

Components

Products

Suppliers

Customers

Purchase Orders

Inventory

Stock Opname

Production Recipes

Work Orders

Assembly Recipes

Assembly Orders

Sales Orders

Shipments

Reports

Audit Log

Settings
