## Description
  Can you use your knowledge of format strings to make the customers happy?  
  Download the binary here.  
  Download the source here.  
  Connect with the challenge instance here:
  nc mimas.picoctf.net 59150
  

## Writeup
  Access nc mimas.picoctf.net 59150 we have these text 
  ![image](https://github.com/user-attachments/assets/22bc53e3-ea37-4bda-87f6-3e912cffe631)
  We need to choose right burger for go to next step.
  IN three option: Breakf@st_Burger, Gr%114d_Cheese, Bac0n_D3luxe, only Gr%114d_Cheese have format string(%11).
  ![image](https://github.com/user-attachments/assets/e49e8e1d-ee06-43e2-8197-fb255b6e3061)
  Like above, we choose Cla%sic_Che%s%steak and we have flag.
  **Flag: picoCTF{7h3_cu570m3r_15_n3v3r_SEGFAULT_74f6c0e7}**
  
