#include<iostream>
#include <stdlib.h>

using namespace std;

// This function check engine condition
int goodCondition(double horsePower, double milage, double temp, string indicator){ 

   // Execute if vehicle temperature gauge reading is between 60 to 90.
   // Vehicle indicator is off
   if((temp>=60 && temp<=90) && indicator.compare("off")==0){

      // Vehicle horsepower 1.0 CC to 1.4 CC
      if(horsePower>=1.0 && horsePower<=1.4){
         // Execute if vehicle milage per liter is 12 KM/L or above
         if(milage>=12){
            return 1;
         }
         return 0;

      // Vehicle horsepower 1.5 CC to 2.5 CC
      }else if(horsePower>=1.5 && horsePower<=2.5){
      	
         // car's milage per liter is 10 KM/L or above
         if(milage>=10){
            return 1;
         }
         return 0;

      // Vehicle horsepower 2.5 CC to 5.0 CC
      }else if(horsePower>=2.5 && horsePower<=5.0){

         // car's milage per liter is 8 KM/L 
         if(milage==8){
            return 1;
         }
         return 0;
      }
   }
   return 0;
}

// This function check need Tuning condition 
int needTuning(double horsePower, double milage, double temp, string indicator){

   // Vehicle temperature gauge reading is between 60 to 90.
   // Vehicle indicator is off
   if((temp>=60 && temp<=120) && indicator.compare("off")==0){

      // Vehicle horsepower 1.0 CC to 1.4 CC
      if(horsePower>=1.0 && horsePower<=1.4){
         // car's milage per liter is less than 10 KM/L
         if(milage<10){
            return 1;
         }
         return 0;
         
      // vehicle horsepower 1.5 CC to 2.5 CC
      }else if(horsePower>=1.5 && horsePower<=2.5){

         // car's milage per liter is 6 KM/L or above
         if(milage>=6){
            return 1;
         }
         return 0;

      // Vehicle horsepower 2.5 CC to 5.0 CC
      }else if(horsePower>=2.5 && horsePower<=5.0){
      	
         // car's milage per liter is less than 4 KM/L
         if(milage<4){
            return 1;
         }
         return 0;
      }
   }
   return 0;
}

// This function check need Overhaul condition return boolean value
int needOverhaul(double temp, string indicator){
   if(temp>120 && indicator.compare("on")==0){
      return 1;
   }
   return 0;
}

// main() function
int main(){
	system("COLOR F0");
   // 1. Declare all variables
   string model, indicator;
   double horsePower, milage, temp;
   int flag = 1;

   // 2. Prompt all details
   //Prompt vehicle model
   printf ("Welcome to the UTHM engine diagnose system");
   cout<<"\n\nEnter the vehicle model: ";
   cin>>model;
   while(flag){
   	
      //Prompt vehicle horsepower
      cout<<"Enter the vehicle horsepower: ";
      cin>>horsePower;

      // check input is valid or not
      // display message if a user enters a wrong input
      if(horsePower<1.0 || horsePower>5.0){
         cout<<"Workshop does not in checking cars with horsepower more then 5.0 CC."<<endl;
      }else{
         flag = 0;
      }
   };

   //Prompt vehicle milage per liter fuel
   cout<<"Enter the vehicle milage per liter fuel: ";
   cin>>milage;
   flag = 1;
   while(flag){

      //Prompt vehicle temperature gauge reading
      cout<<"Enter the vehicle temperature gauge reading: ";
      cin>>temp;
      
      // check input is valid or not
      // display message if a user enters a wrong input
      if(temp<0.0 || temp>180){
         cout<<"Workshop does not in checking cars with temperature gauge reading less than 0 and more then 180.";
      }else{
         flag = 0;
      }
   };
   flag = 1;
   while(flag){

      //Prompt vehicle engine light indication
      cout<<"Enter the vehicle engine light indication(on/off): ";
      cin>>indicator; 
      
      // check input is valid or not
      // display message if a user enters a wrong input
      if(indicator.compare("off")!=0 && indicator.compare("on")!=0){
         cout<<"Enter wrong input"<<endl;
      }else{
         flag = 0;
      }
   };

   // 3.calling function
   // calling goodCondition() function and pass the parameters
   int c1 = goodCondition(horsePower, milage, temp, indicator);
   
   // calling needTuning() function and pass the parameters
   int c2 = needTuning(horsePower, milage, temp, indicator);

   // calling needOverhaul() function and pass the parameters
   int c3 = needOverhaul(temp, indicator);

   // 4. Display the condition for vehicle according to above details.
   cout<<"\n";

   if(c1)
      cout<<"Engine is in Good condition."<<endl;
   else
      cout<<"Engine is in Bad condition."<<endl;
   if(c2)
      cout<<"Engine needs tuning."<<endl;
   else
      cout<<"Engine doesn't need tuning."<<endl;
   if(c3)
      cout<<"Engine needs overhaul."<<endl;
   else
      cout<<"Engine doesn't need to overhaul."<<endl;
   return 0;
}
