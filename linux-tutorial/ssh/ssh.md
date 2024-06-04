## Linuxt Tutorial - Part 6 : A Complete Guide on SSH : Step-By-Step
**SSH:**

First, let's understand what is SSH?  SSH stands for Secure Shell. It is a cryptographic network protocol for operating network services securely over an unsecured network. It is a way to securely exchange data over a computer network and the data that is exchanged is encrypted. It's like a super secure tunnel that lets you log in to another computer remotely over the network. It is commonly used for remote login, secure file transfer, and executing commands on remote machines.

**How SSH Works**	

First client initiates the connections by contacting the server and the server responds with it’s public key. Both the client and server negotiate algorithm to use for the session and the user can log in to the server host operating system. 
So let’s look into more details about how ssh works:
1. Initiating a Connection

+ Client Request: The SSH client initiates a connection to the SSH server using the command ssh user@hostname.
+ Server Response: The server responds with its public key and a list of supported encryption algorithms.
2. Algorithm Negotiation
+ Agreement: Here the client and server agree on the encryption, hashing, and compression algorithms to use for the session.
3. Authentication
+ There are 2 types of Authentication: Password-Based Authentiation and Key Based Authentication.
+ Password-Based Authentication: 
    + Prompt: The server prompts the client for a username and password.
    + Verification: The server verifies the password. If it matches, the user is authenticated.
+ Key-Based Authentication: 
    + Key Pair Generation: The client generates a pair of keys (public and private) using `ssh-keygen`.
    + Public Key Distribution: The client’s public key is added to the server’s authroized_keys files which is located inside `~/.ssh/authorized_keys` file.(~:tilde refers to user home directory)
    + Challenge-Response: The server sends an encrypted challenge using the client’s public key. The client decrypts it with its private key and sends it back. If correct, the user is authenticated.
4. Establishing a Secure Session
   + Session Key: The client and server use the Diffie-Hellman key exchange algorithm to generate a shared secret session key. The Diffie-Hellman key exchange algorithm is a method used to securely exchange cryptographic keys over a public channel. It enables two parties, each with their own private key, to jointly establish a shared secret key, which can then be used for encrypted communication.
   + Encryption: This session key is used to encrypt all data transmitted between the client and server.
5. Data Transmission
   + Remote Commands: The client can execute commands on the remote server.
   + File Transfer: Client can also do Secure file transfer can be done using scp or sftp.
   + Port Forwarding: SSH can also tunnel other network services through its encrypted connection.
6. Terminating the Connection
   + Session End: The session ends when the client logs out or the connection is terminated, closing the secure channel.

This process ensures that all data sent between the client and server is encrypted, protecting it from eavesdropping and tampering.

**Installing SSH**

SSH comes in two parts: the client and the server. Most Linux distributions have the SSH client installed by default if it’s not installed then you can install using command 
`sudo apt install openssh-client openssh-server` (in Ubuntu/Debian Linux)
`sudo yum install openssh-clients openssh-server` (in Red Hat based Linux like CentOS and Rocky Linux)

**Starting and Enabling SSH Service**

If ssh-client and server are installed by default then these services are already running into your system. If not we can manually check the status and run it if it’s not running.
+ To start ssh service in Ubuntu/Debian Linux, we use command: `sudo systemctl start ssh`
+ To enable it we use command: `sudo systemctl enable ssh` Enable will allow the machines to start the service even after the reboot. So if we don’t enable ssh services then we won’t be able to run ssh services after the machine reboot so make sure you always enable it. Again all these services come enabled by default on most of the Linux distribution.
+ To check if the service is running or not we use command `sudo systemctl status ssh`
+ To start ssh service in Red hat based Linux, we use command: ~sudo systemctl start sshd` 
+ To enable it we use command: `sudo systemctl enable sshd` and 
+ To check the status we use command `sudo systemctl status sshd`


Now as we have learn some basics about SSH let’s do some practical example for SSH
So I have opened rocky linux on this terminal and debian 12 on another terminal. So we will ssh from debian12 to rocky linux. 
+ First of all we will need ip address for the target host. For that we can run any ip command such as `ip a` or  `ip addr` and copy the ip address of the target host. Now let’s go back into the debian host and let’s ssh into rocky linux using command `ssh user@hostname` in our case it’s `ssh <user-name-of-remote-host>@<ip-address-remote-host>` and hit "enter"
+ When you try to log in for the first time it will ask you to save "fingerprint key". Type "yes" and it will ask for the "password". Give the password for the target host and hit "enter" and you should be able to login to your server. 
+ You can run the command `cat /etc/os-release` to check more. 

As you have looked into password based ssh connection now let’s look into key based SSH connection or the passwordless ssh connection.

+ "For added security, you can use "SSH key-based authentication" instead of passwords so for that first we need to Generate a SSH key pair and copy the public key to the server. 
+ To generate ssh key, Use command `ssh-keygen`. It will ask to save the path, you can hit enter, it will now ask if you want to enter any "passphrase" for the key, you can enter passphrase if you would like to make it more secure. If you have use passphrase then type your passphrase again to verify it. Now your private and public key is generated. 
+ To check, use command `ls -al` (This command will list any files or directory including hidden files/directory)
+ As you can see `.ssh` directory is generated here. 
+ In linux dot any directory means it’s a hidden directory and to see hidden directory you have to use `-a` flag. We will also discuss more about it in the upcoming videos.
+ Now let’s go into this `.ssh` directory. To go inside this directory we use command `cd` which means change directory. `cd .ssh`, we are now inside `.ssh` directory and execute `ls` command to check the content inside this directory.
+ As you can see "id_rsa" which us a private key  and "id_rsa.pub" file which is a public key.
+ Now we need to copy the public key into the target host where we want to establish our connection. In our case, we will do it from debian 12 to rocky linux.
+ To copy we use command `ssh-copy-id username@hostname` so in our case it’s ssh-copy-id username is <username-remote-host>@<ip-address-remote-host>
+ It will ask for the password for the remote host. Enter the password and your public key will be saved in remote host. 
+ Now you should be able to login to remote host without a password. 

Now let’s look into more advance features of SSH that is we will be using "config" file for SSH 
+ so to create config file first go inside `.ssh` dir
+ `cd .ssh` and let’s create config file here using "vi" editor that is `vi config` and hit "enter". Now we can define ssh configuration here.

        Host rocky-linux
            Hostname <remote-host-ip>
            IdentityFile ~/.ssh/id_rsa 
            User <user-name-of-remote-host>
Save and quit the file using escape `:wq` which means write and quiet.
Now we can ssh into the remote host using our config file that we recently configured.
Run command `ssh rocky-linux` and you will be able to login now using the config file which is one of the best method to ssh into the remote server. You can add as many remote host you would like into the config file and make the ssh login much easier and simple for you to login.
