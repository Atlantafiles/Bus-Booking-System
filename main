#include<iostream.h>
  #include<iomanip.h>
  #include<conio.h>
  #include<fstream.h>
  #include<string.h>
  #include<stdio.h>
  #include<bios.h>
  #include<dos.h>
  #include<process.h>
  #define u 18432
  #define en 7181
  #define d 20480
  #define e 4709
  #define esc 283

void seat(char* dt1);
int check(char *n1);
void bookaticket();
void searchbydate(char *dt1);
void searchbydtsn(char dt1[10],char st[4]);
void searchbydtname(char dt1[10],char name[15]);
void rentonaday(char dt1[10]);
void vacantseat();
void border();
void mainmenu();
void intro();
void aboutus();
void enter();
void report();

    //START OF PROGRAM

    //start of class

class booking
{
    char dt[10];
    char name[15];
    long phoneno;
    char add[50];
    char gender[10];
    char n[4];
    int age;
    public:
    void entry()
    {
    clrscr();
    border();
        textcolor(YELLOW);
        gotoxy(3,3);cout<<"Press ENTER to enter data";
        gotoxy(4,5);cprintf("Enter passenger name (first name): ");
        gets(name);
        gotoxy(4,6);cprintf("Enter phone number : ");
        cin>>phoneno;
        gotoxy(4,7);cprintf("Enter passenger address (city): ");
        gets(add);
        gotoxy(4,8);cprintf("Enter gender (F/M/T): ");
        gets(gender);
        gotoxy(4,9);cprintf("Enter age: ");
        cin>>age;
        gotoxy(4,10);cprintf("Enter date (dd/mm/yy): ");
        cin>>dt;
        output();
        border();
        seat(dt);
        textcolor(YELLOW);
        gotoxy(3,3);cout<<"Press ENTER to enter data";
        gotoxy(4,5);cprintf("Enter seat no (e.g. A01): ");
        gets(n);
    }
    void output()
    {
        clrscr();
        gotoxy(48,3);
        cout<<"..........SEAT LAYOUT.........."<<endl;
        gotoxy(48,5);
        cout<<"      A     B         C    D  ";
        gotoxy(48,6);
        cout<<" 01   _   _    X    _   _ ";
        gotoxy(48,7);
        cout<<" 02   _   _    X    _   _ ";
        gotoxy(48,8);
        cout<<" 03   _   _    X    _   _ ";
        gotoxy(48,9);
        cout<<" 04   _   _    X    _   _ ";
        gotoxy(48,10);
        cout<<" 05   _   _    X    _   _ ";
        gotoxy(48,11);
        cout<<" 06   _   _    X    _   _ ";
        gotoxy(48,12);
        cout<<" 07   _   _    X    _   _ ";
        gotoxy(48,13);
        cout<<" 08   _   _    X    _   _ ";
        gotoxy(48,14);
        cout<<" 09   _   _    X    _   _ ";
        gotoxy(48,15);
        cout<<" 10   _   _    X    _   _ ";
        textcolor(YELLOW);
        gotoxy(48,17);
        cprintf("--B for already booked seats--");
    }

    void display(int &a,int &r)
    {
        int y=2;int l;
        if (a==0)
        {
        border();
        textcolor(YELLOW);
            gotoxy(2,3);cprintf("Date :");cout<<dt;cout<<"\n";
            textcolor(YELLOW);
            while(y<=75)
            {gotoxy(y,4);cprintf("%c",char(196));y++;}
            textcolor(WHITE);
            gotoxy(2,5);cprintf("Passenger Name");cout<<"\t"<<"\t";
            cprintf("Phone Number");cout<<"\t"<<"\t";
            cprintf("Gender");cout<<"\t"<<"\t";
            cprintf("Seat No.");cout<<"\n";a++;
            l=strlen(name);
            gotoxy(2,r);cout<<name;
            l=23-l;
            while(l>=0)
                {cout<<" ";l--;}
            cout<<phoneno<<"\t"<<"\t";
            cout<<gender<<"\t"<<"\t";
            cout<<n<<endl;
        }
        else
        {
            r++;
            gotoxy(2,r);cout<<name;
            l=strlen(name);
            gotoxy(2,r);cout<<name;
            l=23-l;
            while(l>=0)
                {cout<<" ";l--;}
            cout<<phoneno<<"\t"<<"\t";
            cout<<gender<<"\t"<<"\t";
            cout<<n<<endl;
        }
    }

     char*   getdt();
     char*   getname();
     char*   getn();
};

    //end of class

    //START OF ALL THE FUNCTIONS


    char* booking::getdt()
    {
        return dt;
    }
    char* booking::getn()
    {
        return n;
    }
    char* booking::getname()
    {
        return name;
    }

    void seat(char* dt1)
    {
        textcolor(YELLOW);
        ifstream fin1;
        char n1[4];
        int a;
        booking ob1;
        fin1.open("STD.DAT",ios::in|ios::binary);
        while(fin1.read((char*)&ob1,sizeof(ob1)))
        {
            if(strcmpi(ob1.getdt(),dt1)==0)
            {
                strcpy(n1,ob1.getn());
                if(n1[2]>=49)
                    a=n1[2]-43;
                else
                    a=15;

                if(n1[0]=='A')
                {
                    gotoxy(55,a);
                    cprintf("B");
                }
                else if(n1[0]=='B')
                {
                    gotoxy(60,a);
                    cprintf("B");
                }
                else if(n1[0]=='C')
                {
                    gotoxy(71,a);
                    cprintf("B");
                }
                else if(n1[0]=='D')
                {
                    gotoxy(76,a);
                    cprintf("B");
                }
            }
        }
        fin1.close();
    }

    int check(char * n1)
    {
        ifstream fin;
        booking obb;int c=0;
        fin.open("STD.DAT",ios::in|ios::binary);
        while(fin.read((char *)&obb,sizeof(obb)))
        {
            if(strcmpi(n1,obb.getn())==0)
                c=1;
        }
        return c;
    }


  void bookaticket()
 {
 clrscr();
 textcolor(YELLOW);
    ofstream fout;
    fout.open("STD.DAT",ios::app|ios::binary);
    booking ob;
    int k=0;char n1[4];
    ob.entry();
    k=check(ob.getn());
    if(k==1)
    {
        do
        {
            textcolor(RED+BLINK);
            gotoxy(4,6);cprintf("ALREADY BOOKED, retry!");
            seat(ob.getdt());
            gotoxy(29,5);cout<<"      ";
            gotoxy(4,3);cout<<"Press ENTER to enter data";
            textcolor(YELLOW);
            gotoxy(4,5);cprintf("Enter seat no (e.g. A01): ");
            gets(n1);
            strcpy(ob.getn(),n1);
            k=check(n1);
        }while(k>0);
    }
    gotoxy(4,6);cout<<"                          ";
    char y;
    gotoxy(4,8);cout<<"Do you want to save? Press Y for yes ";
    y=getch();
    if(y=='Y' || y== 'y')
    {
        fout.write((char *)&ob,sizeof(ob));
    }
    fout.close();
    long n;
    gotoxy(50,20);cout<<"Press ESC to go back";
    n=bioskey(0);
    if(n==esc)
    mainmenu();
 getch();
 }

void searchbydate(char *dt1)
{
    clrscr();
    border();
    ifstream fin;
    fin.open("STD.DAT",ios::in|ios::binary);
    booking ob;
    int c=0, dd=0,a=6;
    while(fin.read((char *)&ob,sizeof(ob)))
    {
        if(strcmpi(ob.getdt(),dt1)==0)
        {    c++;
            ob.display(dd,a);
        }
    }
    if(c==0)
    {
        textcolor(RED);
        gotoxy(25,10);cprintf("Sorry ! There is no such record found.");
    }
    fin.close();
    long n;
    gotoxy(50,20);cout<<"Press ESC to go back";
    n=bioskey(0);
    if(n==esc)
        report();
}

    void searchbydtsn(char dt1[10],char st[4])
    {
    clrscr();
    border();
        ifstream fin;
        booking ob; int c=0,a=6,dd=0;
        fin.open("STD.DAT",ios::in|ios::binary);
        while(fin.read((char*)&ob,sizeof(ob)))
        {
            if((strcmpi(dt1,ob.getdt())==0)&&(strcmpi(st,ob.getn())==0))
            {
                c++;
                ob.display(dd,a);
            }
        }
        if(c==0)
        {
                textcolor(RED);
                gotoxy(25,10);cprintf("Sorry ! There is no such record found.");
        }
        fin.close();
        long n;
        gotoxy(50,20);cout<<"Press ESC to go back";
        n=bioskey(0);
        if(n==esc)
            report();
    }

    void searchbydtname(char dt1[10],char name[15])
    {
    clrscr();
    border();
        ifstream fin;
        booking ob;int c=0,dd=0,a=6;
        fin.open("STD.DAT",ios::in|ios::binary);
        while(fin.read((char*)&ob,sizeof(ob)))
        {
            if((strcmpi(dt1,ob.getdt())==0)&&(strcmpi(name,ob.getname())==0))
             {
                c++;
                ob.display(dd,a);
             }
        }
        if(c==0)
        {
            textcolor(RED);
            gotoxy(25,10);cprintf("Sorry ! There is no such record found.");
        }
        fin.close();
        long n;
    gotoxy(50,20);cout<<"Press ESC to go back";
    n=bioskey(0);
    if(n==esc)
        report();
    }

    void rentonaday(char dt1[10])
    {
        border();
        long c=0;
        ifstream fin;
        booking ob;
        fin.open("STD.DAT",ios::in|ios::binary);
        while(fin.read((char*)&ob,sizeof(ob)))
        {
            if(strcmpi(dt1,ob.getdt())==0)
                c++;
        }
        gotoxy(10,10);textcolor(YELLOW);
        cprintf("Total rent collected :Rs.");cout<<c*800;
        gotoxy(10,11);cprintf("(Per seat = Rs. 800)");
        c=0;
        fin.close();
        long n;
        gotoxy(50,20);cout<<"Press ESC to go back";
        n=bioskey(0);
        if(n==esc)
            report();
    }

    void vacantseat()
    {
    clrscr();
    border();
        booking ob;
        char dt[10];
        textcolor(YELLOW);
        gotoxy(3,3);cout<<"Press ENTER to enter data";
        gotoxy(3,5);cprintf("Enter date to search (dd/mm/yy):");
        gets(dt);
        ob.output();
        border();
        seat(dt);
        gotoxy(10,4);cprintf("Your seat layout of date (");cout<<dt;cprintf(") :");
        long n;
        gotoxy(50,20);cout<<"Press ESC to go back";
        n=bioskey(0);
        if(n==esc)
            report();
    }


       void cancelaticket()
       {
       clrscr();
       border();
            ifstream fin;
            ofstream fout;
            char dtt[10],stno[4];
            textcolor(YELLOW);
            gotoxy(3,3);cout<<"Press ENTER to enter data";
            gotoxy(3,5);cprintf("Enter date of booking (dd/mm/yy): ");
            gets(dtt);
            gotoxy(3,6);cprintf("Enter seat number (e.g. A01): ");
            gets(stno);
            fin.open("STD.DAT",ios::in|ios::binary);
            fout.open("TEMP.DAT",ios::out|ios::binary);
            booking ob;
            int c=0,k=0;
            while(fin.read((char*)&ob,sizeof(ob)))
            {
                if(!(strcmpi(ob.getdt(),dtt)==0 && strcmpi(ob.getn(),stno)==0))
                {
                    fout.write((char*)&ob,sizeof(ob));
                    c++;
                }
                k++;
            }
            textcolor(RED);
            if (c>0 && k>c)
                {gotoxy(10,10);cprintf("Your seat is deleted!");}
            else
                {gotoxy(10,10);cprintf("Sorry ! There is no such record found.");}
            fout.close();
            fin.close();
            remove("STD.DAT");
            rename("TEMP.DAT","STD.DAT");
            long n;
            gotoxy(50,20);cout<<"Press ESC to go back";
            n=bioskey(0);
            if(n==esc)
                mainmenu();
       getch();
       }



    void border()
    {
        int c=2;
        textcolor(RED);
        gotoxy(1,2);cprintf("%c",char (201));
        while(c<=78)
        {gotoxy(c,2);cprintf("%c",char (205));c++;}
        gotoxy(79,2);cprintf("%c",char (187));
        gotoxy(1,24);cprintf("%c",char (200));
        c=2;
        while(c<=78)
        {gotoxy(c,24);cprintf("%c",char (205));c++;}
        gotoxy(79,24);cprintf("%c",char (188));
        int r=3;
        while(r<=23)
        {gotoxy(1,r);cprintf("%c",char (186));r++;}
        r=3;
        while(r<=23)
        {gotoxy(79,r);cprintf("%c",char (186));r++;}
    }
    void mainmenu()
    {
        clrscr();
        int r=12;
        long n;
        textcolor(WHITE);
        border();
        gotoxy(34,8);cprintf("MAIN MENU");
        gotoxy(50,21);cprintf("Press e to Exit");
        textcolor(YELLOW);
        gotoxy(35,12);cprintf("Entry");
            textcolor(WHITE);
        gotoxy(35,13);cprintf("Reports");
            textcolor(YELLOW);
        gotoxy(35,14);cprintf("Cancel a ticket");
            textcolor(CYAN);
        gotoxy(33,12);cprintf("->");
        while(2>1)
        {
            n=bioskey(0);
            if(n==d && r!=14)
            {
                gotoxy(33,r);cout<<"  ";r++;
                gotoxy(33,r);cprintf("->");
            }
            else if(n==u && r!=12)
            {
                gotoxy(33,r);cout<<"  ";r--;
                gotoxy(33,r);cprintf("->");
            }
            else if(n==e)
            {
                exit(0);
            }
            else if(n==en)
            {
                break;
            }
        }
        if (r==12)
            bookaticket();
        else if (r==13)
            report();
        else if (r==14)
            cancelaticket();

    }
    void aboutus()
    {
        clrscr();
        long n;
        border();
        textcolor(YELLOW);
        gotoxy(20,6);cprintf("--DEVELOPERS OF BUS-TICKET BOOKING SOFTWARE--");
        gotoxy(32,10);cprintf("1.ATLANTA GOGOI");
        gotoxy(32,11);cprintf("2.EGYPTA GOGOI");
        gotoxy(32,12);cprintf("3.MANJIMA BARUAH");
        gotoxy(32,13);cprintf("4.REBECCA ANGEL");
        gotoxy(22,16);cprintf("* (Special thanks to DEEPANKAR BHUYAN sir) *");
        gotoxy(35,18);cprintf("Happy Booking !");
        gotoxy(50,22);cprintf("Press ESC to go back");
        n=bioskey(0);
        if(n==esc)
            intro();
        getch();
    }

    void intro()
    {
        clrscr();
        long n;
        int k=12;
        border();
        textcolor(RED);
        gotoxy(31,8);
        cprintf("BUS-TICKET BOOKING");
        gotoxy(32,9);cprintf("(Digboi-Guwahati)");
        textcolor(YELLOW);
        gotoxy(35,12);
        cprintf("Main menu");
        textcolor(WHITE);
        gotoxy(35,13);
        cprintf("About us");
        textcolor(YELLOW);
        gotoxy(35,14);
        cprintf("Exit");
        textcolor(CYAN);
        gotoxy(33,12);
        cprintf("->");
        while(2>1)
        {
            n=bioskey(0);
            if(n==u && k!=12)
            {
                gotoxy(33,k);cout<<"  ";k--;
                gotoxy(33,k);cprintf("->");
            }
            else if(n==d && k!=14)
            {
                gotoxy(33,k);cout<<"  ";k++;
                gotoxy(33,k);cprintf("->");
            }
            else if(n==en)
            {
                break;
            }
        }
        if(k==12)
            mainmenu();
        else if(k==13)
            aboutus();
        else if(k==14)
            exit(0);

    }





    void report()
    {
        long x;int y=10;
        clrscr();
        border();
            gotoxy(50,20);cout<<"Press ESC to go back";
            textcolor(RED);gotoxy(12,8);cprintf("REPORTS");
                textcolor(YELLOW);
            gotoxy(10,10);cprintf("Search by date");
                textcolor(WHITE);
            gotoxy(10,11);cprintf("Search by date and seat number");
                textcolor(YELLOW);
            gotoxy(10,12);cprintf("Search by date and passenger name");
                textcolor(WHITE);
            gotoxy(10,13);cprintf("Total rent collection on a particular day");
                textcolor(YELLOW);
            gotoxy(10,14);cprintf("Display vacant seats");
                textcolor(CYAN);
            gotoxy(8,10);cprintf("->");
            while(2>1)
            {
                x=bioskey(0);
                if(x==u && y!=10)
                {
                    gotoxy(8,y);cout<<"  ";y--;
                    gotoxy(8,y);cprintf("->");
                }
                else if(x==d && y!=14)
                {
                    gotoxy(8,y);cout<<"  ";y++;
                    gotoxy(8,y);cprintf("->");
                }
                else if(x==en)
                    break;
                else if(x==esc)
                      mainmenu();
            }
            if (y==10)
            {
                clrscr();
                border();
                char dt[10];
                gotoxy(3,3);cout<<"Press ENTER to enter data";
                textcolor(YELLOW);
                gotoxy(3,5);cprintf("Enter date (dd/mm/yy): ");
                gets(dt);
                searchbydate(dt);
                getch();
            }
            else if(y==11)
            {
                clrscr();
                border();
                char dt[10],st[4];
                textcolor(YELLOW);
                gotoxy(3,3);cout<<"Press ENTER to enter data";
                gotoxy(3,5);cprintf("Enter date (dd/mm/yy): ");
                gets(dt);
                gotoxy(3,6);cprintf("Enter seat number (e.g. A01): ");
                gets(st);
                searchbydtsn(dt,st);
                getch();
            }
            else if(y==12)
            {
                clrscr();
                border();
                char dt[10],nm[40];
                textcolor(YELLOW);
                gotoxy(3,3);cout<<"Press ENTER to enter data";
                gotoxy(3,5);cprintf("Enter date (dd/mm/yy): ");
                gets(dt);
                gotoxy(3,6);cprintf("Enter passenger name (first name): ");
                gets(nm);
                searchbydtname(dt,nm);
                getch();
            }
            else if(y==13)
            {
                clrscr();
                border();
                char dt[10];
                textcolor(YELLOW);
                gotoxy(3,3);cout<<"Press ENTER to enter data";
                gotoxy(3,5);cprintf("Enter date (dd/mm/yy): ");
                gets(dt);
                rentonaday(dt);
                getch();
            }
            else if(y==14)
            {
                vacantseat();
            }

    }

    //END OF FUNCTION

void main()
{

        clrscr();
        intro();
}
    //END OF PROGRAM
