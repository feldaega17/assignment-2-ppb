# Assignment 2 - My First App

Aplikasi Flutter sederhana yang mendemonstrasikan penggunaan **Row**, **Column**, **StatelessWidget**, **StatefulWidget**, serta berbagai widget dasar lainnya.

## Screenshot Struktur Aplikasi

Aplikasi terdiri dari 4 bagian utama yang tersusun secara vertikal dalam sebuah `Column`:

```
┌──────────────────────────────────┐
│           AppBar                 │  ← "My First App" (orange)
├──────────────────────────────────┤
│                                  │
│     ┌──────────────────┐         │
│     │                  │         │
│     │   Image.network  │         │  ← Gambar random (lightBlue)
│     │  (picsum.photos) │         │
│     │                  │         │
│     └──────────────────┘         │
│                                  │
│  ┌─────────────────────────┐     │
│  │ What image is that      │     │  ← Teks pertanyaan (pink)
│  └─────────────────────────┘     │
│                                  │
│  ┌─────────────────────────┐     │
│  │  Food  Scenery  People  │     │  ← Kategori icon (yellow)
│  └─────────────────────────┘     │
│                                  │
│  ┌─────────────────────────┐     │
│  │ Counter here: 0     [+] │     │  ← Counter interaktif (cyan)
│  └─────────────────────────┘     │
│                                  │
└──────────────────────────────────┘
```

## Widget Tree

Diagram widget tree lengkap tersedia di file [`widget_tree.puml`](widget_tree.puml).

## Penjelasan Widget

### 1. MyApp (StatelessWidget)
Widget root aplikasi. Membungkus seluruh aplikasi dalam `MaterialApp` dengan konfigurasi:
- **Theme**: Material 3 dengan seed color `deepPurple`
- **Home**: Mengarah ke `RowColumnPage`

### 2. RowColumnPage (StatelessWidget)
Halaman utama aplikasi yang menggunakan `Scaffold` sebagai struktur dasar. Terdiri dari:

#### a. AppBar
- Judul **"My First App"** dengan teks berwarna hitam
- Background warna `orange[200]`
- Judul diposisikan di tengah (`centerTitle: true`)

#### b. Body - Column (Konten Utama)
Seluruh konten body disusun secara vertikal menggunakan `Column` dengan alignment center. Berisi 4 section:

**Section 1 - Image (Gambar Random)**
| Widget | Fungsi |
|--------|--------|
| `Container` | Wrapper luar |
| `AspectRatio` (1:1) | Menjaga rasio gambar tetap persegi |
| `Container` (lightBlue) | Background biru muda dengan margin dan padding |
| `Center` | Menempatkan gambar di tengah |
| `Image.network` | Menampilkan gambar random dari `picsum.photos/200` |

**Section 2 - Text (Pertanyaan)**
| Widget | Fungsi |
|--------|--------|
| `Container` (pink) | Background pink dengan margin dan padding |
| `Text` | Menampilkan teks **"What image is that"** (fontSize: 16) |

**Section 3 - Category Row (Kategori)**
| Widget | Fungsi |
|--------|--------|
| `Container` (yellow) | Background kuning dengan margin dan padding |
| `Row` (spaceEvenly) | Menyusun 3 kategori secara horizontal dengan jarak merata |
| `Column` x3 | Masing-masing berisi `Icon` + `Text` untuk: **Food**, **Scenery**, **People** |

Menggunakan icon bawaan Material:
- `Icons.food_bank` - Kategori makanan
- `Icons.landscape` - Kategori pemandangan
- `Icons.people` - Kategori orang

### 3. CounterCard (StatefulWidget)
Widget interaktif yang mendemonstrasikan **state management** sederhana di Flutter.

| Widget | Fungsi |
|--------|--------|
| `Container` (cyan) | Background cyan dengan margin dan padding |
| `Row` (spaceBetween) | Menyusun teks counter dan tombol di ujung kiri-kanan |
| `Text` | Menampilkan **"Counter here: $_counter"** yang berubah secara dinamis |
| `IconButton` | Tombol `+` yang memanggil `_incrementCounter()` |

**Cara Kerja State:**
- Variabel `_counter` (int) menyimpan nilai counter, dimulai dari `0`
- Saat tombol `+` ditekan, method `_incrementCounter()` dipanggil
- Di dalam method tersebut, `setState()` dipanggil untuk mengupdate `_counter++`
- `setState()` memberi tahu Flutter untuk me-rebuild widget ini sehingga UI menampilkan nilai terbaru

```dart
void _incrementCounter() {
  setState(() {
    _counter++; // Update state, trigger rebuild
  });
}
```

## Konsep Flutter yang Digunakan

| Konsep | Penjelasan |
|--------|-----------|
| **StatelessWidget** | Widget yang tidak memiliki state internal (MyApp, RowColumnPage) |
| **StatefulWidget** | Widget yang memiliki state yang bisa berubah (CounterCard) |
| **Column** | Layout widget untuk menyusun children secara vertikal |
| **Row** | Layout widget untuk menyusun children secara horizontal |
| **Container** | Widget serbaguna untuk styling (warna, margin, padding) |
| **AspectRatio** | Memaksa child memiliki rasio lebar:tinggi tertentu |
| **MediaQuery** | Mengambil informasi ukuran layar perangkat |
| **setState()** | Method untuk mengupdate state dan trigger rebuild UI |

## Cara Menjalankan

```bash
flutter pub get
flutter run
```
