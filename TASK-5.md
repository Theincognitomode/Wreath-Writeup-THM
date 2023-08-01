**TASK 5 : Webserver Enumeration**


Description of the task : 


As with any attack, we first begin with the enumeration phase. Completing the Nmap room (if you haven't already) will help with this section.
Thomas gave us an IP to work with (shown on the Network Panel at the top of the page). Let's start by performing a port scan on the first **15000 ports of this IP**.


_Note: Here (and in general), it's a good idea to save your scan results to a file so you don't have to re-run the same scan twice._


You might be wondering whats the ip address, and where is the ip address mentioned :

The ip address is mentioned of the top of :

![image](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/a9bbc5ad-50ba-4530-acc9-fe5b8b3c804b)

i.e in mycase its: `10.200.57.200`

Now lets start our nmap enumeration and do the task given to us :


**Q. How many of the first 15000 ports are open on the target?**
As learned the Nmap module to specify the ports we use `-p` and then we specify the range of the ports in this case we can do `0-15000` or simply 15000 both means the same 

so the command will be : `nmap <ip> -p 0-15000 > output`



