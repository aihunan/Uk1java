// Kelas Induk Pertama
class Kendaraan {
    private String nama;
    private int jumlahRoda;

    // Constructor Overloading
    public Kendaraan() {
        this.nama = "Tidak diketahui";
        this.jumlahRoda = 0;
    }

    public Kendaraan(String nama, int jumlahRoda) {
        this.nama = nama;
        this.jumlahRoda = jumlahRoda;
    }

    // Getter dan Setter (Encapsulation)
    public String getNama() {
        return nama;
    }

    public void setNama(String nama) {
        this.nama = nama;
    }

    public int getJumlahRoda() {
        return jumlahRoda;
    }

    public void setJumlahRoda(int jumlahRoda) {
        this.jumlahRoda = jumlahRoda;
    }

    // Method untuk Polimorfisme (akan di-override oleh kelas anak)
    public void berjalan() {
        System.out.println(nama + " berjalan dengan " + jumlahRoda + " roda.");
    }
}

// Kelas Induk Kedua
class Mesin {
    private String jenisMesin;

    public Mesin() {
        this.jenisMesin = "Tidak diketahui";
    }

    public Mesin(String jenisMesin) {
        this.jenisMesin = jenisMesin;
    }

    public String getJenisMesin() {
        return jenisMesin;
    }

    public void setJenisMesin(String jenisMesin) {
        this.jenisMesin = jenisMesin;
    }

    public void nyalakanMesin() {
        System.out.println("Mesin " + jenisMesin + " dinyalakan.");
    }
}

// Kelas Anak Pertama yang menginduk ke Kendaraan
class Mobil extends Kendaraan {
    private int jumlahPintu;

    // Constructor Overloading
    public Mobil() {
        super();
        this.jumlahPintu = 0;
    }

    public Mobil(String nama, int jumlahRoda, int jumlahPintu) {
        super(nama, jumlahRoda); // Memanggil constructor dari kelas induk
        this.jumlahPintu = jumlahPintu;
    }

    // Getter dan Setter untuk jumlahPintu
    public int getJumlahPintu() {
        return jumlahPintu;
    }

    public void setJumlahPintu(int jumlahPintu) {
        this.jumlahPintu = jumlahPintu;
    }

    // Method Overriding (Polimorfisme)
    @Override
    public void berjalan() {
        System.out.println(getNama() + " berjalan dengan " + getJumlahRoda() + " roda dan memiliki " + jumlahPintu + " pintu.");
    }
}

// Kelas Anak Kedua yang menginduk ke Kendaraan
class Motor extends Kendaraan {
    private boolean memilikiKopling;

    // Constructor Overloading
    public Motor() {
        super();
        this.memilikiKopling = false;
    }

    public Motor(String nama, int jumlahRoda, boolean memilikiKopling) {
        super(nama, jumlahRoda);
        this.memilikiKopling = memilikiKopling;
    }

    // Getter dan Setter untuk memilikiKopling
    public boolean isMemilikiKopling() {
        return memilikiKopling;
    }

    public void setMemilikiKopling(boolean memilikiKopling) {
        this.memilikiKopling = memilikiKopling;
    }

    // Method Overriding (Polimorfisme)
    @Override
    public void berjalan() {
        String koplingStatus = memilikiKopling ? "dengan kopling" : "tanpa kopling";
        System.out.println(getNama() + " berjalan dengan " + getJumlahRoda() + " roda dan " + koplingStatus + ".");
    }
}

// Kelas Anak Ketiga yang menginduk ke Kendaraan dan Mesin
class Truk extends Kendaraan {
    private int kapasitasMuatan;

    public Truk() {
        super();
        this.kapasitasMuatan = 0;
    }

    public Truk(String nama, int jumlahRoda, int kapasitasMuatan) {
        super(nama, jumlahRoda);
        this.kapasitasMuatan = kapasitasMuatan;
    }

    // Getter dan Setter untuk kapasitasMuatan
    public int getKapasitasMuatan() {
        return kapasitasMuatan;
    }

    public void setKapasitasMuatan(int kapasitasMuatan) {
        this.kapasitasMuatan = kapasitasMuatan;
    }

    // Method Overriding (Polimorfisme)
    @Override
    public void berjalan() {
        System.out.println(getNama() + " berjalan dengan " + getJumlahRoda() + " roda dan membawa muatan sebesar " + kapasitasMuatan + " ton.");
    }
}

// Kelas Main
public class Main {
    public static void main(String[] args) {
        // Pembuatan objek dari kelas anak
        Mobil mobil = new Mobil("Sedan", 4, 4);
        Motor motor = new Motor("Sepeda Motor", 2, true);
        Truk truk = new Truk("Truk Kontainer", 6, 20);

        // Menampilkan informasi dan menjalankan metode
        mobil.berjalan();   // Overriding
        motor.berjalan();   // Overriding
        truk.berjalan();    // Overriding

        // Menggunakan setter untuk mengubah nilai atribut
        mobil.setNama("SUV");
        mobil.setJumlahPintu(5);
        mobil.berjalan();   // Menampilkan hasil setelah perubahan

        // Menggunakan metode getter
        System.out.println("Nama kendaraan: " + motor.getNama());
        System.out.println("Jumlah roda: " + motor.getJumlahRoda());
        System.out.println("Apakah memiliki kopling: " + motor.isMemilikiKopling());
    }
}
