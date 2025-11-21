# hello-rust

Koleksi kecil contoh dan eksperimen Rust — setiap file di folder `bin/` adalah contoh/mini-program terpisah yang menunjukkan konsep Rust (ownership, borrowing, concurrency, generics, trait, dsb.). Projek ini menggunakan `tokio` untuk beberapa contoh async.

## Struktur proyek

- `Cargo.toml` — manifest Cargo (menggunakan crate `tokio` dengan fitur `full`).
- `bin/` — banyak file `.rs`, masing-masing adalah binary/example terpisah (mis. `hello.rs`, `async.rs`, `async_mutex.rs`, `thread.rs`, `ownership.rs`, `borrow.rs`, dsb.).
- `target/` — keluaran build (diabaikan oleh `.gitignore`).

> Catatan: contoh disusun sebagai binary independen. Nama binary sama dengan nama file tanpa ekstensi.

## Prasyarat

- Rust toolchain (rustc + cargo). Pasang via https://rustup.rs jika belum terpasang.
- Pada saat pembuatan proyek ini, `tokio` ada sebagai dependency (lihat `Cargo.toml`). Cargo akan mengunduh dependency saat build pertama.

## Cara build dan menjalankan

Buka PowerShell (pwsh) pada Windows di root proyek lalu:

- Build seluruh proyek (debug):

```powershell
cargo build
```

- Jalankan satu binary/contoh (debug):

```powershell
# ganti <name> dengan nama file tanpa .rs, mis. hello, async_mutex, thread
cargo run --bin <name>
```

Contoh menjalankan `hello.rs` atau `async_mutex.rs`:

```powershell
cargo run --bin hello
cargo run --bin async_mutex
```

- Build dan jalankan release (optimasi):

```powershell
cargo build --release
# executable akan berada di target\release\<name>.exe
.
```

## Contoh-contoh yang sering dicoba

Berikut beberapa file di `bin/` yang menarik untuk dicoba:

- `hello.rs` — program "hello world" sederhana.
- `async.rs` dan `async_mutex.rs` — contoh menggunakan `tokio` dan async/await.
- `thread.rs`, `scoped_thread.rs` — contoh concurrency berbasis thread.
- `ownership.rs`, `borrow.rs`, `borrow_slice.rs`, `borrow_string_str.rs` — konsep ownership dan borrowing.
- `generic_trait.rs`, `generic_func.rs`, `generic_lifetime.rs` — contoh generik dan lifetime.
- `channel.rs`, `mutex.rs`, `rc.rs`, `arc.rs` — primitive sinkronisasi dan smart pointers.

Lihat file-file di `bin/` untuk deskripsi lebih rinci di setiap contoh.

## Menambahkan contoh baru

Tambahkan file `.rs` baru ke folder `bin/` (mis. `bin/my_example.rs`). Nama file akan menjadi nama binary. Setelah itu jalankan:

```powershell
cargo run --bin my_example
```

Jika Cargo tidak menemukan binary baru, pastikan struktur file dan nama file benar. Jika perlu, tambahkan entry `[[bin]]` di `Cargo.toml` untuk konfigurasi khusus.

## Catatan

- Proyek ini dibuat untuk belajar — tidak ada tests/unit otomatik bawaan.
- Target build berada di folder `target/` dan diabaikan oleh `.gitignore`.