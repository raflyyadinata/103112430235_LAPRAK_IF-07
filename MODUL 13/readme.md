<h1 align="center">Laporan Praktikum Modul 13 <br>multi linked list</h1>
<p align="center">RAFLY ADINATA PRAYOGA - 103112430235</p>

## Dasar Teori

---
Multi linked list adalah linked list dengan lebih dari satu pointer per node yang digunakan untuk mengelola relasi antar data. Sangat cocok untuk sistem many-to-many.

## Guided

### Soal 1

> 
```cpp
#include <iostream>
#include <string>
using namespace std;

struct ChildNode
{
    string info;
    ChildNode *next;
};

struct ParentNode
{
    string info;
    ChildNode *childHead;
    ParentNode *next;
};

ParentNode *createParent(string info)
{
    ParentNode *newNode = new ParentNode;
    newNode->info = info;
    newNode->childHead = NULL;
    newNode->next = NULL;
    return newNode;
}

ChildNode *createChild(string info)
{
    ChildNode *newNode = new ChildNode;
    newNode->info = info;
    newNode->next = NULL;
    return newNode;
}

void insertParent(ParentNode *&head, string info)
{
    ParentNode *newNode = createParent(info);
    if (head == NULL)
    {
        head = newNode;
    }
    else
    {
        ParentNode *temp = head;
        while (temp->next != NULL)
        {
            temp = temp->next;
        }
        temp->next = newNode;
    }
}

void insertChild(ParentNode *head, string parentInfo, string childInfo)
{
    ParentNode *p = head;
    while (p != NULL && p->info != parentInfo)
    {
        p = p->next;
    }
    
    if (p != NULL)
    {
        ChildNode *newChild = createChild(childInfo);
        
        if (p->childHead == NULL)
        {
            p->childHead = newChild;
        }
        else
        {
            ChildNode *c = p->childHead;
            while (c->next != NULL)
            {
                c = c->next;
            }
            c->next = newChild;
        }
    }
}

void printAll(ParentNode *head)
{
    ParentNode *p = head;
    while (p != NULL)
    {
        cout << p->info;
        ChildNode *c = p->childHead;
        if (c != NULL)
        {
            while (c != NULL)
            {
                cout << " -> " << c->info;
                c = c->next;
            }
        }
     cout << endl;
        p = p->next;
    }
}

int main()
{
    ParentNode *list = NULL;
    
    insertParent(list, "Parent Node 1");
    insertParent(list, "Parent Node 2");
    
    printAll(list);
    cout << "\n";
    
    insertChild(list, "Parent Node 1", "Child Node A");
    insertChild(list, "Parent Node 1", "Child Node B");
    insertChild(list, "Parent Node 2", "Child Node C");
    
    printAll(list);
    
    return 0;
}
```

> Output
> 
> ![Screenshot Output Guided 1](output/guided1.png)



## Unguided

### Soal 1

buat ADT Multi Linked List 

>circularlist.h
```cpp
#ifndef CIRCULARLIST_H_INCLUDED
#define CIRCULARLIST_H_INCLUDED

#include <iostream>
using namespace std;

#define Nil NULL

struct infotype {
    string nama;
    string nim;
    char jenis_kelamin;
    float ipk;
};

typedef struct ElmList *address;

struct ElmList {
    infotype info;
    address next;
};

struct List {
    address First;
};

// PROTOTYPE
void createList(List &L);
address alokasi(infotype x);
void dealokasi(address P);

void insertFirst(List &L, address P);
void insertAfter(List &L, address Prec, address P);
void insertLast(List &L, address P);

void deleteFirst(List &L, address &P);
void deleteAfter(List &L, address Prec, address &P);
void deleteLast(List &L, address &P);

address findElm(List L, infotype x);
void printInfo(List L);

#endif
```
>circularlist.cpp
```cpp
#include "circularlist.h"

void createList(List &L){
    L.First = Nil;
}

address alokasi(infotype x){
    address P = new ElmList;
    P->info = x;
    P->next = Nil;
    return P;
}

void dealokasi(address P){
    delete P;
}

void insertFirst(List &L, address P){
    if(L.First == Nil){
        L.First = P;
        P->next = P;
    } else {
        address Q = L.First;
        while(Q->next != L.First){
            Q = Q->next;
        }
        Q->next = P;
        P->next = L.First;
        L.First = P;
    }
}

void insertAfter(List &L, address Prec, address P){
    if(Prec != Nil){
        P->next = Prec->next;
        Prec->next = P;
    }
}

void insertLast(List &L, address P){
    if(L.First == Nil){
        L.First = P;
        P->next = P;
    } else {
        address Q = L.First;
        while(Q->next != L.First){
            Q = Q->next;
        }
        Q->next = P;
        P->next = L.First;
    }
}

void deleteFirst(List &L, address &P){
    if(L.First == Nil){
        P = Nil;
    } else if(L.First->next == L.First){
        P = L.First;
        L.First = Nil;
    } else {
        address Q = L.First;
        while(Q->next != L.First){
            Q = Q->next;
        }
        P = L.First;
        Q->next = P->next;
        L.First = P->next;
        P->next = Nil;
    }
}

void deleteAfter(List &L, address Prec, address &P){
    if(Prec != Nil){
        P = Prec->next;
        Prec->next = P->next;
        P->next = Nil;
    }
}

void deleteLast(List &L, address &P){
    if(L.First == Nil){
        P = Nil;
    } else if(L.First->next == L.First){
        P = L.First;
        L.First = Nil;
    } else {
        address Q = L.First;
        while(Q->next->next != L.First){
            Q = Q->next;
        }
        P = Q->next;
        Q->next = L.First;
        P->next = Nil;
    }
}

address findElm(List L, infotype x){
    if(L.First == Nil) return Nil;
    address P = L.First;
    do {
        if(P->info.nim == x.nim){
            return P;
        }
        P = P->next;
    } while(P != L.First);
    return Nil;
}

void printInfo(List L){
    if(L.First == Nil){
        cout << "List kosong" << endl;
        return;
    }

    address P = L.First;
    do {
        cout << "Nama : " << P->info.nama << endl;
        cout << "NIM  : " << P->info.nim << endl;
        cout << "L/P  : " << P->info.jenis_kelamin << endl;
        cout << "IPK  : " << P->info.ipk << endl;
        cout << endl;

        P = P->next;
    } while(P != L.First);
}
```
main.cpp
```cpp
    #include <iostream>
#include "circularlist.h"
using namespace std;

address createData(string nama, string nim, char jenis_kelamin, float ipk)
{
    infotype x;
    x.nama = nama;
    x.nim = nim;
    x.jenis_kelamin = jenis_kelamin;
    x.ipk = ipk;
    return alokasi(x);
}

int main()
{
    List L;
    address P1, P2;
    infotype x;

    createList(L);

    cout << "coba insert first, last, dan after" << endl;

    P1 = createData("Danu", "04", 'l', 4.0);
    insertFirst(L, P1);

    P1 = createData("Fahmi", "06", 'l', 3.45);
    insertLast(L, P1);

    P1 = createData("Bobi", "02", 'l', 3.71);
    insertFirst(L, P1);

    P1 = createData("Ali", "01", 'l', 3.3);
    insertFirst(L, P1);

    P1 = createData("Gita", "07", 'p', 3.75);
    insertLast(L, P1);

    x.nim = "07";
    P1 = findElm(L,x);
    P2 = createData("Cindi", "03", 'p', 3.5);
    insertAfter(L, P1, P2);

    x.nim = "02";
    P1 = findElm(L,x);
    P2 = createData("Hilmi", "08", 'p', 3.3);
    insertAfter(L, P1, P2);

    x.nim = "04";
    P1 = findElm(L,x);
    P2 = createData("Eli", "05", 'p', 3.4);
    insertAfter(L, P1, P2);

    printInfo(L);

    return 0;
}
```

> Output
> Program ini menggunakan struktur data Circular Linked List .main menambahkan variabel list menggunakan fungsi insertLast(), kmudian mencetak seluruh isi list dengan printList(). traversal dilakukan mulai dari head dan berhenti ketika kembali ke node awal. Program ini menunjukkan cara menyimpan dan menampilkan data secara berurutan menggunakan linked list yang ujungnya terhubung kembali ke awal.
> ![Screenshot Output Unguided 1](output/unguided1.png)

---


## Referensi
> 

