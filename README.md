# LIB_DIRTY
nothinng



#include<iostream>
#include<string>
#include<vector>
#include<set>
using namespace std;
class LIB
{
private:
	string name, adress, department, phone_num;
public:
	LIB(string a,string b,string d,string c)
	{
		name = a; adress = b; department = c; phone_num = d;
	}
	string getd()
	{
		return department;
	}
	string getn()
	{
		return name;
	}
	void getinfo()
	{
		cout << "Имя: " << name << endl << "Адрес: "<<adress << endl << "Отдел:"<<department << endl<<"Номерок: "<<phone_num<<endl;
	}
};
class R
{
private:
	string name, phone_num, order;
public:
	R(string a, string e, string d)
	{
		name = a; phone_num = d; order = e;
	}
	string getb()
	{
		return order;
	}
	string getn()
	{
		return name;
	}
	void getinfo()
	{
		cout << "Имя: " << name << endl << "Номер: " << phone_num << endl << "Заказ: " << order;
	}
};
class Order 
{
private:
	string book, author; int time1, time2, year;
public:
	Order(string k, string l, int m, int n, int o) 
	{
		book = k;
		author = l;
		time1 = m;
		time2 = n;
		year = o;
	}
	int gettime()
	{
		return time1 + time2;
	}
	string getb()
	{
		return book;
	}
	void getinfo() 
	{
		cout << "Название книги: " << book << endl << "Автор: " << author << endl << "Год издания: " << year << endl << "Время доставки: " << time1 << endl << "Hold time: " << time2 << endl;
	}
};
void READLIST(vector<R> & werewolf)
{
	int e = 0; int  n = werewolf.size(); string t;
	cout << "Поиск по читателям введите книгу: "; cin >> t;
	while (n--)
	{
		if (werewolf[e].getb() == t)
		{
			cout << werewolf[e].getn() << endl;
		}
		e++;
	}
	cout << endl << endl;
}
void LIBLIST(vector<LIB> & reptiloid)
{
	cout << "Поиск по отделу библиотекарей";
	string t;int  e = 0; int n = reptiloid.size(); cout<<endl<<"Введите отдел: ";cin >> t;
	while (n--)
	{
		if (reptiloid[e].getd() == t)
		{
			cout << reptiloid[e].getn() << endl;
		}
		e++;
	}
	cout<<endl<<endl;
}
void TIMEB(vector<Order>& old)
{
    int min{INT16_MAX}; double medium {0};
	int n = old.size();int e = 0;
	while (n--)
	{
		medium += old[e].gettime();
		if (old[e].gettime() < min)
		{
			min = old[e].gettime();
		}
		e++;
	}
	cout << endl << "Минимальное время заказа " << min << endl << "Среднее время заказа " << medium / e << endl;
}
string POPBOOK(vector<R> & werewolf,vector<Order> & old)
{
	set<string> pop; int e = 0; int n = old.size();
	while (n--)
	{
		pop.insert(old[e].getb());
		e++;
	}
	set<string>::iterator yuy; int max = -1; string popular;
	for (yuy = pop.begin(); yuy != pop.end(); yuy++)
	{
		n = werewolf.size(); e = 0; int y = 0;
		while (n--)
		{
			if (werewolf[e++].getb() == *yuy)
			{
				y++;
			}
		}
		if (y > max)
		{
			max = y;
			popular = *yuy;
		}
	}
	return popular;
}
int main()
{
	setlocale(LC_ALL, "");
	int n;
	cout << "Введите число библиотекарей: "; cin >> n; int e = 0;
	vector<LIB> Reptiloid;
	while (n--)
	{
		string name, adress, cell_phone, department;
		cout << "Имя: "; cin >> name;
		cout << "Адрес: "; cin >> adress; 
		cout << "Номер: "; cin >> cell_phone; 
		cout << "Отдел: "; cin >> department; 
		LIB* q = new LIB(name, adress, cell_phone, department);
		Reptiloid.push_back(*q);
		delete q; q = nullptr;
	}
	n = Reptiloid.size(); e = 0; cout << endl << endl << endl;
	while (n--)
	{
		Reptiloid[e++].getinfo(); cout << endl;
	}
	vector<R> Werewolf; n = 0;
	cout << "Введите число читателей: "; cin >> n;
	while (n--)
	{
		string name, order, cell_phone;
		cout << "Имя: "; cin >> name, 
		cout << "Заказ: "; cin >> order; 
		cout << "Номер: "; cin >> cell_phone; 
		R* q = new R(name, order, cell_phone);
		Werewolf.push_back(*q);
		delete q; q = nullptr;
	}
	n = Werewolf.size(); e = 0;  cout << endl << endl << endl;
	while (n--)
	{
		Werewolf[e++].getinfo(); cout << endl;
	}
	vector<Order> OLD; n = 0;
	cout << "Введите число заказов: "; cin >> n;
	while (n--)
	{
		string name, author; int t1, t2, year;
		cout << "Название книги: "; cin >> name, cout << endl;
		cout << "Автор: "; cin >> author; cout << endl;
		cout << "Delivery time to the client: "; cin >> t1; cout << endl;
		cout << "Hold time: "; cin >> t2, cout << endl;
		cout << "Год издания: "; cin >> year; cout << endl;
		Order* q = new Order(name, author, t1, t2, year);
		OLD.push_back(*q);
		delete q; q = nullptr;
	}
	n = OLD.size(); e = 0; cout << endl << endl << endl;
	while (n--)
	{
		OLD[e++].getinfo(); cout << endl;
	}
	cout << endl << endl; 
	//LIBLIST(Reptiloid);
	//READLIST(Werewolf);
	//cout << POPBOOK(Werewolf,OLD);
	//TIMEB(OLD);
	return 0;
}
