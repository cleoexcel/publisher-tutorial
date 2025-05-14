1. How much data your publisher program will send to the message broker in one run?
Program Publisher akan mengirimkan lima buah pesan ke message broker setiap kali dijalankan. Hal ini terlihat dari pemanggilan fungsi publish_event sebanyak lima kali dalam kode program. Setiap kali fungsi tersebut dipanggil, program membuat objek UserCreatedEventMessage dengan data user_id dan user_name yang berbeda, lalu mengirimkannya ke message broker. Jadi, dalam satu eksekusi penuh, Publisher secara total akan mengirim 5 data (pesan) ke antrian pesan.

2. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?
URL amqp://guest:guest@localhost:5672 adalah alamat koneksi yang digunakan oleh aplikasi (Publisher maupun Subscriber) untuk terhubung ke message broker yang berjalan di komputer lokal menggunakan protokol AMQP (Advanced Message Queuing Protocol). Rinciannya sebagai berikut:

- guest:guest adalah username dan password default untuk autentikasi ke server RabbitMQ.

- localhost menunjukkan bahwa server RabbitMQ dijalankan di komputer lokal (bukan di server eksternal).

- 5672 adalah port default yang digunakan RabbitMQ untuk koneksi AMQP.

- Fakta bahwa Publisher dan Subscriber menggunakan URL yang sama menandakan bahwa keduanya berkomunikasi dengan message broker yang sama. Publisher bertugas untuk mengirimkan pesan ke antrian (queue), sedangkan Subscriber bertugas sebagai listener yang akan mengambil dan memproses pesan dari antrian tersebut. Inilah cara kerja sistem message-oriented middleware — yaitu dengan peran pengirim dan penerima yang terpisah namun terhubung melalui satu server pusat (broker).

# Running RabbitMQ as message broker.
![Alt text](images/image1.jpg)


# “Sending and processing event.
![Alt text](images/image2.jpg)
![Alt text](images/image3.jpg)
![Alt text](images/image4.jpg)

 Publisher mengirim pesan ke RabbitMQ, dan Subscriber mengambil dan memproses pesan-pesan tersebut, sebagaimana yang terlihat di konsol. Ini menunjukkan bagaimana Publisher dan Subscriber berinteraksi menggunakan RabbitMQ sebagai perantara pesan dengan fungsionalitas dasar.