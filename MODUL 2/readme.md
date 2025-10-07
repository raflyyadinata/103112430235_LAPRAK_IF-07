<h1 align="center">Laporan Praktikum Modul 1 <br> pengenalan cpp part 2</h1>
<p align="center">RAFLY ADINATA PRAYOGA - 103112430235</p>

## Dasar Teori

Dalam C++, struct digunakan untuk mengelompokkan beberapa variabel menjadi satu data. Operasi aritmatika seperti tambah, kurang, kali, dan bagi digunakan untuk menghitung data. Pernyataan kondisi seperti if dan switch digunakan untuk membuat keputusan dalam program. Struktur perulangan seperti for dan while digunakan untuk mengulang kode. Sedangkan fungsi digunakan untuk membagi program menjadi bagian-bagian kecil agar lebih rapi dan mudah dipahami. Semua ini adalah dasar penting dalam membuat program C++ yang baik.

---

## Guided

### Soal 1

CALL BY POINTER

```cpp
#include <iostream>
using namespace std;

void tukar(int *px, int *py);   
int main()
{
    int a = 10, b = 20;
    cout << "Sebelum ditukar: a = " << a << ", b = " << b << endl;
    tukar(&a, &b);
    cout << "Setelah ditukar: a = " << a << ", b = " << b << endl;
    return 0;
}

void tukar(int *px, int *py)
{
    int temp = *px;
    *px = *py;
    *py = temp;
}

```

> Output
> membuat tipe data Mahasiswa yang memiliki atribut nama, nim, dan ipk. Program meminta input dari pengguna, menyimpan data ke dalam struct, dan menampilkannya kembali ke layar.
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
> operasi aritmatika dengan variabel bertipe int dan float. Nilai X, Y, dan W dijumlahkan/dibagi, lalu hasilnya (float) ditampilkan ke layar.
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
> menerima dua input bilangan bertipe float  . kemudian menghitung hasil dari operasi penjumlahan, pengurangan, perkalian, dan pembagian. Setiap operasi dipisahkan dalam fungsi tersendiri agar kode lebih terstruktur dan mudah dibaca. Input dibaca menggunakan cin, dan hasil ditampilkan dengan cout.
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
> mengubah input berupa angka bulat dari 0 hingga 100 menjadi bentuk tulisan dalam Bahasa Indonesia. Program menggunakan array untuk menyimpan nama-nama angka satuan dan puluhan, serta menggunakan logika percabangan if-else untuk menangani kondisi khusus seperti angka 11, belasan, dan 100. Operator pembagian (/) dan modulo (%) digunakan untuk memisahkan digit puluhan dan satuan.
> ![Screenshot Output Unguided 2](output/unguided2.png)


---


## Referensi

https://www.duniailkom.com/tutorial-belajar-c-plus-plus-cara-membuat-fungsi-bahasa-c-plus-plus/#google_vignette (diakses 27 September 2025)
https://www.youtube.com/watch?v=hVzmJwyMH2Q&t=10s (diakses 29 September 2025)
https://www.belajarcpp.com/tutorial/cpp/struct/ (diakses 29 September 2025)
https://www.duniailkom.com/tutorial-belajar-c-plus-plus-perulangan-while-bahasa-c-plus-plus/ (diakses 30 September 2025)
