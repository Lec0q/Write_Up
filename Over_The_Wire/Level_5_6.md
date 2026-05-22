ssh bandit5@bandit.labs.overthewire.org -p 2220
Password: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
// cái này cũng ghi bằng tiếng anh nên cố đọc nha
Level Goal:
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
-human-readable
-1033 bytes in size
-not executable

Solution:
//The problem requires us to find a file in the inhere directory that meets the specified criteria.
//Let see what we have in the inhere folder
//Okay so we have 19 different folder and each one of them have some files in them.
// So let use the find command to search for the file that meets the criteria.
bandit5@bandit:~/inhere$ find ./ -size 1033c -not -executable
//Here is the result   "./maybehere07/.file2"
//So the password is in the file .file2 in the maybehere07 folder
bandit5@bandit: cat ./maybehere07/.file2
