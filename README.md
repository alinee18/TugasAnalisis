# Tugas Analisis 1 – OOP Python (Class Hero)

## Soal
Apa yang terjadi jika kamu mengubah `hero1.hp` menjadi 500 setelah baris  
`hero1 = Hero(...)` lalu menjalankan `print(hero1.hp)`?
## Jawaban
Jika `hero1.hp` diubah menjadi `500` setelah object dibuat, maka nilai HP milik `hero1` akan berubah dari `100` menjadi `500`.  
Saat `print(hero1.hp)` dijalankan, yang tampil adalah `500` karena atribut `hp` pada object `hero1` sudah diperbarui setelah object dibuat

## Tugas Analisis 2

### Soal
Mengapa parameter `lawan` pada method `serang` harus berupa objek utuh, bukan hanya string nama?
### Jawaban
Parameter `lawan` harus berupa objek Hero agar method `serang` bisa mengakses data dan method milik lawan, seperti `lawan.name` dan `lawan.diserang()`.  
Jika `lawan` hanya berupa string, maka kita tidak bisa mengurangi HP lawan atau memanggil method `diserang()`.  
Dengan menerima objek utuh, Hero bisa benar-benar berinteraksi satu sama lain.

## Tugas Analisis 3 – Inheritance & super()

### Soal
Apa yang terjadi jika baris `super().__init__(name, hp, attack_power)` dihapus dari class Mage?
### Hasil Eksperimen
Saat baris `super().__init__()` dihapus dan program dijalankan, muncul error:
### Penjelasan
Error tersebut muncul karena atribut `name`, `hp`, dan `attack_power` dibuat di constructor class Hero.  
Jika `super().__init__()` tidak dipanggil di class Mage, maka constructor Hero tidak dijalankan, sehingga atribut-atribut tersebut tidak pernah dibuat.

Akibatnya, saat `eudora.info()` mencoba mengakses `self.name`, Python tidak menemukannya dan menampilkan error.

### Peran Fungsi `super()`
Fungsi `super()` digunakan untuk memanggil constructor milik class induk (Hero) dari dalam class anak (Mage).  
Dengan `super().__init__(name, hp, attack_power)`, data dari Hero diturunkan ke Mage, sehingga Mage memiliki atribut `name`, `hp`, dan `attack_power`, serta atribut tambahan miliknya sendiri seperti `mana`.
### Kesimpulan
`super()` sangat penting agar class anak tetap terhubung dengan data dan perilaku dari class induknya.
Tanpa `super()`, atribut dari class induk tidak akan dimiliki oleh class anak.


## Tugas Analisis 4 – Enkapsulasi (Getter & Setter)

### 1. Percobaan Hacking

#### Kode:
```python
print(f"Mencoba akses paksa: {hero1._Hero__hp}")

## Tugas Analisis 5 – Interface / Abstract Class

### 1. Melanggar Kontrak

Jika method `serang()` di class Hero dihapus, lalu program dijalankan, muncul error:


#### Penjelasan:
Error ini berarti kita tidak boleh membuat object dari class Hero karena Hero adalah class abstrak dan masih memiliki method abstrak yang belum diimplementasikan.

Interface / abstract class bertindak sebagai kontrak.  
Jika kontrak tersebut dilanggar (method tidak dibuat), maka program akan error.

#### Konsekuensi jika lupa membuat method dari Interface:
- Object tidak bisa dibuat
- Program tidak bisa berjalan
- Fitur penting dalam game tidak ada

---

### 2. Mencetak Cetakan (GameUnit)

Saat kode:
```python
unit = GameUnit()


## Tugas Analisis 6 – Polymorphism

### 1. Uji Skalabilitas (Menambah Class Healer)

Saya menambahkan class baru:

```python
class Healer(Hero):
    def serang(self):
        print(f"{self.nama} tidak menyerang, tapi menyembuhkan teman!")
