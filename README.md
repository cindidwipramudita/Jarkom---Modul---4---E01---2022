# Jarkom Modul 4 E01 - 2022

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

![image](https://user-images.githubusercontent.com/87058985/204078465-58599bf7-65b9-4e00-ae90-3a053f7a23a4.png)

     
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
      
      ### A6
     
     - Atur IP pada *interface* **The Order** yang mengarah ke *client* **The Resonance** dengan `10.22.11.201` dan *subnet mask* `255.255.255.252`.
     
       ![image](https://user-images.githubusercontent.com/87058985/204078819-293cea55-7aae-4659-a140-40d81cba29cb.png)
     
     - Atur IP pada *client* **The Resonance** yang mengarah ke **The Order** dengan `10.22.11.202` dan *subnet mask* `255.255.255.252`.

       ![image](https://user-images.githubusercontent.com/87058985/204078834-7ac76897-a7ec-4c1a-9171-56e2c937b9cf.png)
       
      ### A7
     
     - Atur IP pada *interface* **The Instrument** yang mengarah ke *client* **Maatt Cugat** dengan `10.22.10.1` dan *subnet mask* `255.255.255.128`.
     
       ![image](https://user-images.githubusercontent.com/87058985/204078928-d4cdb975-7710-4f4a-9a90-97b269bee8bf.png)
     
     - Atur IP pada *client* **Maatt Cugat** yang mengarah ke **The Instrument** dengan `10.22.10.2` dan *subnet mask* `255.255.255.128`.

       ![image](https://user-images.githubusercontent.com/87058985/204078963-8b38905f-4273-43f9-9bcc-17061c40ffb2.png)
       
      ### A8
     
     - Atur IP pada *interface* **The Firelist** yang mengarah ke *client* **The Queen** dengan `10.22.9.1` dan *subnet mask* `255.255.255.0`.
     
       ![image](https://user-images.githubusercontent.com/87058985/204079088-3cb02d05-6bc3-41ad-ae81-bc32e8441162.png)

     - Atur IP pada *client* **The Queen** yang mengarah ke **Keith** dengan `10.22.9.2` dan *subnet mask* `255.255.255.0`.

       ![image](https://user-images.githubusercontent.com/87058985/204079158-3ddb57bb-0bb2-48e5-b872-370d2885cef1.png)
       
     - Atur IP pada *client* **Keith** yang mengarah ke **The Firelist** dengan `10.22.9.3` dan *subnet mask* `255.255.255.0`.

       ![image](https://user-images.githubusercontent.com/87058985/204079233-df79e3b1-c73f-4eda-8b2d-50559ad066c2.png)
       
     ### A9
     
     - Atur IP pada *interface* **The Queen** yang mengarah ke *client* **The Witch** dengan `10.22.11.205` dan *subnet mask* `255.255.255.25`.
     
       ![image](https://user-images.githubusercontent.com/87058985/204079451-513fbc2e-bf21-4abf-acd2-1e6ded357a21.png)
     
     - Atur IP pada *client* **The Witch** yang mengarah ke **The Queen** dengan `10.22.11.206` dan *subnet mask* `255.255.255.252`.

       ![image](https://user-images.githubusercontent.com/87058985/204079463-9f18dff6-1953-4f05-aebb-2981d78a0050.png)
       
     ### A10
     
     - Atur IP pada *interface* **The Firelist** yang mengarah ke *client* **Oakleave** dengan `10.22.4.1` dan *subnet mask* `255.255.254.0`.
     
      ![image](https://user-images.githubusercontent.com/87058985/204079525-bd4e1480-1948-47b9-a0c5-9155e807528a.png)
     
     - Atur IP pada *client* **Oakleave** yang mengarah ke **The Firelist** dengan `10.22.4.2` dan *subnet mask* `255.255.254.0`.

       ![image](https://user-images.githubusercontent.com/87058985/204079542-2a78ada9-313a-4032-8ac8-6f3f422de16a.png)
       
       
     ### A11
     
     - Atur IP pada *interface* **The Instrument** yang mengarah ke *client* **The Firelist** dengan `10.22.11.209` dan *subnet mask* `255.255.255.25`.
     
       ![image](https://user-images.githubusercontent.com/87058985/204079589-03a9ec51-00fb-47bf-a74b-bbfde783b0eb.png)
     
     - Atur IP pada *client* **The Firelist** yang mengarah ke **The Instrument** dengan `10.22.11.210` dan *subnet mask* `255.255.255.25`.

       ![image](https://user-images.githubusercontent.com/87058985/204079606-aa99c2d2-5df1-4e66-9520-0283f840e68e.png)
       
       
     ### A12
     
     - Atur IP pada *interface* **The Resonance** yang mengarah ke *client* **The Instrument** dengan `10.22.11.213` dan *subnet mask* `255.255.255.252`.
     
       ![image](https://user-images.githubusercontent.com/87058985/204079672-e173f821-56ce-4d43-98db-a10755066148.png)
     
     - Atur IP pada *client* **The Instrument** yang mengarah ke **The Resonance** dengan `10.22.11.214` dan *subnet mask* `255.255.255.252`.

      ![image](https://user-images.githubusercontent.com/87058985/204079684-d6c0f5bd-1c86-4067-b4d6-3b694ff202b1.png)
       
       
     ### A13
     
     - Atur IP pada *interface* **The Resonance** yang mengarah ke *client* **The Beast** dengan `10.22.11.217` dan *subnet mask* `255.255.255.252`.
     
       ![image](https://user-images.githubusercontent.com/87058985/204079840-2264e052-04de-49df-8428-044e584d052b.png)
     
     - Atur IP pada *client* **The Beast** yang mengarah ke **The Resonance** dengan `10.22.11.218` dan *subnet mask* `255.255.255.252`.

       ![image](https://user-images.githubusercontent.com/87058985/204079865-c4460a3e-a134-4561-8557-c6e7575e0cbc.png)
       
       
     ### A14
     
     - Atur IP pada *interface* **The Resonance** yang mengarah ke *client* **The Magical** dengan `10.22.11.221` dan *subnet mask* `255.255.255.252`.
     
       ![image](https://user-images.githubusercontent.com/87058985/204079958-9a7b2288-73fd-49c0-928e-f265dd60afbb.png)
     
     - Atur IP pada *client* **The Magical** yang mengarah ke **The Resonance** dengan `10.22.11.222` dan *subnet mask* `255.255.255.252`.

       ![image](https://user-images.githubusercontent.com/87058985/204079990-33d30bbb-3e32-4e53-bbca-1d06917b40d2.png)
       
         
     ### A15
     
     - Atur IP pada *interface* **The Instrument** yang mengarah ke *client* **The Profound** dengan `10.22.11.225` dan *subnet mask* `255.255.255.252`.
     
       ![image](https://user-images.githubusercontent.com/87058985/204080154-f8ee871d-ea13-436c-b808-bd289145d8a2.png)
     
     - Atur IP pada *client* **The Profound** yang mengarah ke **The Instrument** dengan `10.22.11.226` dan *subnet mask* `255.255.255.252`.

       ![image](https://user-images.githubusercontent.com/87058985/204080182-bde2d3a0-b908-41ec-8de7-d5d71eb73fa1.png)
       
      ### A16
     
     - Atur IP pada *interface* **The Magical** yang mengarah ke *client* **Corvekt** dengan `10.22.6.1` dan *subnet mask* `255.255.254.0`.
     
       ![image](https://user-images.githubusercontent.com/87058985/204080345-42b2f147-2af2-4ed9-9449-f09ffd1b8f80.png)
     
     - Atur IP pada *client* **Corvekt** yang mengarah ke **Haines** dengan `10.22.6.2` dan *subnet mask* `255.255.254.0`.

       ![image](https://user-images.githubusercontent.com/87058985/204080364-6803fb27-b035-48f1-ada1-11c380419e68.png)
       
     - Atur IP pada *client* **Haines** yang mengarah ke **The Magical** dengan `10.22.6.3` dan *subnet mask* `255.255.254.0`.

      ![image](https://user-images.githubusercontent.com/87058985/204080355-28526f56-d62b-4228-98b2-c7306e8d6ac1.png)
        
     ### A17
     
     - Atur IP pada *interface* **The Profound** yang mengarah ke *client* **Helga** dengan `10.22.11.1` dan *subnet mask* `255.255.255.128`.
     
       ![image](https://user-images.githubusercontent.com/87058985/204080424-d85ae973-b288-46f6-a9a9-c2c7038d4883.png)
     
     - Atur IP pada *client* **Helga** yang mengarah ke **The Profound** dengan `10.22.11.2` dan *subnet mask* `255.255.255.128`.

       ![image](https://user-images.githubusercontent.com/87058985/204080432-bfa9ff95-1874-4af4-b9cd-aaafec64458f.png)
   
          
     ### A18
     
     - Atur IP pada *interface* **The Profound** yang mengarah ke *client* **Spendrow** dengan `10.22.10.129` dan *subnet mask* `255.255.255.128`.
     
       ![image](https://user-images.githubusercontent.com/87058985/204080507-bfa148ef-4f7c-44fc-86f9-432baae92b07.png)
     
     - Atur IP pada *client* **Spendrow** yang mengarah ke **The Profound** dengan `10.22.10.130` dan *subnet mask* `255.255.255.128`.

       ![image](https://user-images.githubusercontent.com/87058985/204080529-39c50d2c-cf97-418b-bd00-eb1c5d3a8551.png)
       
       
     ## Hasil

     ![image](https://user-images.githubusercontent.com/87058985/204078356-65397cb7-dc11-48c7-a505-c42dff76bf8e.png)
## Kendala
- CPT agak kurang responsif/konsisten sehingga butuh beberapa kali pengiriman untuk mendapatkan pesan *success*.
- Beberapa *node* pada GNS3 masih belum bisa melakukan *ping* sehingga pengerjaan GNS3 untuk CIDR tidak selesai.
