![image](https://github.com/Anirudh-Saxena/Wreath-Writeup-THM/assets/73027020/bb259779-6d84-4b76-971a-fdfc85eb3fc2)


**TASK 4 : Brief**

In this task Thomas is giving information about his network our task here is too highlight the main points from this description given by Thomas..

After readin this i was able to conclude this points :
1. There are two machines on home network
2. The first one which Host projects.
3. The second one whihch is for his personal use
4. One of them has a webserver that's port forwarded.

As a beginner :) i was only able to find this much useful information from the description, but THM has also analysed this and gave us some idea about how to see diiffernt problems, and what are the main points that we need to identify.
From this we can take away the following pieces of information:

- There are three machines on the network
- There is at least one public facing webserver
- There is a self-hosted git server somewhere on the network
- The git server is internal, so Thomas may have pushed sensitive information into it
- There is a PC running on the network that has antivirus installed, meaning we can hazard a guess that this is likely to be Windows
- By the sounds of it this is likely to be the server variant of Windows, which might work in our favour
- The (assumed) Windows PC cannot be accessed directly from the webserver


By reading the **NOTE** of this task  i got the motivation to create this writeup :) ty THM for this!!

Note: You are also encouraged to treat this Network like a penetration test -- i.e. take notes and screenshots of every step and write a full report at the end (especially if you're not already familiar with writing such reports). Keeping track of any files (e.g. tools or payloads) and users you create would also be a good idea. Reports will not be marked, but the act of writing them is good practice for any professional work -- or certifications -- you may do in the future.

After reading all of this we just have to click on questions completed and then move on to the **Task 5**
Before moving to task 5 make sure to **update your kali machine**
The command for that is simple :
make sure you are root before rolling out these commands : 
sudo apt-get update && apt-get upgrade 


