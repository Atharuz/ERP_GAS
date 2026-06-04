# Ciluba ERP - MVP Scope Definition v1.0

## Purpose

Dokumen ini mendefinisikan ruang lingkup Minimum Viable Product (MVP) ERP Ciluba.

Tujuan:

* Menjaga proyek tetap sederhana.
* Menghindari scope creep.
* Memastikan sistem dapat digunakan secepat mungkin.
* Menentukan prioritas pengembangan.

---

# MVP Objective

Pada akhir MVP, Owner harus dapat:

✅ Mengetahui stok aktual

✅ Mengetahui kebutuhan pembelian

✅ Mengetahui biaya material

✅ Mengetahui biaya packaging

✅ Mengetahui HPP dasar

✅ Mengetahui status produksi

✅ Mengetahui status assembly

✅ Mengetahui status pengiriman

✅ Mengetahui asal channel penjualan

✅ Mengetahui profit dasar per produk

---

# MVP Business Problems To Solve

## Inventory

Saat ini stok tidak tercatat dengan baik.

Target:

* Stock On Hand
* Stock Movement
* Stock Opname
* Low Stock Alert

---

## Purchasing

Saat ini pembelian tidak terdokumentasi.

Target:

* Purchase Order
* Goods Receipt
* Supplier Price History

---

## Production

Saat ini penggunaan material tidak terukur.

Target:

* Production Recipe
* Work Order
* Actual Usage Tracking

---

## Assembly

Saat ini proses perakitan tidak terdokumentasi.

Target:

* Assembly Recipe
* Assembly Order

---

## Sales

Saat ini asal penjualan sulit dilacak.

Target:

* Sales Order
* Channel Tracking

---

## Shipping

Saat ini pengiriman dipantau manual.

Target:

* Shipment Management
* Manual Delivery Update

---

# Included Modules

## Dashboard

Included

---

## Master Data

Included

Sub Modules:

* Material Master
* Purchased Component Master
* Produced Component Master
* Product Master
* Packaging Material Master
* Supplier Master
* Customer Master
* Channel Master
* Courier Master
* UoM Master

---

## Purchasing

Included

Sub Modules:

* Purchase Order
* Goods Receipt
* Supplier Price History

---

## Inventory

Included

Sub Modules:

* Stock Overview
* Stock Movement
* Stock Opname
* Stock Adjustment
* Low Stock Alert

---

## Manufacturing

Included

Sub Modules:

* Production Recipe
* Recipe Builder
* Work Order
* Production Variance

---

## Assembly

Included

Sub Modules:

* Assembly Recipe
* Assembly Order

---

## Packaging

Included

Sub Modules:

* Packaging Recipe
* Packaging Execution

---

## Sales

Included

Sub Modules:

* Sales Order
* Customer Management
* Channel Tracking
* Custom Order

---

## Shipping

Included

Sub Modules:

* Shipment
* Delivery Status

---

## Reports

Included

Sub Modules:

* Sales Report
* Inventory Report
* Purchasing Report
* Production Report
* Assembly Report
* Product Profitability
* Channel Performance

---

## Audit Log

Included

---

# Deferred Features

## Accounting

Not Included

Reason:

Memerlukan desain akun dan jurnal yang kompleks.

---

## Payroll

Not Included

Reason:

Belum memiliki kebutuhan payroll formal.

---

## HR

Not Included

Reason:

Jumlah karyawan masih sangat sedikit.

---

## CRM

Not Included

Reason:

Belum menjadi prioritas operasional.

---

## Multi Warehouse

Not Included

Reason:

Masih satu lokasi operasional.

---

## Multi Company

Not Included

Reason:

Hanya satu bisnis.

---

## Forecasting

Not Included

Reason:

Belum memiliki data historis yang cukup.

---

## Production Scheduling

Not Included

Reason:

Volume produksi masih rendah.

---

## Capacity Planning

Not Included

Reason:

Belum ada kebutuhan penjadwalan mesin atau operator.

---

## Barcode System

Not Included

Reason:

Jumlah SKU masih sedikit.

---

## QR Code Tracking

Not Included

Reason:

Belum memberikan manfaat signifikan pada tahap awal.

---

## Mobile Application

Not Included

Reason:

Web App sudah cukup untuk MVP.

---

## Marketplace Integration

Not Included

Reason:

Sinkronisasi otomatis dengan marketplace akan menambah kompleksitas besar.

Untuk MVP:

Input order dilakukan manual.

---

## Automatic Shipping Tracking

Not Included

Reason:

Status pengiriman masih diperbarui manual.

---

## WhatsApp Integration

Not Included

Reason:

Belum diperlukan untuk operasional inti.

---

# MVP Constraints

## Platform

Google Apps Script

---

## Database

Google Sheets

---

## Users

Maximum:

10 Users

---

## Company Structure

Single Company

---

## Warehouse Structure

Single Warehouse

---

## Currency

IDR Only

---

## Language

Bahasa Indonesia

---

# Success Metrics

## Inventory Accuracy

Target:

≥ 90%

---

## Purchase Recording

Target:

100% pembelian tercatat

---

## Production Recording

Target:

100% Work Order tercatat

---

## Assembly Recording

Target:

100% Assembly Order tercatat

---

## Sales Recording

Target:

100% Sales Order tercatat

---

## Shipping Recording

Target:

100% Shipment tercatat

---

# Phase 2 Candidates

Fitur yang dapat dipertimbangkan setelah MVP stabil:

* Accounting
* Marketplace Integration
* WhatsApp Integration
* Barcode System
* Forecasting
* Production Scheduling
* Mobile App
* Multi Warehouse

---

# Golden Rule

Jika muncul fitur baru selama pengembangan:

1. Evaluasi manfaat bisnis.
2. Cek dampak terhadap database.
3. Cek dampak terhadap UI.
4. Cek dampak terhadap timeline.
5. Jika tidak kritikal, masukkan ke Phase 2.

Jangan menambah fitur ke MVP tanpa alasan bisnis yang jelas.

---

# Definition of MVP Complete

ERP dianggap MVP Complete jika:

* Seluruh master data berjalan.
* Pembelian tercatat.
* Stok dapat dipantau.
* Production Recipe digunakan.
* Work Order digunakan.
* Assembly Order digunakan.
* Sales Order digunakan.
* Pengiriman tercatat.
* HPP dasar dapat dihitung.
* Laporan dasar tersedia.
* Audit Log aktif.

Pada tahap ini ERP sudah dapat digunakan untuk operasional harian Ciluba.
