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

### Question 26
**Write a program to demonstrate the implementation of Inter Process Communication (IPC) using shared memory.**

**Client Code**
```c
#include <sys/types.h>
#include <sys/ipc.h>
#include <sys/shm.h>
#include <stdio.h>
#include <stdlib.h>
#define SHMSZ 27
main()
{
    int shmid;
    key_t key;
    char *shm, *s;
    key = 1269; // to get the segment created by server
    // Locate the segment. If not exists, exit.
    if ((shmid = shmget(key, SHMSZ, 0666)) < 0) 
    {
        perror("shmget");
        exit(1);
    }
    // Attach the segment to our data space. If unsuccesssful, exit.
    if ((shm = shmat(shmid, NULL, 0)) == (char *) -1)
    {
        perror("shmat");
        exit(1);
    }
    // Read the content of server
    for (s = shm; *s != NULL; s++)
        putchar(*s);
    putchar('\n');
    // Now change the first character of the segment to indicate we have read the segment.
    *shm = '#';
    exit(0);
}
```

**Server Code**
```c
#include <sys/shm.h>
#include <stdio.h>
#include<stdlib.h>
#define SHMSZ 27
int main()
{
    char c;
    int shmid;
    key_t key;
    char *shm, *s;
    key = 1269;
    if ((shmid = shmget(key, SHMSZ, IPC_CREAT | 0666)) < 0)
    {
        perror("shmget");
        exit(1);
    }
    if ((shm = shmat(shmid, NULL, 0)) == (char *) -1)
    {
        perror("shmat");
        exit(1);
    }
    //Put some things for the client to read.
    s = shm;
    char content[] = "Process is Now Running";
    for (int i=0; i<sizeof(content); i++)
        *s++ = content[i];
    *s = NULL;
    printf("Shared Memory Content: %s\n",shm);
    // Wait until client changes the first character of the segment, indicating that client has read the
    content of segment.
    while (*shm != '#')
        sleep(1);
    printf("Shared Memory Content: %s\n",shm);
    exit(0);
    return 0;
}
```
---

### Question 27
**Write a program to create a thread and let the thread check whether the given number is prime or not.**
```c
#include<stdio.h>
#include<stdlib.h>
#include<pthread.h>
#include<unistd.h>
#define MAX_THREAD
int n;
void *isPrime(void *vargp)
{
    if(n%2)
    printf("Odd Number\n");
    else
    printf("Even Number\n");
    int flag = 0;
    for(int i=2; i<n; i++)
    {
        if(n%i==0)
        {
            flag=1;
            break;
        }
    }
    if(flag)
        printf("Not Prime\n");
    else
        printf("Prime\n");
}
int main()
{
    printf("Enter the number :");
    scanf("%d",&n);
    pthread_t thread_id;
    printf("Thread Created\n");
    pthread_create(&thread_id, NULL, isPrime, NULL);
    (void)pthread_join(thread_id, NULL);
    printf("Thread Joined\n");
    exit(0);
    return 0;
}
```
---

### Question 28
**Implement FCFS, SJF, Priority and Round–Robin process scheduling algorithms.**

**FCFS**
```c
#include<stdio.h>
int main()
{
    int n,bt[20],wt[20],tat[20],avwt=0,avtat=0,i,j;
    printf("Enter total number of processes:");
    scanf("%d",&n);
    printf("\nEnter Process Burst Time\n");
    for(i=0;i<n;i++)
    {
        printf("P[%d]:",i+1);
        scanf("%d",&bt[i]);
    }
    wt[0]=0;
    for(i=1;i<n;i++)
    {
        wt[i]=0;
        for(j=0;j<i;j++)
            wt[i]+=bt[j];
    }
    printf("\nProcess\t\tBurst Time\tWaiting Time\tTurnaround Time");
    for(i=0;i<n;i++)
    {
        tat[i]=bt[i]+wt[i];
        avwt+=wt[i];
        avtat+=tat[i];
        printf("\nP[%d]\t\t%d\t\t%d\t\t%d",i+1,bt[i],wt[i],tat[i]);
    }
    avwt/=i;
    avtat/=i;
    printf("\n\nAverage Waiting Time:%d",avwt);
    printf("\nAverage Turnaround Time:%d\n",avtat);
    return 0;
}
```

**SJF**
```c
#include<stdio.h>
void main()
{
    int bt[20],p[20],wt[20],tat[20],i,j,n,total=0,pos,temp;
    float avg_wt,avg_tat;
    printf("Enter number of process:");
    scanf("%d",&n);
    printf("\nEnter Burst Time:\n");
    for(i=0;i<n;i++)
    {
        printf("p%d:",i+1);
        scanf("%d",&bt[i]);
        p[i]=i+1;
    }
    for(i=0;i<n;i++)
    {
        pos=i;
        for(j=i+1;j<n;j++)
        {
            if(bt[j]<bt[pos])
                pos=j;
        }
        temp=bt[i];
        bt[i]=bt[pos];
        bt[pos]=temp;
        temp=p[i];
        p[i]=p[pos];
        p[pos]=temp;
    }
    wt[0]=0;
    for(i=1;i<n;i++)
    {
        wt[i]=0;
        for(j=0;j<i;j++)
        wt[i]+=bt[j];
        total+=wt[i];
    }
    avg_wt=(float)total/n;
    total=0;
    printf("\nProcess\t Burst Time \tWaiting Time\tTurnaround Time");
    for(i=0;i<n;i++)
    {
        tat[i]=bt[i]+wt[i];
        total+=tat[i];
        printf("\np%d\t\t %d\t\t %d\t\t\t%d",p[i],bt[i],wt[i],tat[i]);
    }
    avg_tat=(float)total/n;
    printf("\n\nAverage Waiting Time=%f",avg_wt);
    printf("\nAverage Turnaround Time=%f\n",avg_tat);
}
```

**Priority**
```c
#include<stdio.h>
int main()
{
    int bt[20],p[20],wt[20],tat[20],pr[20],i,j,n,total=0,pos,temp,avg_wt,avg_tat;
    printf("Enter Total Number of Process:");
    scanf("%d",&n);
    printf("\nEnter Burst Time and Priority\n");
    for(i=0;i<n;i++)
    {
        printf("\nP[%d]\n",i+1);
        printf("Burst Time:");
        scanf("%d",&bt[i]);
        printf("Priority:");
        scanf("%d",&pr[i]);
        p[i]=i+1;
    }
    for(i=0;i<n;i++)
    {
        pos=i;
        for(j=i+1;j<n;j++)
        {
            if(pr[j]<pr[pos])
                pos=j;
        }
        temp=pr[i];
        pr[i]=pr[pos];
        pr[pos]=temp;
        temp=bt[i];
        bt[i]=bt[pos];
        bt[pos]=temp;
        temp=p[i];
        p[i]=p[pos];
        p[pos]=temp;
    }
    wt[0]=0;
    for(i=1;i<n;i++)
    {
        wt[i]=0;
        for(j=0;j<i;j++)
        wt[i]+=bt[j];
        total+=wt[i];
    }
    avg_wt=total/n;
    total=0;
    printf("\nProcess\t Burst Time \tWaiting Time\tTurnaround Time");
    for(i=0;i<n;i++)
    {
        tat[i]=bt[i]+wt[i];
        total+=tat[i];
        printf("\nP[%d]\t\t %d\t\t %d\t\t\t%d",p[i],bt[i],wt[i],tat[i]);
    }
    avg_tat=total/n;
    printf("\n\nAverage Waiting Time=%d",avg_wt);
    printf("\nAverage Turnaround Time=%d\n",avg_tat);
    return 0;
}
```

**Round-Robins**
```c
#include<stdio.h>
int main()
{
    int count,j,n,time,remain,flag=0,time_quantum;
    int wait_time=0,turnaround_time=0,at[10],bt[10],rt[10];
    printf("Enter Total Process:\t ");
    scanf("%d",&n);
    remain=n;
    for(count=0;count<n;count++)
    {
        printf("Enter Arrival Time and Burst Time for Process Process Number %d:",count+1);
        scanf("%d",&at[count]);
        scanf("%d",&bt[count]);
        rt[count]=bt[count];
    }
    printf("Enter Time Quantum:\t");
    scanf("%d",&time_quantum);
    printf("\n\nProcess\t|Turnaround Time|Waiting Time\n\n");
    for(time=0,count=0;remain!=0;)
    {
        if(rt[count]<=time_quantum && rt[count]>0)
        {
            time+=rt[count];
            rt[count]=0;
            flag=1;
        }
        else if(rt[count]>0)
            {
            rt[count]-=time_quantum;
            time+=time_quantum;
        }
        if(rt[count]==0 && flag==1)
        {
            remain--;
            printf("P[%d]\t|\t%d\t|\t%d\n",count+1,time-at[count],time-at[count]-bt[count]);
            wait_time+=time-at[count]-bt[count];
            turnaround_time+=time-at[count];
            flag=0;
        }
        if(count==n-1)
            count=0;
        else if(at[count+1]<=time)
            count++;
        else
            count=0;
    }
    printf("\nAverage Waiting Time= %f\n",wait_time*1.0/n);
    printf("Avg Turnaround Time = %f",turnaround_time*1.0/n);
    return 0;
}
```
---

### Question 29
**Write a program to perform a tidy exit on receipt of an interrupt signal.**
```c
#include <stdio.h>
#include <stdlib.h>
#include <signal.h>
FILE *temp_file;
void leave(int sig);
int main()
{
    (void)signal(SIGINT, leave);
    temp_file = fopen("tmp", "w");
    for (;;)
    {
        printf("Ready...\n");
        (void)getchar();
    }
    exit(EXIT_SUCCESS);
    return 0;
}
void leave(int sig)
{
    printf("\nSIGINT Recieved, Exiting\n");
    fprintf(temp_file, "\nInterrupted..\n");
    fclose(temp_file);
    exit(sig);
}

```
---

### Question 30
**Implement a) Binary Semaphore b) Counting Semaphore.**
**Binary Semaphore.**
```c
#include <stdio.h>
#include <pthread.h>
#include <semaphore.h>
int a, b;
sem_t sem;
void ScanNumbers(void *ptr){
    for (;;){
        printf("%s", (char *)ptr);
        scanf("%d %d", &a, &b);
        sem_post(&sem);
        usleep(100 * 10);
    }
}
void SumAndPrint(void *ptr){
    for (;;){
        sem_wait(&sem);
        printf("%s %d\n", (char *)ptr, a + b);
    }
}
int main()
{
    pthread_t thread1;
    pthread_t thread2;
    char *Msg1 = "Enter The Two Numbers : \n";
    char *Msg2 = "sum = ";
    sem_init(&sem, 0, 0);
    pthread_create(&thread1, NULL, (void *)ScanNumbers, (void *)Msg1);
    pthread_create(&thread2, NULL, (void *)SumAndPrint, (void *)Msg2);
    pthread_join(thread1, NULL);
    pthread_join(thread2, NULL);
    printf("Wait For Both Thread Finished\n");
    sem_destroy(&sem);
    return 0;
}

```
**Counting Semaphore.**
```c
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <semaphore.h>
#include <unistd.h>
#include <time.h>
#define NO_OF_QUEUE 5 /* #of Students in queue */
#define NO_OF_SLOTS 3 /* Lab Capacity */
int Q[NO_OF_SLOTS];
int front = -1;
int rear = -1;
int c = 0; /*Counting sem*/
pthread_mutex_t mutex;
sem_t full;
sem_t empty;
void *Supervisor(void *arg){
    while( c < -5) { /* Supervisor limit */
        int student = (int)arg;
        pthread_detach(pthread_self());
        sem_wait(&empty);
        pthread_mutex_lock(&mutex);
        rear = rear + 1;
        if (rear >= NO_OF_SLOTS){
            rear = 0;
        }
        Q[rear] = student;
        printf("%4d.Student was called to the presentation \n", student+1);
        pthread_mutex_unlock(&mutex);
        sem_post(&full);
    }
    c--;
    printf(" Counting value c after decremented by Supervisor : %d\n",c);
}
void *Student(void *arg){
    int student = 0;
    int studentRemoved= 0;
    printf("Presentations started \n");
    while (studentRemoved < NO_OF_QUEUE){
        sem_wait(&full);
        pthread_mutex_lock(&mutex);
        front = front + 1;
        if (front >= NO_OF_SLOTS ) front = 0;
        student = Q[front];
        printf("%4d. Student is done. He was removed from the queue \n", student+1);
        studentRemoved++;
        pthread_mutex_unlock(&mutex);
        sem_post(&empty);
        c++;
        printf("Counting value after the c incremented by the Student : %d \n",c);
        usleep((int)(drand48()*500000));
    }
}
int main(int argc,char *argv[]){
    int i;
    pthread_t supervisorid;
    pthread_t queueId;
    srand48(time(NULL));
    pthread_mutex_init(&mutex,NULL);
    sem_init(&full, 0, 5);
    sem_init(&empty, 0, NO_OF_SLOTS);
    /* Supervisor Thread */
    pthread_create(&queueId, NULL, Student, NULL);
    for(i=0; i < NO_OF_QUEUE;i++){
        pthread_create(&supervisorid, NULL, Supervisor , (void *)i);
    }
    pthread_join(queueId, NULL);
}
```
---


### Question 31
**Write a program to demonstrate the implementation of Producer and Consumer problem**
```c
#include <pthread.h>
#include <semaphore.h>
#include <stdlib.h>
#include <stdio.h>
#define MaxItems 5 // Maximum items a producer can produce or a consumer can consume
#define BufferSize 5 // Size of the buffer
sem_t empty;
sem_t full;
int in = 0;
int out = 0;
int buffer[BufferSize];
pthread_mutex_t mutex;
void *producer(void *pno)
{
    int item;
    for(int i = 0; i < MaxItems; i++) {
        item = rand() % 100; // Produce an random item
        sem_wait(&empty);
        pthread_mutex_lock(&mutex);
        buffer[in] = item;
        printf("Producer %d: Insert Item %d at %d\n", *((int *)pno),buffer[in],in);
        in = (in+1)%BufferSize;
        pthread_mutex_unlock(&mutex);
        sem_post(&full);
    }
}
void *consumer(void *cno)
{
    for(int i = 0; i < MaxItems; i++) {
        sem_wait(&full);
        pthread_mutex_lock(&mutex);
        int item = buffer[out];
        printf("Consumer %d: Remove Item %d from %d\n",*((int *)cno),item, out);
        out = (out+1)%BufferSize;
        pthread_mutex_unlock(&mutex);
        sem_post(&empty);
    }
}
int main()
{
    pthread_t pro[5],con[5];
    pthread_mutex_init(&mutex, NULL);
    sem_init(&empty,0,BufferSize);
    sem_init(&full,0,0);
    int a[5] = {1,2,3,4,5}; //Just used for numbering the producer and consumer
    for(int i = 0; i < 5; i++) {
        pthread_create(&pro[i], NULL, (void *)producer, (void *)&a[i]);
    }
    for(int i = 0; i < 5; i++) {
        pthread_create(&con[i], NULL, (void *)consumer, (void *)&a[i]);
    }
    for(int i = 0; i < 5; i++) {
        pthread_join(pro[i], NULL);
    }
    for(int i = 0; i < 5; i++) {
        pthread_join(con[i], NULL);
    }
    pthread_mutex_destroy(&mutex);
    sem_destroy(&empty);
    sem_destroy(&full);
    return 0;
}

```
---


### Question 32
**Write a program to implement Reader – Writer’s problem.**
```c
#include <pthread.h>
#include <semaphore.h>
#include <stdio.h>
sem_t wrt;
pthread_mutex_t mutex;
int cnt = 1;
int numreader = 0;
void *writer(void *wno)
{
    sem_wait(&wrt);
    cnt = cnt*2;
    printf("Writer %d: modified count to %d\n",(*((int *)wno)),cnt);
    sem_post(&wrt);
}
void *reader(void *rno)
{
    pthread_mutex_lock(&mutex);
    numreader++;
    if(numreader == 1) {
        sem_wait(&wrt);
    }
    pthread_mutex_unlock(&mutex);
    printf("Reader %d: read count as %d\n",*((int *)rno),cnt);
    pthread_mutex_lock(&mutex);
    numreader--;
    if(numreader == 0) {
        sem_post(&wrt);
    }
    pthread_mutex_unlock(&mutex);
}
int main()
{
    pthread_t read[10],write[5];
    pthread_mutex_init(&mutex, NULL);
    sem_init(&wrt,0,1);
    int a[10] = {1,2,3,4,5,6,7,8,9,10};
    for(int i = 0; i < 10; i++) {
        pthread_create(&read[i], NULL, (void *)reader, (void *)&a[i]);
    }
    for(int i = 0; i < 5; i++) {
        pthread_create(&write[i], NULL, (void *)writer, (void *)&a[i]);
    }
    for(int i = 0; i < 10; i++) {
        pthread_join(read[i], NULL);
    }
    for(int i = 0; i < 5; i++) {
        pthread_join(write[i], NULL);
    }
    pthread_mutex_destroy(&mutex);
    sem_destroy(&wrt);
    return 0;
}

```
---


### Question 33
**Write a program to implement Dining Philosopher’s problem. Implement Banker’s algorithm.**
**Dining Plilosopher**
```c
#include<stdio.h>

#define n 4
int compltedPhilo = 0, i;
struct fork {
    int taken;
}
ForkAvil[n];
struct philosp {
    int left;
    int right;
}
Philostatus[n];
void goForDinner(int philID) {
    if (Philostatus[philID].left == 10 && Philostatus[philID].right == 10)
        printf("Philosopher %d completed his dinner\n", philID + 1);
    else if (Philostatus[philID].left == 1 && Philostatus[philID].right == 1) {
        printf("Philosopher %d completed his dinner\n", philID + 1);
        Philostatus[philID].left = Philostatus[philID].right = 10;
        int otherFork = philID - 1;
        if (otherFork == -1)
            otherFork = (n - 1);
        ForkAvil[philID].taken = ForkAvil[otherFork].taken = 0;
        printf("Philosopher %d released fork %d and fork%d\n", philID + 1, philID + 1, otherFork + 1);
        compltedPhilo++;
    }
    else if (Philostatus[philID].left == 1 && Philostatus[philID].right == 0) {
        if (philID == (n - 1)) {
            if (ForkAvil[philID].taken == 0) {
                ForkAvil[philID].taken = Philostatus[philID].right = 1;
                printf("Fork %d taken by philosopher %d\n", philID + 1, philID + 1);
            } else {
                printf("Philosopher %d is waiting for fork %d\n", philID + 1, philID + 1);
            }
        } else {
            int dupphilID = philID;
            philID -= 1;
            if (philID == -1)
                philID = (n - 1);
            if (ForkAvil[philID].taken == 0) {
                ForkAvil[philID].taken = Philostatus[dupphilID].right = 1;
                printf("Fork %d taken by Philosopher %d\n", philID + 1, dupphilID + 1);
            } else {
                printf("Philosopher %d is waiting for Fork %d\n", dupphilID + 1, philID + 1);
            }
        }
    }
    else if (Philostatus[philID].left == 0) {
        if (philID == (n - 1)) {
            if (ForkAvil[philID - 1].taken == 0) {
                ForkAvil[philID - 1].taken = Philostatus[philID].left = 1;
                printf("Fork %d taken by philosopher %d\n", philID, philID + 1);
            } else {
                printf("Philosopher %d is waiting for fork %d\n", philID + 1, philID);
            }
        } else {
            if (ForkAvil[philID].taken == 0) {
                ForkAvil[philID].taken = Philostatus[philID].left = 1;
                printf("Fork %d taken by Philosopher %d\n", philID + 1, philID + 1);
            } else {
                printf("Philosopher %d is waiting for Fork %d\n", philID + 1, philID + 1);
            }
        }
    }
}
int main() {
    for (i = 0; i < n; i++)
        ForkAvil[i].taken = Philostatus[i].left = Philostatus[i].right = 0;
    while (compltedPhilo < n) {
        for (i = 0; i < n; i++)
            goForDinner(i);
        printf("\nTill now no. of philosophers completed dinner are: %d\n\n", compltedPhilo);
    }
    return 0;
}

```
**Banker**
```c
#include <stdio.h>
int main() {
    int Max[10][10], need[10][10], alloc[10][10], avail[10], completed[10], safeSequence[10];
    int p, r, i, j, process, count;
    count = 0;
    printf("Enter the no of processes : ");
    scanf("%d", & p);
    for (i = 0; i < p; i++)
        completed[i] = 0;
    printf("\n\nEnter the no of resources : ");
    scanf("%d", & r);
    printf("\n\nEnter the Max Matrix for each process : ");
    for (i = 0; i < p; i++) {
        printf("\nFor process %d : ", i + 1);
        for (j = 0; j < r; j++)
            scanf("%d", & Max[i][j]);
    }
    printf("\n\nEnter the allocation for each process : ");
    for (i = 0; i < p; i++) {
        printf("\nFor process %d : ", i + 1);
        for (j = 0; j < r; j++)
            scanf("%d", & alloc[i][j]);
    }
    printf("\n\nEnter the Available Resources : ");
    for (i = 0; i < r; i++)
        scanf("%d", & avail[i]);
    for (i = 0; i < p; i++)
        for (j = 0; j < r; j++)
            need[i][j] = Max[i][j] - alloc[i][j];
    do {
        printf("\n Max matrix:\tAllocation matrix:\n");
        for (i = 0; i < p; i++) {
            for (j = 0; j < r; j++)
                printf("%d ", Max[i][j]);
            printf("\t\t");
            for (j = 0; j < r; j++)
                printf("%d ", alloc[i][j]);
            printf("\n");
        }
        process = -1;
        for (i = 0; i < p; i++) {
            if (completed[i] == 0) //if not completed
            {
                process = i;
                for (j = 0; j < r; j++) {
                    if (avail[j] < need[i][j]) {
                        process = -1;
                        break;
                    }
                }
            }
            if (process != -1)
                break;
        }
        if (process != -1) {
            printf("\nProcess %d runs to completion!", process + 1);
            safeSequence[count] = process + 1;
            count++;
            for (j = 0; j < r; j++) {
                avail[j] += alloc[process][j];
                alloc[process][j] = 0;
                Max[process][j] = 0;
                completed[process] = 1;
            }
        }
    } 
    while (count != p && process != -1);
    if (count == p) {
        printf("\nThe system is in a safe state!!\n");
        printf("Safe Sequence : < ");
        for (i = 0; i < p; i++)
            printf("%d ", safeSequence[i]);
        printf(">\n");
    }
    else
        printf("\nThe system is in an unsafe state!!");
}

```
---


### Question 34
**Implement the First Fit, Best Fit and Worst Fit file allocation strategy.**
**First Fit**
```c
#include<stdio.h>
void main()
{
    int bsize[10], psize[10], bno, pno, flags[10], allocation[10], i, j;
    for(i = 0; i < 10; i++)
    {
        flags[i] = 0;
        allocation[i] = -1;
    }
    printf("Enter no. of blocks: ");
    scanf("%d", &bno);
    printf("\nEnter size of each block: ");
    for(i = 0; i < bno; i++)
    scanf("%d", &bsize[i]);
    printf("\nEnter no. of processes: ");
    scanf("%d", &pno);
    printf("\nEnter size of each process: ");
    for(i = 0; i < pno; i++)
    scanf("%d", &psize[i]);
    for(i = 0; i < pno; i++)
    for(j = 0; j < bno; j++)
    if(flags[j] == 0 && bsize[j] >= psize[i])
    {
        allocation[j] = i;
        flags[j] = 1;
        break;
    }
    printf("\nBlock no.\tsize\t\tprocess no.\t\tsize");
    for(i = 0; i < bno; i++)
    {
        printf("\n%d\t\t%d\t\t", i+1, bsize[i]);
        if(flags[i] == 1)
            printf("%d\t\t\t%d",allocation[i]+1,psize[allocation[i]]);
        else
            printf("Not allocated");
    }
}
```
**Best Fit**
```c
#include<stdio.h>
void main()
{
    int fragment[20],b[20],p[20],i,j,nb,np,temp,lowest=9999;
    static int barray[20],parray[20];
    printf("\nEnter the number of blocks: ");
    scanf("%d",&nb);
    printf("Enter the number of processes: ");
    scanf("%d",&np);
    printf("\nEnter the size of the blocks:-\n");
    for(i=1;i<=nb;i++)
    {
        printf("Block no.%d: ",i);
        scanf("%d",&b[i]);
    }
    printf("\nEnter the size of the processes:-\n");
    for(i=1;i<=np;i++)
    {
        printf("Process no.%d :",i);
        scanf("%d",&p[i]);
    }
    for(i=1;i<=np;i++)
    {
        for(j=1;j<=nb;j++)
        {
            if(barray[j]!=1)
            {
                temp=b[j]-p[i];
                if(temp>=0)
                if(lowest>temp)
                {
                    parray[i]=j;
                    lowest=temp;
                }
            }
        }
        fragment[i]=lowest;
        barray[parray[i]]=1;
        lowest=10000;
    }
    printf("\nProcess_no\tProcess_size\tBlock_no\tBlock_size\tFragment");
    for(i=1;i<=np && parray[i]!=0;i++)
        printf("\n%d\t\t%d\t\t%d\t\t%d\t\t%d",i,p[i],parray[i],b[parray[i]],fragment[i]);
    printf("\n");
}

```
**Worst Fit**
```c
#include<stdio.h>
int main()
{
    int fragments[10], blocks[10], files[10];
    int m, n, number_of_blocks, number_of_files, temp, top = 0;
    static int block_arr[10], file_arr[10];
    printf("\nEnter the Total Number of Blocks:\t");
    scanf("%d",&number_of_blocks);
    printf("Enter the Total Number of Files:\t");
    scanf("%d",&number_of_files);
    printf("\nEnter the Size of the Blocks:\n");
    for(m = 0; m < number_of_blocks; m++)
    {
        printf("Block No.[%d]:\t", m + 1);
        scanf("%d", &blocks[m]);
    }
    printf("Enter the Size of the Files:\n");
    for(m = 0; m < number_of_files; m++)
    {
        printf("File No.[%d]:\t", m + 1);
        scanf("%d", &files[m]);
    }
    for(m = 0; m < number_of_files; m++)
    {
        for(n = 0; n < number_of_blocks; n++)
        {
            if(block_arr[n] != 1)
            {
                temp = blocks[n] - files[m];
                if(temp >= 0)
                {
                    if(top < temp)
                    {
                        file_arr[m] = n;
                        top = temp;
                    }
                }
            }
            fragments[m] = top;
            block_arr[file_arr[m]] = 1;
            top = 0;
        }
    }
    printf("\nFile Number\tFile Size\tBlock Number\tBlock Size\tFragment");
    for(m = 0; m < number_of_files; m++)
    {
        printf("\n%d\t\t%d\t\t%d\t\t%d\t\t%d", m, files[m], file_arr[m], blocks[file_arr[m]],
        fragments[m]);
    }
    printf("\n");
    return 0;
}

```
---