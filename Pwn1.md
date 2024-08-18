## Description
  win win?? 
  nc 14.225.255.41 13331 

## Writeup
  Download file pwn1.zip và sử dụng lệnh unzip pwn1.zip để giải nén ta, trong file giải nén, ta quan tâm tới 2 file *flag.txt* và *pwn1*  
  Ta sử dụng lệnh `cat flag.txt`, ta được `PTITCTF{fake_flag}`
  Đầu bài yêu cầu ta nhập tên để có **flag**, ta đoán đây là dạng bài *overflow* nên ta sử dụng ida và có đoạn mã giả sau
  ![image](https://github.com/user-attachments/assets/b8232881-a997-47bc-bc80-b876116aa229)  
  ![image](https://github.com/user-attachments/assets/8c7d2db1-dcff-4456-a7d2-8fc06140dc74)  
  Ở đây, ta có thể thấy câu lệnh **read(0, &buffer, 0x200uLL)** cho phép ta nhập 512 ký tự. Như vậy ta chắc chắn đây là dạng bài *overflow*, nhiệm vụ của ta là thay đổi giá trị của a thành 0xdeadbeef  
  Dùng ida, ta biết được số ký tự tối đa của buffer (136 ký tự), a (8 ký tự).
  ![image](https://github.com/user-attachments/assets/9681f570-332d-4797-a0e9-90aad14143de)  
  ![image](https://github.com/user-attachments/assets/26c15ce6-f0ea-46d7-a24f-9b931599e18f)
  Khi đó với payload với 136 ký tự A và địa chỉ 0xdeadbeef ở dạng big edian, ta đã thay đổi được giá trị của a thành 0xdeadbeef, việc cần làm bây giờ là sửa hàm **ptr_function** về địa chỉ của hàm **win**. Dùng ida, ta cũng biết được **ptr_function** cũng có thể thay đổi bằng cách *overflow* và  
  nó có cùng dạng với a nên ta đổi địa chỉ hàm **win** thành dạng big edian và thêm vào cuối payload. Cuối cùng là viết payload hoàn chỉnh  
  ![image](https://github.com/user-attachments/assets/ada4c568-4c4c-4a27-bf20-19a1202066f3)
  Điề bất thường là sau khi ta chạy file thì chương trình lại không trả về bất cứ giá trị gì nên ta thử thay `p.recvline()` bằng `p.interactive()`  
  ![image](https://github.com/user-attachments/assets/45333404-c28e-499f-b01b-4df5bb013648)
  Sau khi chạy, ta có thể tương tác với chương trình, dùng lệnh `ls` và `cat` ta sẽ in ra được **flag**  
  ![image](https://github.com/user-attachments/assets/45fcff90-611e-4060-bde9-3801ba429c9d)

  

  

  

  



  
