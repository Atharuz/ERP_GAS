# Ciluba ERP

Version: 1.0

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

## Materials

| Screen    | Type               | Purpose             | Roles             |
| --------- | ------------------ | ------------------- | ----------------- |
| Materials | Table + Modal CRUD | Raw Material Master | Owner, Operations |

Actions:

* Create
* View
* Edit
* Archive

---

## Purchased Components

| Screen               | Type               | Purpose                    | Roles             |
| -------------------- | ------------------ | -------------------------- | ----------------- |
| Purchased Components | Table + Modal CRUD | Purchased Component Master | Owner, Operations |

Actions:

* Create
* View
* Edit
* Archive

---

## Produced Components

| Screen              | Type               | Purpose                   | Roles             |
| ------------------- | ------------------ | ------------------------- | ----------------- |
| Produced Components | Table + Modal CRUD | Produced Component Master | Owner, Operations |

Actions:

* Create
* View
* Edit
* Archive

---

## Products

| Screen   | Type               | Purpose               | Roles             |
| -------- | ------------------ | --------------------- | ----------------- |
| Products | Table + Modal CRUD | Finished Goods Master | Owner, Operations |

Actions:

* Create
* View
* Edit
* Archive

---

## Packaging Materials

| Screen              | Type               | Purpose                   | Roles             |
| ------------------- | ------------------ | ------------------------- | ----------------- |
| Packaging Materials | Table + Modal CRUD | Packaging Material Master | Owner, Operations |

Actions:

* Create
* View
* Edit
* Archive

---

## Suppliers

| Screen    | Type               | Purpose         | Roles             |
| --------- | ------------------ | --------------- | ----------------- |
| Suppliers | Table + Modal CRUD | Supplier Master | Owner, Operations |

Actions:

* Create
* View
* Edit
* Archive

---

## Customers

| Screen    | Type               | Purpose         | Roles             |
| --------- | ------------------ | --------------- | ----------------- |
| Customers | Table + Modal CRUD | Customer Master | Owner, Operations |

Actions:

* Create
* View
* Edit
* Archive

---

## Channels

| Screen   | Type               | Purpose              | Roles             |
| -------- | ------------------ | -------------------- | ----------------- |
| Channels | Table + Modal CRUD | Sales Channel Master | Owner, Operations |

Actions:

* Create
* View
* Edit
* Archive

---

## Couriers

| Screen   | Type               | Purpose        | Roles             |
| -------- | ------------------ | -------------- | ----------------- |
| Couriers | Table + Modal CRUD | Courier Master | Owner, Operations |

Actions:

* Create
* View
* Edit
* Archive

---

## UoM

| Screen | Type               | Purpose                | Roles |
| ------ | ------------------ | ---------------------- | ----- |
| UoM    | Table + Modal CRUD | Unit of Measure Master | Owner |

Actions:

* Create
* View
* Edit
* Archive

---

## UoM Conversions

| Screen          | Type               | Purpose              | Roles |
| --------------- | ------------------ | -------------------- | ----- |
| UoM Conversions | Table + Modal CRUD | UoM Conversion Rules | Owner |

Actions:

* Create
* View
* Edit
* Archive

---

# Purchasing Module

| Screen                 | Type        | Purpose                   | Roles             |
| ---------------------- | ----------- | ------------------------- | ----------------- |
| Purchase Orders        | List + Form | Purchase Order Management | Owner, Operations |
| Goods Receipts         | List + Form | Goods Receipt Management  | Owner, Operations |
| Supplier Price History | Page        | Supplier Price Tracking   | Owner, Operations |

---

# Inventory Module

| Screen           | Type        | Purpose                       | Roles             |
| ---------------- | ----------- | ----------------------------- | ----------------- |
| Stock Overview   | Page        | Inventory Position Overview   | Owner, Operations |
| Stock Movement   | Page        | Inventory Transaction History | Owner, Operations |
| Stock Opname     | List + Form | Stock Counting Process        | Owner, Operations |
| Stock Adjustment | List + Form | Inventory Correction          | Owner             |

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

| Screen                     | Type   | Purpose                   | Roles |
| -------------------------- | ------ | ------------------------- | ----- |
| Sales Report               | Report | Sales Analysis            | Owner |
| Purchasing Report          | Report | Purchasing Analysis       | Owner |
| Inventory Report           | Report | Inventory Analysis        | Owner |
| Production Report          | Report | Production Analysis       | Owner |
| Assembly Report            | Report | Assembly Analysis         | Owner |
| Packaging Report           | Report | Packaging Analysis        | Owner |
| Profitability Report       | Report | Revenue & Profit Analysis | Owner |
| Channel Performance Report | Report | Sales Channel Analysis    | Owner |

---

# Audit Module

| Screen     | Type | Purpose               | Roles |
| ---------- | ---- | --------------------- | ----- |
| Audit Logs | Page | System Change History | Owner |

---

# Screen Count Summary

## Dashboard

1 Screen

## Master Data

11 Screens

## Purchasing

3 Screens

## Inventory

4 Screens

## Production

3 Screens

## Assembly

3 Screens

## Packaging

3 Screens

## Sales

1 Screen

## Shipping

2 Screens

## Reports

8 Screens

## Audit

1 Screen

---

# Total Screens

40 Screens

---

# Notes

Screen Inventory hanya mendefinisikan:

* Nama Screen
* Tujuan Screen
* Tipe Screen
* Hak Akses

Field, layout, validation, workflow, dan business rules akan dijelaskan pada:

SCREEN_SPECIFICATIONS.md
