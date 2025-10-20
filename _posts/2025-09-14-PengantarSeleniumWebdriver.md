---
layout: post
date: 2025-09-14
author: "Kelompok 7 - Sistem Informasi 2023"
title: "Pengantar Selenium WebDriver"
categories: [Software Development, Quality Assurance, Automation]
description: Panduan pengantar Selenium WebDriver, alat automasi browser open-source, keunggulannya, dan contoh test case untuk automasi web.
tags: [Selenium, WebDriver, Automation Testing, QA, Python, Java, Web Testing]
image: /assets/img/pengantar-selenium-webdriver.png
---

# **Pengantar Selenium WebDriver**

Selenium adalah sebuah *framework* *open-source* yang sangat populer untuk automasi *browser*. Kegunaan utamanya adalah untuk menguji aplikasi web secara otomatis dengan mensimulasikan interaksi pengguna langsung di berbagai *browser* seperti Chrome, Firefox, Edge, dan Safari.

> **Tujuan Utama:** Mengotomatiskan pengujian aplikasi web di berbagai browser dan platform untuk memastikan fungsionalitasnya berjalan sesuai harapan.

---

## **Apa itu Selenium WebDriver?**

**WebDriver** adalah komponen inti dan API utama dalam Selenium. Ia berfungsi sebagai "jembatan" atau penghubung yang memungkinkan kode program Anda (yang ditulis dalam bahasa seperti Python atau Java) untuk berkomunikasi dan memberi perintah langsung ke *browser*.

WebDriver inilah yang bertugas menjalankan perintah seperti:
* Membuka halaman web
* Mengklik tombol
* Mengisi formulir (input teks)
* Menjalankan navigasi (maju, mundur, *refresh*)
* Memvalidasi atau membaca teks pada halaman

---

## **Kenapa Harus Selenium?**

Selenium menjadi standar industri untuk automasi web karena beberapa alasan kuat:

* **Open-Source dan Gratis:** Tidak memerlukan biaya lisensi untuk digunakan.
* **Mendukung Banyak Bahasa:** Anda dapat menulis skrip pengujian menggunakan bahasa yang Anda kuasai, termasuk **Python**, **Java**, C#, dan JavaScript.
* **Multi-Platform:** Dapat dijalankan di berbagai sistem operasi seperti Windows, macOS, dan Linux.
* **Multi-Browser:** Mendukung semua *browser* modern utama (Chrome, Firefox, Safari, Edge).
* **Integrasi Mudah:** Bisa diintegrasikan dengan *framework testing* populer seperti Pytest, JUnit, dan TestNG untuk membuat laporan pengujian yang terstruktur.
* **Komunitas Besar:** Memiliki komunitas yang besar dan dokumentasi yang lengkap, sehingga mudah mencari solusi jika menemukan masalah.

---

## **Interaksi Dasar dengan Selenium**

Untuk memulai automasi, ada tiga langkah dasar yang perlu dipahami:

1.  **Instalasi:** Menginstal *library* Selenium untuk bahasa pemrograman Anda (misalnya, `pip install selenium` untuk Python).
2.  **Membuka Browser:** Menulis kode untuk menginisiasi WebDriver dan memerintahkannya membuka *browser* ke URL tertentu.
3.  **Interaksi dengan Elemen HTML:** Bagian terpentING, yaitu mencari elemen di halaman web (seperti tombol, *link*, atau *textbox*) dan melakukan aksi padanya.

---

## **Contoh Skenario & Test Case**

Mari kita lihat contoh penerapan Selenium untuk menguji halaman login "SauceDemo".

### **Test Scenario (Apa yang Diuji)**
* **TS-001:** Login berhasil di halaman SauceDemo.
* **TS-002:** Login gagal dengan kredensial yang salah.
* **TS-003:** Menambahkan produk ke keranjang setelah login berhasil.

### **Test Case (Bagaimana Mengujinya)**

| ID | Deskripsi | Steps (Langkah-langkah) | Expected Result (Hasil Diharapkan) |
| :--- | :--- | :--- | :--- |
| **TC-001** | Login sukses | 1. Buka browser ke halaman SauceDemo.<br>2. Input username: `standard_user`<br>3. Input password: `secret_sauce`<br>4. Klik tombol Login. | Pengguna berhasil masuk dan diarahkan ke halaman inventory. |
| **TC-002** | Login gagal | 1. Buka browser ke halaman SauceDemo.<br>2. Input username: `user_salah`<br>3. Input password: `secret_sauce`<br>4. Klik tombol Login. | Pengguna tetap di halaman login dan muncul pesan error kredensial salah. |
| **TC-003** | Tambah produk ke *cart* | 1. Lakukan langkah-langkah **TC-001** (Login sukses).<br>2. Di halaman inventory, klik tombol "Add to cart" pada satu produk. | Ikon keranjang (*cart*) di pojok kanan atas bertambah menjadi 1. |

---

## **Contoh Penggunaan**

Berikut adalah contoh sederhana penggunaan Selenium WebDriver untuk menguji halaman login:

```python
from selenium import webdriver

# Inisialisasi WebDriver
driver = webdriver.Chrome()
driver.get("https://saucedemo.com")

# Mengisi form login
driver.find_element_by_name("user-name").send_keys("standard_user")
driver.find_element_by_name("password").send_keys("secret_sauce")
driver.find_element_by_css_selector("input[type='submit']").click()

# Validasi URL
assert "inventory.html" in driver.current_url

# Menutup browser
driver.quit()
```

## **Sumber Daya Tambahan**

Untuk mempelajari lebih lanjut tentang Selenium WebDriver, Anda dapat mengunjungi:

- [Dokumentasi Resmi Selenium](https://www.selenium.dev/documentation/en/)
- [Tutorial Selenium di YouTube](https://www.youtube.com/results?search_query=selenium+tutorial)
- [Selenium GitHub Repository](https://github.com/SeleniumHQ/selenium)

---

## **Kesimpulan**

Selenium WebDriver adalah alat yang sangat kuat dan esensial dalam dunia *Software Quality Assurance*. Ia memungkinkan tim untuk mengotomatiskan pengujian fungsional aplikasi web yang repetitif, sehingga menghemat waktu dan memastikan kualitas rilis yang konsisten.

> **Pesan Utama:** Menguasai Selenium WebDriver adalah keterampilan kunci bagi siapa saja yang ingin serius dalam bidang automasi testing dan QA, memungkinkan pengujian yang lebih cepat, lebih andal, dan mencakup lebih banyak skenario.

---

## **Referensi**

Materi ini dirangkum dari presentasi "Pengantar Selenium WebDriver" oleh Kelompok 7 - Sistem Informasi 2023. Presentasi (PPT) lengkap dari materi ini dapat dilihat melalui tautan berikut:

[Lihat Presentasi (PPT)](https://drive.google.com/file/d/1G8XP7xVKPqGMZah4RyEfYVi3NrzOKuCo/view?usp=drive_link)