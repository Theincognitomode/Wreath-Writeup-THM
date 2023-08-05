

**Task 15: sshuttle**

![image](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/5249e755-b19f-49a0-b807-762b4197f870)

Last tool in this sectionn ufff...


This tool is different from the other tools as it doesn't uses any port forwading or proxy creation instead it uses SSH connection to create a tunnelled proxy that acts like a new interface.

In short it creates a VPN(Virtual Private Network), which allows us to divert the traffic without using proxychains...

Lets move forward with the installation of this tool..

Either you can type the command as 

    sudo apt install sshuttle
    
Or just simply type the name then press `y` to download it

![Screenshot_2023-08-05_03_24_33](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/8f1c10bc-e495-4a49-a42c-430d40d28ed5)


The basic command for connecting with the server is:

    sshuttle -r username@address subnet  

  And if you are not sure about the subnet you can mention `-N' in it

  As the previous tools this tool also supports the backgrounded search by using the ampersand (&) symbol to the end.

  We won't be using this tool practically though in this room,so if you prefer to read the commands make sure to read the task file..

  Lets move forward with the questions..

**Q. How would you use sshuttle to connect to 172.16.20.7, with a username of "pwned" and a subnet of 172.16.0.0/16**

      sshuttle -r pwned@172.16.20.7 172.16.0.0/16 

**Q. What switch (and argument) would you use to tell sshuttle to use a keyfile called "priv_key" located in the current directory?**

    --ssh-cmd "ssh -i priv_key"

**Q. You are trying to use sshuttle to connect to 172.16.0.100.  You want to forward the 172.16.0.x/24 range of IP addreses, but you are getting a Broken Pipe error. What switch (and argument) could you use to fix this error?**

    -x 172.16.0.100
  


