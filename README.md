#include <iostream>
#include <thread>
#include <chrono>
#include <string>
#include <cmath>

using namespace std;

// Fungsi animasi per karakter
void animasiTeks(const string& teks, int delayMs = 40) {
    for (char c : teks) {
        cout << c << flush;
        this_thread::sleep_for(chrono::milliseconds(delayMs));
    }
    cout << endl;
}

const double KURS_DOLLAR = 16.000;

// Fungsi-fungsi utama
void konversiRupiahKeDollar() {
    double rupiah;
    cout << "\nMasukkan jumlah Rupiah: ";
    cin >> rupiah;
    double dollar = rupiah / KURS_DOLLAR;
    cout << "Hasil konversi: $ " << dollar << endl;
}

void hitungDiskon() {
    double harga, persen;
    cout << "\nMasukkan harga barang (Rp): ";
    cin >> harga;
    cout << "Masukkan persen diskon (contoh: 20%): ";
    cin >> persen;
    double hasil = harga - (harga * persen / 100);
    int final=std::round(hasil);
    cout << "Harga setelah diskon: Rp" << fixed << (final) << endl;
}

void hitungUntungRugi() {
    double beli, jual;
    cout << "\nMasukkan harga beli: ";
    cin >> beli;
    cout << "Masukkan harga jual: ";
    cin >> jual;
    double selisih = jual - beli;

    if (selisih > 0)
        cout << "Keuntungan: Rp " << selisih << endl;
    else if (selisih < 0)
        cout << "Kerugian: Rp " << -selisih << endl;
    else
        cout << "Tidak ada keuntungan maupun kerugian." << endl;
}

void hitungTabunganMasaDepan() {
    double tabunganAwal, bunga, tahun;
    cout << "\nMasukkan tabungan awal (Rp): ";
    cin >> tabunganAwal;
    cout << "Masukkan suku bunga (%): ";
    cin >> bunga;
    cout << "Masukkan jangka waktu (tahun): ";
    cin >> tahun;

    double hasil = tabunganAwal * pow(1 + bunga / 100, tahun);
    cout << "Total tabungan setelah " << tahun << " tahun: Rp " << fixed << hasil << endl;
}    

void tampilkanMenu() {
    cout << "\n=== MENU KALKULATOR KEUANGAN ===" << endl;
    cout << "1. Konversi Rupiah ke Dollar" << endl;
    cout << "2. Hitung Diskon" << endl;
    cout << "3. Hitung Untung/Rugi" << endl;
    cout << "4. Hitung Tabungan Masa Depan" << endl;
    cout << "5. Keluar" << endl;
    cout << "Pilih menu (1-5): ";
}

int main() {
    // Animasi teks selamat datang
    animasiTeks("\n===========================================", 2 );
    animasiTeks("   SELAMAT DATANG DI KALKULATOR KEUANGAN   ", 200);
    animasiTeks("        Dibuat Oleh Kelompok 1           ", 90);
    animasiTeks("===========================================", 20);

    int pilihan;
    do {
        tampilkanMenu();
        cin >> pilihan;

        switch (pilihan) {
            case 1: konversiRupiahKeDollar(); break;
            case 2: hitungDiskon(); break;
            case 3: hitungUntungRugi(); break;
            case 4: hitungTabunganMasaDepan(); break;
            case 5: cout << "\nTerima kasih telah menggunakan kalkulator keuangan!\n"; main();
            default: cout << "Pilihan tidak valid. Silakan coba lagi.\n";
        }
    } while (pilihan != 5);

 return 0;
}
