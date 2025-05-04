def tampilkan_soal(nama_file):
    """
    Menampilkan soal dari file teks, meminta jawaban pengguna, dan memeriksa kebenarannya.

    Args:
        nama_file (str): Nama file teks berisi soal dengan format "pertanyaan || jawaban_benar".
    """
    try:
        with open(nama_file, 'r') as file_soal:
            print(f"nama file1: {nama_file}")
            for line in file_soal:
                parts = line.strip().split('||')
                if len(parts) == 2:
                    pertanyaan = parts[0].strip()
                    jawaban_benar = parts[1].strip()

                    print(pertanyaan)
                    jawaban_pengguna = input("Jawab: ").strip()

                    if jawaban_pengguna.lower() == jawaban_benar.lower():
                        print("Jawaban benar!")
                    else:
                        print(f"Jawaban salah! Seharusnya: {jawaban_benar}")
                else:
                    print(f"Format baris tidak sesuai: {line.strip()}")

    except FileNotFoundError:
        print(f"File '{nama_file}' tidak ditemukan.")
    except Exception as e:
        print(f"Terjadi kesalahan: {e}")

# Membuat contoh file soal.txt (untuk demonstrasi)
nama_file_soal = "soal.txt"
with open(nama_file_soal, 'w') as f:
    f.write("1+1 = || 2\n")
    f.write("Bendera Indonesia? || Merah Putih\n")
    f.write("Kota gudeg adalah: || Yogyakarta\n")
    f.write("Komponen PC untuk penyimpanan file adalah... || harddisk\n")
    f.write("50 * 20 = || 1000\n")

tampilkan_soal(nama_file_soal)
