Tugas Akhir Judul 3 - Praktikum Jaringan Komputer
Ini adalah dokumentasi proyek untuk lab jaringan yang dibuat menggunakan Cisco Packet Tracer. Proyek ini mencakup topologi, konfigurasi, dan hasil verifikasi konektivitas antar perangkat.

Topologi Jaringan
Berikut adalah topologi jaringan yang digunakan dalam lab ini:
<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/d3475251-4487-4785-9978-6bb52fdfd3fe" />

Topologi Jaringan Tugas Akhir Judul 3
Video Penjelasan
Untuk penjelasan lengkap dan tutorial langkah demi langkah mengenai konfigurasi lab ini, silakan tonton video YouTube berikut:
https://youtu.be/lcFgVXZqySw

Part 1: Pengecekan Konektivitas (Ping)
Bagian ini berisi hasil-hasil pengecekan konektivitas awal menggunakan perintah ping untuk memverifikasi komunikasi antar perangkat.

1. Ping PC-A ke PC-B
Pengecekan konektivitas antara dua host pada switch yang berbeda (atau sama, tergantung topologi yang lebih detail). 
<img width="1071" height="480" alt="image" src="https://github.com/user-attachments/assets/d95e6380-0998-442e-8d7a-bc6526b81e0e" />

Hasil: Sukses (0% loss).
Analisis: PC-A (IP tidak terlihat) dan PC-B (192.168.10.4) dapat berkomunikasi dengan sukses.



2. Ping PC-A ke Switch 1 (S1)
Pengecekan konektivitas dari PC-A ke interface manajemen Switch 1 (S1). Part 1 Ping PC-A ke Switch 1
<img width="995" height="308" alt="image" src="https://github.com/user-attachments/assets/b3449e81-a122-4183-b98f-278667724c01" />

Hasil: Gagal (100% loss).
Analisis: PC-A tidak dapat menjangkau interface manajemen S1 di 192.168.1.11. Ini bisa disebabkan oleh kesalahan konfigurasi IP pada PC-A, S1, atau masalah VLAN.




3. Ping PC-B ke Switch 2 (S2)
Pengecekan konektivitas dari PC-B ke interface manajemen Switch 2 (S2).
<img width="1016" height="466" alt="image" src="https://github.com/user-attachments/assets/fc01fef7-71e5-4bf3-8f06-60523a66bd5c" />



Hasil: Gagal (100% loss).
Analisis: Sama seperti kasus PC-A, PC-B tidak dapat menjangkau interface manajemen S2 di 192.168.1.12.
4. Ping PC-C ke Semua Switch
Pengecekan konektivitas dari PC-C ke interface manajemen S1 (192.168.1.11) dan S2 (192.168.1.12). 
<img width="1077" height="746" alt="image" src="https://github.com/user-attachments/assets/eceb44e5-9aa8-4138-8313-fc489bb15a13" />




Hasil: Sukses dengan 25% loss (paket pertama timeout).
Analisis: PC-C berhasil terhubung ke kedua switch karena tidak ada default gateaway lain halnya dengan PC-A dan PC-B. Kehilangan paket pertama (Request timed out) adalah hal yang wajar dan biasanya disebabkan oleh proses ARP (Address Resolution Protocol) yang sedang bekerja untuk menemukan alamat MAC switch.



5. Ping Switch 1 (S1) ke Switch 2 (S2)
Pengecekan konektivitas antar switch, kemungkinan melalui link trunk. Part 1 Ping Switch 1 ke Switch 2
<img width="1028" height="267" alt="image" src="https://github.com/user-attachments/assets/537123bf-1d97-4c8a-bd47-b6453d7881d2" />




Hasil: Percobaan pertama 60% sukses, percobaan kedua 100% sukses.
Analisis: Koneksi antar switch berfungsi. Kehilangan beberapa paket pada percobaan pertama (ditandai dengan .!!!!) bisa jadi karena proses seperti Spanning Tree Protocol (STP) yang sedang converging atau ARP. Percobaan kedua yang sukses 100% (!!!!!) mengkonfirmasi bahwa link sudah stabil.
Tentu, ini adalah lanjutan untuk file README.md Anda, yang mencakup Part 2.



Part 2: Membuat VLAN dan Menetapkan Port Switch
Pada bagian ini, konfigurasi VLAN diterapkan. Beberapa VLAN (Operations, Parking_Lot, Management, dan Native) dibuat di kedua switch. Selanjutnya, port untuk PC dan interface manajemen switch dipindahkan ke VLAN yang sesuai.

Hasil Pengecekan Konektivitas
Setelah memindahkan port PC dan interface manajemen ke VLAN masing-masing, pengecekan konektivitas dilakukan kembali.

Penting: Kegagalan ping pada tahap ini sudah diharapkan. Ini terjadi karena port yang menghubungkan S1 dan S2 (Fa0/1) masih merupakan port access dan belum dikonfigurasi sebagai trunk untuk membawa trafik dari VLAN 10 dan VLAN 99.

1. Ping PC-A ke PC-B (Gagal)
<img width="1080" height="433" alt="image" src="https://github.com/user-attachments/assets/a2e60b6a-3289-435d-81f9-c02c1ef9a5ac" />

Hasil: Gagal (100% loss).
Analisis: Meskipun PC-A dan PC-B sekarang berada di VLAN yang sama (VLAN 10), trafik antar-switch untuk VLAN 10 diblokir karena tidak ada trunk link yang mengizinkannya.
2. Ping Switch 1 ke Switch 2 (Gagal)
<img width="1065" height="130" alt="image" src="https://github.com/user-attachments/assets/4461e900-88ec-4928-b568-999aafa54f9e" />

Hasil: Gagal (0% success).
Analisis: Sama seperti trafik PC, trafik manajemen (VLAN 99) juga tidak dapat melewati port antar-switch karena port tersebut belum dikonfigurasi sebagai trunk.
Tentu, ini adalah draf untuk Part 4 yang bisa Anda tambahkan ke file README.md Anda.

Part 4: Konfigurasi 802.1Q Trunk Antar Switch
Pada bagian ini, link antar switch (interface F0/1) dikonfigurasi sebagai trunk untuk mengizinkan trafik dari beberapa VLAN (VLAN 10 dan VLAN 99) melewatinya.

Konfigurasi ini awalnya menggunakan Dynamic Trunking Protocol (DTP). Interface F0/1 pada S1 diatur ke mode dynamic desirable, yang menyebabkannya berhasil bernegosiasi menjadi trunk dengan S2 (yang berada dalam mode default dynamic auto).

Hasil Pengecekan Konektivitas (Setelah Trunk Aktif)
Setelah link trunk terbentuk, konektivitas yang sebelumnya gagal di Part 2 sekarang diuji kembali.

1. Ping PC-A (VLAN 10) ke PC-B (VLAN 10)
<img width="1071" height="485" alt="image" src="https://github.com/user-attachments/assets/5aa37340-a972-4a74-b170-b86b1415c356" />

Hasil: Sukses (0% loss).
Analisis: Link trunk sekarang mengizinkan trafik untuk VLAN 10 (Operations) lewat. Karena kedua PC berada di VLAN yang sama, mereka sekarang dapat berkomunikasi melintasi kedua switch.
2. Ping Switch 1 (VLAN 99) ke Switch 2 (VLAN 99)
<img width="1052" height="274" alt="image" src="https://github.com/user-attachments/assets/5001c65a-b46d-4b81-b3c7-2fbf869f75af" />

Hasil: Sukses (100% success).
Analisis: Link trunk juga mengizinkan trafik untuk VLAN 99 (Management). Ini memungkinkan interface manajemen S1 dan S2 untuk saling berkomunikasi.
3. Ping PC-B (VLAN 10) ke Switch 2 (VLAN 99)
<img width="1024" height="327" alt="image" src="https://github.com/user-attachments/assets/444da677-39a0-46e4-ad42-994198d2d3d5" />

Hasil: Gagal (100% loss).
Analisis: Ping ini gagal sesuai desain (inter-VLAN). PC-B berada di VLAN 10, sedangkan interface manajemen S2 berada di VLAN 99. Switch (Layer 2) tidak akan meneruskan trafik antara VLAN yang berbeda tanpa adanya router (Layer 3).
4. Ping PC-C (VLAN 99) ke Switch 1 & 2 (VLAN 99)
<img width="1001" height="631" alt="image" src="https://github.com/user-attachments/assets/a252d9f4-65ba-409e-a725-d80130bd512f" />

Hasil: Sukses (dengan 25% loss untuk paket pertama/ARP).
Analisis: PC-C (yang tampaknya dikonfigurasi di VLAN 99) dapat berhasil melakukan ping ke interface manajemen S1 dan S2. Ini mengkonfirmasi bahwa PC-C berada di VLAN manajemen dan memiliki konektivitas yang benar.
