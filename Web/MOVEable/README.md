# 1200 Transmissions ✅

## Challenge Description
> ![image](https://github.com/user-attachments/assets/b9f3744a-2bc9-4a64-8a58-b5e05f6e022f)




## Approach
1. Opening the transmissions.wav file, I was hit with some seriously loud and eerie sounds—definitely a horror vibe! After trying basic steganography techniques and getting nowhere, I took a breather and thought about the challenge title.

2. ChatGPT suggested that "1200" relates to modulated data signals, which led me to use a tool called **Minimodem**,  a command-line program which decodes (or generates) audio modem tones at any specified baud rate, using various framing protocols. It acts a general-purpose software FSK modem, and includes support for various standard FSK protocols such as Bell103, Bell202, RTTY, TTY/TDD, NOAA SAME, and Caller-ID. After installing it, I ran:
   
   ```
   minimodem --rx 1200 -f transmissions.wav
   ``` 

3. Success! I decoded a hidden message along with the flag!

   ![image](https://github.com/user-attachments/assets/f400721b-cf27-4aef-a88d-83dff8b2a443)
   
## Flag: 
flag{f28d133e7174c412c1e39b4a84158fa3}




   
