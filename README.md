\\ Library-management-system giki
  #include<iostream>
#include<string>
#include<cstdlib> //used for clearing the screen
using namespace std;

struct project {
    string book_nam[100];
    string author_name[100];
    string edition[100];
    string student_name[100];
    int reg_no[100];
    int hostel_no[100];
};
project library;
int total_books = 0;
void add() {//to add books
        char addMore;
        cout << "Enter the book name: ";//ask the user to enter the book information
        cin >> library.book_nam[total_books];
        cout << "Enter the book author: ";
        cin >> library.author_name[total_books];
        cout << "Enter the book edition: ";
        cin >> library.edition[total_books];
        if (total_books == 100) //check if the library is full
         { 
           cout << "Sorry, the library is full. Cannot add more books.\n";
           return;
         }
          total_books++;//increment the total number of books
          cout << "Book successfully added to the library.\n"; //display a confirmation message
          cout << "Do you want to add more books? (y/n): ";
          cin >> addMore;
           if (addMore == 'y' || addMore == 'Y') 
           {
                      add(); // Recursively call add() function to add more books
           }  
           else if (addMore == 'n' || addMore == 'N') {// Optionally provide an exit message or return to the menu
        
     } else {
        cout << "Invalid input. Returning to the main menu." << endl;
     }
}
 void del() //to delete books
{
   string book_name; //ask the user to enter the book name
   cout << "Enter the book name to delete: ";
   cin >> book_name;
   int index = -1; //search for the book in the library array
   for (int i = 0; i < total_books; i++)
    {
      if (library.book_nam[i] == book_name) 
      {
        index = i;
        break;
      }
    }
    if (index == -1) //check if the book is found
    {
      cout << "Sorry, the book is not found in the library.\n";
      return;
    }
    for (int i = index; i < total_books - 1; i++) //delete the book by shifting all the elements after it to the left
     {
      library.book_nam[i] = library.book_nam[i + 1];
      library.author_name[i] = library.author_name[i + 1];
      library.edition[i] = library.edition[i + 1];
     }
     total_books--;//decrement the total number of books
     cout << "Book successfully deleted from the library.\n"; //display a confirmation message
     char delMore;
     cout << "Do you want to delete more books? (y/n): ";
     cin >> delMore;
     if (delMore == 'y' || delMore == 'Y')
        {
          del(); // Recursively call del() function to delete more books
        }
      else if (delMore == 'n' || delMore == 'N')
       {
        // Optionally provide an exit message or return to the menu
       } else
       {
        cout << "Invalid input. Returning to the main menu." << endl;
       }
}
void view(){
  system("cls");
  for(int i=0;i<=total_books;i++){
    cout<<"book name:"<<library.book_nam[i]<<endl;
    cout<<"authore name:"<<library.author_name[i]<<endl;
    cout<<"edition :"<<library.edition[i]<<endl;
    cout<<endl;
  }
}//to view all the books present
void issu_view(){}//to see all the books issued,authore name,book edd , student name ,reg no,hostel no,
void issue(){}//to issue a book
void retur(){}//to return a book
int main()
{
   int choice,stu_choice,libr_choice;
   do{
   cout<<"_____________MENU_______________"<<endl;
   cout<<"  1:student \n";
   cout<<"  2:librarian\n";
   cout<<"  3:exit\n";
   cout<<"enter your choice:";
   cin>>choice;
  if(choice==1)
  {    
       system("CLS");
       do{
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
          main();
        break;
        default:
           cout<<"invalid input";
        break;
        }
      }
      while(stu_choice!=4);
    }
    else if(choice==2){
        system("CLS");
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
             do
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
                   main();
                    cout<<"going back to main menu";
                 break;
                 default:
                   cout<<"invalid input";
                 break;
                }  
             }while(libr_choice!=4);
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
       else if(choice==3)
         {
          system("CLS");
          cout<<"&&&&&&&&&&  EXITING PROGRAM &&&&&&&&&&&&&&";
          return 0;
         }
     }while(choice!=3);
  } 
   
//work need to be done :::::
//use outer do will loop in main func  for all the program 
//user inner loops for student and librarian where exit will help them go out to main menu
//make thee function
