#include<iostream>
#include<fstream>
#include<string>

using namespace std;

  //structures of needed data

struct date 
{
	int startdate;
	int enddate;
};
struct event
{
	int ID;
	string name;
	date eventstime;
	int seats[100];
};
struct halls
{
	string name;
	string place;
	int numberofseats;
	event listofevents;
};
     //adding hall function

void addnewhall(void)   
{
	halls hall; //declaring a variable of type halls mentioned above
	system("cls");
	cout << "Please enter the following details : " << endl;
	cout << "Hall's name : ";
	cin >> hall.name;
	string NewHall = hall.name + ".txt"; 
	ifstream hall_exist;
	hall_exist.open(NewHall.c_str());

	if (hall_exist.fail())        //check if the hall's name doesn't exist,if true new hall's file will be created. 
	{
		ofstream newhalldetails;
		newhalldetails.open(NewHall.c_str());
		newhalldetails << hall.name << endl;
		cout << "Place : ";                    //entering data of the added hall
		cin >> hall.place;
		newhalldetails << hall.place << endl;
		cout << "Number of seats ( maxiumum 100 ) : ";
		cin >> hall.numberofseats;
		newhalldetails << hall.numberofseats << endl;
		newhalldetails.close();
		cout << "Hall added successfully.";
	} 
	else  //if the previous condition was false so the name already exists
	{
		cout << "This name already exists." << endl << "Press 1 to retry." << endl;
		hall_exist.close();
		int retry;   
		cin >> retry;
		if (retry == 1)
		{
			addnewhall();
		}
	}
}

 //removing hall function 

void deletehall()
{
	halls hall;
	system("cls");
	cout << "Enter hall's name : ";
	cin >> hall.name;
	string halltoberemoved = hall.name + ".txt";
	ifstream hall_exist;
	hall_exist.open(halltoberemoved.c_str());
	if (hall_exist.fail())  
	{
		cout << "This hall doesn't exist." << endl << "Please press 2 to retry.";
		int retry;
		cin >> retry;
		if (retry == 2)
		{
			deletehall();
		}
	}
	else
	{
		hall_exist.close();
		remove(halltoberemoved.c_str());
		cout << "Hall removed successfully." << endl ;
	}
}
int main()
{
	char press; //to choose add or delete (a or r)
	int cases;  //to choose halls or events managment
	cout << "1-Halls' management." << endl << "2-Events' managment." << endl;
	cin >> cases;
	if (cases == 1)
	{
		system("cls");
		cout << "Do you want to add or remove halls? " << endl;
		cin >> press;
		system("cls");
		switch (press)
		{
		case 'a':
			addnewhall();
			break;
		case 'r':
			deletehall();
			break;

		}

	}

	system("pause");
	return 0;
}
