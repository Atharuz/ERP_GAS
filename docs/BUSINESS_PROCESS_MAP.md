# BUSINESS_PROCESS_MAP.md - Update v1.2

## Changes From v1.1

Dokumen diperbarui berdasarkan hasil diskusi desain manufaktur Ciluba.

Perubahan utama:

* Memisahkan Manufacturing BOM dan Assembly BOM.
* Menambahkan Production Recipe.
* Menambahkan Packaging Recipe.
* Menambahkan BOM Governance.
* Menambahkan Actual Usage Tracking.
* Menambahkan BOM Revision Management.

---

# Manufacturing Concept Revision

#Concept

Raw Material

↓

Production Recipe

↓

Produced Component

↓

Assembly Recipe

↓

Finished Goods

↓

Packaging Recipe

↓

Ready To Ship

---

# Production Recipe

## Purpose

Mendefinisikan bagaimana Raw Material diubah menjadi Produced Component.

Production Recipe digunakan oleh:

* Work Order
* Production Planning
* Material Consumption
* Cost Calculation

---

## Production Flow

Raw Material

↓

Production Recipe

↓

Work Order

↓

Produced Component

↓

Component Inventory

---

## Example

Papan Jati

Cat Toska

Beeswax

↓

Production Recipe

↓

Cube Kayu Toska

---

# Assembly Recipe

## Purpose

Mendefinisikan bagaimana Produced Component dan Purchased Component dirakit menjadi Finished Goods.

Assembly Recipe digunakan oleh:

* Assembly Order
* Product Costing
* Finished Goods Production

---

## Important Rule

Assembly Recipe TIDAK menggunakan Raw Material.

Assembly Recipe hanya boleh menggunakan:

* Produced Component
* Purchased Component

---

## Example

Cube Kayu Toska

Skrup Topi

Ring Besi

Rantai Nuri

↓

Assembly Recipe

↓

Busy Cube Toska Easy

---

# Packaging Recipe

## Purpose

Mendefinisikan kebutuhan packaging setiap Finished Goods.

Packaging Recipe digunakan untuk:

* Packaging Cost
* HPP
* Shipping Preparation

---

## Example

Busy Cube Toska Easy

↓

Packaging Recipe

↓

Kardus M

Bubble Wrap

Sticker

Lakban

↓

Ready To Ship

---

# BOM Governance

## Philosophy

Karena Ciluba masih dalam tahap validasi proses produksi, Recipe tidak harus langsung akurat.

Recipe dapat berkembang berdasarkan data produksi aktual.

---

# Recipe Status

## Draft

Belum tervalidasi.

Digunakan untuk estimasi awal.

---

## Estimated

Sudah digunakan beberapa kali produksi.

Masih dapat berubah.

---

## Verified

Sudah tervalidasi berdasarkan data produksi aktual.

Digunakan sebagai dasar costing resmi.

---

## Obsolete

Sudah tidak digunakan.

Tetap disimpan untuk histori.

---

# Recipe Versioning

Setiap perubahan Recipe harus menghasilkan versi baru.

Contoh:

Busy Cube Toska Easy

Version 1

↓

Version 2

↓

Version 3

---

ERP harus menyimpan:

* Version Number
* Effective Date
* Created By
* Notes

---

# Recipe Revision History

ERP harus mencatat:

* Siapa mengubah Recipe
* Kapan perubahan dilakukan
* Material yang ditambahkan
* Material yang dihapus
* Quantity yang berubah

---

# Actual Usage Tracking

## Purpose

Membandingkan estimasi Recipe dengan pemakaian aktual.

---

## Process

Recipe

↓

Work Order

↓

Actual Material Usage

↓

Variance Analysis

---

## Example

Recipe:

Cat Toska = 20 ml

Actual:

Cat Toska = 28 ml

Variance:

+8 ml

---

Data ini digunakan untuk:

* Penyempurnaan Recipe
* Perbaikan HPP
* Analisis Waste

---

# Copy Recipe

ERP harus mendukung:

* Create Empty Recipe
* Copy Existing Recipe

---

## Example

Busy Cube Pink Easy

↓

Copy Recipe

↓

Busy Cube Toska Easy

↓

Ubah Cat Pink menjadi Cat Toska

---

# Production Reporting Enhancement

Laporan produksi harus menampilkan:

* Planned Material Usage
* Actual Material Usage
* Variance
* Waste
* Yield

---

# Inventory Impact

Production Recipe:

Raw Material
↓
Berkurang

Produced Component
↓
Bertambah

---

Assembly Recipe:

Produced Component
↓
Berkurang

Purchased Component
↓
Berkurang

Finished Goods
↓
Bertambah

---

Packaging Recipe:

Packaging Material
↓
Berkurang

Ready To Ship Product
↓
Bertambah
