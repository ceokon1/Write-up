## Description  
  what's your name ?    
  nc 14.225.255.41 13333

## Writeup  
  Ta kết nối tới server và nhập tên với id bất kì  
  ![image](https://github.com/user-attachments/assets/3e6a1997-365a-4b5c-acde-8effd652cbf6)  
  Nhận thấy không thể khai thác được gì, ta sử dụng ida để xem pseudo code  
  ![image](https://github.com/user-attachments/assets/fe284838-6585-43e3-99d1-2fea650800df)  
  Ta thấy lệnh `mmap` có thể sử dụng **ret2shellcode** để yêu cầu server gửi **flag** 
  Dùng lệnh `file` để kiểm tra dạng tệp tin  
  ![image](https://github.com/user-attachments/assets/c89033bc-d8ef-405d-bcdc-f4a43d5c75d8)  
  Tìm trên [shellstorm](https://shell-storm.org/shellcode/files/shellcode-806.html), ta thấy có thể sử dụng file shellcode [Linux/x86-64 execute /bin/sh/](https://shell-storm.org/shellcode/files/shellcode-806.html)  
  Ta có đoạn payload `\x31\xc0\x48\xbb\xd1\x9d\x96\x91\xd0\x8c\x97\xff\x48\xf7\xdb\x53\x54\x5f\x99\x52\x57\x54\x5e\xb0\x3b\x0f\x05` để **ret2shellcode**. Việc cần làm bây giờ là viết payload hoàn chỉnh để yêu cầu server gửi **flag**  
  ![image](https://github.com/user-attachments/assets/8431cc61-737f-41bb-ab4e-fd44abaad778)  
  Chạy file **solve.py** và sử dụng `ls` cùng với `cat flag.txt`, server sẽ trả về **flag**  
  ![image](https://github.com/user-attachments/assets/2d6064ca-6df2-4e62-be52-f109219973a6)  
  **Flag:** `PTITCTF{sk3llc0d3_js_byt3c0d3?}`

  
  

  


  
  
