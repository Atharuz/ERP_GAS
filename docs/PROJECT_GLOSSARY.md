# Ciluba ERP - Project Glossary v1.0

## Purpose

Dokumen ini mendefinisikan istilah resmi yang digunakan dalam ERP Ciluba.

Tujuan:

* Menyamakan pemahaman seluruh tim.
* Menjadi referensi saat development.
* Menghindari penggunaan istilah yang berbeda untuk konsep yang sama.
* Menjadi acuan AI saat menghasilkan kode dan dokumentasi.

---

# General Rules

## Rule 1

Satu konsep hanya boleh memiliki satu istilah resmi.

---

## Rule 2

Gunakan istilah yang ada di dokumen ini pada:

* Database
* UI
* Dokumentasi
* Apps Script
* Testing

---

## Rule 3

Jika muncul istilah baru, wajib ditambahkan ke dokumen ini.

---

# Inventory Terms

## Item

Definisi:

Objek yang dapat dibeli, disimpan, diproduksi, dirakit, dijual, atau digunakan.

Kategori Item:

* Raw Material
* Purchased Component
* Produced Component
* Packaging Material
* Finished Good

---

## Stock

Definisi:

Jumlah item yang tersedia di inventory.

---

## Stock Movement

Definisi:

Perubahan stok akibat transaksi.

Contoh:

* Purchase
* Production
* Assembly
* Packaging
* Sales
* Adjustment
* Opname

---

## Stock Opname

Definisi:

Proses menghitung stok fisik dan membandingkannya dengan stok sistem.

---

## Stock Adjustment

Definisi:

Perubahan stok secara manual untuk memperbaiki selisih.

---

## Reorder Point

Definisi:

Batas minimum stok yang memicu rekomendasi pembelian.

---

# Item Categories

## Raw Material

Definisi:

Material dasar yang digunakan dalam proses produksi.

Contoh:

* Papan Jati
* Cat
* Beeswax
* Tali

---

## Purchased Component

Definisi:

Komponen yang dibeli dalam bentuk jadi dan digunakan dalam assembly.

Contoh:

* Skrup
* Ring
* Handel
* Krincingan

---

## Produced Component

Definisi:

Komponen yang diproduksi sendiri dari Raw Material.

Contoh:

* Cube Kayu Toska
* Gear Besar
* Gear Kecil

---

## Packaging Material

Definisi:

Material yang digunakan dalam proses packaging
untuk menyiapkan Finished Good agar siap dikirim.

Contoh:

* Kardus
* Bubble Wrap
* Sticker
* Lakban

---

## Finished Good

Definisi:

Produk yang selesai dirakit dan siap dijual.

Contoh:

* Busy Cube Toska Easy
* Busy Cube Pink Easy
* Busy Board Pink Difficult

---

# Purchasing Terms

## Supplier

Definisi:

Pihak yang memasok material atau komponen.

---

## Purchase Request (PR)

Definisi:

Permintaan pembelian internal.

Belum menjadi pesanan resmi.

---

## Purchase Order (PO)

Definisi:

Dokumen resmi pembelian kepada supplier.

---

## Goods Receipt (GR)

Definisi:

Pencatatan penerimaan barang dari supplier.

---

## Supplier Price History

Definisi:

Riwayat harga pembelian dari supplier.

---

# Production Terms

## Production Recipe

Definisi:

Dokumen yang menjelaskan bagaimana Raw Material diubah menjadi Produced Component.

---

## Recipe Builder

Definisi:

Fitur untuk membuat dan mengelola Production Recipe.

---

## Work Order (WO)

Definisi:

Perintah produksi berdasarkan Production Recipe.

---

## Material Consumption

Definisi:

Jumlah material yang digunakan selama produksi.

---

## Actual Usage

Definisi:

Jumlah material yang benar-benar digunakan.

---

## Planned Usage

Definisi:

Jumlah material yang dihitung berdasarkan Recipe.

---

## Variance

Definisi:

Selisih antara Planned Usage dan Actual Usage.

Formula:

Variance = Actual - Planned

---

## Yield

Definisi:

Persentase hasil produksi dibandingkan bahan yang digunakan.

---

## Waste

Definisi:

Material yang hilang, rusak, atau tidak dapat digunakan.

---

# Assembly Terms

## Assembly Recipe

Definisi:

Dokumen yang menjelaskan bagaimana Produced Component dan Purchased Component dirakit menjadi Finished Good.

---

## Assembly Order (AO)

Definisi:

Perintah perakitan berdasarkan Assembly Recipe.

---

## Component Consumption

Definisi:

Jumlah komponen yang digunakan saat assembly.

---

# Packaging Terms

## Packaging Recipe

Definisi:

Dokumen yang menjelaskan kebutuhan material packing untuk suatu produk.

---

## Packaging Execution

Definisi:

Proses penggunaan Packaging Material pada Finished Good.

---

## Ready To Ship

Definisi:

Status produk yang sudah selesai dipacking dan siap dikirim.

---

# Sales Terms

## Sales Order (SO)

Definisi:

Pesanan pelanggan yang tercatat dalam sistem.

---

## Customer

Definisi:

Pembeli produk Ciluba.

---

## Sales Channel

Definisi:

Sumber asal pesanan.

Contoh:

* Shopee
* Tokopedia
* TikTok Shop
* WhatsApp
* Instagram
* Facebook

---

## Custom Order

Definisi:

Pesanan yang memiliki spesifikasi khusus di luar produk standar.

---

# Shipping Terms

## Shipment

Definisi:

Proses pengiriman pesanan kepada customer.

---

## Courier

Definisi:

Perusahaan jasa pengiriman.

Contoh:

* JNE
* J&T
* SiCepat
* Pos Indonesia

---

## Tracking Number

Definisi:

Nomor resi pengiriman.

---

## Delivery Status

Status resmi:

* Waiting Pickup
* Shipped
* Delivered

Catatan:

Untuk MVP, status diperbarui secara manual.

---

# Costing Terms

## HPP

Definisi:

Harga Pokok Produksi.

Komponen:

* Material Cost
* Component Cost
* Packaging Cost

---

## Material Cost

Definisi:

Biaya seluruh Raw Material yang digunakan.

---

## Component Cost

Definisi:

Biaya Purchased Component dan Produced Component.

---

## Packaging Cost

Definisi:

Biaya material packing.

---

## Gross Profit

Formula:

Revenue - HPP

---

## Margin

Formula:

Gross Profit / Revenue × 100%

---

# System Terms

## Master Data

Definisi:

Data referensi yang digunakan oleh seluruh modul.

---

## Transaction

Definisi:

Aktivitas bisnis yang menghasilkan perubahan data.

---

## Audit Log

Definisi:

Catatan seluruh perubahan penting dalam sistem.

---

## Active

Definisi:

Status data yang masih dapat digunakan.

---

## Inactive

Definisi:

Status data yang tidak digunakan lagi tetapi tetap disimpan.

---

## Versioning

Definisi:

Mekanisme penyimpanan versi historis suatu Recipe.

---

## Revision History

Definisi:

Riwayat perubahan Recipe atau Master Data.

---

# Official Document Names

Dokumen resmi proyek:

* BUSINESS_PROCESS_MAP.md
* PRODUCT_STRUCTURE.md
* MASTER_DATA_CATALOG.md
* BOM_STRATEGY.md
* ERP_MODULES.md
* DATABASE_DESIGN.md
* UI_FLOW.md
* IMPLEMENTATION_PLAN.md
* PROJECT_GLOSSARY.md
* MVP_SCOPE.md

---

# Golden Rule

Jika terjadi konflik antara istilah yang digunakan oleh user, AI, dokumentasi lama, atau kode aplikasi:

Gunakan definisi yang ada di PROJECT_GLOSSARY.md sebagai sumber kebenaran utama (Single Source of Truth).
