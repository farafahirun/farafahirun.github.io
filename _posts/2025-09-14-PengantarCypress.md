---
layout: post
date: 2025-09-14
author: "Kelompok 8 - Sistem Informasi 2023"
title: "Pengantar Cypress"
categories: [Software Development, Quality Assurance, Automation]
description: Pengantar Cypress, framework end-to-end testing modern untuk aplikasi web. Mencakup setup, perintah dasar, keunggulan, dan contoh test case.
tags: [Cypress, Automation Testing, E2E Testing, QA, JavaScript, Web Testing]
image: /assets/img/pengantar-cypress.png
---

# **Pengantar Cypress**

Cypress adalah sebuah *framework* *end-to-end (E2E) testing* yang modern, dirancang khusus untuk menguji aplikasi web. Alat ini populer untuk menguji aplikasi yang dibangun dengan *framework* modern seperti React, Vue, dan Angular.

Dalam piramida pengujian, Cypress utamanya berada di level **End-to-End**, namun juga sangat mumpuni untuk digunakan di level **Integration Testing** dan **Component Testing**.

> **Tujuan Utama:** Menyediakan alat *testing* yang cepat, mudah di-setup, dan andal untuk menguji aplikasi web modern dari perspektif pengguna akhir.

---

## **Keunggulan Cypress**

Cypress memiliki beberapa fitur unggulan yang membuatnya berbeda dari *tools* automasi lain seperti Selenium:

* **Arsitektur Modern:** Cypress berjalan langsung di dalam *browser* (pada *run loop* yang sama dengan aplikasi Anda), memberikannya kontrol lebih cepat dan hasil yang lebih andal.
* **Test Runner Interaktif:** Fitur paling menonjol. Anda bisa melihat perintah dieksekusi secara visual, *real-time*, dan berinteraksi langsung dengan aplikasi Anda saat tes berjalan.
* **Time Travel:** Memungkinkan Anda untuk "kembali ke masa lalu" dengan melihat *snapshot* dari setiap langkah tes, memudahkan *debugging* saat terjadi kegagalan.
* **Automatic Waits:** Cypress secara otomatis menunggu elemen muncul di DOM dan perintah dijalankan. Anda tidak perlu menulis perintah `wait` atau `sleep` secara manual, yang membuat tes lebih stabil dan tidak *flaky*.

---

## **Setup dan Instalasi**

Memulai Cypress sangatlah mudah. Prasyarat utamanya hanyalah **Node.js** yang sudah terinstal di sistem Anda.

1.  **Inisialisasi Proyek (jika perlu):**
    ```bash
    npm init -y
    ```

2.  **Install Cypress:**
    ```bash
    npm install cypress --save-dev
    ```

3.  **Buka Cypress Test Runner:**
    ```bash
    npx cypress open
    ```
    Perintah ini akan membuka Test Runner interaktif untuk pertama kalinya dan membuat semua struktur folder yang diperlukan.

4.  **Jalankan Tes (via Terminal):**
    Untuk menjalankan tes di *headless mode* (tanpa membuka UI *browser*), Anda bisa menggunakan:
    ```bash
    npx cypress run --browser chrome
    ```

---

## **Perintah Dasar Cypress**

Sintaks Cypress sangat intuitif dan mudah dibaca, menyerupai bahasa alami.

| Perintah | Deskripsi |
| :--- | :--- |
| **`cy.visit('URL')`** | Membuka halaman web di *browser*. |
| **`cy.get('selector')`** | Mengambil satu atau lebih elemen berdasarkan *selector* (seperti ID, class, atau atribut). |
| **`cy.contains('text')`** | Mencari elemen berdasarkan teks yang terlihat di halaman. |
| **`cy.click()`** | Melakukan aksi klik pada elemen yang dipilih. |
| **`cy.type('text')`** | Mengetik teks ke dalam sebuah *input field* atau *textarea*. |
| **`cy.url()`** | Mendapatkan URL yang sedang aktif di *browser*. |

---

## **Studi Kasus: Login SauceDemo**

Berikut adalah contoh *test case* untuk menguji fungsionalitas login di website `saucedemo.com`.

| ID | Test Case | Steps (Langkah-langkah) | Expected Result (Hasil Diharapkan) |
| :--- | :--- | :--- | :--- |
| **TC01** | Login dengan username & password valid | 1. Buka halaman login.<br>2. Masukkan username: `standard_user`<br>3. Masukkan password: `secret_sauce`<br>4. Klik tombol login. | Berhasil masuk ke halaman inventory. |
| **TC02** | Login dengan password salah | 1. Buka halaman login.<br>2. Masukkan username: `standard_user`<br>3. Masukkan password: `wrong_pass`<br>4. Klik tombol login. | Muncul pesan error "Username and password do not match". |
| **TC03** | Login dengan username kosong | 1. Buka halaman login.<br>2. Kosongkan username.<br>3. Masukkan password: `secret_sauce`<br>4. Klik tombol login. | Muncul pesan error "Username is required". |

---

## **Contoh Penggunaan**

Berikut adalah contoh sederhana penggunaan Cypress untuk menguji halaman login:

```javascript
describe('Login Test', () => {
    it('should login with valid credentials', () => {
        cy.visit('https://saucedemo.com');
        cy.get('input[name="user-name"]').type('standard_user');
        cy.get('input[name="password"]').type('secret_sauce');
        cy.get('input[type="submit"]').click();
        cy.url().should('include', '/inventory.html');
    });
});
```

## **Sumber Daya Tambahan**

Untuk mempelajari lebih lanjut tentang Cypress, Anda dapat mengunjungi:

- [Dokumentasi Resmi Cypress](https://docs.cypress.io)
- [Tutorial Cypress di YouTube](https://www.youtube.com/results?search_query=cypress+tutorial)
- [Cypress GitHub Repository](https://github.com/cypress-io/cypress)

---

## **Kesimpulan**

Cypress adalah *framework testing* modern yang digunakan untuk menguji aplikasi web secara *end-to-end*. Dengan instalasi yang mudah dan fitur unggulan seperti Test Runner interaktif, *Time Travel*, dan *automatic waits*, Cypress memudahkan pengujian berbasis UI secara cepat dan efisien.

> **Pesan Utama:** Cypress menjadi alat yang andal untuk meningkatkan kualitas dan keandalan aplikasi web modern, karena struktur tesnya yang jelas serta perintah intuitif yang memungkinkan pengujian dilakukan seperti perilaku pengguna asli.

---

## **Referensi**

Materi ini dirangkum dari presentasi "Pengantar Cypress" oleh Kelompok 8 - Sistem Informasi 2023. Presentasi (PPT) lengkap dari materi ini dapat dilihat melalui tautan berikut:

[Lihat Presentasi (PPT)](https://drive.google.com/file/d/1lBwmTvmXF0iDxCIX0SbTfTBOQ7-eOLOx/view?usp=drive_link)