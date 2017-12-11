/*
 The demo of 徐爱昆  王玉芬 吴信昌
*/
#include<sys/types.h>
#include<stdio.h>
#include<unistd.h>
#include<stdlib.h>
/*****************************************
function:get childern's pid and ppid,get parent's pid
input	:None
output	:0
*****************************************/
int main()
{
	int p1,p2,i;//define the value of p1,p2,i 
	pid_t pid;//define pid
	while((p1=fork())==-1);//fork fail
	if(p1==0)//get the child 1
	{
		for(i=0;i<5;i++)//loop 5 times
		printf("I am child 1,pid is %d,ppid is %d,count %d\n",getpid(),getppid(),i);
	}
	else
	{
		while((p2=fork())==-1);//fork fail
		switch(p2)
		{
			case 0://get the child 2
				for(i=0;i<5;i++)//loop 5 times
				printf("I am child 2,pid is %d,ppid is %d,count %d\n",getpid(),getppid(),i);
			break;
			default://get the parent
				for(i=0;i<5;i++)//loop 5 times
				printf("I am parent,pid is %d,count %d\n",getpid(),i);
			break;
		}
	}
return 0;
}
