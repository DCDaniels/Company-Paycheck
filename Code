#include <iostream>
#include <iomanip>
#include <string>
#include <fstream>
using namespace std;

float compute_gross_pay(int a, float b, char c); //function prototypes
float compute_taxes(float f);
float compute_net_pay(float totalTax, float grossPay);
void print_pay_check(string fname, string lname, string city, int zip, string date, string streetname, string state, string streettype, int address, float grosspay, float netpay, float totaltax);
float compute_federal_tax(float b);
float compute_state_tax(float b);
float compute_city_tax(float b);

int main() {
    string dummy; //declare variables
    char parttime_fulltime;
    float payRate;
    float grossPay;
    float netPay;
    float totalTax;
    const string date = "02/16/2016";
    string last_name, first_name, street_address, street_name, street_type, city, state;
    int zip, deductions, employee_id, address_num;
    
    
    
    ifstream myfile;
    myfile.open("infile.txt"); // open infile;
    for(int r=0;r<5;r++)
    {
      myfile >> last_name >> first_name >> deductions >> employee_id >> address_num >> street_name >> street_type >> city >> state >> zip >>payRate >> parttime_fulltime; // get employee information
      grossPay=compute_gross_pay(deductions, payRate, parttime_fulltime);
      totalTax = compute_taxes(grossPay);
      netPay = compute_net_pay(totalTax, grossPay);
      print_pay_check(first_name, last_name, city, zip, date, street_name, state, street_type, address_num, grossPay, netPay, totalTax);

    }
    
    return 0;
}

float compute_gross_pay(int a, float b, char c) 
{
  float grossPay;
  if (c == 'F')
  {
    grossPay=40 * b;
  }
  else
  {
    grossPay = 40 * b + (float (a) * 10.5);
  }
  
  return grossPay;

}

float compute_taxes(float f)
{
  float fedTax,stateTax,cityTax,totalTax;
  fedTax=compute_federal_tax(f);
  stateTax=compute_state_tax(fedTax);
  cityTax=compute_city_tax(stateTax);
  totalTax=fedTax+stateTax+cityTax;
  return totalTax;

}

float compute_net_pay(float totalTax, float grossPay) {
    return grossPay - totalTax;
}

void print_pay_check(string fname, string lname, string city, int zip, string date, string streetname, string state, string streettype, int address, float grosspay, float netpay, float totaltax) {
    cout << "****************************************************\n";
     cout << fname << " " << lname << endl;
    cout << address << " " << streetname << " " << streettype << setw(25 ) << date <<endl;
    cout << city << " "<< state<<" "<<zip<< endl<<endl;
    cout << "Pay this amount: "<< fixed << setprecision(2) << netpay << endl;
   
    cout << "Gross Pay $" << fixed << setprecision(2) << grosspay << endl;

}

float compute_federal_tax(float b) {
  float federal_tax;
  if (b > 500)
  {
    federal_tax= (200*0.15)+(300*0.25)+((b-500)*0.35);
  }
  else if ( b > 200)
  {
    federal_tax=(200*0.15)+((b-300)*0.25);
  }
  else 
  {
    federal_tax=b*0.15;
  }
  return federal_tax;
}

float compute_state_tax(float b) {
    if (b < 80) {
   	 return 0;
    }
    else {
   	 return b * .1;
    }
}

float compute_city_tax(float b) {
    if (b <= 50) {
   	 return 0;
    }
    else {
   	 return b * .08;
    }
    
}
