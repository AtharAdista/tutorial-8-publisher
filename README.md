### Nama : Shaquille Athar Adista
### NPM : 2206081875

1. How many data your publlsher program will send to the message broker in one
run?

    Jumlah data yang dipublish dalam satu kali run adalah lima  data, hal ini dapat kita lihat di dalam main.rs. Di main.rs terdapat lima data yang dipublish dengan memanfaatkan method publish_event, yang masing-masingnya mengirimkan UserCreatedEventMessage.

2. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?
   
   - `amqp://` menunjukkan penggunaan protokol amqp
   - `guest:guest@localhost:5672` menentukan kredensial untuk otentikasi ke server RabbitMQ dan alamat serta port server RabbitMQ
   - `guest:guest` adalah username (guest) dengan kata sandi guest, ini dignakan untuk melakukan proses otentikasi
   - `localhost:5672` adalah alamat dan port server RabbitMQ. localhost menunjukkan bahwa server RabbitMQ berjalan di mesin lokal (komputer tempat program dijalankan), dan 5672 adalah port default yang digunakan oleh RabbitMQ.
  
    Nantinya publisher dan subscriber akan saling terhubung, sehingga publisher akan dapat mempublish data dan subscriber akan dapat mengambil data yang dikirim oleh publisher.

Interface RabbitMQ

![alt text](images/RabbitMQ_interface.png)

RabbitMQ memiliki 1 koneksi
![alt text](images/RabbitMQ_connection.png)

menerima 5 event message dari publisher
![alt text](images/5_data.png)

console dari publisher ketika menjalankan cargo run
![alt text](images/console_publisher.png)

Image diatas menunjukkan saat melakukan cargo run di publisher dan subscriber, maka publisher akan mengirimkan data melalui RabbitMQ, kemudian subscriber akan menerima data yang sudah dipublish oleh publisher. Publisher akan membuat koneksi dengan server message dalam kasus ini RabbitMQ, publisher mengirim pesan ke exchage, exchange bertanggung jawab untuk megarahkan pesan ke queue, kemudian subscriber akan menerima pesan yang ada di queue.

spikes di RabbitMQ
![alt text](spikes_RabbitMQ.png)

pada gambar terlihat bahwa pada grafik kedua terjadi peningkatan, hal ini berhubungan dengan cargo run yang dijalankan di publisher, semakin sering publisher dijalankan maka akan terjadi peningkatan message rate karena RabbitMQ menerima lebih banyak pesan dalam suatu interval waktu. Pada grafik kedua saya menjalankan publisher lebih banyak daripada saat di grafik pertama.



