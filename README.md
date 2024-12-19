# ✨ Menyiapkan Server FTP dengan ProFTPD ✨

Nama kelompok :
Alfi Mifta Nurhakim  - 233040013
Aufa Ramadhan        - 233040028
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

## 📝 Ringkasan
Dengan mengikuti langkah-langkah ini, Anda telah menyiapkan dan mengonfigurasi server FTP menggunakan ProFTPD. Anda sekarang dapat mengakses server FTP menggunakan klien FTP, seperti FileZilla, dengan menghubungkan ke alamat IP server dan port 21. Pastikan Anda menguji konfigurasi dan mengamankan server sesuai kebutuhan untuk penggunaan produksi.
