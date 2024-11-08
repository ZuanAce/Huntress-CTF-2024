# Nightmare on Hunt Street 🔍

## 🧾 Challenge Description
> **Points:** 250   
> Author: Austin Worline, Jose Oregon, and Adrian Garcia
> 
> DeeDee hears the screams,<br>
> In the logs, a chilling trace—<br>
> Freddy's waiting near.<br>
> Are you able to unravel the attack chain? The first question is:
>
> What is the IP address of the host that the attacker used?
> 
> **NOTE: Flags for Part #1 to Part #5 will all be human-readable answers and in a non-standard flag format. You will use the same downloadable attachment and log files to answer all the questions.**
> 
> Download the file(s) 
> 
> **Category:** Challenge Group 


## 🔍 Analysis 
1. Fire up Flare-VM, download the file, and unzip the file.
2. I noticed that the files are in .evtx extensions, thus I opened them using Windows Event Viewer. Only the *System* and *Security* have events, *Application* does not have any.
   
   ![image](https://github.com/user-attachments/assets/490333c6-89ea-4209-8b5f-e855ec1c0c41)

   ![image](https://github.com/user-attachments/assets/5ef53534-db52-469d-bfd3-739262e90cd1)


## 🛠️ Solution
- By simply using [ROT-13 Cipher Decoder](https://www.dcode.fr/rot-13-cipher) , the ciphertext is decoded to reveal the flag.

![image](https://github.com/user-attachments/assets/4effbdae-9a14-43e7-a961-12d70a24bac2)
```
Faktor penentangan Dato Maharaja Lela
Mengambil hak mengutip cukai.
24Julai1875 Birch memaksa Sultan Abdullah menandatangani pengisytiharan
yang membolehkan British mengambil hak mengutip cukai.
Sultan Abdullah diugut akan diturunkan takhta jika enggan menandatangani pengisytiharan tersebut.
Birch membakar rumah Raja Ngah Orang Besar Perak kerana meneruskan kutipan cukai di Bidor.
Mencabar Ketuanan Melayu.
Kemarahan Sultan dan pembesar Perak memuncak pada 2Oktober1875.
Sultan Abdullah dipaksa menandatangani surat penyerahan kuasa kepada British.
Kuasa mentadbir negeri diserahkan kepada Residen yang berkuasa melantik hakim, menguruskan
cukai dan melantik penghulu.
Memperkenalkan Cukai Baru Birch bertindak sesuka hati dengan memperkenalkan cukai baru seperti cukai
padi, perahu atap, senjata dan bayaran permit untuk membalak. 3108k3b4ngk1tanp4hl4w4n Setiap isi rumah perlu
membayar 2Dolar sebagai cukai kelamin. Mencabuli Adat Resam Birch dibenci oleh sultan dan
pembesar-pembesar Perak apabila mengharamkan sistem perhambaan yang menjadi adat resam Melayu
Birch sengaja menimbulkan kemarahan orang Melayu dengan menyimpan hamba-hamba perempuan di rumahnya.an menyimpan hamba-hamba perempuan di rumahnya.
```
3108{k3b4ngk1tanp4hl4w4n}
  
## 🧰 Tools Used
- ROT-13 Cipher Decoder

