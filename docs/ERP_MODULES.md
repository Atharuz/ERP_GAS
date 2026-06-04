# Ciluba ERP - Module Architecture v1.0

## Purpose

Dokumen ini mendefinisikan seluruh modul ERP Ciluba sebagai dasar:

* UI Design
* Menu Structure
* Permission Design
* Database Design
* MVP Scope

---

# Module Architecture

Dashboard

Master Data

Purchasing

Inventory

Manufacturing

Assembly

Sales

Shipping

Reports

Audit Log

Settings

---

# Dashboard

## Purpose

Menampilkan kondisi bisnis secara real-time.

### Widgets

* Today's Revenue
* Orders Today
* Low Stock Alert
* Open Work Orders
* Open Assembly Orders
* Pending Shipments
* Top Selling Products
* Stock Value
* Monthly Revenue

---

# Master Data

## Purpose

Menyimpan seluruh data referensi ERP.

### Sub Modules

#### Material Master

Raw Material

Contoh:

* Papan Jati
* Cat
* Beeswax
* Tali

---

#### Purchased Component Master

Contoh:

* Skrup
* Ring
* Handel
* Krincingan

---

#### Produced Component Master

Contoh:

* Cube Kayu Toska
* Gear Besar
* Gear Kecil

---

#### Product Master

Contoh:

* Busy Cube Toska Easy
* Busy Cube Pink Easy
* Busy Board Pink Difficult
* Busy Board Toska Difficult

---

#### Packaging Material Master

Contoh:

* Kardus
* Bubble Wrap
* Sticker
* Lakban

---

#### Supplier Master

---

#### Customer Master

---

#### Sales Channel Master

* Shopee
* Tokopedia
* TikTok Shop
* WhatsApp
* Instagram
* Facebook

---

#### Courier Master

---

#### UoM Master

---

# Purchasing

## Purpose

Mengelola pembelian material dan komponen.

### Purchase Request

### Purchase Order

### Goods Receipt

### Supplier Price History

### Purchase Analytics

---

# Inventory

## Purpose

Mengelola seluruh stok.

### Stock Overview

### Stock Movement

### Stock Opname

### Stock Adjustment

### Reorder Monitoring

### Stock Valuation

---

# Manufacturing

## Purpose

Mengubah Raw Material menjadi Produced Component.

---

## Production Recipe

### Features

* Recipe Builder
* Copy Recipe
* Versioning
* Revision History
* Cost Preview

---

## Work Order

### Features

* Create Work Order
* Material Consumption
* Production Output
* Waste Recording

---

## Production Variance

### Features

* Planned Usage
* Actual Usage
* Variance

---

## Yield Analysis

### Features

* Yield Tracking
* Waste Percentage

---

# Assembly

## Purpose

Mengubah Produced Component menjadi Finished Goods.

---

## Assembly Recipe

### Features

* Recipe Builder
* Copy Recipe
* Versioning
* Revision History

---

## Assembly Order

### Features

* Create Assembly Order
* Component Consumption
* Finished Goods Output

---

## Assembly Variance

### Features

* Planned vs Actual

---

# Packaging

## Purpose

Mengelola kebutuhan packing.

---

## Packaging Recipe

### Features

* Packaging Builder
* Packaging Cost

---

## Packaging Execution

### Features

* Consume Packaging Material
* Mark Ready To Ship

---

# Sales

## Purpose

Mengelola pesanan pelanggan.

---

## Sales Order

### Features

* Create Order
* Edit Order
* Cancel Order

---

## Custom Order

### Features

* Customer Request
* Additional Cost
* Optional Components

---

## Customer Management

### Features

* Customer History
* Purchase History

---

# Shipping

## Purpose

Mengelola pengiriman.

Catatan:

Tracking masih dilakukan manual.

---

## Shipment

### Features

* Create Shipment
* Input Resi
* Select Courier

---

## Delivery Status

Status:

* Waiting Pickup
* Shipped
* Delivered

---

# Reports

## Sales Reports

* Daily
* Weekly
* Monthly
* Yearly

---

## Inventory Reports

* Stock On Hand
* Low Stock
* Dead Stock

---

## Purchasing Reports

* Purchase History
* Supplier Price Trend

---

## Manufacturing Reports

* Material Usage
* Waste Analysis
* Yield Analysis

---

## Assembly Reports

* Component Usage
* Product Output

---

## Product Reports

* Best Seller
* Slow Moving
* Profit Per Product

---

## Channel Reports

* Shopee
* Tokopedia
* TikTok Shop
* WhatsApp
* Instagram
* Facebook

---

## Financial Summary

* Revenue
* Material Cost
* Packaging Cost
* Gross Profit

---

# Audit Log

## Purpose

Mencatat seluruh perubahan penting.

---

## Tracked Activities

* Master Data Changes
* Recipe Changes
* Purchase Changes
* Inventory Adjustments
* Work Orders
* Assembly Orders
* Sales Orders

---

## Stored Data

* Timestamp
* User
* Action
* Entity
* Before Value
* After Value

---

# Settings

## Company Settings

---

## Numbering Settings

Examples:

PO-2026-0001

WO-2026-0001

AO-2026-0001

SO-2026-0001

---

## User Management

Roles:

### Owner

Full Access

---

### Production

Production + Inventory

---

### Admin

Sales + Shipping

---

# MVP Scope

## Included

✅ Dashboard

✅ Master Data

✅ Purchasing

✅ Inventory

✅ Manufacturing

✅ Assembly

✅ Packaging

✅ Sales

✅ Shipping

✅ Reports

✅ Audit Log

---

## Deferred

❌ Accounting

❌ Payroll

❌ HR

❌ CRM

❌ Multi Warehouse

❌ Multi Company

❌ Forecasting

❌ Mobile App
