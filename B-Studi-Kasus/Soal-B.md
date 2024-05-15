## 1. Jika diminta untuk melakukan mengirim dan meneriman file ke suatu server, protokol apa yang digunakan? Jelaskan tahapan yang diperlukan untuk mengirim dan menerima file dengan protokol tersebut
### A. SFTP (Secure File Transfer Protocol)
SFTP adalah versi aman dari FTP yang menggunakan Secure Shell (SSH) untuk enkripsi data, sehingga lebih aman dibandingkan FTP. SFTP cocok untuk melakukan transfer file kepada server dalam ukuran yang besar

#### Tahapan Mengirim dan Menerima File dengan SFTP:
1. **Koneksi ke Server SFTP**: Gunakan klien SFTP (seperti FileZilla, WinSCP, atau perintah `sftp` di terminal) untuk menghubungkan ke server SFTP. Anda memerlukan alamat server, username, dan password atau kunci SSH.
    ```bash
    sftp your_username@ftp.example.com
    ```
2. **Login**: Jika menggunakan kunci SSH, autentikasi akan dilakukan dengan kunci tersebut. Jika menggunakan password, masukkan password Anda.
    ```bash
    Password: your_password
    ```
3. **Navigasi Direktori**: Gunakan perintah `cd` untuk berpindah ke direktori tujuan di server.
    ```bash
    cd /path/to/remote/directory
    ```
4. **Mengirim File (Upload)**: Gunakan perintah `put` untuk mengirim file dari lokal ke server.
    ```bash
    put localfile.txt remotefile.txt
    ```
5. **Menerima File (Download)**: Gunakan perintah `get` untuk menerima file dari server ke lokal.
    ```bash
    get remotefile.txt localfile.txt
    ```
6. **Menutup Koneksi**: Gunakan perintah `exit` untuk menutup koneksi SFTP.
    ```bash
    exit
    ```

#### Contoh Menggunakan SFTP di Terminal
Misalkan akan mengirim file `example.txt` ke server dengan alamat `sftp.example.com`, lalu disimpan ke direktori `/uploads` di server:


```bash
sftp your_username@sftp.example.com
# Setelah login
cd /uploads
put example.txt
exit
```


### B. HTTP/HTTPS (HyperText Transfer Protocol/Secure)
HTTP adalah protokol yang digunakan untuk mentransfer data di web, sedangkan HTTPS adalah versi aman dari HTTP yang menggunakan enkripsi SSL/TLS. HTTP/HTTPS cocok untuk transfer file yang diintegrasikan dengan aplikasi web dan RESTful API.

#### Tahapan Mengirim dan Menerima File dengan HTTP/HTTPS:
1. **Menggunakan HTTP Form Upload**
    Form upload sering digunakan dalam aplikasi web untuk mengunggah file ke server.

    ##### Tahapan Mengirim File dengan HTTP Form Upload:
    1. **Membuat Form HTML**: Buat form HTML dengan metode POST dan atribut `enctype="multipart/form-data"`.
        ```html
        <form action="https://example.com/upload" method="post" enctype="multipart/form-data">
            <input type="file" name="file" />
            <input type="submit" value="Upload File" />
        </form>
        ```
    2. **Mengirim File**: Pengguna memilih file dan mengklik tombol "Upload File" untuk mengirim file ke server.
    3. **Server Menerima File**: Server menerima file melalui endpoint yang ditentukan (`https://example.com/upload`) dan menyimpannya di lokasi yang diinginkan.

2. **Menggunakan HTTP/HTTPS dengan RESTful API**
    RESTful API memungkinkan transfer file menggunakan endpoint yang dapat diakses dengan HTTP/HTTPS.

    ##### Tahapan Mengirim File dengan RESTful API:
    1. **Endpoint API**: Server menyediakan endpoint untuk menerima file, misalnya `https://example.com/api/upload`.
    2. **Mengirim File**: Gunakan klien HTTP seperti `curl`, `Postman`, atau library HTTP di bahasa pemrograman tertentu untuk mengirim file ke endpoint.

        Contoh menggunakan `curl`:
        ```bash
        curl -X POST https://example.com/api/upload \
        -H "Content-Type: multipart/form-data" \
        -F "file=@/path/to/localfile.txt"
        ```

    3. **Server Menerima File**: Server memproses file yang diterima dan menyimpannya di lokasi yang sesuai.

3. **Menggunakan HTTP/HTTPS untuk Mengunduh File**
    HTTP/HTTPS juga digunakan untuk mengunduh file dari server.

    ##### Tahapan Menerima File dengan HTTP/HTTPS:
    1. **Endpoint API**: Server menyediakan endpoint untuk mengunduh file, misalnya `https://example.com/api/download/file.txt`.
    2. **Mengunduh File**: Gunakan klien HTTP untuk mengakses URL dan mengunduh file.

        Contoh menggunakan `curl`:
        ```bash
        curl -O https://example.com/api/download/file.txt
        ```


## 2. Jelaskan tahapan yang diperlukan untuk menulis hasil perintah ping ke sebuah file text!
Menggunakan CMD untuk Ping dan Trace Route

#### 1. Buat Folder untuk Menyimpan Hasil
Buat folder baru untuk menyimpan hasil ping dan trace route.

1. **Buat Folder**: 
    - Buka File Explorer.
    - Navigasi ke lokasi di mana Anda ingin membuat folder.
    - Klik kanan dan pilih `New > Folder`.
    - Beri nama folder, misalnya `PingResults`.

#### 2. Buka CMD dan Arahkan ke Folder Tersebut
1. **Buka CMD**: 
    - Tekan `Windows + R` untuk membuka dialog Run.
    - Ketik `cmd` dan tekan `Enter`.

2. **Arahkan ke Folder**:
    - Gunakan perintah `cd` untuk berpindah ke folder yang telah Anda buat.
    ```bash
    cd path\to\PingResults
    ```

#### 3. Melakukan Ping dan Trace Route
##### A. Normal Ping
1. **Ping ke IP Address**:
    - Gunakan perintah berikut untuk melakukan ping dan menyimpan hasilnya ke file `pingresults.txt`.
    ```bash
    ping [IP Address] > pingresults.txt
    ```

##### B. Continuous Ping
1. **Ping ke localhost secara terus-menerus**:
    - Gunakan perintah berikut untuk melakukan ping secara terus-menerus dan menyimpan hasilnya ke file `pingresults.txt`.
    ```bash
    ping localhost -t > pingresults.txt
    ```
2. **Menghentikan Ping**:
    - Tekan `Control + C` untuk menghentikan proses ping.

##### C. Trace Route
1. **Trace Route ke IP Address**:
    - Gunakan perintah berikut untuk melakukan trace route dan menyimpan hasilnya ke file `tracert.txt`.
    ```bash
    tracert [IP Address] > tracert.txt
    ```

