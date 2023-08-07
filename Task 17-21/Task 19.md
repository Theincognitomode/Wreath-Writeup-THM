**Task 19: Code Review**

In this module we will be using the python RCE exploit 2.3.10

Make the copy of the exploit using the command:

    searchsploit -m 43777

![Screenshot_2023-08-07_02_27_33](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/ca3c36d9-34d3-40d8-b7ab-f676ef6e41a4)

As we can see that it wont work cause, the local exploit copies stored by searchsploit use DOS line endings, 
which can cause problems in scripts when executed on Linux:

In order to fix this we will use the command 

      dos2unix ./43777.py

With this now lets read the file and answer the questions..

I will be using the `vim` to read the code and answer the questions..

![Screenshot_2023-08-07_02_35_58](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/e2e9798f-1bfa-46b1-ad3e-09a3f7589dd4)

**Q. Look at the information at the top of the script. On what date was this exploit written?**

Ans: 18.01.2018


**Q. Bearing this in mind, is the script written in Python2 or Python3?**

Ans: Python2, cause all the print statments in this exploit have "" ..

Add the shenbang command to the top, in vim we can do this by pressing `i` to open the intsert mode and then esc `:wq`to save the file

After this read through the the task file, if you want the explanation of the code, in order to enbale numbers in the vim type :set number

**Q. Just to confirm that you have been paying attention to the script: What is the name of the cookie set in the POST request made on line 74 (line 73 if you didn't add the shebang) of the exploit?**

![Screenshot_2023-08-07_02_46_07](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/359efd53-ad4f-4a26-9e51-51962385d084)

    csrftoken

Lets move forward and see the exploitation part..
