# Ciluba ERP

Version: 1.1

---

# Purpose

Dokumen ini mendefinisikan seluruh screen yang akan tersedia pada ERP Ciluba MVP.

Dokumen ini digunakan sebagai acuan untuk:

* UI Design
* Screen Specifications
* Google Sheets Structure
* Apps Script Development
* User Acceptance Testing (UAT)

---

# Global UI Rules

## Dashboard

Menggunakan Dedicated Page.

---

## Master Data

Menggunakan:

* Table Page
* Detail Modal
* Create/Edit Modal

Actions:

* Create
* View
* Edit
* Archive
* Restore

Tidak menggunakan Hard Delete.

---

## Transaction Modules

Menggunakan:

* List Page
* Form Page

Karena transaksi memiliki workflow yang lebih kompleks.

---

## Reports

Menggunakan Dedicated Page.

---

## Audit Logs

Menggunakan Dedicated Page.

---

# User Roles

## Owner

Akses penuh ke seluruh modul.

## Operations

Mengelola operasional harian.

## Future Admin

Membantu operasional sesuai hak akses yang diberikan.

---

# Dashboard Module

| Screen    | Type | Purpose                  | Roles             |
| --------- | ---- | ------------------------ | ----------------- |
| Dashboard | Page | Ringkasan kondisi bisnis | Owner, Operations |

---

# Master Data Module

## Categories

| Screen              | Type               | Purpose               | Roles |
| ------------------- | ------------------ | --------------------- | ----- |
| Material Categories | Table + Modal CRUD | Kategori Raw Material | Owner |
| Product Categories  | Table + Modal CRUD | Kategori Product      | Owner |

---

## Inventory Masters

| Screen               | Type               | Purpose                    | Roles             |
| -------------------- | ------------------ | -------------------------- | ----------------- |
| Materials            | Table + Modal CRUD | Raw Material Master        | Owner, Operations |
| Purchased Components | Table + Modal CRUD | Purchased Component Master | Owner, Operations |
| Produced Components  | Table + Modal CRUD | Produced Component Master  | Owner, Operations |
| Products             | Table + Modal CRUD | Finished Goods Master      | Owner, Operations |
| Packaging Materials  | Table + Modal CRUD | Packaging Material Master  | Owner, Operations |

---

## Business Partners

| Screen    | Type               | Purpose         | Roles             |
| --------- | ------------------ | --------------- | ----------------- |
| Suppliers | Table + Modal CRUD | Supplier Master | Owner, Operations |
| Customers | Table + Modal CRUD | Customer Master | Owner, Operations |

---

## Sales Masters

| Screen   | Type               | Purpose              | Roles             |
| -------- | ------------------ | -------------------- | ----------------- |
| Channels | Table + Modal CRUD | Sales Channel Master | Owner, Operations |
| Couriers | Table + Modal CRUD | Courier Master       | Owner, Operations |

---

## System Masters

| Screen          | Type               | Purpose                | Roles |
| --------------- | ------------------ | ---------------------- | ----- |
| UoM             | Table + Modal CRUD | Unit of Measure Master | Owner |
| UoM Conversions | Table + Modal CRUD | UoM Conversion Rules   | Owner |

---

# Purchasing Module

| Screen                 | Type        | Purpose                   | Roles             |
| ---------------------- | ----------- | ------------------------- | ----------------- |
| Purchase Orders        | List + Form | Purchase Order Management | Owner, Operations |
| Goods Receipts         | List + Form | Goods Receipt Management  | Owner, Operations |
| Supplier Price History | Page        | Histori Harga Supplier    | Owner, Operations |

---

# Inventory Module

| Screen           | Type        | Purpose                  | Roles             |
| ---------------- | ----------- | ------------------------ | ----------------- |
| Stock Overview   | Page        | Ringkasan Posisi Stock   | Owner, Operations |
| Stock Movement   | Page        | Histori Pergerakan Stock | Owner, Operations |
| Stock Opname     | List + Form | Proses Stock Opname      | Owner, Operations |
| Stock Adjustment | List + Form | Koreksi Stock            | Owner             |

---

# Production Module

| Screen             | Type           | Purpose                      | Roles             |
| ------------------ | -------------- | ---------------------------- | ----------------- |
| Production Recipes | List + Builder | Production Recipe Management | Owner, Operations |
| Recipe Builder     | Builder        | Production Recipe Builder    | Owner, Operations |
| Work Orders        | List + Form    | Production Execution         | Owner, Operations |

---

# Assembly Module

| Screen           | Type           | Purpose                    | Roles             |
| ---------------- | -------------- | -------------------------- | ----------------- |
| Assembly Recipes | List + Builder | Assembly Recipe Management | Owner, Operations |
| Recipe Builder   | Builder        | Assembly Recipe Builder    | Owner, Operations |
| Assembly Orders  | List + Form    | Assembly Execution         | Owner, Operations |

---

# Packaging Module

| Screen              | Type           | Purpose                     | Roles             |
| ------------------- | -------------- | --------------------------- | ----------------- |
| Packaging Recipes   | List + Builder | Packaging Recipe Management | Owner, Operations |
| Recipe Builder      | Builder        | Packaging Recipe Builder    | Owner, Operations |
| Packaging Execution | List + Form    | Packaging Process Execution | Owner, Operations |

---

# Sales Module

| Screen       | Type        | Purpose                | Roles             |
| ------------ | ----------- | ---------------------- | ----------------- |
| Sales Orders | List + Form | Sales Order Management | Owner, Operations |

---

# Shipping Module

| Screen           | Type        | Purpose                       | Roles             |
| ---------------- | ----------- | ----------------------------- | ----------------- |
| Shipments        | List + Form | Shipment Management           | Owner, Operations |
| Delivery Updates | Form        | Manual Delivery Status Update | Operations        |

---

# Reports Module

| Screen                     | Type   | Purpose                  | Roles |
| -------------------------- | ------ | ------------------------ | ----- |
| Sales Report               | Report | Analisa Penjualan        | Owner |
| Purchasing Report          | Report | Analisa Pembelian        | Owner |
| Inventory Report           | Report | Analisa Persediaan       | Owner |
| Production Report          | Report | Analisa Produksi         | Owner |
| Assembly Report            | Report | Analisa Assembly         | Owner |
| Packaging Report           | Report | Analisa Packaging        | Owner |
| Profitability Report       | Report | Analisa Profit & HPP     | Owner |
| Channel Performance Report | Report | Analisa Performa Channel | Owner |

---

# Audit Module

| Screen     | Type | Purpose                  | Roles |
| ---------- | ---- | ------------------------ | ----- |
| Audit Logs | Page | Histori Perubahan Sistem | Owner |

---

# Screen Count Summary

## Dashboard

1 Screen

## Master Data

13 Screens

### Categories

2 Screens

* Material Categories
* Product Categories

### Inventory Masters

5 Screens

* Materials
* Purchased Components
* Produced Components
* Products
* Packaging Materials

### Business Partners

2 Screens

* Suppliers
* Customers

### Sales Masters

2 Screens

* Channels
* Couriers

### System Masters

2 Screens

* UoM
* UoM Conversions

---

## Purchasing

3 Screens

---

## Inventory

4 Screens

---

## Production

3 Screens

---

## Assembly

3 Screens

---

## Packaging

3 Screens

---

## Sales

1 Screen

---

## Shipping

2 Screens

---

## Reports

8 Screens

---

## Audit

1 Screen

---

# Total Screens

42 Screens

---

# Notes

Screen Inventory hanya mendefinisikan:

* Nama Screen
* Tujuan Screen
* Tipe Screen
* Hak Akses

Field, layout, validation, workflow, business rules, dan UI behavior akan dijelaskan pada:

SCREEN_SPECIFICATIONS_PART_1.md
SCREEN_SPECIFICATIONS_PART_2.md
SCREEN_SPECIFICATIONS_PART_3.md
SCREEN_SPECIFICATIONS_PART_4.md
SCREEN_SPECIFICATIONS_PART_5.md
