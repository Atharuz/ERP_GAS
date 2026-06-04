
# Ciluba ERP - Business Process Mapping v1.1

## Overview

Ciluba adalah usaha manufaktur mainan edukasi anak.

Model bisnis:

Supplier → Raw Material → Component Production → Assembly → Finished Goods → Sales → Shipping → Customer

---

# Business Goals

## Operational Goals

* Mengetahui stok aktual setiap saat
* Mengurangi stockout
* Mengetahui kebutuhan pembelian
* Mengetahui progres produksi
* Mengontrol proses assembly

## Financial Goals

* Menghitung HPP secara konsisten
* Mengetahui profit per produk
* Mengetahui biaya tersembunyi
* Mengetahui performa channel penjualan

## Management Goals

* Mengetahui siapa mengubah data
* Mengetahui histori transaksi
* Mengetahui performa supplier
* Mengetahui performa produk

---

# Core Business Flow

Supplier
→ Purchasing
→ Goods Receipt
→ Raw Material Inventory
→ Production
→ Component Inventory
→ Assembly
→ Finished Goods Inventory
→ Sales Order
→ Shipping
→ Customer
→ Reporting

---

# Purchasing Process

## Objective

Mengelola pembelian bahan baku dan material pendukung.

## Flow

Stock Monitoring
→ Purchase Request
→ Purchase Order
→ Goods Receipt
→ Inventory Update

## Outputs

* Purchase Request
* Purchase Order
* Goods Receipt
* Supplier Price History

## Stored Information

* Supplier
* Material
* Quantity
* Purchase Unit
* Unit Price
* Shipping Cost
* Purchase Date

---

# Supplier Price History

Tujuan:

Melacak perubahan harga supplier.

Contoh:

MDF

2026-01-01 : 38.000
2026-02-01 : 40.000
2026-03-01 : 42.000

ERP harus menyimpan histori harga setiap pembelian.

---

# Inventory Management

Inventory dibagi menjadi 3 kategori.

## Raw Material

Contoh:

* MDF
* Cat
* Tali
* Sekrup
* Lem

## Component

Contoh:

* Gear Besar
* Gear Kecil
* Roda Putar
* Panel Aktivitas

## Finished Goods

Contoh:

* Busy Cube
* Busy Board

---

# Unit of Measure (UoM)

ERP harus mendukung perbedaan antara:

* Purchase Unit
* Inventory Unit
* Consumption Unit

Contoh:

## Cat

Purchase Unit:

Kaleng

Inventory Unit:

Liter

Consumption Unit:

Ml

Conversion:

1 Kaleng = 1 Liter
1 Liter = 1000 Ml

---

## Tali

Purchase Unit:

Roll

Inventory Unit:

Meter

Consumption Unit:

Cm

Conversion:

1 Roll = 100 Meter
1 Meter = 100 Cm

---

Catatan:

UoM Conversion berbeda dengan Manufacturing Conversion.

Contoh:

1 MDF → 20 Gear

Ini termasuk proses produksi, bukan konversi satuan.

---

# Reorder Planning

Tujuan:

Menghindari kehabisan stok.

Setiap material memiliki:

* Minimum Stock
* Reorder Point
* Lead Time

Contoh:

MDF

Current Stock = 5
Minimum Stock = 10

Status:

REORDER REQUIRED

---

# Stock Opname

## Objective

Memastikan stok sistem sesuai dengan stok fisik.

## Frequency

### Daily

Item kritis:

* MDF
* Gear Besar
* Gear Kecil
* Busy Cube
* Busy Board

### Monthly

Semua item.

---

# Stock Adjustment

Dilakukan setelah stock opname.

Contoh:

System Stock = 150
Physical Stock = 127

Difference = -23

Adjustment dibuat dengan alasan:

* Damage
* Scrap
* Missing
* Input Error

---

# Production Process

## Objective

Mengubah Raw Material menjadi Component.

## Flow

Work Order
→ Material Issue
→ Production
→ Production Result
→ Component Inventory

## Outputs

* Work Order
* Material Consumption
* Production Result

---

# Production Variance

ERP harus menyimpan:

* Expected Output
* Actual Output
* Waste

Contoh:

Expected = 40 Gear

Actual = 34 Gear

Waste = 6 Gear

Tujuan:

Mengukur efisiensi produksi.

---

# Assembly Process

## Objective

Mengubah Component menjadi Finished Goods.

## Flow

Assembly Order
→ Component Consumption
→ Finished Goods Creation

## Outputs

* Assembly Order
* Finished Goods Receipt

---

# Packaging Process

Packaging dianggap sebagai inventory.

## Packaging Materials

* Kardus
* Sticker
* Bubble Wrap
* Lakban

Packaging harus masuk ke perhitungan HPP.

---

# Packaging BOM

Contoh:

Busy Cube

* Kardus M = 1
* Sticker = 1
* Bubble Wrap = 0.5 Meter
* Lakban = 0.2 Meter

Busy Board

* Kardus L = 1
* Sticker = 1
* Bubble Wrap = 1 Meter
* Lakban = 0.4 Meter

---

# Sales Process

## Sales Channels

* Shopee
* Tokopedia
* TikTok Shop
* WhatsApp
* Instagram
* Facebook

## Flow

Sales Order
→ Reservation
→ Packing
→ Shipping
→ Delivered

---

# Sales Order Status

* Draft
* Confirmed
* Waiting Production
* In Production
* Ready
* Shipped
* Delivered
* Cancelled

---

# Shipping Process

MVP Version:

Tracking dilakukan secara manual.

## Stored Information

* Courier
* Tracking Number
* Shipping Cost
* Shipping Date
* Delivery Date

---

# Customer Management

ERP harus menyimpan:

* Customer Name
* Phone Number
* City
* Sales Channel
* Total Orders
* Total Revenue

---

# Cost Structure

## Revenue

* Product Price

## Direct Material Cost

* MDF
* Cat
* Tali
* Sekrup
* Lem

## Packaging Cost

* Kardus
* Sticker
* Bubble Wrap
* Lakban

## Selling Cost

* Marketplace Fee
* Discount
* Shipping Subsidy

---

# Profit Calculation

Revenue

* Material Cost
* Packaging Cost
* Marketplace Fee
* Discount
* Shipping Subsidy

= Gross Profit

---

# Audit Log

## Objective

Mengetahui siapa mengubah data dan kapan.

## Audit Scope

### Master Data

* Material
* Supplier
* Product
* BOM

### Inventory

* Stock Adjustment
* Stock Opname
* Goods Receipt
* Goods Issue

### Transactions

* Purchase Order
* Sales Order
* Work Order
* Assembly Order

## Stored Information

* Timestamp
* User
* Action
* Entity
* Old Value
* New Value

---

# Reporting Requirements

## Sales Report

* Daily
* Weekly
* Monthly
* Yearly

## Inventory Report

* Stock On Hand
* Low Stock
* Dead Stock

## Purchasing Report

* Purchase History
* Supplier Performance
* Price Trend

## Manufacturing Report

* Work Order
* Production Output
* Waste

## Product Report

* Best Selling Product
* Slow Moving Product

## Channel Report

* Shopee
* Tokopedia
* TikTok Shop
* WhatsApp
* Instagram
* Facebook

## Profitability Report

* Revenue
* HPP
* Gross Profit
* Margin
* Profit Per Product

---

# Out Of Scope (Phase 1)

Tidak termasuk dalam MVP:

* Full Accounting
* General Ledger
* Balance Sheet
* Payroll
* HR Management
* Multi Warehouse
* Forecasting
* Multi Company

Akan dipertimbangkan pada fase berikutnya.
