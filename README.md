# OS Shell Script 
---
## CYCLE SHEET 1
### Question 2
**Write a shell script to read three numbers from standard input and print the minimum value and maximum.**
```shell
#!/bin/sh
#Write a shell script to read three numbers from standard input and print the minimum value and maximum.
echo "enter the three numbers"
read x
read y
read z
if [ $x -ge $y ] && [ $x -ge $z ]
then
echo "$x is the largest number"
elif [ $y -ge $x ] && [ $y -ge $z ]
then
echo "$y is the largest number"
else
echo "$z is the largest number"
fi
if [ $x -lt $y ] && [ $x -lt $z ]
then
echo "$x is the smallest number"
elif [ $y -lt $x ] && [ $y -lt $z ]
then
echo "$y is the smallest number"
else
echo "$z is the smallest number"
fi
```
---

### Question 3
**Write a shell script to swap two numbers without using 3rd variable.**

```shell
#!/bin/bash
#swap 3 numbers without 3rd number
echo "enter first number"
read a
echo "enter second number"
read b
echo "a before swapping is $a and b is $b"
a=$((a+b))
b=$((a - b))
a=$((a-b))
echo "a after swapping is $a and b is $b"
```
---

### Question 4
**Write a shell script to read the marks of a Student and print the grade**

```shell
#!/bin/bash
#print grade for marks
echo "Enter the Marks"
read m
if [ $m -ge 90 ]
then
    echo "Grade : S"
elif [ $m -ge 80 ]
then
    echo "Grade : A"
elif [ $m -ge 70 ]
then
    echo "Grade : B"
elif [ $m -ge 60 ]
then
    echo "Grade : C"
elif [ $m -ge 50 ]
then
    echo "Grade : D"
elif [ $m -ge 35 ]
then
    echo "Grade : E"
else
    echo "Result : Fail"
fi
```
---

### Question 5
**Write a shell script to read two integer numbers and perform basic arithmetic operations based on user’s choice (use ‘case’ structure).**

```shell
# !/bin/bash
# perform arithmetic operations on 2 numbers
echo "Enter Two numbers : "
read a
read b
# Input type of operation
echo "Enter Choice :"
echo "1. Addition"
echo "2. Subtraction"
echo "3. Multiplication"
echo "4. Division"
read ch
case $ch in
1)res=`echo $a + $b | bc`;;
2)res=`echo $a - $b | bc`;;
3)res=`echo $a \* $b | bc`;;
4)res=`echo "scale=2; $a / $b" | bc`;;
esac
echo "Result : $res"
```
---

### Question 6
**Write a shell script to find the sum of first ‘N’ Natural Numbers (use ‘while’ structure)**

```shell
# !/bin/bash
#find sum of n numbers
echo "Enter number : "
read n
i=1
sum=0
while [ $i -le $n ]
 do
 sum=$(( $sum + $i ))
 i=$(( $i + 1 ))
 done
echo "Sum of all digit is $sum"
```
---

### Question 7
**Write a shell script to find the sum of first ‘N’ numbers in Fibonacci series (use ‘for’ structure)**

```shell
#!/bin/bash
#Sum of n numbers of fibonacci
echo "Enter a number"
read n
sum=1
a=0
b=1
for ((i=2; i<n; i++))
do
 c=`expr $a + $b`
 sum=`expr $sum + $c`
 a=$b
 b=$c
done
echo $sum
```
---

### Question 8
**Write a shell script to print a given number in reverse order and sum of the individual digits.**

```shell
#!/bin/bash
#reverse a number and sum of digits
echo "Enter a number"
read n
rev=0
sum=0
while [ $n -gt 0 ]
do
 d=$(( n % 10))
 n=$(( n / 10))
 sum=$(( sum + d))
 rev=$(( rev*10 + d))
done
echo "reverse is $rev"
echo "sum is $sum"
```
---

### Question 9
**Write a shell script to read two strings and display whether it is equal, not equal, null strings or string with special characters.**

```shell
#!/bin/sh
#Compare two strings
echo "Enter a string"
read str1
echo "Enter a string"
read str2
if [ $str1 \> $str2 ]
then
echo "$str1 is greater then $str2";
elif [ $str1 \< $str2 ]
then
echo "$str1 is less then $str2";
else
echo "Both string are same";
fi
if [ `expr "str1" : ".[~!@#$%^&()_+].*"` -gt 0 ]
then
echo "First string contains special characters"
fi
if [ `expr "str2" : ".[~!@#$%^&()_+].*"` -gt 0 ]
then
 echo "Second string contains special characters"
fi
if [ -z "$str1" ];
then
echo "$str1 is null";
else
echo "$str1 is not null";
fi
if [ -z "$str2" ];
then
echo "$str2 is null";
else
echo "$str2 is not null";
fi
```
---

### Question 10
**Write a shell script to accept one integer argument and print its multiplication table.**

```shell
#!/bin/sh
#multiplication table of a number
echo "enter number"
read n
i=1
while [ $i -le 10 ]
do
echo " $n * $i =`expr $n \* $i ` "
i=`expr $i + 1`
done
```
---

### Question 11
**Write a shell script, which accepts any number of arguments and prints them in the Reverse order. (For example, if the script is passed A B C as arguments, then execution should produce C B A on the standard output).**

```shell
echo "Input string is:$*"
for x in "$@"
do
y=$x" "$y
done
echo "Reversed string :$y"
```
---

### Question 12
**Write a Shell Script that makes use of grep to isolate the line in etc passwd that contains your login details**

```shell
#!/bin/sh
#isolate the line in login details
grep -n 'Your Roll No' /etc/passwd
```
---

### Question 13
**. Write a shell script to display all files in the /home/YourLoginName subdirectory as well as display the type of all files**

```shell
#!/bin/sh
#names and details of files in present working directory
echo "\nname of files are\n"
ls
echo "\n types of files are\n"
ls -l
```
---

### Question 14
**Using shell script, display the contents of the present working directory. If it is an ordinary file print its permission and change the permissions to r--r--r--.**

```shell
# !/bin/bash
for item in *
do
if [ -f $item ]
then
echo "----------------$item----------------"
if [ -x $item ]
then
echo "File in Executable mode"
chmod -x $item
echo "Executable permission Removed!"
fi
if [ -w $item ]
then
echo "File in Write mode"
chmod -w $item
echo "Write permission Removed!"
fi
if [ -r $item ]
then
echo "Already in read mode(r--r--r--)"
else
chmod +r $item
echo "Now the read permission granted "
fi
echo "final permission"
ls -al $item
fi
echo
done
```
---

### Question 15
**Use find, grep and sort to display a sorted list of all files in the /home/YourLoginName subdirectory that contains the word “hello” somewhere inside them.**

```shell
-type f -print0 | xargs -0 grep -li "hello" | sort
```
---
### Question 16
**Write a shell script to produce a list of users and their login shells.**

```shell
#! /bin/bash
#
for i in $(cat /etc/passwd | cut -d: -f1); do
 echo -n $i ": "
 grep $i /etc/group | cut -d: -f1 | tr "\n" " "
 echo
done
```
---


## CYCLE SHEET 2

### Question 17
**Write a C program to kill a process by specifying its name rather than its PID.**
```c
    #include<stdio.h>
    #include<string.h>
    main()
    {
    char cmd[50],cmd1[50],cmd2[50],log[50],pname[50],pid[50];
    FILE * fp;
    system("rm newpro");
    system("rm data");
    printf("enter ur login name\n");
    fgets(log,sizeof(log),stdin);
    strcpy(cmd,"ps -aux | grep ");
    strcat(cmd,log);
    system(cmd);
    printf("enter the name of the process u want to terminate\n");
    scanf("%s",pname);
    strcpy(cmd1,"ps -a | grep ");
    strcat(cmd1,pname);
    strcat(cmd1," > newpro");
    system(cmd1);
    system("cut -f2 -d' ' newpro > data");
    fp=fopen("data","r");
    fscanf(fp,"%s",pid);
    strcpy(cmd2,"kill ");
    strcat(cmd2,pid);
    system(cmd2);
    system(cmd);
    printf("the process %s is killed successfully",pname);
}

```
---

### Question 18
**Create a file with few lines, Write a C program to read the file and delete the spaces more than one in the file (use UNIX file API’s).**
```c
#include<stdio.h>
#include <string.h>
#include<sys/types.h>
#include<sys/stat.h>
#include<fcntl.h>
int main()
{
    int fd1,fd2;
    char buf1[50],buf2[50];
    int i=0,j=0,n;
    fd1=open("file1.txt",O_RDONLY);
    fd2=open("file2.txt",O_CREAT|O_WRONLY,0754);
    read(fd1,buf1,sizeof(buf1));
    for(i=0;i<strlen(buf1);i++)
    {
        if(((buf1[i]==' ')&&(buf1[i+1]!=' '))||(((buf1[i]!=' '))))
            buf2[j++]=buf1[i];
        else
        {
            buf2[j++]=buf1[i];
            for(n=i+1;n<strlen(buf1);n++)
                buf1[n]=buf1[n+1];
        }
    }
    write(fd2,buf2,sizeof(buf2));
    close(fd1);
    close(fd2);
    return 0;
}
```
---

### Question 19
**Implement a C program to list the users who have logged in more than once.**
```c
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
int main()
{
    char user[30],check[30];
    int i,f,count,c=0;
    char arr[80][30];
    FILE *fp1,*fp2;
    system("clear");
    system("who > yy");
    system("cut -f1 -d ' ' yy > original");
    fp1=fopen("original","r");
    while(!feof(fp1))
    {
        fscanf(fp1,"%s",user);
        count=0;
        f=1;
        fp2=fopen("original","r");
        while(!feof(fp2))
            {
            fscanf(fp2,"%s",check);
            if(strcmp(user,check)==0)
                count++;
            strcpy(check,"");
        }
        fclose(fp2);
        for(i=0;i<c;i++)
        {
            if(strcmp(arr[i],user)==0)
                f=0;
        }
        if(count==2 && f==1)
        {
            printf("%s has logged on %d times\n",user,count);
            strcpy(arr[c++],user);
        }
    }
    fclose(fp1);
}
```
---

### Question 20
**Write a C program which renames all .txt files as .text files.**
```c
#include<stdio.h>
#include<string.h>
int main()
{
    FILE *fp;
    int i;
    char temp[50],cmd[20];
    system("ls");
    system("ls > list");
    fp=fopen("list","r");
    while(!feof(fp))
    {
        fscanf(fp,"%s",temp);
        i=0;
        strcpy(cmd,"mv ");
        while(temp[i]!='.')
            i++;
        if(temp[i+1]=='t'&&temp[i+2]=='x'&&temp[i+3]=='t')
        {
            strcat(cmd,temp);
            strcat(cmd," ");
            temp[i+2]='e';temp[i+3]='x';temp[i+4]='t';temp[i+5]='\0';
            strcat(cmd,temp);
            //printf("%s\n",cmd);
            system(cmd);
        }
        //printf(" %s \n",temp);
    }
    printf("after changing: ");
    system("ls");
    return 0;
}

```
---

### Question 21
**Implement a C program that reports the number of file names in the current working directory that consist of exactly five characters.**
```c
#include<stdio.h>
#include<string.h>
int main()
{
    FILE *fp;
    int i;
    char temp[50],cmd[20];
    system("ls > list");
    fp=fopen("list","r");
    while(!feof(fp))
    {
        fscanf(fp,"%s",temp);
        if(strlen(temp)==5)
            printf(" %s \n",temp);
    }
    return 0;
}
```
---

### Question 22
**Write Programs to a) Report the behaviour of the OS to get the CPU type and model, kernel version. b) Get the amount of memory configured into the computer, amount of memory currently available.**
```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
    system("clear");
    system("echo CPU Type and Model:");
    system("cat /proc/cpuinfo | awk 'NR==2 {print $3}'");
    system("cat /proc/cpuinfo | awk 'NR==5 {print}'");
    printf("\n\n");
    system("echo Kernel Version:");
    system("cat /proc/sys/kernel/osrelease | awk 'NR==1 {print}'");
    printf("\n\n");
    system("echo MEMORY:");
    system("cat /proc/meminfo | awk 'NR==1 {print}'");
    system("cat /proc/meminfo | awk 'NR==2 {print}'");
    printf("\n\n");
    system("echo Load Average:");
    system("cat /proc/loadavg | awk 'NR==1 {print}'");
}
```
---

### Question 23 
**Write a program to a create child process and display the process ID of parent and child processes.**
```c
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main()
{
    int pid = fork();
    if(pid)
        printf("I am the child Process with %d pid\n", getpid());
    else
        printf("I am the Parent Process with %d pid\n", getpid());
    return 0;
}
```
---

### Question 24
**Write a program to demonstrate the implementation of Inter Process Communication (IPC) "who | grep YourLoginName" using pipes.**
```c
#include<stdio.h>
#include<unistd.h>
int main() {
    int pipefds[2];
    int returnstatus;
    char writemessages[2][20]={"P1 started", "P2 Started"};
    char readmessage[20];
    returnstatus = pipe(pipefds);
    if (returnstatus == -1) 
    {
        printf("Unable to create pipe\n");
        return 1;
    }
    printf("Writing to pipe - Message from Process 1 is %s\n", writemessages[0]);
    write(pipefds[1], writemessages[0], sizeof(writemessages[0]));
    read(pipefds[0], readmessage, sizeof(readmessage));
    printf("Reading from pipe – Message from Process 1 is %s\n",readmessage);
    printf("Writing to pipe - Message from Process 2 is %s\n", writemessages[1]);
    write(pipefds[1], writemessages[1], sizeof(writemessages[0]));
    read(pipefds[0], readmessage, sizeof(readmessage));
    printf("Reading from pipe – Message from Process 2 is %s\n", readmessage);
    return 0;
}
```
---

### Question 25
**Write a program to demonstrate the implementation of Inter Process Communication (IPC) using Message Queues.** 

**Reader Program**
```c
#include <stdio.h>
#include <sys/ipc.h>
#include <sys/msg.h>
struct msg_buffer
{
    long msg_type;
    char msg_text[100];
} message;
int main()
{
    key_t key;
    int msgid;
    key = ftok("process", 110);
    msgid = msgget(key, 0666 | IPC_CREAT);
    msgrcv(msgid, &message, sizeof(message), 1, 0);
    printf("Message Received is : %s \n", message.msg_text);
    msgctl(msgid, IPC_RMID, NULL);
    return 0;
}
```
**Writer Program**
```c
#include <stdio.h>
#include <sys/ipc.h>
#include <sys/msg.h>
#define MAX 20
struct msg_buffer
{
    long msg_type;
    char msg_text[100];
} message;
int main()
{
    key_t key;
    int msgid;
    key = ftok("process", 110);
    msgid = msgget(key, 0666 | IPC_CREAT);
    message.msg_type = 1;
    printf("Write Data : ");
    fgets(message.msg_text, MAX, stdin);
    msgsnd(msgid, &message, sizeof(message), 0);
    printf("Message queued : %s \n", message.msg_text);
    return 0;
}

```
---

