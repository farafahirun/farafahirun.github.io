---
layout: post
date: 2025-09-01
author: "Kelompok 3 - Sistem Informasi 2023"
title: "Testing Plan"
categories: [Software Development, Quality Assurance]
description: Panduan lengkap mengenai Testing Plan, tujuannya, dan 19 komponen utama berdasarkan standar IEEE 829 untuk memastikan pengujian terstruktur.
tags: [Software Testing, Test Plan, QA, Quality Assurance, SDLC]
image: /assets/img/testing-plan.png
---

# **Testing Plan**

*Testing Plan* (Rencana Pengujian) adalah dokumen panduan yang menjelaskan bagaimana proses pengujian perangkat lunak akan dilakukan. Dokumen ini berfungsi sebagai acuan resmi bagi tim penguji agar kegiatan pengujian lebih terarah dan konsisten.

Di dalamnya memuat ruang lingkup pengujian, strategi/metodologi yang dipakai, sumber daya (tim, alat, data uji), serta jadwal pelaksanaan.

> **Tujuan Utama:** Memberikan gambaran yang jelas tentang apa yang akan diuji, bagaimana cara mengujinya, serta mengoptimalkan penggunaan waktu, biaya, dan tenaga untuk menjamin perangkat lunak mencapai kualitas yang diterima pengguna.

---

## **Tujuan Testing Plan**

Membuat *Testing Plan* yang matang sangat penting untuk kesuksesan proyek. Beberapa tujuan utamanya adalah:

* **Memberikan Kejelasan:** Menyediakan gambaran yang jelas tentang apa saja yang akan diuji dan bagaimana cara mengujinya.
* **Memastikan Kualitas:** Memastikan proses pengujian dapat menemukan sebanyak mungkin kesalahan dan menjamin perangkat lunak mencapai kualitas yang dapat diterima pengguna.
* **Optimalisasi Sumber Daya:** Mengoptimalkan penggunaan waktu, biaya, dan tenaga yang dialokasikan untuk pengujian.
* **Dokumentasi:** Memberikan dokumentasi formal yang bisa dijadikan referensi dan bahan evaluasi pada proyek berikutnya.

---

## **Komponen Testing Plan (Standar IEEE 829)**

Rencana pengujian memiliki sejumlah komponen penting untuk memastikan seluruh aspek pengujian tercakup. Standar **IEEE 829-1988** mendefinisikan berbagai komponen yang idealnya ada dalam sebuah dokumen *test plan*.

Berikut adalah penjabaran komponen-komponen utamanya:

---

### **1. Test Plan Identifier**
* **Pengertian:** Penanda unik (biasanya kode atau nomor versi) untuk setiap dokumen *test plan*. Ini membantu membedakan rencana pengujian antar proyek atau antar versi.
* **Fungsi:** Memudahkan pengelolaan dokumen dan revisi, menjadi referensi jika ada perubahan, dan menghindari kebingungan.

### **2. References**
* **Pengertian:** Daftar semua dokumen, standar, atau sumber yang mendukung pembuatan *test plan* (misalnya, dokumen spesifikasi kebutuhan, desain sistem, dll.).
* **Fungsi:** Memastikan pengujian selaras dengan kebutuhan aplikasi, menjadi acuan jika terjadi perbedaan interpretasi, dan mendukung validitas hasil pengujian.

### **3. Introduction**
* **Pengertian:** Bagian pembuka yang berfungsi seperti *executive summary*. Bagian ini menjelaskan tujuan, ruang lingkup, dan fokus utama dari pengujian yang akan dilakukan.
* **Fungsi:** Memberi gambaran umum kepada *stakeholder* tentang arah pengujian sebelum masuk ke detail teknis.

### **4. Test Items**
* **Pengertian:** Komponen, fitur, modul, atau artefak perangkat lunak yang akan diuji. Ini adalah daftar "apa" saja yang masuk dalam ruang lingkup pengujian.

### **5. Software Risk Issues**
* **Pengertian:** Potensi risiko yang dapat muncul dari perangkat lunak maupun proses pengujiannya. Risiko ini perlu diidentifikasi agar tersedia rencana pencegahan dan penanganan.
* **Contoh Risiko:** Fitur yang kompleks atau modul baru, integrasi dengan sistem lain, kebutuhan yang samar, atau kesalahpahaman terhadap spesifikasi.

### **6. Features to be Tested**
* **Pengertian:** Daftar fitur atau fungsi perangkat lunak yang akan diuji dari sudut pandang pengguna. Fokusnya lebih pada deskripsi penggunaan dan tingkat risiko yang terkait.

### **7. Features not to be Tested**
* **Pengertian:** Daftar fitur yang secara eksplisit dikecualikan dari proses pengujian, beserta alasannya.
* **Alasan Umum:** Fitur tersebut mungkin sudah stabil, tidak direncanakan untuk dirilis, atau memiliki risiko rendah yang dapat diterima.

### **8. Approach**
* **Pengertian:** Mendefinisikan strategi atau pendekatan umum yang akan digunakan untuk menguji perangkat lunak.
* **Faktor Penentu:** Tipe pengujian (unit, integration, system), Teknik (black-box, white-box), Metode (manual, otomatis), dan Tujuan (validasi fungsional, kinerja, keamanan).

### **9. Item Pass/Fail Criteria**
* **Pengertian:** Menetapkan standar yang jelas dan terukur untuk menentukan apakah suatu *test item* (fitur atau modul) telah "Lulus" atau "Gagal" dalam pengujian.
* **Pass Criteria:** Cth: Semua *test case* utama berjalan sesuai harapan, tidak ada *bug* kritis, fungsi sesuai spesifikasi.
* **Fail Criteria:** Cth: Satu atau lebih *test case* gagal, ditemukan *defect* kritis, perilaku aplikasi tidak sesuai spesifikasi.

### **10. Suspension Criteria & Resumption Requirements**
* **Suspension Criteria:** Kondisi di mana pengujian harus dihentikan sementara (misalnya, ditemukan *bug* serius yang memblokir pengujian lain).
* **Resumption Requirements:** Kondisi yang harus dipenuhi sebelum pengujian dapat dilanjutkan kembali (misalnya, *bug* pemblokir telah diperbaiki dan diverifikasi).

### **11. Test Deliverables**
* **Pengertian:** Daftar semua dokumen, artefak, dan hasil nyata yang akan dihasilkan selama proses pengujian.
* **Contoh:** Dokumen *Test Plan* itu sendiri, *Test Case*, skrip otomasi, laporan *bug*, dan *Test Summary Report*.

### **12. Remaining Test Tasks**
* **Pengertian:** Daftar pekerjaan pengujian yang masih belum selesai pada saat laporan status dibuat, atau tugas-tugas yang harus diselesaikan sebelum pengujian bisa ditutup.

### **13. Environmental Needs**
* **Pengertian:** Spesifikasi dan konfigurasi lingkungan yang diperlukan agar pengujian dapat dijalankan secara valid, meliputi *hardware*, *software* (dan versinya), data uji, akses/*credential*, serta alat dan pengaturan jaringan.

### **14. Staffing and Training Needs**
* **Pengertian:** Mengidentifikasi kebutuhan personel dan pelatihan.
* **Staffing:** Menentukan peran yang dibutuhkan (Test Manager, Tester, dll.) dan kompetensi mereka.
* **Training:** Rencana pelatihan untuk memastikan tim siap menjalankan pengujian, mungkin termasuk *cheat-sheet* atau *cross-training*.

### **15. Responsibilities**
* **Pengertian:** Pembagian tanggung jawab yang jelas. Siapa yang bertugas melakukan koordinasi, menulis dan mengeksekusi *test case*, memverifikasi perbaikan, serta siapa yang berwenang mengambil keputusan.

### **16. Schedule**
* **Pengertian:** Garis waktu (timeline) untuk semua aktivitas pengujian.
* **Mencakup:** Waktu mulai, periode eksekusi, *milestone* penting (cth: *review test case*), jadwal *retest* (pengujian ulang), hingga tanggal *sign-off* rilis.

### **17. Planning Risks and Contingencies**
* **Pengertian:** Mengidentifikasi risiko yang terkait dengan *proyek pengujian* itu sendiri (berbeda dari *Software Risk Issues*) dan menyiapkan rencana darurat (kontingensi) jika risiko itu terjadi. (Cth: Risiko kekurangan sumber daya, jadwal *delay* dari *developer*).

### **18. Approvals**
* **Pengertian:** Bagian untuk persetujuan resmi.
* **Tujuan:** Memastikan semua pihak yang berkepentingan (misalnya, Manajer Proyek, Manajer Pengujian) telah menyetujui ruang lingkup, jadwal, dan sumber daya yang ditetapkan dalam *test plan*.

### **19. Glossary**
* **Pengertian:** Daftar istilah teknis, akronim, atau singkatan yang digunakan dalam dokumen *test plan* beserta definisinya, untuk memastikan semua pembaca memiliki pemahaman yang sama.

---

## **Kesimpulan**

*Testing Plan* adalah fondasi dari proses *Quality Assurance* yang sukses. Tanpa rencana yang jelas, pengujian menjadi tidak terarah, membuang sumber daya, dan berisiko melewatkan *bug* kritis.

> **Pesan Utama:** Membuat *Testing Plan* yang komprehensif berdasarkan standar seperti IEEE 829 adalah langkah krusial untuk memastikan proses pengujian berjalan efisien, terukur, dan efektif dalam menjamin kualitas perangkat lunak.

---

## **Referensi**

Materi ini dirangkum dari presentasi “Testing Plan” oleh Kelompok 3 - Sistem Informasi 2023. Presentasi (PPT) lengkap dari materi ini dapat dilihat melalui tautan berikut:

[Lihat Presentasi (PPT)](https://drive.google.com/file/d/1Pjx6n08veg7o6P-4LjazQCGOx29xH-YS/view?usp=drive_link)