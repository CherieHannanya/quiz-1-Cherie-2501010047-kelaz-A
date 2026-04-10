# Karakteristik Memori dan Akses Data
karena terdapat perbedaan kecepatan akses antara keduanya terletak pada cara mereka menggunakan ruang di dalam memori (RAM).
Array dapat langsung "melompat" ke tujuan karena alamatnya bisa dihitung secara matematis (seperti lift menuju lantai tertentu), sedangkan Linked List harus menelusuri rantai satu per satu karena setiap data hanya tahu lokasi data setelahnya (seperti permainan mencari jejak).
# Analisis Efisiensi Operasi Manipulasi
dalam kondisi : 
1. Operasi di Bagian Depan (Awal List) dimana linked list hanya perlu mengubah satu atau dua pointer untuk menghubungkan node baru. Proses ini memakan waktu O(1) (Konstan) sedangkan array harus menggeser semua elemen yang ada.
   
2. Ketika Ukuran Data Sangat Dinamis dimana linked list dapat menambah atau menghapus elemen kapan saja tanpa biaya tambahan, sedangkan array jika kapasitas penuh, Array perlu melakukan resizing.
   
3. Penyisipan/Penghapusan di Tengah (Jika Posisi Sudah Diketahui) dimana linked list ketika posisi , sedangkan array walaupun indeksnya telah diketahui, Array tetap harus menggeser elemen untuk menutupi celah atau memberi ruang.

# Konsep Doubly Linked List
1. Anatomi Node
Berbeda dengan Singly Linked List yang hanya memiliki satu arah, setiap node dalam Doubly Linked List memiliki tiga komponen utama:

Data: Menyimpan nilai atau informasi (misal: angka, teks).

Pointer Next: Menyimpan alamat memori node setelahnya.

Pointer Prev (Previous): Menyimpan alamat memori node sebelumnya.

2. Dampak Penggunaan Memori
Lebih Boros: Keberadaan pointer Prev menambah beban penyimpanan. Setiap node harus menyimpan satu alamat memori tambahan (biasanya 4 atau 8 byte tergantung sistem).

Konsekuensi: Secara total, Doubly Linked List membutuhkan ruang memori yang lebih besar dibandingkan Singly Linked List untuk jumlah data yang sama.

3. Dampak terhadap Fleksibilitas
Keberadaan pointer tambahan ini memberikan keunggulan signifikan dalam penelusuran:

Dua Arah (Bidirectional): bisa menelusuri list dari depan ke belakang (Forward) maupun dari belakang ke depan (Backward). Pada Singly Linked List, kamu tidak bisa kembali ke node sebelumnya tanpa mengulang dari awal (Head).

Kemudahan Penghapusan: Operasi penghapusan node tertentu menjadi lebih efisien karena sistem sudah tahu alamat node sebelum dan sesudahnya secara langsung tanpa perlu melakukan pencarian ulang dari awal.

# Mekanisme Circular Linked List
1. Perbedaan Teoritis
Linked List Biasa (Linear): Node terakhir memiliki pointer next yang menunjuk ke None atau Null. Ini menandakan bahwa daftar telah mencapai ujungnya dan perjalanan berhenti di sana.

Circular Linked List: Node terakhir tidak menunjuk ke None, melainkan menunjuk kembali ke Node Pertama (Head). Hal ini menciptakan siklus atau lingkaran yang tidak terputus.

2. Skenario Penggunaan (Use Case)
Salah satu skenario yang paling efektif adalah pada Sistem Penjadwalan Round Robin (CPU Scheduling) dalam Sistem Operasi.

Cara Kerjanya: Bayangkan ada beberapa aplikasi (Proses A, B, dan C) yang membutuhkan waktu CPU. CPU akan memberikan waktu 10ms untuk A, lalu lanjut ke B, lalu ke C.

Keunggulan Circular: Karena strukturnya melingkar, setelah CPU selesai melayani Proses C, sistem secara otomatis kembali ke Proses A tanpa perlu logika tambahan untuk mencari kembali posisi awal. Proses ini terus berputar secara adil sampai semua tugas selesai.

# Array Dinamis di Python
1. Alokasi Memori Baru (Over-allocation)
Python tidak hanya menambah satu slot memori. Sistem akan memesan blok memori baru yang jauh lebih besar dari sebelumnya. Ukurannya biasanya sekitar 1.125 kali lipat hingga 2 kali lipat dari ukuran lama (tergantung pertumbuhan list). Ini dilakukan agar Python tidak perlu terlalu sering melakukan proses perpindahan data yang berat.

2. Menyalin Elemen (Copying)
Setelah blok memori baru yang lebih besar tersedia, Python akan menyalin setiap elemen dari alamat memori lama ke alamat memori yang baru secara berurutan.

3. Penghapusan Memori Lama
Setelah semua elemen berhasil dipindahkan ke "rumah baru", Python akan melepaskan (dealokasi) blok memori lama agar bisa digunakan kembali oleh sistem.

4. Menambahkan Data Baru
Terakhir, data yang di append akan diletakkan di slot kosong pertama pada memori baru tersebut.


