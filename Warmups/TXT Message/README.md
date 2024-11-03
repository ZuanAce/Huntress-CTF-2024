# TXT Message 

## Challenge Description
> ![image](https://github.com/user-attachments/assets/8c948459-bc69-4ae1-b3b7-b59c302c44fc)

  
## Approach
1. The challenge hinted at an odd DNS record for the ctf.games domain, so I decided to investigate.
   Using the [DNS Checker Tool](https://dnschecker.org/all-dns-records-of-domain.php?query=ctf.games&rtype=ALL&dns=google), I pulled up all the DNS records for ctf.games and, sure enough, spotted a strange TXT record. This looked like it could contain something important.

   ![image](https://github.com/user-attachments/assets/9808f747-0daa-41db-8353-62723bb9b963)
   
3. The TXT record itself appeared to be a string of ASCII codes.
   To make sense of it, I turned to an [ASCII converter tool](https://www.dcode.fr/ascii-code) to translate it. After converting the codes, the output revealed exactly what I was hoping for—a flag!

   ![image](https://github.com/user-attachments/assets/2d923641-8485-49a5-a792-dd5dbdbe62b0)
   
## Flag: 
flag{14e072f705d45882401d141c562fdc0b}

   


