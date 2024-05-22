### Watch command repeatedly run the given command every 2 seconds
`watch ls`

`watch df-h`

`watch free -m` #m stands for in MB

### -d highlights the change

`watch -d free -m`

### -n to change the interval (default is 2s)

`watch -d -n free -m`

### In case of Piped commads its important to wrap them in single quotes '' otherwise it will not work

`watch 'ls -lh | grep important_file.txt'`

[Back to Home](index.md)
