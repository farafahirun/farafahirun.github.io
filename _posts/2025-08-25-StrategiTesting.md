---
layout: post
date: 2025-08-25
author: "Kelompok 1 - Sistem Informasi 2023"
title: "Strategi Testing"
categories: [Software Development, Quality Assurance]
description: Panduan komprehensif mengenai strategi software testing, mencakup siklus hidup (STLC), berbagai level klasifikasi (Abstraction, Function, Domain, Structure), dan pentingnya testing dalam SDLC.
tags: [Software Testing, STLC, SDLC, Unit Testing, Integration Testing, System Testing, Black Box, White Box, Quality Assurance]
image: /assets/img/strategi-testing.png
---

# **Strategi Software Testing**

## **Apa itu Software Testing?**

**Software Testing** adalah proses sistematis untuk mengevaluasi perangkat lunak dengan tujuan menemukan cacat (*bugs* atau *defects*) dan memastikan produk bekerja sesuai kebutuhan yang telah ditentukan, baik kebutuhan fungsional maupun non-fungsional.

> **Tujuan Utama:**  
> Menemukan dan memperbaiki kesalahan dalam perangkat lunak **sebelum** produk dirilis ke pengguna akhir, sehingga memastikan kualitas, keamanan, dan keandalan aplikasi.

### **Mengapa Testing Itu Penting?**

Bayangkan jika aplikasi banking Anda tiba-tiba error saat transfer uang, atau game favorit Anda *crash* di tengah permainan. Inilah yang dicegah oleh testing!

**6 Manfaat Utama Software Testing:**

| Manfaat | Penjelasan | Contoh Nyata |
|---------|------------|--------------|
| **Verifikasi & Validasi** | Memastikan software memenuhi spesifikasi dan kebutuhan user | Fitur "Lupa Password" benar-benar mengirim email reset |
| **Mengurangi Risiko** | Mengidentifikasi masalah sebelum user mengalaminya | Menemukan bug sebelum launch produk |
| **Efisiensi Biaya** | Memperbaiki bug saat development 10x lebih murah dari setelah rilis | Bug ditemukan saat coding = $100, setelah rilis = $1000+ |
| **Keamanan** | Menemukan celah keamanan sebelum dieksploitasi hacker | Mencegah SQL Injection, XSS attacks |
| **User Experience** | Memastikan aplikasi mudah digunakan dan menyenangkan | Navigasi lancar, loading cepat, UI intuitif |
| **Kepercayaan Stakeholder** | Membuktikan produk stabil dan berkualitas | Investor dan client yakin dengan produk kita |

> **Fun Fact:** 
> Menurut IBM, biaya memperbaiki bug setelah produk rilis bisa **100x lebih mahal** dibanding memperbaikinya saat fase development!

---

## **Posisi Testing dalam SDLC**

Testing bukanlah aktivitas yang berdiri sendiri. Ini adalah fase integral dari **Software Development Life Cycle (SDLC)**, atau Siklus Hidup Pengembangan Perangkat Lunak.

### **Kapan Testing Dilakukan?**

```
SDLC Phases:
┌─────────────────────────────────────────────────────────────┐
│  Planning → Analysis → Design → Development → Testing → Deploy  │
│                          ↓           ↓          ↓           │
│                      [Unit Test] [Integration] [System]     │
│                                                              │
│  Testing dilakukan di SETIAP FASE, bukan hanya di akhir!    │
└─────────────────────────────────────────────────────────────┘
```

**Testing Modern: Shift-Left Approach**
- Testing dimulai dari fase **Planning & Design** (lebih awal = lebih baik!)
- Developer menulis **Unit Test** saat coding

- **Continuous Testing** di setiap commit (CI/CD)
- **Acceptance Testing** sebelum deployment

---

## **Software Testing Life Cycle (STLC)**

**STLC** adalah proses sistematis yang diikuti tim Quality Assurance (QA) untuk memastikan pengujian dilakukan secara efektif dan terstruktur. STLC memiliki fase-fase spesifik dengan tujuan dan hasil yang jelas.

### **Fase-Fase STLC**

```
Test Planning → Test Design → Test Execution → Reporting
      ↓              ↓              ↓              ↓
  Strategi       Skenario       Jalankan       Analisis
   & Scope       & Data         Testing        & Lapor
```

### **1. Test Planning (Perencanaan Pengujian)**

**Tujuan:** Menentukan strategi dan ruang lingkup pengujian

**Aktivitas Utama:**
- **Membuat Test Strategy** - Tentukan pendekatan testing (manual/automation, tools yang digunakan)
- **Menentukan Scope** - Apa yang akan diuji dan apa yang tidak
- **Setup Test Environment** - Persiapkan server, database, browser untuk testing
- **Assign Resources** - Tentukan siapa mengerjakan apa
- **Estimasi Timeline** - Berapa lama testing akan berlangsung
- **Budget Planning** - Estimasi biaya testing

**Output:**
- Test Plan Document
- Test Strategy Document
- Effort Estimation

**Contoh:**
> "Kita akan test aplikasi e-commerce dengan 5 tester, menggunakan Selenium untuk automation, fokus pada flow checkout dan payment, estimasi 2 minggu."

---

### **2. Test Design (Perancangan Pengujian)**

**Tujuan:** Mengubah rencana menjadi skenario pengujian yang detail dan actionable

**Aktivitas Utama:**
- **Menulis Test Cases** - Detail langkah-langkah testing
- **Membuat Test Data** - Siapkan data dummy (user, produk, transaksi)
- **Menentukan Expected Results** - Apa hasil yang diharapkan dari setiap test
- **Requirement Traceability Matrix (RTM)** - Mapping requirement dengan test case
- **Test Scenario Creation** - Buat skenario end-to-end

**Output:**
- Test Cases & Test Scripts
- Test Data
- RTM (Requirement Traceability Matrix)
**Contoh Test Case:**

| Test Case ID | TC_LOGIN_001 |
|--------------|--------------|
| **Title** | Login dengan kredensial valid |
| **Precondition** | User sudah terdaftar di sistem |
| **Steps** | 1. Buka halaman login<br>2. Masukkan email valid<br>3. Masukkan password valid<br>4. Klik tombol Login |
| **Expected Result** | User berhasil login dan diarahkan ke dashboard |
| **Test Data** | Email: test@example.com<br>Password: Test123! |

---

### **Test Execution (Pelaksanaan Pengujian)**

**Tujuan:** Menjalankan test cases dan membandingkan hasil aktual dengan hasil yang diharapkan

**Aktivitas Utama:**
- **Execute Test Cases** - Jalankan testing sesuai skenario
- **Bug Logging** - Catat setiap bug yang ditemukan di bug tracking tool (Jira, Trello)
- **Regression Testing** - Test ulang fitur lama setelah ada perubahan
- **Screenshot & Video** - Dokumentasi bug untuk developer
- **Re-testing** - Test ulang bug yang sudah diperbaiki
**Jenis Testing yang Dilakukan:**

#### **a) Component/Unit Testing**
- Testing komponen terkecil (fungsi, method, class)
- Biasanya dilakukan oleh **Developer**
- Contoh: Test fungsi `calculateDiscount()`

#### **b) Integration Testing**
- Testing interaksi antar modul/komponen
- Memastikan API, database, services berkomunikasi dengan benar
- Contoh: Test koneksi Login Module → Database → Session Management

#### **c) System Testing**
- Testing sistem secara keseluruhan (end-to-end)
- Dilakukan oleh **QA Team**
- Contoh: Test full flow dari browse produk → checkout → payment → konfirmasi

#### **d) Acceptance Testing (UAT)**
- Testing oleh **User/Client** sebelum go-live
- Memvalidasi apakah sistem memenuhi kebutuhan bisnis
- Contoh: Client mencoba semua fitur dan memberikan approval

**Output:**
- Test Execution Report
- Bug Reports
- Test Logs
**Status Test Case:**
- **Passed** - Test berhasil, sesuai expected result
- **Failed** - Test gagal, ditemukan bug
- **Blocked** - Test tidak bisa dijalankan karena dependency issue
- **Skipped** - Test dilewati karena alasan tertentu

---

### **Test Reporting & Analysis (Pelaporan & Analisis)**

**Tujuan:** Mengumpulkan, menganalisis, dan melaporkan hasil testing kepada stakeholder

**Aktivitas Utama:**
- **Generate Test Metrics** - Statistik testing (pass rate, bug count, dll)
- **Bug Analysis** - Klasifikasi bug berdasarkan severity & priority
- **Quality Assessment** - Evaluasi kualitas software
- **Final Test Report** - Laporan lengkap untuk management
- **Recommendations** - Saran perbaikan untuk tim development
**Metrics yang Dilaporkan:**

| Metric | Penjelasan | Contoh |
|--------|------------|--------|
| **Test Coverage** | Persentase requirement yang sudah ditest | 95% (190 dari 200 requirements) |
| **Pass Rate** | Persentase test case yang passed | 85% (170 passed, 30 failed) |
| **Bug Count** | Total bug yang ditemukan | 45 bugs |
| **Bug Severity** | Klasifikasi tingkat keparahan bug | Critical: 5, High: 15, Medium: 20, Low: 5 |
| **Defect Density** | Jumlah bug per 1000 baris kode | 2.5 bugs/KLOC |

**Bug Severity & Priority:**

| Severity | Description | Example |
|----------|-------------|---------|
| **Critical** | Aplikasi crash, data loss, security breach | Payment gagal, database terhapus |
| **High** | Fitur utama tidak berfungsi | Login tidak bisa, checkout error |
| **Medium** | Fitur minor bermasalah, ada workaround | Filter search tidak akurat |
| **Low** | Cosmetic issues, typo | Warna tombol salah, typo di label |

**Output:**
- Test Summary Report
- Bug Status Report 
- Quality Metrics Dashboard
- Recommendations Document

---
* Mengidentifikasi uji kasus
* Memperkirakan waktu dan biaya
* Mengidentifikasi hasil tes dan capaiannya
* Menugaskan peran dan tanggung jawab
* Meninjau dan menyetujui rencana testing

### **2. Test Design**
Di sini, rencana diubah menjadi skenario pengujian yang dapat ditindaklanjuti.
* Mengidentifikasi *test case*
* Menulis *test case*
* Membuat data dan skenario pengujian
* Mengidentifikasi hasil yang diharapkan
* Meninjau dan memvalidasi hasil
* Memperbarui dokumen *Requirement Traceability Matrix*

### **3. Test Execution**
Fase di mana pengujian sebenarnya dilakukan. Penguji menjalankan *test case* yang telah dirancang, membandingkan hasil aktual dengan hasil yang diharapkan, dan mencatat setiap perbedaan sebagai *bug*. Ini bisa mencakup berbagai level seperti:
* **Komponen Testing:** Pengujian komponen-komponen program, biasanya dilakukan oleh *component developer*.
* **Integration Testing:** Pengujian terhadap keterhubungan antar sub-sistem atau kelompok komponen yang terintegrasi.
* **Sistem Testing:** Pengujian berdasarkan spesifikasi sistem, sering oleh tim penguji yang independen.
* **Acceptance Testing:** Pengujian terakhir sebelum sistem dipakai oleh user, seringkali melibatkan data dari pengguna sistem.

### **4. Pelaporan & Analisis Testing**
Setelah pengujian selesai, hasilnya dikumpulkan dan dianalisis.
* **Ringkasan hasil:** Menyajikan jumlah kasus uji yang berhasil, gagal, atau belum dijalankan.
* **Identifikasi bug:** Mencatat kesalahan yang ditemukan, termasuk tingkat keparahan dan status perbaikannya.
* **Evaluasi kualitas:** Menilai apakah sistem memenuhi spesifikasi fungsional dan non-fungsional.
* **Grafik dan data analitik:** Menampilkan tren pengujian, seperti peningkatan jumlah kasus uji yang berhasil atau penurunan jumlah bug.
* **Rekomendasi:** Memberikan saran untuk peningkatan performa, keamanan, atau stabilitas sistem.

---

## **Klasifikasi Strategi Testing**

Strategi testing dapat diklasifikasikan berdasarkan beberapa pendekatan berbeda untuk mencakup semua aspek perangkat lunak. Setiap klasifikasi memiliki fokus dan tujuan yang spesifik.

```
┌─────────────────────────────────────────────────────────┐
│          4 KLASIFIKASI UTAMA TESTING                    │
├─────────────────────────────────────────────────────────┤
│  1. Abstraction Level → Unit/Integration/System/UAT    │
│  2. Functionality → Functional vs Non-Functional       │
│  3. Domain Specific → Performance/Security/Usability   │
│  4. Structure → Black-Box vs White-Box                 │
└─────────────────────────────────────────────────────────┘
```

---

### **1. Berdasarkan Level Abstraksi (Testing Pyramid)**

Klasifikasi ini mengurutkan pengujian dari komponen terkecil hingga sistem secara keseluruhan, membentuk **Testing Pyramid**.

```
        ┌─────────────┐
       │     UAT      │  ← Paling sedikit test, paling lambat
      ├───────────────┤
     │ System Testing │
    ├─────────────────┤
   │ Integration Test │
  ├───────────────────┤
 │   Unit Testing    │  ← Paling banyak test, paling cepat
└────────────────────┘
```

#### **Unit Testing**

**Definisi:** Menguji komponen terkecil dari software secara terpisah (fungsi, method, class).

**Karakteristik:**
- **Paling cepat** dijalankan (milliseconds)
- **Scope terkecil** - fokus pada satu fungsi/method
- **Dilakukan oleh:** Developer
- **Frequency:** Setiap kali code berubah (automated)
- **Isolated:** Tidak bergantung pada database, API, file system

**Tools Populer:**
- Java: **JUnit**, TestNG
- JavaScript: **Jest**, Mocha, Jasmine
- Python: **pytest**, unittest
- C#: **NUnit**, xUnit

**Contoh Kasus:**

```javascript
// Fungsi yang akan ditest
function calculateDiscount(price, discountPercent) {
 if (price < 0 || discountPercent < 0) return 0;
 return price * (discountPercent / 100);
}

// Unit Test
test('calculateDiscount returns correct value', () => {
 expect(calculateDiscount(100, 10)).toBe(10);
 expect(calculateDiscount(200, 25)).toBe(50);
 expect(calculateDiscount(-100, 10)).toBe(0); // negative price
});
```

**Kapan Menggunakan:**
- Test business logic
- Test validasi input
- Test kalkulasi matematis
- Test transformasi data

---

#### **Integration Testing**

**Definisi:** Menguji interaksi dan komunikasi antara dua atau lebih modul/komponen.

**Karakteristik:**

- **Fokus:** Koneksi antar modul
- **Dilakukan oleh:** Developer atau QA
- **Mencakup:** API calls, database queries, external services
- **Lebih lambat** dari unit test tapi lebih cepat dari system test

**Pendekatan Integration Testing:**

| Approach | Deskripsi | Kelebihan | Kekurangan |
|----------|-----------|-----------|------------|
| **Big Bang** | Semua modul digabung sekaligus lalu ditest | Cepat untuk sistem kecil | Sulit debug jika error |
| **Top-Down** | Test dari modul atas ke bawah | Bisa detect masalah arsitektur awal | Butuh stub untuk modul bawah |
| **Bottom-Up** | Test dari modul bawah ke atas | Modul kritikal ditest duluan | Butuh driver untuk modul atas |
| **Sandwich** | Kombinasi top-down & bottom-up | Balanced approach | Lebih kompleks |

**Contoh Kasus:**

```python
# Integration Test: Login Flow
def test_login_integration():
 # Test: Frontend → Backend → Database → Session
 
 # 1. User submit login form
 response = client.post('/login', data={
 'email': 'test@example.com',
 'password': 'password123'
 })
 
 # 2. Check if database query works
 assert user_exists_in_db('test@example.com') == True
 
 # 3. Check if session created
 assert session.get('user_id') is not None
 
 # 4. Check redirect to dashboard
 assert response.status_code == 302
 assert response.location == '/dashboard'
```

**Kapan Menggunakan:**
- Test API integration
- Test database connections
- Test third-party services (payment gateway, email service)
- Test microservices communication

---

#### **System Testing**

**Definisi:** Menguji sistem perangkat lunak secara keseluruhan sebagai satu kesatuan yang terintegrasi (end-to-end).

**Karakteristik:**

- **Scope:** Seluruh sistem
- **Environment:** Mirip dengan production
- **Dilakukan oleh:** QA Team (independen)
- **Berdasarkan:** System Requirements Specification (SRS)

**Jenis System Testing:**

| Jenis | Tujuan | Contoh |
|-------|--------|--------|
| **Functional Testing** | Test semua fitur sesuai requirement | Test checkout flow lengkap |
| **Performance Testing** | Test kecepatan & stabilitas | Load test 1000 concurrent users |
| **Security Testing** | Test keamanan sistem | Penetration testing, vulnerability scan |
| **Usability Testing** | Test kemudahan penggunaan | User bisa checkout dalam 3 klik |
| **Compatibility Testing** | Test di berbagai platform | Chrome, Firefox, Safari, Mobile |

**Contoh Skenario E-commerce:**

```
Test Case: Complete Purchase Flow

 1. User browse produk 
 2. User add produk ke cart 
 3. User apply coupon code 
 4. User proceed to checkout 
 5. User isi shipping address 
 6. User pilih payment method 
 7. User confirm & pay 
 8. System send confirmation email 
 9. System update inventory 
 10. User receive order tracking number 

 Expected: Order successfully placed
```

**Kapan Menggunakan:**
- Sebelum UAT (User Acceptance Testing)
- Test business workflows lengkap
- Regression testing setelah major update

---

#### **Acceptance Testing (UAT)**

**Definisi:** Testing oleh user/client untuk validasi apakah sistem memenuhi kebutuhan bisnis sebelum go-live.

**Karakteristik:**

- **Dilakukan oleh:** End User, Client, Stakeholder
- **Tujuan:** Final approval sebelum production
- **Berdasarkan:** User Requirements, Business Scenarios
- **Fokus:** User experience & business value

**Jenis UAT:**

| Jenis | Deskripsi | Contoh |
|-------|-----------|--------|
| **Alpha Testing** | Testing oleh internal team sebelum rilis | Internal employees test aplikasi |
| **Beta Testing** | Testing oleh selected users sebelum public release | 100 users test aplikasi mobile baru |
| **Contract Acceptance** | Testing berdasarkan kontrak dengan client | Client verify semua fitur di kontrak ada |
| **Regulation Acceptance** | Testing compliance dengan regulasi | Banking app comply dengan BI regulations |

**Contoh UAT Scenario:**

```
Scenario: HR Manager merekrut karyawan baru

Given: HR Manager login ke sistem
When: HR Manager buat job posting baru
 And: Candidates submit applications
 And: HR Manager review & shortlist candidates
 And: HR Manager schedule interviews
 And: HR Manager offer job to selected candidate
Then: Candidate receive offer letter via email
 And: Sistem create employee profile
 And: Sistem notify IT untuk setup account

 Acceptance Criteria:
- Proses selesai dalam 5 langkah
- Email notifikasi terkirim otomatis
- Employee data masuk ke database
```

---

### **Berdasarkan Fungsi (What vs How)**

Klasifikasi ini membagi testing berdasarkan **apa yang dilakukan** sistem (functional) vs **bagaimana** sistem melakukannya (non-functional).

#### **Functional Testing**

**Definisi:** Menguji apakah software berfungsi sesuai dengan persyaratan fungsionalnya.
**Fokus:** **WHAT** the system does
- Apakah fitur bekerja sesuai requirement?
- Apakah output sesuai dengan input yang diberikan?
- Apakah user bisa menyelesaikan task?
**Karakteristik:**

- **Based on:** Functional Requirements Document
- **Focus:** Features & Functions
- **Approach:** Biasanya Black-Box Testing
- **Perspective:** User-centric
**Contoh Test Cases:**

| Feature | Test Case | Expected Result |
|---------|-----------|-----------------|
| **Login** | User login dengan kredensial valid | Redirect ke dashboard |
| **Search** | User search "laptop" | Show relevant products |
| **Add to Cart** | User add product to cart | Cart count +1, total price updated |
| **Payment** | User pay dengan credit card | Payment success, order created |
| **Forgot Password** | User request reset password | Email with reset link sent |

**Tools:**
- Selenium, Cypress (Web automation)
- Appium (Mobile automation)
- Postman (API testing)
- Katalon Studio

---

#### **Non-Functional Testing**

**Definisi:** Menguji **bagaimana** sistem bekerja, bukan apa yang dilakukan (performance, security, usability, reliability).

**Fokus:** **HOW** the system works
- Seberapa cepat sistemnya?
- Seberapa aman sistemnya?
- Seberapa mudah digunakan?
- Seberapa stabil sistemnya?

**Jenis-jenis Non-Functional Testing:**

```
Non-Functional Testing
 Performance Testing
 Load Testing
 Stress Testing
 Spike Testing
 Endurance Testing
 Security Testing
 Penetration Testing
 Vulnerability Scanning
 Security Auditing
 Usability Testing
 Compatibility Testing
 Reliability Testing
 Scalability Testing
```

---

### **3. Berdasarkan Domain (Specific Test Types)**

Ini adalah jenis pengujian non-fungsional yang lebih spesifik dan mendalam.

#### **Performance Testing**

**Definisi:** Menguji kinerja sistem dari segi kecepatan, responsivitas, dan stabilitas di bawah beban tertentu.

**4 Jenis Performance Testing:**

| Jenis | Tujuan | Skenario | Tools |
|-------|--------|----------|-------|
| **Load Testing** | Test sistem dengan beban normal | 1000 concurrent users | JMeter, LoadRunner |
| **Stress Testing** | Test batas maksimal sistem | Naikkan user sampai crash | Gatling, K6 |
| **Spike Testing** | Test lonjakan tiba-tiba | Flash sale, viral moment | JMeter |
| **Endurance Testing** | Test stabilitas jangka panjang | Run 24/7 selama seminggu | LoadRunner |

**Metrics yang Diukur:**
- **Response Time** - Berapa lama server respond? (Target: < 2 detik)
- **Throughput** - Berapa request per detik? (Target: 1000 req/s)
- **CPU Usage** - Berapa % CPU terpakai? (Target: < 70%)
- **Memory Usage** - Berapa RAM terpakai? (Target: < 80%)
- **Error Rate** - Berapa % request yang error? (Target: < 1%)

**Contoh Test Scenario:**

```
Load Test: Flash Sale 12.12

Setup:
- 5000 concurrent users
- Duration: 30 minutes
- Ramp-up: 1000 users every 5 minutes

Metrics:
   Response time < 3 seconds
  Error rate < 0.5%
  Server uptime 100%
  Database connection stable

Result:
  - Avg response time: 1.8s 
- Peak traffic: 10,000 req/min 
- 0 crashes 
-  Error rate: 0.2% 
```

---

#### **Security Testing**

**Definisi:** Mengidentifikasi celah keamanan dan melindungi data dari ancaman eksternal dan internal.

**Tujuan:**
- Protect data dari unauthorized access
- Prevent hacking & cyber attacks
- Ensure compliance (GDPR, ISO 27001)
- Protect user privacy
**OWASP Top 10 Security Risks:**

| Rank | Vulnerability | Contoh Attack | Prevention |
|------|---------------|---------------|------------|
| 1 |

**Broken Access Control** | User biasa akses admin panel | Implement proper authorization |
| 2 |

**Cryptographic Failures** | Password disimpan plain text | Use bcrypt, encryption |
| 3 |

**Injection** | SQL Injection, XSS | Input validation, parameterized queries |
| 4 |

**Insecure Design** | Tidak ada rate limiting | Security by design |
| 5 |

**Security Misconfiguration** | Default password masih aktif | Change default settings |

**Jenis Security Testing:**

```
Security Testing
 Vulnerability Scanning
 Tools: Nessus, OpenVAS
 Penetration Testing (Ethical Hacking)
 Tools: Metasploit, Burp Suite
 Security Auditing
 Review code, config, logs
 Risk Assessment
 Identify & prioritize threats
```
**Contoh Test Cases:**

| Test Case | Attack Type | Expected Result |
|-----------|-------------|-----------------|
| SQL Injection Test | Input: `' OR '1'='1` | Query rejected, error logged |
| XSS Attack Test | Input: `<script>alert('XSS')</script>` | Script sanitized, not executed |
| Brute Force Test | 100 failed login attempts | Account locked after 5 attempts |
| Session Hijacking | Steal session cookie | Session invalid after logout |

---

#### **Usability Testing**

**Definisi:** Mengevaluasi kemudahan penggunaan software dari perspektif end user.

**Fokus:**
- **Ease of Use** - Apakah user bisa gunakan tanpa training?
- **Learnability** - Seberapa cepat user bisa belajar?
- **Efficiency** - Apakah user bisa selesaikan task dengan cepat?
- **Memorability** - Apakah user ingat cara pakainya?
- **Satisfaction** - Apakah user puas dengan experience?

**Metode Usability Testing:**

| Metode | Deskripsi | Kapan Digunakan |
|--------|-----------|-----------------|
| **Hallway Testing** | Minta random orang coba app | Quick feedback, early stage |
| **A/B Testing** | Compare 2 versi design | Optimize conversion rate |
| **Eye Tracking** | Track kemana user lihat | Optimize UI layout |
| **Think Aloud** | User explain apa yang mereka pikir | Understand user mental model |
| **Survey** | User isi questionnaire | Large scale feedback |

**5 Second Test:**
```
Show landing page selama 5 detik
> Close page
 > Ask: Apa yang kamu ingat?
 > Good UX: User ingat key message
```
**Task Success Metrics:**

| Metric | Formula | Good Score |
|--------|---------|------------|
| **Task Success Rate** | (Completed tasks / Total tasks) × 100% | > 80% |
| **Time on Task** | Average time to complete task | < Target time |
| **Error Rate** | (Errors / Total attempts) × 100% | < 5% |
| **Satisfaction Score** | Average rating (1-5 scale) | > 4.0 |

---

### **Berdasarkan Struktur (The "Box" Approach)**

Klasifikasi berdasarkan tingkat pengetahuan tester tentang internal sistem.

```

 Black Box Gray Box White Box 
 
 No Code Partial Full Code 
 Knowledge Knowledge Knowledge 
 
 QA Tester QA + Dev Developer 

```

#### **Black-Box Testing**

**Definisi:** Tester **TIDAK tahu** struktur internal atau kode program. Fokus pada input-output.

**Karakteristik:**

- **Perspective:** External (User perspective)
- **Focus:** Functionality, not implementation
- **Who:** QA Tester (tidak perlu coding skill)
- **Based on:** Requirements & Specifications
**Teknik Black-Box Testing:**

| Teknik | Deskripsi | Contoh |
|--------|-----------|--------|
| **Equivalence Partitioning** | Bagi input ke dalam grup valid/invalid | Age: <0 (invalid), 0-120 (valid), >120 (invalid) |
| **Boundary Value Analysis** | Test nilai batas | Test dengan age: -1, 0, 1, 119, 120, 121 |
| **Decision Table** | Test kombinasi kondisi | Login: emailpassword → success |
| **State Transition** | Test perubahan state | Order: pending → paid → shipped → delivered |
| **Error Guessing** | Guess kemungkinan error | User mungkin input emoji di email field |

**Kelebihan:**
- Tidak butuh knowledge tentang code
- Test dari user perspective (realistic)
- Bisa dilakukan oleh non-developer
- Cocok untuk large-scale functional testing
**Kekurangan:**
- Tidak guarantee 100% code coverage
- Sulit detect hidden bugs di logic
- Test cases mungkin incomplete
**Contoh:**

```
Black-Box Test: Login Form

Input: email, password
Output: Success/Error message

Test Cases:

 Email Password Expected 

 valid@test.com valid123 Login OK 
 invalid valid123 Email error
 valid@test.com wrong Pass error 
 (empty) valid123 Required 
 test@test.com (empty) Required 

 Tester TIDAK perlu tahu bagaimana sistem validasi bekerja
```

---

#### **White-Box Testing**

**Definisi:** Tester **TAHU** struktur internal, kode, algoritma, dan logic program.

**Karakteristik:**

- **Perspective:** Internal (Developer perspective)
- **Focus:** Code quality, logic flow, coverage
- **Who:** Developer atau QA dengan coding skill
- **Based on:** Source code & architecture
**Teknik White-Box Testing:**

| Teknik | Deskripsi | Contoh |
|--------|-----------|--------|
| **Statement Coverage** | Setiap statement di-execute minimal 1x | Test semua lines of code |
| **Branch Coverage** | Setiap branch (if/else) di-test | Test both true & false conditions |
| **Path Coverage** | Setiap possible path di-test | Test all combinations |
| **Condition Coverage** | Setiap kondisi di-test | if (A && B) → test all combinations |
| **Loop Testing** | Test loop dengan berbagai iterasi | Loop 0x, 1x, 2x, max, max+1 |

**Code Coverage Metrics:**

```
Function calculateGrade(score) {
 if (score >= 90) { ← Branch 1
 return "A";
 } else if (score >= 80) { ← Branch 2
 return "B";
 } else if (score >= 70) { ← Branch 3
 return "C";
 } else { ← Branch 4
 return "F";
 }
}

Test Cases for 100% Branch Coverage:
 calculateGrade(95) → "A" (Branch 1)
 calculateGrade(85) → "B" (Branch 2)
 calculateGrade(75) → "C" (Branch 3)
 calculateGrade(60) → "F" (Branch 4)
```
**Kelebihan:**
- High code coverage
- Detect hidden bugs di logic
- Optimize & improve code quality
- Find security vulnerabilities
**Kekurangan:**
- Butuh deep programming knowledge
- Time-consuming untuk complex systems
- Tidak test user experience
- Expensive (butuh skilled developers)
**Tools:**
- **Coverage Tools:** JaCoCo (Java), Coverage.py (Python), Istanbul (JavaScript)
- **Static Analysis:** SonarQube, ESLint, Pylint
- **Code Review:** CodeClimate, Codacy

---

#### **Gray-Box Testing** (Bonus)

**Definisi:** Kombinasi Black-Box dan White-Box. Tester punya **partial knowledge** tentang internal system.

**Karakteristik:**

- **Mix of:** External + Internal view
- **Knowledge:** Database schema, API docs, architecture
- **Who:** QA dengan technical background
- **Use case:** Integration testing, database testing
**Contoh:**
```
Test: User Registration

Black-Box Part:
- Fill registration form
- Click submit
- Check success message

Gray-Box Part (dengan akses database):
- Verify data masuk ke DB 
- Check password encrypted (not plain text) 
- Check email verification token generated 

White-Box Part (tidak dilakukan):
- Tidak perlu review encryption algorithm code
```

---

---

## **Kesimpulan**

Software testing adalah **fondasi kualitas** dalam pengembangan perangkat lunak modern. Ini bukan hanya tentang menemukan bug, tetapi tentang:
- **Membangun kepercayaan** stakeholder dan user
- **Menghemat biaya** dengan mencegah bug di production
- **Meningkatkan user experience** dan kepuasan pelanggan
- **Menjamin keamanan** dan melindungi data
- **Memastikan kualitas** produk yang reliable

### **Key Takeaways**

| Aspek | Poin Penting |
|-------|--------------|
| **STLC** | Testing punya siklus terstruktur: Planning → Design → Execution → Reporting |
| **Test Pyramid** | Banyak unit test, sedikit UI test (cepat & efisien) |
| **Klasifikasi** | 4 dimensi: Level, Fungsi, Domain, Struktur |
| **Balance** | Combine Black-Box (user view) & White-Box (code view) |
| **Continuous** | Testing bukan fase terakhir, tapi ongoing process |

### **Best Practices**

```
 Golden Rules of Testing

1. Start testing EARLY (shift-left)
2. Automate REPETITIVE tests
3. Write CLEAR test cases
4. Test with REAL data scenarios
5. Document EVERYTHING
6. Regression test setelah EVERY change
7. Collaborate dengan DEVELOPERS
8. Keep learning & UPDATE skills
```

### **Next Steps untuk Belajar Testing**

| Level | Learning Path | Resources |
|-------|---------------|-----------|
| **Beginner** | Manual testing basics, test case writing | ISTQB Foundation |
| **Intermediate** | Automation tools (Selenium, Cypress) | Udemy courses |
| **Advanced** | Performance testing, Security testing | JMeter, OWASP |
| **Expert** | Test strategy, DevOps integration | CI/CD, Jenkins |

> Remember: 
> "Testing shows the presence, not the absence of bugs." - Edsger Dijkstra
> 
> Tapi dengan strategi testing yang tepat, kita bisa **minimize risk** dan **maximize quality**! 

---

## **Referensi & Resources**

### **Sumber Materi**
Materi ini dirangkum dari presentasi “Strategi Testing” oleh Kelompok 1 - Sistem Informasi 2023. Presentasi (PPT) lengkap dari materi ini dapat dilihat melalui tautan berikut:
**[Lihat Presentasi (PPT)](https://drive.google.com/file/d/1bNFmdW8ePz_z0VM0660SZU4meSBaxc9c/view?usp=drive_link)**

### **Rekomendasi Belajar Lebih Lanjut**

#### **Books**
- *"Software Testing Fundamentals"* - Rex Black
- *"The Art of Software Testing"* - Glenford Myers
- *"Agile Testing"* - Lisa Crispin & Janet Gregory

#### **Online Resources**
- [ISTQB Certification](https://www.istqb.org/) - International standard for testing
- [Test Automation University](https://testautomationu.applitools.com/) - Free courses
- [Ministry of Testing](https://www.ministryoftesting.com/) - Testing community

#### **Tools untuk Dicoba**
- **Manual Testing:** TestRail, Zephyr, qTest
- **Automation:** Selenium, Cypress, Playwright
- **Performance:** JMeter, Gatling, K6
- **Security:** OWASP ZAP, Burp Suite
- **API Testing:** Postman, SoapUI, REST Assured

#### **Practice Platforms**
- [The Internet](https://the-internet.herokuapp.com/) - Practice web automation
- [Restful Booker](https://restful-booker.herokuapp.com/) - Practice API testing
- [OWASP Juice Shop](https://owasp.org/www-project-juice-shop/) - Practice security testing

---

## **FAQ (Frequently Asked Questions)**

<details>
<summary><strong>Q: Kapan waktu terbaik untuk mulai testing?</strong></summary>
<br>
<b>A:</b> Seawal mungkin! Di fase <b>Requirements & Design</b> sudah bisa:
<ul>
 <li>Review requirements untuk ambiguity</li>
 <li>Membuat test strategy</li>
 <li>Menulis test cases</li>
</ul>
Konsep "Shift-Left Testing" menekankan testing dimulai sejak awal SDLC.
</details>

<details>
<summary><strong>Q: Berapa persentase test coverage yang ideal?</strong></summary>
<br>
<b>A:</b> Tidak ada angka magic, tapi guideline umum:
<ul>
 <li><b>Unit Test:</b> 70-80% code coverage</li>
 <li><b>Integration Test:</b> Cover semua critical paths</li>
 <li><b>E2E Test:</b> Cover main user journeys</li>
</ul>
<b>Quality > Quantity.</b> Lebih baik 50% coverage dengan test berkualitas daripada 100% coverage dengan test yang buruk.
</details>

<details>
<summary><strong>Q: Manual testing vs Automation testing, mana lebih baik?</strong></summary>
<br>
<b>A:</b> Keduanya penting! Gunakan sesuai kebutuhan:

<table>
<tr>
<th>Manual Testing</th>
<th>Automation Testing</th>
</tr>
<tr>
<td> Exploratory testing<br> Usability testing<br> Ad-hoc testing<br> One-time tests</td>
<td> Regression testing<br> Load testing<br> Repetitive tests<br> CI/CD integration</td>
</tr>
</table>

<b>Best approach:</b> Kombinasi keduanya (Hybrid Testing)
</details>

<details>
<summary><strong>Q: Apa skill yang dibutuhkan untuk jadi QA/Tester?</strong></summary>
<br>
<b>A:</b> 
<br><br>
<b>Technical Skills:</b>
<ul>
 <li>Test case writing</li>
 <li>Bug reporting</li>
 <li>Basic programming (untuk automation)</li>
 <li>SQL (untuk database testing)</li>
 <li>Tools: Jira, Selenium, Postman</li>
</ul>

<b>Soft Skills:</b>
<ul>
 <li>Attention to detail</li>
 <li>Analytical thinking</li>
 <li>Communication</li>
 <li>Critical thinking</li>
 <li>Patience & persistence</li>
</ul>
</details>

<details>
<summary><strong>Q: Bagaimana prioritas testing jika waktu terbatas?</strong></summary>
<br>
<b>A:</b> Gunakan <b>Risk-Based Testing</b>:
<ol>
 <li><b>High Priority:</b> Core functionality (login, payment, checkout)</li>
 <li><b>Medium Priority:</b> Secondary features (search, filters)</li>
 <li><b>Low Priority:</b> Nice-to-have features (animations, tooltips)</li>
</ol>

<b>Focus on:</b> Features yang paling sering digunakan user + features yang paling critical untuk bisnis
</details>

---

*"Quality is not an act, it is a habit." - Aristotle*