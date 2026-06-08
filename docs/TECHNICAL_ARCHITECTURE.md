# ERP Ciluba Technical Architecture v1.0

## Purpose

Dokumen ini mendefinisikan arsitektur teknis ERP Ciluba yang dibangun menggunakan Google Apps Script (GAS) dan Google Sheets.

Tujuan utama:

* Menjaga konsistensi implementasi
* Menentukan struktur project
* Menentukan pola akses data
* Menentukan standar transaksi
* Menentukan strategi audit

Dokumen ini bukan spesifikasi bisnis.

Business Rules mengikuti:

* BUSINESS_PROCESS_MAP.md
* DATABASE_DESIGN.md
* SCREEN_SPECIFICATIONS.md

---

# Technology Stack

## Frontend

```text
HTML
CSS
JavaScript
Bootstrap 5
```

Frontend menggunakan:

```text
HtmlService
```

Google Apps Script.

---

## Backend

```text
Google Apps Script
```

Menggunakan:

```text
Code.gs
Modules
Services
Repositories
```

---

## Database

```text
Google Sheets
```

Sebagai primary datastore.

---

## File Storage

```text
Google Drive
```

Digunakan untuk:

* Attachment
* Export Files
* Backup Files

---

# System Architecture

```text
Browser
↓
HTML UI
↓
google.script.run
↓
Service Layer
↓
Repository Layer
↓
Google Sheets
```

---

# Application Layers

## UI Layer

Tanggung jawab:

* Rendering Screen
* Form Validation
* User Interaction

Tidak boleh:

```text
Business Logic
Database Access
```

---

## Service Layer

Tanggung jawab:

* Business Rules
* Workflow Logic
* Transaction Validation

Contoh:

```text
Confirm Purchase Order
Complete Work Order
Complete Assembly Order
Complete Shipment
```

---

## Repository Layer

Tanggung jawab:

* Read Data
* Write Data
* Update Data
* Archive Data

Tidak boleh:

```text
Business Logic
```

---

# Project Structure

```text
src/

core/
├── config/
├── constants/
├── helpers/
├── security/

repositories/
├── master/
├── purchasing/
├── inventory/
├── production/
├── assembly/
├── packaging/
├── sales/
└── system/

services/
├── master/
├── purchasing/
├── inventory/
├── production/
├── assembly/
├── packaging/
├── sales/
└── system/

ui/
├── layouts/
├── pages/
├── modals/
├── components/

app/
└── main.gs
```

---

# Spreadsheet Strategy

## Principle

Pisahkan data berdasarkan fungsi.

Jangan membuat satu spreadsheet besar yang berisi seluruh sistem.

---

# Spreadsheet Structure

## ERP_MASTER

Master data.

Sheets:

```text
materials
produced_components
purchased_components
products
suppliers
customers
sales_channels
categories
uom
```

---

## ERP_TRANSACTION

Data transaksi.

Sheets:

```text
purchase_orders
purchase_order_lines

goods_receipts
goods_receipt_lines

work_orders

assembly_orders

packaging_execution

sales_orders
sales_order_lines

shipments
shipment_lines
```

---

## ERP_RECIPE

Data recipe.

Sheets:

```text
production_recipes
production_recipe_lines

assembly_recipes
assembly_recipe_lines

packaging_recipes
packaging_recipe_lines
```

---

## ERP_INVENTORY

Inventory tracking.

Sheets:

```text
inventory_balance
inventory_movements

stock_opname
stock_adjustments
```

---

## ERP_SYSTEM

System data.

Sheets:

```text
audit_logs
activity_logs

document_sequences

settings
```

---

# CRUD Pattern

Semua transaksi mengikuti pola:

```text
UI
↓
Service
↓
Repository
↓
Sheet
```

---

## Example

```text
Create Purchase Order
```

Flow:

```text
PurchaseOrderPage
↓
PurchaseOrderService
↓
PurchaseOrderRepository
↓
purchase_orders
```

---

# Document Numbering

Semua nomor dokumen dihasilkan sistem.

User tidak boleh mengisi manual.

---

## Format

### Purchase Order

```text
PO-YYYYMM-0001
```

Contoh:

```text
PO-202606-0001
```

---

### Goods Receipt

```text
GR-YYYYMM-0001
```

---

### Work Order

```text
WO-YYYYMM-0001
```

---

### Assembly Order

```text
AO-YYYYMM-0001
```

---

### Packaging Execution

```text
PK-YYYYMM-0001
```

---

### Sales Order

```text
SO-YYYYMM-0001
```

---

### Shipment

```text
SH-YYYYMM-0001
```

---

# Soft Delete Strategy

Data tidak boleh dihapus permanen.

Gunakan:

```text
is_active
```

atau:

```text
status = Archived
```

---

# Audit Strategy

## Audit Logs

Catat perubahan data.

Actions:

```text
Create
Edit
Archive
Restore
```

---

## Audit Fields

Setiap tabel memiliki:

```text
created_at
created_by

updated_at
updated_by
```

---

# Activity Log Strategy

Catat aktivitas user.

Contoh:

```text
Login

Create Purchase Order

Receive Goods

Complete Work Order

Complete Assembly Order

Complete Packaging Execution

Create Sales Order

Complete Shipment
```

---

# Inventory Strategy

## Inventory Balance

Menyimpan saldo terkini.

---

## Inventory Movements

Menyimpan histori pergerakan.

Semua perubahan stock harus menghasilkan movement.

---

## Source Transactions

```text
Goods Receipt

Work Order

Assembly Order

Packaging Execution

Shipment

Stock Adjustment
```

---

# Transaction Snapshot Strategy

Saat transaksi dibuat:

Recipe dan harga harus disimpan sebagai snapshot.

Tujuan:

```text
Histori tidak berubah
```

walaupun recipe atau harga berubah di masa depan.

---

# Customer Strategy

Customer dapat dibuat otomatis dari Sales Order.

Duplicate check menggunakan:

```text
Phone Number
Customer Name
```

---

# Reservation Strategy

Saat Sales Order dikonfirmasi:

```text
Ready To Ship
↓
Reserved
```

Formula:

```text
Available
=
Ready To Ship
-
Reserved
```

---

# Security Strategy

## Roles

### Owner

Akses penuh.

---

### Operations

Akses operasional harian.

---

## Authorization

Semua akses menu diperiksa melalui role.

---

# Performance Principles

## Read Optimization

Gunakan batch read.

Hindari:

```text
getRange()
getValue()
```

berulang kali.

---

## Write Optimization

Gunakan batch update.

Hindari write per baris.

---

## Cache

Gunakan CacheService untuk:

```text
Settings
Categories
UoM
Sales Channels
```

---

# Backup Strategy

Backup dilakukan dengan:

```text
Spreadsheet Copy
```

secara berkala.

---

# MVP Technical Scope

Termasuk:

```text
Single Company

Single Warehouse

Google Sheets Database

Google Apps Script

Audit Logs

Activity Logs
```

---

Tidak termasuk:

```text
Multi Company

Multi Warehouse

API Integration

Accounts Receivable

Invoice Module

POS Module

Offline Mode
```
