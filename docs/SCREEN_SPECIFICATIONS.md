# Ciluba ERP

Version: 1.0

Status: Draft Review

---

# Purpose

Dokumen ini mendefinisikan spesifikasi screen untuk:

* Dashboard
* Material Categories
* Product Categories
* Materials
* Purchased Components
* Produced Components
* Products
* Packaging Materials
* Suppliers
* Customers
* Channels
* Couriers
* UoM
* UoM Conversions

Dokumen ini digunakan sebagai acuan:

* UI Development
* Database Design
* Apps Script Development
* UAT Testing

---

# Global Rules

## CRUD Policy

Allowed:

* Create
* View
* Edit
* Archive
* Restore

Not Allowed:

* Hard Delete

---

## Auto Generate Code Policy

Semua master data menggunakan Auto Generate Code.

Contoh:

```text
MCAT-00001
PCAT-00001

MAT-00001
PURC-00001
PROD-00001
FG-00001
PKG-00001

SUP-00001
CUS-00001

CHN-00001
CUR-00001
```

Code bersifat read-only dan dibuat sistem.

---

## Archive Policy

Master data yang di-archive:

* Tetap tersimpan
* Tetap muncul pada histori transaksi
* Tidak dapat dipilih untuk transaksi baru

---

## Audit Log Policy

Aktivitas berikut wajib dicatat:

* Create
* Edit
* Archive
* Restore

Audit Log menyimpan:

* Timestamp
* User
* Entity
* Entity ID
* Action
* Old Value
* New Value

---

# DASHBOARD

## Purpose

Menampilkan ringkasan kondisi bisnis secara real-time.

---

## Access Roles

* Owner
* Operations

---

## Screen Type

Dedicated Dashboard Page

---

## KPI Cards

### Revenue This Month

Total omzet bulan berjalan.

---

### Orders This Month

Jumlah Sales Order bulan berjalan.

---

### Units Sold

Jumlah unit produk terjual.

---

### Gross Profit

Pendapatan dikurangi HPP.

---

### Inventory Value

Total nilai inventory saat ini.

---

### Low Stock Items

Jumlah item di bawah minimum stock.

---

### Open Work Orders

Jumlah Work Order aktif.

---

### Open Assembly Orders

Jumlah Assembly Order aktif.

---

### Pending Shipments

Jumlah pengiriman yang belum selesai.

---

## Dashboard Widgets

### Sales Trend

Grafik penjualan harian.

### Top Products

10 produk terlaris.

### Top Channels

Performa channel penjualan.

### Low Stock Alerts

Daftar item yang harus segera dibeli.

### Recent Activities

Aktivitas terbaru sistem.

---

## Navigation

Dashboard menjadi halaman pertama setelah login.

---

# MATERIAL CATEGORIES

## Purpose

Mengelola kategori untuk Raw Material.

---

## Access Roles

* Owner

---

## Screen Type

Table Page + Modal

---

## Table Columns

| Column        | Description       |
| ------------- | ----------------- |
| Category Code | Auto Generated    |
| Category Name | Nama Kategori     |
| Status        | Active / Inactive |

---

## Filters

* Search
* Status

---

## Actions

* Create
* View
* Edit
* Archive
* Restore

---

## Create/Edit Modal

| Field         | Required |
| ------------- | -------- |
| Category Name | Yes      |

---

## Validation Rules

### Category Name

Must be unique.

---

## Archive Rules

Tidak boleh di-archive jika masih digunakan oleh Material.

---

# PRODUCT CATEGORIES

## Purpose

Mengelola kategori untuk Finished Goods.

---

## Access Roles

* Owner

---

## Screen Type

Table Page + Modal

---

## Table Columns

| Column        | Description       |
| ------------- | ----------------- |
| Category Code | Auto Generated    |
| Category Name | Nama Kategori     |
| Status        | Active / Inactive |

---

## Filters

* Search
* Status

---

## Actions

* Create
* View
* Edit
* Archive
* Restore

---

## Create/Edit Modal

| Field         | Required |
| ------------- | -------- |
| Category Name | Yes      |

---

## Validation Rules

### Category Name

Must be unique.

---

## Archive Rules

Tidak boleh di-archive jika masih digunakan oleh Product.

---

# MATERIALS

## Purpose

Mengelola seluruh Raw Material yang digunakan dalam Production Recipe.

---

## Access Roles

* Owner
* Operations

---

## Screen Type

Table Page + Detail Modal + Create/Edit Modal

---

## Table Columns

| Column        | Description       |
| ------------- | ----------------- |
| Material Code | Auto Generated    |
| Material Name | Nama Material     |
| Category      | Material Category |
| Purchase UoM  | Satuan Pembelian  |
| Inventory UoM | Satuan Stock      |
| Current Stock | Stock Saat Ini    |
| Minimum Stock | Minimum Stock     |
| Status        | Active / Inactive |

---

## Filters

* Search
* Category
* Status
* Low Stock Only

---

## Actions

* Create
* View
* Edit
* Archive
* Restore

---

## Detail Modal

### General Information

* Material Code
* Material Name
* Category
* Purchase UoM
* Inventory UoM
* Consumption UoM
* Minimum Stock
* Current Stock
* Notes

### System Information

* Created At
* Created By
* Updated At
* Updated By

---

## Create/Edit Modal

| Field           | Required |
| --------------- | -------- |
| Material Name   | Yes      |
| Category        | Yes      |
| Purchase UoM    | Yes      |
| Inventory UoM   | Yes      |
| Consumption UoM | Yes      |
| Minimum Stock   | Yes      |
| Notes           | No       |

---

## Validation Rules

* Material Name required
* Category required
* UoM required

---

## Business Rules

* Material Code auto generated
* Material dapat digunakan pada Production Recipe
* Material dapat dibeli melalui Purchase Order

---

## Related Screens

* Purchase Orders
* Goods Receipts
* Production Recipes
* Stock Overview

---

# PRODUCTS

## Purpose

Mengelola Finished Goods yang dijual ke customer.

---

## Access Roles

* Owner
* Operations

---

## Screen Type

Table Page + Detail Modal + Create/Edit Modal

---

## Table Columns

| Column           | Description        |
| ---------------- | ------------------ |
| Product Code     | Auto Generated     |
| Product Name     | Nama Produk        |
| Product Category | Kategori Produk    |
| Selling Price    | Harga Jual Default |
| Current Stock    | Stock Saat Ini     |
| Status           | Active / Inactive  |

---

## Filters

* Search
* Category
* Status

---

## Actions

* Create
* View
* Edit
* Archive
* Restore

---

## Detail Modal

### General Information

* Product Code
* Product Name
* Product Category
* Selling Price
* Product Description
* Current Stock
* Notes

### System Information

* Created At
* Created By
* Updated At
* Updated By

---

## Create/Edit Modal

| Field               | Required |
| ------------------- | -------- |
| Product Name        | Yes      |
| Product Category    | Yes      |
| Selling Price       | Yes      |
| Product Description | No       |
| Notes               | No       |

---

## Validation Rules

* Product Name required
* Product Category required
* Selling Price > 0

---

## Business Rules

* Product Code auto generated
* Selling Price menjadi harga default saat Sales Order dibuat
* Sales Order boleh override harga
* Perubahan Selling Price tidak mengubah histori transaksi lama

---

## Related Screens

* Assembly Recipes
* Packaging Recipes
* Sales Orders
* Shipments

---

# CUSTOMERS

## Purpose

Mengelola data customer.

---

## Access Roles

* Owner
* Operations

---

## Screen Type

Table Page + Detail Modal + Create/Edit Modal

---

## Customer Creation Policy

Customer tidak wajib dibuat manual.

Saat Sales Order dibuat:

1. Sistem mencari customer berdasarkan Phone Number.
2. Jika tidak ditemukan, sistem mencari berdasarkan Customer Name.
3. Jika ditemukan kemungkinan duplikasi, sistem menampilkan warning.
4. User dapat memilih customer existing.
5. Jika tidak ada, sistem membuat customer baru otomatis.

---

## Table Columns

| Column        | Description       |
| ------------- | ----------------- |
| Customer Code | Auto Generated    |
| Customer Name | Nama Customer     |
| Phone Number  | Nomor Telepon     |
| City          | Kota              |
| Total Orders  | Total Order       |
| Status        | Active / Inactive |

---

## Duplicate Detection

### Primary Match

Phone Number

### Secondary Match

Customer Name

---

## Business Rules

* Customer Code auto generated
* Customer dapat dibuat otomatis dari Sales Order
* Duplicate warning wajib ditampilkan

---

# UOM

## Purpose

Mengelola Unit of Measure.

---

## Access Roles

* Owner

---

## Screen Type

Table Page + Modal

---

## Table Columns

| Column   | Description       |
| -------- | ----------------- |
| UoM Code | Manual            |
| UoM Name | Nama Satuan       |
| Status   | Active / Inactive |

---

## Examples

```text
PCS
CM
M
ROLL
SHEET
PACK
GRAM
KG
ML
LITER
```

---

## Business Rules

* User Defined
* Tidak boleh archive jika masih digunakan

---

# UOM CONVERSIONS

## Purpose

Mengelola konversi satuan.

---

## Access Roles

* Owner

---

## Table Columns

| Column            | Description       |
| ----------------- | ----------------- |
| From UoM          | Satuan Asal       |
| To UoM            | Satuan Tujuan     |
| Conversion Factor | Faktor Konversi   |
| Status            | Active / Inactive |

---

## Examples

```text
1 Roll = 1000 CM

1 Liter = 1000 ML

1 KG = 1000 GR
```

---

## Validation Rules

* From UoM required
* To UoM required
* Conversion Factor > 0

---

# PURCHASED COMPONENTS

## Purpose

Mengelola komponen yang dibeli langsung dari supplier dan digunakan pada Assembly Recipe.

Contoh:

* Bel
* Resleting
* Magnet
* Velcro
* Buckle
* Switch
* Roda

---

## Access Roles

* Owner
* Operations

---

## Screen Type

Table Page + Detail Modal + Create/Edit Modal

---

## Table Columns

| Column         | Description       |
| -------------- | ----------------- |
| Component Code | Auto Generated    |
| Component Name | Nama Komponen     |
| Purchase UoM   | Satuan Pembelian  |
| Inventory UoM  | Satuan Stock      |
| Current Stock  | Stock Saat Ini    |
| Minimum Stock  | Minimum Stock     |
| Status         | Active / Inactive |

---

## Filters

* Search
* Status
* Low Stock Only

---

## Actions

* Create
* View
* Edit
* Archive
* Restore

---

## Detail Modal

### General Information

* Component Code
* Component Name
* Purchase UoM
* Inventory UoM
* Minimum Stock
* Current Stock
* Notes

### System Information

* Created At
* Created By
* Updated At
* Updated By

---

## Create/Edit Modal

| Field          | Required |
| -------------- | -------- |
| Component Name | Yes      |
| Purchase UoM   | Yes      |
| Inventory UoM  | Yes      |
| Minimum Stock  | Yes      |
| Notes          | No       |

---

## Validation Rules

* Component Name required
* Purchase UoM required
* Inventory UoM required

---

## Business Rules

* Component Code auto generated
* Dapat dibeli melalui Purchase Order
* Dapat digunakan pada Assembly Recipe

---

## Related Screens

* Purchase Orders
* Goods Receipts
* Assembly Recipes
* Stock Overview

---

# PRODUCED COMPONENTS

## Purpose

Mengelola komponen hasil proses produksi yang digunakan pada Assembly Recipe.

Contoh:

* Gear 4x4
* Gear 7x7
* Puzzle Circle
* Puzzle Triangle
* Huruf A
* Huruf B

---

## Access Roles

* Owner
* Operations

---

## Screen Type

Table Page + Detail Modal + Create/Edit Modal

---

## Table Columns

| Column         | Description       |
| -------------- | ----------------- |
| Component Code | Auto Generated    |
| Component Name | Nama Komponen     |
| Inventory UoM  | Satuan Stock      |
| Current Stock  | Stock Saat Ini    |
| Minimum Stock  | Minimum Stock     |
| Status         | Active / Inactive |

---

## Filters

* Search
* Status
* Low Stock Only

---

## Actions

* Create
* View
* Edit
* Archive
* Restore

---

## Detail Modal

### General Information

* Component Code
* Component Name
* Inventory UoM
* Current Stock
* Minimum Stock
* Notes

### System Information

* Created At
* Created By
* Updated At
* Updated By

---

## Create/Edit Modal

| Field          | Required |
| -------------- | -------- |
| Component Name | Yes      |
| Inventory UoM  | Yes      |
| Minimum Stock  | Yes      |
| Notes          | No       |

---

## Validation Rules

* Component Name required
* Inventory UoM required

---

## Business Rules

* Component Code auto generated
* Tidak dapat dibeli langsung
* Harus dihasilkan melalui Work Order
* Dapat digunakan pada Assembly Recipe

---

## Related Screens

* Production Recipes
* Work Orders
* Assembly Recipes
* Stock Overview

---

# PACKAGING MATERIALS

## Purpose

Mengelola material packaging yang digunakan dalam Packaging Recipe.

Contoh:

* Kardus
* Bubble Wrap
* Sticker
* Lakban
* Kartu Ucapan

---

## Access Roles

* Owner
* Operations

---

## Screen Type

Table Page + Detail Modal + Create/Edit Modal

---

## Table Columns

| Column         | Description       |
| -------------- | ----------------- |
| Packaging Code | Auto Generated    |
| Packaging Name | Nama Material     |
| Purchase UoM   | Satuan Pembelian  |
| Inventory UoM  | Satuan Stock      |
| Current Stock  | Stock Saat Ini    |
| Minimum Stock  | Minimum Stock     |
| Status         | Active / Inactive |

---

## Filters

* Search
* Status
* Low Stock Only

---

## Actions

* Create
* View
* Edit
* Archive
* Restore

---

## Detail Modal

### General Information

* Packaging Code
* Packaging Name
* Purchase UoM
* Inventory UoM
* Current Stock
* Minimum Stock
* Notes

### System Information

* Created At
* Created By
* Updated At
* Updated By

---

## Create/Edit Modal

| Field          | Required |
| -------------- | -------- |
| Packaging Name | Yes      |
| Purchase UoM   | Yes      |
| Inventory UoM  | Yes      |
| Minimum Stock  | Yes      |
| Notes          | No       |

---

## Validation Rules

* Packaging Name required
* Purchase UoM required
* Inventory UoM required

---

## Business Rules

* Packaging Code auto generated
* Dapat dibeli melalui Purchase Order
* Digunakan pada Packaging Recipe
* Biaya packaging masuk ke HPP produk

---

## Related Screens

* Purchase Orders
* Goods Receipts
* Packaging Recipes
* Stock Overview

---

# SUPPLIERS

## Purpose

Mengelola data supplier.

---

## Access Roles

* Owner
* Operations

---

## Screen Type

Table Page + Detail Modal + Create/Edit Modal

---

## Table Columns

| Column         | Description       |
| -------------- | ----------------- |
| Supplier Code  | Auto Generated    |
| Supplier Name  | Nama Supplier     |
| Contact Person | PIC               |
| Phone Number   | Telepon           |
| City           | Kota              |
| Status         | Active / Inactive |

---

## Filters

* Search
* City
* Status

---

## Actions

* Create
* View
* Edit
* Archive
* Restore

---

## Detail Modal

### General Information

* Supplier Code
* Supplier Name
* Contact Person
* Phone Number
* Email
* Address
* City
* Notes

### System Information

* Created At
* Created By
* Updated At
* Updated By

---

## Create/Edit Modal

| Field          | Required |
| -------------- | -------- |
| Supplier Name  | Yes      |
| Contact Person | No       |
| Phone Number   | No       |
| Email          | No       |
| Address        | No       |
| City           | No       |
| Notes          | No       |

---

## Validation Rules

* Supplier Name required

---

## Duplicate Detection

Jika ditemukan Supplier Name yang sama:

* Sistem menampilkan warning
* User dapat melanjutkan atau membatalkan

---

## Business Rules

* Supplier Code auto generated
* Supplier dapat digunakan pada Purchase Order

---

## Related Screens

* Purchase Orders
* Goods Receipts
* Supplier Price History

---

# CHANNELS

## Purpose

Mengelola sumber penjualan.

---

## Examples

* Shopee
* Tokopedia
* TikTok Shop
* WhatsApp
* Instagram
* Facebook

---

## Access Roles

* Owner
* Operations

---

## Screen Type

Table Page + Detail Modal + Create/Edit Modal

---

## Table Columns

| Column       | Description       |
| ------------ | ----------------- |
| Channel Code | Auto Generated    |
| Channel Name | Nama Channel      |
| Status       | Active / Inactive |

---

## Filters

* Search
* Status

---

## Actions

* Create
* View
* Edit
* Archive
* Restore

---

## Create/Edit Modal

| Field        | Required |
| ------------ | -------- |
| Channel Name | Yes      |

---

## Validation Rules

* Channel Name required
* Channel Name unique

---

## Business Rules

* Channel Code auto generated
* Digunakan pada Sales Order
* Digunakan pada Channel Performance Report

---

## Related Screens

* Sales Orders
* Channel Performance Report

---

# COURIERS

## Purpose

Mengelola data ekspedisi pengiriman.

---

## Examples

* JNE
* J&T
* SiCepat
* AnterAja
* POS Indonesia

---

## Access Roles

* Owner
* Operations

---

## Screen Type

Table Page + Detail Modal + Create/Edit Modal

---

## Table Columns

| Column       | Description       |
| ------------ | ----------------- |
| Courier Code | Auto Generated    |
| Courier Name | Nama Ekspedisi    |
| Status       | Active / Inactive |

---

## Filters

* Search
* Status

---

## Actions

* Create
* View
* Edit
* Archive
* Restore

---

## Create/Edit Modal

| Field        | Required |
| ------------ | -------- |
| Courier Name | Yes      |

---

## Validation Rules

* Courier Name required
* Courier Name unique

---

## Business Rules

* Courier Code auto generated
* Digunakan pada Shipment

---

## Related Screens

* Shipments
* Delivery Updates

---

# PART 1 COMPLETION CHECKLIST

## Dashboard

✅ Complete

## Categories

✅ Material Categories

✅ Product Categories

## Inventory Masters

✅ Materials

✅ Purchased Components

✅ Produced Components

✅ Products

✅ Packaging Materials

## Business Partners

✅ Suppliers

✅ Customers

## Sales Masters

✅ Channels

✅ Couriers

## System Masters

✅ UoM

✅ UoM Conversions

---

# PURCHASE ORDERS

## Purpose

Mengelola pembelian inventory dari supplier.

Purchase Order dapat digunakan untuk:

* Materials
* Purchased Components
* Packaging Materials

Purchase Order tidak digunakan untuk:

* Produced Components
* Products

---

## Access Roles

* Owner
* Operations

---

## Screen Type

List Page + Form Page

---

## Status Flow

```text
Draft
↓
Submitted
↓
Approved
↓
Partially Received
↓
Received
↓
Closed
```

Cancelled dapat dilakukan dari:

```text
Draft
Submitted
Approved
```

---

## List Page

### Columns

| Column       | Description    |
| ------------ | -------------- |
| PO Number    | Auto Generated |
| PO Date      | Tanggal PO     |
| Supplier     | Supplier       |
| Total Items  | Jumlah Item    |
| Total Amount | Nilai PO       |
| Status       | Status PO      |
| Created By   | User           |
| Created Date | Timestamp      |

---

### Filters

* Date Range
* Supplier
* Status
* Created By

---

### Actions

* Create PO
* View
* Edit Draft
* Approve
* Cancel
* Print PDF

---

## PO Form

### Header

| Field     | Required |
| --------- | -------- |
| PO Number | Auto     |
| PO Date   | Yes      |
| Supplier  | Yes      |
| Notes     | No       |

---

### Detail Lines

| Field        | Required |
| ------------ | -------- |
| Item         | Yes      |
| Quantity     | Yes      |
| Purchase UoM | Yes      |
| Unit Price   | Yes      |

---

### Calculated Fields

```text
Line Total

Qty × Unit Price
```

```text
PO Total

Sum(Line Total)
```

---

## Validation Rules

Supplier wajib dipilih.

Minimal 1 item.

Qty > 0

Unit Price > 0

---

## Business Rules

PO Number auto generated.

PO dapat berisi campuran:

* Material
* Purchased Component
* Packaging Material

PO tidak mengubah stock.

Stock bertambah saat Goods Receipt.

---

## Related Screens

* Suppliers
* Goods Receipts
* Supplier Price History

---

# GOODS RECEIPTS

## Purpose

Mencatat penerimaan barang dari supplier.

Goods Receipt menjadi sumber utama penambahan stock.

---

## Access Roles

* Owner
* Operations

---

## Screen Type

List Page + Form Page

---

## Status Flow

```text
Draft
↓
Posted
```

Setelah Posted:

```text
Tidak dapat diubah.
```

---

## List Page

### Columns

| Column       | Description    |
| ------------ | -------------- |
| GR Number    | Auto Generated |
| Receipt Date | Tanggal Terima |
| Supplier     | Supplier       |
| PO Number    | Referensi PO   |
| Status       | Status         |

---

### Filters

* Date Range
* Supplier
* Status

---

### Actions

* Create
* View
* Post

---

## Form

### Header

| Field        | Required |
| ------------ | -------- |
| GR Number    | Auto     |
| Receipt Date | Yes      |
| Supplier     | Yes      |
| PO Reference | Optional |

---

### Receipt Lines

| Field             | Required |
| ----------------- | -------- |
| Item              | Yes      |
| Quantity Received | Yes      |
| Purchase UoM      | Yes      |

---

## Validation Rules

Quantity Received > 0

---

## Business Rules

Posting Goods Receipt:

```text
Increase Inventory Stock
Create Stock Movement
Update Inventory Valuation
```

Jika berasal dari PO:

```text
Update PO Status
```

---

## Related Screens

* Purchase Orders
* Stock Movement
* Stock Overview

---

# SUPPLIER PRICE HISTORY

## Purpose

Menampilkan histori harga pembelian per supplier.

Digunakan untuk:

* Negosiasi supplier
* Analisa kenaikan harga
* Pemilihan supplier terbaik

---

## Access Roles

* Owner
* Operations

---

## Screen Type

Report Page

---

## Columns

| Column       | Description |
| ------------ | ----------- |
| Date         | Tanggal     |
| Supplier     | Supplier    |
| Item         | Item        |
| Purchase UoM | UoM         |
| Price        | Harga       |
| PO Number    | Referensi   |

---

## Filters

* Supplier
* Item
* Date Range

---

## Business Rules

Data berasal dari:

```text
Posted Goods Receipts
```

---

# STOCK OVERVIEW

## Purpose

Menampilkan posisi stock seluruh inventory.

---

## Access Roles

* Owner
* Operations

---

## Screen Type

Dashboard Page

---

## Columns

| Column        | Description                    |
| ------------- | ------------------------------ |
| Item Code     | Kode                           |
| Item Name     | Nama                           |
| Item Type     | Material / Component / Product |
| Current Stock | Stock                          |
| UoM           | UoM                            |
| Min Stock     | Minimum                        |
| Stock Status  | Normal / Low                   |

---

## Filters

* Item Type
* Category
* Low Stock Only

---

## Business Rules

Menampilkan stock real-time.

---

# STOCK MOVEMENT

## Purpose

Audit trail seluruh pergerakan stock.

---

## Access Roles

* Owner
* Operations

---

## Screen Type

Report Page

---

## Columns

| Column        | Description      |
| ------------- | ---------------- |
| Date          | Timestamp        |
| Item          | Item             |
| Movement Type | Transaction Type |
| Qty In        | Masuk            |
| Qty Out       | Keluar           |
| Balance       | Saldo            |
| Reference     | Referensi        |

---

## Movement Sources

### Inbound

* Goods Receipt
* Production Output
* Assembly Output
* Stock Adjustment (+)

### Outbound

* Production Consumption
* Assembly Consumption
* Packaging Consumption
* Shipment
* Stock Adjustment (-)

---

## Business Rules

Tidak dapat diedit manual.

---

# STOCK OPNAME

## Purpose

Melakukan perhitungan fisik stock.

---

## Access Roles

* Owner
* Operations

---

## Screen Type

List Page + Form Page

---

## Status Flow

```text
Draft
↓
Submitted
↓
Approved
↓
Posted
```

---

## Header

| Field         | Required |
| ------------- | -------- |
| Opname Number | Auto     |
| Opname Date   | Yes      |
| Notes         | No       |

---

## Detail Lines

| Field       | Description    |
| ----------- | -------------- |
| Item        | Inventory Item |
| System Qty  | Qty Sistem     |
| Counted Qty | Qty Fisik      |
| Difference  | Selisih        |

---

## Business Rules

Posting Stock Opname:

```text
Tidak mengubah stock.
```

Posting hanya menghasilkan:

```text
Variance Report
```

Selisih stock harus diselesaikan melalui:

```text
Stock Adjustment
```

---

# STOCK ADJUSTMENT

## Purpose

Melakukan koreksi stock berdasarkan hasil Stock Opname atau kebutuhan bisnis lainnya.

---

## Access Roles

* Owner

---

## Screen Type

List Page + Form Page

---

## Adjustment Types

### Increase

Stock bertambah.

### Decrease

Stock berkurang.

---

## Header

| Field             | Required |
| ----------------- | -------- |
| Adjustment Number | Auto     |
| Adjustment Date   | Yes      |
| Reason            | Yes      |

---

## Detail Lines

| Field     | Required            |
| --------- | ------------------- |
| Item      | Yes                 |
| Quantity  | Yes                 |
| Direction | Increase / Decrease |

---

## Required Reasons

Contoh:

```text
Stock Opname Correction
Damaged Item
Lost Item
Manual Correction
```

---

## Business Rules

Posting Adjustment:

```text
Update Stock
Create Stock Movement
Create Audit Log
```

---

# PART 2 COMPLETION CHECKLIST

## Purchasing

✅ Purchase Orders

✅ Goods Receipts

✅ Supplier Price History

---

## Inventory

✅ Stock Overview

✅ Stock Movement

✅ Stock Opname

✅ Stock Adjustment

---

# PART 2 STATUS

Ready For Review



