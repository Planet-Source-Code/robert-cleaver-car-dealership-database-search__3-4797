<div align="center">

## Car Dealership Database Search


</div>

### Description

This loads a database of cars from a file into an array and searches through them for Make Model Year Price Mileage and Lot... i hope you like it, it is a really cool program.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Robert Cleaver](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/robert-cleaver.md)
**Level**          |Advanced
**User Rating**    |5.0 (15 globes from 3 users)
**Compatibility**  |C\+\+ \(general\), Borland C\+\+
**Category**       |[Complete Applications](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/complete-applications__3-7.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/robert-cleaver-car-dealership-database-search__3-4797/archive/master.zip)





### Source Code

```
/*
  Name: Robert Cleaver
  Date: 9-7-02
  Prog: CARPRICE.CPP
  Desc: Loads a database file and searches through it.
*/
#include<iostream.h>
#include<iomanip.h>
#include<fstream.h>
#include<conio.h>
#include<lvp/string.h>
#include<ctype.h>
typedef String stype[8];
void StartProg();
char GetSearch();
void LoadDatabase(stype &Make, stype &Model, stype &Year, stype &Price, stype &Mileage, stype &Lot, int &Counter);
void StartSearch(stype &Make, stype &Model, stype &Year, stype &Price, stype &Mileage, stype &Lot, int &Counter, char SearchItem);
void SearchMake(stype &Make, stype &Model, stype &Year, stype &Price, stype &Mileage, stype &Lot, int &Counter);
void SearchModel(stype &Make, stype &Model, stype &Year, stype &Price, stype &Mileage, stype &Lot, int &Counter);
void SearchYear(stype &Make, stype &Model, stype &Year, stype &Price, stype &Mileage, stype &Lot, int &Counter);
void SearchPrice(stype &Make, stype &Model, stype &Year, stype &Price, stype &Mileage, stype &Lot, int &Counter);
int main()
{
	StartProg();
	return(0);
}
void StartProg()
{
	stype Make, Model, Price, Mileage, Lot, Year;
	int Counter;
	char SearchItem;
	clrscr();
	SearchItem = GetSearch();
	Counter = 0;
	LoadDatabase(Make, Model, Year, Price, Mileage, Lot, Counter);
	StartSearch(Make, Model, Year, Price, Mileage, Lot, Counter, SearchItem);
}
void LoadDatabase(stype &Make, stype &Model, stype &Year, stype &Price, stype &Mileage, stype &Lot, int &Counter)
{
	ifstream in_file;
	in_file.open("U:\cars.rdb");
	while (! in_file.eof()) {
		Counter++;
		getline(in_file, Make[Counter]);
		getline(in_file, Model[Counter]);
		getline(in_file, Year[Counter]);
		getline(in_file, Price[Counter]);
		getline(in_file, Mileage[Counter]);
		getline(in_file, Lot[Counter]);
	}
}
char GetSearch()
{
	char MenuItem;
	cout<<"--- Search Menu ---"<<endl;
	cout<<" A. Make"<<endl;
	cout<<" B. Model"<<endl;
	cout<<" C. Year"<<endl;
	cout<<" D. Price"<<endl;
	cout<<" X. Exit"<<endl;
	cout<<"-------------------"<<endl;
	cout<<"Search(A,B,C,D,X): ";
	cin>>MenuItem;
	MenuItem=toupper(MenuItem);
	return(MenuItem);
}
void StartSearch(stype &Make, stype &Model, stype &Year, stype &Price, stype &Mileage, stype &Lot, int & Counter, char SearchItem)
{
	char SelItem;
	switch (SearchItem) {
	case 'A':
		SearchMake(Make, Model, Year, Price, Mileage, Lot, Counter);
		break;
	case 'B':
		SearchModel(Make, Model, Year, Price, Mileage, Lot, Counter);
		break;
	case 'C':
		SearchYear(Make, Model, Year, Price, Mileage, Lot, Counter);
		break;
	case 'D':
		SearchPrice(Make, Model, Year, Price, Mileage, Lot, Counter);
		break;
	case 'X':
		break;
	default:
		clrscr();
		SelItem = GetSearch();
		SelItem = toupper(SelItem);
		StartSearch(Make, Model, Year, Price, Mileage, Lot, Counter, SelItem);
		break;
	}
}
void SearchMake(stype &Make, stype &Model, stype &Year, stype &Price, stype &Mileage, stype &Lot, int &Counter)
{
	int SearchLoop, Matches;
	String MakeMatch;
	SearchLoop = 0;
	Matches = 0;
	clrscr();
	cout<<"Make: ";
	cin>>MakeMatch;
	clrscr();
	for (SearchLoop = 0; SearchLoop <= Counter; SearchLoop++)
	{
		if (Make[SearchLoop] == MakeMatch)
		{
			cout<<"Make: "<<Make[SearchLoop]<<endl;
			cout<<"Model: "<<Model[SearchLoop]<<endl;
			cout<<"Year: "<<Year[SearchLoop]<<endl;
			cout<<"Price: "<<Price[SearchLoop]<<endl;
			cout<<"Mileage: "<<Mileage[SearchLoop]<<endl;
			cout<<"Lot: "<<Lot[SearchLoop]<<endl;
			cout<<"\n################\n"<<endl;
			Matches = Matches + 1;
		} else if (Matches == 0 && SearchLoop == Counter) {
			cout<<"No matches found in database\n"
			  <<"containing "<<Counter<<" Cars.\n\n"
			  <<"Hit any key to return to the \"Search\" menu.";
			getch();
			clrscr();
			StartProg();
		}
		if (Matches != 0 && SearchLoop == Counter)
		{
			cout<<"\n\nHit any key to return to the \"Search\" menu.";
			getch();
			clrscr();
			StartProg();
		}
	}
}
void SearchModel(stype &Make, stype &Model, stype &Year, stype &Price, stype &Mileage, stype &Lot, int &Counter)
{
	int SearchLoop, Matches;
	String ModelMatch;
	SearchLoop = 0;
	Matches = 0;
	clrscr();
	cout<<"Model: ";
	cin>>ModelMatch;
	clrscr();
	for (SearchLoop = 0; SearchLoop <= Counter; SearchLoop++)
	{
		if (Model[SearchLoop] == ModelMatch)
		{
			cout<<"Make: "<<Make[SearchLoop]<<endl;
			cout<<"Model: "<<Model[SearchLoop]<<endl;
			cout<<"Year: "<<Year[SearchLoop]<<endl;
			cout<<"Price: "<<Price[SearchLoop]<<endl;
			cout<<"Mileage: "<<Mileage[SearchLoop]<<endl;
			cout<<"Lot: "<<Lot[SearchLoop]<<endl;
			cout<<"\n################\n"<<endl;
			Matches = Matches + 1;
		} else if (Matches == 0 && SearchLoop == Counter) {
			cout<<"No matches found in database\n"
			  <<"containing "<<Counter<<" Cars.\n\n"
			  <<"Hit any key to return to the \"Search\" menu.";
			getch();
			clrscr();
			StartProg();
		}
		if (Matches != 0 && SearchLoop == Counter)
		{
			cout<<"\n\nHit any key to return to the \"Search\" menu.";
			getch();
			clrscr();
			StartProg();
		}
	}
}
void SearchYear(stype &Make, stype &Model, stype &Year, stype &Price, stype &Mileage, stype &Lot, int &Counter)
{
	int SearchLoop, Matches;
	String MinimumYear, MaximumYear;
	char YearRange;
	//String ModelMatch;
	SearchLoop = 0;
	Matches = 0;
	MinimumYear = "0";
	MaximumYear = "0";
	clrscr();
	cout<<"--- Year Ranges --- "<<endl;
	cout<<"A. 1970-1975"<<endl;
	cout<<"B. 1976-1980"<<endl;
	cout<<"C. 1981-1985"<<endl;
	cout<<"D. 1986-1990"<<endl;
	cout<<"E. 1991-1995"<<endl;
	cout<<"F. 1996-2000"<<endl;
	cout<<"G. 2001-2005"<<endl;
	cout<<"------------------- "<<endl;
	cout<<"Year Range: ";
	cin>>YearRange;
	YearRange=toupper(YearRange);
	switch (YearRange) {
	case 'A':
		MinimumYear="1970";
		MaximumYear="1975";
		break;
	case 'B':
		MinimumYear="1976";
		MaximumYear="1980";
		break;
	case 'C':
		MinimumYear="1981";
		MaximumYear="1985";
		break;
	case 'D':
		MinimumYear="1986";
		MaximumYear="1990";
		break;
	case 'E':
		MinimumYear="1991";
		MaximumYear="1995";
		break;
	case 'F':
		MinimumYear="1996";
		MaximumYear="2000";
		break;
	case 'G':
		MinimumYear="2001";
		MaximumYear="2005";
		break;
	default:
		clrscr();
		cout<<"That year is not available."<<endl;
		cout<<"Hit any key to return to the \"Search\" menu."<<endl;
		getch();
		StartProg();
		break;
	}
	clrscr();
	for (SearchLoop = 0; SearchLoop <= Counter; SearchLoop++)
	{
		if (Year[SearchLoop] >= MinimumYear && Year[SearchLoop] <= MaximumYear)
		{
			cout<<"Make: "<<Make[SearchLoop]<<endl;
			cout<<"Model: "<<Model[SearchLoop]<<endl;
			cout<<"Year: "<<Year[SearchLoop]<<endl;
			cout<<"Price: "<<Price[SearchLoop]<<endl;
			cout<<"Mileage: "<<Mileage[SearchLoop]<<endl;
			cout<<"Lot: "<<Lot[SearchLoop]<<endl;
			cout<<"\n################\n"<<endl;
			Matches = Matches + 1;
		} else if (Matches == 0 && SearchLoop == Counter) {
			cout<<"No matches found in database\n"
			  <<"containing "<<Counter<<" Cars.\n\n"
			  <<"Hit any key to return to the \"Search\" menu.";
			getch();
			clrscr();
			StartProg();
		}
		if (Matches != 0 && SearchLoop == Counter)
		{
			cout<<"\n\nHit any key to return to the \"Search\" menu.";
			getch();
			clrscr();
			StartProg();
		}
	}
}
void SearchPrice(stype &Make, stype &Model, stype &Year, stype &Price, stype &Mileage, stype &Lot, int &Counter)
{
	clrscr();
	int SearchLoop, Matches;
	SearchLoop = 0;
	Matches = 0;
	String PriceMatch, StartPrice, EndPrice;
	cout<<"*Note* Do not Include commas or dollar signs\n\n";
	cout<<"Starting Price: ";
	cin>>StartPrice;
	clrscr();
	cout<<"*Note* Do not Include commas or dollar signs\n\n";
	cout<<"Ending Price: ";
	cin>>EndPrice;
	clrscr();
	for (SearchLoop = 0; SearchLoop <= Counter; SearchLoop++)
	{
		if (Price[SearchLoop] >= StartPrice && Price[SearchLoop] <= EndPrice)
		{
			cout<<"Make: "<<Make[SearchLoop]<<endl;
			cout<<"Model: "<<Model[SearchLoop]<<endl;
			cout<<"Year: "<<Year[SearchLoop]<<endl;
			cout<<"Price: "<<Price[SearchLoop]<<endl;
			cout<<"Mileage: "<<Mileage[SearchLoop]<<endl;
			cout<<"Lot: "<<Lot[SearchLoop]<<endl;
			cout<<"\n################\n"<<endl;
			Matches++;
		}
		if (Matches == 0 && SearchLoop == Counter)
		{
			cout<<"No matches found in database\n"
			  <<"containing "<<Counter<<" Cars.\n\n"
			  <<"Hit any key to return to the \"Search\" menu.";
			getch();
			clrscr();
			StartProg();
		}
		else if (Matches != 0 && SearchLoop == Counter)
		{
			cout<<"Hit any key to return to the \"Search\" menu.";
			getch();
			clrscr();
			StartProg();
		}
	}
}
```

