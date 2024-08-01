## Description 
  Patrick and Sponge Bob were really happy with those orders you made for them, but now they're curious about the secret menu. Find it, and along the way, maybe you'll find something else of interest!    
  Download the binary here.    
  Download the ![source](<https://artifacts.picoctf.net/c_rhea/13/vuln.c>) here.    
  Connect with the challenge instance here: nc mimas.picoctf.net 61035

## Writeup
  Connect to nc mimas.picoctf.net 61035, we have this text
  ![image](https://github.com/user-attachments/assets/d8619bb4-73f7-4820-a9c4-c0bc92c26583)  
  After reading source code, in line 34 and line 36  
  ![image](https://github.com/user-attachments/assets/153fac2f-7790-4a46-928c-d99c6140c13f)  
  and reading in <https://github.com/Naetw/CTF-pwn-tips?tab=readme-ov-file#overflow>, i was try %p then i have a hexadecimal  
  ![image](https://github.com/user-attachments/assets/20d61a56-5ea1-4847-b6fb-249cfd2d9817)  
  I was try type many %p and i have many hex and i think it is flag after decode  
  ![image](https://github.com/user-attachments/assets/859f2153-3d70-4073-873d-fb4a7542b820)  
  Go to <[decode.fr](https://www.dcode.fr/ascii-code)>, i try to decode this  
  ![image](https://github.com/user-attachments/assets/b95cb549-d38d-422d-8bb2-bddbcf865d25)  
  I think i find the flag but word was reverse so i try to decode one by one hexadecimal and i have flag (0x7b4654436f636970, 0x355f31346d316e34, 0x3478345f33317937, 0x65355f673431665f, 0x7d346263623736)  
  **Flag: picoCTF{4n1m41_57y13_4x4_f14g_5e67bcb4}**



  

