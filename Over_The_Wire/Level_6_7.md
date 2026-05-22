ssh bandit6@bandit.labs.overthewire.org -p 2220
Password: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
Level Goal:
Find a file somewhere on the server. Properties:
-owned by user bandit7
-owned by group bandit6
-33 bytes in size
Solution:
// Ở level này thì khi ta list file ra thì sẽ không thấy gì cả và khi dùng cả cách ls -la thì vẫn chỉ thấy 3 file bash
// Khi này t đọc lại goal thì thấy rằng là ta phải tìm trong cả toàn system chứ không phải riêng trong thư mực
// Dựa vào gợi ý thì ta sẽ có dòng lệnh file như sau
bandit6@bandit:~$ find / -type f -user bandit7 -group bandit6 -size 33c
// Nhưng khi chạy dòng lệnh thì ta nhận được rằng rất nhiều file trong đó không có quyền đọc
// khi đó ta cần thêm vào dòng lệnh này
"  2>/dev/null "
// dòng lệnh trên để bỏ qua những file không có quyền đọc
bandit6@bandit:~$ find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null

bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password