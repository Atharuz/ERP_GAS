# ERP Module Architecture v1.2

## Overview

ERP Ciluba dibangun menggunakan pendekatan modular yang mengikuti alur bisnis perusahaan dari pembelian bahan baku hingga pengiriman produk ke customer.

Setiap modul memiliki tanggung jawab yang jelas dan saling terintegrasi melalui inventory, production flow, dan sales flow.

---

# Module Structure

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
├── Recipe Builder
└── Work Orders

Assembly
├── Assembly Recipes
├── Recipe Builder
└── Assembly Orders

Packaging
├── Packaging Recipes
├── Recipe Builder
└── Packaging Execution

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

# Dashboard Module

## Purpose

Memberikan ringkasan operasional dan performa bisnis dalam satu layar.

## Features

### KPI Summary

* Revenue
* Gross Profit
* Total Orders
* Units Sold
* Inventory Value

### Operational Summary

* Open Purchase Orders
* Open Work Orders
* Open Assembly Orders
* Pending Shipments

### Alerts

* Low Stock Items
* Recent Activities

---

# Master Data Module

## Purpose

Menyimpan seluruh data referensi yang digunakan oleh sistem.

## Components

### Materials

Bahan baku yang digunakan pada proses produksi.

Contoh:

```text
MDF
Cat
Lem
```

---

### Produced Components

Komponen hasil produksi internal.

Contoh:

```text
Gear
Panel
Wheel
```

---

### Purchased Components

Komponen yang dibeli dari supplier.

Contoh:

```text
Bell
Magnet
Switch
```

---

### Products

Produk yang dijual ke customer.

Contoh:

```text
Busy Board
Busy Cube
```

---

### Suppliers

Data pemasok material dan komponen.

---

### Customers

Data customer.

Customer dapat dibuat otomatis saat Sales Order dibuat.

Sistem melakukan duplicate check menggunakan:

* Phone Number
* Customer Name

---

### Sales Channels

Contoh:

```text
Shopee
Tokopedia
WhatsApp
Instagram
Website
Offline
```

---

### Categories

Kategori item yang didefinisikan user.

Digunakan untuk:

* Materials
* Components
* Products

---

### Units of Measure

Contoh:

```text
PCS
Sheet
Meter
ML
KG
Pack
```

---

# Purchasing Module

## Purpose

Mengelola proses pembelian material dan komponen.

## Components

### Purchase Orders

Membuat pesanan pembelian ke supplier.

Status:

```text
Draft
Issued
Partially Received
Received
Closed
Cancelled
```

---

### Goods Receipts

Mencatat penerimaan barang dari supplier.

Fungsi:

* Menambah inventory
* Menyimpan harga pembelian
* Membentuk histori harga supplier

---

### Supplier Price History

Menampilkan histori harga pembelian berdasarkan supplier dan item.

Digunakan sebagai referensi pembelian berikutnya.

---

# Inventory Module

## Purpose

Mengelola seluruh pergerakan inventory.

## Components

### Stock Overview

Menampilkan saldo inventory saat ini.

Mendukung:

* Current Stock
* Minimum Stock
* Low Stock Alert

---

### Stock Movements

Audit seluruh transaksi inventory.

Sumber transaksi:

* Goods Receipt
* Work Order
* Assembly Order
* Packaging Execution
* Shipment
* Stock Adjustment

---

### Stock Opname

Mencatat hasil perhitungan fisik stock.

Tidak mengubah stock sistem.

---

### Stock Adjustments

Mengubah stock sistem berdasarkan hasil review.

Digunakan setelah Stock Opname.

---

# Production Module

## Purpose

Mengubah Raw Material menjadi Produced Component.

## Components

### Production Recipes

Mendefinisikan formula produksi.

Mendukung:

* Versioning
* Effective Date

---

### Recipe Builder

Menyusun material yang digunakan dalam proses produksi.

---

### Work Orders

Menjalankan proses produksi.

Status:

```text
Draft
Released
In Progress
Completed
Cancelled
```

Output:

```text
Raw Material
↓
Produced Component
```

---

# Assembly Module

## Purpose

Mengubah Produced Components dan Purchased Components menjadi Product.

## Components

### Assembly Recipes

Mendefinisikan struktur assembly produk.

---

### Recipe Builder

Menyusun komponen produk.

---

### Assembly Orders

Menjalankan proses assembly.

Status:

```text
Draft
Released
In Progress
Completed
Cancelled
```

Output:

```text
Produced Components
+
Purchased Components
↓
Product
```

---

# Packaging Module

## Purpose

Menyiapkan Product agar siap dikirim ke customer.

Packaging bukan menghasilkan item baru.

Packaging mengkonsumsi Packaging Material dan menambahkan biaya packaging ke HPP produk.

## Components

### Packaging Recipes

Mendefinisikan kebutuhan Packaging Material.

---

### Recipe Builder

Menyusun Packaging Material.

---

### Packaging Execution

Menjalankan proses packaging.

Status:

```text
Draft
Released
In Progress
Completed
Cancelled
```

Output:

```text
Product (Assembled)
+
Packaging Material
↓
Ready To Ship Product
```

Business Rules:

* Tidak menghasilkan Product baru
* Tidak mengubah quantity Product
* Mengkonsumsi Packaging Material
* Menambahkan Packaging Cost ke HPP
* Mengubah status menjadi Ready To Ship

---

# Sales Module

## Purpose

Mengelola penjualan dan pengiriman produk.

## Components

### Sales Orders

Mencatat pesanan customer.

Status:

```text
Draft
Confirmed
Shipped
Cancelled
```

Fitur:

* Customer Auto Create
* Duplicate Check
* Price Snapshot
* Inventory Reservation

---

### Inventory Reservation

Saat Sales Order dikonfirmasi:

```text
Ready To Ship
↓
Reserved
```

Validation:

```text
Order Qty
≤
Available Qty
```

---

### Shipments

Mencatat pengiriman barang.

Saat Shipment selesai:

* Reservation dilepas
* Stock berkurang
* Revenue diakui
* HPP diakui

---

### Customer History

Menampilkan histori transaksi customer.

---

### Sales History

Menampilkan histori penjualan.

---

# Reports Module

## Purpose

Menyediakan laporan operasional dan analitis.

## Report Categories

### Inventory Reports

* Stock Balance
* Stock Movement
* Low Stock

### Purchasing Reports

* Purchase Order Summary
* Supplier Price History

### Production Reports

* Work Order History
* Production Cost Analysis

### Assembly Reports

* Assembly History
* Product Cost Analysis

### Packaging Reports

* Packaging History

### Sales Reports

* Sales History
* Product Performance
* Channel Performance
* Customer Performance

### Profitability Reports

* Gross Profit
* Product Profitability

---

# System Module

## Purpose

Mendukung keamanan dan audit sistem.

## Components

### Audit Logs

Mencatat perubahan data.

Aktivitas:

```text
Create
Edit
Archive
Restore
```

---

### Activity Logs

Mencatat aktivitas pengguna.

Contoh:

```text
Login
Create Purchase Order
Complete Work Order
Complete Assembly Order
Complete Packaging Execution
Create Sales Order
Complete Shipment
```

---

### Settings

Konfigurasi sistem.

Meliputi:

* Company Settings
* User Management
* System Preferences

---

# Architecture Principles

## Inventory Driven

Semua proses bisnis terhubung melalui inventory.

---

## Recipe Based Manufacturing

Production, Assembly, dan Packaging menggunakan recipe yang terversi.

---

## Transaction Snapshot

Setiap transaksi menyimpan snapshot recipe dan harga pada saat transaksi dibuat.

---

## Auditability

Seluruh perubahan data dan aktivitas pengguna dapat ditelusuri melalui audit log.

---

## MVP Scope

Versi MVP tidak mencakup:

```text
Invoice Management
Accounts Receivable
Payment Tracking
Purchase Request
Approval Workflow
POS Module
Multi Warehouse
Multi Company
```
