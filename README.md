# Sistem Rekomendasi Film

Nama: Abraham Pardomuan Naiborhu

## Daftar Isi

* [Project Overview](#project-overview)

* [Business Understanding](#business-understanding)

* [Data Understanding](#data-understanding)

* [Data Preparation](#data-preparation)

* [Modeling](#modeling)

* [Evaluation](#evaluation)

* [Reference](#referensi)

  

## Project Overview

​	Dewasa ini, film sudah banyak beredar di dunia. Film yang beredar di dunia itu juga memiliki keragaman yang sangat luas. Ditambah lagi, film sudah menjadi konsumsi sehari-hari bagi masyarakat dunia. Orang-orang dari sabang sampai merauke juga telah memahami kenikmatan menonton film, terutama nikmatnya menonton film bersama orang-orang tersayang (seperti pacar). Akses terhadap film juga sangat mudah akibat perkembangan zaman, kita dapat mengakses film via bioskop, via DVD, dan via website seperti Netflix, Hulu, Disney+. Kemudahan akses terhadap film dan keragaman film dapat membuat kita *overwhelmed*. Terlalu banyak informasi (terutama mengenai film [untuk kasus ini]) dapat membuat kita kesusahan untuk menikmati kenikmatan dari film itu sendiri. Oleh sebab itu, dibutuhkanlah sebuah sistem yang dapat mempermudah kita untuk membuat keputusan mengenai apa yang harus ditonton dan tontonan tersebut sesuai dengan selera sang penontonnya.

​	Sistem remomendasi itu sangat penting. karena di Internet, di mana jumlah pilihan sangat banyak, ada kebutuhan untuk menyaring, memprioritaskan, dan menyampaikan informasi yang relevan secara efisien untuk mengurangi masalah kelebihan informasi. Sistem rekomendasi dapat memecahkan masalah ini dengan mencari melalui sejumlah besar informasi yang dihasilkan secara dinamis untuk menyediakan konten dan layanan yang dipersonalisasi kepada pengguna [[1](https://www.sciencedirect.com/science/article/pii/S1110866515000341#:~:text=Recommender%20system%20has%20the%20ability,online%20shopping%20environment%20%5B4%5D.)]. Pada proyek ini, akan dibuat sebuah sistem rekomendasi film yang dapat merekomendasikan film secara tepat kepada pengguna demi meningkatkan *user experience*.  Data yang digunakan dalam proyek ini adalah data mengenai film yang sudah diberi rating dari penikmat film lainnya.

## Business Understanding

### Problem Statements

Berdasarkan project overviewnya,  kita dapat menyimpulkan permasalahan yang perlu diselesaikan di proyek ini, yaitu:

* Apa sistem rekomendasi yang dapat digunakan untuk memaksimalkan *user experience* para pengguna?
* Bagaimana cara membuat sistem rekomendasi film untuk pengguna?

### Goals

Berdasarkan Problem and Statements diatas, ini adalah tujuan dari dibuatnya proyek ini:

* Memilih sistem rekomendasi yang dapat memaksimalkan user experience para pengguna
* Membuat sistem rekomendasi film untuk para pengguna
* Memberikan rekomendasi film yang kemungkinan disukai pengguna

### Solution Approach

Proyek ini akan menggunakan dua teknik dalam pembuatan recommendation systemnya. Teknik pertama adalah Conten Based Filtering dan teknik kedua adalah Collaborative Based Filtering. Kedua teknik itu dipilih karena dataset yang akan digunakan berkaitan dengan rating dari pengguna, dan genre. Dataset yang digunakan untuk proyek ini adalah dataset dari [Kaggle](https://www.kaggle.com/aigamer/movie-lens-dataset) mengenai film.

**Content Based Filtering** adalah adalah teknik Machine Learning yang menggunakan kesamaan fitur untuk membuat keputusan. Teknik ini sering digunakan dalam sistem pemberi rekomendasi, yaitu algoritma yang dirancang untuk mengiklankan atau merekomendasikan sesuatu kepada pengguna berdasarkan pengetahuan yang terkumpul tentang pengguna[[2](https://www.educative.io/edpresso/what-is-content-based-filtering)]. Pada Proyek, teknik yang digunakan dalam Content Based Filtering adalah *Cosine Similarity*. Cosine Similarity mengukur kesamaan antara dua vektor ruang hasil kali dalam. Ini diukur dengan kosinus sudut antara dua vektor dan menentukan apakah dua vektor menunjuk ke arah yang kira-kira sama [[2](sciencedirect.com/topics/computer-science/cosine-similarity)].
![cosine similarity](https://neo4j.com/docs/graph-data-science/current/_images/cosine-similarity.png)

Content Based Filtering memiliki beberapa kelebihan dan kekurangan. Kekruangan dari content based filtering adalah sebagai berikut [[3](https://developers.google.com/machine-learning/recommendation/content-based/summary)]:

* modelnya tidak memerlukan data apa pun tentang pengguna lain, karena rekomendasinya khusus untuk pengguna ini. Ini membuatnya lebih mudah untuk menskalakan ke sejumlah besar pengguna.
* Model dapat menangkap minat khusus pengguna, dan dapat merekomendasikan item khusus yang sangat sedikit diminati pengguna lain.



Sementara itu, kelebihan dari conten based filtering adalah sebagai berikut:

* Karena representasi fitur dari item direkayasa dengan manual sampai batas tertentu, teknik ini membutuhkan banyak pengetahuan domain. Oleh karena itu, modelnya hanya bisa sebagus fitur rekayasa manual.
* Model hanya dapat membuat rekomendasi berdasarkan minat pengguna yang ada. Dengan kata lain, model memiliki kemampuan terbatas untuk memperluas minat pengguna yang ada.



**Collaborative Based Filtering** atau penyaringan kolaboratif menggunakan kesamaan antara pengguna dan item secara bersamaan untuk memberikan rekomendasi. Hal ini memungkinkan untuk rekomendasi yang dapat dibilang sebagai "tanpa sengaja"; yaitu, model pemfilteran kolaboratif dapat merekomendasikan item kepada pengguna A berdasarkan minat pengguna B yang serupa. Selanjutnya, penyematan dapat dipelajari secara otomatis, tanpa mengandalkan fitur rekayasa [[3](https://developers.google.com/machine-learning/recommendation/collaborative/basics)]. Untuk proyek ini, teknik yang akan digunakan untuk Collaborative Based Filtering adalah teknil Deep Learning (Hal mengenai Deep Learning akan dijelaskan kelak di bab Modeling).

Untuk Collaborative Based Filtering, Terdapatnya kelebihan dan kekurangan [[4](https://developers.google.com/machine-learning/recommendation/collaborative/summary)]. Kelebihan dari Collaborative Based Filtering adalah sebagai berikut:

* Tidak diperlukannya pengetahuan domain karena embeddings dipelajari secara otomatis.
* Model ini dapat membantu pengguna menemukan minat baru. Secara terpisah, sistem ML mungkin tidak mengetahui bahwa pengguna tertarik pada item tertentu, tetapi model mungkin masih merekomendasikannya karena pengguna serupa tertarik pada item tersebut.
* Sampai batas tertentu, sistem hanya membutuhkan matriks umpan balik untuk melatih model faktorisasi matriks. Secara khusus, sistem tidak memerlukan fitur kontekstual. Dalam praktiknya, ini dapat digunakan sebagai salah satu dari beberapa kandidat generator.

Sementara itu, Collaborative Based Filtering juga memiliki kekurangan seperti:

* Tidak dapat menangami kontent segar (baru)
* Sulit untuk menyertakan fitur sampingan untuk kueri/item



## Data Understanding

Dataset--yang berjudul Movie Lens Datasets--untuk proyek ini berasal dari [kaggle](https://www.kaggle.com/) dengan url menuju datasetnya sebagai berikut: https://www.kaggle.com/aigamer/movie-lens-dataset. Dataset ini memiliki empat files yaitu:

* Links.csv

  ​	Terdapat tiga variabel yaitu: movieId(identifier for movies used by Movie Lens), imdbId(identifier for movies used by IMDb), tmdbId(identifier for movies used by TMDB).

* Movies.csv

  ​	Terdapat tiga variabel pada file ini, yaitu: moveiId (unique Id provided for each movie), Title (name of the moview with 9737 unique values), genres (genre dari film tersebut)

* Ratings.csv

  ​	Terdapat empat variabel pada file ini, yaitu: userId(unique id provided for each user), moveId(unique id provided for each movie), rating(5 scale star with 0.5 increment), timestamp(Timestamps represent seconds since midnight Coordinated Universal Time (UTC) of January 1, 1970.)

* Tags.csv

  ​	userId(unique id provided for each user), moveId(unique id provided for each movie), rating(5 scale star with 0.5 increment), tags(Tags are user-generated metadata about movies.), timestamp(Timestamps represent seconds since midnight Coordinated Universal Time (UTC) of January 1, 1970.)

  

Di dataset ini terdapat 9742 judul film dengan 100836 rating yang diberikan oleh pengguna. Di dataset ini pula terdapat banyak gendres, yaitu: Action, Adventure, Animation, Children's, Comedy, Crime, Documentary, Drama, Fantasy, Film-Noir, Horror, Musical, Mystery, Romance, Sci-Fi, Thriller, War, Western, dan (no genres listed). Kemudian, setelah membaca Business understanding, kita mengetahui bahwa data yang akan digunakan hanya berdasarkan dari dua file, yaitu rating.csv dan file movie.csv, file-file lainnya tidak akan kita gunakan. Terakhir, setelah melihat hasil dari kedua file, kita dapat menyimpulkan variable variabe yang akan digunakan adalah sebagai berikut:

* movie.csv
  * MovieID: Data ID Film (int64)
  * Title: Judul Film (Object)
  * Genres: Genre Film (Object)

* rating.csv

  * UserID: Data ID pengguna (int64)

  * MoveID: Data ID Film (int64)

  * Rating: Penilaian pengguna terhadap film (float64)

  * Timestamp: timestamp (int64)

    

Dalam proses data understanding, banyak visualisasi data yang diberlakukan, dapat berupa histogram atau tabel yang bertujuan untuk mengetahui lebih lanjut mengenai data-data pada dataset ini. Tanpa berlama lama, visualisasinya akan di mulai dari sekarang:

![first](https://user-images.githubusercontent.com/87258755/141749485-9005a370-acf6-4ac6-b9b6-7585977a8900.png)

Dari data kita dapat melihat bahwa distribusi film terbanyak terdapat di tahun 2000 keatas.
![second](https://user-images.githubusercontent.com/87258755/141749699-56b6afbd-8bf9-4740-afbe-6916d9e5edf8.png)

Kemudian, kita dapat melihat visualisasi genre dari dataset movie yang digunakan. Terlihat bahwa genre drama dan movie adalah dua genre paling banyak.

![third](https://user-images.githubusercontent.com/87258755/141749785-ac061c0e-a53b-4eff-9b7f-e26a0c064e2e.png)
![fourth](https://user-images.githubusercontent.com/87258755/141749828-ab6008df-344e-41d5-b425-f419da07fa2c.png)
Selanjutanya, diatas adalah visualisasi dari 10 film dengan rating terbanyak. Kedudukan pertama ditempati oleh Forest Gump dengan 329 rates.
![fifth](https://user-images.githubusercontent.com/87258755/141750001-82089f2d-b469-44a6-90fe-9d9a942cc1bb.png)

Terakhir, ini adalah distribusi dari rating yang diberikan ke film yang ada. Karena datanya telihat left-skewed, kita akan melakukan normalisasi pada data preparation untuk menanggulangi masalah ini.



## Data Preparation

Dalam data preparation ada beberap hal yang saya lakukan yaitu sebagai berikut:

1. Mengecek dan menghilangkan data duplikat

   Mengecek dan menghilangkan data duplikat untuk mengurangi bias yang dapat terjadi saat modeling.

![sixth](https://user-images.githubusercontent.com/87258755/141750371-be0b4bc7-5cca-4b17-b940-68cc5a618fb5.png)

   Untungnya, pada dataset kali ini, tidak ada data duplikat

2. Menghilangkan data Null

   Menghilangkan null akan membuat model yang _**robust**_.

   ![seventh](https://user-images.githubusercontent.com/87258755/141750492-4f949825-99a9-4ff5-809f-6052746fba0b.png)![eigth](https://user-images.githubusercontent.com/87258755/141750570-0fd3603f-b6c2-4b89-8472-6f7a337df4b1.png) 

   Kedua foto tersebut diambil dari file movie.csv dan file rating.csv. Dapat dilihat bahwa ada 13 data null di gambar movie.csv, tetapi data kosong tersebut adalah dari column year, dan column year tidak kita butuhkan. Oleh sebab itu, column year akan kita drop 


3. Menghilangkan variabel yang tidak dibutuhkan lagi

   Variabel yang tidak dibutuhkan dapat mengganggu pembuatan model, oleh sebab itu harus dibuang. Seperti yang sudah dituangkan pada nomor dua, column year akan di drop.
   
4. Preparation for Cosine Similarity

   Untuk Cosine Similarity, ada beberapa hal yang harus kita lakukan sebelum data siap untuk di train, yaitu:

   1. One-Hot-Encoding Genres

      Proses ini dibutuhkan unutk cosine similarity. Karena Cosine similarity kali ini melihat persamaan genres, maka genres lah yang di one-hot-encodingkan

      ![ninth](https://user-images.githubusercontent.com/87258755/141750729-509422a9-9719-4a8c-a10d-67510de21a7a.png)

      

   2. Matrix

      selanjutnya, di buatkan matrix sehingga model dapat menghitung cosine similaritynya kelak.

      ![tenth](https://user-images.githubusercontent.com/87258755/141750788-9db292d4-01ac-45c7-9c7b-2299de3bdc05.png)

      

6. Preparation for Deep Learning

   Untuk tahap ini, hal-hal yang dilakukan adalah sebagai berikut: 

   * Data Encoding fitur userId dan movieId ke dalam inteks integer

     karena model tidak dapat menggunakan data categorical kita akan menyandikan userID dan movieID kedalam indeks integer, kita akan melakukan Data Encoding terhadap datasetnya. Implementasi dari data encoding tersebut menghasilkan hasil seperti ini:

     ![image](https://user-images.githubusercontent.com/87258755/142372907-a4b316ac-e43b-4162-8592-a91076118d35.png)
   
   * Normalisasi pada data
   
     Pada data visualisasi, kita mengentahui bahwa column rating memiliki visualisasi yang left-skewed. oleh sebab itu, kita harus melakukan normalisasi data sehingga data tersebut berada pada rentang 0 hingga 1 menggunakan rumus:
   
     ![image](https://user-images.githubusercontent.com/87258755/142373597-979b4856-0713-4a1d-992b-2a15ad8ffce8.png)
   
     
   
     

## Modeling

Pada modeling ini, ada dua teknik yang digunakan (dan telah disinggung di bagian pendahuluan). Model yang digunakan untuk proyek kali ini adalah Cosine similarity untuk content-based filterting dan Deep Learning untuk collaborative based filtering. Berikut adalah hasilnya:

* Cosine Similarity

  Cosine Similiarity kali ini akan memberikan 5 rekomendasi film yang memiliki genre sama. Sebagai contoh, kali ini saya mencoba untuk mendapatkan rekomendasi dari film "The Darkest Minds (2018)" dan berikut adalah hasil dari rekomendasi yang diberikan:

  ![eleventh](https://user-images.githubusercontent.com/87258755/141750843-e5d30736-cced-43b0-b2f1-baf9a9890883.png)

  Kelima film tersebut memiliki kesamaan pada genre sci-fi dan genre thriller. Sesuai dengan film yang digunakan sebagai contoh, film The Darkest Minds (2018) juga memiliki genre yang sama.

  

* Deep Learning

  Deep learning adalah teknik Machine Learning yang memiliki banyak kegunaan. Contohnya, saya menggunakan Deep Learning untuk melakukan collaborative filtering. Aplikasi dari deep learning dari project ini adalah layer embedding. Embedding adalah pemetaan variabel diskrit — kategoris — ke vektor bilangan kontinu sehingga dapat digunakan untuk proses selanjutnya [[6](https://towardsdatascience.com/neural-network-embeddings-explained-4d028e6f0526)]. Kemudian, setelah didapatkanlah nilai vektornya, lakukan operasi perkalian dot product antara hasil embeddingnya (user dan movie). Selain itu, kita juga dapat menambahkan bias untuk setiap user dan resto. kecocokan ditetapkan dalam skala 0 hingga 1 dengan fungsi aktivasi sigmoid. Pada model ini, Optimizer yang digunakan adalah optimizer adam dan loss function yang digunakan adalah Loss Binary Crossentropy. Untuk metrik yang digunakan, akan dijelaskan pada bagian evaluasi model.

  Pada model ini, kami menggunakan user acak dan mendapatkan rekomendasi berdasarkan film yang pernah dia tonton sebelumnya.

  ![12th](https://user-images.githubusercontent.com/87258755/141750898-d5e68746-a334-4fa0-8388-b61d4a425eac.png)
  
  Terlihat bahwa user 387 menonton beberapa film yang genrenya tertera diatas. Kemudian, rekomendasi yang diberikan adalah film film yang memiliki genre yang juga tertera pada film film yang pernah user 387 tonton sebelumnya.

## Evaluation

Pada evaluation, ada dua teknik yang saya gunakan ke tiap tiap model yang saya gunakan. 

* cosine similarity

  saya melihat kesamaan genre antara film yang input dengan rekomendasi yang diberikan. Pada inputan film tadi, genrenya adalah thriller dan sci-fi. Presisi yang diberikan oleh model adalah 100%, berikut adalah visualisasinya:

  ![13th](https://user-images.githubusercontent.com/87258755/141750966-eb863d23-bb36-46cc-aebd-6faa3a7fc538.png)

  Metrik yang diatas adalah metrik precision. Precision adalah ratio dari true positive dan total dari true positive dan false positive, rumusnya sebagai berikut:

  **precision = True Positive / (True Positive + False Positive)**

  Berdasarkan akurasi diatas, kita dapat melihat bahwa precisionnya mencapai 100%. Artinya tidak ada false positive dari prediction tersebut. Pada intinya, berdasarkan metriks precision, kita dapat melihat bahwa model dapat memberikan rekomendasi berdasarkan content yang tepat sasaran dengan nilai 100.

  

* Deep Learning

  Pada model ini, saya menggunakan Root Mean Square Error (RMSE) sebagai metriks evaluasi. adalah standar deviasi dari residual (kesalahan prediksi). RMSE adalah standar deviasi dari residual (kesalahan prediksi). Residual adalah ukuran seberapa jauh dari titik data garis regresi; RMSE adalah ukuran seberapa menyebar residu ini. Dengan kata lain, ini memberi tahu Anda seberapa terkonsentrasi data di sekitar garis yang paling cocok. Berikut adalah rumus dari RMSE[[6](https://www.statisticshowto.com/probability-and-statistics/regression-analysis/rmse-root-mean-square-error/)]:
  ![Needed](https://user-images.githubusercontent.com/87258755/141751082-062dfe1c-9833-47ce-818c-8d52a8af3e4f.jpeg)

  Pada model ini, saya menggunakan 25 epochs, dan berikut adalah hasil dari metriksnya:

 ![14th](https://user-images.githubusercontent.com/87258755/141751150-156ddfe0-6eff-479e-8122-441be1f14737.png)

 Dapat dilihat bahwa RMSE ada dibawah 20% (sekitar 0.1799). RMSE tersebut memang besar, tetapi model tersebut masih dapat digunakan.

Perlu diingat bahwa, Cosine Similarity dapat bekerja dengan sempurna (prediksi 100%), dan RMSE dibawah 20%. Berdasarkan kedua metriks yang digunakan untuk model kali ini, dapat dideklarasikan bahwa model ini dapat digunakan. 

Oleh sebab kedua model mekerja, dapat diruangkum semua penjelasan bahwa kedua model ini bisa digunakan untuk sistem rekomendasi berbasis *collaborative filtering* dan *content-based filtering*.

## Reference

* [Recommendation Systems: Principles, Methods and Evaluation](https://www.sciencedirect.com/science/article/pii/S1110866515000341#:~:text=Recommender%20system%20has%20the%20ability,online%20shopping%20environment%20%5B4%5D.)

* [What is Content-Based Filtering?](https://www.educative.io/edpresso/what-is-content-based-filtering)

* [Content-Based Filtering Advantages & Disadvantages](
  https://developers.google.com/machine-learning/recommendation/content-based/summary)

* [Collaborative Filtering](https://developers.google.com/machine-learning/recommendation/collaborative/basics)

* [Collaborative Filtering Advantages & Disadvantages](
  https://developers.google.com/machine-learning/recommendation/collaborative/summary)

* [Neural Network Embeddings Explained](
  https://towardsdatascience.com/neural-network-embeddings-explained-4d028e6f0526)

* [What is Root Mean Square Error (RMSE)](https://www.statisticshowto.com/probability-and-statistics/regression-analysis/rmse-root-mean-square-error/)

* [Movie Lens Dataset](https://www.kaggle.com/aigamer/movie-lens-dataset)

  







