#include<iostream>
#include<fstream>
using namespace std;
	char fname[10],lname[10];   int acc_no,acc_no1;
	float balance,amount;  
class account{

	public:
		void new_account() ;   
		void deposite() ;
		void withdrawl (); 
		void balance_enquiry();
		void search_acc ();
		void delete_acc ();
		void update_acc ();
		void display();
};
void account :: new_account(){
	cout<<"Enter first name=";   cin>>fname;
	cout<<"Enter last name=";  cin>>lname;
	cout<<"Enter account no.=";   cin>>acc_no;
    cout<<"First name="<<fname<<endl;
	cout<<"Last name="<<lname<<endl;
	cout<<"Your account no.="<<acc_no<<endl;
}
void account::deposite(){
	cout<<"Enter account no.=";   cin>>acc_no;
	cout<<"Enter amount to deposite=";  cin>>amount;
	balance+=amount;
	cout<<"balance="<<balance;
	cout<<endl<<"\t\t Amount deposited successfully \t\t"<<endl;  
}
void account::withdrawl(){
	cout<<"Enter account no.=";   cin>>acc_no;
	cout<<"Enter amount to withdrawl=";   cin>>amount;
	if(amount<=balance){
    balance-=amount;
	cout<<"left balance="<<balance<<endl;
    cout<<"\t\t Amount withdrawl successfully \t\t"<<endl;}
    else{  cout<<"Insufficient amount"<<endl;
	}
	}
void account::balance_enquiry() {
	cout<<"Enter account no.=";   cin>>acc_no;
	cout<<endl<<"Balance left "<<balance<<endl;   
}
void account::delete_acc(){
		cout<<"\n Enter account no. to be deleted=";   cin>>acc_no;
        cout<<endl<<"\t\t Account deleted successfully \t\t"<<endl;
}
void account::update_acc(){
	    	cout<<"Enter account no.=";   cin>>acc_no;
            cout<<"Enter name to update=";  cin>>fname>>lname;
            cout<<"Updated name="<<fname<<ends<<lname<<endl;
            cout<<"\t\tAccount updated successfully\t\t"<<endl; 
		}
void account::search_acc(){
	
	cout<<"Enter account no.=";   cin>>acc_no1;
	if(acc_no1 == acc_no){
	cout<<"Name="<<fname<<ends<<lname<<endl;
	
	cout<<"Your account no.="<<acc_no1<<endl; }
	else{  cout<<"Account not found"<<endl;
	}   } 

void account::display(){
	cout<<"Name="<<fname<<ends<<lname<<endl;
	cout<<"Your account no.="<<acc_no<<endl;
	cout<<"Balance"<<balance<<endl;
}  
int  main(){
	
	account a;  char ch;  int num; 
	int key;
	do{  
	cout<<"\tMain menu\t";
		cout<<"\n1.New account \n2.Deposite amount \n3.Withdrawl amount  \n4.Balance enquiry ";
		cout<<"\n5.Search account  \n6.Update account  \n7.Delete account  ";
		cout<<"\n 8.Exit\n";
		cout<<"Select your option (1-8)"<<ends;
		cin>>key;
	if(key==1){

				 a.new_account();
				 ofstream root;
				 root.open("fri.doc",ios::out);
			 root.write((char*)&a, sizeof(a)) ;
				 if(!root){
				 	cout<<"error"<<endl;
				 }
				 else{  cout<<"successfully"<<endl;
				 root.close();  }
			}
		else if(key==2){
					int acc;	cout<<"Enter account no.=";     cin>>acc;
 				ifstream k;
				 k.open("fri.doc");
 				while(k.read((char*)&a,sizeof(a)))	   {
			   if (acc==acc_no){
			      	
			   ofstream f("fri1.doc",ios::app);
			  cout << "Name of account holder is: " << fname << " " <<lname << endl;
					cout << "Current amount is: " << balance << endl;
					cout << "Please enter new amount: "; cin >> amount;
				balance += amount;
					cout << "Name of account holder is: " <<fname<< " " <<lname << endl;
					cout << "Current amount is: " <<balance << endl;
					f.write((char*)&a, sizeof(a));
					ifstream u("E:\\Bank Management\\Reg_users.dat");
			   f.write((char*)&a,sizeof(a)) ;
			   ifstream k("fri.doc");
			   while(k.read((char*)&a,sizeof(a)))  {
			   	if (acc!=acc_no){
			   		f.write((char*)&a,sizeof(a));
				   }
			   }  f.close();	  
			    }
			    else{    	cout<<"Data not found\n";		}
			}		
				
					}
		else if(key==3){
		
				a.withdrawl();
			}
			else if(key==4){
				a.balance_enquiry();
			}
			else if(key==5){
		        a.search_acc();
		      }
		  else if(key==6){
		       a.update_acc(); 
		        }
		  else if(key==7){
		        a.delete_acc();
		       }
		   else if(key==8){
		    	cout<<"\n\n Thank for visiting the bank:";
		    	exit(0);   }
		  else{
		  
		    	cout<<"\a";  }
		}
			
			while(key!=8);
		

/*	a.new_account();  a.deposite();     a.withdrawl();   a.balance_enquiry();
	    a.update_acc();   a.delete_acc(); */
	   return 0;
}
