ssh bandit9@bandit.labs.overthewire.org -p 2220
Password: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
Level Goal:
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.


Solution:
// Lần nay thì dữ liệu trong file không đọc được nhưng sẽ có những dòng có thể đọc được và sẽ bắt đầu bằng dấu =
// ta có thể tìm dòng đó bằng lệnh strings
bandit9@bandit:~$ strings data.txt | grep ==

// trong đó strings là để tìm chuỗi dữ liệu và grep == để tìm dữ liệu chứa dấu =