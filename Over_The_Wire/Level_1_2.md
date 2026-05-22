ssh bandit1@bandit.labs.overthewire.org -p 2220
Password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
Level Goal:
The password for the next level is stored in a file called - located in the home directory

Solution:
// Ở level tiếp theo thì file chứa Key được lưu trong file có tên là - (dấu trừ) trong thư mục home, điều này có thể đánh lừa vài newbie nếu không để ý kỹ rằng tên file là - (dấu trừ) và cho rằng không có file nào cả.
// Ta có thể sử dụng lệnh cat để đọc nội dung của file đó
@bandit:ls
@bandit:cat./-
