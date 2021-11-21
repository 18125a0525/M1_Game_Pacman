CODE:

#include <graphics.h>
#include<conio.h>
#include <stdlib.h>
#include<dos.h>

void m_right(int,int,int,int);
void m_left(int,int,int,int);
void m_up(int,int,int,int);
void m_down(int,int,int,int);
void grid();

int main(void)
{

int gdriver = DETECT, gmode;
int xmax, ymax;
initgraph(&gdriver, &gmode, “”);
//==============MAIN FUNCTIONS=================//
grid();
m_right(80,360,560,360);
m_up(560,360,560,80);
m_left(560,80,80,80);
m_down(80,80,80,360);
getch();
clrscr();
settextstyle(0,0,4);
outtextxy(160,160,”GAME OVER”);
settextstyle(0,0,2);
getch();
return 0;
}
//=========FUNCTION FOR GRID FORMATION============//
void grid()
{ setcolor(8);
outtextxy(400,460,”Pacman”);
setcolor(9);
for(int i=40;i<640;i++)
{for(int j=40;j<480;j++)
{if(i%40==0&&j%40==0)
{outtextxy(i,j,”x”);
}
}
}
}
//=============FUNTION FOR MOVING RIGHT========//
void m_right(int a,int b,int c,int d)
{
int s,e;
s=30,e=330;
for(int k=a;k<c;k++)
{if(s==0)
{s=30;e=330;
}
setfillstyle(SOLID_FILL,14);
pieslice(k,b,s,e,25);
setfillstyle(SOLID_FILL,0);
pieslice(k,b-15,0,360,5);
setcolor(0);
delay(15);
circle(k,b,25);
s=s-1;e=e+1;
}
}
//=========FUNCTION FOR MOVING LEFT===========//
void m_left(int a,int b,int c,int d)
{
int s,e;
s=150,e=210;
for(int k=a;k>c;k–)
{if(s==180)
{s=150;e=210;
}
setfillstyle(SOLID_FILL,14);
pieslice(k,b,0,360,25);
setfillstyle(SOLID_FILL,0);
pieslice(k,b-15,0,360,5);
pieslice(k,b,s,e,25);
setcolor(0);
delay(15);
circle(k,b,25);
s=s+1;e=e-1;
}
}
//========FUNCTION FOR MOVING UP=============//
void m_up(int a,int b,int c,int d)
{ int s,e;
s=60,e=120;
for(int l=b;l>d;l–)
{if(s==90)
{s=60;e=120;
}
setfillstyle(SOLID_FILL,14);
pieslice(a,l,0,360,25);
setfillstyle(SOLID_FILL,0);
pieslice(a-15,l,0,360,5);
pieslice(a,l,s,e,25);
setcolor(0);
delay(15);
circle(a,l,25);
s=s+1;e=e-1;
}
}

 

//========FUNCTION FOR MOVING DOWN==============//
void m_down(int a,int b,int c,int d)
{ int s,e;
s=250,e=300;
for(int l=b;l<d;l++)
{if(s==270)
{s=250;e=300;
}
setfillstyle(SOLID_FILL,14);
pieslice(a,l,0,360,25);
setfillstyle(SOLID_FILL,0);
pieslice(a-15,l,0,360,5);
pieslice(a,l,s,e,25);
setcolor(0);
delay(15);
circle(a,l,25);
s=s+1;e=e-1;
}
}
