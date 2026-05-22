ssh bandit8@bandit.labs.overthewire.org -p 2220
Password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
Level Goal:
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

Solution:
// lần này thì key vẫn được lưu trong file nhưng mà chúng ta không có keyword để tìm key nữa mà phải lọc qua và tìm key không bị duplicate
// sử dụng lệnh sort để tìm key không bị duplicate
ls
sort data.txt | uniq -u
// trong đó uniq -u là để tìm ra key không bị dup hoặc có thể dùng -d để chỉ trả lại key bị dup

