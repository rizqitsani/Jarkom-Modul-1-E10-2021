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

### Jawaban

## Soal 7

### Soal

### Jawaban

## Soal 8

### Soal

### Jawaban

## Soal 9

### Soal

### Jawaban

## Soal 10

### Soal

### Jawaban

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
