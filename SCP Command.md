# SCP (Secure Copy)
It uses SSH

scp filename.txt user@ipaddress:/home/user/
This will copy a file name filename.txt to remote server

### Reverse Copy. From remote to local machine

scp user@ipaddress:/home/user/filename.txt /home/localuser/


### Bonus
If yo want to list the files on the remote server without going into ssh shell then

ssh user@ipadress ls

or if its in your network then

ssh hostname ls


### Copy a Directory to remote server

scp -r backup hostname:/Path

scr -pr

-p preserves the date of file
-r for recursive i.e all the files in a directory

