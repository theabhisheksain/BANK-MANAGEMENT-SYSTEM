# BANK-MANAGEMENT-SYSTEM
THIS IS A FULLY C++ ORIENTED MINOR PROJECT,THAT TRY THE MAJOR PROPERTIES OF C++ LANGUAGE
THIS INCLUDE:
              1. C++ fundamentals
              2. OOP concepts
              3. Dynamic memory allocation
              4. Pointer arithmetic
              5. Menu-driven design
              6. Input validation

FROM USER THIS SYSTEM INPUTS A n NUMBER OF ENTRIES AND NUMBER OF OPERATIONS WHICH A REAL WORLD BANKING SYSTEM IS ALLOWS.
IT HAVE A NESTED OPERATION TO GRANT A IDEAL BANKING.


                ~~~~~~~~~~~CODE~~~~~~~~~~~~
<c++>
    #include<iostream>
    #include<iomanip>
    #include<string>
    #include<cctype>

    using namespace std;

    class demo{
        int n=1;
        public:
            struct info{    
                int age;
                string name="", phone_No="", address="", email="";
                float total_Amount=0, withdrawl_Amount=0, deposit=0;

            };
            info *obj = nullptr;

            void numberOfCoustumer(){

            cout<<"ENTER THE NUMBER OF COUSTUMER TO BE ENTERING:"<<endl;
            cin>>n;
            cin.ignore();

                 delete[] obj;
                 obj = nullptr;    
                 obj = new info[n];
            }
            void getData(){
                for(int i=0; i<n; i++){
                cout<<left<<setfill('-')<<setw(37)<<"ENTER DETAIL FOR"<<(i+1)<<endl;
                    cout<<setfill(' ')<<""<<endl;
                cout<<setw(25)<<"\nENTER NAME :"<<endl;
                getline(cin,(obj+i)->name);

                cout<<setw(25)<<"\nENTER contact :"<<endl;
                getline(cin,(obj+i)->phone_No);

                cout<<setw(25)<<"\nENTER AGE :"<<endl;
                cin>>(obj+i)->age;
                cin.ignore();

                cout<<setw(25)<<"\nENTER ADDRESS :"<<endl;
                getline(cin,(obj+i)->address);

                cout<<setw(25)<<"\nENTER E-MAIL :"<<endl;
                getline(cin,(obj+i)->email);

                cout<<setw(25)<<"\nENTER  INITIAL BALANCE:"<<endl;
                cin>>(obj+i)->total_Amount;
                cin.ignore();

                }

            }
            void tranx(){
                int choice=0;
                for(int i=0; i<n; i++){
                
                do{

                cout<<right<<setfill('=')<<setw(25)<<"";
                cout<<left<<setfill('=')<<setw(37)<<"TRANSACTIONS";
                cout<<"\n1.DEPOSITE \n2.WITHDRAWL \n3.SHOW BALANCE \n4.EXIT"<<endl;
                cin>>choice;

                    switch(choice){
                    case 1:
                        cout<<"\nENTER AMOUNT IN ₹:"<<endl;
                        cin>>(obj+i)->deposit;
                        cin.ignore();

                        if((obj+i)->deposit>0){
                        (obj+i)->total_Amount+=(obj+i)->deposit;
                        cout<<"SUCCESSFULLY DEPOSITED"<<endl;
                        cout<<"AMOUNT: ₹"<<(obj+i)->deposit<<endl;
                    }else{
                        cout<<"ENTER POSITIVE AMOUNT"<<endl;
                    }
                        break;
                    case 2:
                        cout<<"\nENTER WITHDRAWAL AMOUNT IN ₹:"<<endl;
                        cin>>(obj+i)->withdrawl_Amount;
                        cin.ignore();

                        if((obj+i)->withdrawl_Amount<0){
                            cout<<"ENTER POSITIVE AMOUNT"<<endl;
                        }
                        else if((obj+i)->total_Amount>=(obj+i)->withdrawl_Amount){

                                (obj+i)->total_Amount-=(obj+i)->withdrawl_Amount;
                                cout<<"AMOUNT WITHDRAWLED"<<endl;
                                cout<<"NEW BALANCE: ₹ "<<fixed<<setprecision(2)<<(obj+i)->total_Amount<<endl;

                        }else{
                        cout<<"OOPS! INSUFFICIENT BALANCE!"<<endl;
                        cout<<"AVAILABLE BALANCE: ₹ "<<fixed<<setprecision(2)<<(obj+i)->total_Amount<<endl;
                        }
                        break;
                    case 3:
                        cout<<left<<setfill('=')<<setw(50)<<"YOUR BALANCE :₹"<<endl;
                        cout<<"YOUR BALANCE:"<<fixed<<setprecision(2)<<(obj+i)->total_Amount<<endl;
                        break;
                    case 4:
                        cout<<"NEXT !"<<endl;
                        break;
                    default:
                        cout<<"CHOOSE 1-4"<<endl;
                    }
                }while(choice!=4);
            }
        }

        void showData(){
            if(obj==nullptr){
            cout<<"NO CUSTOMER REGISTERED! ADD FIRST"<<endl;
            return;
            }
            cout<<right<<setfill('=')<<setw(25)<<"";
            cout<<left<<setfill('=')<<setw(37)<<"DETAILS";

            for(int i=0; i<n; i++){
                cout<<setfill('~')<<setw(25)<<"NAME: "<<(obj+i)->name<<endl;
                cout<<setw(25)<<"CONTACT:"<<(obj+i)->phone_No<<endl;
                cout<<setw(25)<<"ADDRESS:"<<(obj+i)->address<<endl;
                cout<<setw(25)<<"AGE:"<<(obj+i)->age<<endl;
                cout<<setw(25)<<"E-MAIL:"<<(obj+i)->email<<endl;
                char xyz;
                cout<<setw(25)<<"DO YOU WANT TO CHECK BALANCE\n1.Y  \n2.N"<<endl;
                cin>>xyz;
                cin.ignore();

                switch(tolower(xyz)){
                    case 'y':
                        cout<<setfill('=')<<setw(25)<<"YOUR BALANCE:₹"<<fixed<<setprecision(2)<<(obj+i)->total_Amount<<endl;
                        break;
                    case 'n':
                        cout<<setfill('=')<<setw(25)<<"THANK  YOU:"<<endl;
                        break;
                    default:    
                        cout<<"INVALID CHOICE  (ONLY Y/N)"<<endl;
                }

            }
        }
        ~demo(){
            delete [] obj;
        }
    };
    int main(){
        int choice;
        demo d;

        do{

        cout<<"\n"<<right<<setfill('₹')<<setw(25)<<"";
        cout<<left<<setfill('₹')<<setw(40)<<"BANK OF JAIPUR"<<endl;
        cout<<setw(10)<<"\n1.TRANSACTION ? \n2.BALANCE \n3.EXIT"<<"|"<<endl;
        cin>>choice;
        
        switch(choice){
            case 1:
                    d.numberOfCoustumer();
                    d.getData();
                    d.tranx();
                    break;
            case 2:
                    d.showData();
                    break;
            case 3: 
                    cout<<"~~EXIT~~"<<endl;
                    break;
            default:
                cout<<"INVALID CHOICE:"<<endl;
        }
    }while(choice !=3);
    return 0;
    }
              
