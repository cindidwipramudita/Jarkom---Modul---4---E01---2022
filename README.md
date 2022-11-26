# Jarkom Modul 4 A08 - 2021

Anggota:
-   5025201002 - Tegar Ganang Satrio Priambodo
-   5025201042 - Cindi Dwi Pramudita

## Narasi Soal

![image](https://user-images.githubusercontent.com/87058985/204070973-b9b54efe-6618-46fe-a7db-2a0fd119052c.png)


1. Soal shift dikerjakan pada Cisco Packet Tracer dan GNS3 menggunakan metode perhitungan CLASSLESS yang berbeda. Keterangan: Bila di CPT menggunakan VLSM, maka di GNS3 menggunakan CIDR atau Sebaliknya
    
2. Jika tidak ada pemberitahuan revisi soal dari asisten, berarti semua soal BERSIFAT BENAR dan DAPAT DIKERJAKAN.
    
3. Untuk di GNS3 CLOUD merupakan NAT1 jangan sampai salah agar bisa terkoneksi internet.
    
4. Pembagian IP menggunakan Prefix IP yang telah ditentukan pada modul pengenalan
    
5. Pembagian IP dan routing harus SE-EFISIEN MUNGKIN.
    
6. Gambar topologi yang lebih jelas dapat diakses pada link berikut https://intip.in/6MGm

## Jawaban

## VLSM (*Variable Length Subnet Masking*)
   - Pembagian *subnet* (*subnetting*) terhadap topologi
   
   ![image](https://user-images.githubusercontent.com/87058985/204071065-9f3c9b1b-6d61-4cd2-826e-70dc00e2e4d1.png)

   - Penentuan jumlah alamat IP yang dibutuhkan tiap *subnet* dan ***labelling netmask*** berdasarkan jumlah IP. Berdasarkan hasil perhitungan, maka menggunakan *length* **/20** untuk *netmask*-nya.

     ![image](https://user-images.githubusercontent.com/87058985/204071210-a409f091-a9a1-494e-bdbf-93a12fa0a399.png)
     ![image](https://user-images.githubusercontent.com/87058985/204071230-eb950c2a-e85e-40b9-9082-feec7582c3e3.png)

     
   - Pembuatan ***tree subnet*** untuk nantinya membagi IP berdasarkan **NID** dan ***netmask***-nya.

![image](https://user-images.githubusercontent.com/87058985/204075543-6067cd8b-ecc7-4200-91b2-3d90071321a6.png)

     
   - Pembagian IP dan *netmask* dengan tabel berdasarkan ***tree subnet*** yang sudah dibuat.
  
![image](https://user-images.githubusercontent.com/87058985/204075566-9b1c692e-3de6-49e1-acda-88153157305e.png)

![image](https://user-images.githubusercontent.com/87058985/204075583-37a7eeac-6f15-4c48-a8fb-c7a8417e28b9.png)

![image](https://user-images.githubusercontent.com/87058985/204075599-c294976b-9b76-4bb4-a372-f90f3caa03cf.png)

![image](https://user-images.githubusercontent.com/87058985/204075611-35c68ac8-edd7-43e3-8d83-8f763b651df5.png)


## CIDR (*Classless Inter Domain Routing*)
   - Pembagian *subnet* (*subnetting*) terhadap topologi
 
 ![image](https://user-images.githubusercontent.com/87058985/204075757-902ef881-c291-4454-b712-44e6428c2217.png)

   - Penggabungan *subnet* paling bawah dalam topologi. Paling bawah di sini berarti paling jauh dari **internet** (*cloud*). Sebagai contoh di bawah **A7 dan A3** digabungkan menjadi **B1**, **A8 dan A1** digabungkan menjadi **B2**, **A6 dan A9** digabungkan menjadi **B3**. *Subnet* yang digabung tersebut akan membentuk sebuah *subnet* lebih besar dari *subnet*-*subnet* kecil yang ada di dalamnya. Penggabungan dilakukan terus sampai mencakup 1 topologi yang dimiliki.
   - Untuk penentuan *netmask* per *subnet*, didapat dari *netmask* yang 1 tingkat di atas *subnet* **terbesar** yang digabungkan. Sebagai contoh **A8 dan A1** jika digabung, *netmask* terbesarnya adalah **/21**, maka *netmask* untuk *subnet* **B2** adalah **/20** karena setingkat di atasnya.
   
   ![image](https://user-images.githubusercontent.com/87058985/204075769-3cfaea30-cead-43fb-b204-198359f519ce.png)

 

## VLSM dengan CPT (Cisco Packet Tracer)

   - Pembuatan topologi baru
   
     <img src="https://user-images.githubusercontent.com/37539546/143675534-6799685d-091e-4f80-8778-8ba6d0306f7b.PNG" width="600">

   - ***Subnetting*** dan ***routing***
   
     ### A2
     
     - Atur IP pada *interface* **FOOSHA** yang mengarah ke *client* **BLUENO** dengan `10.3.8.1` dan *subnet mask* `255.255.252.0`.
     
       <img src="https://user-images.githubusercontent.com/37539546/143676218-8bebdc9d-07a9-4688-a5f7-179aae1b5124.JPG" width="600">
     
     - Atur IP pada *client* **BLUENO** yang mengarah ke **FOOSHA** dengan `10.3.8.2` dan *subnet mask* `255.255.252.0` serta *default gateway* `10.3.8.1`.

       <img src="https://user-images.githubusercontent.com/37539546/143676410-6de5336b-9b03-4044-aa40-fef1ddbae61d.JPG" width="600">
       
     ### A14
     
     - Atur IP pada *interface* **FOOSHA** yang mengarah ke *client* **DORIKI** dengan `10.3.27.161` dan *subnet mask* `255.255.255.252`.

       <img src="https://user-images.githubusercontent.com/37539546/143676488-d7aa10c3-f7d3-4e5d-bebe-3d7b08d458fe.JPG" width="600">
     
     - Atur IP pada *client* **DORIKI** yang mengarah ke **FOOSHA** dengan `10.3.27.162` dan *subnet mask* `255.255.255.252` serta *default gateway* `10.3.27.161`.

       <img src="https://user-images.githubusercontent.com/37539546/143676531-30c8fb9e-1dd1-4604-b814-77552bb3360b.JPG" width="600">
   
     ### A12
     
     - Atur IP pada *interface* **FOOSHA** yang mengarah ke *router* **GUANHAO** dengan `10.3.27.153` dan *subnet mask* `255.255.255.252`.

       <img src="https://user-images.githubusercontent.com/37539546/143676650-3f2da1c2-43f5-4ee5-913b-1f909a76bcd2.JPG" width="600">
     
     - Atur IP pada *interface* **GUANHAO** yang mengarah ke *router* **FOOSHA** dengan `10.3.27.154` dan *subnet mask* `255.255.255.252`.

       <img src="https://user-images.githubusercontent.com/37539546/143676700-325bb260-2466-4519-92e9-fad63d304343.JPG" width="600">
       
     - Tambahkan *default routing* yang mengarah ke **FOOSHA** pada *client* **GUANHAO**.

       <img src="https://user-images.githubusercontent.com/37539546/143676835-d2e747ce-1212-4da1-bb5c-adb382cbe5c6.JPG" width="600">
       
     ### A5
     
     - Atur IP pada *interface* **GUANHAO** yang mengarah ke *client* **JABRA** dengan `10.3.16.1` dan *subnet mask* `255.255.252.0`.

       <img src="https://user-images.githubusercontent.com/37539546/143676964-fdf8eae9-ac50-4faf-8650-309725d7f5b2.JPG" width="600">
     
     - Atur IP pada *client* **JABRA** yang mengarah ke **GUANHAO** dengan `10.3.16.2` dan *subnet mask* `255.255.252.0` serta *default gateway* `10.3.16.1`.

       <img src="https://user-images.githubusercontent.com/37539546/143677001-9502419b-18e1-41b4-9434-7ffa113e45f3.JPG" width="600">
       
     - Tambahkan *static routing* yang menuju jaringan yang digunakan *client* **JABRA** melalui *router* **GUANHAO** pada **FOOSHA**.

       <img src="https://user-images.githubusercontent.com/37539546/143677127-95f3a0d1-5ec7-4b94-b089-271509878c38.JPG" width="600">
       
     ### A6
     
     - Atur IP pada *interface* **GUANHAO** yang mengarah ke *client* **MAINGATE** dengan `10.3.24.1` dan *subnet mask* `255.255.254.0`.

       <img src="https://user-images.githubusercontent.com/37539546/143677174-6008dc8e-c89d-4b92-8674-b64fbd2096b3.JPG" width="600">

     - Atur IP pada *client* **MAINGATE** yang mengarah ke **GUANHAO** dengan `10.3.24.2` dan *subnet mask* `255.255.254.0` serta *default gateway* `10.3.24.1`.

       <img src="https://user-images.githubusercontent.com/37539546/143677213-2e98e1fe-f977-4c0b-9cf5-3c1fe767dc10.JPG" width="600">
       
     - Tambahkan *static routing* yang menuju jaringan yang digunakan *client* **MAINGATE** melalui *router* **GUANHAO** pada **FOOSHA**.

       <img src="https://user-images.githubusercontent.com/37539546/143677269-678625ff-0697-4884-8737-abd7e889c040.JPG" width="600">
       
     - Atur IP pada *interface* **ALABASTA** yang mengarah ke *router* **GUANHAO** dengan `10.3.24.3` dan *subnet mask* `255.255.254.0`.

       <img src="https://user-images.githubusercontent.com/37539546/143677321-cf2e0fb3-e912-4de0-9a44-3f002b9b1a48.JPG" width="600">
     
     - Tambahkan *default routing* yang mengarah ke **GUANHAO** pada *router* **ALABASTA**.

       <img src="https://user-images.githubusercontent.com/37539546/143677363-d6258334-e439-4f18-92e9-4e7f4fb03f89.JPG" width="600">
       
     ### A9
     
     - Atur IP pada *interface* **ALABASTA** yang mengarah ke *client* **JORGE** dengan `10.3.27.129` dan *subnet mask* `255.255.255.240`.

       <img src="https://user-images.githubusercontent.com/37539546/143677413-ea09f100-1fd9-4009-ab31-5833cc16b25e.JPG" width="600">

     - Atur IP pada *client* **JORGE** yang mengarah ke **ALABASTA** dengan `10.3.27.130` dan *subnet mask* `255.255.255.240` serta *default gateway* `10.3.27.129`.

       <img src="https://user-images.githubusercontent.com/37539546/143677458-7815aa2a-9af1-4ded-bc67-b9ca7a6a20df.JPG" width="600">

     - Tambahkan *static routing* yang menuju jaringan yang digunakan *client* **JORGE** melalui *router* **ALABASTA** pada **GUANHAO**.

       <img src="https://user-images.githubusercontent.com/37539546/143677499-9dfcd99a-d6da-4f68-8138-f4f97774a2df.JPG" width="600">

     - Tambahkan *static routing* yang menuju jaringan yang digunakan *client* **JORGE** melalui *router* **GUANHAO** pada **FOOSHA**.

       <img src="https://user-images.githubusercontent.com/37539546/143677562-82797495-aff0-496f-a7ad-d1d62f5491ec.JPG" width="600">

     ### A13
     
     - Atur IP pada *interface* **GUANHAO** yang mengarah ke *router* **OIMO** dengan `10.3.27.157` dan *subnet mask* `255.255.255.252`.

       <img src="https://user-images.githubusercontent.com/37539546/143677590-3c4f1c6c-30c4-4318-b422-f57efb546a2e.JPG" width="600">

     - Atur IP pada *client* **OIMO** yang mengarah ke **GUANHAO** dengan `10.3.27.158` dan *subnet mask* `255.255.255.252`.

       <img src="https://user-images.githubusercontent.com/37539546/143677624-ea5bdeec-9b92-45da-91b2-6b30eb3aba65.JPG" width="600">

     - Tambahkan *static routing* yang menuju jaringan yang digunakan **OIMO** melalui *router* **GUANHAO** pada **FOOSHA**.

       <img src="https://user-images.githubusercontent.com/37539546/143677758-02b24649-8f94-4483-8f06-16ac3e77eafa.JPG" width="600">
     
     - Tambahkan *default routing* yang mengarah ke **GUANHAO** pada *router* **OIMO**.

       <img src="https://user-images.githubusercontent.com/37539546/143677698-6dcbc073-34f3-4f03-b1d2-e2dddcfc8485.JPG" width="600">
     
     ### A7
     
     - Atur IP pada *interface* **OIMO** yang mengarah ke *client* **ENIESLOBBY** dengan `10.3.26.1` dan *subnet mask* `255.255.255.0`.

       <img src="https://user-images.githubusercontent.com/37539546/143677927-08df19c6-33dc-4789-a7c2-5b57eaefd41a.JPG" width="600">

     - Atur IP pada **ENIESLOBBY** yang mengarah ke *router* **OIMO** dengan `10.3.26.2` dan *subnet mask* `255.255.255.0` serta *default gateway* `10.3.26.1`.

       <img src="https://user-images.githubusercontent.com/37539546/143677958-58e79a87-c291-4fcb-b8c7-d877c72e05b0.JPG" width="600">

     - Tambahkan *static routing* yang menuju jaringan yang digunakan *client* **ENIESLOBBY** melalui *router* **OIMO** pada **GUANHAO**.

       <img src="https://user-images.githubusercontent.com/37539546/143678030-d09b9793-9006-4bcf-a650-58adb5b266b3.JPG" width="600">
     
     - Tambahkan *static routing* yang menuju jaringan yang digunakan *client* **ENIESLOBBY** melalui *router* **GUANHAO** pada **FOOSHA**.

       <img src="https://user-images.githubusercontent.com/37539546/143678089-070bab1e-6544-4996-9d16-9b1f3a6b18e8.JPG" width="600">
       
     - Atur IP pada *interface* **SEASTONE** yang mengarah ke *router* **OIMO** dengan `10.3.26.3` dan *subnet mask* `255.255.255.0`.

       <img src="https://user-images.githubusercontent.com/37539546/143678148-055106e6-fc62-4392-a023-b81a8612db46.JPG" width="600">
       
     - Tambahkan *default routing* yang mengarah ke **OIMO** pada *router* **SEASTONE**.

       <img src="https://user-images.githubusercontent.com/37539546/143678215-9eb11b08-2ef3-4ba2-ab2f-f3cd1e564447.JPG" width="600">
       
     ### A15
     
     - Atur IP pada *interface* **OIMO** yang mengarah ke *server* **FUKUROU** dengan `10.3.27.165` dan *subnet mask* `255.255.255.252`.

       <img src="https://user-images.githubusercontent.com/37539546/143678276-464ddcb9-4b72-43a9-858b-d5c97f202c6a.JPG" width="600">

     - Atur IP pada *server* **FUKUROU** yang mengarah ke **OIMO** dengan `10.3.27.166` dan *subnet mask* `255.255.255.252` serta *default gateway* `10.3.27.165`.

       <img src="https://user-images.githubusercontent.com/37539546/143678367-8ca72993-d12f-451f-9436-4e434d1421f7.JPG" width="600">
       
     - Tambahkan *static routing* yang menuju jaringan yang digunakan *server* **FUKUROU** melalui *router* **OIMO** pada **GUANHAO**.

       <img src="https://user-images.githubusercontent.com/37539546/143678517-15d275a6-1a76-4ab7-9884-c9e42508d414.JPG" width="600">
       
     - Tambahkan *static routing* yang menuju jaringan yang digunakan *server* **FUKUROU** melalui *router* **GUANHAO** pada **FOOSHA**.

       <img src="https://user-images.githubusercontent.com/37539546/143678424-d7d3d85e-c74c-464a-8d45-7e6f863e8ac4.JPG" width="600">

     ### A3
     
     - Atur IP pada *interface* **SEASTONE** yang mengarah ke *client* **ELENA** dengan `10.3.20.1` dan *subnet mask* `255.255.252.0`.

       <img src="https://user-images.githubusercontent.com/37539546/143678664-679d2543-fa8a-4957-ba5f-d7827c650206.JPG" width="600">

     - Atur IP pada *client* **ELENA** yang mengarah ke **SEASTONE** dengan `10.3.20.2` dan *subnet mask* `255.255.252.0` serta *default gateway* `10.3.20.1`.

       <img src="https://user-images.githubusercontent.com/37539546/143678706-99499e85-ebbb-4d95-a9aa-79eb65632986.JPG" width="600">

     - Tambahkan *default routing* yang mengarah ke **OIMO** pada *router* **SEASTONE**.

       <img src="https://user-images.githubusercontent.com/37539546/143678215-9eb11b08-2ef3-4ba2-ab2f-f3cd1e564447.JPG" width="600">
       
     - Tambahkan *static routing* yang menuju jaringan yang digunakan *client* **ELENA** melalui *router* **OIMO** pada **GUANHAO**.

       <img src="https://user-images.githubusercontent.com/37539546/143678790-b5d2f6c6-dc9c-4614-a151-18dd3f38da47.JPG" width="600">
       
     - Tambahkan *static routing* yang menuju jaringan yang digunakan *client* **ELENA** melalui *router* **GUANHAO** pada **FOOSHA**.

       <img src="https://user-images.githubusercontent.com/37539546/143679439-2a0e240e-e3ee-48d2-96c8-752bc5581e0b.JPG" width="600">

     ### A11
     
     - Atur IP pada *interface* **FOOSHA** yang mengarah ke *router* **WATER7** dengan `10.3.27.149` dan *subnet mask* `255.255.255.252`.

       <img src="https://user-images.githubusercontent.com/37539546/143680007-fe301afd-8b84-4c4c-8973-935b72764514.JPG" width="600">

     - Atur IP pada *interface* **WATER7** yang mengarah ke *router* **FOOSHA** dengan `10.3.27.150` dan *subnet mask* `255.255.255.252`.

       <img src="https://user-images.githubusercontent.com/37539546/143678945-bc12f009-3206-4a09-ae1b-e404ef0ac756.JPG" width="600">

     - Tambahkan *default routing* yang mengarah ke **FOOSHA** pada *router* **WATER7**.

       <img src="https://user-images.githubusercontent.com/37539546/143678990-efb447e2-945a-4660-80bc-44a0c333779e.JPG" width="600">
       
     ### A4
     
     - Atur IP pada *interface* **WATER7** yang mengarah ke *client* **CIPHER** dengan `10.3.12.1` dan *subnet mask* `255.255.252.0`.

       <img src="https://user-images.githubusercontent.com/37539546/143679073-2145a4cd-088c-4d47-9884-529de2babd46.JPG" width="600">

     - Atur IP pada *interface* **CIPHER** yang mengarah ke **WATER7** dengan `10.3.12.2` dan *subnet mask* `255.255.252.0` serta *default gateway* `10.3.12.1`.

       <img src="https://user-images.githubusercontent.com/37539546/143679136-701cda15-a7e8-4a7f-8db9-d6301f4263b4.JPG" width="600">

     - Tambahkan *static routing* yang menuju jaringan yang digunakan *client* **CIPHER** melalui *router* **WATER7** pada **FOOSHA**.

       <img src="https://user-images.githubusercontent.com/37539546/143678839-8c751434-fdb4-4fc7-b837-370de8881685.JPG" width="600">

     ### A10
     
     - Atur IP pada *interface* **WATER7** yang mengarah ke *router* **PUCCI** dengan `10.3.27.145` dan *subnet mask* `255.255.255.252`.

       <img src="https://user-images.githubusercontent.com/37539546/143679219-cd4ed4a4-31b9-44b8-9b95-803eb3f88f16.JPG" width="600">

     - Atur IP pada *interface* **PUCCI** yang mengarah ke *router* **WATER7** dengan `10.3.27.146` dan *subnet mask* `255.255.255.252`.

       <img src="https://user-images.githubusercontent.com/37539546/143679236-76007745-b440-4849-a744-01ddbcc1a4dd.JPG" width="600">

     - Tambahkan *default routing* yang mengarah ke **WATER7** pada *router* **PUCCI**.

       <img src="https://user-images.githubusercontent.com/37539546/143679286-24016dc5-8f97-4543-8459-381a3889db0e.JPG" width="600">

     - Tambahkan *static routing* yang menuju jaringan yang digunakan **PUCCI** melalui *router* **WATER7** pada **FOOSHA**.

       <img src="https://user-images.githubusercontent.com/37539546/143679184-be8d58a8-cf7c-43fd-a446-57fffcafdadc.JPG" width="600">
       
     ### A8
     
     - Atur IP pada *interface* **PUCCI** yang mengarah ke *client* **JIPANGU** dengan `10.3.27.1` dan *subnet mask* `255.255.255.128`.

       <img src="https://user-images.githubusercontent.com/37539546/143679558-19f60130-dc8e-4ff6-941b-3fd2bfaaaf5f.JPG" width="600">

     - Atur IP pada *interface* **JIPANGU** yang mengarah ke **PUCCI** dengan `10.3.27.2` dan *subnet mask* `255.255.255.128` serta *default gateway* `10.3.27.1`.

       <img src="https://user-images.githubusercontent.com/37539546/143679594-776d9e5c-fc41-489e-8b32-b0760bcf052d.JPG" width="600">

     - Tambahkan *static routing* yang menuju jaringan yang digunakan *client* **JIPANGU** melalui *router* **PUCCI** pada **WATER7**.

       <img src="https://user-images.githubusercontent.com/37539546/143679680-2711b06a-fd72-4e76-a39d-495869e4ca74.JPG" width="600">
       
     - Tambahkan *static routing* yang menuju jaringan yang digunakan **PUCCI** melalui *router* **WATER7** pada **FOOSHA**.

       <img src="https://user-images.githubusercontent.com/37539546/143680286-aed1e905-c528-4cb2-988d-c48874c58365.JPG" width="600">

     ### A1
     
     - Atur IP pada *interface* **PUCCI** yang mengarah ke jaringan **A1** dengan `10.3.0.1` dan *subnet mask* `255.255.248.0`.

       <img src="https://user-images.githubusercontent.com/37539546/143679770-0e92032f-31c2-4157-aa53-fc6866943596.JPG" width="600">

     - Atur IP pada *interface* **CALMBELT** yang mengarah ke **PUCCI** dengan `10.3.0.2` dan *subnet mask* `255.255.248.0` serta *default gateway* `10.3.0.1`.

       <img src="https://user-images.githubusercontent.com/37539546/143679818-57f07ed6-9297-412c-a5d1-1b55750efdef.JPG" width="600">
       
     - Atur IP pada *interface* **COURTYARD** yang mengarah ke **PUCCI** dengan `10.3.0.3` dan *subnet mask* `255.255.248.0` serta *default gateway* `10.3.0.1`.

       <img src="https://user-images.githubusercontent.com/37539546/143679863-6ed11afa-e1f2-4377-9a02-c5f28ef5ff7b.JPG" width="600">

     - Tambahkan *static routing* yang menuju jaringan **A1** melalui *router* **PUCCI** pada **WATER7**.

       <img src="https://user-images.githubusercontent.com/37539546/143680053-a73a276a-aef4-4439-bd55-0d730bf7951a.JPG" width="600">

     - Tambahkan *static routing* yang menuju jaringan **A1** *router* **WATER7** pada **FOOSHA**.

       <img src="https://user-images.githubusercontent.com/37539546/143680169-7f076a2c-7675-48d0-8e82-6cb776947402.JPG" width="600">
       
     ## Hasil

     <img src="https://user-images.githubusercontent.com/37539546/143685713-49463581-e81c-475f-8f7b-19a229a99fba.JPG" width="600">

## Kendala
- CPT agak kurang responsif/konsisten sehingga butuh beberapa kali pengiriman untuk mendapatkan pesan *success*.
- Beberapa *node* pada GNS3 masih belum bisa melakukan *ping* sehingga pengerjaan GNS3 untuk CIDR tidak selesai.
