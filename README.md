# PROJECT-SISTEMOPERASI-DIVAMKLLG
Project Based Learing 1
# LANGKAH 1 BUAT STRUKTUR DIREKTORI
# Berikut contoh Membuat Project_1:
#(Deskripsi gambar)
# (https://github.com/divamkallg-alt/diva/edit/main/README.md)
```
#ubuntu@divamakalalag :mkdir project_1
```

# Perintah Berpindah Direktori ke Project_1 dan Membuat folder documents, image, archives, logs
#(Deskripsi gambar")
# (https://github.com/divamkallg-alt/diva/edit/main/README.md)
```
#cd project_1
```
```
#mkdir documents images archivers logs
```
# Perintah membuat 20 file:
#(Deskripsi gambar")
# (https://github.com/divamkallg-alt/diva/edit/main/README.md)
```
#touch file{1...10}.txt file{11...15}.jpg file{16...18};pdf file{19...20}.log
```
# Perintah Memasukkan sebuah teks ke masing-masing file yang berbeda:
#(Deskripsi gambar")
# (https://github.com/divamkallg-alt/diva/edit/main/README.md)
```
echo "Ini adalah dokumen contoh" > file1.txt
```
```
echo "Data gambar" >> file11.jpg
```
```
echo "Log sistem contoh" >> file20.log
```
Penjelasan:
- `mkdir` membuat folder baru.
- `touch` membuat file kosong 
- `echo` menulis tekx ke dalam file
# LANGKAH 2 SCRIPT ORGANISASI FILE
# Buat Script Organisasi File Di dalam direktori:
```
nano operasi_file.sh
```
#ISI SCRIPT
#(Deskripsi gambar")
# (https://github.com/divamkallg-alt/diva/edit/main/README.md)
```
#!/bin/bash
#Script untuk mengorganisasi file berdasarkan eksitensi

#Pastikan berada di direktori proyek
cd ~/project_1

#Pindahkan file sesuai ekstensi
find . -maxdepth 1 -type f -name "*.txt" -exec mv {} documents/ \;
find . -maxdepth 1 -type f -name "*.jpg" -exec mv {} images/ \;
find . -maxdepth 1 -type f -name "*.pdf" -exec mv {} archives/ \;
find . -maxdepth 1 -type f -name "*.log" -exec mv {} logs/ \;

#Konfirmasi hasil
echo "file berhasil dipindahkan ke folder sesuai ekstensi!"
ls documents images archives logs
```
# Beri Hak Eksekusi
```
chmod +x operasi_file.sh
```
# Eksekusi file yang sudah dibuat
```
./operasi_file.sh
```
Penjelasan:
- `find . -maxdepth 1 -type f -name "*.ext` mencari file berdasarkan eksternal di direktori saat ini
- `-exec mv {}folder/ \;` memindahkan file hasil pencarian ke folder sesuai
- `chmod +x` memberi izin eksekusi
# LANGKAH 3 FUNGSI PENCARIAN
# buat file search_file.sh
(deskripsi gambar)

```
#!/bin/bash
#Script: search_file.sh
#Fungsi: Mencari file berdasarkan nama, ukuran, atau konten

cd ~/project_1

echo "=== PENCARIAN FILE ==="
echo "1. Cari berdasarkan nama"
echo "2. Cari berdasarkan ukuran"
echo "3. Cari berdasarkan isi konten"
read -p "Pilih opsi (1/2/3): " opsi

case $opsi in
1)
    read -p "Masukkan nama atau pola file (contoh: *.txt): " nama
    echo "Hasil pencarian:"
    find . -type f -name "$nama"
    ;;
2)
    read -p "Masukkan batas ukuran (contoh: +1M untuk lebih dari 1MB, -500k untuk dari 500KB): " ukuran
    echo "Hasil pencarian:"
    find . -type f -size "$ukuran"
    ;;
3)
    read -p "Masukkan kata kunci yang ingin dicari dalam file: " keyword
    echo "Hasil pencarian:"
    grep -r "$keyword" .
    ;;
*)
    echo "Opsi tidak valid."
    ;;
esac
```
# hak eksekusi
```
chmod +x search_file.sh
```
# eksekusi file yang telah dibuat
```
./search_file.sh
```
Penjelasan:
- `find . -type f -name "$nama"` mencari file dengan pola nama tertentu
- `find .-size + 1m` mencari file berukuran lebih dari 1MB
- `grep -r "teks"`mencari teks didalam isi file secara rekursif
# lahkah 4 - generator laporan file sistem
# buat file report.sh
```
nano report.sh
```
(deskripsi gambar)
```
#!/bin/bash
#Script: generate_report.sh
#Fungsi: Membuat laporan statistik file sistem

cd ~/project_1

echo "=== LAPORAN FILE SISTEM ==" > report.txt
echo "Tanggal: $(date)" >> report.txt
echo "" >> report.txt

echo "--- Jumlah File dan Folder ---" >> report.txt
ls -lR | wc -l >> report.txt
echo "" >> report.txt

echo "--- Ukuran Total Folder ---" >> report.txt
du -sh . >> report.txt
echo "" >> report.txt

echo "--- Statistik Berdasarkan Ekstensi ---" >> report.txt
echo "TXT: $(find . -type f -name '*.txt' | wc -l)" >> report.txt
echo "JPG: $(find . -type f -name '*.jpg' | wc -l)" >> report.txt
echo "PDF: $(find . -type f -name '*.pdf' | wc -l)" >> report.txt
echo "LOG: $(find . -type f -name '*.log' | wc -l)" >> report.txt

echo "" >> report.txt
echo "=== Selesai! Laporan disimpan di report.txt ==="
```
# bwri hak akses eksekusi 
```
chmod +x report.sh
```
# eksekusi file yang telah dibuat
```
./report.sh
```
Penjelasan:
- `find . -type f -name "$nama"` mencari file dengan pola nama tertentu
- `find .-size + 1m` mencari file berukuran lebih dari 1MB
- `grep -r "teks"`mencari teks didalam isi file secara rekursif
