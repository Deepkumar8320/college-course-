#include <iostream>
#include <string>
using namespace std;
class CollegeCourse {
   protected:
       string department;
       int courseNum;
       int creditHours;
       double tuition;
   public :
       CollegeCourse(string, int, int, double);
       void showCollegeCourse();
};
CollegeCourse::CollegeCourse( string dept, int num, int hours, double tuit){
   department = dept;
   courseNum = num;
   creditHours = hours;
   tuition = tuit;
}
void CollegeCourse::showCollegeCourse(){
   cout << department << courseNum << " " << creditHours <<" credits. Tuition $" << tuition << endl;
}
class LabCourse:public CollegeCourse{ // public inheritance //2
   private:
       double labFee;
   public:
       LabCourse(string, int, int, double);
   void showLabCourse();
};
LabCourse::LabCourse( string dept, int num, int hours, double tuit):CollegeCourse(dept,num,hours,tuit){
   labFee = 30.25;
}
void LabCourse::showLabCourse(){
   double totalTuition;
   showCollegeCourse();
   cout<< "plus lab fee $" << labFee;
   totalTuition = tuition+labFee;
   cout << " for a grand total of $" << totalTuition << endl;
}
int main(){
   CollegeCourse cc("ENG", 121, 3, 333.33);
   LabCourse lc("CIS", 250, 4, 444.44);
   cc.showCollegeCourse();
   lc.showLabCourse();
   return 0;
}
