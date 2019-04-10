
#include <iostream>
#include <string>
using namespace std ; 
struct date
{
	string day; 
	string month;
	string  year;
};

struct eventdate
{
	string eventname;
	string id; 
	string place; 
	string starttine; 
	string enddate;
}events[100];
 struct userdate
{
	string username; 
	string password; 
	string eventid [100];
} user[100];
 struct currentuser {
	 string currentname;
	 string reservedid[100];
 }userx;
void cancelreservation()           
{ 
	int count1 = 0, count2 = 0;               // the actual elements of array
	for (int i = 0; i < 100; i++)     // identifay the eventid  of user
	{
		
		if (userx.reservedid[i].empty());
		{
			break;
		}
		{
			count1++; 
		}
	}
	for (int j = 0; j < 100; j++)       // identifay  the eventid of events 
	{
		if (events[j].id.empty());
		{
			break;
		}
		{
			count2++;
		}
	}
	for (int i = 0; i < count1; i++)
	{
		for (int j= 0; j < count2; j++)
		{
			if (userx.reservedid[i] == events[j].id)
			{
				cout << events[j].eventname << endl;
				break;
			}
		}
	}
}
int main()
{
	
	cancelreservation();
	system("pause");
	return 0;
}
