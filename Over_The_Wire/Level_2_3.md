ssh bandit2@bandit.labs.overthewire.org -p 2220
Password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
Level Goal:
The password for the next level is stored in a file called spaces in this filename located in the home directory

Solution:
// Bài này cũng có thể gây lú nếu ta không để ý đến tên file, Nhưng ta chỉ cần list ra tên của file và cấm Tab để có thể tự điền tên file

@bandit:ls

@bandit:cat spaces\ in\ this\ filename

