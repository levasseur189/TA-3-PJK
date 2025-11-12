# TA-3-PJK
Proyek ini berjudul Packet Tracer – Configure VLANs and Trunking (Physical Mode) yang bertujuan untuk memahami konsep dasar konfigurasi VLAN dan trunking pada jaringan komputer menggunakan aplikasi Cisco Packet Tracer. Dalam kegiatan ini, dilakukan simulasi pembuatan jaringan yang terdiri dari dua switch dan dua PC yang saling terhubung untuk mempraktikkan cara membangun jaringan virtual yang efisien, aman, dan tersegmentasi dengan baik.

Langkah pertama yang dilakukan adalah membangun topologi jaringan sesuai dengan desain yang diberikan, kemudian mengonfigurasi pengaturan dasar seperti hostname perangkat, password akses, banner keamanan, serta pengaturan IP address pada masing-masing switch dan PC. Selanjutnya, dibuat beberapa VLAN dengan fungsi yang berbeda, yaitu VLAN 10 (Operations), VLAN 20 (Parking_Lot), VLAN 99 (Management), dan VLAN 1000 (Native). Masing-masing port pada switch diatur agar terhubung dengan VLAN tertentu sesuai kebutuhan, sehingga setiap perangkat hanya dapat berkomunikasi dengan anggota VLAN yang sama.

Setelah VLAN berhasil dikonfigurasi, tahap berikutnya adalah melakukan pemeliharaan dan pengujian VLAN, seperti menambahkan dan menghapus VLAN dari database, serta memindahkan port ke VLAN lain untuk memahami dampaknya terhadap konektivitas jaringan. Proses ini membantu dalam memahami bagaimana VLAN bekerja dalam membatasi domain broadcast dan meningkatkan keamanan jaringan.

Pada bagian akhir, dilakukan konfigurasi trunking antar switch menggunakan protokol 802.1Q. Awalnya port F0/1 pada kedua switch dikonfigurasi dalam mode dynamic desirable agar dapat menegosiasikan trunk secara otomatis, lalu diubah menjadi mode trunk manual untuk memastikan stabilitas koneksi. Native VLAN juga diganti dari VLAN 1 menjadi VLAN 1000 guna meningkatkan keamanan jaringan, karena VLAN 1 merupakan default VLAN yang rawan disalahgunakan.

Hasil pengujian menunjukkan bahwa PC-A dan PC-B dapat saling berkomunikasi setelah trunk berhasil dikonfigurasi, namun tidak dapat berkomunikasi langsung dengan switch karena berada pada VLAN yang berbeda. Hal ini menunjukkan bahwa komunikasi antar VLAN membutuhkan perangkat Layer 3 seperti router atau switch multilayer untuk melakukan inter-VLAN routing.

Secara keseluruhan, proyek ini memberikan pemahaman mendalam mengenai manfaat penggunaan VLAN dalam jaringan, yaitu meningkatkan keamanan, efisiensi penggunaan bandwidth, dan performa jaringan dengan membagi domain broadcast menjadi lebih kecil. Selain itu, praktik trunking memperlihatkan bagaimana VLAN dapat diperluas antar beberapa switch tanpa kehilangan segmentasi logisnya. Implementasi ini menggambarkan konsep penting dalam desain jaringan modern yang efisien dan terstruktur.

link youtube: https://youtu.be/lcFgVXZqySw

