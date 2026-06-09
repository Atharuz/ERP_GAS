# Ciluba ERP
## Product Requirements Document (PRD)
**Version:** 1.1 (Updated & Frozen)  
**Platform:** Google Apps Script  
**Development Strategy:** Phased Approach (to ensure context stability and avoid GAS quota limits)

---

### 1. PROJECT OVERVIEW
**Objective**  
Membangun ERP internal berbasis Google Apps Script untuk mengelola:
- Procurement
- Inventory
- Production
- Assembly
- Packaging
- Marketing
- Sales
- Shipment  
dalam satu sistem terintegrasi dengan Single Source of Truth.

### 2. SYSTEM SCOPE
**Company Structure**  
- Single Company
- Single Warehouse

**User Scale**  
- Target: 1 – 15 User
- Recommended Concurrent Users: < 10 User

### 3. TECHNOLOGY STACK
- **Backend:** Google Apps Script
- **Frontend:** HTML Service, Bootstrap 5, Vanilla JavaScript
- **Database:** Google Spreadsheet (Setiap sheet dianggap sebagai table)
- **File Storage:** Google Drive

### 4. BUSINESS RULES
- **Inventory Driven:** Seluruh transaksi wajib menghasilkan inventory movement.
- **Costing Method:** Moving Average Cost (MAC). *Optimasi:* Perhitungan MAC dilakukan secara incremental. Sheet `inv_balance` menyimpan `Total_Qty` dan `Total_Value` yang di-update real-time per transaksi, menghindari pembacaan seluruh riwayat `inv_movements` untuk mencegah timeout GAS.
- **Reservation System:** Aktif. Formula: `Available Qty = On Hand Qty - Reserved Qty`.
- **Auto Numbering:** Semua dokumen menggunakan nomor otomatis dari `sys_document_sequences`.
- **Audit Trail:** Semua transaksi wajib tercatat di `sys_audit_logs` dan `inv_movements`.
- **Approval Workflow:** Tidak digunakan.
- **Excluded Modules:** Invoice, Account Receivable, Account Payable, Purchase Request.
- **Customer Creation:** Dibuat otomatis saat Sales Order pertama. Anti-duplikat berdasarkan `Customer Name` dan `Normalized Phone Number`.
- **Phone Normalization:** Semua input nomor HP di UI akan otomatis diawali '62' (jika belum) dan diformat menjadi string angka murni (misal: `6281234567890`) sebelum validasi duplikat dan penyimpanan.
- **Stock Opname Flow:** Count → Variance → Adjustment. Proses adjustment dieksekusi langsung tanpa approval, namun wajib mencatat history ke `inv_movements` (Movement Type: Stock Adjustment).

### 5. MASTER DATA
- **Category:** Material, Produced Component, Purchased Component, Product. (Code, Name, Type)
- **UOM:** Code, Name
- **Material:** Code, Name, Category, UOM, Minimum Stock
- **Produced Component:** Code, Name, Category, UOM
- **Purchased Component:** Code, Name, Category, UOM
- **Product:** Code, Name, Category, UOM
- **Supplier:** Code, Name, Phone, Email, Address
- **Customer:** Code, Name, Phone (Normalized to 62xxxxxxxxxx), Address. (Auto-generated jika belum ada saat SO).
- **Sales Channel:** Code, Name

### 6. MARKETING
*Tujuan: Mengatur harga jual dan promo. Tidak mempengaruhi costing.*
- **Pricing Strategy:** Strategy Code, Name, Start Date, End Date, Status (Fixed Price / Markup %)
- **Product Pricing:** Product, Selling Price, Effective Date
- **Promotion:** Promo Code, Name, Start Date, End Date, Type (Percentage Discount, Fixed Discount, Buy X Get Y)
- **Promotion Product:** Promo, Product, Discount Value

### 7. RECIPE MANAGEMENT
- **Production Recipe:** Input (Material) → Output (Produced Component)
- **Assembly Recipe:** Input (Produced Component, Purchased Component) → Output (Product)
- **Packaging Recipe:** Input (Packaging Material) → Output (Product). *Packaging Cost menambah Product Cost.*

### 8. PROCUREMENT
- **Purchase Order:** Status (Draft, Issued, Partially Received, Received, Cancelled)
- **Goods Receipt:** Fungsi: Add Inventory, Update Average Cost (Incremental).

### 9. PRODUCTION
- **Work Order:** 
  - Input: Material (berdasarkan Recipe)
  - Output: Produced Component
  - Additional Input: **Production Cost** (Manual input untuk biaya tenaga kerja/overhead pabrik)
  - Status: Draft, Released, In Progress, Completed, Cancelled
  - *Costing Formula:* Produced Component Cost = (Total Material Cost + Manual Production Cost) / Output Qty.

### 10. ASSEMBLY
- **Assembly Order:** 
  - Input: Produced Component, Purchased Component
  - Output: Product
  - Status: Draft, Released, In Progress, Completed, Cancelled

### 11. PACKAGING
- **Packaging Execution:** 
  - Input: Packaging Material
  - Output: Product
  - Status: Draft, Released, In Progress, Completed, Cancelled

### 12. SALES
- **Sales Order:** 
  - Header: SO Number, Order Date, Customer, Sales Channel, Notes
  - Lines: Product, Qty, Selling Price, Discount, Subtotal
  - Status: Draft, Confirmed, Shipped, Cancelled
  - Rules: Confirmed = Reserve Inventory. Cancelled = Release Reservation.

### 13. SHIPMENT
- **Shipment:** 
  - Fields: Shipment Number, Shipment Date, Sales Order
  - Status: Draft, Ready, Shipped, Cancelled
  - Rules: Shipped = Reduce Inventory, Release Reservation, Create Inventory Movement.

### 14. INVENTORY
- **Inventory Balance:** Item, Item Type, On Hand Qty, Reserved Qty, Available Qty, Average Cost, **Total_Qty** (untuk MAC incremental), **Total_Value** (untuk MAC incremental).
- **Inventory Movement:** Movement Types: Purchase Receipt, Production Issue, Production Receipt, Assembly Issue, Assembly Receipt, Packaging Issue, Packaging Receipt, Shipment, Stock Adjustment, Stock Opname.
- **Stock Opname:** Flow: Count → Variance → Adjustment. Eksekusi langsung memperbarui `inv_balance` dan mencatat `inv_movements`.
- **Stock Adjustment:** Manual correction. Wajib menyimpan alasan adjustment.

### 15. COSTING
- **Material Cost:** Berasal dari Goods Receipt (MAC incremental).
- **Produced Component Cost:** Material Cost + Production Cost (Manual input di Work Order).
- **Product Cost:** Produced Component Cost + Purchased Component Cost + Packaging Cost.

### 16. DASHBOARD
**Widgets (Manual Refresh, No Websocket):**
- Sales Today
- Sales This Month
- Inventory Value
- Low Stock Alert
- Open Purchase Orders
- Open Work Orders
- Open Assembly Orders
- Open Shipments

### 17. SECURITY
- **Roles:** Super Admin, Admin, Inventory, Production, Sales, Marketing.
- **Permission:** Berdasarkan module.

### 18. UI PRINCIPLES
- **Simple CRUD (Master Data):** Menggunakan modal popup standar. Tidak membuat halaman CRUD terpisah.
- **Complex Transactions (SO, PO, WO, Assembly, Packaging, Stock Opname):** Menggunakan **Full-Screen Modal** atau **Offcanvas Panel** (lebar 90-100% layar) untuk menampung Header, Detail Lines, pencarian produk, dan kalkulasi real-time dengan UX yang baik.
- **List Screen Components:** Search, Filter, Table, Pagination.
- **Form Screen Components:** Header, Detail Lines, Save, Cancel.
- **Phone Input:** UI form nomor HP otomatis menambahkan prefix `62` dan hanya menerima angka.

### 19. MENU STRUCTURE
1. Dashboard
2. Master Data (Categories, UOM, Materials, Produced Components, Purchased Components, Products, Suppliers, Customers, Sales Channels)
3. Marketing (Pricing Strategy, Product Pricing, Promotions)
4. Recipes (Production Recipes, Assembly Recipes, Packaging Recipes)
5. Procurement (Purchase Orders, Goods Receipts)
6. Production (Work Orders)
7. Assembly (Assembly Orders)
8. Packaging (Packaging Execution)
9. Sales (Sales Orders, Shipments)
10. Inventory (Inventory Balance, Inventory Movements, Stock Opname, Stock Adjustments)
11. Administration (Users, Roles, Settings, Audit Logs)

### 20. SPREADSHEET DATABASE SCHEMA
**Master Data:** `mst_categories`, `mst_uom`, `mst_materials`, `mst_produced_components`, `mst_purchased_components`, `mst_products`, `mst_suppliers`, `mst_customers`, `mst_sales_channels`  
**Marketing:** `mkt_pricing_strategies`, `mkt_product_pricing`, `mkt_promotions`, `mkt_promotion_products`  
**Recipes:** `recipe_production_headers`, `recipe_production_lines`, `recipe_assembly_headers`, `recipe_assembly_lines`, `recipe_packaging_headers`, `recipe_packaging_lines`  
**Procurement:** `trx_purchase_orders`, `trx_purchase_order_lines`, `trx_goods_receipts`, `trx_goods_receipt_lines`  
**Production:** `trx_work_orders` *(Tambah field: Production_Cost)*  
**Assembly:** `trx_assembly_orders`  
**Packaging:** `trx_packaging_execution`  
**Sales:** `trx_sales_orders`, `trx_sales_order_lines`, `trx_shipments`, `trx_shipment_lines`  
**Inventory:** `inv_balance` *(Tambah field: Total_Qty, Total_Value)*, `inv_movements`, `inv_stock_opname`, `inv_stock_adjustments`  
**System:** `sys_users`, `sys_roles`, `sys_permissions`, `sys_document_sequences`, `sys_audit_logs`, `sys_settings`

### 21. TECHNICAL ARCHITECTURE
**Layer Flow:**  
UI Layer (HTML/JS/Bootstrap) → Service Layer (GAS Business Logic) → Repository Layer (GAS Spreadsheet CRUD) → Google Spreadsheet.

### 22. SINGLE SOURCE OF TRUTH
Dokumen ini adalah referensi tertinggi proyek. Semua coding, database, UI, testing, dan maintenance harus mengikuti PRD ini. Jika terjadi konflik dengan dokumen lain atau instruksi sebelumnya, PRD ini selalu menjadi sumber kebenaran utama.

### 23. PHASED DEVELOPMENT STRATEGY (CRITICAL FOR CONTEXT STABILITY)
Untuk mencegah kehilangan konteks, error sinkronisasi, dan batas kuota GAS, pengembangan akan dilakukan secara bertahap. Setiap fase harus selesai dan diuji sebelum melanjutkan ke fase berikutnya:
- **Fase 1:** Inisialisasi Database (membuat semua sheet & header sesuai schema), Master Data CRUD, Inventory Balance & Movements (dengan logika MAC incremental), serta Dashboard dasar.
- **Fase 2:** Procurement (PO, Goods Receipt) dan Sales (SO, Shipment) + Logika Reservasi & Auto-Customer.
- **Fase 3:** Recipe Management, Production (dengan input Production Cost manual), Assembly, dan Packaging.
- **Fase 4:** Marketing (Pricing, Promo), User Roles, Settings, dan Audit Logs.
