ssh bandit4@bandit.labs.overthewire.org -p 2220
Password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
// level này lỡ ghi bằng tiếng anh nên cố đọc nha :3
Level Goal:
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

Solution:
@bandit:ls
//Let see what we have in the inhere directory
@bandit:cd inhere
@bandit:ls -la
//hmm, seem like we have flew files but we dont know which one is holding the key
//Let see what is inside the first file
@bandit:cat ./-file00
// hmm, it return this "�p��&�y�,�(jo�.at�:uf�^���"
// Seem like this a a ELF file and we can't unreadable. Let try see what types of files we have in this directory
bandit4@bandit:~/inhere$ file ./*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
// We can see that ./-file07 is a ASCII text file. Let see what is inside
@bandit:cat ./-file07
// We can see that the password is inside the file
