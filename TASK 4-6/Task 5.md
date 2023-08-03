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

so the command will be : `nmap -O -sV -p 0-15000 <ip> -oA output`

- **-O stands for operating system**

- **-sV stands for**

- **-oA stands for output type**

For more commands you can simply type **man nmap** and browse to your needs accordingly.
In between you can also press **Enter** to check the progress of your scan

This is the report of the nmap
![cropednmaprepo](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/64001f87-a9c4-4182-84fb-db9a831701e1)

By this we get the answer of the first question lets move to the second one.

**Q. What OS does Nmap think is running?**

After struggling on this i read the hint and it said that -O wont give you accurate result on this case try using a different approach.
The hint says that look for web host so i looked in the scan and found _centos_ you might be wondering what _centos_ is ??

**Centos:**
The Apache HTTP server is the most widely-used web server in the world. It provides many powerful features including dynamically loadable modules, robust media support, and extensive integration with other popular software. In this guide, you will install an Apache web server with virtual hosts on your CentOS 7 server.

**Q. Open the IP in your browser -- what site does the server try to redirect you to?**

For this simply go to the browser and paste the ip address then it will redirect you to a valid website which will be the answer of this question :)
`https://thomaswreath.thm/`

Now lets move to the second half of this task in which we have to add the ip to our local host so that we can access this website and see the contents of it

**Make sure to do this as a root user**
type the command as : `gedit /etc/hosts`

after doing so go to the browser and reload the page the page will look something like this:



And then add the dns in this file in this format `<ip> thomaswreath.thm`
![Screenshot_2023-08-01_15_07_07](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/ed075934-78fb-4251-8d4e-0636b7790ca1)

Lets move ahead .....

**Q. Read through the text on the page. What is Thomas' mobile phone number?**
Well this is more like a **OSINT CHAL** from the ctf
` +447821548812 `

**Q. Look back at your service scan results: what server version does Nmap detect as running here?**

For this we can simply check the file in which we stored the nmap result, the answer is `MiniServ 1.890 (Webmin httpd)` present on the 13 line 

**Q. What is the CVE number for this exploit?**
For this we can search `MiniServ 1.890 (Webmin httpd)` on google and can get the result of it and the answer was

`CVE-2019-15107` for more info about this follow this https://www.cvedetails.com/cve/CVE-2019-10507/?q=CVE-2019-10507


And with this our **TASK 5** ends here lets move to the next task..


