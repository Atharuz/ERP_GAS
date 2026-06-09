# Ciluba ERP

## Product Requirements Document (PRD)

Version: 1.0

Status: FROZEN

Platform: Google Apps Script

---

# 1. PROJECT OVERVIEW

## Objective

Membangun ERP internal berbasis Google Apps Script untuk mengelola:

* Procurement
* Inventory
* Production
* Assembly
* Packaging
* Marketing
* Sales
* Shipment

dalam satu sistem terintegrasi.

---

# 2. SYSTEM SCOPE

## Company Structure

* Single Company
* Single Warehouse

## User Scale

Target:

* 1 – 15 User

Recommended Concurrent Users:

* < 10 User

---

# 3. TECHNOLOGY STACK

## Backend

Google Apps Script

---

## Frontend

HTML Service

Bootstrap 5

Vanilla JavaScript

---

## Database

Google Spreadsheet

Setiap sheet dianggap sebagai table.

---

## File Storage

Google Drive

---

# 4. BUSINESS RULES

## Inventory Driven

Seluruh transaksi harus menghasilkan inventory movement.

---

## Costing Method

Moving Average Cost

---

## Reservation System

Aktif

Formula:

Available Qty = On Hand Qty - Reserved Qty

---

## Auto Numbering

Semua dokumen menggunakan nomor otomatis.

---

## Audit Trail

Semua transaksi wajib tercatat.

---

## Approval Workflow

Tidak digunakan.

---

## Invoice

Tidak digunakan.

---

## Account Receivable

Tidak digunakan.

---

## Account Payable

Tidak digunakan.

---

## Purchase Request

Tidak digunakan.

---

## Customer Creation

Customer dibuat otomatis saat Sales Order pertama.

Anti duplicate berdasarkan:

* Customer Name
* Phone Number

---

# 5. MASTER DATA

## Category

Digunakan untuk:

* Material
* Produced Component
* Purchased Component
* Product

Fields:

* Category Code
* Category Name
* Category Type

---

## UOM

Fields:

* UOM Code
* UOM Name

---

## Material

Fields:

* Material Code
* Material Name
* Category
* UOM
* Minimum Stock

---

## Produced Component

Fields:

* Component Code
* Component Name
* Category
* UOM

---

## Purchased Component

Fields:

* Component Code
* Component Name
* Category
* UOM

---

## Product

Fields:

* Product Code
* Product Name
* Category
* UOM

---

## Supplier

Fields:

* Supplier Code
* Supplier Name
* Phone
* Email
* Address

---

## Customer

Auto Generated

Fields:

* Customer Code
* Customer Name
* Phone
* Address

---

## Sales Channel

Fields:

* Channel Code
* Channel Name

---

# 6. MARKETING

## Purpose

Mengatur harga jual dan promo.

Tidak mempengaruhi costing.

---

## Pricing Strategy

Fields:

* Strategy Code
* Strategy Name
* Start Date
* End Date
* Status

Pricing Methods:

* Fixed Price
* Markup %

---

## Product Pricing

Fields:

* Product
* Selling Price
* Effective Date

---

## Promotion

Types:

* Percentage Discount
* Fixed Discount
* Buy X Get Y

Fields:

* Promo Code
* Promo Name
* Start Date
* End Date
* Promo Type

---

## Promotion Product

Fields:

* Promo
* Product
* Discount Value

---

# 7. RECIPE MANAGEMENT

## Production Recipe

Input:

* Material

Output:

* Produced Component

---

## Assembly Recipe

Input:

* Produced Component
* Purchased Component

Output:

* Product

---

## Packaging Recipe

Input:

* Packaging Material

Output:

* Product

Packaging Cost menambah Product Cost.

---

# 8. PROCUREMENT

## Purchase Order

Status:

* Draft
* Issued
* Partially Received
* Received
* Cancelled

---

## Goods Receipt

Functions:

* Add Inventory
* Update Average Cost

---

# 9. PRODUCTION

## Work Order

Input:

* Material

Output:

* Produced Component

Status:

* Draft
* Released
* In Progress
* Completed
* Cancelled

---

# 10. ASSEMBLY

## Assembly Order

Input:

* Produced Component
* Purchased Component

Output:

* Product

Status:

* Draft
* Released
* In Progress
* Completed
* Cancelled

---

# 11. PACKAGING

## Packaging Execution

Input:

* Packaging Material

Output:

* Product

Status:

* Draft
* Released
* In Progress
* Completed
* Cancelled

---

# 12. SALES

## Sales Order

Header:

* SO Number
* Order Date
* Customer
* Sales Channel
* Notes

Lines:

* Product
* Qty
* Selling Price
* Discount
* Subtotal

Status:

* Draft
* Confirmed
* Shipped
* Cancelled

Rules:

Confirmed:

* Reserve Inventory

Cancelled:

* Release Reservation

---

# 13. SHIPMENT

## Shipment

Fields:

* Shipment Number
* Shipment Date
* Sales Order

Status:

* Draft
* Ready
* Shipped
* Cancelled

Rules:

Shipped:

* Reduce Inventory
* Release Reservation

---

# 14. INVENTORY

## Inventory Balance

Fields:

* Item
* Item Type
* On Hand Qty
* Reserved Qty
* Available Qty
* Average Cost

---

## Inventory Movement

Movement Types:

* Purchase Receipt
* Production Issue
* Production Receipt
* Assembly Issue
* Assembly Receipt
* Packaging Issue
* Packaging Receipt
* Shipment
* Stock Adjustment

---

## Stock Opname

Dipisahkan dari Stock Adjustment.

Flow:

Count

→ Variance

→ Adjustment

---

## Stock Adjustment

Manual correction.

Wajib menyimpan alasan adjustment.

---

# 15. COSTING

## Material Cost

Berasal dari Goods Receipt.

---

## Produced Component Cost

Material Cost

*

Production Cost

---

## Product Cost

Produced Component Cost

*

Purchased Component Cost

*

Packaging Cost

---

# 16. DASHBOARD

Widgets:

* Sales Today
* Sales This Month
* Inventory Value
* Low Stock Alert
* Open Purchase Orders
* Open Work Orders
* Open Assembly Orders
* Open Shipments

Refresh manual.

Tidak menggunakan realtime websocket.

---

# 17. SECURITY

Roles:

* Super Admin
* Admin
* Inventory
* Production
* Sales
* Marketing

Permission berdasarkan module.

---

# 18. UI PRINCIPLES

## CRUD

Seluruh CRUD menggunakan modal popup.

Tidak membuat halaman CRUD terpisah.

---

## List Screen

Komponen:

* Search
* Filter
* Table
* Pagination

---

## Form Screen

Komponen:

* Header
* Detail Lines
* Save
* Cancel

---

# 19. MENU STRUCTURE

Dashboard

Master Data

* Categories
* UOM
* Materials
* Produced Components
* Purchased Components
* Products
* Suppliers
* Customers
* Sales Channels

Marketing

* Pricing Strategy
* Product Pricing
* Promotions

Recipes

* Production Recipes
* Assembly Recipes
* Packaging Recipes

Procurement

* Purchase Orders
* Goods Receipts

Production

* Work Orders

Assembly

* Assembly Orders

Packaging

* Packaging Execution

Sales

* Sales Orders
* Shipments

Inventory

* Inventory Balance
* Inventory Movements
* Stock Opname
* Stock Adjustments

Administration

* Users
* Roles
* Settings
* Audit Logs

---

# 20. SPREADSHEET DATABASE SCHEMA

Master Data

* mst_categories
* mst_uom
* mst_materials
* mst_produced_components
* mst_purchased_components
* mst_products
* mst_suppliers
* mst_customers
* mst_sales_channels

Marketing

* mkt_pricing_strategies
* mkt_product_pricing
* mkt_promotions
* mkt_promotion_products

Recipes

* recipe_production_headers
* recipe_production_lines
* recipe_assembly_headers
* recipe_assembly_lines
* recipe_packaging_headers
* recipe_packaging_lines

Procurement

* trx_purchase_orders
* trx_purchase_order_lines
* trx_goods_receipts
* trx_goods_receipt_lines

Production

* trx_work_orders

Assembly

* trx_assembly_orders

Packaging

* trx_packaging_execution

Sales

* trx_sales_orders
* trx_sales_order_lines
* trx_shipments
* trx_shipment_lines

Inventory

* inv_balance
* inv_movements
* inv_stock_opname
* inv_stock_adjustments

System

* sys_users
* sys_roles
* sys_permissions
* sys_document_sequences
* sys_audit_logs
* sys_settings

---

# 21. TECHNICAL ARCHITECTURE

Architecture Layer:

UI Layer

↓

Service Layer

↓

Repository Layer

↓

Google Spreadsheet

---

Folder Structure:

src/

core/

repositories/

services/

ui/

---

# 22. SINGLE SOURCE OF TRUTH

Dokumen ini adalah referensi tertinggi proyek.

Semua coding, database, UI, testing dan maintenance harus mengikuti PRD ini.

Jika terjadi konflik dengan dokumen lain, maka PRD.md selalu menjadi sumber kebenaran utama.
