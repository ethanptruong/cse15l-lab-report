#This is cd in all its entirety
```
1 [user@sahara ~]$ pwd
2 /home
3 [user@sahara ~]$ cd lecture1
4 [user@sahara ~/lecture1]$ pwd
5 /home/lecture1
6 [user@sahara ~/lecture1]$ cd
7 [user@sahara ~]$ pwd
8 /home
9 [user@sahara ~]$ cd lecture1/messages/en-us.txt
10 bash: cd: lecture1/messages/en-us.txt: Not a directory
11 [user@sahara ~]$ pwd
12 /home
```
>I first tried to use the change directory or *cd* command to change the directory
>to lecture 1 from the home directory. Using the *pwd* or "print working directory" 
>command to demonstrate my current folder is now lecture1. The command worked as 
>intended because the working directory was lecture 1. 

>I then tried to use the cd command with no argument. As you can see, the folder
before I used command was "/home/lecture1". After using the cd command with no 
argument, the directory was changed to the home directory as intended because there 
>was no argument. This is seen in line 8. 

>Lastly, I used the cd command with a path to the "en-us.txt" file as the argument.
>The working directory at the time was the home directory This resulted in an error 
>because this command was intended to change to a different directory and not a file. 

#this is ls in all its entirety
```
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ ls
lecture1
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ ls lecture1
Hello.class  Hello.java  messages  README
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ ls lecture1/messages/en-us.txt
lecture1/messages/en-us.txt
[user@sahara ~]$ pwd
/home
```

>First, I used ls with no command on the home directory. This printed lecture1,
>as intended, because lecture1 was the only directory in the home folder. 

>I then used ls with the lecture1 directory as an argument. This printed all of
>the files and directories within the lecture1 folder because I used lecture1 
>as the argument. 

> I lastly used the file path to the en-us.txt file as an argument for ls. The 
>computer then printed the relative? file path to the terminal

#this is cat in al its entirety
```
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ cat
hellow
hellow
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ cat lecture1
cat: lecture1: Is a directory
[user@sahara ~]$ cat lecture1/messages/en-us.txt
Hello World!
```

>I first used the cat without any argument at the home directory. The terminal 
>had me input any characters and when I pressed enter, it would print another 
>copy of what I wrote because I didn't use any arg. 

>I then used the cat command using the lecture1 directory as an argument and 
>home as the working directory. This returned an error because the cat command
>was designed so that a file would be used as an argument whereas we used a 
>directory for our argument. 

>I lastly used the file path to en-us.txt as an argument for the cat command. 
>"Hello World!" was printed into the terminal because the command told the 
>computer to follow the file path and print whatever the contents of the file 
>is there, which happened to be "Hello World!"