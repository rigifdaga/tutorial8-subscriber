1. What is AMQP?
   AMQP, atau Advanced Message Queuing Protocol, adalah protokol standar yang biasa digunakan pada lapisan aplikasi untuk middleware berbasis pesan. Protokol ini umumnya digunakan dalam pembuatan sistem pengiriman pesan. Melalui AMQP, berbagai aplikasi dapat berinteraksi satu sama lain secara efisien melalui pertukaran pesan.


2. what it means? guest:guest@localhost:5672 , what is the first quest, and what is
   the second guest, and what is localhost:5672 is for?  
   guest:guest@localhost:5672 adalah string koneksi untuk sebuah server AMQP. guest:guest adalah kombinasi nama pengguna dan kata sandi default untuk autentikasi pada server. Di sini, baik nama pengguna maupun kata sandinya adalah 'guest'. Pada banyak konfigurasi standar broker pesan seperti RabbitMQ, nama pengguna dan kata sandi defaultnya juga 'guest'. Namun, di lingkungan produksi, disarankan untuk mengubah kredensial default ini karena pertimbangan keamanan.
   @localhost:5672 menunjukkan alamat host dan port yang digunakan. Istilah 'localhost' merujuk pada komputer lokal, yang berarti bahwa message broker (RabbitMQ) berjalan di komputer yang sama di mana kode ini dieksekusi. Port 5672 adalah port default yang digunakan oleh RabbitMQ untuk melakukan komunikasi menggunakan protokol AMQP.

3. Simulation slow subscriber
   Screenshot antarmuka RabbitMQ yang di mana Queue-nya mencapai 20. Hal ini disebabkan karena saya menjalankan `cargo run` sebanyak 6 kali sehingga terjadi queue sebanyak 5 cargo run. Jadi, 1 cargo run itu mengirimkan sebanyak 4 data sehingga terdapat queue sebanyak 20 data.
   
   [![e08ce3d8-6527-4ffc-bd1c-bbf9cc91f8c5.jpg](https://i.postimg.cc/Z5GyhT92/e08ce3d8-6527-4ffc-bd1c-bbf9cc91f8c5.jpg)](https://postimg.cc/87bCRgmm)

   4. Running at least three subscribers
   Screenshot menjalankan `cargo run` sebanyak 3 kali di console yang perbeda pada subscriber.
  
   [![b7873ba0-724f-48d6-b01d-0a899b1e9081.jpg](https://i.postimg.cc/gJYmZjFB/b7873ba0-724f-48d6-b01d-0a899b1e9081.jpg)](https://postimg.cc/Lq0cdHsz)

   Screenshot menjalankan `cargo run` sebanyak 4 kali pada publisher.
   [![21fe9747-ed95-4dc5-9804-d0b3c254337a.jpg](https://i.postimg.cc/V69QTXHV/21fe9747-ed95-4dc5-9804-d0b3c254337a.jpg)](https://postimg.cc/PpqRvvHW)

* Screenshot hasil spike dari message queue berkurang yang menunjukkan peningkatan kecepatan dari sebelumnya karena request yang diterima queue dapat dibagi kepada 3 subscriber.
  [![3c1a7127-2157-43b7-af3d-cbc3fec421bf.jpg](https://i.postimg.cc/wTX2m0RP/3c1a7127-2157-43b7-af3d-cbc3fec421bf.jpg)](https://postimg.cc/ppdKNQZY)