# sem1
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <locale.h>
struct file
{
	char name[16],gender[7],bday[11];
	int znak;
};

int main()
{
	setlocale(LC_ALL,"");
	FILE* list=fopen("C:/Users/Денис/Desktop/list.txt","r");
	int n=1;
	struct file* list1=(struct file*)malloc(n*sizeof(struct file));
	while(fscanf(list,"%s%s%s",list1[n-1].name,list1[n-1].gender,list1[n-1].bday)!=EOF)
	{
		if ((list1[n-1].znak=atoi(list1[n-1].bday)+atoi(&list1[n-1].bday[3])*100)>=1222)
			list1[n-1].znak*=-1;
		list1=(struct file*)realloc(list1,++n*sizeof(struct file));
	}
	n--;
	for(int j=0;j<n-1;j++)
		if (list1[j].bday[3]==list1[n-1].bday[3]&&list1[j].bday[4]==list1[n-1].bday[4])
			printf ("%15s%8s%12s\n",list1[j].name,list1[j].gender,list1[j].bday);
	int d=0;
	for (int i=0;i<n;i++)
	{
		for (int j=n-1;j>i;j--)
			if (list1[j-1].znak>list1[j].znak)
			{
				list1[n]=list1[j-1];
				list1[j-1]=list1[j];
				list1[j]=list1[n];
			}
		if (list1[i].znak<=120)
		{
			if (!d) printf ("\nКозерог\n");
			printf ("%15s%8s%12s\n",list1[i].name,list1[i].gender,list1[i].bday);
			d=1;
		}
		else if (list1[i].znak<=218)
			{
				if (d<=1) printf ("\nВодолей\n");
				printf ("%15s%8s%12s\n",list1[i].name,list1[i].gender,list1[i].bday);
				d=2;
			}
			else if (list1[i].znak<=320)
				{
					if (d<=2) printf ("\nРыбы\n");
					printf ("%15s%8s%12s\n",list1[i].name,list1[i].gender,list1[i].bday);
					d=3;
				}
				else if (list1[i].znak<=420)
					{
						if (d<=3) printf ("\nОвен\n");
						printf ("%15s%8s%12s\n",list1[i].name,list1[i].gender,list1[i].bday);
						d=4;
					}
					else if (list1[i].znak<=520)
						{
							if (d<=4) printf ("\nТелец\n");
							printf ("%15s%8s%12s\n",list1[i].name,list1[i].gender,list1[i].bday);
							d=5;
						}
						else if (list1[i].znak<=621)
							{
								if (d<=5) printf ("\nБлизнецы\n");
								printf ("%15s%8s%12s\n",list1[i].name,list1[i].gender,list1[i].bday);
								d=6;
							}
							else if (list1[i].znak<=722)
								{
									if (d<=6) printf ("\nРак\n");
									printf ("%15s%8s%12s\n",list1[i].name,list1[i].gender,list1[i].bday);
									d=7;
								}
								else if (list1[i].znak<=823)
									{
										if (d<=7) printf ("\nЛев\n");
										printf ("%15s%8s%12s\n",list1[i].name,list1[i].gender,list1[i].bday);
										d=8;
									}
									else if (list1[i].znak<=923)
										{
											if (d<=8) printf ("\nДева\n");
											printf ("%15s%8s%12s\n",list1[i].name,list1[i].gender,list1[i].bday);
											d=9;
										}
										else if (list1[i].znak<=1023)
											{
												if (d<=9) printf ("\nВесы\n");
												printf ("%15s%8s%12s\n",list1[i].name,list1[i].gender,list1[i].bday);
												d=10;
											}
											else if (list1[i].znak<=1122)
												{
													if (d<=10) printf ("\nСкорпион\n");
													printf ("%15s%8s%12s\n",list1[i].name,list1[i].gender,list1[i].bday);
													d=11;
												}
												else if (list1[i].znak<=1221)
													{
														if (d<=11) printf ("\nСтрелец\n");
														printf ("%15s%8s%12s\n",list1[i].name,list1[i].gender,list1[i].bday);
														d=12;
													}
	}
	fclose(list);
	free(list1);
	printf ("\n");
	return 0;
}
