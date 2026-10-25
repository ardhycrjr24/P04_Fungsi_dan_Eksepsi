**Nama:** Ardiansyah  
**NIM:** 6304250091  
**Kelas:** RPL3D Rekayasa Perangkat Lunak (RPL)  
**Dosen Pengampu:** Depandi Enda, S.ST., M.Kom

# P04 - Fungsi dan Eksepsi

Praktikum 4 mata kuliah Pemrograman Multiplatform: mempelajari fungsi (deklarasi, parameter, return, lambda, callback, rekursi) dan eksepsi (throw, try-on-catch-finally, eksepsi buatan pengguna) melalui 24 program console di Dart.

## Tujuan

- Mengidentifikasi jenis fungsi dan eksepsi di Dart.
- Mendefinisikan fungsi dan eksepsi di Dart.
- Mengimplementasikan fungsi dan eksepsi di Dart.
- Membuat aplikasi Dart berbasis console.

## Alat yang Digunakan

- macOS (Apple Silicon)
- Dart SDK 3.13.2 (via Flutter SDK)
- Visual Studio Code + extension Dart
- Git
- Terminal

## Struktur Folder

```text
P04_Fungsi_dan_Eksepsi/
├── ex1_fungsi_math.dart                 # Fungsi bawaan dart:math (sqrt, pow)
├── ex2_fungsi_void.dart                 # Fungsi void dengan dynamic
├── ex2_fungsi_return_null.dart          # Fungsi tanpa return (return null)
├── ex3_fungsi_return.dart               # Fungsi dengan return value
├── ex4_fungsi_ringkas.dart              # Arrow syntax (=>)
├── ex5_fungsi_parameter.dart            # Parameter wajib
├── ex6_parameter_opsional_posisi.dart   # Parameter opsional posisi [...]
├── ex7_parameter_opsional_nama.dart     # Parameter opsional penamaan {...}
├── ex8_parameter_opsional_default.dart  # Parameter opsional default value
├── ex9_passing_parameter_list.dart      # Passing parameter List
├── ex10_passing_parameter_map.dart      # Passing parameter Map
├── ex11_fungsi_lambda.dart              # Fungsi anonim (lambda)
├── ex12_fungsi_sebagai_parameter.dart   # Higher-order function
├── ex13_fungsi_callback.dart            # Callback fungsi bernama
├── ex14_fungsi_dalam_fungsi_lain.dart   # Fungsi bersarang (nested)
├── ex15_fungsi_rekursif.dart            # Fungsi rekursif (faktorial)
├── ex16_list_map_lanjutan.dart          # Operasi List & Map lanjutan
├── ex17_throw.dart                      # Keyword throw
├── ex18_throw_exception.dart            # Throw Exception kustom
├── ex19_try_on.dart                     # Blok try-on spesifik
├── ex20_try_catch.dart                  # Blok try-catch umum
├── ex21_try_catch_finally.dart          # Blok try-catch-finally
├── ex22_multiple_exception.dart         # Multiple blok on
└── ex23_user_defined_exception.dart     # Eksepsi buatan pengguna
```

## Catatan

- Parameter opsional posisi pada `ex6` dan named parameter pada `ex7` disesuaikan menjadi nullable (`int?`, `bool?`) sesuai aturan null safety Dart 3.
- `stdin.readLineSync()` pada `ex17`–`ex23` ditambahkan operator `!` karena mengembalikan `String?`.
- Properti `message` pada kelas `NegativeError` di `ex23` diubah menjadi `String? message` agar aman terhadap nilai null.
- `IntegerDivisionByZeroException` pada `ex17`, `ex19`, dan `ex22` dipertahankan sesuai modul (pada Dart modern disarankan `UnsupportedError`).
- Peringatan `unused_catch_stack` pada `ex22` dan `ex23` dibiarkan sesuai modul untuk menunjukkan penulisan penanganan eksepsi lengkap.
