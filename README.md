# Jarkom-Modul-1-E10-2021

### Kelompok E10

| **No** | **Nama** | **NRP** | 
| ------------- | ------------- | --------- |
| 1 | Muhammad Rizqi Tsani  | 05111940000045 | 
| 2 | Dicksen Alfersius Novian | 05111940000076 |
| 3 | Bill Harit Yafi | 05111940000114 |

## Soal 1

### Soal
Sebutkan webserver yang digunakan pada "ichimarumaru.tech"!

### Jawaban

Menggunakan display filter `tcp contains ichimarumaru`

![image25](https://user-images.githubusercontent.com/68275535/134756559-1cb4cd70-4fb7-4170-80da-1c10f8ded871.png)

Selanjutnya follow tcp stream dari salah satu package untuk mendapat informasi tentang webserver yang digunakan yaitu nginx/1.18.0 (Ubuntu)

![image24](https://user-images.githubusercontent.com/68275535/134756581-2338f579-5469-46d4-84b5-d9875c67c39c.png)

## Soal 2

### Soal
Temukan paket dari web-web yang menggunakan basic authentication method!

### Jawaban

Menggunakan display filter `http.authbasic`

![image4](https://user-images.githubusercontent.com/68275535/134756629-e8e61c3b-22aa-43a6-b96b-eaa799f7b3c2.png)

## Soal 3

### Soal
Ikuti perintah di [basic.ichimarumaru.tech](http://basic.ichimarumaru.tech/)! Username dan password bisa didapatkan dari file .pcapng!

### Jawaban

Pertama, menggunakan display filter `http.authbasic` dan melihat Authorization header dari salah satu package

![image1](https://user-images.githubusercontent.com/68275535/134756706-15ae26db-6793-42fa-9b1c-f9c852efb7dc.png)

Dari header tersebut diperoleh username dan password
kuncimenujulautan:tQKEJFbgNGC1NCZlWAOjhyCOm6o3xEbPkJhTciZN

Setelah login, menjawab pertanyaan konfigurasi pengkabelan T568A

![image21](https://user-images.githubusercontent.com/68275535/134756842-0a0b53fc-2c1d-4953-bb87-2fa61325bfa7.png)

## Soal 4

### Soal
Temukan paket mysql yang mengandung perintah query select!

### Jawaban

Menggunakan display filter `mysql.query contains select || mysql.query contains SELECT`

![image3](https://user-images.githubusercontent.com/68275535/134756888-1f73c731-2da1-496d-abb5-4d690f98bbe6.png)

## Soal 5

### Soal
Login ke [portal.ichimarumaru.tech](http://portal.ichimarumaru.tech/) kemudian ikuti perintahnya! Username dan password bisa didapat dari query insert pada table users dari file .pcap!

### Jawaban

Menggunakan display filter `mysql.query contains insert || mysql.query contains INSERT`

![image](https://user-images.githubusercontent.com/68275535/134756928-05e16ac9-db05-4272-8e04-c9e9eadb3279.png)

Dari query didapatkan username password
akakanomi:pemisah4lautan

Setelah login, menjawab pertanyaan konfigurasi pengkabelan T568B

![image22](https://user-images.githubusercontent.com/68275535/134756971-95c36765-8237-43e6-829b-092d1c6dc402.png)

## Soal 6

### Soal
Cari username dan password ketika melakukan login ke FTP Server!

### Jawaban
Menggunakan filter ftp.request lalu melihat request USER dan PASS yang respondnya logged on
![image](https://user-images.githubusercontent.com/77628684/134760796-82af7163-5861-4b49-a108-eaca82f5b2d0.png)

## Soal 7

### Soal
Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ...,
499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")

### Jawaban
Menggunakan display filter “frame contains “Real.pdf” “
![image](https://user-images.githubusercontent.com/77628684/134760809-a0dc2b5f-a284-4f88-93a7-3f74655e5623.png)
Lalu ikuti tcp stream dari paket dan simpan dalam bentuk RAW kedalam file “real.pdf”
![image](https://user-images.githubusercontent.com/77628684/134760812-c26adc3e-e9f7-4a7e-9820-53cca37b04ce.png)
![image](https://user-images.githubusercontent.com/77628684/134760814-e12c1b14-ec73-4548-8674-7955f3148bef.png)

## Soal 8

### Soal
Cari paket yang menunjukan pengambilan file dari FTP tersebut!

### Jawaban
Tidak ditemukan paket menggunakan filter ftp.request.command == RETR

## Soal 9

### Soal
Dari paket-paket yang menuju FTP terdapat indikasi penyimpanan beberapa file. Salah
satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka
file tersebut!

### Jawaban
Ketik di display ftp-data.command contains secret.zip
![image](https://user-images.githubusercontent.com/77628684/134760834-3914ed84-62ec-41b9-8b1b-90765613671d.png)
Klik kanan yang memiliki info STOR secret.zip lalu pencet follow tcp streams
![image](https://user-images.githubusercontent.com/77628684/134760837-536e66a8-bf45-4e6f-8ca3-810d49866323.png)

Ganti data dari ASCII menjadi raw lalu save as secret.zip. Isi dari zip tersebut adalah file
wanted.pdf passwordnya didapat dari nomor 10
![image](https://user-images.githubusercontent.com/77628684/134760841-a879228e-ad8a-4010-a8b1-ea3dd63a6a08.png)

## Soal 10

### Soal
Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut!
Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia
yang ada di "secret.zip"!

### Jawaban
Ketik ftp-data contains history.txt
![image](https://user-images.githubusercontent.com/77628684/134760853-71d967a1-4957-4569-8eec-e1e84d0fa877.png)
Klik kanan follow stream pada stor history.txt
![image](https://user-images.githubusercontent.com/77628684/134760860-aa5393b8-05de-400b-b94f-93bdb1059a5f.png)
Password secret.zip ada pada $key yang valuenya =”$(tail -1 bukanapaapa.txt)” disini
kita cari bukanapaapa.txt dengan display filter ftp-data.command contains
bukanapaapa.txt
![image](https://user-images.githubusercontent.com/77628684/134760884-85dc39d7-fb45-4dc6-8d17-2b0a439d95fb.png)
lalu akan dapat STOR bukanapaapa.txt klik kanan follow tcp stream
![image](https://user-images.githubusercontent.com/77628684/134760896-69b25895-92b3-4ec9-9fd0-4d10cd80f5a5.png)
tail -1 berarti mengambil baris terakhir karena hanya 1 baris maka password untuk
secret.zip adalah “d1b1langbukanapaapajugagapercaya”


## Soal 11

### Soal
Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!

### Jawaban
menggunakan capture filter : ```src port 80```

![Capture Filter](https://user-images.githubusercontent.com/68275535/134756982-263b664d-0873-4e80-9cb3-555d4fcaacd9.png)

![Hasil Capture](https://user-images.githubusercontent.com/68275535/134756992-f7e6b601-4bcc-4998-a98a-b49a5b153709.png)

## Soal 12

### Soal
Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!

### Jawaban
menggunakan capture filter : ```port 21```

![Capture Filter](https://user-images.githubusercontent.com/68275535/134756998-f5a64e77-b46c-4105-b68d-329aa877621e.png)

![Hasil Capture](https://user-images.githubusercontent.com/68275535/134757002-3bcef147-2f16-4f65-afa3-30c6efabdd23.png)

## Soal 13

### Soal
Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!

### Jawaban
menggunakan capture filter : ```dst port 443```

![Capture Filter](https://user-images.githubusercontent.com/68275535/134757014-d4b23d24-4c39-4947-bb21-e16f09c5ea3b.png)

![Hasil Capture](https://user-images.githubusercontent.com/68275535/134757016-ef17ccfe-7059-4461-82f1-557a207e52a2.png)

## Soal 14

### Soal
Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!

### Jawaban
menggunakan capture filter : ```dst host kemenag.go.id```

![Capture Filter](https://user-images.githubusercontent.com/68275535/134757026-d835a1d6-47cd-47c6-ad60-06d7c38a87b5.png)

![Hasil Capture](https://user-images.githubusercontent.com/68275535/134757030-ca9e8350-ed86-4f1f-820f-624c6b67294e.png)

## Soal 15

### Soal
Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!

### Jawaban
Pertama untuk cek IP sendiri, dapat menggunakan Command Prompt (CMD) untuk windows, lalu menjalankan perintah ```ipconfig```

![IP config](https://user-images.githubusercontent.com/68275535/134757035-ba835180-e7f0-4cd1-af0e-30c5d094881a.png)

pada contoh diatas, didapat IPv4 Address ```192.168.1.7```. Masukkan dalam capture filter ```src host 192.168.1.7```

![Capture Filter](https://user-images.githubusercontent.com/68275535/134757036-cfe050e7-e133-4e52-8029-21e7fd415fd1.png)

![Hasil Capture](https://user-images.githubusercontent.com/68275535/134757038-5db02abc-648a-43fd-ae0c-41ee7923d46e.png)

## Kendala

- Kendala jaringan saat praktikum sehingga agak lama mengunduh file-file praktikum
