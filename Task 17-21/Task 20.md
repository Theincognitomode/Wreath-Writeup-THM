**Task 20: Exploitation**

**Make sure that you are connected with the server if you are not connected with the server then you might not be able to proccedd futher..**


Its time to execute the exploitt....

Before doing so change the ip address to the target ip and change your exploit name with that of your user name on thm..
![ipchange](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/9faa797b-b877-449a-850e-c99931204f23)

![exploit](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/9924c6c9-8584-486c-a1f5-f3cb6736713b)

After changing the ip address and exploit, execute the python script..

![resulr](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/cd4b4fbd-f997-4edb-8792-e462b6869ce2)

Now lets get started with the burpsuite and intercept the request and follow the tasks in the room..

Open the burpsuite set your foxyproxy on and change it to the burpsuite..

Now lets turn on the proxy and and intercept the proxy request, and modify it according to the task given..

After intersecpting the request send it to the repeater by pressing `ctrl+R`, or press right click there you will see the option to do so..

Now Lets edit the request in the repeater..

Make sure to edit the Get request change it with POST, the request would  look something like this..

![editedreq](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/200995b5-9fc2-4192-854e-5e57a5375971)

After this send the request,and check the response tab 

![respo](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/c953e518-a99c-4c2a-895a-f731ceacc4cd)

You might be wondering what `nt authority\system` means??

nt authority\system is considered as the most powerful account on a windows machine like we can access anything if we have the access of this..

**Q. First up, let's use some basic enumeration to get to grips with the webshell:What is the hostname for this target?**

Ans: For this modify the a=whoami to `a=hostname` : git-serv

**Q. What operating system is this target?**

Ans: Windows

**Q. What user is the server running as?**

    nt authority\system

**Q. this will send three ICMP ping packets back to you.
How many make it to the waiting listener?**

Ans: 0

I did this by changing the burpsuite request of a with that of `a = ping -n 3 10.50.55.145`

There was no response on the tcpdump page..


