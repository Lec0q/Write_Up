ssh bandit0@bandit.labs.overthewire.org -p 2220
Password: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

Level Goal:
The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

Solution:
// level đầu tiên thì rất là đơn giản, chỉ cần đọc được file readme trong thư mục home là sẽ có key cho level tiếp theo.
@bandit:ls

@bandit:cat readme
