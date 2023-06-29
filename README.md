
Deskripsi Project 4 :
![dada](https://github.com/Abdlfuad/DATAANALYTICS_WITHHADOOP/assets/132795355/31791a1f-8c02-4906-87a3-549016761df3)


	
Data Analytics with Hadoop adalah project dimana kita sebagai seorang Data Engineer melakukan proses analisa data berupa map and reduce di datawarehouse(Hadoop). Proses Analisa data ini dilakukan karena permintaan dari user (analis), pada kasus ini seorang analis meminta kita untuk membuat data mart yang berisi total jumlah penjualan berdasarkan bulan. Flow project 4 ini dimulai dari kegiatan extract data menuju postgresql(data source), data yang telah diextract kemudian ditarik ke Hadoop(datawarehouse) berupa file dwh (dim_orders). Setelah data masuk di datawarehouse, data dianalis kemudian menghasilkan output berupa data mart, pada project 4 ini, output data mart berupa file .txt.


Alur Project 4 :
1.	Buat connection ke hadoop dengan menambah function baru “def hadoop_conn”
2.	Isi function adalah try and except, untuk mengeksekusi connection apakah berjalan
3.	Kembali ke app.py, masukkan script connection configuration hadoop
4.	Langkah selanjutnya ingest ke hadoop
5.	Buat script untuk ingest ke hadoop :
•	define file dengan nama file time yang berisi pembuatan file pada waktu saat ini
•	define path agar sesuai dengan keinginan kita
•	buat script data to csv
•	buat keterangan Hadoop Success
•	cek apakah file masuk ke hadoop server, pilih utilities dan directory

6.	File sudah berhasil masuk ke hadoop
7.	Langkah selanjutnya buka file mapreduce
8.	Import mrjob untuk mapreduce dan mrstep untuk multistage
9.	Buat fungsi step
10.	Define fungsinya, step pertama diawal menjalankan mapper, kemudian reducer
11.	Step kedua menjalan reducer berdasarkan mapper yang sudah dijalankan sebelumnya (hasil self reducer)

Flow pada project 4, data yang sudah di hadoop didownload dahulu ke local. Kemudian dari local akan diproses dengan mapreduce

12.	Cek data dengan row, jika row pertama order_id , maka itu header (akan dilewati)
13.	Pada fungsi mapper buat key berupa tahun dan bulan, maka yield row dengan indeks [0:7]
14.	Pada fungsi reducer value berisi key dan sum(values) karena tujuannya untuk sort
15.	Pada fungsi sort, reducer displit menjadi order_date dan order_count dan append dengan data
16.	Looping split order_date dan order_count pada data
17.	Output berupa order_date dan order_count yang sudah disort

Setelah dilakukan MapReduce, selanjutnya masukan script untuk pembuatan data mart

18.	Mengambil data dari hadoop kemudian diambil mapreducenya untuk kebutuhan datamart
19.	Pada script hdfs berisi syntax untuk mendownload output,menjadikan file agar support mapreduce (dijadikan di csv)
20.	Kemudian file csv nya dijalankan dengan map reduce untuk mendapatkan output datamart
21.	Wordercount_output_hadoop_map.txt' adalah output datamart
