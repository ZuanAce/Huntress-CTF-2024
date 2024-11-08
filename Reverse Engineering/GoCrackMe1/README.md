# GoCrackMe1 ✅

## Challenge Description
> ![image](https://github.com/user-attachments/assets/44e3d79f-0fbd-4e1d-b204-5db900044a36)


## Approach
1. You’re given a ZIP file which, when you unzip, gives a Go binary file. This was my first time dealing with a Go binary. And in case you don’t know, Go binaries are a lot harder to crack than C binaries.
2. Using IDA, decompile the file and found the `main.main function`.

   ![image](https://github.com/user-attachments/assets/e959e313-61cd-44a5-8cbe-a5749ae8f94d)

3. With some assistance from ChatGPT, I managed to understand the important parts of the code:

   ```C
   qmemcpy(v12, "0:71-44coc``3dg0cc3c`nf2cno0e24435f0n+", sizeof(v12));
   ```
   The string `"0:71-44coc``3dg0cc3cnf2cno0e24435f0n+"` is copied into `v12`, a buffer of 38 bytes.

   ```C
   v1 = (uint8 *)runtime_makeslice((runtime__type *)&stru_48BA20, 38LL, 38LL);
   for (i = 0LL; i < 38; ++i)
       v1[i] = v12[i] ^ 0x56;
   ```
   This loop takes each byte from `v12` and XORs it with 0x56, storing the result in `v1`. This is a common obfuscation technique used to hide strings. We can decode it to reveal the hidden message.

   ```C
   v4 = runtime_slicebytetostring(0LL, v1, 38LL);
   ```
   The `v1` slice (which now contains the XOR-deciphered bytes) is converted into a string `v4`.

5. To decrypt the obfuscated string `"0:71-44coc``3dg0cc3cnf2cno0e24435f0n+"` using XOR with 0x56, I wrote a quick Python script for this.

   ```python
   # Hardcoded string from the code
   original_string = "0:71-44coc``3dg0cc3c`nf2cno0e24435f0n+"
   xor_key = 0x56
   flag_bytes = []

   # XOR each byte with the key
   for char in original_string:
       flag_bytes.append(chr(ord(char) ^ xor_key))

   # Join the bytes to form the flag string
   flag = ''.join(flag_bytes)
   print("Extracted flag:", flag)
   ```

7. Running the script reveals the flag!!

   ![image](https://github.com/user-attachments/assets/aa52e274-f459-47fe-be87-dbb8d65aa60a)
  
## Flag: 
flag{bb59566e21f55e5680d589f3dbbec0f8}




   
