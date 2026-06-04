# Ciluba ERP - Implementation Plan v1.0

## Purpose

Dokumen ini mendefinisikan urutan implementasi ERP Ciluba.

Tujuan utama:

* Menjaga scope tetap terkendali.
* Mengurangi risiko proyek gagal.
* Memastikan setiap fase menghasilkan manfaat nyata.
* Memudahkan pengembangan menggunakan AI.

---

# Development Principles

## Rule 1

Jangan membangun seluruh ERP sekaligus.

---

## Rule 2

Setiap fase harus dapat digunakan secara nyata.

---

## Rule 3

Setiap fase harus selesai dan stabil sebelum melanjutkan ke fase berikutnya.

---

## Rule 4

Tidak boleh membuat modul baru sebelum modul sebelumnya selesai diuji.

---

## Rule 5

Database harus selalu berkembang secara bertahap.

Jangan membuat tabel untuk fitur yang belum akan digunakan.

---

# Phase Overview

Phase 0

Project Foundation

↓

Phase 1

Master Data

↓

Phase 2

Inventory

↓

Phase 3

Purchasing

↓

Phase 4

Production

↓

Phase 5

Assembly

↓

Phase 6

Sales

↓

Phase 7

Shipping

↓

Phase 8

Reports

↓

Phase 9

Optimization

---

# Phase 0 - Project Foundation

## Goal

Membangun fondasi aplikasi.

---

## Deliverables

### Authentication

* Login
* Logout

---

### User Roles

* Owner
* Production
* Admin

---

### Layout

* Sidebar
* Header
* Footer

---

### Dashboard Skeleton

Placeholder widgets.

---

### Audit Log Framework

Belum digunakan penuh.

---

## Success Criteria

User dapat login.

User dapat mengakses menu sesuai role.

---

# Phase 1 - Master Data

## Goal

Membangun seluruh master data.

---

## Modules

### Material Master

### Purchased Component Master

### Produced Component Master

### Product Master

### Packaging Master

### Supplier Master

### Customer Master

### Channel Master

### Courier Master

### UoM Master

---

## Features

Create

Edit

Deactivate

Search

Filter

---

## Success Criteria

Semua master data dapat dikelola.

Tidak ada transaksi.

---

# Phase 2 - Inventory

## Goal

Mengetahui stok aktual.

---

## Modules

### Stock List

### Stock Movement

### Stock Adjustment

### Stock Opname

### Low Stock Alert

---

## Features

Stock On Hand

Movement History

Physical Count

Variance

Adjustment

---

## Success Criteria

Stok dapat dicatat dengan benar.

Stock Opname berjalan.

---

# Phase 3 - Purchasing

## Goal

Mengontrol pembelian.

---

## Modules

### Purchase Order

### Goods Receipt

### Supplier Price History

---

## Features

Create PO

Receive Material

Update Inventory

Price Tracking

---

## Success Criteria

Pembelian tercatat.

Harga supplier tersimpan.

---

# Phase 4 - Production

## Goal

Mengubah Raw Material menjadi Produced Component.

---

## Modules

### Production Recipe

### Recipe Builder

### Work Order

### Production Variance

---

## Features

Recipe Versioning

Copy Recipe

Material Consumption

Actual Usage Tracking

Variance Analysis

---

## Success Criteria

Produced Component dapat diproduksi melalui sistem.

---

# Phase 5 - Assembly

## Goal

Mengubah Produced Component menjadi Finished Goods.

---

## Modules

### Assembly Recipe

### Assembly Order

### Assembly Variance

---

## Features

Component Consumption

Finished Goods Output

Recipe Versioning

---

## Success Criteria

Finished Goods dapat dibuat melalui sistem.

---

# Phase 6 - Sales

## Goal

Mencatat seluruh pesanan.

---

## Modules

### Sales Order

### Customer Management

### Custom Order

---

## Features

Order Entry

Channel Tracking

Customer Tracking

Custom Cost

---

## Success Criteria

Semua penjualan tercatat.

Asal channel diketahui.

---

# Phase 7 - Shipping

## Goal

Mengontrol pengiriman.

---

## Modules

### Shipment

### Delivery Status

---

## Features

Input Resi

Courier Selection

Manual Delivery Update

---

## Success Criteria

Status pengiriman dapat dipantau.

---

# Phase 8 - Reports

## Goal

Menyediakan data untuk pengambilan keputusan.

---

## Reports

### Sales

### Inventory

### Purchasing

### Production

### Assembly

### Product Profitability

### Dead Stock

### Best Seller

### Channel Performance

---

## Success Criteria

Owner dapat melihat kondisi bisnis tanpa spreadsheet tambahan.

---

# Phase 9 - Optimization

## Goal

Penyempurnaan sistem.

---

## Candidates

### Advanced Dashboard

### Forecasting

### Mobile Layout

### Automation

### Integration

---

# MVP Definition

## Included

Master Data

Inventory

Purchasing

Production

Assembly

Sales

Shipping

Basic Reports

Audit Log

---

## Excluded

Accounting

Payroll

HR

CRM

Multi Warehouse

Multi Company

Forecasting

Mobile App

---

# AI Development Strategy

## Development Unit

AI hanya boleh mengerjakan:

1 Module

atau

1 Page

atau

1 Feature

dalam satu waktu.

---

## Example

GOOD

Create Product Master List Page

---

BAD

Create Complete ERP System

---

## Documentation Rule

Setiap perubahan harus memperbarui:

* BUSINESS_PROCESS_MAP.md
* MASTER_DATA_CATALOG.md
* BOM_STRATEGY.md
* ERP_MODULES.md
* DATABASE_DESIGN.md

jika terdampak.

---

# Change Management

Setiap fitur baru harus melalui:

Requirement

↓

Impact Analysis

↓

Documentation Update

↓

Implementation

↓

Testing

↓

Release

---

# Definition of Done

Sebuah fase dianggap selesai jika:

* Feature Complete
* User Tested
* Bug Fixed
* Documentation Updated
* Audit Log Working

---

# Recommended Build Order

1. Authentication

2. Master Data

3. Inventory

4. Purchasing

5. Production Recipe

6. Work Order

7. Assembly Recipe

8. Assembly Order

9. Sales Order

10. Shipping

11. Reports

12. Optimization

---

# Final Goal

Owner dapat mengetahui:

* Stok aktual
* Kebutuhan pembelian
* HPP produk
* Profit produk
* Sumber penjualan
* Status produksi
* Status pengiriman

dalam satu sistem terintegrasi.
