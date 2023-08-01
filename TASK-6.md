
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







