# PillowFight ✅

## Challenge Description
> ![Screenshot 2024-11-04 100601](https://github.com/user-attachments/assets/2ca3e185-2ef4-4fde-9e70-3a2b2ecd790b)

## Approach
1. First, I tried uploading two images, and the system combined them, giving back a grayscale image. Curious to test boundaries, I uploaded non-image files… but that just gave a 500 internal server error.

     ![image](https://github.com/user-attachments/assets/73646ba1-bf1c-4ca8-b438-ceeded53cd10)

     ![image](https://github.com/user-attachments/assets/09f6bffb-47cb-4d6e-8949-33bc946d48df)


3. Checking the Swagger API docs, I noticed a custom eval() function—yes, eval()! It’s known for being potentially exploitable, especially if used without proper security checks. 

   ![image](https://github.com/user-attachments/assets/78ac1833-a608-4b07-a9a0-9c6d62491e12)
   
   
4. Time to experiment. I threw different inputs at it, but mostly hit walls (hello, 400 errors). Then I noticed something odd: the function would accept empty strings and None without complaint. This got me thinking…what if I injected a Python command directly?
   ```
   convert(img1 + open('flag.txt').read()img2, 'L')
   ```
   And there it was—the flag appeared in the output!
   
   ![image](https://github.com/user-attachments/assets/270853df-a49d-4e57-a839-edc360b725af)

   
## Flag: 
flag{b6b62e6c5cdfda3b3a8b87d90fd48d01}
