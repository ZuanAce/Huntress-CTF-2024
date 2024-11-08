# Obfuscation Station ✅

## Challenge Description
> ![image](https://github.com/user-attachments/assets/c1152d55-0a0f-420c-84a9-10e0b387c644)

## Approach
1. I was given a ZIP file containing a PowerShell script. When I opened it, the script seemed a little intimidating at first due to its obfuscated nature. Here’s the content I found inside:
   
    ```
    (nEW-objECt  SYstem.iO.COMPreSsIon.deFlaTEStREAm( [IO.mEmORYstreAM][coNVERt]::FROMBAse64sTRING( 'UzF19/UJV7BVUErLSUyvNk5NMTM3TU0zMDYxNjSxNDcyNjexTDY2SUu0NDRITDWpVQIA') ,[io.COmPREssioN.coMpreSSioNmODE]::DeCoMpReSS)| %{ nEW-objECt  sYStEm.Io.StREAMrEADeR($_,[TeXT.encodiNG]::AsCii)} |%{ $_.READTOENd()})| & ( $eNV:cOmSPEc[4,15,25]-JOin'')
    ```
   The first thing that stands out is the Base64 string embedded in the PowerShell script. It’s obvious that the script is doing something like:
   - Decoding the Base64 string.
   - Decompressing the resulting data (with the DeflateStream function).
   - Transforming it into ASCII text.
   - Outputting the result.
     
  2. I decided to replicate what the script does in Python. Here’s the script I wrote:

     ```python
     import base64
     import zlib

     # Decoding the Base64 string
     data = base64.b64decode('UzF19/UJV7BVUErLSUyvNk5NMTM3TU0zMDYxNjSxNDcyNjexTDY2SUu0NDRITDWpVQIA')

     # Decompressing the data using Zlib (raw deflate stream)
     decompressed_data = zlib.decompress(data, -zlib.MAX_WBITS)

     # Printing the ASCII output
     print(decompressed_data.decode('ascii'))
     ``` 

4. Running the script reveals the flag!
  
   ![image](https://github.com/user-attachments/assets/cd5e4420-1121-40e2-beb0-31368f287b6c)
   
## Flag: 
flag{3ed675ef0343149723749c34fa910ae4}



   



