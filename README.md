# Proyek Pertama Machine Learning Terapan - *Car Price Prediction*
**Dibuat oleh Aksel E**

Berikut merupakan Proyek Pertama mengenai *Predictive Analysis* untuk memprediksi harga mobil di Polandia.

## Domain Proyek
### Latar Belakang
<br>
<div><img src="https://images.pexels.com/photos/210182/pexels-photo-210182.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2"></div>
<br>
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

  - **fuel**
  
    Terdapat 6 jenis bahan bakar yang digunakan dalam *dataset* ini dengan pemakaian bahan bakar terbanyak ialah *Gasoline* dan *Diesel*.
    
    <img width="290" alt="image" src="https://user-images.githubusercontent.com/116968275/216534073-f85ba1bd-fce6-40b7-8d80-1966e9e36eaf.png">

    Melihat pemerataan data yang kurang baik serta masih kurang banyak pemakaian bahan bakar selain *Gasoline* dan *Diesel*, maka data mobil yang menggunakan bahan bakar selain *Gasoline* dan *Diesel* akan dihapus.

    <img width="289" alt="image" src="https://user-images.githubusercontent.com/116968275/216534162-d36b171a-e890-44cf-af6b-f4ff08b839d0.png">

  - **city**

    Dalam kolom *city* ini, terdapat 4224 kota yang terdaftar dalam *dataset*. Dengan melihat jumlah kota yang sangat banyak ini, maka kolom *city* akan dihapus dan digantikan oleh kolom *province* yang dapat menggantikan fungsi kolom *city*.
    
    <img width="239" alt="image" src="https://user-images.githubusercontent.com/116968275/216534966-9a692248-f3ec-4c42-9057-01fcf21cac1d.png">
    <br>
    <img width="288" alt="image" src="https://user-images.githubusercontent.com/116968275/216535042-8f34df7a-9520-4d9b-882c-6270ae76ccb9.png">

  - **province**

    Dalam kolom *province*, terdapat 22 provinsi yang terdaftar. Jika kita lihat kembali, terdapat satu provinsi dengan nama "(" yang dimana data tersebut sudah pasti berupa *error*.
    
    <img width="289" alt="image" src="https://user-images.githubusercontent.com/116968275/216535766-073d1039-6384-4b06-99e4-082e96944fe7.png">

    Dengan melihat pemerataan data yang kurang baik juga, maka provinsi dengan jumlah data dibawah 2000 akan dihapus.
    
    <img width="289" alt="image" src="https://user-images.githubusercontent.com/116968275/216535927-62128eb3-c71a-4ac1-a7fc-0134f995a0a6.png">

- **Data Numerikal**
  
    <img width="666" alt="image" src="https://user-images.githubusercontent.com/116968275/216536393-e85da033-9caa-476f-9504-ee5f25bb10f8.png">

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

      Beberapa merek mobil memiliki pengaruh terhadap harga mobil, tetapi kebanyakan merek mobil tersebut merupakan sebuah *luxury brand* dimana harga mobilnya sudah pasti tinggi (*Mercedes Benz*, *BMW*, *Audi*, dan *Volvo*).
      
    - **Korelasi antara *price* dengan *fuel***

      <img width="960" alt="image" src="https://user-images.githubusercontent.com/116968275/216544047-b2b3f154-0176-4ba2-b709-6f2e5e7b89e9.png">

      Jenis bahan bakar tidak memiliki pengaruh terhadap harga mobil.
      
    - **Korelasi antara *price* dengan *province***

      <img width="960" alt="image" src="https://user-images.githubusercontent.com/116968275/216544137-e0222b9f-f30a-491c-85e2-fab8c61cbee2.png">

      Provinsi asal mobil tidak memiliki pengaruh terhadap harga mobil, walaupun ada beberapa provinsi yang memiliki harga mobil lebih tinggi dibandingkan dengan provinsi lain.

- **Data Numerikal**
  - ***Pairplot***

    <img width="449" alt="image" src="https://user-images.githubusercontent.com/116968275/216545855-072042ee-a49f-4f69-98f4-bfa726bb69c2.png">

    Berdasarkan *Pairplot* di atas, terlihat jika nilai kapasitas mesin(*vol_engine*) tidak memiliki pengaruh terhadap harga mobil, dikarenakan sebaran data yang terlihat acak dan tidak memiliki pola. Untuk tahun produksi mobil (*year*), terlihat jika semakin tinggi tahun mobil (Mendekati tahun sekarang) maka akan semakin tinggi pula harganya dan dibuktikan dengan adanya pola data positif. Untuk jarak tempuh mobil (*mileage*), datanya memiliki korelasi negatif dengan harga mobil yang dimana semakin tinggi jarak tempuh mobil maka harganya akan semakin rendah.
    
  - ***Heat Map***

    <img width="419" alt="image" src="https://user-images.githubusercontent.com/116968275/216545921-58f58eda-c559-49f4-817f-ec484be84ef7.png">

    Jika kita lihat berdasarkan *Heat Map* yang sudah dibuat, *Heat Map* ini menjadi bukti penguat dari apa yang sudah disimpulkan dari *Pairplot* yang telah dibuat. Terlihat jika nilai tahun produksi mobil (*year*) memiliki korelasi positif terhadap harga mobil dan jarak tempuh mobil (*mileage*) memiliki korelasi negatif terhadap harga mobil.
    
## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan kelebihan dan kekurangan dari setiap algoritma yang digunakan.
- Jika menggunakan satu algoritma pada solution statement, lakukan proses improvement terhadap model dengan hyperparameter tuning. **Jelaskan proses improvement yang dilakukan**.
- Jika menggunakan dua atau lebih algoritma pada solution statement, maka pilih model terbaik sebagai solusi. **Jelaskan mengapa memilih model tersebut sebagai model terbaik**.

## Evaluation
Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.

Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan
- Menjelaskan hasil proyek berdasarkan metrik evaluasi

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
