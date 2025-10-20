---
layout: post
date: 2025-09-01
author: "Kelompok 4 - Sistem Informasi 2023"
title: "Test Scenario, Test Case, dan Bug Report"
categories: [Software Development, Quality Assurance]
description: Panduan praktis untuk memahami Test Scenario (Apa yang diuji), Test Case (Bagaimana menguji), dan Bug Report (Pelaporan kesalahan).
tags: [Test Scenario, Test Case, Bug Report, QA, Quality Assurance, Testing]
image: /assets/img/test-scenario-test-case-and-bug-report.png
---

# **Test Scenario, Test Case, dan Bug Report**

Test scenario, test case, dan bug report adalah tiga elemen penting dalam proses pengujian perangkat lunak. Ketiganya saling melengkapi untuk memastikan aplikasi berjalan sesuai harapan dan bebas dari kesalahan.

> **Tujuan Utama:** Memastikan aplikasi berjalan sesuai harapan dan bebas dari kesalahan dengan mendefinisikan apa yang diuji (Scenario), bagaimana cara mengujinya (Case), dan bagaimana melaporkan jika terjadi masalah (Bug Report).

---

## **Test Scenario vs. Test Case**

Perbedaan utama antara keduanya terletak pada fokus pertanyaan yang mereka jawab:

---

#### **Test Scenario: Apa yang Harus Diuji?**
* **Definisi:** Ini adalah gambaran umum tentang apa yang akan diuji untuk memastikan fungsi aplikasi sesuai kebutuhan. Ini berfokus pada fungsionalitas *end-to-end* dari perspektif pengguna.
* **Komponen Utama:**
    * **ID Scenario:** Nomor unik skenario.
    * **Deskripsi:** Ringkasan skenario pengujian.
    * **Modul/Fitur:** Modul atau fitur yang diuji.

---

#### **Test Case: Bagaimana Melakukan Pengujian?**
* **Definisi:** Ini adalah langkah-langkah detail pengujian, yang mencakup input spesifik, proses, dan hasil yang diharapkan (expected result).
* **Komponen Utama:**
    * **ID Test Case:** Nomor unik test case.
    * **Deskripsi:** Ringkasan singkat tentang pengujian.
    * **Precondition:** Kondisi awal sebelum pengujian.
    * **Test Steps:** Langkah-langkah detail pengujian.
    * **Test Data:** Data yang digunakan untuk pengujian.
    * **Expected Result:** Hasil yang diharapkan sesuai requirement.
    * **Actual Result:** Hasil aktual yang muncul setelah pengujian.
    * **Status:** Lulus/Gagal (Pass/Fail).

---

## **Bug Report: Laporan Formal Kesalahan**

Saat *Actual Result* dari sebuah *Test Case* tidak sesuai dengan *Expected Result*, sebuah **Bug Report** (Laporan Kesalahan) dibuat untuk developer. Laporan ini berisi detail masalah dan cara mereproduksinya.

Dua konsep penting dalam bug report adalah **Severity** dan **Priority**.

---

#### **Bug Severity: Ukuran Dampak Bug**
Ini mengukur seberapa besar dampak *bug* terhadap fungsionalitas perangkat lunak.
* **Critical:** Bug yang menyebabkan kegagalan total pada sistem atau fungsionalitas utama. Aplikasi tidak dapat digunakan atau data menjadi rusak.
* **Major (High):** Bug yang menyebabkan fungsionalitas utama tidak bekerja dengan benar, tetapi tidak menyebabkan sistem *crash* total.
* **Minor (Medium):** Bug yang tidak memengaruhi fungsionalitas utama, tetapi dapat menyebabkan ketidaknyamanan bagi pengguna.
* **Low:** Bug tidak mengakibatkan kerusakan pada sistem.

---

#### **Bug Priority: Ukuran Urgensi Perbaikan**
Ini menentukan seberapa mendesak *bug* tersebut harus diperbaiki, yang seringkali dipengaruhi oleh dampak bisnis.
* **P1 (Urgent/Critical):** Harus diperbaiki sesegera mungkin.
* **P2 (High):** Bug penting yang harus diperbaiki secepatnya karena memengaruhi banyak pengguna, tetapi tidak se-mendesak P1.
* **P3 (Medium):** Bug yang bisa diperbaiki di siklus rilis berikutnya. Tidak memengaruhi fungsionalitas inti.
* **P4 (Low):** Bug minor atau kosmetik yang bisa diperbaiki kapan saja.

---

#### **Komponen Utama Bug Report**
Sebuah bug report yang baik dan jelas biasanya mencakup:
* **Bug Title** & **Bug ID**
* **Step to Reproduce** (Langkah untuk mengulangi bug)
* **Actual Result** (Hasil yang sebenarnya terjadi)
* **Expected Result** (Hasil yang seharusnya terjadi)
* **Severity** & **Priority**
* **Assignee** (Developer yang ditugaskan) & **Reporter** (Penemu bug/QA)
* Informasi Lingkungan (cth: **Build Number**, **Testing on** seperti Android/iOS)

---

## **Cara Menghindari Bug**

Cara terbaik untuk menghindari *bug* dalam sebuah perangkat lunak adalah dengan menerapkan praktik terbaik di seluruh siklus pengembangan, tidak hanya saat pengujian.

Beberapa praktik terbaik tersebut meliputi:
* **1. Pahami Persyaratan:** Pastikan semua persyaratan dipahami dengan jelas oleh seluruh tim.
* **2. Unit Testing:** Lakukan pengujian unit untuk mendeteksi bug di tahap awal pengembangan.
* **3. Code Review:** Minta pengembang lain meninjau kode untuk menemukan kesalahan.
* **4. Rencana Pengujian:** Buat test plan yang komprehensif.
* **5. Pengujian Otomatis:** Manfaatkan *automation testing* untuk deteksi bug yang lebih cepat.
* **6. Kolaborasi Tim:** Tingkatkan komunikasi dan kolaborasi antara pengembang dan penguji.

---

## **Kesimpulan**

Test Scenario, Test Case, dan Bug Report adalah pilar dari *Quality Assurance*. Test Scenario menetapkan "apa" yang diuji, Test Case merinci "bagaimana" mengujinya, dan Bug Report adalah alat komunikasi formal ketika terjadi kegagalan.

> **Pesan Utama:** Menguasai pembuatan Test Scenario, Test Case, dan Bug Report yang efektif sangat penting untuk memastikan perangkat lunak yang dirilis memiliki kualitas tinggi, sesuai dengan kebutuhan pengguna, dan bebas dari kesalahan kritis.

---

## **Referensi**

Materi ini dirangkum dari presentasi "Test Scenario, Test Case, dan Bug Report" oleh Kelompok 4 - Sistem Informasi 2023. Presentasi (PPT) lengkap dari materi ini dapat dilihat melalui tautan berikut:

[Lihat Presentasi (PPT)](https://drive.google.com/file/d/1er2wwoA69y6OFqgGZCR4S9YeQEx0rM6z/view?usp=drive_link)