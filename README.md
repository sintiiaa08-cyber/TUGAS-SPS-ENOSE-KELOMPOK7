# 💻 Sistem Pengolah Sinyal (SPS) - Proyek E-Nose Cerdas

Proyek ini adalah implementasi sistem **Electronic Nose (E-Nose)** yang dikembangkan untuk tugas mata kuliah Sistem Pengolah Sinyal.

Sistem ini menyediakan solusi *end-to-end* yang menangani:
1.  **Akuisisi Data:** Pengambilan data sensor gas secara *real-time* dari perangkat Arduino.
2.  **Visualisasi:** Tampilan grafik data yang responsif melalui antarmuka GUI.
3.  **Penyimpanan:** Data *time-series* yang terstruktur dan siap untuk diolah lebih lanjut (misalnya, untuk *Machine Learning*).

### 👩‍💻 Dibuat Oleh:
* **Sintia Ompusunggu** (2042241113)
* **galen zahid wajendra** (2042241044)
* **Rijal Difaul Haq** (2042241097)

---

## 🏗️ Struktur Arsitektur Sistem

Sistem ini didesain secara modular, terbagi menjadi empat lapisan utama yang bekerja paralel:

1.  **Perangkat Keras (Embedded - Arduino):**
    * Berfungsi sebagai akuisitor sinyal. Bertanggung jawab membaca data dari sensor dan mengontrol aktuator (misalnya motor), lalu mengirimkan data ke *Backend* melalui TCP/IP.
2.  **Layanan Data (Backend - Rust):**
    * Bertindak sebagai penghubung (TCP Server). Mengelola komunikasi dengan perangkat Arduino, memproses data mentah, dan menyimpan data *time-series* ke *Database*.
3.  **Gudang Data (Database - InfluxDB):**
    * Basis data khusus untuk data yang bergantung pada waktu (*Time-Series*). Menyimpan semua pembacaan sensor secara permanen.
4.  **Antarmuka Pengguna (Frontend - Python/Qt):**
    * Aplikasi *desktop* GUI. Menyediakan *dashboard* visualisasi, kontrol sistem (seperti kalibrasi), dan *real-time monitoring*.

---

## ⚙️ Pra-Syarat Instalasi

Pastikan semua *tools* berikut sudah terinstal di komputer Anda:

* ✅ **Docker Desktop:** Untuk menjalankan *Database* (`InfluxDB`).
* ✅ **Rust Toolchain:** Diperlukan untuk kompilasi dan menjalankan *Backend*.
* ✅ **Python 3.8+:** Untuk menjalankan *Frontend* dan mengelola *virtual environment*.
* ✅ **Arduino IDE:** Untuk meng-*upload* *firmware* ke *board* E-Nose.

---

## 🚀 Setup & Instalasi (Hanya Dilakukan Sekali)

### 1. Inisialisasi Database (Via Docker)

Buka Terminal di *root folder* proyek dan jalankan:

```bash
docker-compose up -d
