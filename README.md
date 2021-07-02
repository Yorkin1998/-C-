# -C-
C语言期末大作业/学生成绩管理系统/宁波大学

#include<stdio.h>// main input output library
#include<string.h> //include the string library
#include<stdlib.h> // include stdlib library for exit() system("cls") 
#define N 100 // suppose we have 100 students
struct STU{    //defining the structure
	char name[25]; //defining student`s name 25characters for each
	char ID[11]; //defining the student`s number 11 characters for each
	int math,english,computer,all;//student`s subjects
	char classname[150];//defining class name
}; 
STU stu[N]; //changing stu for having many relationship
int n=0;//Define the global variable n, which represents the number of members in the structure.
int MAIN_MENU_FUNCTION()//menu function
{
	int choice_number;//defining number for choosing menu list
	do{
	printf("\n\t\tMain Menu\n");
	printf("   ________________________________\n");
	printf("  | 1 Add student information      |\n");
	printf("  | 2 Show student's information   |\n");
	printf("  | 3 Search student information   |\n");
	printf("  | 4 Delete student information   |\n");
	printf("  | 5 Input student information    |\n");
	printf("  | 6 Sort                         |\n");
	printf("  | 0 Exit                         |\n");
	printf("  |________________________________|\n");
	printf("\n\tINPUT NUMBER IN MENU:");
	scanf("%d",&choice_number);
	}while(choice_number<0||choice_number>6);
	return choice_number;//return number for switch function
}
void INPUT_STUDENT_INFORMATION()//input student information function
{
	system("cls");//console will clears the screen
	char k,x[10];
	while(k!='n' and k!='N')//the loop for inputting st informations respectively till N or n
	{
		printf("Enter the student ID:");
		scanf("%s",stu[n].ID);
		printf("Enter the student name:");
		scanf("%s",stu[n].name);
		printf("Enter the student class:");
		scanf("%s",stu[n].classname);
		printf("Enter the math score:");
		scanf("%d",&stu[n].math);
		printf("Enter the english score:");
		scanf("%d",&stu[n].english);
		printf("Enter the computer score:");
		scanf("%d",&stu[n].computer);
		stu[n].all=stu[n].math+stu[n].english+stu[n].computer;
		gets(x);
		printf("Do you want to add next? (Y/N))\n");//asks Y or N if N it will stops loop
		scanf("%c",&k);
		n++;
	}
}
void OUTPUT_INFORMATION_FUNCTION()//output function
{
	system("cls");
	int i;
	printf("----------------------------------------------------------------------------------------------\n");
	printf("Student ID |   Name    |   Classname    |       Math  |   English |  Computer  |   Overall\n");
	printf("----------------------------------------------------------------------------------------------\n");
	for(i=0;i<n;i++)//loop for output
	{
		printf("%-14s%-14s%-14s%-14d%-14d%-14d%-14d\n",stu[i].ID,stu[i].name,stu[i].classname,stu[i].math,stu[i].english,stu[i].computer,stu[i].all);
		printf("---------------------------------------------------------------------------------------------\n");
	}	
}
void DELETE_STUDENT_INFORMATION_FUNCTION()//delete selecting function
{
	system("cls");
	char x[8];
	int j,i=0;
	printf("Enter the student name for delete:");//for deleting you should enter st.name
	scanf("%s",x);
	while(strcmp(stu[i].name,x)!=0&&i<n)
		i++;
	if(i==n)//If there is not available so not found
	{
		printf("Not found!\n");
	}
	for(j=i;j<n-1;j++)//deleting loop
	{
		strcpy(stu[j].ID,stu[j+1].ID);
		strcpy(stu[j].name,stu[j+1].name);
		strcpy(stu[j].classname,stu[j+1].classname);
		stu[j].math=stu[j+1].math;
		stu[j].english=stu[j+1].english;
		stu[j].computer=stu[j+1].computer;
		stu[j].all=stu[j+1].all;
	}
	n--;
	printf("SUCCESSFULLY DELETED!\n");
}
void FINDING_STUDENT_BY_NAME()//finds st.information by name
{
	system("cls");
	char s[20];
	int i=0;
	printf("Enter the name which you want to search:");//you should enter student name for this
	scanf("%s",s);
	while(strcmp(stu[i].name,s)!=0&&i<n)
		i++;
	if(i==n)
	{
		printf("Not found\n");	
	}
	printf("----------------------------------------------------------------------------------------------\n");
	printf("Student ID |   Name    |   Classname    |       Math  |   English |  Computer  |   Overall\n");
	printf("----------------------------------------------------------------------------------------------\n");
	printf("%-14s%-14s%-14s%-14d%-14d%-14d%-14d\n",stu[i].ID,stu[i].name,stu[i].classname,stu[i].math,stu[i].english,stu[i].computer,stu[i].all);
	printf("---------------------------------------------------------------------------------------------\n");
}
void FINDING_STUDENT_BY_ID()//finds st.information by ID
{
	system("cls");
	char s[20];
	int i=0;
	printf("Enter the ID which you want to search:");//you should enter student ID for this
	scanf("%s",s);
	while(strcmp(stu[i].ID,s)!=0&&i<n)
		i++;
	if(i==n)
	{
		printf("Not found\n");	
	}
	printf("----------------------------------------------------------------------------------------------\n");
	printf("Student ID |   Name    |   Classname    |       Math  |   English |  Computer  |   Overall\n");
	printf("----------------------------------------------------------------------------------------------\n");
	printf("%-14s%-14s%-14s%-14d%-14d%-14d%-14d\n",stu[i].ID,stu[i].name,stu[i].classname,stu[i].math,stu[i].english,stu[i].computer,stu[i].all);
	printf("---------------------------------------------------------------------------------------------\n");			
}
void INSERT_BY_POSITION()
{
	system("cls");
	int i,j;
	printf("Enter the position for insert:");
	scanf("%d",&i);
	if(i>n)
	{
		printf("Enter the student ID:");
		scanf("%s",stu[n].ID);
		printf("Enter the student name:");
		scanf("%s",stu[n].name);
		printf("Enter the student class:");
		scanf("%s",stu[n].classname);
		printf("Enter the math score:");
		scanf("%d",&stu[n].math);
		printf("Enter the english score:");
		scanf("%d",&stu[n].english);
		printf("Enter the computer score:");
		scanf("%d",&stu[n].computer);
		stu[n].all=stu[n].math+stu[n].english+stu[n].computer;
		printf("Sucessfully added!\n");
	}
	else
	{
		for(j=n-1;j>=i;j--)
		{
			strcpy(stu[j+1].ID,stu[j].ID);
			strcpy(stu[j+1].name,stu[j].name);
			strcpy(stu[j+1].classname,stu[j].classname);
			stu[j+1].math=stu[j].math;
			stu[j+1].english=stu[j].english;
			stu[j+1].computer=stu[j].computer;
			stu[j+1].all=stu[j].all;	
		}
		printf("Enter the student ID:");
		scanf("%s",stu[n].ID);
		printf("Enter the student name:");
		scanf("%s",stu[n].name);
		printf("Enter the student class:");
		scanf("%s",stu[n].classname);
		printf("Enter the math score:");
		scanf("%d",&stu[n].math);
		printf("Enter the english score:");
		scanf("%d",&stu[n].english);
		printf("Enter the computer score:");
		scanf("%d",&stu[n].computer);
		stu[n].all=stu[n].math+stu[n].english+stu[n].computer;
		printf("Sucessfully added!\n");
	}
	n++;
}
void SORTING_FUNCTION()//Sort added information
{
	system("cls");
	int i,j,p,q,r;
	double y;
	char x[20],t[10],w[10];
	printf("Sorting by student number, please wait..\n");
	for(i=0;i<n-1;i++)
		for(j=0;j<n-1-i;j++)
			if(strcmp(stu[j].ID,stu[j+1].ID)>0)
				{	
					strcpy(t,stu[j].ID);
					strcpy(stu[j].ID,stu[j+1].ID);
					strcpy(stu[j+1].ID,t);
					strcpy(x,stu[j].name);
					strcpy(stu[j].name,stu[j+1].name);
					strcpy(stu[j+1].name,x);
					strcpy(w,stu[j].classname);
					strcpy(stu[j].classname,stu[j+1].classname);
					strcpy(stu[j+1].classname,w);
					y=stu[j].math;
					stu[j].math=stu[j+1].math;
					stu[j+1].math=y;
					p=stu[j].english;
					stu[j].english=stu[j+1].english;
					stu[j+1].english=p;
					q=stu[j].computer;
					stu[j].computer=stu[j+1].computer;
					stu[j+1].computer=q;
					r=stu[j].all;
					stu[j].all=stu[j+1].all;
					stu[j+1].all=r;
				}
}
int Find()
{
	system("cls");
	int i;
	printf("\t\t1.Search by Name\n\t\t2.Search by ID\n");
	scanf("%d",&i);
	return i;
}
int main()
{
	for(;;)
	{
		for(;;)
		{
			int n=0;
			switch(MAIN_MENU_FUNCTION())
			{
				case 1: 
						INPUT_STUDENT_INFORMATION();
						OUTPUT_INFORMATION_FUNCTION();
							break;
				case 2: 
					OUTPUT_INFORMATION_FUNCTION();
					break;
				case 3:
					switch(Find())
					{
						case 1: 
							FINDING_STUDENT_BY_NAME();
								break;
						case 2: 
							FINDING_STUDENT_BY_ID();
								break;	
					}break;
				case 4: 
					DELETE_STUDENT_INFORMATION_FUNCTION();
						break;
				case 5: 
					INSERT_BY_POSITION();
						break;
				case 6: 
					SORTING_FUNCTION();
						break;
				case 0: 
					exit(0);
						break;
				default: 
					printf("Error! please enter valid number");
						break;	
			}
		}
	}
	return 0;
}

