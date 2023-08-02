**TASK 6: Exploitation**  

In this task we will be exploiting the vuln that we found while solving the TASK 5

![cruped](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/501c59ab-00f0-4f1f-b1e1-12977be6f753)

Lets move and download the exploits that is provided to us by the THM 

we can copy paste the command and simply run in the terminal inorder to solve this task 6 

`git clone https://github.com/MuirlandOracle/CVE-2019-15107`

This creates a local copy of the exploit on our attacking machine. Navigate into the folder then install the required Python libraries:

`cd CVE-2019-15107 && pip3 install -r requirements.txt`

If this doesn't work, you may need to install pip before downloading the libraries. This can be done with:
`sudo apt install python3-pip`

and after this we have to run the script as : `./CVE-2019-15107.py <TARGET_IP>`

The interface will look something like this:
![Screenshot_2023-08-01_15_32_48](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/0db24b19-1801-41bc-b614-78e6d7ebbc1f)

The first question is just a check wether we were able to follow all the steps mentioned above..

**Q. Which user was the server running as?**

For this type `whoami`, I learned about this module form the linux fundamentals it will come very handy while solving this room make sure to do that room if you haven't till now..
anyhow the **ans : root**


Now we have to do the reverse connection for this we will have to type the shell and provide the ip address and port number in it and then using the netcat we can connect to this server, more like pwn challenges in ctf

**NOTE: Make sure to press enter only after executing this command: `sudo nc -lvnp <portnumber>`** cause we want to do the reverse connection and by doing so we can hear what are the activites going on the other side.. 
![Screenshot_2023-08-01_16_28_43](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/1d0f1380-e6af-42a6-842f-ba07b04d0702)



If you are facing issue with the connection as _connection being refused_ then use the command `chmod +x ./CVE...`


For solving this question searched for https://www.cyberciti.biz/faq/where-are-the-passwords-of-the-users-located-in-linux/

and type the following command in the cmd prompt `cat /etc/shadow`

The cat command reads each File parameter in sequence and writes it to standard output. If you do not specify a file name, the cat command reads from standard input.


![Screenshot_2023-08-01_16_50_00](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/ffb278ff-9a9e-435d-8244-3c2d8c50cd5b)


**Q. What is the root user's password hash?**

The password is: $6$i9vT8tk3SoXXxK2P$HDIAwho9FOdd4QCecIJKwAwwh8Hwl.BdsbMOUAd3X/chSCvrmpfy.5lrLgnRVNq6/6g0PxK9VqSdy47/qKXad1::0:99999:7:::

Now lets follow the other steps and we are ready to go for the next taskk....!!

**Q. What is the full path to this file??**

Ans: /root/.ssh/id_rsa

Download the key (copying and pasting it to a file on your own Attacking Machine works), then use the command `chmod 600 KEY_NAME` (substituting in the name of the key) to obtain persistent access to the box.

For this we have to look for some useful files that can help us to obtain a key that will be able to connect to a server with SSH 

By using the `cat` command we can view the key

`cat id_sha`

The file will have contents like this 
![Screenshot_2023-08-02_02_12_35](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/f1d3c8ae-d667-4649-b329-10f63d7175b6)
Here we can see that its a private key so we can use this key to connect with the ip of the machine to gain root privilages!!

In my case i wasnt able to download this file to my local machine so i copied the contents of the files and made a new file with the same name i.e _id_rsa_

After doing so i tried to connect with ssh server using the private key to gain the access...

![Screenshot_2023-08-02_02_15_11](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/8e7126a1-c3d6-4492-b362-1fafdda9f27b)
Might be wondering why `chmod 600` ??

chmod 600 is a command used to set file permissions in Linux. It means that only the owner of the file has full read and write access to it. Once a file permission is set to 600, no one else can access the file1. The command sets permissions so that the user/owner can read and write but not execute, while the group and others have no access to the file.

With this lets move to another taskk....
