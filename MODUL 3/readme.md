<h1 align="center">Laporan Praktikum Modul 3 <br>singly linked list</h1>
<p align="center">RAFLY ADINATA PRAYOGA - 103112430235</p>

## Dasar Teori


---

## Guided

### Soal 1


```cpp
#include <iostream>
using namespace std;

// Struktur Node
struct Node {
 int data;
 Node* next;
};

// Pointer kepala (head)
Node* kepala = nullptr;

// Fungsi untuk membuat node baru
Node* buatNode(int data) {
 Node* nodeBaru = new Node();
 nodeBaru->data = data;
 nodeBaru->next = nullptr;
 return nodeBaru;
}

// Fungsi untuk menyisipkan node di depan
void sisipDepan(int data) {
 Node* nodeBaru = buatNode(data);
 nodeBaru->next = kepala; // Node baru menunjuk ke kepala lama
 kepala = nodeBaru;       // Kepala sekarang menunjuk ke node baru
 cout << "Data " << data << " berhasil disisipkan di depan.\n";
}

// Fungsi untuk menyisipkan node di belakang
void sisipBelakang(int data) {
 Node* nodeBaru = buatNode(data);
 if (kepala == nullptr) {
     kepala = nodeBaru;
 } else {
     Node* temp = kepala;
     while (temp->next != nullptr) {
         temp = temp->next;
     }
     temp->next = nodeBaru;
 }
 cout << "Data " << data << " berhasil disisipkan di belakang.\n";
}

// Fungsi untuk menyisipkan node setelah node tertentu
void sisipSetelah(int target, int dataBaru) {
 Node* temp = kepala;
 while (temp != nullptr && temp->data != target) {
     temp = temp->next;
 }

 if (temp == nullptr) {
     cout << "Data target " << target << " tidak ditemukan!\n";
 } else {
     Node* nodeBaru = buatNode(dataBaru);
     nodeBaru->next = temp->next;
     temp->next = nodeBaru;
     cout << "Data " << dataBaru << " berhasil disisipkan setelah " << target << ".\n";
 }
}

// ========== FUNGSI HAPUS ==========
void hapusNode(int data) {
 if (kepala == nullptr) {
     cout << "List kosong!\n";
     return;
 }

 Node* temp = kepala;
 Node* sebelumnya = nullptr;

 // Kasus 1: Jika data di node pertama (kepala)
 if (temp != nullptr && temp->data == data) {
     kepala = temp->next;
     delete temp;
     cout << "Data " << data << " berhasil dihapus.\n";
     return;
 }

 // Kasus 2: Cari node yang akan dihapus
 while (temp != nullptr && temp->data != data) {
     sebelumnya = temp;
     temp = temp->next;
 }

 // Jika data tidak ditemukan
 if (temp == nullptr) {
     cout << "Data " << data << " tidak ditemukan!\n";
     return;
 }

 // Lepaskan node dari list dan bebaskan memori
 sebelumnya->next = temp->next;
 delete temp;
 cout << "Data " << data << " berhasil dihapus.\n";
}

// ========== FUNGSI PERBARUI ==========
void perbaruiNode(int dataLama, int dataBaru) {
 Node* temp = kepala;
 while (temp != nullptr && temp->data != dataLama) {
     temp = temp->next;
 }

 if (temp == nullptr) {
     cout << "Data " << dataLama << " tidak ditemukan!\n";
 } else {
     temp->data = dataBaru;
     cout << "Data " << dataLama << " berhasil diperbarui menjadi " << dataBaru << ".\n";
 }
}

// ========== FUNGSI TAMPILKAN ==========
void tampilkanList() {
 if (kepala == nullptr) {
     cout << "List kosong!\n";
     return;
 }

 Node* temp = kepala;
 cout << "Isi Linked List: ";
 while (temp != nullptr) {
     cout << temp->data << " -> ";
     temp = temp->next;
 }
 cout << "NULL\n";
}

// ========== PROGRAM UTAMA ==========
int main() {
 int pilihan, data, target, dataBaru;

 do {
     cout << "\n=== MENU SINGLE LINKED LIST ===\n";
     cout << "1. Sisip Depan\n";
     cout << "2. Sisip Belakang\n";
     cout << "3. Sisip Setelah\n";
     cout << "4. Hapus Data\n";
     cout << "5. Perbarui Data\n";
     cout << "6. Tampilkan List\n";
     cout << "0. Keluar\n";
     cout << "Pilih opsi: ";
     cin >> pilihan;

     switch (pilihan) {
         case 1:
             cout << "Masukkan data: ";
             cin >> data;
             sisipDepan(data);
             break;
         case 2:
             cout << "Masukkan data: ";
             cin >> data;
             sisipBelakang(data);
             break;
         case 3:
             cout << "Masukkan data target: ";
             cin >> target;
             cout << "Masukkan data baru: ";
             cin >> dataBaru;
             sisipSetelah(target, dataBaru);
             break;
         case 4:
             cout << "Masukkan data yang ingin dihapus: ";
             cin >> data;
             hapusNode(data);
             break;
         case 5:
             cout << "Masukkan data lama: ";
             cin >> data;
             cout << "Masukkan data baru: ";
             cin >> dataBaru;
             perbaruiNode(data, dataBaru);
             break;
         case 6:
             tampilkanList();
             break;
         case 0:
             cout << "Program selesai.\n";
             break;
         default:
             cout << "Pilihan tidak valid!\n";
     }
 } while (pilihan != 0);

 return 0;
}

```

> Output
> Fungsi tukar() menerima dua pointer ke int (*px dan *py).
*px artinya nilai di alamat yang ditunjuk oleh px.
Proses menukar:
Simpan nilai *px ke temp.
Salin nilai *py ke *px.
Salin temp ke *py.
> ![Screenshot Output Guided 1](output/guided1.png)



---

### Soal 2

CALL BY REFERENCE
```cpp
#include <iostream>
using namespace std;

void tukar(int &x, int &y);   

int main()
{
    int a = 10, b = 20;
    cout << "Sebelum ditukar: a = " << a << ", b = " << b << endl;
    tukar(a, b);
    cout << "Setelah ditukar: a = " << a << ", b = " << b << endl;
    return 0;
}

void tukar(int &x, int &y)
{
    int temp = x;
    x = y;
    y = temp;
}

```

> Output
> Fungsi tukar() menerima dua variabel by reference.
Artinya: x dan y langsung mereferensikan a dan b dari main() — tanpa pointer.
> ![Screenshot Output Guided 2](output/guided2.png)



---

## Unguided

### Soal 1

1. Buatlah sebuah program untuk melakukan transpose pada sebuah matriks persegi berukuran 3x3. Operasi transpose adalah mengubah baris menjadi kolom dan sebaliknya. Inisialisasi matriks awal di dalam kode, kemudian buat logika untuk melakukan transpose dan simpan hasilnya ke dalam matriks baru. Terakhir, tampilkan matriks awal dan matriks hasil transpose.

Contoh Output:

Matriks Awal:
1 2 3
4 5 6
7 8 9

Matriks Hasil Transpose:
1 4 7
2 5 8
3 6 9

```cpp
#include <iostream>
using namespace std;

int main() {
    int matriks[3][3] = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };

    int transpose[3][3];
    
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            transpose[j][i] = matriks[i][j];
        }
    }

    cout << "Matriks Awal:" << endl;
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            cout << matriks[i][j] << " ";
        }
        cout << endl;
    }

    cout << "\nMatriks Hasil Transpose:" << endl;
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            cout << transpose[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}


```

> Output
> Loop ini menukar baris dan kolom.
Misal:
matriks[0][1] = 2 akan dipindahkan ke transpose[1][0].
> ![Screenshot Output Unguided 1](output/unguided1.png)

---

### Soal 2

2. Buatlah program yang menunjukkan penggunaan call by reference. Buat sebuah prosedur bernama kuadratkan yang menerima satu parameter integer secara referensi (&). Prosedur ini akan mengubah nilai asli variabel yang dilewatkan dengan nilai kuadratnya. Tampilkan nilai variabel di main() sebelum dan sesudah memanggil prosedur untuk membuktikan perubahannya. 

Contoh Output:

Nilai awal: 5
Nilai setelah dikuadratkan: 25


```cpp
#include <iostream>
using namespace std;

void kuadratkan(int &x) {
    x = x * x;
}

int main() {
    int angka = 5;

    cout << "Nilai awal: " << angka << endl;

    kuadratkan(angka);

    cout << "Nilai setelah dikuadratkan: " << angka << endl;

    return 0;
}

```

> Output
> Fungsi ini menerima parameter integer by reference.
Nilai x diubah menjadi kuadratnya (x²) langsung mengubah variabel asli.
> ![Screenshot Output Unguided 2](output/unguided2.png)


---


## Referensi

https://www.geeksforgeeks.org/cpp/pointers-vs-references-cpp/ (diakses 5 Oktober 2025)
https://www.w3schools.com/cpp/cpp_pointers.asp (diakses 5 Oktober 2025)
https://codefinity.com/blog/References-vs-Pointers-in-C-plus-plus (diakses 6 Oktober 2025)
