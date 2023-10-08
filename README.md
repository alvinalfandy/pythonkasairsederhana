# pythonkasairsederhana
Script Python kasir sederhana, Jam Live, Daftar menu dan diskon, dan uang pembeli

## Cara Penggunaan

1. Jalankan program dan ikuti instruksi.
2. Pilih menu dengan memasukkan angka (1-5) atau ketik 'selesai' untuk mengakhiri pesanan.
3. Masukkan jumlah pesanan.
4. Total harga akan dihitung, dan jika total harga melebihi 100rb, akan diberikan diskon 20%.
5. Masukkan uang pelanggan.
6. Struk kasir akan ditampilkan dengan rincian pesanan, total harga, diskon (jika ada), uang pelanggan, dan kembalian.

## Catatan


Program ini dibuat dengan menggunakan Python dan dapat digunakan sebagai referensi tugas atau digunakan dalam kasir sehari-hari.


##Script
from datetime import datetime

# Rincian toko
toko_nama = "===== Chicken Geprek Alfandy ====="
toko_alamat = "BLOK A 2"
toko_nomor_telepon = "083814329508"

# Daftar menu
daftar_menu = [
    {"nama": "Ayam Geprek", "harga": 5000},
    {"nama": "Ayam Bakar", "harga": 5000},
    {"nama": "Paket Geprekdy Hemat 1", "harga": 10000},
    {"nama": "Paket Geprekdy Hemat 2", "harga": 20000},
    {"nama": "Minuman Air Putih", "harga": 2000}
]

# Tampilkan rincian toko
print("# Nama toko")
print(toko_nama)
print(toko_alamat)
print(toko_nomor_telepon)
print("=" * 29)

# Tampilkan daftar menu
print("Daftar Menu:")
for i, menu in enumerate(daftar_menu, start=1):
    print(f"{i}. {menu['nama']} ({menu['harga']} IDR)")

# Input pesanan
pesanan = {}
total_harga = 0

while True:
    pilihan = input("Pilih menu (1-5) atau ketik 'selesai' untuk mengakhiri pesanan: ")
    if pilihan.lower() == 'selesai':
        break
    elif not pilihan.isdigit() or int(pilihan) < 1 or int(pilihan) > len(daftar_menu):
        print("Pilihan tidak valid.")
    else:
        indeks_menu = int(pilihan) - 1
        menu_terpilih = daftar_menu[indeks_menu]
        jumlah = input(f"Jumlah {menu_terpilih['nama']} yang dipesan: ")
        while not jumlah.isdigit() or int(jumlah) <= 0:
            print("Jumlah tidak valid. Harap masukkan angka positif.")
            jumlah = input(f"Jumlah {menu_terpilih['nama']} yang dipesan: ")
        jumlah = int(jumlah)
        total_harga += menu_terpilih['harga'] * jumlah
        pesanan[menu_terpilih['nama']] = jumlah

# Diskon 20% jika total harga lebih dari 100rb
diskon = 0
if total_harga > 100000:
    diskon = 0.2 * total_harga

# Input uang dari pelanggan
uang_pelanggan = float(input("Input uang: "))

# Tampilkan struk
print("# Nama toko")
print(toko_nama)
print(toko_alamat)
print(toko_nomor_telepon)
print("=" * 29)
print("=" * 29)
print("Menu yang dipesan:")
for item, jumlah in pesanan.items():
    print(f"{item}: {jumlah}")
print("Total: ", total_harga)
if diskon > 0:
    print(f"Diskon: {diskon}")
print("Uang: ", uang_pelanggan)
print("Kembalian: ", uang_pelanggan - total_harga)
print("=" * 29)
print("Barang yang sudah dibeli tidak dapat dikembalikan")
print("=" * 29)
print(datetime.now().strftime("%d/%m/%Y %H:%M:%S"))








