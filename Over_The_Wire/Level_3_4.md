ssh bandit3@bandit.labs.overthewire.org -p 2220
Password: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
Level Goal:
The password for the next level is stored in a hidden file in the inhere directory.

Solution:
// Ở level này thì cũng sẽ khác tương đồng với level trước nhưng lần này thì file chứa key của của chúng ta sẽ bị ẩn đi

@bandit:ls
@bandit:cd inhere
// khi chúng ta list file ra ở đây thì chúng ta sẽ không thấy file nào ở đây cả, nhưng mà khi list bằng các -la thì lại xuất hiện 1 file tên là ...Hiding_From_You
@bandit:ls -a
// Khi đã biết được tên của file key thì chúng ta sẽ làm giống level trước
@bandit:cat ./...Hiding-From-You
