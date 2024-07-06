#include<iostream>
using namespace std;
#include<string.h>


class Bank{
    //private variable used inside the class
    private:
    string name;
    long long acc_number;
    char type[10];
    long long Amount=0;
    long long total=0;

      //public variables

      public:
      //making a function to set person's data
      void setvalue()
      {
        cout<<"Enter Name\n";
        cin.ignore();

        //To use space in string
        getline(cin,name);

        cout<<"Enter Account number\n";
        cin>>acc_number;
        cout<<"Enter Account type\n";
        cin>>type;
        cout<<"Enter Balance\n";
        cin>>total;

    }
    //Function to display the required data.
    void showdata()
    {
        cout<<"Name:"<<name<<endl;
        cout<<"Account_Num:"<<acc_number<<endl;
        cout<<"Account Type:"<<type<<endl;
        cout<<"Account Balance:"<<total<<endl;
    }

    //Function to deposit the amount in ATM
    void deposit()
    {
        cout<<"\nEnter amount to be Deposited\n";
        cin>>Amount;
    }

    //Function to show the balance Amount
    void showbal(){
        total=total+Amount;
        cout<<"\n Total Balance is "<<total;

    }

    //Function to whithdraw amount from Atm
    void Withdraw(){
        int a,Available_Balance;
        cout<<"Enter the Amount To WithDraw\n";
        cin>>a;
        Available_Balance=total-a;
        cout<<"Available Balance is"<<Available_Balance;


    }
};



int main(){
    //Object of class

    Bank b;
    int choice;
    //infinite while loop to choose
    //options everytime
    while(1){
        cout<<"\n~~~~~~~~~~~~~~~~~~~~~~~~~~~~~"
            <<"~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~"
            <<"~~~~~~~~~~WELCOME~~~~~~~~~~~~~~"
            <<"~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~"
            <<"~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~"
            <<"~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~"
            <<"~~~~~~~~~~~~~~~~~~\n\n";

        cout<< "Enter Your Choice\n";
        cout<< "\t1. Enter Name, Account"
            << "Number , Account-Type\n";
        cout<< "\t2. Balance Enquiry\n";
        cout<< "\t3. Deposit Money\n";
        cout<< "\t4. Show Total Balance\n";
        cout<< "\t5. WithDraw Money\n";
        cout<< "\t6. Cancel\n";
        cin>>choice;

        //choices to select from----------
        switch (choice){

        case 1:
            b.setvalue();
            break;
        case 2:
            b.showdata();
            break;
        case 3:
            b.deposit();
            break;
        case 4:
            b.showbal();
            break;
        case 5:
            b.Withdraw();
            break;
        case 6:
            exit(1);
            break;

        default:
           cout<<  "\nInvalid Choice\n";
        }
    }
}
