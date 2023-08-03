**TASK 10: Proxychains and Foxyproxy**

![image](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/66dc4da9-4dcd-4c63-a37b-0a55e93ec990)

In this task we'll be looking at two "proxy" tools: Proxychains and FoxyProxy and at the end we will be setting up our poxyfoxy ..

**Proxychains:**

Proxychains is a tool we have already briefly mentioned in previous tasks. It's a very useful tool -- although not without its drawbacks. 
Proxychains can often slow down a connection: performing an nmap scan through it is especially hellish. 
Ideally you should try to use static tools where possible, and route traffic through proxychains only when required.

U can set it by using this command `proxychain nc <ip>`

I will skip the proxychain part and will move to foxyproxy, if you guys want then feel free to give a read on proxychain and how they are
used in kali.

**Make sure to use firefox or chrome browser**

In order to install the foxyproxy extention in the firefox visit this : https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/?utm_source=addons.mozilla.org&utm_medium=referral&utm_content=search

And add the extention to your browser give all the permission and so on..

Now lets see how can we add a proxy to it so that we can work with that proxy address

1. Click on the foxyproxy extension
2. Click on `options`
3. If you are using firefox you will be redirected to foxyproxy options tab, it will look something like this
![options](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/ad6a3dc6-f41f-4c9a-9ca2-58d0712f7def)
4. Now click on the add option
![addoption](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/aeead99c-e1d3-4751-af5e-bf56a83fd5df)

5. And fill them accordingly at the end click on save and you are good to gooo...
6. And by clicking on the icon of the foxyproxy you can change the proxy
![opt](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/7ec9ec69-3d31-4eae-ad07-127031813587)

**Q.What line would you put in your proxychains config file to redirect through a socks4 proxy on 127.0.0.1:4242?**

Ans: socks4 127.0.0.1:4242

**Q. What command would you use to telnet through a proxy to 172.16.0.100:23?**

     proxychain telnet 172.16.0.100:23

**Q. You have discovered a webapp running on a target inside an isolated network. Which tool is more apt for proxying to a webapp: Proxychains (PC) or FoxyProxy (FP)?**

Ans: Ofcourse FP cause it comes very handy with burpsuite for pentesting and many more..

With this our task 10 ends lets move forward...
