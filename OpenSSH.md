# OPEN SSH

- To find ssh is install on you PC

   ` which ssh`

- To search if openssh-client is installed

   ` dnf search openssh-client`

    or

   ` apt search openssh-client`


### .ssh folder contains known_host file. First time you connect then the entry is stored here. If you remove known_host file it will again start asking you to save fingerprint.

- To check the logs of authentication check file /var/log

    tail /var/log/auth.log

#### Config file
```
Host osserver
    Hostname 192.168.1.23
    Port 22
    User osidris

Host server2
    Hostname 170.12.145.43
    Port 22
    User testuser
```

This enables to remember simple names instead of IPs.

### Creating SSH key. And follow the wizard

    `ssh-keygen`

### add this public key to ssh remote server

 - Manual Way: ==log on to remote system==

    ` cd  .ssh`

    ` nano authorized_keys`

    Now copy the public key content here. It will be in one line.. each line represent a key. Now save and exit nano.

 - ssh-copy-id command

    `ssh-copy-id -i ~/.sssh/id_rsa.pub root@ipaddr`

### Key managment. Default is RSA.
 - Type ED25519 with Comment. This type of key is

    `ssh-keygen -t ed25519 -C "acme"`

    Now follow the wizard and you can choose file name there. Adding a passphrase add additional layer of security. One can have 1 key for each client. This is recommended.

    `ssh -i ~/.ssh/acme_id_ed26619 root@ipdaddr`

    This will ask for passphrase again and again. To avoid this **SSH Agent** is used.

## SSH Agent

 1. Checking what agent is running : `ps aux | ssh-agent
 2. Starting agent: `eval "$(ssh-agent)"`
 3. This will give a **PID**
 4. Adding key to ssh-agent: `ssh-add ~/ssh/acme_id_ed26619`
 5. This will ask for passphrase. Hence forth during the ssh login it will not ask for passphrase. This will be in memory during the terminal session.




## Server
SSH Deamon : `which sshd`

Check Status of Service: `systemctl status sshd`    *(or for ubuntu/debian **ssh**)*

Enable Status of Service: `systemctl enable sshd`


Restart Deamon: `systemctl restart sshd`


### Keys

`/etc/ssh`

This has following type of keys

1. Host keys: You don't want to delete this key. This is a unique fingerprint of server.
2. ssh_config : Global ssh client config
3. sshd_config: We are interested in this files.

After changing any configs in sshd_config make sure you restart the server. **`$systemctl restart sshd`**


[Back to Home](index.md)


