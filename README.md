#include<stdio.h>
#include<windows.h>
#include<conio.h>

#define row 9
#define col 11
char map[row][col+1]=
{
	{"*#*********"},
	{"***###*###*"},
	{"###**#****#"},
	{"*#**###**#*"},
	{"***********"},
	{"#####*##*##"},
	{"**#*****#*E"},
	{"***#*###**#"},
	{"*#*********"},
};

void print_map()
{
	int i;
	for(i=0;i<row;i++)
	{
		puts(map[i]);
	}
}

void show_cursor(int x,int y)
{
	COORD pos;
	pos.X=x;
	pos.Y=y;
	printf("curX=%d,curY=%d\n",x,y);
	SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE),pos);
}

int curX,curY;
int main()
{
	char t;
	while(1)
	{
		system("cls");
		print_map();
		show_cursor(curX,curY);

		t=getch();
		if(t=='w')
		{
			if((curY-1)>=0&&(map[curY-1][curX]=='*'||map[curY-1][curX]=='E'))curY--;
		}
		else if(t=='s')
		{
			if((curY+1)<row&&(map[curY+1][curX]=='*'||map[curY+1][curX]=='E'))curY++;
		}
		else if(t=='a')
		{
			if((curX-1)>=0&&(map[curY][curX-1]=='*'||map[curY][curX-1]=='E'))curX--;
		}
		else if(t=='d')
		{
			if((curX+1)<col&&(map[curY][curX+1]=='*'||map[curY][curX+1]=='E'))curX++;
		}
		if(map[curY][curX]=='E')
		{
			break;
		}
	}
	return 0;
}
