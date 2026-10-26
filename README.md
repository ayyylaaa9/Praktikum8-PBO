# Tugas Praktikum 8: Polymorphism, Abstract Class, dan Interface

**Noer Afdila (L0325033)**

# Source Code dan Penjelasan

## 1. Class Hewan

### Source Code

```java
public class Hewan {
    public void bersuara() {
        System.out.println("Hewan ini mengeluarkan suara yang tidak spesifik.");
    }
}
```

### Penjelasan

Class `Hewan` digunakan untuk merepresentasikan hewan secara umum dalam program. Class ini menjadi superclass atau kelas induk yang nantinya diwariskan kepada class `Kucing` dan `Anjing`.
Pada class ini terdapat method `bersuara()` yang digunakan untuk menampilkan suara umum dari hewan.
Method tersebut memiliki fungsi sebagai berikut:
- `public` menunjukkan bahwa method dapat diakses dari class lain.
- `void` menunjukkan bahwa method tidak mengembalikan nilai.
- `bersuara()` merupakan nama method yang digunakan untuk menampilkan suara hewan.
- `System.out.println()` digunakan untuk menampilkan teks ke console.
Method `bersuara()` nantinya akan di-override oleh subclass sehingga setiap jenis hewan dapat memiliki perilaku yang berbeda meskipun menggunakan nama method yang sama.

## 2. Class Kucing

### Source Code

```java
public class Kucing extends Hewan {
    @Override
    public void bersuara() {
        System.out.println("Kucing: Meow meow!");
    }
}
```

### Penjelasan

Class `Kucing` digunakan untuk merepresentasikan hewan kucing. Class ini merupakan subclass dari class `Hewan`, sehingga dapat mewarisi method yang dimiliki oleh kelas induknya.
Pada class ini terdapat beberapa bagian penting, yaitu:
- `extends Hewan` digunakan untuk menunjukkan bahwa class `Kucing` mewarisi class `Hewan`.
- `@Override` digunakan untuk menandai bahwa method `bersuara()` merupakan method yang didefinisikan ulang dari superclass.
- `public void bersuara()` merupakan method yang digunakan untuk menampilkan suara kucing.
- `System.out.println("Kucing: Meow meow!")` digunakan untuk menampilkan suara khas kucing.
Method `bersuara()` memiliki nama dan parameter yang sama dengan method pada class `Hewan`, tetapi isi implementasinya berbeda. Hal ini disebut **method overriding**, yaitu proses mendefinisikan ulang method dari kelas induk pada kelas turunannya.

## 3. Class Anjing

### Source Code

```java
public class Anjing extends Hewan {
    @Override
    public void bersuara() {
        System.out.println("Anjing: Guk guk!");
    }
}
```

### Penjelasan

Class `Anjing` digunakan untuk merepresentasikan hewan anjing dalam program. Class ini merupakan subclass dari class `Hewan`, sehingga mewarisi struktur dan perilaku dari kelas induknya.
Pada class ini terdapat beberapa bagian penting, yaitu:
- `extends Hewan` menunjukkan bahwa class `Anjing` merupakan turunan dari class `Hewan`.
- `@Override` menandakan bahwa method `bersuara()` menggantikan implementasi method dari superclass.
- `public void bersuara()` digunakan untuk mendefinisikan perilaku suara anjing.
- `System.out.println("Anjing: Guk guk!")` digunakan untuk menampilkan suara khas anjing.
Meskipun class `Kucing` dan `Anjing` memiliki method dengan nama yang sama, keduanya menghasilkan output berbeda. Hal ini menunjukkan penerapan polymorphism melalui method overriding.

## 4. Class PoliTester

### Source Code

```java
public class PoliTester {
    public static void main(String[] args) {
        Hewan[] daftarHewan = new Hewan[3];
        daftarHewan[0] = new Hewan();
        daftarHewan[1] = new Kucing();
        daftarHewan[2] = new Anjing();

        for (Hewan h : daftarHewan) {
            h.bersuara();
        }
    }
}
```

### Penjelasan

Class `PoliTester` digunakan untuk menguji penerapan polymorphism pada tingkat runtime. Class ini memiliki method `main()` yang menjadi titik awal eksekusi program Java.
Pada class ini terdapat beberapa bagian penting, yaitu:
- `public static void main(String[] args)` merupakan method utama yang dijalankan ketika program dimulai.
- `Hewan[] daftarHewan = new Hewan[3]` digunakan untuk membuat array bertipe `Hewan` yang dapat menampung tiga objek.
- `daftarHewan[0] = new Hewan()` digunakan untuk membuat objek dari class `Hewan`.
- `daftarHewan[1] = new Kucing()` digunakan untuk memasukkan objek `Kucing` ke dalam array bertipe `Hewan`.
- `daftarHewan[2] = new Anjing()` digunakan untuk memasukkan objek `Anjing` ke dalam array bertipe `Hewan`.
Penyimpanan objek subclass ke dalam referensi superclass disebut *upcasting*. Selanjutnya, program menggunakan perulangan `for-each` untuk mengakses setiap objek di dalam array.
Pada bagian `h.bersuara()`, program memanggil method yang sama untuk setiap objek. Java kemudian menentukan implementasi method berdasarkan jenis objek yang sebenarnya. Proses ini disebut *dynamic binding* dan merupakan bentuk runtime polymorphism.

### Hasil Output

```text
Hewan ini mengeluarkan suara yang tidak spesifik.
Kucing: Meow meow!
Anjing: Guk guk!
```

Output tersebut menunjukkan bahwa method `bersuara()` dapat menghasilkan perilaku berbeda bergantung pada objek yang memanggilnya.

## 5. Class BangunDatar

### Source Code

```java
public abstract class BangunDatar {
    String warna;

    public BangunDatar(String warna) {
        this.warna = warna;
    }

    public abstract double hitungLuas();

    public void cetakWarna() {
        System.out.println("Warna bangun ini adalah: " + warna);
    }
}
```

### Penjelasan

Class `BangunDatar` merupakan abstract class yang digunakan sebagai kerangka dasar untuk kelas bangun datar lainnya. Class ini tidak dapat dibuat objeknya secara langsung karena dideklarasikan menggunakan kata kunci `abstract`.
Pada class ini terdapat beberapa atribut dan method, yaitu:
- `String warna` digunakan untuk menyimpan informasi warna bangun datar.
- `public BangunDatar(String warna)` merupakan constructor yang digunakan untuk memberikan nilai awal pada atribut warna.
- `this.warna = warna` digunakan untuk menyimpan nilai parameter ke dalam atribut milik objek.
- `public abstract double hitungLuas()` merupakan abstract method yang tidak memiliki implementasi dan harus di-override oleh subclass konkret.
- `public void cetakWarna()` merupakan concrete method yang digunakan untuk menampilkan warna bangun datar.
Abstract class memungkinkan programmer menentukan struktur dasar suatu objek tanpa harus memberikan implementasi untuk seluruh perilakunya. Pada class `BangunDatar`, perhitungan luas diserahkan kepada subclass karena setiap bangun datar memiliki rumus luas yang berbeda.
Sementara itu, method `cetakWarna()` sudah memiliki implementasi sehingga dapat digunakan oleh subclass yang mewarisinya.

## 6. Class Lingkaran

### Source Code

```java
public class Lingkaran extends BangunDatar {
    private double jariJari;

    public Lingkaran(String warna, double jariJari) {
        super(warna);
        this.jariJari = jariJari;
    }

    @Override
    public double hitungLuas() {
        return Math.PI * jariJari * jariJari;
    }
}
```

### Penjelasan

Class `Lingkaran` merupakan subclass dari abstract class `BangunDatar`. Class ini digunakan untuk merepresentasikan lingkaran yang memiliki warna dan ukuran jari-jari.
Pada class ini terdapat beberapa bagian penting, yaitu:
- `private double jariJari` merupakan atribut untuk menyimpan ukuran jari-jari lingkaran.
- `public Lingkaran(String warna, double jariJari)` merupakan constructor yang digunakan untuk memberikan nilai awal pada objek lingkaran.
- `super(warna)` digunakan untuk memanggil constructor superclass `BangunDatar` agar atribut warna dapat diinisialisasi.
- `this.jariJari = jariJari` digunakan untuk menyimpan nilai jari-jari ke dalam atribut objek.
- `@Override` menandakan bahwa method `hitungLuas()` mengimplementasikan abstract method dari superclass.
- `Math.PI` digunakan untuk memperoleh nilai konstanta pi dalam perhitungan luas lingkaran.
- `return Math.PI * jariJari * jariJari` digunakan untuk menghitung dan mengembalikan luas lingkaran.
Rumus luas lingkaran yang digunakan adalah:
**Luas = π × r × r**
Class `Lingkaran` harus mengimplementasikan method `hitungLuas()` karena mewarisi abstract method dari class `BangunDatar`. Jika method tersebut tidak diimplementasikan, class `Lingkaran` harus dideklarasikan sebagai abstract class juga.

## 7. Interface AlatElektronik

### Source Code

```java
public interface AlatElektronik {
    void nyalakan();
    void matikan();
}
```

### Penjelasan

Interface `AlatElektronik` digunakan untuk mendefinisikan kontrak perilaku yang harus dimiliki oleh perangkat elektronik. Interface ini memiliki dua method, yaitu `nyalakan()` dan `matikan()`.
Pada interface ini terdapat beberapa bagian penting, yaitu:
- `public interface AlatElektronik` digunakan untuk mendeklarasikan interface dengan nama `AlatElektronik`.
- `void nyalakan()` merupakan deklarasi method untuk menyalakan perangkat elektronik.
- `void matikan()` merupakan deklarasi method untuk mematikan perangkat elektronik.

Kedua method tersebut tidak memiliki badan implementasi. Class yang mengimplementasikan interface ini harus menyediakan isi dari kedua method tersebut.
Interface membantu memisahkan definisi perilaku dengan implementasinya. Dengan demikian, berbagai jenis perangkat elektronik dapat menggunakan kontrak yang sama meskipun cara kerja masing-masing perangkat berbeda.

## 8. Interface Kamera

### Source Code

```java
public interface Kamera {
    void ambilFoto();
}
```

### Penjelasan

Interface `Kamera` digunakan untuk mendefinisikan perilaku pengambilan foto pada perangkat yang memiliki fitur kamera.
Pada interface ini terdapat method `ambilFoto()` yang berfungsi sebagai deklarasi perilaku untuk mengambil foto. Method tersebut belum memiliki implementasi sehingga class yang mengimplementasikan interface `Kamera` harus menyediakan isi method-nya.
Interface `Kamera` nantinya digunakan bersama interface `AlatElektronik` pada class `Smartphone`. Hal ini menunjukkan bahwa satu class dalam Java dapat mengimplementasikan lebih dari satu interface.

## 9. Class Smartphone

### Source Code

```java
public class Smartphone implements AlatElektronik, Kamera {
    private String merk;

    public Smartphone(String merk) {
        this.merk = merk;
    }

    @Override
    public void nyalakan() {
        System.out.println(merk + " menyala. Booting OS...");
    }

    @Override
    public void matikan() {
        System.out.println(merk + " dimatikan. Goodbye.");
    }

    @Override
    public void ambilFoto() {
        System.out.println("Cekrek! Foto berhasil disimpan di galeri " + merk + ".");
    }
}
```

### Penjelasan

Class `Smartphone` digunakan untuk merepresentasikan perangkat smartphone yang memiliki kemampuan sebagai alat elektronik sekaligus perangkat kamera. Class ini mengimplementasikan dua interface, yaitu `AlatElektronik` dan `Kamera`.
Pada class ini terdapat beberapa atribut dan method, yaitu:
- `private String merk` digunakan untuk menyimpan merek smartphone.
- `public Smartphone(String merk)` merupakan constructor yang digunakan untuk memberikan nilai awal pada atribut merek.
- `this.merk = merk` digunakan untuk menyimpan nilai parameter ke dalam atribut objek.
- `nyalakan()` merupakan implementasi method dari interface `AlatElektronik` untuk menyalakan smartphone.
- `matikan()` merupakan implementasi method dari interface `AlatElektronik` untuk mematikan smartphone.
- `ambilFoto()` merupakan implementasi method dari interface `Kamera` untuk menjalankan perilaku pengambilan foto.

Kata kunci `implements` menunjukkan bahwa class `Smartphone` harus menyediakan implementasi untuk seluruh method abstrak dari kedua interface tersebut.
Method `nyalakan()` menampilkan pesan bahwa smartphone menyala dan melakukan proses booting sistem operasi. Method `matikan()` menampilkan pesan bahwa smartphone telah dimatikan. Sementara itu, method `ambilFoto()` menampilkan pesan bahwa foto berhasil disimpan ke galeri smartphone.
Penerapan dua interface sekaligus disebut *multiple interface implementation*. Konsep ini memungkinkan sebuah class memiliki beberapa kelompok perilaku tanpa harus mewarisi lebih dari satu class induk.

# Kesimpulan

Berdasarkan praktikum Modul 8 Pemrograman Berorientasi Objek, dapat dipahami bahwa polymorphism, abstract class, dan interface merupakan konsep penting dalam pemrograman berorientasi objek.
Polymorphism diterapkan melalui method overriding pada class `Hewan`, `Kucing`, dan `Anjing`. Konsep ini memungkinkan pemanggilan method yang sama menghasilkan perilaku berbeda sesuai dengan jenis objeknya.
Abstract class diterapkan melalui class `BangunDatar` yang menyediakan kerangka dasar bagi bangun datar. Class `Lingkaran` kemudian mewarisi kerangka tersebut dan mengimplementasikan perhitungan luas sesuai dengan rumus lingkaran.
Interface diterapkan melalui `AlatElektronik` dan `Kamera`, yang diimplementasikan secara bersamaan oleh class `Smartphone`. Konsep ini memungkinkan sebuah class memiliki beberapa perilaku yang ditentukan melalui kontrak interface.
