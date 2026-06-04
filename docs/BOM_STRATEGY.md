# Ciluba ERP - BOM Strategy v1.0

## Purpose

Dokumen ini mendefinisikan strategi Recipe/BOM yang digunakan dalam ERP Ciluba.

Karena proses produksi Ciluba terdiri dari beberapa tahapan berbeda, ERP tidak menggunakan satu jenis BOM tunggal.

ERP menggunakan tiga jenis Recipe:

1. Production Recipe
2. Assembly Recipe
3. Packaging Recipe

---

# Manufacturing Philosophy

ERP memisahkan proses:

Raw Material
→ Produced Component
→ Finished Goods
→ Ready To Ship

Setiap tahap memiliki Recipe sendiri.

---

# Recipe Types

## Production Recipe

### Purpose

Mengubah Raw Material menjadi Produced Component.

### Input

Raw Material

Contoh:

* Papan Jati
* Cat Kayu
* Beeswax
* Tali Paracord

### Output

Produced Component

Contoh:

* Cube Kayu Toska
* Gear Besar
* Gear Kecil
* Panel Aktivitas

### Used By

* Work Order
* Material Consumption
* Production Planning
* Cost Calculation

---

## Assembly Recipe

### Purpose

Mengubah Produced Component menjadi Finished Goods.

### Important Rule

Assembly Recipe TIDAK boleh menggunakan Raw Material.

Assembly Recipe hanya boleh menggunakan:

* Produced Component
* Purchased Component

### Input

Produced Component

Contoh:

* Cube Kayu Toska
* Gear Besar
* Gear Kecil

Purchased Component

Contoh:

* Skrup Topi
* Ring Besi
* Handel Laci
* Rantai Nuri

### Output

Finished Goods

Contoh:

* Busy Cube Toska Easy
* Busy Cube Pink Easy
* Busy Board Pink Difficult
* Busy Board Toska Difficult

### Used By

* Assembly Order
* Product Costing
* Finished Goods Production

---

## Packaging Recipe

### Purpose

Mengelola kebutuhan packing setiap produk.

### Input

Packaging Material

Contoh:

* Kardus
* Bubble Wrap
* Sticker
* Lakban

### Output

Ready To Ship Product

### Used By

* Packaging Process
* Packaging Costing
* Shipping Preparation

---

# Recipe Lifecycle

Recipe tidak harus langsung sempurna.

Recipe berkembang berdasarkan data produksi aktual.

---

## Draft

Recipe awal.

Belum tervalidasi.

Dapat digunakan untuk estimasi.

---

## Estimated

Sudah digunakan pada beberapa produksi.

Masih dapat berubah.

---

## Verified

Sudah tervalidasi berdasarkan data aktual.

Digunakan sebagai dasar costing resmi.

---

## Obsolete

Sudah tidak digunakan.

Tetap disimpan untuk histori.

---

# Recipe Versioning

Setiap perubahan Recipe menghasilkan versi baru.

Contoh:

Busy Cube Toska Easy

Version 1

↓

Version 2

↓

Version 3

ERP tidak boleh menghapus versi lama.

---

# Recipe Revision History

ERP wajib menyimpan:

* Tanggal perubahan
* User
* Recipe Version
* Catatan perubahan

Contoh:

Version 3

Perubahan:

* Cat Toska 20 ml → 28 ml

---

# Recipe Builder

ERP menyediakan Recipe Builder untuk seluruh jenis Recipe.

---

## Create Empty Recipe

Membuat Recipe dari awal.

---

## Copy Existing Recipe

Menyalin Recipe yang sudah ada.

Contoh:

Busy Cube Pink Easy

↓

Copy Recipe

↓

Busy Cube Toska Easy

↓

Ubah Cat Pink menjadi Cat Toska

---

# Actual Usage Tracking

## Purpose

Membandingkan kebutuhan Recipe dengan pemakaian aktual.

---

## Process

Recipe

↓

Work Order / Assembly Order

↓

Actual Usage

↓

Variance Analysis

---

## Example

Recipe

Cat Toska = 20 ml

Actual Usage

Cat Toska = 28 ml

Variance

+8 ml

---

# Cost Preview

Recipe Builder harus dapat menghitung biaya estimasi secara otomatis.

Komponen biaya:

* Raw Material Cost
* Purchased Component Cost
* Packaging Cost

Output:

* Estimated Component Cost
* Estimated Product Cost

---

# Optional Components

Recipe dapat memiliki komponen opsional.

Contoh:

Krincingan

Optional = Yes

Saat menerima Custom Order, komponen opsional dapat ditambahkan atau dihapus tanpa membuat Product baru.

---

# Future Scope

Belum termasuk dalam MVP:

* Multi-level Manufacturing
* Alternative Recipe
* Engineering Change Management
* Automatic Yield Optimization
* Production Routing

---

# MVP Scope

Termasuk dalam MVP:

✅ Production Recipe

✅ Assembly Recipe

✅ Packaging Recipe

✅ Recipe Builder

✅ Copy Recipe

✅ Versioning

✅ Revision History

✅ Cost Preview

✅ Actual Usage Tracking

✅ Variance Analysis

✅ Optional Components

---

# Design Principles

1. Recipe harus mudah dibuat oleh user non-teknis.

2. Recipe dapat berkembang seiring pengalaman produksi.

3. Seluruh perubahan harus dapat diaudit.

4. Historical Recipe tidak boleh dihapus.

5. Costing harus selalu dapat ditelusuri ke Recipe yang digunakan saat produksi.
