# ✨ Menyiapkan Server FTP dengan ProFTPD ✨

### Anggota : 
Alfi Mifta Nurhakim  - 233040013 \
Aufa Ramadhan        - 233040028 \
I Made Surya Kartika - 233040034 

Panduan ini memberikan langkah-langkah untuk menyiapkan server FTP menggunakan ProFTPD di sistem Linux.

## 📋 Langkah-Langkah

### 1. 🔄 Perbarui dan Tingkatkan Sistem
Untuk memastikan sistem Anda mutakhir dengan paket dan pembaruan keamanan terbaru, jalankan perintah berikut:
```bash
sudo apt-get update && sudo apt-get upgrade -y
```


### 2. ⚙ Instal Server FTP ProFTPD
ProFTPD adalah server FTP yang populer dan dapat dikonfigurasi dengan baik. Instal dengan perintah berikut:
```bash
sudo apt install proftpd
```

### 3. ▶ Mulai Layanan ProFTPD
Setelah diinstal, mulai layanan ProFTPD:
```bash
sudo systemctl start proftpd
```

### 4. ✅ Periksa Status ProFTPD
Periksa status layanan ProFTPD untuk memastikan layanan berjalan:
```bash
sudo systemctl status proftpd
```

### 5. 🛠 Konfigurasi ProFTPD
Edit file konfigurasi ProFTPD untuk menyesuaikan pengaturan sesuai kebutuhan:
```bash
sudo nano /etc/proftpd/proftpd.conf
```
Lalu aktifkan command berikut:
```bash
ServerName "namaserver"
ServerType standalone
Port 21
PassivePorts 10000 31000
```

Setelah melakukan perubahan, simpan file dan mulai ulang layanan ProFTPD untuk menerapkan konfigurasi baru:
```bash
sudo systemctl restart proftpd
```

### 6. 🌐 Temukan Alamat IP Server
Untuk menghubungkan ke server FTP, Anda perlu mengetahui alamat IP-nya. Instal net-tools jika belum terinstal:
```bash
sudo apt install net-tools
```

Kemudian, gunakan perintah ifconfig untuk menemukan alamat IP server:
```bash
ifconfig
```

### 7. 🔒 Konfigurasi Firewall
Untuk memastikan komunikasi dengan server FTP berjalan lancar, konfigurasikan firewall sebagai berikut:

1. Aktifkan firewall:
   ```bash
   sudo ufw enable
   ```

2. Izinkan koneksi FTP pada port 21:
   ```bash
   sudo ufw allow 21/tcp
   ```

3. Izinkan rentang port pasif FTP (10000-31000):
   ```bash
   sudo ufw allow 10000:31000/tcp
   ```

4. Periksa status firewall untuk memverifikasi perubahan:
   ```bash
   sudo ufw status verbose
   ```
##
# ✨ Tutorial Menggunakan FileZilla ✨

FileZilla adalah klien FTP yang populer untuk mengakses dan mengelola file di server FTP. Tutorial ini akan memandu Anda langkah demi langkah untuk menggunakannya.

## Langkah-langkah

### 1. 🔧 Unduh dan Instal FileZilla

- **Untuk Windows/Mac**: 
  Kunjungi [filezilla-project.org](https://filezilla-project.org) dan unduh versi terbaru.

- **Untuk Linux**: 
  Instal FileZilla melalui package manager:
  ```bash
  sudo apt install filezilla
  ```

### 2. 🔑 Sambungkan ke Server FTP

1. Buka FileZilla.
2. Masukkan informasi berikut:
   - **Host**: Masukkan alamat IP server Anda.
   - **Username**: Masukkan username pengguna FTP.
   - **Password**: Masukkan password pengguna FTP.
   - **Port**: Masukkan "21" (default FTP).
3. Klik tombol **Quickconnect** untuk memulai koneksi.

### 3. 🎯 Transfer File

- **Navigasi**: Gunakan panel kiri untuk menjelajahi file lokal Anda dan panel kanan untuk file di server.
- **Upload File**: Seret file dari panel kiri (lokal) ke panel kanan (server).
- **Download File**: Seret file dari panel kanan (server) ke panel kiri (lokal).

### 4. ⚖ Troubleshooting

Jika gagal terhubung:

- Periksa kembali informasi koneksi (alamat IP, username, password, dan port).
- Pastikan firewall tidak memblokir koneksi FTP.
- Verifikasi layanan ProFTPD aktif dengan perintah berikut:
  ```bash
  sudo systemctl status proftpd
  ```

## 📝 Kesimpulan ProFTPD & FileZilla
Dengan mengikuti langkah-langkah ini, Anda telah menyiapkan dan mengonfigurasi server FTP menggunakan ProFTPD. Anda sekarang dapat mengakses server FTP menggunakan klien FTP, seperti FileZilla, dengan menghubungkan ke alamat IP server dan port 21. Pastikan Anda menguji konfigurasi dan mengamankan server sesuai kebutuhan untuk penggunaan produksi.

