# Proyek Pertama Machine Learning Terapan - *Car Price Prediction*
**Dibuat oleh Aksel E**

Berikut merupakan Proyek Pertama mengenai *Predictive Analysis* untuk memprediksi harga mobil di Polandia.

## Domain Proyek
### Latar Belakang
<br>
<div><img src="https://images.pexels.com/photos/210182/pexels-photo-210182.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2"></div>
<br>

Gambar 1. Kumpulan Kendaraan di Jalanan Sore Hari

Ditengah kondisi zaman yang semakin berkembang pesat, kebutuhan setiap manusia pun akan semakin bertambah demi memenuhi kebutuhan harian. Salah satu kebutuhan yang dibutuhkan banyak orang ialah kendaraan. Banyak orang lebih memilih mempunyai kendaraan berupa mobil dikarenakan memiliki kenyamanan dan fungsionalitas yang lebih baik. Dengan melihat harga mobil yang semakin tinggi, beberapa orang lebih memilih membeli mobil dengan kondisi bekas dikarenakan harga yang lebih murah.
<br><br>

*Machine Learning* adalah cabang dari ilmu data yang berfokus pada pembuatan sistem yang dapat mempelajari dan membuat prediksi berdasarkan data. Dalam hal memprediksi harga mobil, dapat dibuat sebuah model *Machine Learning* yang dapat digunakan untuk mempelajari data harga mobil dan faktor-faktor yang mempengaruhinya. Kemudian, model yang dibuat ini dapat membuat prediksi harga mobil baru berdasarkan data yang diberikan. Ini sangat berguna karena memungkinkan untuk membuat estimasi harga yang akurat dan cepat dibandingkan dengan metode manual.

## *Business Understanding*

### *Problem Statements*
Dengan melihat latar belakang tersebut, terdapat beberapa masalah yang didapat:
- Bagaimana melakukan pemrosesan data untuk membuat data yang baik dan dapat digunakan untuk melatih model?
- Fitur apa yang berpengaruh terhadap harga mobil?
- Model algoritma apa yang lebih baik dan memiliki akurasi yang tinggi untuk memprediksi harga mobil?

### *Goals*
Berikut beberapa solusi yang dapat dilakukan untuk menjawab pertanyaan di atas:
- Melakukan pembersihan data dengan baik hingga dapat digunakan untuk melatih model.
- Mempelajari dan melihat korelasi data agar mendapatkan fitur yang berpengaruh terhadap harga mobil.
- Mencoba dan membandingkan beberapa model algoritma dalam hal memprediksi harga mobil.

### *Solution statements*
- Melakukan analisis data dengan sistem *Univariate Analysis* dan *Multivariate Analysis* untuk melihat korelasi antar data. Gunakan juga beberapa fitur seperti *Heat Map* untuk memastikan tingkat korelasi antar data.
- Menggunakan dan membandingkan beberapa model algoritma (*K-Nearest Neighbor*, *Random Forest*, dan *AdaBoost*) serta mengubah nilai *Hyper Parameter* guna mencapai nilai akurasi yang maksimal.

## *Data Understanding*
Data yang digunakan dalam proyek ini merupakan data harga mobil di Polandia dengan beberapa karakteristik dari mobil tersebut. Dalam *dataset* ini, terdapat sekitar 118 ribu data dengan 10 kolom didalamnya. Data ini dapat diunduh dari situs Kaggle.

*Link* menuju data: [Car Price in Poland](https://www.kaggle.com/datasets/aleksandrglotov/car-prices-poland)

### Berikut merupakan beberapa kolom yang terdapat dalam *dataset* *Car Price in Poland*:
- mark : Merupakan merek dari mobil.
- model : Merupakan model dari merek mobil yang tercantum dalam kolom sebelumnya.
- generation_name : Merupakan nama generasi dari model yang tercantum dalam kolom sebelumnya.
- year : Berupa tahun berapa mobil tersebut diproduksi.
- mileage : Berupa seberapa jauh mobil tersebut telah digunakan dalam satuan Kilometer.
- vol_engine : Berupa seberapa besar kapasitas mesin yang digunakan dalam mobil tersebut.
- fuel : Merupakan jenis bahan bakar yang digunakan mobil tersebut.
- city : Merupakan kota asal mobil tersebut digunakan.
- province : Merupakan provinsi asal mobil tersebut digunakan.
- price : Harga mobil dalam satuan Polish Zloty.

Dari 10 kolom yang ada dalam *dataset*, kolom model dan generation_name tidak digunakan karena dapat digantikan dengan kolom year dan vol_engine serta tidak memiliki korelasi dengan harga mobil.

Untuk melihat korelasi antar kolom dengan harga mobil, digunakan 2 analisis berikut:

### *Univariate Analysis*:
Ini merupakan analisis yang digunakan untuk melihat jenis yang ada dalam satu kolom saja. Dalam analisis ini, data numerikal dan data kategorikal akan dipisahkan.
- **Data Kategorikal**
  - **mark**
  
    Terdapat 23 jenis merek dalam kolom mark ini, dengan merek *Audi* dan *Opel* yang memiliki data terbanyak sebesar masing-masing ~10%.
    
    <img width="288" alt="image" src="https://user-images.githubusercontent.com/116968275/216391713-709812c9-146b-4e2b-a8b9-482f57f9d7cd.png">
    
    Gambar 2. Visualisasi Penyebaran Data pada Kolom *mark*

  - **fuel**
  
    Terdapat 6 jenis bahan bakar yang digunakan dalam *dataset* ini dengan pemakaian bahan bakar terbanyak ialah *Gasoline* dan *Diesel*.
    
    <img width="290" alt="image" src="https://user-images.githubusercontent.com/116968275/216534073-f85ba1bd-fce6-40b7-8d80-1966e9e36eaf.png">
    
    Gambar 3. Visualisasi Penyebaran Data pada Kolom *fuel*

    Melihat pemerataan data yang kurang baik serta masih kurang banyak pemakaian bahan bakar selain *Gasoline* dan *Diesel*, maka data mobil yang menggunakan bahan bakar selain *Gasoline* dan *Diesel* akan dihapus.

    <img width="289" alt="image" src="https://user-images.githubusercontent.com/116968275/216534162-d36b171a-e890-44cf-af6b-f4ff08b839d0.png">
    
    Gambar 4. Visualisasi Data *Gasoline* dan *Diesel* pada Kolom *mark*

  - **city**

    Dalam kolom *city* ini, terdapat 4224 kota yang terdaftar dalam *dataset*. Dengan melihat jumlah kota yang sangat banyak ini, maka kolom *city* akan dihapus dan digantikan oleh kolom *province* yang dapat menggantikan fungsi kolom *city*.
    
    <img width="239" alt="image" src="https://user-images.githubusercontent.com/116968275/216534966-9a692248-f3ec-4c42-9057-01fcf21cac1d.png">
    
    Gambar 5. Daftar Nama Koya yang Terdaftar pada Kolom *city*
   
    <img width="288" alt="image" src="https://user-images.githubusercontent.com/116968275/216535042-8f34df7a-9520-4d9b-882c-6270ae76ccb9.png">
    
    Gambar 6. Visualisasi Penyebaran pada Data Kolom *city*

  - **province**

    Dalam kolom *province*, terdapat 22 provinsi yang terdaftar. Jika kita lihat kembali, terdapat satu provinsi dengan nama "(" yang dimana data tersebut sudah pasti berupa *error*.
    
    <img width="289" alt="image" src="https://user-images.githubusercontent.com/116968275/216535766-073d1039-6384-4b06-99e4-082e96944fe7.png">
    
    Gambar 7. Visualisasi Penyebaran pada Data Kolom *province*

    Dengan melihat pemerataan data yang kurang baik juga, maka provinsi dengan jumlah data dibawah 2000 akan dihapus.
    
    <img width="289" alt="image" src="https://user-images.githubusercontent.com/116968275/216535927-62128eb3-c71a-4ac1-a7fc-0134f995a0a6.png">
    
    Gambar 8. Visualisasi Penyebaran pada Data Kolom *province* Setelah Data Dirapihkan 

- **Data Numerikal**
  
    <img width="666" alt="image" src="https://user-images.githubusercontent.com/116968275/216536393-e85da033-9caa-476f-9504-ee5f25bb10f8.png">
    
    Gambar 9. Visualisasi Penyebaran pada Data Numerikal

    Berikut beberapa informasi yang dapat diambil dari grafik di atas:
    - Dataset ini banyak mengandung data mobil dengan tahun produksi diatas tahun 2000.
    - Kebanyakan mobil pada *dataset* ini menempuh jarak berkisar dari 10 km hingga 224000 km.
    - Semakin rendah jarak tempuh mobil, maka harga mobil itupun semakin tinggi.
    - Dataset ini banyak mengandung mobil dengan volume mesin 1000cc hingga 2000cc.

### *Multivariate Analysis*:
Ini merupakan analisis yang digunakan untuk melihat korelasi antar kolom. Dalam analisis ini, data numerikal dan data kategorikal akan dipisahkan.
- **Data Kategorikal**
    - **Korelasi antara *price* dengan *mark***

      <img width="960" alt="image" src="https://user-images.githubusercontent.com/116968275/216543954-02269cc8-f9cf-43e9-b1a6-591521cd307e.png">
      
      Gambar 10. Visualisasi Korelasi antara Kolom *price* dengan Kolom *mark*

      Beberapa merek mobil memiliki pengaruh terhadap harga mobil, tetapi kebanyakan merek mobil tersebut merupakan sebuah *luxury brand* dimana harga mobilnya sudah pasti tinggi (*Mercedes Benz*, *BMW*, *Audi*, dan *Volvo*).
      
    - **Korelasi antara *price* dengan *fuel***

      <img width="960" alt="image" src="https://user-images.githubusercontent.com/116968275/216544047-b2b3f154-0176-4ba2-b709-6f2e5e7b89e9.png">
      
      Gambar 11. Visualisasi Korelasi antara Kolom *price* dengan Kolom *fuel*

      Jenis bahan bakar tidak memiliki pengaruh terhadap harga mobil.
      
    - **Korelasi antara *price* dengan *province***

      <img width="960" alt="image" src="https://user-images.githubusercontent.com/116968275/216544137-e0222b9f-f30a-491c-85e2-fab8c61cbee2.png">
      
      Gambar 12. Visualisasi Korelasi antara Kolom *price* dengan Kolom *province*

      Provinsi asal mobil tidak memiliki pengaruh terhadap harga mobil, walaupun ada beberapa provinsi yang memiliki harga mobil lebih tinggi dibandingkan dengan provinsi lain.

- **Data Numerikal**
  - ***Pairplot***

    <img width="449" alt="image" src="https://user-images.githubusercontent.com/116968275/216545855-072042ee-a49f-4f69-98f4-bfa726bb69c2.png">
    
    Gambar 13. Visualisasi Penyebaran Data dengan *Pairplot* pada Data Numerikal

    Berdasarkan *Pairplot* di atas, terlihat jika nilai kapasitas mesin(*vol_engine*) tidak memiliki pengaruh terhadap harga mobil, dikarenakan sebaran data yang terlihat acak dan tidak memiliki pola. Untuk tahun produksi mobil (*year*), terlihat jika semakin tinggi tahun mobil (Mendekati tahun sekarang) maka akan semakin tinggi pula harganya dan dibuktikan dengan adanya pola data positif. Untuk jarak tempuh mobil (*mileage*), datanya memiliki korelasi negatif dengan harga mobil yang dimana semakin tinggi jarak tempuh mobil maka harganya akan semakin rendah.
    
  - ***Heat Map***

    <img width="419" alt="image" src="https://user-images.githubusercontent.com/116968275/216545921-58f58eda-c559-49f4-817f-ec484be84ef7.png">
    
    Gambar 14. Visualisasi Korelasi Data Numerikal dengan *Heat Map* pada Data Numerikal

    Jika kita lihat berdasarkan *Heat Map* yang sudah dibuat, *Heat Map* ini menjadi bukti penguat dari apa yang sudah disimpulkan dari *Pairplot* yang telah dibuat. Terlihat jika nilai tahun produksi mobil (*year*) memiliki korelasi positif terhadap harga mobil dan jarak tempuh mobil (*mileage*) memiliki korelasi negatif terhadap harga mobil.
    
## Data Preparation
Dalam bagian ini, ada beberapa hal yang akan dilakukan guna menunjang data yang baik untuk digunakan untuk melatih model.
- ***One-Hot Encoding***

  *One-Hot Encoding* merupakan suatu teknik yang digunakan untuk mengubah data kategorikal menjadi data numerik, dikarenakan model hanya bisa mengenali satu jenis data saja. Teknik ini dilakukan dengan cara menggunakan fungsi `get_dummies()` yang dapat mengubah data kategorikal menjadi kolom baru dengan data 0 atau 1.
  
  Tabel 1. *Dataset Car Price in Poland* Setelah Menggunakan *One-Hot Encoding*
  
  |   | year | mileage | vol_engine | price | mark_alfa-romeo | mark_audi | mark_bmw | mark_chevrolet | mark_citroen | mark_fiat | ... | province_Mazowieckie | province_Małopolskie | province_Podkarpackie | province_Pomorskie | province_Warmińsko-mazurskie | province_Wielkopolskie | province_Zachodniopomorskie | province_Łódzkie | province_Śląskie | province_Świętokrzyskie |
  |--:|-----:|--------:|-----------:|------:|----------------:|----------:|---------:|---------------:|-------------:|----------:|----:|---------------------:|---------------------:|----------------------:|-------------------:|-----------------------------:|-----------------------:|----------------------------:|-----------------:|-----------------:|------------------------:|
  | 0 | 2015 |  139568 |       1248 | 35900 |               0 |         0 |        0 |              0 |            0 |         0 | ... |                    1 |                    0 |                     0 |                  0 |                            0 |                      0 |                           0 |                0 |                0 |                       0 |
  | 1 | 2018 |   31991 |       1499 | 78501 |               0 |         0 |        0 |              0 |            0 |         0 | ... |                    0 |                    0 |                     0 |                  0 |                            0 |                      0 |                           0 |                0 |                1 |                       0 |
  | 5 | 2017 |  121203 |       1598 | 51900 |               0 |         0 |        0 |              0 |            0 |         0 | ... |                    1 |                    0 |                     0 |                  0 |                            0 |                      0 |                           0 |                0 |                0 |                       0 |
  | 6 | 2017 |  119965 |       1248 | 44700 |               0 |         0 |        0 |              0 |            0 |         0 | ... |                    0 |                    0 |                     0 |                  0 |                            0 |                      0 |                           0 |                0 |                0 |                       0 |
    | 7 | 2016 |  201658 |       1248 | 29000 |               0 |         0 |        0 |              0 |            0 |         0 | ... |                    0 |                    0 |                     0 |                  0 |                            0 |                      0 |                           0 |                0 |                0 |                       0 |

- ***Train-Test Split***

  *Train-Test Split* merupakan suatu fungsi yang digunakan untuk memecahkan data menjadi data latih dan data uji. Dalam pengaplikasiannya, digunakan rasio antara data latih dan data uji guna menghindari model menjadi *overfit* atau *underfit*. Dalam kasus prediksi harga mobil ini, digunakan rasio 90:10 dikarenakan terdapat ~100000 data dalam *dataset* ini.
  
  Hasil dari pembagian data latih dan data uji dengan fungsi *Train-Test Split* dengan menggunakan rasio 90:10 adalah sebagai berikut:
  - Total Data Keseluruhan: 103712
  - Total Data Latih: 93340
  - Total Data Uji: 10372
    
- **Standarisasi Data**

  Model *machine learning* dilatih menggunakan data yang sudah diproses sebelumnya agar nantinya memiliki performa dan akurasi yang baik. Model ini dapat dilatih lebih baik dan cepat jika data yang sudah kita proses sebelumnya memiliki nilai yang seragam dan memiliki skala yang relatif sama. Untuk memenuhi hal tersebut dapat digunakan fungsi `Standard_Scaler()` dari *library sklearn*. Fungsinya adalah agar data yang akan kita pakai untuk model memiliki nilai *mean* = 0 dan nilai standar deviasi = 1.
  
  Tabel 2. Hasil Standarisasi Data menggunakan fungsi `Standard_Scaler()`
  
  |       | year       | mileage    | vol_engine |
  |-------|------------|------------|------------|
  | count | 93340.0000 | 93340.0000 | 93340.0000 |
  |  mean |    -0.0000 |     0.0000 |    -0.0000 |
  |  std  |     1.0000 |     1.0000 |     1.0000 |
  |  min  |    -8.8020 |    -1.5912 |    -1.3902 |
  |  25%  |    -0.6868 |    -0.7711 |    -0.5681 |
  |  50%  |     0.0346 |     0.0600 |    -0.0772 |
  |  75%  |     0.7559 |     0.6592 |     0.2506 |
  |  max  |     1.6576 |    29.4388 |     7.8233 |

## Modeling
Pada tahap ini, akan dilakukan pengujian dan pelatihan model menggunakan 3 algoritma (*K-Nearest Neighbor*, *Random Forest*, dan *AdaBoost*)

- ***K-Nearest Neighbor***

  *K-Nearest Neighbor* merupakan salah satu algoritma yang bekerja dengan cara membandingkan jarak satu sampel dengan sampel lain dengan cara memilih jumlah k tetangga terdekat. 
  
  Dalam algoritma *K-Nearest Neighbor*, terdapat *hyperparameter* yang dapat disesuaikan guna meningkatkan performa model:
  - `n_neighbor` : Merupakan jumlah k tetangga terdekat.

  Selain itu, terdapat beberapa kelebihan dan kekurangan dari algoritma *K-Nearest Neighbor* ini:
  - **Kelebihan**

    1. Metode ini cenderung lebih sederhana dan mudah dipahami dibandingkan dengan algoritma lain.
    2. Metode ini pun tidak memerlukan pemodelan, menjadikan algoritma ini dapat memangkas waktu dalam membangun model.

  - **Kekurangan**

    1. Kinerjanya yang terhitung lambat dikarenakan harus membandingkan jarak satu sampel dengan sampel yang lain.
    2. Prediksi dari metode ini dapat sangat berubah walaupun hanya merubah nilai `n_neighbor`, maka dari itu diperlukan nilai k yang pas dan sesuai dengan data yang digunakan.

- ***Random Forest***

  *Random Forest* merukapan algoritma yang bekerja dengan cara menjalankan beberapa model sekaligus dan membandingkan hasil akhirnya. Dalam penggunaannya, algoritma *Random Forest* menggunakan banyak *decision tree* yang dibangun secara acak dari dataset yang ada. Nantinya, hasil akhir dari algoritma ini adalah gabungan dari hasil akhir beberapa *decision tree* yang telah dijalankan. 
  
  Terdapat beberapa *hyperparameter* dalam algoritma ini:
  - `n_estimator` : Ini merupakan berapa banyak *decision tree* yang akan dijalankan dalam model.
  - `max_depth` : Merupakan nilai dari seberapa dalam *decision tree* akan melakukan percabangan.
  - `random_state` : Merupakan nilai untuk mengontrol *seed* dari model yang akan dijalankan.

  Ada juga kelebihan dan kekurangan dari algoritma ini:
  - **Kelebihan**

    1. Metode ini memiliki akurasi yang tinggi dikarenakan model menjalankan beberapa *decision tree* secara bersamaan, dan dapat menghindari masalah *overfit* pada model.

  - **Kekurangan**

    1. Dalam pelatihannya, algoritma *Random Forest* memerlukan waktu yang lebih lama dikarenakan menjalankan banyak *decision tree* secara bersamaan.
  
- ***AdaBoost***

  *AdaBoost (Adapive Boost)* merupakan salah satu algoritma yang memiliki cara kerja menggabungkan beberapa model yang nantinya dapat memperbaiki akurasi dan stabilitas dari model. *AdaBoost* bekerja dengan cara menempatkan bobot lebih kepada data yang sebelumnya tidak diprediksi benar oleh model sebelumnya, nantinya model selanjutnya akan memberi fokus lebih pada data tersebut dan akhirnya meningkatkan akurasi dari model tersebut. Proses ini dilakukan berulang hingga mencapai nilai akurasi yang tinggi.
  
  Ada beberapa *hyperparameter* yang dapat diatur guna meningkatkan performa dari algoritma ini:
  - `learning_rate` : Merupakan nilai dari laju pembelajaran model.
  - `random_state` : Merupakan nilai untuk mengontrol *seed* dari model yang akan dijalankan.

  Adapun kelebihan dan kekurangan dari algoritma ini:
  - **Kelebihan**

    1. Metode ini memiliki akurasi yang tinggi jika dibandingkan dengan metode sederhana lainnya (Contohnya seperti *Random Forest*).

  - **Kekurangan**

    1. Algoritma ini biasanya rentan dengan data *outlier* dan membutuhkan waktu lama dalam proses latih dikarenakan menggabungkan beberapa jenis model dalam penggunaannya.

Dengan menggunakan ketiga algortima diatas serta mencari nilai *hyperparameter* yang paling baik, didapatkan hasil sebagai berikut:

Tabel 3. Hasil Nilai *Hyperparameter* Terbaik pada Setiap Algoritma

| Model               | *Hyperparameter* Terbaik                                   |
|---------------------|------------------------------------------------------------|
| K-Nearest Neighbor  | `n_neighbor` : 4                                           |
| AdaBoost            | `learning_rate` : 0.08, `random_state` : 55                |
| Random Forest       | `n_estimator` : 50, `max_depth` : 64, `random_state` : 55  |

## Evaluation
Untuk mengevaluasi hasil kinerja model yang telah dibangun, dalam kasus ini digunakan metrik MSE (*Mean Squared Error*). Metrik ini bekerja dengan cara melihat selisih dari nilai asli (*y_true*) dengan hasil prediksi dari masing-masing model. 

![image](https://user-images.githubusercontent.com/116968275/216582083-3a912459-5489-4e29-a7c8-4f7d0b3a12c0.png)

Gambar 15. Rumus Mencari Nilai *Mean Squared Error*

**Penjelasan**:
- MSE : *Mean Squared Error*
- yi : Nilai asli (*y_true*)
- y_pred : Nilai prediksi model

Dengan menggunakan MSE, berikut hasil dari setiap model algortima yang digunakan:

Tabel 4. Hasil Nilai *Error* pada Data Uji dan Data Latih Setiap Model Algoritma

| Model               | Train            | Test             |
|---------------------|------------------|------------------|
| K-Nearest Neighbor  | 520014.135924    | 732296.875684    |
| AdaBoost            | 1838754.256309   | 1703197.195434   |
| Random Forest       | 184651.209957    | 589524.177038    |

<img width="339" alt="image" src="https://user-images.githubusercontent.com/116968275/216583247-26c4840a-e6c8-4a5f-b40b-def19d131a00.png">

Gambar 16. Visualisasi *error* pada Data Latih dan Data Uji menggunakan Model Algoritma yang Sudah Dilatih

Berikut juga hasil prediksi dari setiap model jika dibandingkan dengan nilai *y_true* dari *dataset*:

Tabel 5. Hasil Nilai Prediksi Harga Mobil pada Setiap Model Algoritma

| Model               | Hasil Prediksi   |
|---------------------|------------------|
| y_true              | 76000            |
| K-Nearest Neighbor  | 51625            |
| AdaBoost            | 78337.3          |
| Random Forest       | 52459.8          |

Melihat hasil di atas, maka model yang menggunakan algoritma *AdaBoost* merupakan model dengan nilai akurasi yang paling tinggi serta memiliki nilai error yang paling kecil jika dibandingkan dengan model *K-Nearest Neighbor* dan *Random Forest*.
