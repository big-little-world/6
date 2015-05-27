# 6
// 3 laba.cpp: определяет точку входа для консольного приложения.
//списки, стеки, очереди
/*
1. Списки.
	Входные данные:
N - количество действий со списком (простой односвязный)
	а <индекс> <значение>
	b <индекс>
	-
	-
	-
	Выходные данные:
распечатать списко.
	Пример 
	а1 10
	а1 9
	b2
	9
*/
#include "stdafx.h"
#include "locale.h"
#include "iostream"
using namespace std;

struct DoubleList //opisanie uzla spiska
{
int data; //information pole
DoubleList *next; //ykazatel' na sleduyshii elemntik
DoubleList *prev; //ykazatel' na predidushiy elementik
};
DoubleList *head; //ykazatel' na perviy element spiska
//dobavlenie elementa
void AddList(int value, int position)
{
DoubleList *node=new DoubleList; //создание нового элемента
node->data=value; //присвоение элементу значения
if (head==NULL) //если список пуст
{
node->next=node; //установка указателя next
node->prev=node; //установка указателя prev
head=node; //определяется голова списка
}
else
{
DoubleList *p=head;
for(int i=position; i>1; i--) p=p->next;
p->prev->next=node;
node->prev=p->prev;
node->next=p;
p->prev=node;
}
cout<<"\nElement dobavlen!!!\n\n";
}

//Udalenie elemntika
int DeleteList(int znache)
{
	if (head==NULL)
	{
		cout<<"\nSpisok pust\n\n"; return 0;
	}
	if(head==head->next)
	{
		delete head;
		head=NULL;
	}
	else
	{
		DoubleList *a=head;
		for (int i=znache; i>1; i--) a=a->next;
		if (a==head)
			head=a->next;
		a->prev->next=a->next;
		a->next->prev=a->prev;
		delete a;
}
	cout<<"\nElementik udalen!!!\n\n";
}
//vivod spiska
void PrintList()
{
	if(head==NULL) 
		cout<<"\nSpisok pust\n\n";
	else
	{
		DoubleList *a=head;
		cout<<"\nElementi spiska: ";
		do
		{
			cout<<a->data<<" ";
			a=a->next;
		}
		while (a!=head); cout<<"\n\n";
	}
}

int _tmain(int argc, _TCHAR* argv[])
{   
int znache, pozi, x;
do
{
cout<<"1.dobavit' element"<<endl;
cout<<"2.udalit' element"<<endl;
cout<<"3. Vivesti spisok"<<endl;
cout<<"0. Viyti"<<endl;
cout<<"\n\nNomer operacii > "; cin>>x;
switch (x)
{
case 1:
	cout<<"Znachenie > "; cin>>znache;
		cout <<"Poziciya > "; cin>>pozi;
		//DeleteList(pozi); break;
		AddList(znache,pozi); break;
case 2:
	cout << "Znachenie > "; cin >> znache;
	//cout << "Poziciya > "; cin >> pozi;
	DeleteList(znache); break;
case 3: PrintList(); break;
}
}
while (x!=0);
}

	
