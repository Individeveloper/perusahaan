# 🧾 SEMKEU Dashboard — Panel Navigation System
**(Sistem Manajemen Keuangan)**

## 🧩 Konsep Aplikasi
Proyek ini menerapkan konsep **One Single Page** di mana `panelForm` berfungsi sebagai wadah utama yang menampung **sidebar** dan **content panel** yang dinamis.

## ⚙️ Fitur Utama

### Dynamic Panel Switching
- `panelForm` menampung area konten (`contentPanel`).
- Konten diganti secara dinamis menggunakan method `showPanel()`.
- Setiap panel seperti `dashboardPanel` dan `infoPanel` merupakan `JPanel` terpisah.

### Active State Button
- Sidebar memiliki highlight aktif berdasarkan panel yang sedang ditampilkan.
- Warna aktif diatur melalui fungsi `setActivePanel()`.

### Hover Effect
- Efek hover untuk tiap tombol di sidebar agar interaktif.

### Swing Thread Safe Initialization
- Menggunakan `SwingUtilities.invokeLater()` untuk memastikan `showPanel()` dijalankan aman di **Event Dispatch Thread (EDT)**.

## 📄 Struktur File
src/
└── semkeuproject/
├── panelForm.java → Form utama (sidebar + content area)
├── dashboardPanel.java → Panel untuk tampilan dashboard
├── infoPanel.java → Panel untuk tampilan informasi/chart
└── assets/ → Folder ikon, gambar, dll

markdown
Copy code

## 🧠 Konsep Kerja
- Saat aplikasi dijalankan, `panelForm` otomatis memanggil:

```java
showPanel(dashboardPanel);
Sehingga tampilan default adalah halaman Dashboard.

Saat pengguna klik tombol lain di sidebar, konten diganti dengan:

java
Copy code
contentPanel.removeAll();
contentPanel.add(panel);
contentPanel.repaint();
contentPanel.revalidate();
⚠️ Catatan Penting
JANGAN mengubah ukuran (setSize) dan layout utama (AbsoluteLayout) pada file panelForm!
Hal ini bisa menyebabkan tampilan antar panel menjadi tidak sejajar atau rusak posisinya.

Jika ingin menambahkan panel baru, ikuti ukuran default:

Width: 660px

Height: 610px

Gunakan layout yang sama agar konsisten di semua tampilan.
