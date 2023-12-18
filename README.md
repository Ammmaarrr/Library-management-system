
#include<iostream>
#include<string>
#include<cstdlib> //used for clearing the screen
using namespace std;
//_________________struct___________________//
struct project {
    string book_nam[100];
    string author_name[100];
    string edition[100];
};
struct isu{
    string issubook[100];
    string issuauthorname[100];
    string issuedition[100];
    string student_name[100];
    string reg_no[100];
    string faculty[100];
};
project library;
isu ammar;
int total_books = 0;
int total_issu;
//---------------function to call to clear screen-------------------//
void clear_function(){
    system("cls");
}
//_____________ to view books_____________________//
void view(){
    clear_function();
    if ( total_books==0){
      cout <<"\t\tNo books found in the library\n ";
    }
    else{
    cout<<"List of books\n";
     cout<<"----------------------------------------------\n";
    for(int i=0;i<total_books;i++){
    cout<<i+1<<":";
    cout<<"book name:"<<library.book_nam[i]<<endl;
    cout<<"author name:"<<library.author_name[i]<<endl;
    cout<<"edition :"<<library.edition[i]<<endl;
    cout<<endl;}
  }
}
//_____________________----to see issued books-----_____________________//to see all the books issued,authore name,book edd , student name ,reg no,hostel no,
void view2(){
     clear_function();
    if (total_issu == 0) {
        cout << "No books have been issued yet.\n";
    } else {
            cout << "List of Issued Books:\n";
            cout<<"----------------------------------------------\n";
            for (int i = 0; i < total_issu; ++i) {
            cout << "Book " << i + 1 << ":\n";
            cout << "  Book Name: " << ammar.issubook[i] << endl;
            cout << "  Author Name: " << ammar.issuauthorname[i] << endl;
            cout << "  Edition: " << ammar.issuedition[i] << endl;
            cout << "  Student Name: " << ammar.student_name[i] << endl;
            cout << "  Registration Number: " << ammar.reg_no[i] << endl;
            cout << "  Faculty: " << ammar.faculty[i] << endl;
            cout << endl;
        }
    }
}
//___________add book function___________________//
void add() {//to add books
        clear_function();
        char addMore;
        cout<<"\t\t\t----enter book details---\n";
         cout<<"----------------------------------------------\n";
        cout << "\t\tEnter the book name: ";//ask the user to enter the book information       // isnt this function for the librarian
        cin >> library.book_nam[total_books];
        cout << "\t\tEnter the book author: ";
        cin >> library.author_name[total_books];
        cout << "\t\tEnter the book edition: ";
        cin >> library.edition[total_books];
        clear_function();
        if (total_books == 100) //check if the library is full
         { 
           cout << "Sorry, the library is full. Cannot add more books.\n";
           return;
         }
          total_books++;//increment the total number of books
          cout<<"----------------------------------------------\n";
          cout << "Book successfully added to the library.\n"; //display a confirmation message
           cout<<"----------------------------------------------\n";
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
//_____________ to delete books function_____________________//
 void del() 
{
   clear_function();
   string book_name; //ask the user to enter the book name
   view ();
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
      cout<<"----------------------------------------------\n";
     cout << "Book successfully deleted from the library.\n"; //display a confirmation message
     char delMore;
      cout<<"----------------------------------------------\n";
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
//_____________for issuing book_______________________//
void issue() {
    clear_function();
    string bookname, studentname, regno, faculty;
    view();
     cout<<"----------------------------------------------\n";
	 cout << "Enter the Book name: " << endl;
    cin >> bookname;
  cout<<"----------------------------------------------\n";
    for (int i = 0; i < total_books; i++) {
        if (library.book_nam[i] == bookname) {
            cout << "\t\t\tEnter your details" << endl;
            cout<<"----------------------------------------------\n";
            cout << "\t\tEnter your name: ";
            cin >> studentname;
            cout << "\t\tEnter your Registration number: ";
            cin >> regno;
            cout << "\t\tEnter your faculty: ";
            cin >> faculty;

            // Add the book details to the issued books struct
            ammar.issubook[total_issu] = library.book_nam[i];
            ammar.issuauthorname[total_issu] = library.author_name[i];
            ammar.issuedition[total_issu] = library.edition[i];
            ammar.student_name[total_issu] = studentname;
            ammar.reg_no[total_issu] = regno;
            ammar.faculty[total_issu] = faculty;

            // Increment the total issued books counter
            total_issu++;

            // Remove the book from the library by shifting elements after it to the left
            for (int j = i; j < total_books - 1; j++) {
                library.book_nam[j] = library.book_nam[j + 1];
                library.author_name[j] = library.author_name[j + 1];
                library.edition[j] = library.edition[j + 1];
            }

            total_books--; // Decrement the total number of books

            cout << "----------------------------------------------\n";
            cout << "Book has been issued, and it is removed from the library." << endl;
            cout << "----------------------------------------------\n";

            break;
        }
    }
}
//_________________________to return a book_____________________________//
void retur() {
    clear_function();
    string studname, bookname, regno, faculty;
    cout << "Enter book name: " << endl;
    cin >> bookname;

    for (int i = 0; i < total_issu; i++) {
        cout << "\t\t------Enter your details------" << endl;
        cout << "Enter your name: ";
        cin >> studname;
        cout << "Enter your registration number: ";
        cin >> regno;
        cout << "Enter your faculty: ";
        cin >> faculty;
       // clear_function();

        if (ammar.student_name[i] == studname &&
            ammar.reg_no[i] == regno &&
            ammar.faculty[i] == faculty &&
            ammar.issubook[i] == bookname) {
            
            // Add the book back to the library
            library.book_nam[total_books] = ammar.issubook[i];
            library.author_name[total_books] = ammar.issuauthorname[i];
            library.edition[total_books] = ammar.issuedition[i];

            // Increment the total number of books
            total_books++;

            // Remove the book from the issued books struct by shifting elements after it to the left
            for (int j = i; j < total_issu - 1; j++) {
                ammar.issubook[j] = ammar.issubook[j + 1];
                ammar.issuauthorname[j] = ammar.issuauthorname[j + 1];
                ammar.issuedition[j] = ammar.issuedition[j + 1];
                ammar.student_name[j] = ammar.student_name[j + 1];
                ammar.reg_no[j] = ammar.reg_no[j + 1];
                ammar.faculty[j] = ammar.faculty[j + 1];
            }

            total_issu--; // Decrement the total issued books counter

            cout << "----------------------------------------------\n";
            cout << "Book has been returned, and it is added back to the library." << endl;
            cout << "----------------------------------------------\n";

            break;
        } else {
            cout << "Book is not found or details are invalid." << endl;
        }
    }
}

//__________________________student menu_______________________________//
void stu_menu()
{      
       int stu_choice;
       clear_function();
       cout<<"\t\t\t\t---------WELCOME STUDENT--------"<<endl;
       do{
       cout<<"\t\t\t\t-----------  M E N U  -----------"<<endl;
       cout<<"\t\t\t\t _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ "<<endl;
       cout<<"\t\t\t\t|                               |"<<endl;
       cout<<"\t\t\t\t|  1:book list                  |"<<endl; 
       cout<<"\t\t\t\t|  2:return book                |"<<endl;
       cout<<"\t\t\t\t|  3:exit                       |"<<endl;
       cout<<"\t\t\t\t|_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _|"<<endl;
       cout<<endl;
       cout<<"\tenter your choice:";
       cin>>stu_choice;
       switch (stu_choice)
        {
        case 1:
         
          view();
        break;
        case 2:
          retur();
        break;
        case 3:
          return;
        break;
        default:
        cout<<"invalid input";
           stu_menu();
        break;
        }
      }
      while(stu_choice!=3);

}
//_________________________librarian menu__________________________________________//
void libr_menu(){
        int libr_choice;
        string name="admin";
        string passw="admin123";
        int i=3;
        do{   //used for loop for only three chances
            cout<<"\t\t\t-----for access enter your specified name and password(max tries are three only)-----"<<endl;
            cout<<"\t\tenter your NAME:";
            cin>>name;
            cout<<"\t\tenter your Password:";
            cin>>passw;
            clear_function();
            if(name=="admin" && passw=="admin123")
            {          
                       cout<<"\t\t\t\t--------- WELCOME LIBRARIAN--------"<<endl;
            do
             {        
                       cout<<"\t\t\t\t-----------  M E N U  -----------"<<endl;
                       cout<<"\t\t\t\t _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ "<<endl;
                       cout<<"\t\t\t\t|                               |"<<endl;
                       cout<<"\t\t\t\t|  1:Add Book                   |"<<endl; 
                       cout<<"\t\t\t\t|  2:Delete Book                |"<<endl;
                       cout<<"\t\t\t\t|  3:Book list                  |"<<endl;
                       cout<<"\t\t\t\t|  4:Issue Book                 |"<<endl;
                       cout<<"\t\t\t\t|  5:List Of Issued Books       |"<<endl;
                       cout<<"\t\t\t\t|  6:exit                       |"<<endl;
                       cout<<"\t\t\t\t|_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _|"<<endl;
                       cout<<endl;
                       cout<<"\t\tenter your choice:";
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
                         
                         issue();
                        
                       break;
                       case 5:
                         view2();
                         break;
                       case 6:
                         return;
                         cout<<"going back to main menu";
                       break;
                       default:
                         cout<<"invalid input";
                         libr_menu();
                       break;
                       }  
             }while(libr_choice!=6);
                    }  
                     else if (name != "admin" && passw != "admin123")
                     {
                           cout << "Invalid name and password.Try again\n";
                     } 
                     else if (name != "admin")
                     {
                           cout << "Invalid name.Try again\n";
                     } 
                    else if (passw != "admin123") 
                    {
                            cout << "Invalid password.Try again\n";
                    }
                          
                          i--;
          }              
                   while(i>0);
                   {
                     cout<<"you have reached maximum tryes\n";
                   }
}
//--------------------------------------------------------------------------------------------------------------------//
//___________________________MAIN MENU--------------------------------------------------------------------------------//
int main(){
   string choice;
   do{
   	  do{
        cout<<"\t\t\t ----WELCOME TO LIBRARY MANAGMENT SYSTEM----"<<endl;
        cout<<"\t\t\t\t-----------  M E N U  -----------"<<endl;
       cout<<"\t\t\t\t _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ "<<endl;
       cout<<"\t\t\t\t|                               |"<<endl;
       cout<<"\t\t\t\t|  1:Student                    |"<<endl; 
       cout<<"\t\t\t\t|  2:Librarian                  |"<<endl;
       cout<<"\t\t\t\t|  3:exit                       |"<<endl;
       cout<<"\t\t\t\t|_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _|"<<endl;
       cout<<"\t\tenter your choice:";
       cin>>choice;
         if(choice=="1")
  {    
     system("CLS");
     stu_menu();
    }
    else if(choice=="2"){
        system("CLS");
       
        libr_menu();
       
        }
       
          else if(choice=="3")
         {
          system("CLS");
          cout<<"&&&&&&&&&&  EXITING PROGRAM &&&&&&&&&&&&&&";
          return 0;
         }
         }while(choice=="1"||choice=="2"||choice=="3");

        }while(choice!="3");
}
