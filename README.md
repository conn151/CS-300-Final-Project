# CS-300-Final-Project
//Name: Connor Corson


#include <iostream>
#include<string>
#include <algorithm>
#include <fstream>
#include <vector>
#include <sstream>


using namespace std;

const unsigned int DEFAULT_SIZE = 179;
struct course{

 string courseID;
 string courseName;
 vector <string> prereqs;


};


void printSampleSchedule(vector<course> & courseList) {
	for (int i=0; i < courseList.size(); i++) {
    	cout << courseList[i].courseID;
    	cout << ",";
      	cout << courseList[i].courseName;
      	cout << "\n";
      	//for (int p=0; p < courseList[i].prereqs.size(); p++){
          	//cout << courseList[i].prereqs[p]; }
        }
    }


void printCourseInformation(vector<course> & courseList, string courseID) {



  for (int i=0; i < courseList.size(); i++) {
		if (courseList[i].courseID == courseID) {
			cout <<courseList[i].courseID;
          	cout << ",";
			cout <<courseList[i].courseName;
          	cout << "\n";
			cout<< "Prerequisites: ";

			for (int p=0; p < courseList[i].prereqs.size(); p++){

         cout<<" - " << courseList[i].prereqs[p];

        }

			return;

		}







	}

}
int main()
{
vector<course> courseList;
	ifstream inFile;

	cout << "Welcome to the course Planner";
	while (true) {
		int option;
		string option2;
		string option3;
		option = 0;










		cout << "	 1.Load Data Structure.";
		cout << "	 2.Print Course List.";
		cout << "	 3.Print Course.";
		cout << "	 9.Exit.";
		cout << "What would you like to do ?";
		cin >> option;
		cout << endl;
		if (option == 9) {
			break;
		}
		else if (option == 1) {

			cout << "Enter the name of the file in question:"; 	//define load data structure code here
			cin >> option3;
			cout << endl;

			inFile.open(option3);
			if (!inFile) {
				cout << "This is not an option. Please try again";

			}



		      else {
		        course inCourse;
		        string line;
		        string linePre;
		        while (getline(inFile,line)) {

		          course inCourse;
		          stringstream ss(line);
		          getline(ss,inCourse.courseID,',');

		          getline(ss,inCourse.courseName,',');



		          while (getline(ss,linePre,',')) {

		            inCourse.prereqs.push_back(linePre);
		          }
		          courseList.push_back(inCourse);
		        }

		      }



		    }




		    else if (option == 2) {


		      printSampleSchedule(courseList);


		    }
			else if (option == 3) {
			cout << "What course do you want to know about?";
			cin >> option2;
			cout << endl;

			printCourseInformation(courseList, option2);


}
	else {

				cout << " is not a valid option";

		}

}


	return 0;
}


