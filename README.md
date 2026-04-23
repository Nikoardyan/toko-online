# Alesha Collection — Online Furniture Store

> A full-stack PHP web application for an online furniture store, featuring a customer-facing storefront and a dedicated admin panel for managing products, orders, and financials.

![PHP](https://img.shields.io/badge/PHP-8.2-777BB4?style=flat-square&logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-MariaDB_10.4-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap-5-7952B3?style=flat-square&logo=bootstrap&logoColor=white)
![Server](https://img.shields.io/badge/Server-XAMPP-FB7A24?style=flat-square)
![Status](https://img.shields.io/badge/Status-Active-success?style=flat-square)

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Database Schema](#database-schema)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Screenshots](#screenshots)
- [Author](#author)

---

## Overview

**Alesha Collection** is a web-based e-commerce application built with PHP and MySQL, designed for a furniture retail business. It provides two separate interfaces: a customer storefront for browsing products and placing orders, and a full-featured admin panel for managing the entire operation — from product inventory to financial reporting.

---

## Features

### Customer Panel (`/`)

| Feature | Description |
|---|---|
| Product catalog | Browse furniture with category filtering and search |
| Product detail | View product description, photos, and stock availability |
| Shopping cart | Add, update, and remove items before checkout |
| Checkout | Fill in shipping details and select payment method |
| Payment upload | Upload proof of bank transfer payment |
| Order tracking | View order status: `pending`, `terkonfirmasi`, `dibatalkan` |
| Invoice | View and print customer invoice per order |
| User account | Register, login, edit profile |

### Admin Panel (`/adminpanel`)

| Feature | Description |
|---|---|
| Dashboard | Sales summary and key metrics |
| Product management | Add, edit, delete products and categories |
| Order management | Confirm or cancel incoming orders, print shipping receipt |
| Invoice management | View, detail, and delete invoices |
| Financial reports | Income (`data_masuk`), expenses (`data_keluar`), export to Excel |
| Summary report | Sales chart and revenue summary |
| Withdraw / transfer | Record fund withdrawals and transfers |
| Admin profile | Edit admin account details |

---

## Tech Stack

| Layer | Technology |
|---|---|
| Backend | PHP 8.2 (procedural + MySQLi) |
| Database | MariaDB 10.4 / MySQL |
| Frontend | HTML5, CSS3, Bootstrap 5 |
| Typography | Google Fonts — Poppins |
| Icons | Font Awesome |
| Local server | XAMPP / Laragon |
| DB admin | phpMyAdmin |

---

## Database Schema

The application uses a single database: `toko_online`, consisting of 10 tables.

| Table | Description |
|---|---|
| `users` | Registered customer accounts |
| `produk` | Product listings with stock and pricing |
| `kategori` | Product categories |
| `invoice` | Order header — customer info, status, payment method |
| `invoice_detail` | Line items per order |
| `order_details` | Order item records linked to products |
| `penjualan` | Sales records per product/category |
| `data_masuk` | Income records |
| `data_keluar` | Expense/withdrawal records |
| `messages` | Internal messaging |

### Order Status Flow

```
pending  →  terkonfirmasi
         →  dibatalkan
```

---

## Project Structure

```
Toko online/
│
├── index.php                    # Homepage — product catalog
├── login.php                    # Customer login
├── register.php                 # Customer registration
├── navbar.php                   # Shared navigation bar
├── produk-detail.php            # Product detail page
├── keranjang.php                # Shopping cart
├── checkout.php                 # Checkout form
├── beli.php                     # Buy now handler
├── purchase.php                 # Purchase processing
├── proses.php                   # Order processing logic
├── proses_pesanan.php           # Post-order handling
├── pesanan_belum_bayar.php      # Pending payment page
├── upload_bukti_pembayaran.php  # Payment proof upload
├── invoice_pelanggan.php        # Customer invoice view
├── confirmation.php             # Order confirmation page
├── profil.php                   # Customer profile
├── edit_profil.php              # Edit profile form
├── update_profil.php            # Update profile handler
├── logout.php                   # Session logout
│
├── adminpanel/
│   ├── index.php                # Admin dashboard
│   ├── login.php                # Admin login
│   ├── register.php             # Admin registration
│   ├── navbar.php               # Admin navigation
│   ├── session.php              # Session guard
│   ├── produk.php               # Product list & management
│   ├── produk-detail.php        # Admin product detail
│   ├── produk-edit.php          # Edit product
│   ├── produk-hapus.php         # Delete product
│   ├── kategori.php             # Category management
│   ├── kategori-detail.php      # Category detail
│   ├── kategori-hapus.php       # Delete category
│   ├── invoice.php              # Invoice list
│   ├── invoice-detail.php       # Invoice detail
│   ├── detail_invoice.php       # Extended invoice view
│   ├── manajemen_invoice.php    # Invoice management
│   ├── hapus_invoice.php        # Delete invoice
│   ├── daftar_invoice.php       # Invoice directory
│   ├── konfirmasi_pesanan.php   # Confirm orders
│   ├── ubah_status.php          # Update order status
│   ├── cetak_resi.php           # Print shipping receipt
│   ├── view_order.php           # View orders
│   ├── orders.php               # Orders list
│   ├── data_masuk.php           # Income records
│   ├── edit_data_masuk.php      # Edit income entry
│   ├── delete_data_masuk.php    # Delete income entry
│   ├── data_keluar.php          # Expense records
│   ├── export_data_keluar.php   # Export expenses to Excel
│   ├── tambah_pengeluaran.php   # Add expense entry
│   ├── summary_report.php       # Financial summary report
│   ├── chart.php                # Sales chart
│   ├── transfer_data.php        # Fund transfer recording
│   ├── withdraw_process.php     # Withdrawal processing
│   ├── take_money.php           # Cash withdrawal page
│   ├── admin_dashboard.php      # Dashboard panel
│   ├── profil.php               # Admin profile
│   └── logout.php               # Admin logout
│
├── bootstrap/                   # Bootstrap CSS/JS assets
├── css/                         # Custom stylesheets
├── js/                          # Custom scripts
├── image/                       # Static images
├── uploads/                     # Uploaded payment proofs
└── toko_online (2).sql          # Database dump
```

---

## Getting Started

### Prerequisites

- [XAMPP](https://www.apachefriends.org/) or [Laragon](https://laragon.org/) (PHP 8.x + MySQL)
- Web browser

### Installation

1. **Clone or extract** the project into your server's web root:

   ```bash
   # XAMPP
   C:/xampp/htdocs/toko-online/

   # Laragon
   C:/laragon/www/toko-online/
   ```

2. **Import the database** via phpMyAdmin:
   - Open `http://localhost/phpmyadmin`
   - Create a new database named `toko_online`
   - Import `toko_online (2).sql`

3. **Configure the database connection** — create or edit `koneksi.php` in the project root:

   ```php
   <?php
   $host   = "localhost";
   $user   = "root";
   $pass   = "";          // default XAMPP — change if needed
   $db     = "toko_online";

   $con = mysqli_connect($host, $user, $pass, $db);

   if (!$con) {
       die("Connection failed: " . mysqli_connect_error());
   }
   ?>
   ```

4. **Start Apache and MySQL** from the XAMPP/Laragon control panel.

5. **Open in browser:**
   - Customer storefront: `http://localhost/toko-online/`
   - Admin panel: `http://localhost/toko-online/adminpanel/`

---

## Usage

### Default Admin Credentials

| Field    | Value      |
|----------|------------|
| Username | `admin`    |
| Password | `admin2345` |

> **Security notice:** Change the default admin password immediately after first login, especially before deploying to production.

### Customer Flow

```
Register / Login  →  Browse Products  →  Add to Cart
→  Checkout  →  Upload Payment Proof  →  Wait for Confirmation
→  View Invoice
```

### Admin Flow

```
Login  →  Dashboard  →  Confirm Orders  →  Print Receipt
→  Manage Products & Categories  →  View Financial Reports
```

---

## Author

**Niko Ardyan**
