# friend-function-airline-problem-.cpp
// Online C++ compiler to run C++ program online
#include <iostream>
#include <string>
using namespace std;
class Flight{
public:
    int flightnum;
    string destination;
    int distance;
    int fuelconsumtion;
    void takeinfo(){
    cout<<"enter the flight number: "<<endl;
    cin>>flightnum;
    cout<<"Enter the Destination: "<<endl;
    cin>>destination;
    cout<<"Enter the distance: "<<endl;
    cin>>distance;
    cout<<"enter fuelconsumtion per KM: "<<endl;
    cin>>fuelconsumtion;
    }
    /*double calculate(){
    return distance*fuelconsumtion;  //friend function use na korle eita
    }*/
    void getinfo(){
    cout<<"Flight Number: "<<flightnum<<endl;
    cout<<"Destination: "<<destination<<endl;
    cout<<"Distance: "<<distance<<endl;
    cout<<"Fuelcomsumtion: "<<fuelinfo(*this)<<"litters"<<endl; //notice this
    }
    string takedestination(){
    return destination;
    }
    friend double fuelinfo(Flight f); //this

};
double fuelinfo(Flight f){
return f.distance*f.fuelconsumtion ; //this line for friend function
}
int main(){
int n;
cout<<"enter the total flight num: "<<endl;
cin>>n;
Flight f[n];
for(int i=0;i<n;i++){
    cout<<i+1<<endl;
    f[i].takeinfo();
}
cout<<"-------------------"<<endl;
string dest;
cout<<"enter your DDestination: "<<endl;
cin>>dest;

bool found=false;
cout<<"-------------------"<<endl;
for(int i=0;i<n;i++){
    if(f[i].takedestination()==dest){
        f[i].getinfo();
        found=true;
    }
}
if(!found){
    cout<<"Information Not Found in this Destination!!!"<<endl;
}
return 0;
}
