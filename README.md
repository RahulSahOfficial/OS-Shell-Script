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
