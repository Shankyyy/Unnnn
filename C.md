# Unnnn
DBMS
1.LIBRARY MANAGEMENT
2.TIC TAC TOE
3.ARITHMATIC OPERATOR
4.ARRAY POINTERS
5.CALLBYREFERENCE
6.INVERSE WORDS
7.STUDENT MANAGEMENT
8.STAROne
9.PRIME NUMBER OR NOT
10.INLINE FUNCTION
11.ACCOUNT DETAILS 
12.EMPLOYEE DEPARTMENT
13.CUBE WITH ARRAY
14.HEADER FILE ONE
15.HEADER FILE TWO
16.INHERITANCE
17.FUNCTION OVERLOADING
18.RESULT CODE
19.CLASS
20.CONSTRUCTOR
21.FUNCTION OVERLOADING
22.COPY CONSTRUCTOR
23.FRIEND FUNCTION
24.ALL
25.CONSTRUCTO OVERLOADING
26.Destructor
27.FUNCTION OVERLOADING
28.HIERARCHICAL
29.OPERATOR OVERLOADING
30.STRUCTURES
31.ALL2
32.Header3



1.LIBRARY MANAGEMENT

using namespace std;
class Books
{
public:
    string name,author,dept;
    string page,price;
    Books()
    {
        name="Unknown";
        author="Anonymous";
        page="Undetermined";
        price="Priceless";
        dept="Miscellaneous";
    }
    Books(string bname,string bauthor)
    {
        name=bname;
        author=bauthor;
        page="Undetermined";
        price="Priceless";
        dept="Miscellaneous";
    }
    Books(string bauthor,string bname,string bpage,string bprice,string bdept)
    {
        name=bname;
        author=bauthor;
        page=bpage;
        price=bprice;
        dept=bdept;
    }
    void Display()
    {
        cout<<"Book Name "<<name<<" Author: "<<author<<" Pages: "<<page<<" Price: "<<price<<" Department: "<<dept<<endl;
    }
};
class Library
{
public:
    int _count=0;
    int i;
    int choice;
    string name,author,page,price,dept;
    Books current[10];
    Books book;
    void Add()
    {
        cout<<"Enter 1 if you have no Data of Book"<<endl<<"2 if you have only Book Name and Author"<<endl<<"3 if you have all details"<<endl;
        cin>>choice;
        switch(choice)
        {
        case 1:
            book= Books();
            current[_count]=book;
            _count++;
            break;
        case 2:
            cout<<"Enter Book Name"<<endl;
            cin>>name;
            cout<<"Enter Author Name"<<endl;
            cin>>author;
            book=Books(name,author);
            current[_count]=book;
            _count++;
            break;
        case 3:
            cout<<"Enter Book Name"<<endl;
            cin>>name;
            cout<<"Enter Book Author"<<endl;
            cin>>author;
            cout<<"Enter Book Pages"<<endl;
            cin>>page;
            cout<<"Enter Book Price"<<endl;
            cin>>price;
            cout<<"Enter Book Department"<<endl;
            cin>>dept;
            book=Books(author,name,page,price,dept);
            current[_count]=book;
            _count++;
            break;
        default:
            cout<<"Invalid Input"<<endl;
            break;
        }


    }
    void Display()
    {
        for(i=0;i<_count;i++)
        {
            current[i].Display();
        }
    }
    void WithDraw()
    {
        cout<<"Choose Index to withdraw"<<endl;
        cin>>choice;
        if(choice>_count)
        {
            cout<<"Invalid Index"<<endl;
        }
        else
        {
            for(i=choice;i<_count;i++)
            {
                if(i==9)
                {
                    _count--;
                }
                else
                {
                    current[i]=current[i+1];
                    _count--;
                }
            }
        }
    }
    void Count()
    {
        cout<<"Number of Books is "<<_count<<endl;
    }
};
int main()
{
    Library lib;
    int choice=1;
    while(choice!=5)
    {
        cout<<"Enter 1 to Add Book"<<endl<<"Enter 2 to Display Book"<<endl<<"Enter 3 to Withdraw Book"<<endl<<"Enter 4 to display number of books"<<endl<<"Enter 5 to Exit"<<endl;
        cin>>choice;
        switch(choice)
        {
        case 1:
            lib.Add();
            break;
        case 2:
            lib.Display();
            break;
        case 3:
            lib.WithDraw();
            break;
        case 4:
            lib.Count();
            break;
        case 5:
            cout<<"Thank you"<<endl;
            break;
        default:
            cout<<"Invalid Input"<<endl;
        }
    }

}





2.TIC TAC TOE



#include <iostream>

using namespace std;

char square[10] = {'o','1','2','3','4','5','6','7','8','9'};

int checkwin();
void board();

int main()
{
	int player = 1,i,choice;

	char mark;
	do
	{
		board();
		player=(player%2)?1:2;

		cout << "Player " << player << ", enter a number:  ";
		cin >> choice;

		mark=(player == 1) ? 'X' : 'O';

		if (choice == 1 && square[1] == '1')

			square[1] = mark;
		else if (choice == 2 && square[2] == '2')

			square[2] = mark;
		else if (choice == 3 && square[3] == '3')

			square[3] = mark;
		else if (choice == 4 && square[4] == '4')

			square[4] = mark;
		else if (choice == 5 && square[5] == '5')

			square[5] = mark;
		else if (choice == 6 && square[6] == '6')

			square[6] = mark;
		else if (choice == 7 && square[7] == '7')

			square[7] = mark;
		else if (choice == 8 && square[8] == '8')

			square[8] = mark;
		else if (choice == 9 && square[9] == '9')

			square[9] = mark;
		else
		{
			cout<<"Invalid move ";

			player--;
			cin.ignore();
			cin.get();
		}
		i=checkwin();

		player++;
	}while(i==-1);
	board();
	if(i==1)

		cout<<"==>\aPlayer "<<--player<<" win ";
	else
		cout<<"==>\aGame draw";

	cin.ignore();
	cin.get();
	return 0;
}


int checkwin()
{
	if (square[1] == square[2] && square[2] == square[3])

		return 1;
	else if (square[4] == square[5] && square[5] == square[6])

		return 1;
	else if (square[7] == square[8] && square[8] == square[9])

		return 1;
	else if (square[1] == square[4] && square[4] == square[7])

		return 1;
	else if (square[2] == square[5] && square[5] == square[8])

		return 1;
	else if (square[3] == square[6] && square[6] == square[9])

		return 1;
	else if (square[1] == square[5] && square[5] == square[9])

		return 1;
	else if (square[3] == square[5] && square[5] == square[7])

		return 1;
	else if (square[1] != '1' && square[2] != '2' && square[3] != '3'
                    && square[4] != '4' && square[5] != '5' && square[6] != '6'
                  && square[7] != '7' && square[8] != '8' && square[9] != '9')

		return 0;
	else
		return -1;
}


void board()
{

	cout << "\n\n\tTic Tac Toe\n\n";

	cout << "Player 1 (X)  -  Player 2 (O)" << endl << endl;
	cout << endl;

	cout << "     |     |     " << endl;
	cout << "  " << square[1] << "  |  " << square[2] << "  |  " << square[3] << endl;

	cout << "_____|_____|_____" << endl;
	cout << "     |     |     " << endl;

	cout << "  " << square[4] << "  |  " << square[5] << "  |  " << square[6] << endl;

	cout << "_____|_____|_____" << endl;
	cout << "     |     |     " << endl;

	cout << "  " << square[7] << "  |  " << square[8] << "  |  " << square[9] << endl;

	cout << "     |     |     " << endl << endl;

}



3.ARITHMATIC OPERATOR


using namespace std;
class AO
{
public:
    int sum,mul,sub;
    double div;
    int Sum(int a,int b)
    {
        sum = a+b;
        cout<<sum;
        return sum;
    }
    int Mul(int a,int b)
    {
        mul = a*b;
        cout<<mul;
        return mul;
    }
    int Sub(int a,int b)
    {
        sub = a-b;
        cout<<sub;
        return sub;
    }
    double Div(int a,int b)
    {
        div = a/b;
        cout<<div;
        return div;
    }
};
int main()
{
    int x,y;
    char ch;
    AO obj;
    cout<<"Enter 1st number:";
    cin>>x;
    cout<<"Enter 2n number:";
    cin>>y;
    cout<<"Enter a choice +,-,*,/:";
    cin>>ch;
    switch(ch)
    {
    case '+':
        obj.Sum(x,y);
        break;
    case '-':
        obj.Sub(x,y);
        break;
    case '*':
        obj.Mul(x,y);
        break;
    case '/':
        obj.Div(x,y);
        break;
    default:
        cout<<"Wrong Input!!, Try again...";
        break;
    }
    return 0;
}


4.ARRAY POINTERS

using namespace std;

int main()
{
    int num[3] = {10,20,30};
    int *ptr[3];
    for(int i=0; i<3;i++)
    {
        ptr[i] = &num[i]; //Assign the address of integers
    }
    for(int i=0;i<3;i++)
    {
        cout<<"Value of numbers["<<i<<"]=";
        cout<<*ptr[i]<<endl;
    }
    return 0;
}


5.CALLBYREFERENCE


using namespace std;

void swap(int &x, int &y);
void change(int,int);

void swap(int &x, int &y) //Call By Reference (Permanent value and address changes)
{
    int temp;
    temp = x;
    x = y;
    y = temp;
}
void change(int x, int y) //Call By Value (Only copy of the value will be passed)
{
    int temp;
    temp = x;
    x = y;
    y = temp;
}
int main()
{
    int a = 100;
    int b = 200;
    cout<<"Before swapping, value of a:"<<a<<endl;
    cout<<"Before swapping, value of b:"<<b<<endl;
    swap(a,b); //Call by Reference
    cout<<"After swapping, value of a:"<<a<<endl;
    cout<<"After swapping, value of b:"<<b<<endl;
    change(a,b);
    cout<<"After changing, value of a:"<<a<<endl;
    cout<<"After changing, value of b:"<<b<<endl;
    return 0;
}


6.INVERSE WORDS


#include <iostream>

#include<string.h>
using namespace std;

int main()
{
   char str[20], temp;
   int i,j;
   cout<<"Enter a word:";
    cin>>str;
   j = strlen(str)-1;
   for(i=0;i<j;i++)
   {
       temp = str[i];
       str[i] = str[j];
       str[j] = temp;
       j--;
   }
    cout<<"Reverse: "<<str;
}


7.STUDENT MANAGEMENT


using namespace std;

class Student
{
    public:
    string name,rollno;
    Student()
    {

    }
    Student(string sname,string roll)
    {
        name=sname;
        rollno=roll;
    }
    void CheckPass(string sub1,int marks1,string sub2,int marks2,string sub3,int marks3)
    {
        if((marks1>40)&&(marks2>40)&&(marks3>40))
        {
            cout<<name<<" With Roll Number "<<rollno<<" You Have Passed In "<<sub1<<", "<<sub2<<", "<<sub3<<endl;
        }
        else
        {
            cout<<name<<" With Roll Number "<<rollno<< "Mission Failed"<<endl;
        }
    }
    void CheckPass(string sub1,int marks1,string sub2,int marks2)
    {
        if((marks1>40)&&(marks2>40))
        {
            cout<<name<<" With Roll Number "<<rollno<<" You Have Passed In "<<sub1<<", "<<sub2<<endl;
        }
        else
        {
            cout<<name<<" With Roll Number "<<rollno<<" Mission Failed"<<endl;
        }
    }
    void CheckPass(string sub1,int marks1)
    {
        if((marks1>40))
        {
            cout<<name<<" With Roll Number "<<rollno<<" You Have Passed In "<<sub1<<endl;
        }
        else
        {
            cout<<name<<" With Roll Number "<<rollno<<" Mission Failed"<<endl;
        }
    }
};
int main()
{
    Student students[10];
    string sub1,sub2,sub3,name,roll;
    int marks1,marks2,marks3,_count=0,index;
    int choice;
    while(choice !=5){
    cout<<"Enter 1 if you wrote  1 subject"<<endl<<"Enter 2 if you wrote  2 subject"<<endl<<"Enter 3 if you wrote  3 subject"<<endl<<"Enter 4 to search"<<endl<<"Enter 5 to Exit"<<endl;
    cin>>choice;
    switch(choice)
    {
    case 1:

    cout<<"Enter Name"<<endl;
    cin>>name;
    cout<<"Enter RollNo"<<endl;
    cin>>roll;
    students[_count]= Student(name,roll);
        cout<<"Enter Subject 1 Name"<<endl;
        cin>>sub1;
        cout<<"Enter Marks for Subject 1"<<endl;
        cin>>marks1;
        students[_count].CheckPass(sub1,marks1);
        _count++;
        break;
    case 2:

    cout<<"Enter Name"<<endl;
    cin>>name;
    cout<<"Enter RollNo"<<endl;
    cin>>roll;
    students[_count]= Student(name,roll);
        cout<<"Enter Subject 1 Name"<<endl;
        cin>>sub1;
        cout<<"Enter Marks for Subject 1"<<endl;
        cin>>marks1;
        cout<<"Enter Subject 2 Name"<<endl;
        cin>>sub2;
        cout<<"Enter Marks for Subject 2"<<endl;
        cin>>marks2;
        students[_count].CheckPass(sub1,marks1,sub2,marks2);
        _count++;
        break;
    case 3:

    cout<<"Enter Name"<<endl;
    cin>>name;
    cout<<"Enter RollNo"<<endl;
    cin>>roll;
    students[_count]= Student(name,roll);
        cout<<"Enter Subject 1 Name"<<endl;
        cin>>sub1;
        cout<<"Enter Marks for Subject 1"<<endl;
        cin>>marks1;
        cout<<"Enter Subject 2 Name"<<endl;
        cin>>sub2;
        cout<<"Enter Marks for Subject 2"<<endl;
        cin>>marks2;
        cout<<"Enter Subject 3 Name"<<endl;
        cin>>sub3;
        cout<<"Enter Marks for Subject 3"<<endl;
        cin>>marks3;
        students[_count].CheckPass(sub1,marks1,sub2,marks2,sub3,marks3);
        _count++;
        break;
    case 4:
        cout<<"Enter index to search"<<endl;
        cin>>index;
        if(index<_count)
        {
            cout<<"Name is "<<students[index].name<<"With Roll Number"<<students[index].rollno<<endl;
        }
        break;
    case 5:
        cout<<"Thank You"<<endl;
        break;
    default:
        cout<<"Invalid Input"<<endl;
        break;

    }

}
}



8.STAROne


using namespace std;

int main()
{

   for(int i=1;i<4;i++)
   {
       int k=0;
       for(int j=4;j>i;j--)
       {
           cout<<" ";
       }
       while(k!=2*i-1)
       {
           cout<<"*";
           k++;
       }
       cout<<endl;
   }
}


9.PRIME NUMBER OR NOT


using namespace std;

int main()
{
  int n, i;
  bool isPrime = true;

  cout << "Enter a positive integer: ";
  cin >> n;

  for(i = 2; i <= n / 2; ++i)
  {
      if(n % i == 0)
      {
          isPrime = false;
          break;
      }
  }
  if (isPrime)
      cout << "This is a prime number";
  else
      cout << "This is not a prime number";

  return 0;
}



10.INLINE FUNCTION


using namespace std;

class A
{
public:
    inline int add(int a, int b)
    {
        return(a+b);
    }
};
class B
{
public:
    int sub(int a, int b);
};
inline int B::sub(int a, int b)
{
    return(a-b);
}
inline int Max(int x, int y)
{
    return(x>y)?x:y; //Ternary Operator
}

int main()
{
    A a;
    B b;
    cout<<a.add(10,20)<<endl;
    cout<<b.sub(10,20)<<endl;
    cout<<Max(20,30)<<endl;
    return 0;
}



11.ACCOUNT DETAILS



using namespace std;
class Bank
{
private:
    int minbal,dob1,dob2,pin;
public:
    string aname1,aname2,bname,branch,ifsc;
    int bal1,bal2;
    Bank()
    {
        bname = "State Bank Of India";
        branch = "CMR";
        ifsc = "SBIN0000";
        minbal = 1000;
        aname1 = "LOL";
        aname2 = "NOOB";
        dob1 = 4201999;
        dob2 = 9112008;
        bal1 = 1000;
        bal2 = 3456789;
    }
    void Profile();
};
void Bank::Profile()
{
    cout<<"Enter Account PIN";
    cin>>pin;
    if(pin==0000)
    {
        cout<<bname<<endl<<branch<<endl<<ifsc<<endl<<"Min Balance:"<<minbal<<endl<<"Name:"<<aname1<<endl<<"DOB:"<<dob1<<endl<<endl<<"Balance:"<<bal1<<endl<<endl<<endl<<endl;
    }
    else if(pin==0001)
    {
        cout<<bname<<endl<<branch<<endl<<ifsc<<endl<<"Min Balance:"<<minbal<<endl<<"Name:"<<aname2<<endl<<"DOB:"<<dob2<<endl<<endl<<"Balance:"<<bal2<<endl<<endl<<endl<<endl;
    }
    else
        cout<<"Wrong Input!!";
}
int main()
{
    Bank obj1;
    Bank obj2;
    obj1.Profile();
    obj2.Profile();
    return 0;
}



12.EMPLOYEE DEPARTMENT


using namespace std;

class Employee
{
    public:
    string name,department,position;
    int age,salary;
    virtual void DisplayData()
    {
        cout<<"Please choose a department"<<endl;
    }
};
class Sanitation:public Employee
{
    public:
    Sanitation(string name_e,int age_e)
    {
        name=name_e;
        age=age_e;
        department="Game Designer";
        position="Team Designer ";
        salary=50000;
    }
    Sanitation()
    {

    }
    void DisplayData()
    {
        cout<<"Name: "<<name<<endl<<"Age: "<<age<<endl<<"Department: "<<department<<endl<<"Position: "<<position<<endl<<"Salary: "<<salary<<endl;
    }
};
class Programmer:public Employee
{
    public:
    Programmer(string name_e,int age_e)
    {
        name=name_e;
        age=age_e;
        department="Game Developer";
        position="Head Of Department";
        salary=100000;
    }
    Programmer()
    {

    }
    void DisplayData()
    {
        cout<<"Name: "<<name<<endl<<"Age: "<<age<<endl<<"Department: "<<department<<endl<<"Position: "<<position<<endl<<"Salary: "<<salary<<endl<<endl;
    }
};
class Manager:public Employee
{
    public:
    Manager(string name_e,int age_e)
    {
        name=name_e;
        age=age_e;
        department="Game Tester";
        position="Senior Tester";
        salary=22000;
    }
    Manager()
    {

    }
    void DisplayData()
    {
        cout<<"Name: "<<name<<endl<<"Age: "<<age<<endl<<"Department: "<<department<<endl<<"Position: "<<position<<endl<<"Salary: "<<salary<<endl;
    }
};
int main()
{
    string name;
    int age,i,dept,id;
    int choice;
    Sanitation janitors[10];
    Programmer programers[10];
    Manager managers[10];

    int _count=0,_count1=0,_count2=0,total=0;
    while(choice!=6)
    {
        cout<<"Enter 1 To Enter Employee into Game Designer Dept"<<endl<<"Enter 2 To Enter Employee into Game Developer Dept"<<endl<<"Enter 3 To Enter Employee into Game Tester Dept"<<endl<<"Enter 4 To Display all Employee"<<endl<<"Enter 5 To Display number of Employees"<<endl<<"Enter 6 To Search Database"<<endl<<"Enter 7 To Exit"<<endl;
        cin>>choice;
        switch(choice)
        {
        case 1:

        cout<<"Enter name and age"<<endl;
        cin>>name;
        cin>>age;
            janitors[_count]=Sanitation(name,age);
            _count++;
            break;
        case 2:

        cout<<"Enter name and age"<<endl;
        cin>>name;
        cin>>age;
            programers[_count1]=Programmer(name,age);
            _count1++;
            break;
        case 3:

        cout<<"Enter name and age"<<endl;
        cin>>name;
        cin>>age;
            managers[_count2]=Manager(name,age);
            _count2++;
            break;
        case 4:
            {
                for(i=0;i<_count;i++)
                    janitors[i].DisplayData();
                for(i=0;i<_count1;i++)
                    managers[i].DisplayData();
                for(i=0;i<_count2;i++)
                    programers[i].DisplayData();
                    break;
            }
        case 5:
            {
                total=_count+_count1+_count2;
                cout<<"Number of Employees is "<<total<<endl;
                break;
            }
        case 6:
            cout<<"Enter Dept 1 for janitorial"<<endl<<"2 for managers"<<endl<<"3 for programmers"<<endl;
            cin>>dept;
            cout<<"Enter index"<<endl;
            cin>>id;
            switch(dept)
            {
            case 1:
                if(id<=_count)
                    janitors[id].DisplayData();
                break;

            case 2:
                if(id<=_count1)
                    managers[id].DisplayData();
                break;

            case 3:
                if(id<=_count2)
                    programers[id].DisplayData();
                break;
            default:
                cout<<"Invalid Input"<<endl;
                break;
            }
        case 7:
            cout<<"Thank You"<<endl;
            break;
        default:
            cout<<"Invalid Input"<<endl;
            break;
        }
    }
}



13.CUBE WITH ARRAY


using namespace std;
class cube{
public: int n;
cube()
{
    cout<<"Enter the size ";
    cin>>n;
}
void inputs()
 {
    for(int i=1;i<=n;i++)
 {
    cout<<" "<<(i*i*i);
 }
}

};
int main()
{

   cube c;
   c.inputs();
    return 0;
}



14.14.HEADER FILE ONE


i) main.cpp

#include"ProfileInformation.h"

#include<iostream>

using namespace std;

int main()
{
    ProfileInformation(420,"Rajoo","PUBG Mobile","Single,''Ready To Mingle''");

    return 0;
}

ii) ProfileInformation.h

#ifndef PROFILEINFORMATION_H
#define PROFILEINFORMATION_H

#include <string>


using namespace std;

void ProfileInformation(int num,string name,string game,string status);

#endif


iii)ProfileInformation.cpp

#include"ProfileInformation.h"
#include<iostream>

using namespace std;

void ProfileInformation(int num,string name,string game,string status)
{
     cout<<"My Number is "<<num<<endl;
     cout<<"My Name is "<<name<<endl;
     cout<<"My Favourite Game is "<<game<<endl;
      cout<<"My Status is "<<status<<endl;
}


15.HEADER FILE TWO

i) main.cpp

#include "Array.h"
#include <iostream>

using namespace std;

int main()
{
    Array g;

    return 0;
}

ii) Array.h

#ifndef ARRAY_H
#define ARRAY_H

#include "Array.h"
class Array
{
    public:
        Array();

    public:
        int i,n,min,max,arr[10];
};

#endif // ARRAY_H


iii)Array.cpp

#include "Array.h"
#include <iostream>

using namespace std;

Array::Array()
{
        cout << "Enter the size of the array : ";

        cin >> n;

        cout << "Enter the elements of the array : ";


        for (i = 0; i < n; i++)

        cin >> arr[i];

        max = arr[0];

        for (i = 0; i < n; i++)

        {

            if (max < arr[i])

                max = arr[i];

        }

        min = arr[0];

        for (i = 0; i < n; i++)

        {

            if (min > arr[i])

                min = arr[i];

        }

        cout << "Largest element : " << max<<endl;

        cout << "Smallest element : " << min;
}



16.INHERITANCE


using namespace std;

class Person
{
     public:
        string profession;
        int age;

        Person(): profession("unemployed"), age(16) { }
        void display()
        {
             cout << "My profession is: " << profession << endl;
             cout << "My age is: " << age << endl;
             walk();
             talk();
        }
        void walk() { cout << "I can walk." << endl; }
        void talk() { cout << "I can talk." << endl; }
};

class MathsTeacher : public Person
{
    public:
       void teachMaths() { cout << "I can teach Maths." << endl; }
};

class Footballer : public Person
{
    public:
       void playFootball() { cout << "I can play Football." << endl; }
};

int main()
{
     MathsTeacher t;
     t.profession = "Teacher";
     t.age = 23;
     t.display();
     t.teachMaths();

     Footballer f;
     f.profession = "Footballer";
     f.age = 19;
     f.display();
     f.playFootball();

     return 0;
}



17.FUNCTION OVERLOADING


using namespace std;

class student
{
    public :
    int marks1,marks2,marks3;
    string subj1,subj2,subj3;
    void suppResult(string sub1,int mark1)
    {
        marks1=mark1;
        subj1=sub1;
        cout<<"Marks for "<<sub1<<" is "<<marks1<<endl;
        if(marks1>40)
        {
            cout<<"Pass"<<endl;
        }
        else
            cout<<"Fail"<<endl;
    }

    void suppResult(string sub1,int mark1,string sub2,int mark2)
    {
        marks1=mark1;
        subj1=sub1;
        marks2=mark2;
        subj2=sub2;
        cout<<"Marks for "<<sub1<<" is "<<marks1<<endl<<"Marks for "<<sub2<<" is "<<marks2<<endl;
        if(marks1>=40&&marks2>=40)
        {
            cout<<"Pass"<<endl;
        }
        else
            cout<<"Fail"<<endl;
    }
    void suppResult(string sub1,int mark1,string sub2,int mark2,string sub3,int mark3)
    {
        marks1=mark1;
        subj1=sub1;
        marks2=mark2;
        subj2=sub2;
        marks3=mark3;
        subj3=sub3;
        cout<<"Marks for "<<sub1<<" is "<<marks1<<endl<<"Marks for "<<sub2<<" is "<<marks2<<endl<<"Marks for "<<sub3<<" is "<<marks3<<endl;
        if(marks1>=40&&marks2>=40&&marks3>=40)
        {
            cout<<"Pass"<<endl;
        }
        else
            cout<<"Fail"<<endl;
    }
};

int main()
{

    student obj1;
    obj1.suppResult("Math",80);
    obj1.suppResult("English",60,"Math",75);
    obj1.suppResult("Programming",10,"Math",30,"Science",60);

    return 0;
}



18.RESULT CODE


class studentresult
{
    public:
    string sub1,sub2,sub3;
    int marks1,marks2,marks3;
    studentresult()
    {
        sub1="english";
        sub2="maths";
        sub3="c++";
        marks1=100;
        marks2=40;
        marks3=24;
    }
    void result(string s1,int m1)
    {
       if(m1>=40)
       cout<<"passed in "<<s1<< endl;
       else
       cout<<"falied in "<<s1<< endl;
    }
     void result(string s1,int m1,string s2,int m2)
    {
        if(m1>=40&&m2>=40)
       cout<<"passed in both "<<s1<<" and "<<s2<< endl;
       else if(m1<40&&m2>=40)
       cout<<"falied in "<<s1<<"and passed in"<<s2<< endl;
       else if(m2<40&&m1>=40)
       cout<<"falied in "<<s2<<"and passed in"<<s1<< endl;
       else
        cout<<"failed in both "<<s1<<" and "<<s2<< endl;
    }
      void result(string s1,int m1,string s2,int m2,string s3,int m3)
    {
       if(m1>=40&&m2>=40&&m3>=40)
       cout<<"passed in all subjects:"<<s1<<","<<s2<<","<<s3<< endl;
       else if(m1<40&&m2>=40&&m3>=40)
       cout<<"falied in "<<s1<<"and passed in"<<s2<<","<<s3<< endl;
       else if(m2<40&&m1>=40&&m3>=40)
       cout<<"falied in "<<s2<<"and passed in"<<s1<<","<<s3<< endl;
       else if(m2>=40&&m1>=40&&m3<40)
       cout<<"falied in "<<s3<<"and passed in"<<s1<<","<<s2<< endl;

        else if(m1>=40&&m2<40&&m3<40)
       cout<<"passed in "<<s1<<"and failed in"<<s2<<","<<s3<< endl;
       else if(m2>=40&&m1<40&&m3<40)
       cout<<"passed in "<<s2<<"and failed in"<<s1<<","<<s3<< endl;
       else if(m2<40&&m1<40&&m3>=40)
       cout<<"passed in "<<s3<<"and failed in"<<s1<<","<<s2<< endl;
       else
        cout<<"failed in all subjects: "<<s1<<","<<s2<<","<<s3<< endl;
    }
}obj;
 main()
{
    studentresult obj;
    cout<<"for one subject"<< endl;
    obj.result("english",100);
     cout<<"for two subject"<< endl;
    obj.result("english",100,"maths",40);
        cout<<"for three subject"<< endl;
    obj.result("english",100,"maths",40,"c++",24);

    return 0;
}



19.CLASS


#include <iostream>

using namespace std;

class fullname
{
    public :string shankar;

    void printdata()
    {
        cout<<"Shankar "<<shankar;
    }
};

int main()
{
    fullname n;
    n.shankar="Shakywar";
    n.printdata();
    return 0;
}




20.CONSTRUCTOR

#include <iostream>

using namespace std;

class construct
{

    public: int area;
            float sum;

    construct()
    {
        area=12;
    }
    construct(int a,int b)
    {
        area=a*b;
    }
    construct(int a,double b)
    {
        area=a+b;
    }
    void display()
    {
        cout<<area<<endl;
    }
    void display2()
    {
        cout<<sum<<endl;
    }
};

int main()
{
    construct c;
    construct c1(1.1,12);
    construct c2(10,33);

    c.display();
    c1.display2();
    c2.display();
    return 0;
}



21.FUNCTION OVERLOADING


class studentresult
{
    public:
    string sub1,sub2,sub3;
    int marks1,marks2,marks3;
    studentresult()
    {
        sub1="english";
        sub2="maths";
        sub3="c++";
        marks1=100;
        marks2=40;
        marks3=24;
    }
    void result(string s1,int m1)
    {
       if(m1>=40)
       cout<<"passed in "<<s1<< endl;
       else
       cout<<"falied in "<<s1<< endl;
    }
     void result(string s1,int m1,string s2,int m2)
    {
        if(m1>=40&&m2>=40)
       cout<<"passed in both "<<s1<<" and "<<s2<< endl;
       else if(m1<40&&m2>=40)
       cout<<"falied in "<<s1<<"and passed in"<<s2<< endl;
       else if(m2<40&&m1>=40)
       cout<<"falied in "<<s2<<"and passed in"<<s1<< endl;
       else
        cout<<"failed in both "<<s1<<" and "<<s2<< endl;
    }
      void result(string s1,int m1,string s2,int m2,string s3,int m3)
    {
       if(m1>=40&&m2>=40&&m3>=40)
       cout<<"passed in all subjects:"<<s1<<","<<s2<<","<<s3<< endl;
       else if(m1<40&&m2>=40&&m3>=40)
       cout<<"falied in "<<s1<<"and passed in"<<s2<<","<<s3<< endl;
       else if(m2<40&&m1>=40&&m3>=40)
       cout<<"falied in "<<s2<<"and passed in"<<s1<<","<<s3<< endl;
       else if(m2>=40&&m1>=40&&m3<40)
       cout<<"falied in "<<s3<<"and passed in"<<s1<<","<<s2<< endl;

        else if(m1>=40&&m2<40&&m3<40)
       cout<<"passed in "<<s1<<"and failed in"<<s2<<","<<s3<< endl;
       else if(m2>=40&&m1<40&&m3<40)
       cout<<"passed in "<<s2<<"and failed in"<<s1<<","<<s3<< endl;
       else if(m2<40&&m1<40&&m3>=40)
       cout<<"passed in "<<s3<<"and failed in"<<s1<<","<<s2<< endl;
       else
        cout<<"failed in all subjects: "<<s1<<","<<s2<<","<<s3<< endl;
    }
}obj;
 main()
{
    studentresult obj;
    cout<<"for one subject"<< endl;
    obj.result("english",100);
     cout<<"for two subject"<< endl;
    obj.result("english",100,"maths",40);
        cout<<"for three subject"<< endl;
    obj.result("english",100,"maths",40,"c++",24);

    return 0;
}




22.COPY CONSTRUCTOR


class Fruits
{
    public : int price, discount;
             string colour, town;

   Fruits()
    {
       cout<<"Default Constructor";
    }

    Fruits(int p1,int d1,string c1,string t1)
    {
        price=p1;
        discount=d1;
        colour=c1;
        town=t1;

        cout<<" \n Mangoes and Carrots Details are "<<"\n Price = "<<price<<"\n Discount = "<<discount<<"%"<<"\n Colour = "<<colour<<"\n Town = "<<town;
    }

    Fruits(Fruits &orange)
    {
        price=orange.price;
        colour=orange.colour;

        cout<<"\nMangoes and Oranges Details are "<<"\nPrice = "<<price<<"\nColour = "<<colour;
    }


};

int main()
{
    Fruits obj;
    Fruits mangoo(10,20,"Red","Bangalore");
    Fruits carrott(mangoo);

    return 0;
}


23.FRIEND FUNCTION


class Father;
class Son
{
private:
    int sacc,spin;
public:
    Son(int acc,int pin)
    {
        sacc=acc;
        spin=pin;
    }
    friend void Sharing(Son obj,Father obj1);
};
class Father
{
private:
    int facc,fpin;
public:
    Father(int acc,int pin)
    {
        facc=acc;
        fpin=pin;
    }
    friend void Sharing(Son obj,Father obj1);
};
void Sharing(Son obj,Father obj1)
{
    cout<<" Fathers Details\n Account: "<<obj1.facc<<" Pin: "<<obj1.fpin<<endl;
    cout<<" Sons Details\n Account: "<<obj.sacc<<"  Pin: "<<obj.spin<<endl;
}
int main()
{
    Son obj(10,20);
    Father obj1(20,30);
    Sharing(obj,obj1);
    return 0;
}



24.ALL


///////////////////////////////////////constructor overloading/////////////////////////////////

#include <iostream>

using namespace std;
class fruit{
public: int a,b;
string name;
fruit(){
name="apple";
cout<<name<<endl;
}
fruit(int price,int discount){
a=price;
b=discount;
cout<<price<<endl;
cout<<discount;

}
};

int main()
{
    fruit f;
    fruit g(10,5);
   
    return 0;
}

//////////////////////function overloading///////////////////////////////

#include <iostream>

using namespace std;
class shape{
public:int d;
    void area(int l,int b){
    d=l*b;
    cout<<"area of rectangle "<<d<<endl;
    }
    void area(float base){
    d=base*base;//its side *side just ignore

    cout<<"area of triangle "<<d<<endl;
    }
};

int main()
{
    shape s;
    s.area(10,20);
    s.area(5.5f);
    cout << "Hello world!" << endl;
    return 0;
}

/////////////////////////////destructor/////////////////////////////////

#include <iostream>

using namespace std;
class a{
public: string name;
    a(){
cout<<"its a default constructor"<<endl;
}
public: ~a(){
cout<<"its a destructor"<<endl;
}

public: a(string n){
name=n;
cout<<"name : "<<n<<endl;
}

};
int main()
{
   a f;
   a g("akash");
   // there is no need to call destructor coz its called automatically
    return 0;
}


////////////////////////////////////structure without function////////////////////////////////

#include <iostream>

using namespace std;
struct student{
public:
    int age,phone;
    string name;
};


int main()
{
    student s;
    cout<<"enter full name: ";
    cin>>s.name;
    cout<<"enter ur age: ";
    cin>>s.age;
    cout<<"enter ur phone : ";
    cin>>s.phone;
    cout<<" "<<endl;
    cout<<" "<<endl;
    cout<<"//////////////////////////////////////////////////"<<endl;
    cout<<" "<<endl;
    cout<<"displaying"<<endl;
    cout<<" "<<endl;
    cout<<" "<<endl;
    cout<<"name: "<<s.name<<endl;
    cout<<"age: "<<s.age<<endl;
    cout<<"phone: "<<s.phone<<endl;

    return 0;
}


////////////////////////////////operator overloading/////////////////////////////////////
#include <iostream>

using namespace std;
class overloading{
private: int number;
public:
    overloading(){
number = 5;
}
overloading(int m){
number = m;
}
void operator++(){
number=number+2;
}
void operator--(){
number=number-3;
}
overloading operator+(overloading o1){
overloading number2;
number2.number=number+o1.number;
return number2;
}
overloading operator-(overloading o1){
overloading number2;
number2.number=number-o1.number;
return number2;
}
overloading operator*(overloading o1){
overloading num;
num.number=number*o1.number;
return num;
}
overloading operator/(overloading o0){
overloading number2;
number2.number=number/o0.number;
return number2;
}
void displaying(){
cout<<"number is: "<<number<<endl;
}
};

int main()
{
 overloading t,o2(9),o4(4);
    ++t;
    t.displaying();
    --t;
    t.displaying();
    t=t+t;
    t.displaying();
    o4=o2/t;
    t.displaying();
    t=o2*o4;
    t.displaying();
    o4=o4+o2;
    t.displaying();
    o4=o2-o4;
    t.displaying();
    return 0;
}


////////////////////////////////////////////hierarchical inheritance///////////////////////

#include <iostream>

using namespace std;
class cal{
public:
    int x,y,z;
    void getdata(){
    cout<<"enter x value: ";
    cin>>x;
    cout<<"enter y value: ";
    cin>>y;
    }
};
class product:public cal{
public:
    void multiple(){
    z=x*y;
    cout<<"mutiple is: "<<z<<endl;
    }
};
class sum : public cal{
public:
    void add(){
    z=x+y;
    cout<<"sum is: "<<z<<endl;
    }
};

int main()
{
    product obj1;
    sum obj2;
    obj1.getdata();
    obj1.multiple();
    obj2.getdata();
    obj2.add();
    return 0;
}


////////////////////////////////////hybrid inheritance/////////////////////////////////////////

#include <iostream>
using namespace std;

class A
{
 	public:
 	int x;
};
class B : public A
{
 	public:
 	B()      //constructor to initialize x in base class A
 	{
 	   x = 10;
 	}
};
class C
 {
 	public:
 	int y;
 	C()   //constructor to initialize y
 	{
 	    y = 4;
        }
};
class D : public B, public C   //D is derived from class B and class C
{
 	public:
 	void sum()
 	{
 	    cout << "Sum= " << x + y;
 	}
};

int main()
{
         D obj1;          //object of derived class D
 	obj1.sum();
 	return 0;
}    


25.CONSTRUCTOR OVERLOADING


using namespace std;
class fruit{
public: int a,b;
string name;
fruit(){
name="apple";
cout<<name<<endl;
}
fruit(int price,int discount){
a=price;
b=discount;
cout<<price<<endl;
cout<<discount;

}
};

int main()
{
    fruit f;
    fruit g(10,5);

    return 0;
}



26.Destructor


using namespace std;
class a{
public: string name;
    a(){
cout<<"its a default constructor"<<endl;
}
public: ~a(){
cout<<"its a destructor"<<endl;
}

public: a(string n){
name=n;
cout<<"name : "<<n<<endl;
}

};
int main()
{
   a f;
   a g("akash");
   // there is no need to call destructor coz its called automatically
    return 0;
}


27.FUNCTION OVERLOADING


using namespace std;
class shape{
public:int d;
    void area(int l,int b){
    d=l*b;
    cout<<"area of rectangle "<<d<<endl;
    }
    void area(float base){
    d=base*base;//its side *side just ignore

    cout<<"area of triangle "<<d<<endl;
    }
};

int main()
{
    shape s;
    s.area(10,20);
    s.area(5.5f);
    cout << "Hello world!" << endl;
    return 0;
}



28.HIERARCHICAL


 using namespace std;
    class cal{
    public:
        int x,y,z;
        void getdata(){
        cout<<"enter x value: ";
        cin>>x;
        cout<<"enter y value: ";
        cin>>y;
        }
    };
    class product:public cal{
    public:
        void multiple(){
        z=x*y;
        cout<<"mutiple is: "<<z<<endl;
        }
    };
    class sum : public cal{
    public:
        void add(){
        z=x+y;
        cout<<"sum is: "<<z<<endl;
        }
    };

    int main()
    {
        product obj1;
        sum obj2;
        obj1.getdata();
        obj1.multiple();
        obj2.getdata();
        obj2.add();
        return 0;
    }


29.OPERATOR OVERLOADING


using namespace std;
class overloading{
private: int number;
public:
    overloading(){
number = 5;
}
overloading(int m){
number = m;
}
void operator++(){
number=number+2;
}
void operator--(){
number=number-3;
}
overloading operator+(overloading o1){
overloading number2;
number2.number=number+o1.number;
return number2;
}
overloading operator-(overloading o1){
overloading number2;
number2.number=number-o1.number;
return number2;
}
overloading operator*(overloading o1){
overloading num;
num.number=number*o1.number;
return num;
}
overloading operator/(overloading o0){
overloading number2;
number2.number=number/o0.number;
return number2;
}
void displaying(){
cout<<"number is: "<<number<<endl;
}
};

int main()
{
 overloading t,o2(9),o4(4);
    ++t;
    t.displaying();
    --t;
    t.displaying();
    t=t+t;
    t.displaying();
    o4=o2/t;
    t.displaying();
    t=o2*o4;
    t.displaying();
    o4=o4+o2;
    t.displaying();
    o4=o2-o4;
    t.displaying();
    return 0;
}



30.STRUCTURES

using namespace std;
struct student{
public:
    int age,phone;
    string name;
};


int main()
{
    student s;
    cout<<"enter full name: ";
    cin>>s.name;
    cout<<"enter ur age: ";
    cin>>s.age;
    cout<<"enter ur phone : ";
    cin>>s.phone;
    cout<<" "<<endl;
    cout<<" "<<endl;
    cout<<"//////////////////////////////////////////////////"<<endl;
    cout<<" "<<endl;
    cout<<"displaying"<<endl;
    cout<<" "<<endl;
    cout<<" "<<endl;
    cout<<"name: "<<s.name<<endl;
    cout<<"age: "<<s.age<<endl;
    cout<<"phone: "<<s.phone<<endl;

    return 0;
}


31.ALL2


Create 3 diff Classes and implement Multilevel,multiple inheritance, function overloading, overriding using pointer values for a laptop acccessory mmgt program


*************************
#include <iostream>

using namespace std;

class accessory
{
    public : string name,type,manuf;
             float price;

    void details(){
    cout<<"Enter the name of the product"<<endl;
    cin>>name;
    cout<<"Enter the type of the product "<<endl;
    cin>>type;
    cout<<"Enter the manufacturer of the product "<<endl;
    cin>>manuf;
    cout<<"enter the price of the product"<<endl;

    }
};

class discount:public accessory
{
    public :
        float finalprice;
        float calculate()
        {
            finalprice = price - (price*0.10);
            return finalprice;
        }
        void display()
        {
            cout<<"Discounted price :"<<finalprice<<endl;
        }
};


class regulatory : public discount
{
public:
    float msp;
   void display()
   {
       if(manuf!="TVS")
       {
           cout<<"Since the Manufacturer is not Indian, Customs levies a 20% charge"<<endl;

           msp = finalprice + (finalprice*0.20);

           cout<<"MSP :"<<msp<<endl;
       }
       else
       {
           cout<<"No Levy on your product"<<endl;
       }
   }
};

int main()
{
    regulatory obj;
    obj.details();
    obj.calculate();
    obj.display();

}


make a class with 4 functions, in first function  give obj as parameter, in 2nd give array as parameter, in 3rd give structure as parameter, in 4th give pointer as parameter along with constructor and distructor


#include <iostream>

using namespace std;

struct Student{
    string name;
};

class exam{
    public:
    int num;
    exam(){
        cout<<"Constructor\n";
        num = 1;
    }
    ~exam(){
        cout<<"Destructor\n";
    }

    void funObject(exam obj){
        cout<<"Object Function : "<<obj.num<<endl;
    }

    void funStructure(Student s){
        cout<<"Structure Function : "<<s.name<<endl;
    }

    void funArray(int arr[], int n){
        cout<<"Array Function : "<<endl;
        for(int i=0;i<n;i++){
            cout<<arr[i]<<" ";
        }
        cout<<endl;
    }

    void funPointer(int &p){
        cout<<"Pointer Function : "<<&p;
    }
}obj;

int main()
{
    int *p;
    int arr[5] = {1,2,3,4,5};
    Student s;
    obj.funObject(obj);
    obj.funStructure(s);
    obj.funArray(arr,5);
    obj.funPointer(*p);
    return 0;
}


hotel mgmt

#include <iostream>

using namespace std;
class hotelmgmt
{
    public:
        string hName,clname,clAddress;
        int roomno,roomprice;

        hotelmgmt()
        {
            hName="CMR";
            clname="Client";
            clAddress="Address";
            roomno=0;
            roomprice=0;
        }
        void EnterDet()
        {
            cout<<"Enter your name : ";
            cin>>clname;
            cout<<"Enter your permanent address : ";
            cin>>clAddress;
            cout<<"Enter your room number : ";
            cin>>roomno;
            roomprice=calcprice();
        }
        int calcprice()
        {   int rprice;
            if(roomno<10)
                rprice=1000;
            else
                rprice=2000;
            return rprice;
        }
        void display()
        {
            cout<<"Hotel Name : "<<hName<<endl;
            cout<<"Client Name : "<<clname<<endl;
            cout<<"Client Address : "<<clAddress<<endl;
            cout<<"Room number : "<<roomno<<endl;
            cout<<"Room price : "<<roomprice<<endl;

        }


};
int main()
{   hotelmgmt obj[1];
    int opt,i,j;
    char ch;
    bool yes;
    start:
    cout<<"1.Enter the details. " <<endl;
    cout<<"2.Display  the details. "<<endl;
    cout<<"3.Exit. "<<endl;
    cout<<"Enter your choice : ";
    cin>>opt;

            switch(opt)
            {
                case 1:
                    {
                        for(i=0;i<1;i++)
                            obj[i].EnterDet();
                        break;
                    }
                case 2:
                    {

                        for(j=0;j<1;j++)
                        {
                            obj[j].display();
                        }
                        break;
                    }
                default:
                    {
                        cout<<"Enter a valid option "<<endl ;
                        break;
                    }
            }
            cout<<"Do you wish to continue ?(Y/N)";
            cin>>ch;
            if(ch=='y'||ch=='Y')
            {   yes=true;
                    while(yes)
                        goto start;
            }
            else
                cout<<"Thank you";







}


33.HEADER3

main.cpp


#include <iostream>
#include<string.h>
using namespace std;
class Employee
{
   public:
       float esalary;
       int eid, proj;
       string ename, dept, eadd, company;
       Employee()
       {
           company = "LOL";
       }
void EmployeeInput()
{
    cout<<"\nEnter Employee Name: ";
    cin>>ename;
    cout<<"\nEnter Employee id: ";
    cin>>eid;
    cout<<"\nEnter Employee Address: ";
    cin>>eadd;
    cout<<"\nEnter Employee Salary: ";
    cin>>esalary;
    cout<<"\nEnter Department: ";
    cin>>dept;
    cout<<"\nEnter the Number of projects that you have submitted: ";
    cin>>proj;
}
void Promotion()
{
    if(proj>20)
    {
        cout<<"Congrats... you are going to be promoted"<<endl;
    }
    else if(proj>5)
    {
        cout<<"Do more "<<20-proj<<" projects to get promoted"<<endl;
    }
   else
    {
        cout<<"You are gonna get fired, complete more than 5 projects to stay in the company"<<endl;
    }
}
void Display(int noe)
{
    cout<<"Company: "<<company;
    cout<<"\nEmployee Name: "<<ename;
    cout<<"\nEmployee id: "<<eid;
    cout<<"\nEmployee Address: "<<eadd;
    cout<<"\nEmployee Salary: "<<esalary;
    cout<<"\nEmployee Department: "<<dept;
    cout<<"\nNumber of Employees: "<<noe;
    cout<<"\nNumber of Projects: "<<proj<<endl;
}
};
int main()
{
    Employee obj[100];
    int ch, i=0, noe=0;
    bool x = true;
    cout<<"Employee Management";
    while(x==true)
    {
    cout<<"\n1. Input Details";
    cout<<"\n2. Display Details";
    cout<<"\n3. Exit";
    cout<<endl;
    cin>>ch;
    switch(ch)
    {
    case 1:
        obj[i].EmployeeInput();
        noe=i+1;
        i++;
        cout<<endl;
        break;
    case 2:
        for(i=0;i<noe;i++)
        {
            obj[i].Display(noe);
            obj[i].Promotion();
            cout<<endl;
        }
        break;
    case 3:
        x=false;
        break;
    default:
        cout<<"Wrong input";
        break;
    }
    }
}


Profilefunction.h

#include <iostream>
#include<string.h>
using namespace std;
class Employee
{
   public:
       float esalary;
       int eid, proj;
       string ename, dept, eadd, company;
       Employee()
       {
           company = "LOL";
       }
void EmployeeInput()
{
    cout<<"\nEnter Employee Name: ";
    cin>>ename;
    cout<<"\nEnter Employee id: ";
    cin>>eid;
    cout<<"\nEnter Employee Address: ";
    cin>>eadd;
    cout<<"\nEnter Employee Salary: ";
    cin>>esalary;
    cout<<"\nEnter Department: ";
    cin>>dept;
    cout<<"\nEnter the Number of projects that you have submitted: ";
    cin>>proj;
}
void Promotion()
{
    if(proj>20)
    {
        cout<<"Congrats... you are going to be promoted"<<endl;
    }
    else if(proj>5)
    {
        cout<<"Do more "<<20-proj<<" projects to get promoted"<<endl;
    }
   else
    {
        cout<<"You are gonna get fired, complete more than 5 projects to stay in the company"<<endl;
    }
}
void Display(int noe)
{
    cout<<"Company: "<<company;
    cout<<"\nEmployee Name: "<<ename;
    cout<<"\nEmployee id: "<<eid;
    cout<<"\nEmployee Address: "<<eadd;
    cout<<"\nEmployee Salary: "<<esalary;
    cout<<"\nEmployee Department: "<<dept;
    cout<<"\nNumber of Employees: "<<noe;
    cout<<"\nNumber of Projects: "<<proj<<endl;
}
};
int main()
{
    Employee obj[100];
    int ch, i=0, noe=0;
    bool x = true;
    cout<<"Employee Management";
    while(x==true)
    {
    cout<<"\n1. Input Details";
    cout<<"\n2. Display Details";
    cout<<"\n3. Exit";
    cout<<endl;
    cin>>ch;
    switch(ch)
    {
    case 1:
        obj[i].EmployeeInput();
        noe=i+1;
        i++;
        cout<<endl;
        break;
    case 2:
        for(i=0;i<noe;i++)
        {
            obj[i].Display(noe);
            obj[i].Promotion();
            cout<<endl;
        }
        break;
    case 3:
        x=false;
        break;
    default:
        cout<<"Wrong input";
        break;
    }
    }
}



profilefunction.cpp


#include "profilefuction.h"
#include<iostream>

void profilefuction(int num,string name,string game,string status)
{
     cout<<"My Number is "<<num<<endl;
     cout<<"My Name is "<<name<<endl;
     cout<<"My Favourite Game is "<<game<<endl;
      cout<<"My Status is "<<status<<endl;
}

 
