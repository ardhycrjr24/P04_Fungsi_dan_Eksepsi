# P04 - Fungsi dan Eksepsi

> **Nama:** Ardiansyah
> **Kelas:** Rekayasa Perangkat Lunak (RPL)
> **Mata Kuliah:** Pemrograman Multiplatform
> **Politeknik Negeri Bengkalis**

Praktikum 4: membuat aplikasi Dart berbasis console untuk mempelajari fungsi (deklarasi, parameter, return, lambda, callback, rekursi) dan eksepsi (throw, try-on-catch-finally, eksepsi buatan pengguna) di Dart.

## Alat & Bahan

- macOS (Apple Silicon)
- Dart SDK 3.13.2 (via Flutter SDK)
- Visual Studio Code + ekstensi Flutter & Dart

## Cara Menjalankan

Jalankan dari terminal di dalam folder ini:

```bash
dart run ex1_fungsi_math.dart
```

Khusus file yang butuh input keyboard (`ex17`–`ex23`), jalankan lewat terminal lalu ketik nilainya.

Di VS Code: buka file `.dart` lalu tekan **F5** atau klik tombol **▶ Run** di pojok kanan atas editor.

## Daftar Program

| No | File | Materi |
|----|------|--------|
| 1 | `ex1_fungsi_math.dart` | Fungsi bawaan `dart:math` (`sqrt`, `pow`) |
| 2 | `ex2_fungsi_void.dart` | Fungsi `void` dengan parameter `dynamic` |
| 3 | `ex2_fungsi_return_null.dart` | Fungsi tanpa `return` (menghasilkan `null`) |
| 4 | `ex3_fungsi_return.dart` | Fungsi dengan nilai kembalian (`return`) |
| 5 | `ex4_fungsi_ringkas.dart` | Fungsi ringkas `=>` (arrow function) |
| 6 | `ex5_fungsi_parameter.dart` | Fungsi tanpa dan dengan parameter |
| 7 | `ex6_parameter_opsional_posisi.dart` | Parameter opsional posisi `[...]` |
| 8 | `ex7_parameter_opsional_nama.dart` | Parameter opsional penamaan `{...}` |
| 9 | `ex8_parameter_opsional_default.dart` | Parameter opsional dengan nilai default |
| 10 | `ex9_passing_parameter_list.dart` | Passing parameter List |
| 11 | `ex10_passing_parameter_map.dart` | Passing parameter Map |
| 12 | `ex11_fungsi_lambda.dart` | Fungsi anonim / lambda |
| 13 | `ex12_fungsi_sebagai_parameter.dart` | Fungsi sebagai parameter |
| 14 | `ex13_fungsi_callback.dart` | Callback (nama fungsi dikirim sebagai argumen) |
| 15 | `ex14_fungsi_dalam_fungsi_lain.dart` | Fungsi bersarang (nested function) |
| 16 | `ex15_fungsi_rekursif.dart` | Fungsi rekursif (faktorial) |
| 17 | `ex16_list_map_lanjutan.dart` | Operasi List & Map lanjutan + fungsi pembungkus |
| 18 | `ex17_throw.dart` | `throw` eksepsi bawaan |
| 19 | `ex18_throw_exception.dart` | `throw Exception(...)` dengan pesan |
| 20 | `ex19_try_on.dart` | `try` – `on tipeEksepsi` (penanganan spesifik) |
| 21 | `ex20_try_catch.dart` | `try` – `catch` (penanganan umum) + input list |
| 22 | `ex21_try_catch_finally.dart` | `try` – `catch` – `finally` |
| 23 | `ex22_multiple_exception.dart` | Beberapa blok `on` untuk beberapa jenis eksepsi |
| 24 | `ex23_user_defined_exception.dart` | Eksepsi buatan pengguna (`class ... implements Exception`) |

## Catatan Perbaikan Kode

Kode pada modul ditulis untuk Dart versi lama, disesuaikan dengan null safety Dart 3:

- `ex6` — `[int n]` menjadi `[int? n]` karena parameter opsional tanpa default wajib nullable
- `ex7` — `{int n, bool newLine}` menjadi `{int? n, bool? newLine}` (alasan sama)
- `ex17`–`ex23` — `stdin.readLineSync()` ditambahkan `!` karena mengembalikan `String?`
- `ex23` — `String message;` pada class `NegativeError` menjadi `String? message;`
- `ex17`, `ex19`, `ex22` — `IntegerDivisionByZeroException` sudah *deprecated* (disarankan `UnsupportedError`), tetap dipertahankan sesuai modul; tetap berfungsi di Dart 3.13
- Warning `dart analyze` `unused_catch_stack` pada `ex22`/`ex23` disengaja ada — variabel `stackTrace` ditulis sesuai modul untuk keperluan pembelajaran

## Pemahaman Program (Tugas Praktikum)

### 1. Fungsi Dasar (ex1–ex5)

- **ex1 — Fungsi math:** `sqrt(25.0)` menghasilkan `5.0`, lalu `pow(5.0, 4)` menghasilkan `625.0`. Keduanya adalah fungsi bawaan dari library `dart:math` yang harus di-`import` dulu.
- **ex2 void — Fungsi tanpa nilai kembalian:** `void echo(dynamic value)` mencetak nilai apapun (String, int, double, List, Map) karena tipenya `dynamic`. Fungsi `void` tidak mengembalikan apa-apa.
- **ex2 return null — Fungsi tanpa return:** fungsi `echo` tidak punya `void` dan tidak punya `return`, sehingga ia mengembalikan `null`. Itulah sebabnya `Nilai a: null` — fungsi yang tidak mengembalikan nilai otomatis bernilai `null`.
- **ex3 — Nilai kembalian:** `div(8, 5)` memakai `/` sehingga hasilnya `1.6` (double), sedangkan `div_int(42, 4)` memakai `~/` ( bagi bulat) sehingga hasilnya `10` (int, pecahan dibuang).
- **ex4 — Fungsi ringkas:** `=>` menulis fungsi satu baris tanpa kurung kurawal dan tanpa `return` eksplisit. `div(20.4, 3.5) = 5.828...`, `concat` menyambung dua string, `odd(9)` bernilai `true` karena 9 ganjil.

### 2. Parameter Fungsi (ex5–ex10)

- **ex5 — Parameter wajib:** `fungsiNoParam()` tidak menerima argumen dan selalu mencetak 3 baris; `fungsiWithParam(str, jml)` mencetak sebanyak `n` yang dikirim (5 baris). Jumlah argumen **harus sesuai** deklarasi fungsi.
- **ex6 — Parameter opsional posisi:** `[int? n]` diberi tanda kurung siku, jadi boleh tidak diisi. Saat tidak diisi `n == null` lalu di-set 1, sehingga hanya mencetak 1 baris; saat diisi 3 mencetak 3 baris.
- **ex7 — Parameter penamaan:** `{int? n, bool? newLine}` dipanggil dengan `n: 3, newLine: true` sehingga urutan tidak berpengaruh. Jika `newLine` null output memakai `stdout.write` + tab (sejajar), jika `true` memakai `writeln` (per baris).
- **ex8 — Parameter default:** `[int n = 3]` sudah menyediakan nilai bawaan, jadi tidak perlu pengecekan `null` — satu argumen otomatis mencetak 3 baris, dua argumen (`Flutter`, 5) mencetak 5 baris.
- **ex9 — Passing list:** list diteruskan sebagai objek dan dibaca isinya; fungsi `reverse` menyusun ulang dari indeks terakhir ke 0 sehingga `[1,2,3,4,5]` menjadi `[5,4,3,2,1]`. List asli tidak berubah (fungsi membuat list baru).
- **ex10 — Passing map:** `printMap` menerima `Map<String, int>` lalu `forEach` mencetak tiap pasangan key-value: `Durian: 24`, `Dendan: 5`, `Manggis: 3`.

### 3. Fungsi Lanjutan (ex11–ex16)

- **ex11 — Lambda:** fungsi anonim disimpan ke variabel `fungsiLambda` lalu dipanggil seperti variabel biasa; `add(34, 18)` menghasilkan `52.0` (karena parameternya `double`, literal int otomatis jadi double).
- **ex12 — Fungsi sebagai parameter:** `calc(a, b, operation)` menjalankan fungsi yang dikirimkan kepadanya. Satu fungsi `calc` bisa dipakai untuk empat operasi berbeda (+, *, /, %) hanya dengan mengganti argumen ketiga. Hasil: `15.0`, `36.0`, `4.0`, `0.0`.
- **ex13 — Callback:** prinsipnya sama dengan ex12, tetapi fungsi yang dikirim dideklarasikan sebagai fungsi bernama (`add`, `multiply`, `div`) — lebih rapi dan bisa dipakai ulang. Callback = fungsi yang dipanggil kembali oleh fungsi lain.
- **ex14 — Fungsi bersarang:** `square` didefinisikan **di dalam** `hypotenuse` sehingga hanya bisa dipakai di dalamnya. `hypotenuse(3,4)` = √(9+16) = `5.0` (teorema Pythagoras).
- **ex15 — Rekursi:** `factorial(n)` memanggil dirinya sendiri dengan `n-1` sampai mencapai basis `n == 0 → 1`. Hasil: `6! = 720`, `5! = 120`, `4! = 24`.
- **ex16 — List & Map lanjutan:** `add/addAll/insert/insertAll` menambah elemen, `remove/removeAt/removeLast/removeRange/removeWhere` menghapus, `contains` mengecek keberadaan, `sort((a,b) => b-a)` mengurutkan menurun, `every` mengecek seluruh elemen genap → `Semua Genap!`, `clear` mengosongkan list, `toSet()` menghapus duplikat, dan `map()` mengubah tiap elemen menjadi `'Angka 10'`, `'Angka 20'`, dst.

### 4. Eksepsi (ex17–ex23)

- **ex17 — throw:** `throw IntegerDivisionByZeroException()` **menghentikan program** karena tidak ada yang menangkapnya, sehingga muncul *Unhandled exception* beserta stacktrace-nya. Saat `b = 2` program berjalan normal: `10 ~/ 2 = 5`.
- **ex18 — throw Exception:** sama seperti ex17 tetapi memakai `Exception('pesan')`, pesan kesalahan lebih informatif dan muncul di pesan error.
- **ex19 — try-on:** `on IntegerDivisionByZeroException` hanya menangkap jenis eksepsi tersebut. Pada `b = 0` program **tidak crash**, eksepsi dan stacktrace dicetak rapi; pada `b = 2` hasil `5` tetap dicetak.
- **ex20 — try-catch umum:** `catch` menangkap **segala** jenis eksepsi. Input 5 → `Hari ke-5 adalah Kamis`; input 9 → terjadi `RangeError` (indeks 8 di luar rentang 0..6) dan dicetak `SALAH: tidak ada hari ke-9.`
- **ex21 — finally:** blok `finally` **selalu dijalankan** baik terjadi eksepsi maupun tidak. Uji `10, 0` menghasilkan pesan salah **+** `Bagian finalisasi`; uji `10, 2` menghasilkan `10 ~/ 2 = 5` **+** `Bagian finalisasi`.
- **ex22 — Multiple exception:** urutan blok `on` penting — yang paling spesifik di atas. Input bukan bilangan kena `FormatException`, pembagian nol kena `IntegerDivisionByZeroException`, sisanya kena `catch` generik; `finally` selalu mencetak `Selesai...`
- **ex23 — Eksepsi buatan pengguna:** `class NegativeError implements Exception` membuat tipe eksepsi sendiri. Input `-5` kena `on NegativeError` → `SALAH: anda memasukkan nilai negatif.`; input `abc` kena `FormatException`; input `7` → `Anda memasukkan nilai 7.`

---