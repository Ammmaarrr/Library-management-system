\\ Library-management-system giki
#include<iostream>
#include<string>
#include<fstream>
#include<cstdlib> //used for clearing the screen
using namespace std;

struct project {
    string book_nam[100];
    string author_name[100];
    int edition[100];
    string student_name[100];
    int reg_no[100];
    int hostel_no[100];
};
project library;
int total_books = 0;
void add(){}//to add books
void del(){}//to remove books
void view(){}//to view all the books present
void issu_view(){}//to see all the books issued,authore name,book edd , student name ,reg no,hostel no,
void issue(){}//to issue a book
void retur(){}//to return a book
int main()
{
   int choice,stu_choice,libr_choice;
   cout<<"_____________MENU_______________"<<endl;
   cout<<"  1:student \n";
   cout<<"  2:librarian\n";
   cout<<"  3:exit\n";
   cout<<"enter your choice:";
   cin>>choice;
  if(choice==1)
  {    
       system("CLS");
       cout<<"**********welcome student**********\n";
       cout<<"_____________MENU_______________\n";// use switch for studen menu
       cout<<"1:book list\n";
       cout<<"2:issue book\n";
       cout<<"3:return book\n";
       cout<<"4:exit\n";
       cout<<"enter your choice";
       cin>>stu_choice;
       switch (stu_choice)
        {
        case 1:
          view();
        break;
        case 2:
          issue();
        break;
        case 3:
          retur();
        break;
        case 4:
          return 0;
        break;
        default:
           cout<<"invalid input";
        break;
        }
    }
    else if(choice==2)
        {system("CLS");
        string name="admin";
        string passw="admin123";
        int i=3;
        do{   //used for loop for only three chances
            cout<<"      **** for access enter your specified name and password **** max tries are three only"<<endl;
            cout<<"enter your NAME:";
            cin>>name;
            cout<<"enter your Password:";
            cin>>passw;
            system("CLS");
            if(name=="admin" && passw=="admin123")
            {
             cout<<"**********welcome LIBRARIYAN**********\n";//use switch for librian
             cout<<"_____________MENU_______________\n";
             cout<<"1:add books\n";
             cout<<"2:delete books:\n";
             cout<<"3:books list:\n";
             cout<<"4:view list of issued books\n";
             cout<<"5:exit\n";
             cout<<"enter your choice:";
             cin>>libr_choice;
             switch (libr_choice)
             {
             case 1:
                    add();
             break;
             case 2:
                    del();
             break;
             case 3:
                   view();
             break;
             case 4:
                   issu_view();
             break;
             case 5:
                   return 0;
             break;
             default:
                 cout<<"invalid input";
              break;
             }  
           }  else if (name != "admin" && passw != "admin123")
                    {
                      cout << "Invalid name and password.Try again\n";
                    }  else if (name != "admin")
                        {
                           cout << "Invalid name.Try again\n";
                        } else if (passw != "admin123") {
                             cout << "Invalid password.Try again\n";
                        }
                          i--;
                   }              
                   while(i>0);{
              cout<<"you have reached maximum tryes\n";
              return 0;
            }
        }
          else if(choice==3){
          system("CLS");
          cout<<"&&&&&&&&&&  EXITING PROGRAM &&&&&&&&&&&&&&";
          return 0;
      }
}     
   
//work need to be done :::::
//use outer do will loop in main func  for all the program 
//user inner loops for student and librarian where exit will help them go out to main menu
//make thee function
