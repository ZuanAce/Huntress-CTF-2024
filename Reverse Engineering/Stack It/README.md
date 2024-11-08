# Stack It ✅

## Challenge Description
> ![image](https://github.com/user-attachments/assets/3f3413c3-2367-4924-b0c7-b80fd1eec11a)

## Approach
1. We’re given a binary file named stack_it.bin. After running the file command on it, we find that it's an ELF 32-bit executable, which is statically linked and stripped of debug information. It's meant to run on an Intel 80386 architecture.

   ```
   stack_it.bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, stripped
   ```

3. Next, I loaded the binary into IDA Pro to examine its disassembled code.
   
   ![image](https://github.com/user-attachments/assets/304fd9ae-d0c8-40f7-b74d-25b938308546)

4. From the disassembly, I managed to understand the important parts of the code:

   ```C
   byte_804A050 = 102; // 'f'
   byte_804A051 = 108; // 'l'
   byte_804A052 = 97;  // 'a'
   byte_804A053 = 103; // 'g'
   byte_804A054 = 123; // '{'
   ```
   This part sets up the initial characters of the flag: flag{.

   ```C
   v0 = &unk_804A00E;  // Pointer to the decryption key
   v1 = &unk_804A02E;  // Pointer to the encrypted string
   v2 = &unk_804A055;  // Pointer to where decrypted characters will be stored
   v3 = 32;            // Number of bytes to decrypt

   do {
     *v2++ = *v1++ ^ *v0++; // XOR decryption
     --v3;
   } while (v3);
   ```
   Here, we have a simple XOR loop that decrypts 32 bytes of data. It uses a key `(unk_804A00E)` and an encrypted string `(unk_804A02E)`. The result is stored starting at `unk_804A055`.

   ```C
   *v2 = 125;   // Adds '}' to end the flag
   v2[1] = 0;   // Null terminator
   ```
   The decrypted string is terminated with } and a null character (\0), completing the flag.

5. To reveal the flag, we need to XOR the encrypted_bytes with the key_bytes (using the same decryption process as in the disassembled code. Here's the python script for it!

   ```python
   from pwn import *

   # Load the binary
   binary = ELF('stack_it.bin')

   # Extract the key bytes and encrypted bytes from the binary
   key_bytes = binary.read(0x804A00E, 32)
   encrypted_bytes = binary.read(0x804A02E, 32)

   # XOR decryption
   decrypted_flag = bytearray()
   for i in range(len(encrypted_bytes)):
       decrypted_flag.append(encrypted_bytes[i] ^ key_bytes[i])

   # Print the decrypted flag
   print("Decrypted flag:", "flag{"+ decrypted_flag.decode() + "}")
   ```

6. Running the script successfully reveals the flag!

   ![image](https://github.com/user-attachments/assets/7635f642-0b87-46fd-8daa-84fffb25a2bd)

  
## Flag: 
flag{b4234f4bba4685dc84d6ee9a48e9c106}



   
