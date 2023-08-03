**TASK 11: SSH TUNNELLING/Port forwarding**

![image](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/acac5495-e92f-42a2-befa-45998fe5bc83)

The first tool we'll be looking at is none other than the bog-standard SSH client with an OpenSSH server. Using these simple tools, it's possible to create both forward and reverse connections to make SSH "tunnels", allowing us to forward ports, and/or create proxies.

Like we did in task 6, using a git tool and then connecting it with the netcat server to listen and access the system and gain ssh key from in and adding it to our DNS file by giving it 600 permissionsss..

This can be done using the kali terminal, using the `ssh` keyword, lets type `man ssh` and see what are the possible opertaions that this command can perform..

![Screenshot_2023-08-03_11_28_13](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/9f1015b6-b0bb-4d95-9793-4d117dc41a99)

In this task we will be using command from this section only i guess letss move forward ..

Note that it's good practice to use a high port, out of the way, for the local connection. This means that the low ports are still open for their correct use (e.g. if we wanted to start our own webserver to serve an exploit to a target), and also means that we do not need to use sudo to create the connection. 

Proxies are made using the `-D` switch 
![Screenshot_2023-08-03_11_34_08](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/daa4956f-6d85-42dd-95cb-bd8196ebdb41)

**How to do reverse connetion..**

1. Generate the key pairs using the command

       ssh-keygen
![Screenshot_2023-08-03_11_41_01](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/b72a7b16-ead8-47d5-beac-0010c09c9505)


2. Copy the contents of the public key (the file ending with .pub), then edit the ~/.ssh/authorized_keys file on your own attacking machine. You may need to create the ~/.ssh directory and authorized_keys file first. But if you have done the task 6 then the creation step is done no need to do that again..

  ![publickey](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/30768cef-7908-4384-8776-d03b50709a85)

3. On a new line, type the following line, then paste in the public key:

       command="echo 'This account can only be used for port forwarding'",no-agent-forwarding,no-x11-forwarding,no-pty

4. Check the status of the SSH server on your system

        sudo systemctl status ssh
and if its not active then replace the `status` keywoard with `start` in order to start the ssh server..

The only thing left is to do the unthinkable: transfer the private key to the target box. This is usually an absolute no-no, which is why we generated a throwaway set of SSH keys to be discarded as soon as the engagement is over.

well its upto you if you want to do these steps..

if you want to do these steps then read the tasks instructions..

lets move forward with the questionss..

**Q. If you're connecting to an SSH server from your attacking machine to create a port forward, would this be a local (L) port forward or a remote (R) port forward?**

Ans: Local port forward cause we are using our own machine.

**Q. Which switch combination can be used to background an SSH port forward or tunnel?**

Ans: -fN , for more information check the screenshot of man ssh..

**Q. It's a good idea to enter our own password on the remote machine to set up a reverse proxy, Aye or Nay?**

Ans: Nayyy

**Q. What command would you use to create a pair of throwaway SSH keys for a reverse connection?**

Ans: ssh-keygen

**Q. If you wanted to set up a reverse portforward from port 22 of a remote machine (172.16.0.100) to port 2222 of your local machine (172.16.0.200), using a keyfile called id_rsa and backgrounding the shell, what command would you use? (Assume your username is "kali")**

Ans: ssh -R 2222:172.16.0.200:22 kali@172.16.0.100 -i id_rsa -fN, 

for this follow this format `ssh -R LOCAL_PORT:TARGET_IP:TARGET_PORT USERNAME@ATTACKING_IP -i KEYFILE -fN`

**Q. What command would you use to set up a forward proxy on port 8000 to user@target.thm, backgrounding the shell?**

Ans: ssh -L 8000 user@target.thm -fN

**Q. If you had SSH access to a server (172.16.0.50) with a webserver running internally on port 80 (i.e. only accessible to the server itself on 127.0.0.1:80), how would you forward it to port 8000 on your attacking machine? Assume the username is "user", and background the shell.**

Ans: ssh -L 8000:127.0.0.1:80 user@172.16.0.50

