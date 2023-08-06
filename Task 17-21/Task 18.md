**Task 18: Pivoting**

Before moving forward we, check that now we have find the ip address of the machiens that we hace to attack next..

![machine](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/6a89d099-0071-4de1-980a-59437902d440)


Thinking about the interesting service on the next target that we discovered in the previous task, pick a pivoting technique and use it to connect to this service, using the web browser on your attacking machine!  

Better to use to sshuttle for this task lets move ahead and see the process of connecting to the webserver using sshuttle..

**Q.  What is the name of the program running the service?**

For seeing this without using any tools we can simply type

    curl <ipaddress>

in the root@prod serv..

![Screenshot_2023-08-06_11_12_16](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/ec3cfbef-bcb1-42a7-a47b-725c4696332b)


**Now lets use the sshuttle command :**

    ssh -r root@10.200.57.200 --ssh-cmd "ssh id_rsa" 10.200.57.0/24 -x 10.200.57.200

- -r specifiying the remote access option
- --ssh-cmd for specifying different ssh file..
- -x to exclude the connection with the host cause we can already reach it..
![Screenshot_2023-08-06_11_18_08](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/71e9d815-8526-4664-ac9a-d9fc8abf19d6)

After this open browser and type `http://<ip>`


![websuite](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/d45b66d1-37f5-4e56-afbf-d20b1216934a)


After this go to the webserver type this command

    http://10.200.57.150/gitstack


and then you will be redirected to the webpage login one


![login](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/34a30122-af81-441f-bbf6-896e2faae67b)


Q. When navigating to this URI, we are given the following login page:
**Do these default credentials work (Aye/Nay)?**

Ans: Nay

**Use the command: searchsploit SERVICENAME, on Kali to search for exploits related to this service.**

![gitstack](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/f9608f33-69dc-4943-9c68-914defb932db)

**Q. There is one Python RCE exploit for version 2.3.10 of the service. What is the EDB ID number of this exploit?**

Ans: 43777



