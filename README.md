# Foresty CTF Competition 2021 Writeup 👨‍💻

- Position    : `1st Place`
- Team        : [Kurniadi Ahmad Wijaya](https://github.com/ShinyQ), [Muhammad Ilham Mubarak](https://github.com/milhamm), [Hanvito Michael Lee](https://github.com/vitomichael)  
- Total Score : 1970 (Solved All Problems)

## **Reverse Engineering**

### **Static File**

Diberikan sebuah gambar, dengan melakukan penelusuran gambar pada text editor dengan menuliskan format flag yaitu forestyCTF maka didapatkan kumpulan bilangan decimal

![Static File Decimal](https://i.ibb.co/72bP3VN/Picture1.png)

Karena merupakan bilangan decimal maka hal yang paling cocok kita lakukan adalah merubahnya kedalam bentuk ASCII sehingga didapatkan:

![Static File ASCII](https://i.ibb.co/4SBdsZ6/Picture1.png)

Dari clue tersebut maka kita lakukan decode ke rot-5 sehingga flag pun didapatkan.

![Static File Flag](https://i.ibb.co/8xg4wqj/Picture3.png)

Flag : `forestyCTF{puT3rpUt3rS3mp3sukSes}`

<br>

### **Ngapain?**

Diberikan sebuah kode file .class, jika kita telusuri lebih dalam kita bisa mendapatkan file ngapain.java kemudian dapat terlihat prosedur checkPassword dengan menyusun kata pada prosedur tersebut maka didapatkan flagnya.

![Static File ASCII](https://i.ibb.co/hf4jRxB/Picture4.png)

Flag : `forestyCTF{st0PdO1N6s03THiNGSTuPIdr5_9gudLc}`

<br>

### **Kopi Java**

Diberikan kelas java, lakukan decompile .class kemudian modifikasi code (karena saya tidak suka menggunakan java, maka saya menggunakan nodejs) kemudian jalankan program tersebut sehingga didapatkan flagnya.

![Static File ASCII](https://i.ibb.co/KwVTj23/Picture5.png)

<img src="https://i.ibb.co/5G1xPsC/Picture6.png" width="400">

Flag : `forestyCTF{7hr33_b1ll10n_d3v1c35}`

<br>

### **Coded Packer**

Diberikan sebuah executable file linux (ELF). Dengan menggunakan command strings maka didapatkan informasi bahwa file telah di pack menggunakan UPX sehingga harus kita lakukan unpac dengan command `upx -d` sehingga didapatkan file exe.

![Static File ASCII](https://i.ibb.co/x2JRrxh/Picture9.png)

Buka file .exe pada ghidra dan periksa main function yang telah di decompile kemudian periksa function Mask_Check. Kami menyadari bagaimana variabel yang diteruskan ke function dan menambahkan karakter dengan karakter variabel kedua.

<img src="https://i.ibb.co/87G0PYj/Picture8.png" width="450">

Dengan merubah hexadecimal tersebut dan mencari nilai asciinya maka didapatkan kode awal Kemudian kami menyalinnya kedalam fungsi mask_function pada C sehingga didapatkanlah flagnya.

![Static File ASCII](https://i.ibb.co/WnTfgLP/Picture10.png)

![Static File ASCII](https://i.ibb.co/TRmRfBT/Picture11.png)

Flag : `forestyCTF{Am4nD3ng4nP4ck3r}`

<br>

## **Steganography**

### **The Castle**

Diberikan sebuah gambar, dengan menggunakan command strings didapaptkan flagnya.

![Static File ASCII](https://i.ibb.co/gS9s6p1/Picture12.png)

Flag : `forestyCTF{7307249168494-82898ghhsifgadvmgk}`

<br>

### **Uncompiled Citra**

Diberikan sebuah file txt berisi kumpulan file hexadecimal, dengan menggunakan konverter decimal ke image online didapatkan gambar dengan isi flagnya.

![Static File ASCII](https://i.ibb.co/myJ607s/Picture13.png)

Flag : `forestyCTF{thepuzzlesquare}`

<br>

### **Spy Cat**

Diberikan sebuah gambar kucing, dengan menggunakan binwalk maka kita dapat mendapatkan file yang disembunyikan. Selanjutnya dapat kita lakukan ekstraksi dan didapatkanlah flagnya dalam gambar.

<img src="https://i.ibb.co/fFx8MHQ/Picture14.png" width="400">

Flag : `forestyCTF{NYAN_SPY342i}`

<br>

### **My Lost Word**

Diberikan sebuah file txt dengan nama Our_memory. Lakukan Hexdump pada file Our_memory.txt. Kemudian ubah 20 menjadi 0 dan 1d dengan 1. Lakukan konversi ke ascii untuk mendapatkan flag.

<img src="https://i.ibb.co/gjHnpKz/Picture15.png" width="400">

Flag : `forestyCTF{SemangatMembaraDalamPerjuangan}`

<br>

### **Author’s Message**

Diberikan sebuah pdf, ubah file tersebut menjadi html dan buka file html tersebut. Dengan melakukan inspeksi elemen web didapatkan link drive yang menunjukkan flag yang masih di encode. Dari "=" dibelakang kode dapat diketahui bahwa kode tersebut merupakan base64, lakukan decode dan didapatkan flagnya.

<img src="https://i.ibb.co/QX6DqfS/Picture16.png" width="500">

Flag : `forestyCTF{sayaSuKam4k4nP3rMen}`

<br>

### **The Bit Hack**

Diberikan sebuah gambar format .png, dengan menggunakan tools [zsteg](https://github.com/zed-0xff/zsteg) didapatkan flagnya.

![Static File ASCII](https://i.ibb.co/hH7YbXP/Picture17.png)

Flag : `forestyCTF{th1sIsLeast8_Sign1fic4ntBitAlg0rithm,c0ngr4tuTation;tbro}`

<br>

## **Cryptography**

### **Testing Crypto**

Diberikan sebuah code dengan berakhiran "=", diketahui kode tersebut adalah format base64 lakukan decode dan didappatkan flagnya

![Static File ASCII](https://i.ibb.co/mz0ffrJ/Picture18.png)

Flag : `forestyCTF{EzPzBase64hehe}`

<br>

### **Struggle Ways**

Deskripsi soal dapat memenuhi untuk format flag (forestyCTF{}), sehingga jika di logikakan kita hanya tinggal melakukan pergeseran, selanjutnya dilakukan pergeseran sebanyak 9 key menggunakan metode Decode Rail Fence Cipher sehingga didapatkan flagnya.

![Static File ASCII](https://i.ibb.co/DwRqFd4/Picture19.png)

Flag : `forestyCTF{ziggy_Z4ggy_horay_528}`

<br>

### **From The Last Temple**

Diberikan sebuah gambar, setelah ditelusuri gambar tersebut merupakan gambar simbol pada referensi animasi gravity falls yang menggunakan Bill cipher, lakukan decode sehingga didapatkan result GONDBHAKAYBIIMANBHASERFARES.

![Static File ASCII](https://i.ibb.co/gywmhz0/Picture20.png)

Lakukan decode menggunakan clue pada soal yaitu cipher malespin sehingga didapatkan flagnya

![Static File ASCII](https://i.ibb.co/VQnHctK/Picture21.png)

Flag : `forestyCTF{FINDTHEKEYTOOPENTHESARGERAS}`

<br>

### **Temple Box**

Diberikan clue untuk melakukan convert kode dari haxjslaKVJ{481750mtsm38kanwk93927} menjadi ROT 5 sehingga didapatkan mfcoxqfPAO{481750ryxr38pfsbp93927}. Dengan clue yang diberikan soal lakukan decode menggunakan beaufort cipher dengan kamus bahasa perancis sehingga didapatkan flagnya.

![Static File ASCII](https://i.ibb.co/LgTsqv7/Picture22.png)

Flag : `forestyCTF{481750brmm38cobra93927}`

<br>

### **Locked Room**

Diberikan file .rar yang terkunci, dengan menggunakan metode brute force pada tools john the ripper dan wordlist umum (rockyou) didapatkan passwordnya (kaitlynn).

![Static File ASCII](https://i.ibb.co/09xX0bD/Picture23.png)

ketika di ekstrak di dapatkan file The_Room.pdf. Kemudian dari file pdf tersebut apabila kita menekan ctrl+a maka terdapat hidden message yang tidak terlihat tulisannya. Dengan mempaste menggunakan text editor didapatkan flagnya.

<img src="https://i.ibb.co/jy5bzKT/Picture24.png" width="500">

Flag : `forestyCTF{kau_Berhasil_membuka_pintunya}`

<br>

### **Fill the box with the Hope**

Diberikan ketiga buah kode yang terenkripsi setelah ditelusuri ,etode yang digunakan pada soal ini yaitu digrafid cipher dengan memasukkan kedua key yang telah ada pada deskripsi soal dan kode pertama maka didapatkan flagnya.

<img src="https://i.ibb.co/KNRGg9c/Picture34.jpg" width="400">

Flag : `forestyCTF{THISISTHEANSWERYOUWANTJUSTINNNPPUTITINSIDETHETEMPALATEHEHEHEHE####}`

<br>

## **Web Exploitation**

### **Request Aku**

Lakukan inspect element html pada website <http://54.157.128.152:9300/>. Susun dan Submit kode pada web tersebut (1nI_@d4laH_fl4G??) sehingga didapatkan flagnya.

<img src="https://i.ibb.co/L0rG10q/Picture26.png" width="500">

Flag : `forestyCTF{0v33R_th1nkIng_m@y_k1lL_U}`

<br>

### **Kue Chocochips**

Karena pada clue gambar terdapat cookies, maka kami melakukan inspect cookies pada halaman <http://54.157.128.152:9400/> sehingga didapatkan flagnya.

![Static File ASCII](https://i.ibb.co/mFwYVCn/Picture27.png)

Flag : `forestyCTF{c00kiEs_1s_Imp0rt@n7}`

<br>

### **Dagang Murah**

Isi dari laman detail pada web adalah 1.php, 2.php, 3.php semuanya. Kemudian kami mencoba untuk menavigasikan sampai ke link 7.php sesuai clue untuk menambah angka dan menemukan flag dengan melakukan inspeksi elemen.

![Static File ASCII](https://i.ibb.co/D9tmNzG/Picture31.jpg)

Flag : `forestyCTF{m00dyB4ng3tn1hy4ngBu4tw33bsite}`

<br>

## **Misc**

### **Ngerumpi?**

Diberikan link Join discord forestyCTF, masuk ke discord kemudian lihat pada bagian roles pada server setting roles sehingga terdapat flag 

![Static File ASCII](https://i.ibb.co/Vpw05QL/Picture35.png)

Flag : `forestyCTF{4syqu3e_1y3uhh}`

<br>

### **Format Flag**

Pada soal, klik hint, kemudian didapatkan flag

![Static File ASCII](https://i.ibb.co/dGsND6z/Picture36.png)

Flag : `forestyCTF{ctf_assyiik}`

<br>

### **Check Your Whatsapp**

Pada grup ketua lomba ctf Lihat nama grup dari forestyCTF sehingga didapatkan flagnya

![Static File ASCII](https://i.ibb.co/YjWmCnd/Picture37.png)

Flag : `forestyCTF{Grup_CTF}`

<br>

### **Trap**

Dengan melihat nama emoji pada channel discord tersebut didapatkan flagnya.

![Static File ASCII](https://i.ibb.co/cQPkRBp/Picture39.png)

Flag : `forestyCTF{astolfonotTRAP}`
