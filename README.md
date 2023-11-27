# Praktikum_PemWeb7

### Pertanyaan dan Tugas

Buatlah program PHP sederhana dengan menggunakan form input yang menampilkan nama, tanggal lahir dan pekerjaan. Kemudian tampilkan outputnya dengan menghitung umur berdasarkan inputan tanggal lahir. Dan pilihan pekerjaan dengan gaji yang berbeda-beda sesuai pilihan pekerjaan.

#### Kode PHP Sederhana Form Input
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Form Input</title>
</head>
<body>
    <h2>Form Input</h2>
    <form method="post">
        <label>Nama: </label>
        <input type="text" name="nama" required><br>

        <label>Tanggal Lahir: </label>
        <input type="date" name="tgl_lahir" required><br>

        <label>Pekerjaan: </label>
        <select name="pekerjaan" required>
            <option value="programmer">Programmer</option>
            <option value="designer">Designer</option>
            <option value="manager">Manager</option>
        </select><br>

        <input type="submit" value="Submit">
    </form>

    <?php
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        $nama = $_POST["nama"];
        $tgl_lahir = $_POST["tgl_lahir"];
        $pekerjaan = $_POST["pekerjaan"];

        // Hitung umur berdasarkan tanggal lahir
        $tanggal_lahir = new DateTime($tgl_lahir);
        $today = new DateTime();
        $umur = $today->diff($tanggal_lahir)->y;

        // Tentukan gaji berdasarkan pekerjaan
        switch ($pekerjaan) {
            case "programmer":
                $gaji = 5000000;
                break;
            case "designer":
                $gaji = 4500000;
                break;
            case "manager":
                $gaji = 7000000;
                break;
            default:
                $gaji = 0;
        }

        // Tampilkan output
        echo "<h2>Output</h2>";
        echo "Nama: $nama<br>";
        echo "Umur: $umur tahun<br>";
        echo "Pekerjaan: $pekerjaan<br>";
        echo "Gaji: Rp " . number_format($gaji, 0, ',', '.') . "<br>";
    }
    ?>
</body>
</html>
```

##### Output

![Screenshot (217)](https://github.com/Najwaiffa/lab7web/assets/115856206/0493f836-02c7-4c94-a498-449f969beb36)
![Screenshot (218)](https://github.com/Najwaiffa/lab7web/assets/115856206/b5b1fb23-8e74-49ab-91fd-7df2030a5d75)
![Screenshot (219)](https://github.com/Najwaiffa/lab7web/assets/115856206/52c60544-3712-4318-90c4-faa33e96f4ae)
