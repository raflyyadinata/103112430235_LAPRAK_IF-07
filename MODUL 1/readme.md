<h1 align="center">Laporan Praktikum Modul 1 <br> pengenalan cpp</h1>
<p align="center">RAFLY ADINATA PRAYOGA - 103112430235</p>

## Dasar Teori

### Program Operasi Aritmatika
Konsep penting yang digunakan:
- **Fungsi (function):** kode yang dapat dipanggil untuk tugas tertentu.
- **Parameter & Return Value:** mengirim data ke fungsi dan pengembalian hasil.
- **Input/Output:** menggunakan `cin` untuk input dari pengguna dan `cout` untuk menampilkan hasil.

### Program Konversi Angka ke Teks (0–100)
Konsep yang dipakai:
- **Array:** digunakan untuk menyimpan tulisan satuan (`satuan[]`) dan puluhan (`puluhan[]`).
- **Percabangan (if-else):** menentukan tulisan yang sesuai untuk setiap rentang angka (satuan, belasan, puluhan, seratus, dan nol).
- **Operator Modulus (`%`) & Pembagian (`/`):** untuk memisahkan angka puluhan dan satuan.

### Program Pola Angka dengan For Loop
Konsep yang digunakan:
- **Perulangan Bersarang (nested for loop):** digunakan untuk membuat baris dan kolom secara bersamaan.

---

## Guided

### Soal 1

STRUCT

```cpp
#include <iostream>
#include <string>
using namespace std;

// Definisi struct
struct Mahasiswa {
    string nama;
    string nim;
    float ipk;
};

int main() {

    Mahasiswa mhs1;

    cout << "Masukkan Nama Mahasiswa: ";
    getline(cin, mhs1.nama);
    // cin >> mhs1.nama;
    cout << "Masukkan NIM Mahasiswa : ";
    cin >> mhs1.nim;
    cout << "Masukkan IPK Mahasiswa : ";
    cin >> mhs1.ipk;

    cout << "\n=== Data Mahasiswa ===" << endl;
    cout << "Nama : " << mhs1.nama << endl;
    cout << "NIM  : " << mhs1.nim << endl;
    cout << "IPK  : " << mhs1.ipk << endl;

    return 0;
}

```

> Output
> 
> ![Screenshot Output Guided 1](output/ss_guided_1.jpg)



---

### Soal 2

ARITMATIKA
```cpp
#include <iostream>
using namespace std;

// Prosedur: hanya menampilkan hasil, tidak mengembalikan nilai
void tampilkanHasil(double p, double l)
{
    cout << "\n=== Hasil Perhitungan ===" << endl;
    cout << "Panjang : " << p << endl;
    cout << "Lebar   : " << l << endl;
    cout << "Luas    : " << p * l << endl;
    cout << "Keliling: " << 2 * (p + l) << endl;
}

// Fungsi: mengembalikan nilai luas
double hitungLuas(double p, double l)
{
    return p * l;
}

// Fungsi: mengembalikan nilai keliling
double hitungKeliling(double p, double l)
{
    return 2 * (p + l);
}

int main()
{
    double panjang, lebar;

    cout << "Masukkan panjang: ";
    cin >> panjang;
    cout << "Masukkan lebar  : ";
    cin >> lebar;

    // Panggil fungsi
    double luas = hitungLuas(panjang, lebar);
    double keliling = hitungKeliling(panjang, lebar);

    cout << "\nDihitung dengan fungsi:" << endl;
    cout << "Luas      = " << luas << endl;
    cout << "Keliling  = " << keliling << endl;

    // Panggil prosedur
    tampilkanHasil(panjang, lebar);

    return 0;
}
```

> Output
> 
> ![Screenshot Output Guided 2](output/ss_guided_2.jpg)



---

### Soal 3
KONDISI

```cpp
#include <iostream>
using namespace std;
// int main()
// {
//     double tot_pembelian, diskon;
//     cout << "total pembelian: Rp";
//     cin >> tot_pembelian;
//     diskon = 0;
//     if (tot_pembelian >= 100000)
//         diskon = 0.05 * tot_pembelian;
//     cout << "besar diskon = Rp" << diskon;
// }



// int main()
// {
//     double tot_pembelian, diskon;
//     cout << "total pembelian: Rp";
//     cin >> tot_pembelian;
//     diskon = 0;
//     if (tot_pembelian >= 100000)
//         diskon = 0.05 * tot_pembelian;
//     else
//         diskon = 0;
//     cout << "besar diskon = Rp" << diskon;
// }



int main()
{
    int kode_hari;
    cout << "Menentukan hari kerja/libur\n"<<endl;
    cout << "1=Senin 3=Rabu 5=Jumat 7=Minggu "<<endl;
    cout << "2=Selasa 4=Kamis 6=Sabtu "<<endl;
    cin >> kode_hari;
    switch (kode_hari)
    {
    case 1:
    case 2:
    case 3:
    case 4:
    case 5:
        cout<<"Hari Kerja";
        break;
    case 6:
    case 7:
        cout<<"Hari Libur";
        break;
    default:
        cout<<"Kode masukan salah!!!";
    }
    return 0;
}
```

> Output
> 
> ![Screenshot Output Guided 3](output/ss_guided_3.jpg)



---

### Soal 4

PERULANGAN

```cpp
#include <iostream>
using namespace std;
// int main()
// {
//     int jum;
//     cout << "jumlah perulangan: ";
//     cin >> jum;
//     for (int i = 0; i < jum; i++)
//     {
//         cout << "saya sahroni\n";
//     }
//     return 1;
// }


// while
int main()
{
    int i = 1;
    int jum;
    cin >> jum;
    do
    {
        cout << "bahlil ke-" << (i + 1) << endl;
        i++;
    } while (i < jum);
    return 0;
}
```

> Output
> 
> ![Screenshot Output Guided 4](output/ss_guided_4.jpg)


---

### Soal 5

FUNGSI

```cpp
#include <iostream>
using namespace std;

// Prosedur: hanya menampilkan hasil, tidak mengembalikan nilai
void tampilkanHasil(double p, double l)
{
    cout << "\n=== Hasil Perhitungan ===" << endl;
    cout << "Panjang : " << p << endl;
    cout << "Lebar   : " << l << endl;
    cout << "Luas    : " << p * l << endl;
    cout << "Keliling: " << 2 * (p + l) << endl;
}

// Fungsi: mengembalikan nilai luas
double hitungLuas(double p, double l)
{
    return p * l;
}

// Fungsi: mengembalikan nilai keliling
double hitungKeliling(double p, double l)
{
    return 2 * (p + l);
}

int main()
{
    double panjang, lebar;

    cout << "Masukkan panjang: ";
    cin >> panjang;
    cout << "Masukkan lebar  : ";
    cin >> lebar;

    // Panggil fungsi
    double luas = hitungLuas(panjang, lebar);
    double keliling = hitungKeliling(panjang, lebar);

    cout << "\nDihitung dengan fungsi:" << endl;
    cout << "Luas      = " << luas << endl;
    cout << "Keliling  = " << keliling << endl;

    // Panggil prosedur
    tampilkanHasil(panjang, lebar);

    return 0;
}

```

> Output
> 
> ![Screenshot Output Guided 5](output/ss_guided_5.jpg)


---

### Soal 6

TEST

```cpp
#include <iostream>
using namespace std;
int main()
{
    string ch;
    cout << "Masukkan sebuah karakter: ";
    // cin >> ch;
    ch = getchar();  //Menggunakan getchar() untuk membaca satu karakter
    cout << "Karakter yang Anda masukkan adalah: " << ch << endl;
    return 0;
}

```

> Output
> 
> ![Screenshot Output Guided 6](output/ss_guided_6.jpg)



---

## Unguided

### Soal 1

Buatlah program yang menerima input-an dua buah bilangan bertipe float, kemudian memberikan output-an hasil penjumlahan, pengurangan, perkalian, dan pembagian dari dua bilangan tersebut.

```cpp
#include <iostream>
using namespace std;

// function to read two float numbers from user input
void readNumbers (float &a, float &b) {
   cout << "enter first float number : ";
   cin >> a;
   cout << "enter second float number : ";
   cin >> b;
   cout << "ok, we have " << a << " and " << b << endl;
   cout << "so..." << endl;
}

// function to add two numbers
float addition (float a, float b) {
   return a + b;
}

// function to subtract two numbers
float subtraction (float a, float b) {
   return a - b;
}

// function to multiply two numbers
float multiplication (float a, float b) {
   return a * b;
}

// function to divide two numbers
float division (float a, float b) {
   return a / b;
}

int main() {
   // declare two floats
   float a, b;
   // read input values from user
   readNumbers(a, b);

   // perform calculations
   float add = addition(a, b);
   float sub = subtraction(a, b);
   float mul = multiplication(a, b);
   float div = division(a, b);

   // print results
   cout << a << " + " << b << " = " << add  << endl;
   cout << a << " - " << b << " = " << sub << endl;
   cout << a << " * " << b << " = " << mul << endl;
   cout << a << " / " << b << " = " << div << endl;

   return 0;
}
```

> Output
> 
> ![Screenshot Output Unguided 1](output/ss_unguided_1.jpg)


---

### Soal 2

Buatlah sebuah program yang menerima menerima masukan angka dan mengeluarkan output nilai angka tersebut dalam bentuk tulisan. Angka yang akan di-input-kan user adalah bilangan bulat positif mulai dari 0 s.d 100

<pre>79 : tujuh puluh sembilan</pre>

```cpp
#include <iostream>
using namespace std;

int main() {
   // array 1-10
   string satuan[]  = {"", "satu", "dua", "tiga", "empat", "lima", "enam", "tujuh", "delapan", "sembilan", "sepuluh"};
   // array 20, 30, 40, ..., 90
   string puluhan[] = {"", "", "dua puluh", "tiga puluh", "empat puluh", "lima puluh", "enam puluh", "tujuh puluh", "delapan puluh", "sembilan puluh"};

   // declare n
   int n;
   // read n values from user
   cout << "enter number 0-100 : ";
   cin >> n;

   // 1 -10
   if (n >= 1 && n <= 10) {
      cout << satuan[n];
   }

   // 20 - 99
   else if (n >= 20 && n <= 99) {
      cout << puluhan[n/10] << " " << satuan[n%10];
   }

   // 11 - 19
   else if (n >= 11 && n <= 19) {
      if (n == 11) {
         cout << "sebelas";
      } else {
         cout << satuan[n % 10] << " belas";
      }
   }

   // 0
   else if (n == 0) {
      cout << "nol";
   }

   // 100
   else if (n == 100) {
      cout << "seratus";
   }

   // not 0-100
   else {
      cout << "angka di luar 0-100";
   }

   return 0;
}
```

> Output
> 
> ![Screenshot Output Unguided 2](output/ss_unguided_2.jpg)


---

### Soal 3

Buatlah program yang dapat memberikan input dan output sebagai berikut.

<pre>
input  : 3
output :
321*123
 21*12
  1*1
   *
</pre>

```cpp
#include <iostream>
using namespace std;

int main() {
   // declare n
   int n;
   // read n values from user
   cout << "enter n : ";
   cin >> n;

   // outer for to create rows
   for (int i = n; i >= 1; i--) {
      // inner for to print space before numbers
      for (int k = 0; k < n - i; k++) {
         cout << " ";
      }

      // inner for to print descending numbers
      for (int j = i; j >= 1; j--) {
         cout << j;
      }

      // print * as a mirror
      cout << "*";

      // inner for to print ascending numbers
      for (int j = 1; j <= i; j++) {
         cout << j;
      }
      cout << endl;
   }

   // 2nd outer for to print space before last *
   for (int k = 0; k < n; k++) {
      cout << " ";
   }

   // * tail
   cout << "*";

   return 0;
}
```

> Output
> 
> ![Screenshot Output Unguided 3](output/ss_unguided_3.jpg)



## Referensi
