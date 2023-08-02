**TASK 8: High level overview**

![euiuttt](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/a88307de-8ddf-4379-a604-a5e9631017bf)


The methods we use to pivot tend to vary between the different target operating systems. Frameworks like Metasploit can make the process easier, however, for the time being, we'll be looking at more manual techniques for pivoting.

There are two main methods encompassed in this area of pentesting:

**Tunnelling/Proxying:** Creating a proxy type connection through a compromised machine in order to route all desired traffic into the targeted network.
This could potentially also be tunnelled inside another protocol (e.g. SSH tunnelling), 
which can be useful for evading a basic Intrusion Detection System (IDS) or firewall

**Port Forwarding:** Creating a connection between a local port and a single port on a target, via a compromised host

We will be using these two techniques mentioned above in the upcoming task in order to exploit the machines in the upcoming task..

Why we use proxy,**proxy is good in redirecting a lot of traffic into the target machine**

The major diff between port forwading and proxy is that in Port forwading we can also access a single port where as using proxy we can access a huge amout of traffic.

The lower the traffic or the req to forward the faster the task is thats why port forwading is a faster process as compared to that of the proxy

According the machine we will use the process that suits itt..

The remaining tasks in this section will cover the following topics:

- Enumerating a network using native and statically compiled tools
- Proxychains / FoxyProxy
- SSH port forwarding and tunnelling (primarily Unix)
- plink.exe (Windows)
- socat (Windows and Unix)
- chisel (Windows and Unix)
- sshuttle (currently Unix only)


To read more about pivoting follow this link: https://www.geeksforgeeks.org/pivoting-moving-inside-a-network/

**Q. Which type of pivoting creates a channel through which information can be sent hidden inside another protocol?**
Ans: The answer should be pretty clear from the desc of the Q that is make a channel inside another protocol just like caves , **tunnelling**

**Q. Research: Not covered in this Network, but good to know about. Which Metasploit Framework Meterpreter command can be used to create a port forward?**
Google it...

Lets move forward with the another task 

    
