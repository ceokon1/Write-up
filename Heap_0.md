## Description
	Are overflows just a stack concern?
	Download the binary here.
 	Download the source here.
	Connect with the challenge instance here:
	nc tethys.picoctf.net 52214

## Writeup
	Connect to nc tethys.picoctf.net 52214, we have
 	![image](https://github.com/user-attachments/assets/c26228d9-35b1-4b1e-aefc-c8c351d9388d)
	We can in source code, 
 	![image](https://github.com/user-attachments/assets/d62b9acc-74ab-4f24-9be5-a973994a4053)
	**input_data** and **safe_var** have same address. Therefore, we try overflow to change **save_var** and we have flag.
 **Flag: picoCTF{my_first_heap_overflow_4fa6dd49}**
 



