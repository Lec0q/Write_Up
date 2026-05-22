ssh bandit7@bandit.labs.overthewire.org -p 2220
Password: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
Level Goal:
The password for the next level is stored in the file data.txt next to the word millionth


Solution:
// Đối với level này thì khá là đơn giả, key lần này sẽ nằm trong file tên là data. Nhưng khi ta đọc file bằng lệnh cat thì kết quả sẽ rất dài.
// Vì vậy ta sẽ sử dụng lệnh grep để tìm kiếm từ millionth trong file data.txt hoặc tìm kiếm thủ công trong nano
// cách 1: grep

bandit7@bandit:~$ grep -i 'millionth' data.txt
millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
// có thể thấy cách này rất nhanh và đơn giản
// cách 2: nano
bandit7@bandit:~$ nano data.txt
// tìm kiếm từ millionth bằng Ctrl + W
millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc


