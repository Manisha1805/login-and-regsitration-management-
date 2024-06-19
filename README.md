# login-and-regsitration-management-
#include<iostream>
#include<istream>
#include<fstream>
#include<string.h>
#include<stdlib.h>
using namespace std;

void login();
void registration();
void forgot();

int main()
{
 int c;
 cout<<"\t\t\t______________________________________________\n\n\n";
 cout<<"\t\t\t              Welcome to the login page        \n\n\n";
 cout<<"\t\t\t______________________MENU_____________________\n\n\n";
 cout<<"                                                      \n\n\n";
 cout<<"\t|press 1 to LOGIN                    |"<<endl;
 cout<<"\t|press 2 to REGISTER                 |"<<endl;
 cout<<"\t|press 3 if you forgot you password  |"<<endl;
 cout<<"\t|press 4 to EXIT                     |"<<endl;
 cout<<"\n\t\t\t Please enter your choice : ";
 
 switch(c){

    case 1:
         login();
         break;

    case 2:
         registration();
         break;

    case 3:
        forgot();
        break;
    
    case 4:
        cout<<"\t\t\t Thank You \n\n\n";
        break;
    
    default:
        system("cls");
        cout<<"\t\t\t Please select the options given above \n"<<endl;
        main();
 }  

}

void login()
{
    int count ;
    string userID ,password,id,pass;
    system("cls");
    cout<<"\t\t\t Please enter the username and password :"<<endl;
    cout<<"\t\t\t USERNAME ";
    cin>>userID;
    cout<<"\t\t\t PASSWORD ";
    cin>>password;
    
    ifstream input("record.txt");

    while(input>>id>>pass)
    {
        if(id==userID && pass==password)
        {
            count=1;
            system("cls");
        }
        
    }
    input.close();
    if(count==1)
    {
        cout<<userID<<"\n YOUR login is successfull\n Thanks for logging in !"<<endl;
        main();
    }
    else
    {
        cout<<"\n Login error \n Please check your username and password ";
        main();
    }
}
void registration()
{
        string ruserID,rpassword,rid,rpass;
        system("cls");
        cout<<"\n Enter the username :";
        cin>>ruserID;
        cout<<"\n Enter the password :";
        cin>>rpassword;
        ofstream f1("records.txt",ios::app);
        f1<<ruserID<<' '<<rpassword<<endl;
        system("cls");
        cout<<"\n\t\t\t Registration is successfull! \n";
        main();
}
void forgot()
   { 
       int option;
       system("cls");
       cout<<"\t\t\t You forget the password? no worries \n";
       cout<<"press 1 to search your ID by username"<<endl;
       cout<<"press 2 to go back to the main menu"<<endl;
       cout<<"\t\t\t Enter your choice :";
       cin>>option;
       switch(option)
       {
        case 1:
            { int count=0;
            string suserID,sID,spass;
            cout<<"\n\t\t Enter the username which your remembered : ";
            cin>>suserID;

            ifstream f2("records.txt");
            while(f2>>sID>>spass)
               { 
                if(sID==suserID)
                 {
                    count=1;
                 }
               }
               f2.close();
               if(count==1)
               {
                cout<<"\n\n\n Your account is found ! \n ";
                cout<<"\n\n\n Your password is :"<<spass;
               }
               else{
                cout<<"\n\t Sorry your account is not found ! \n";
               }
             
            }
        case 2:
            {
                main();

            }
        default:
        cout<<"\t\t\t Wrong choice ! Please try again"<<endl;
        forgot();
       }
    }
