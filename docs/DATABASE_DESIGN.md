# Ciluba ERP - Database Design v1.0

## Purpose

Dokumen ini mendefinisikan struktur database ERP Ciluba.

Database dirancang untuk:

* Google Sheets
* Google Apps Script
* Single Company
* Single Warehouse (MVP)

---

# Database Architecture

Master Data

↓

Recipe Data

↓

Transaction Data

↓

Reporting Data

↓

Audit Data

---

# MASTER TABLES

## materials

Raw Material

### Fields

* material_id
* material_code
* material_name
* category
* purchase_uom_id
* inventory_uom_id
* consumption_uom_id
* active
* created_at
* updated_at

---

## purchased_components

### Fields

* component_id
* component_code
* component_name
* purchase_uom_id
* inventory_uom_id
* active
* created_at
* updated_at

---

## produced_components

### Fields

* component_id
* component_code
* component_name
* inventory_uom_id
* active
* created_at
* updated_at

---

## products

### Fields

* product_id
* product_code
* product_name
* product_type
* selling_price
* weight
* active
* created_at
* updated_at

---

## packaging_materials

### Fields

* packaging_id
* packaging_code
* packaging_name
* inventory_uom_id
* active
* created_at
* updated_at

---

## suppliers

### Fields

* supplier_id
* supplier_code
* supplier_name
* phone
* city
* notes

---

## customers

### Fields

* customer_id
* customer_code
* customer_name
* phone
* city
* notes

---

## channels

### Fields

* channel_id
* channel_name

Examples:

Shopee

Tokopedia

TikTok Shop

WhatsApp

Instagram

Facebook

---

## couriers

### Fields

* courier_id
* courier_name

---

## uoms

### Fields

* uom_id
* uom_name
* category

Examples:

pcs

cm

meter

ml

liter

gram

kg

lembar

---

## uom_conversions

### Fields

* conversion_id
* from_uom_id
* to_uom_id
* ratio

Examples:

1 liter = 1000 ml

1 meter = 100 cm

---

# RECIPE TABLES

## recipes

### Fields

* recipe_id
* recipe_code
* recipe_name
* recipe_type
* product_id
* version
* status
* effective_date
* notes

recipe_type:

* production
* assembly
* packaging

---

## recipe_lines

### Fields

* recipe_line_id
* recipe_id
* item_type
* item_id
* quantity
* uom_id
* optional_flag

item_type:

* material
* purchased_component
* produced_component
* packaging

---

# TRANSACTION TABLES

## purchase_orders

### Fields

* po_id
* po_number
* supplier_id
* order_date
* status
* notes

---

## purchase_order_lines

### Fields

* po_line_id
* po_id
* item_type
* item_id
* quantity
* uom_id
* price

---

## goods_receipts

### Fields

* receipt_id
* po_id
* receipt_date

---

## inventory_transactions

### Fields

* trx_id
* trx_date
* item_type
* item_id
* transaction_type
* quantity
* uom_id
* reference_type
* reference_id

transaction_type:

* purchase
* production
* assembly
* packaging
* sale
* adjustment
* opname

---

## work_orders

### Fields

* wo_id
* wo_number
* recipe_id
* planned_qty
* actual_qty
* status

---

## work_order_materials

### Fields

* wo_material_id
* wo_id
* item_id
* planned_qty
* actual_qty

---

## assembly_orders

### Fields

* ao_id
* ao_number
* recipe_id
* planned_qty
* actual_qty
* status

---

## sales_orders

### Fields

* so_id
* so_number
* customer_id
* channel_id
* order_date
* status

---

## sales_order_lines

### Fields

* line_id
* so_id
* product_id
* qty
* price

---

## shipments

### Fields

* shipment_id
* so_id
* courier_id
* tracking_number
* shipment_status

shipment_status:

* waiting_pickup
* shipped
* delivered

---

## stock_opnames

### Fields

* opname_id
* opname_date
* notes

---

## stock_opname_lines

### Fields

* line_id
* opname_id
* item_type
* item_id
* system_qty
* actual_qty
* variance

---

# REPORTING TABLES

## product_costs

Materialized Cost Table

### Fields

* product_id
* material_cost
* packaging_cost
* total_cost
* updated_at

---

## inventory_snapshots

Daily Stock Snapshot

### Fields

* snapshot_date
* item_type
* item_id
* qty

---

# AUDIT TABLES

## audit_logs

### Fields

* log_id
* timestamp
* user_id
* entity_type
* entity_id
* action
* old_value
* new_value

---

# SYSTEM TABLES

## users

### Fields

* user_id
* name
* email
* role

roles:

* owner
* production
* admin

---

## settings

### Fields

* setting_key
* setting_value

---

# MVP Tables

Master Data

✔ materials

✔ purchased_components

✔ produced_components

✔ products

✔ packaging_materials

✔ suppliers

✔ customers

✔ channels

✔ couriers

✔ uoms

✔ uom_conversions

---

Recipes

✔ recipes

✔ recipe_lines

---

Transactions

✔ purchase_orders

✔ purchase_order_lines

✔ inventory_transactions

✔ work_orders

✔ assembly_orders

✔ sales_orders

✔ shipments

✔ stock_opnames

---

System

✔ users

✔ audit_logs

---

# Deferred

❌ Accounting

❌ Payroll

❌ CRM

❌ HR

❌ Forecasting

❌ Multi Warehouse

❌ Multi Company
