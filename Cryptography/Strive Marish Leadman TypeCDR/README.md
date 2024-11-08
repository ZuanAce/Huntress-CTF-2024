# Strive Marish Leadman TypeCDR ✅

## Challenge Description
> ![image](https://github.com/user-attachments/assets/d632c4de-59db-4c3f-b6d6-3b9712530479)


## Approach
1. So, I connected to a remote server and what did I find? A heap of large hexadecimal numbers: p, q, n, e, d, and another one without any notation.
    
   ```
   p: 0xfbc7464a095f8a5a997408d74a9fa12d6fa8c3e00d66bb6f8bb8705d60aeea36055297230c23019d7aabb54b99db944944ce7f872445c8a37e80250f9871ee9b
   q: 0xee4e37f52a493271eb731f735381896033a6c138900438f52a590d3ba3d049335b08fd16bd1c55cbadfeaa4b3e40316976c1984c51f4cd1a0b0ff3afc13c82af
   d: 0x9f046eab884855fb254f63ba4ed8bcdc4c512c4894791c2ea18131cde9eb2a82c42a3d7e149e419a37f1820f60264d03288ee71f68b5086f2569b9ea7323ff80df6fb6f77bfcc7415932be0c38c66097c30d0647e4e66c1300f0d7e46ff4eb4284da5339d028cd3a4fd3646ab14bad9218d287695827fb1c903a556911bc12ed
   e: 0x10001
   n: 0xea6031192eac899308557dacd825e1b0155b4f1f2552b247bc0ffa77c3356fb29d1f9f82459baf7816f56c7d977daf00aec2317220707b5e87620f9492fcc61c674f3678a76c65701381c89ab4fd589fd14b1246f0826ed4d5def811c56604fcaac0ce120ba21092ba255e68d2f99e747240a61fa6e5c202fd751d9ed860d1f5

   0x2bd7c5413a2c2b697c178932c48def5ffd0b7260d5d1a5f2426e0571a7a86b6a5b9ee08db46608db314082f2925303057fecb65b9db6ef389cc8ec6280f0503b18bdd8da52aea6ae0e4ec852be34e95534cab169248980e01de5e8c1b384567ade217be4754c52c6f24488e88b681f190aff8391727cd79280625d9698ab26e2
   ```

   It’s an RSA challenge because values for p, q, n, e, and d—all essential components of RSA. 

2. I just need to convert all these hexadecimal values into decimal numbers ~I used an online [Hex to Decimal Converter](https://www.rapidtables.com/convert/number/hex-to-decimal.html) to do the job. Why? Because RSA works with decimal values, and I can’t really use hexadecimal numbers directly for the decryption process. 
3. After converting all the numbers into decimal, it was time to use them in the RSA decryption process. For that, I used the [RSA Cipher](https://www.dcode.fr/rsa-cipher) tool.
   With all the values plugged in—p, q, n, e, d—I clicked "Decrypt" and waited for the result. And boom, the flag was revealed!
   
   ![image](https://github.com/user-attachments/assets/10861655-5332-4339-bd8d-1c02691f78f7)

## Flag: 
flag{cf614b15ac1dd461a2e48afdfe21b8e8}



   



