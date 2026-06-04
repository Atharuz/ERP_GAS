# MASTER_DATA_CATALOG.md

# Ciluba ERP - Master Data Catalog v1.0

## Purpose

Dokumen ini mendefinisikan seluruh master data yang digunakan oleh ERP.

Master data menjadi referensi untuk:

* Purchasing
* Inventory
* Production
* Assembly
* Packaging
* Sales
* Reporting

---

# Master Data Overview

ERP menggunakan master data berikut:

1. Material Master
2. Component Master
3. Product Master
4. Packaging Master
5. Supplier Master
6. Customer Master
7. UoM Master
8. Sales Channel Master
9. Courier Master
10. Recipe Status Master

---

# Material Master

## Purpose

Menyimpan seluruh Raw Material yang dikonsumsi selama proses produksi.

## Categories

### Wood Material

Contoh:

* Papan Jati Belanda 1 cm
* Papan Jati Belanda 0.5 cm
* Papan Jati Belanda 2 cm

---

### Paint Material

Contoh:

* Cat Kayu Toska
* Cat Kayu Pink

---

### Finishing Material

Contoh:

* Beeswax

---

### Rope Material

Contoh:

* Tali Paracord

---

## Required Fields

| Field           | Description       |
| --------------- | ----------------- |
| Material Code   | Kode unik         |
| Material Name   | Nama material     |
| Category        | Kategori material |
| Purchase UoM    | Satuan beli       |
| Inventory UoM   | Satuan stok       |
| Consumption UoM | Satuan pemakaian  |
| Active          | Status aktif      |

---

# Purchased Component Master

## Purpose

Komponen yang dibeli jadi dan digunakan dalam proses assembly.

## Examples

* Skrup Topi
* Skrup Ring
* Ring Besi Pengait
* Handel Laci Bulat
* Gantungan Pigura
* Sodok Tas
* Gotri
* Krincingan
* Biji Genitri

---

## Required Fields

| Field          | Description   |
| -------------- | ------------- |
| Component Code | Kode unik     |
| Component Name | Nama komponen |
| Purchase UoM   | Satuan beli   |
| Inventory UoM  | Satuan stok   |
| Active         | Status aktif  |

---

# Produced Component Master

## Purpose

Komponen hasil produksi internal.

## Examples

* Cube Kayu 5x5
* Gear Besar
* Gear Kecil
* Panel Aktivitas
* Komponen Custom

---

## Required Fields

| Field             | Description   |
| ----------------- | ------------- |
| Component Code    | Kode unik     |
| Component Name    | Nama komponen |
| Inventory UoM     | Satuan stok   |
| Production Recipe | Recipe aktif  |
| Active            | Status aktif  |

---

# Product Master

## Purpose

Produk yang dijual ke customer.

## Existing Products

### FG-14121

Busy Cube Toska Easy

---

### FG-14122

Busy Cube Pink Easy

---

### FG-14123

Busy Board Pink Difficult

---

### FG-14124

Busy Board Toska Difficult

---

## Required Fields

| Field        | Description  |
| ------------ | ------------ |
| Product Code | Kode unik    |
| Product Name | Nama produk  |
| Product Type | Cube / Board |
| Sales Price  | Harga jual   |
| Weight       | Berat        |
| Active       | Status aktif |

---

# Packaging Material Master

## Purpose

Material untuk proses packing.

## Examples

* Kardus S
* Kardus M
* Kardus L
* Bubble Wrap
* Sticker Logo
* Lakban

---

## Required Fields

| Field          | Description   |
| -------------- | ------------- |
| Packaging Code | Kode unik     |
| Packaging Name | Nama material |
| Inventory UoM  | Satuan stok   |
| Active         | Status aktif  |

---

# Supplier Master

## Purpose

Menyimpan data vendor dan supplier.

## Required Fields

| Field          | Description   |
| -------------- | ------------- |
| Supplier Code  | Kode unik     |
| Supplier Name  | Nama supplier |
| Contact Person | PIC           |
| Phone          | Nomor telepon |
| City           | Kota          |
| Notes          | Catatan       |

---

# Customer Master

## Purpose

Menyimpan data pelanggan.

## Required Fields

| Field         | Description    |
| ------------- | -------------- |
| Customer Code | Kode unik      |
| Customer Name | Nama pelanggan |
| Phone         | Nomor telepon  |
| City          | Kota           |
| Notes         | Catatan        |

---

# UoM Master

## Purpose

Mengelola satuan dan konversi.

## Standard Units

### Quantity

* pcs
* pack
* lusin

---

### Length

* cm
* meter

---

### Volume

* ml
* liter

---

### Weight

* gram
* kg

---

### Sheet

* lembar

---

## UoM Conversion

### Length

1 meter = 100 cm

---

### Volume

1 liter = 1000 ml

---

### Quantity

1 lusin = 12 pcs

---

### Item Specific Conversion

Skrup Topi

1 pack = 100 pcs

Catatan:

Konversi item-specific disimpan per item.

---

# Sales Channel Master

## Purpose

Mengidentifikasi sumber penjualan.

## Existing Channels

* Shopee
* Tokopedia
* TikTok Shop
* WhatsApp
* Instagram
* Facebook

---

## Required Fields

| Field        | Description  |
| ------------ | ------------ |
| Channel Code | Kode unik    |
| Channel Name | Nama channel |
| Active       | Status aktif |

---

# Courier Master

## Purpose

Mengelola jasa pengiriman.

## Examples

* JNE
* J&T
* SiCepat
* AnterAja
* Pos Indonesia

---

## Required Fields

| Field        | Description  |
| ------------ | ------------ |
| Courier Code | Kode unik    |
| Courier Name | Nama kurir   |
| Active       | Status aktif |

---

# Recipe Status Master

## Purpose

Mengontrol status Production Recipe, Assembly Recipe, dan Packaging Recipe.

## Available Status

### Draft

Masih dalam tahap awal.

---

### Estimated

Sudah digunakan pada produksi nyata.

---

### Verified

Sudah tervalidasi.

---

### Obsolete

Sudah tidak digunakan.

---

# Data Governance Rules

## Rule 1

Setiap master data wajib memiliki kode unik.

---

## Rule 2

Master data tidak boleh dihapus.

Gunakan status:

Inactive

---

## Rule 3

Perubahan master data wajib tercatat dalam Audit Log.

---

## Rule 4

Setiap item harus memiliki kategori ERP yang jelas.

Kategori yang diperbolehkan:

* Raw Material
* Purchased Component
* Produced Component
* Packaging Material
* Finished Good

---

# Open Items

Masih perlu dilengkapi:

1. Daftar supplier lengkap.
2. Daftar packaging material lengkap.
3. Konversi pack untuk setiap item.
4. Produced Component hasil produksi nyata.
5. Berat aktual setiap produk.
6. Dimensi aktual setiap produk.
7. Kode standar seluruh master data.
