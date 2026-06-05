# PRODUCT_STRUCTURE.md

# Ciluba ERP - Product Structure Mapping v1.1

## Purpose

Dokumen ini mendefinisikan struktur produk Ciluba sebagai dasar untuk:

* Inventory Management
* Purchasing
* Production
* Assembly
* BOM (Bill of Material)
* HPP Calculation
* Work Order
* Assembly Order
* Reporting

---

# Product Hierarchy

```text
Raw Material
│
├── Produced Component
│
├── Purchased Component
│
├── Packaging Material
│
└── Finished Goods
```

---

# ERP Item Classification

## Raw Material

Material yang akan dikonsumsi selama proses produksi.

### RM-1128

Nama:

Tali Paracord

Purchase UoM:

Panjang

Inventory UoM:

Meter

Consumption UoM:

Cm

---

### RM-1129

Nama:

Kepala Tali Sepatu

Inventory UoM:

Pcs

---

### RM-1133

Nama:

Beeswax

Purchase UoM:

Gram

Inventory UoM:

Gram

Consumption UoM:

Gram

---

### RM-1139

Nama:

Monte Kayu

Inventory UoM:

Pcs

---

### RM-1142

Nama:

Papan Jati Belanda Tebal 1 cm

Purchase UoM:

Lembar

Inventory UoM:

Lembar

Keterangan:

13 x 100 cm

---

### RM-1143

Nama:

Papan Jati Belanda Tebal 0.5 cm

Ukuran:

15 x 50 cm

---

### RM-1144

Nama:

Papan Jati Belanda Tebal 0.5 cm

Ukuran:

15 x 100 cm

---

### RM-1145

Nama:

Papan Jati Belanda Tebal 1 cm

Ukuran:

15 x 100 cm

---

### RM-1150

Nama:

Papan Jati Belanda Tebal 2 cm

Ukuran:

40 x 60 cm

---

### RM-1147

Nama:

Cube Kayu 5x5x5 cm

Inventory UoM:

Pcs

---

### RM-1148

Nama:

Cat Kayu Toska

Purchase UoM:

Kaleng

Inventory UoM:

Ml

Consumption UoM:

Ml

Catatan:

Master data perlu dibersihkan karena ID duplikat.

---

### RM-1149

Nama:

Cat Kayu Pink

Purchase UoM:

Kaleng

Inventory UoM:

Ml

Consumption UoM:

Ml

Catatan:

Master data perlu dibersihkan karena ID duplikat.

---

# Purchased Components

Komponen yang dibeli jadi dan langsung digunakan.

## PC-1121

Skrup Topi

Inventory UoM:

Pcs

Purchase UoM:

Pack

Konversi:

1 Pack = 100 pcs

---

## PC-1122

Skrup Panjang 1.5 cm

Purchase UoM:

Pack

Inventory UoM:

Pcs

Konversi Awal:

1/4 Pack = 50 pcs

Perlu validasi jumlah per pack.

---

## PC-1123

Skrup Panjang 1 cm

Purchase UoM:

Pack

Inventory UoM:

Pcs

---

## PC-1124

Skrup Ring

Purchase UoM:

Lusin

Inventory UoM:

Pcs

Konversi:

1 Lusin = 12 pcs

---

## PC-1125

Skrup Panjang 2 cm

Purchase UoM:

Pack

Inventory UoM:

Pcs

---

## PC-1126

Rantai Nuri

Inventory UoM:

Cm

---

## PC-1127

Ring Besi Pengait

Inventory UoM:

Pcs

---

## PC-1130

Gantungan Pigura

Inventory UoM:

Pcs

---

## PC-1131

Webbing Tas Putih

Inventory UoM:

Meter

Consumption UoM:

Cm

---

## PC-1132

Sodok Tas / Gesper

Inventory UoM:

Pcs

---

## PC-1134

Gotri 2 mm

Inventory UoM:

Pcs

---

## PC-1135

Gotri 3 mm

Inventory UoM:

Pcs

---

## PC-1136

Tali Elastis Coklat

Inventory UoM:

Cm

---

## PC-1137

Tali Wol Coklat

Inventory UoM:

Cm

---

## PC-1138

Krincingan Gantung 1.5 cm

Inventory UoM:

Pcs

---

## PC-1140

Biji Genitri Diameter 1 cm

Inventory UoM:

Pcs

---

## PC-1141

Biji Genitri Diameter 1.5 cm

Inventory UoM:

Pcs

---

## PC-1146

Handel Laci Bulat

Inventory UoM:

Pcs

---

# Produced Components

Belum terdefinisi.

Saat ini ERP harus menyiapkan kategori:

* Gear Besar
* Gear Kecil
* Panel Aktivitas
* Komponen Kayu Custom

Kategori ini akan muncul setelah BOM detail dibuat.

---

# Packaging Materials

Belum ada dalam master data.

Harus ditambahkan.

## PM-001

Kardus S

Inventory UoM:

Pcs

---

## PM-002

Kardus M

Inventory UoM:

Pcs

---

## PM-003

Kardus L

Inventory UoM:

Pcs

---

## PM-004

Sticker Logo

Inventory UoM:

Pcs

---

## PM-005

Bubble Wrap

Inventory UoM:

Meter

---

## PM-006

Lakban

Inventory UoM:

Meter

---

# Finished Goods

## FG-14121

Nama:

Busy Cube Toska Easy

Kategori:

Cube

Harga Jual:

98.000

Berat:

150 gr

Status:

Active

---

## FG-14122

Nama:

Busy Cube Pink Easy

Kategori:

Cube

Harga Jual:

98.000

Berat:

150 gr

Status:

Active

---

## FG-14123

Nama:

Busy Board Pink Difficult

Kategori:

Board

Harga Jual:

350.000

Berat:

3000 gr

Status:

Active

---

## FG-14124

Nama:

Busy Board Toska Difficult

Kategori:

Board

Harga Jual:

350.000

Berat:

3000 gr

Status:

Active

---

# Manufacturing Levels

Level 0

Raw Material

↓

Level 1

Produced Component

↓

Level 2

Finished Goods

↓

Level 3

Packaging Process

↓

Ready To Ship

↓

Customer

---

# UoM Conversion Requirements

## Length

1 Meter = 100 Cm

---

## Volume

1 Liter = 1000 Ml

---

## Quantity

1 Lusin = 12 Pcs

---

## Pack Conversion

Perlu master konversi khusus karena setiap item berbeda.

Contoh:

Skrup Topi

1 Pack = 100 pcs

Ring Besi

1 Pack = 100 pcs

---

# Current Product BOM Status

Busy Cube Toska Easy

Status:

Draft

Komposisi Saat Ini:

1221,1226,1121,1122,1123,1147

Perlu Mapping ke Nama Barang.

---

Busy Cube Pink Easy

Status:

Draft

Komposisi Saat Ini:

1124,1125,1126,1127,1223,1226

Perlu Mapping ke Nama Barang.

---

Busy Board Pink Difficult

Status:

Draft

Komposisi tersimpan tetapi belum memiliki quantity BOM.

---

Busy Board Toska Difficult

Status:

Draft

Komposisi tersimpan tetapi belum memiliki quantity BOM.

---

# Data Cleanup Required

Sebelum database dibuat:

1. Perbaiki ID 1148 duplikat.
2. Perbaiki ID 1149 duplikat.
3. Tentukan konversi setiap Pack.
4. Tambahkan Packaging Material.
5. Definisikan Produced Component.
6. Tambahkan Quantity pada seluruh BOM.
7. Tentukan pemakaian cat per produk.
8. Tentukan pemakaian tali per produk.
9. Tentukan waste factor produksi kayu.
10. Tentukan supplier untuk setiap material.

```
```
