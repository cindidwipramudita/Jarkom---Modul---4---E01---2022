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
   
     ### A1
     
     - Atur IP pada *interface* **The Minister** yang mengarah ke *client* **Guideau** dengan `10.22.0.1` dan *subnet mask* `255.255.252.0`.
     
       ![image](https://user-images.githubusercontent.com/87058985/204077205-21a5dcca-79f3-4720-9262-5064678b0d9e.png)
     
     - Atur IP pada *client* **Guideau** yang mengarah ke **The Minister** dengan `10.22.0.2` dan *subnet mask* `255.255.252.0`.

       ![image](https://user-images.githubusercontent.com/87058985/204077291-6e7e277a-05cc-4d43-8898-f9688ca139dc.png)
       
     ### A2
     
     - Atur IP pada *interface* **Johan** yang mengarah ke **Phanora** dengan `10.22.8.2` dan *subnet mask* `255.255.255.0`.

      ![image](https://user-images.githubusercontent.com/87058985/204077538-66ead05c-2759-43ec-b07e-ab3cc014c664.png)
      
     - Atur IP pada **Phanora** yang mengarah ke **The Dauntless** dengan `10.22.8.3` dan *subnet mask* `255.255.255.0`.

       ![image](https://user-images.githubusercontent.com/87058985/204077621-cafe3afa-eebf-4514-9eb4-ab867bf9dff5.png)
       
     - Atur IP pada *interface* **The Dauntless** yang mengarah ke **Johan** dengan `10.22.8.1` dan *subnet mask* `255.255.255.0`.

      ![image](https://user-images.githubusercontent.com/87058985/204077700-a076bd08-7ec9-4866-9017-7de5265e5d69.png)
      
      ### A3
     
     - Atur IP pada *interface* **The Minister** yang mengarah ke *client* **The Dauntless** dengan `10.22.11.193` dan *subnet mask* `255.255.255.25`.
     
       ![image](https://user-images.githubusercontent.com/87058985/204077943-74c1bb2e-807e-4989-8d9f-d5e4f3b73e01.png)
     
     - Atur IP pada *client* **The Dauntless** yang mengarah ke **The Minister** dengan `10.22.11.194` dan *subnet mask* `255.255.255.252`.

       ![image](https://user-images.githubusercontent.com/87058985/204077970-df0de6a0-58db-402a-9a5c-a9a94b84e3df.png)
       
      ### A4
     
     - Atur IP pada *interface* **The Minister** yang mengarah ke *client* **The Order** dengan `10.22.11.197` dan *subnet mask* `255.255.255.25`.
     
       ![image](https://user-images.githubusercontent.com/87058985/204078086-21443bee-1e48-4ccc-842d-f583346182e2.png)
     
     - Atur IP pada *client* **The Order** yang mengarah ke **The Minister** dengan `10.22.11.198` dan *subnet mask* `255.255.255.252`.

       ![image](https://user-images.githubusercontent.com/87058985/204078110-5b6dcad1-c4bd-4c33-8568-a31bfe3645bc.png)
       
      ### A5
     
     - Atur IP pada *interface* **The Order** yang mengarah ke *client* **Ashaf** dengan `10.22.11.129` dan *subnet mask* `255.255.255.25`.
     
       ![image](https://user-images.githubusercontent.com/87058985/204078227-94c66e14-b5b2-4149-8e90-68565783c074.png)
     
     - Atur IP pada *client* **Ashaf** yang mengarah ke **The Order** dengan `10.22.11.130` dan *subnet mask* `255.255.255.252`.

       ![image](https://user-images.githubusercontent.com/87058985/204078248-e239f2bb-4e32-4bdf-ac25-6e8319e24d97.png)

              
     ## Hasil

     <img src="https://user-images.githubusercontent.com/37539546/143685713-49463581-e81c-475f-8f7b-19a229a99fba.JPG" width="600">

## Kendala
- CPT agak kurang responsif/konsisten sehingga butuh beberapa kali pengiriman untuk mendapatkan pesan *success*.
- Beberapa *node* pada GNS3 masih belum bisa melakukan *ping* sehingga pengerjaan GNS3 untuk CIDR tidak selesai.
