**TASK 9: Enumeration**

![image](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/58bbb987-0db5-48ff-a236-fc7496f0006c)

Enumeration is basically information gathering on the target machine by using different sets of tools 

There are five possible ways to enumerate a network through a compromised host:

- Using material found on the machine. The hosts file or ARP cache, for example
- Using pre-installed tools
- Using statically compiled tools
- Using scripting techniques
- Using local tools through a proxy

Before trying anything else its always better to check the ARP cache on system, in order to find any ip address with which our host has 
connected or gain information.

For this we can use the command :

    arp -a

Or we can check manually by going through the files `/etc/hosts`

For identifying any local DNS in our system we can use the commans `/etc/resolv.conf`

Make sure to read the task file to move forward from here....

If somehow nmap is not available in the sytem then we use this bash line command to do the same thing not as smooth as nmap but some sort of it

    for i in {1..255}; do (ping -c 1 <target_ip> | grep "bytes from" &); done

The above command generates a full list of numbers from 1 to 255 and loops through it. For each number, it sends one ICMP ping packet to 192.168.1.x as a backgrounded job (meaning that each ping runs in parallel for speed),
where i is the current number. Each response is searched for "bytes from" to see if the ping was successful. 
Only successful responses are shown.

And then they have mentioned several other ways in which we can perform the same action, by using differnt sets of programming lang..

**Q. What is the absolute path to the file containing DNS entries on Linux?**

Ans: /etc/resolv.conf

**Q. What is the absolute path to the hosts file on Windows?**

Ans: C:\Windows\System32\drivers\etc\hosts

**Q. How could you see which IP addresses are active and allow ICMP echo requests on the 172.16.0.x/24 network using Bash?**

    for i in {1..255}; do (ping -c 1 172.16.0.${i} | grep "bytes from" &); done
