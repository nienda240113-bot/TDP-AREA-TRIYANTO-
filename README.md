<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Input Target & Laporan Sales</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 20px; background-color: #f4f6f9; color: #333; }
        .container { max-width: 600px; margin: auto; background: #fff; padding: 20px; border-radius: 8px; box-shadow: 0 2px 4px rgba(0,0,0,0.1); }
        h2 { text-align: center; color: #2c3e50; }
        .form-group { margin-bottom: 15px; }
        label { display: block; margin-bottom: 5px; font-weight: bold; }
        select, input { width: 100%; padding: 10px; box-sizing: border-box; border: 1px solid #ccc; border-radius: 4px; }
        button { background-color: #27ae60; color: white; padding: 12px; border: none; width: 100%; border-radius: 4px; font-size: 16px; cursor: pointer; }
        button:hover { background-color: #219653; }
        .info-loading { font-size: 12px; color: #e67e22; margin-top: 3px; display: none; }
    </style>
</head>
<body>

<div class="container">
    <h2>Form Target Toko Per Periode</h2>
    
    <!-- Pilihan Toko -->
    <div class="form-group">
        <label for="selectToko">Pilih Toko:</label>
        <select id="selectToko">
            <option value="C624 | Rowosari">C624 - Rowosari</option>
            <option value="C625 | ContohToko2">C625 - Contoh Toko 2</option>
            <!-- Tambahkan daftar toko Anda yang lain di sini -->
        </select>
    </div>

    <!-- Pilihan Periode -->
    <div class="form-group">
        <label for="periodeTarget">Pilih Periode:</label>
        <select id="periodeTarget">
            <option value="1-15">Periode 1 - 15</option>
            <option value="16-31">Periode 16 - 31</option>
        </select>
        <div id="loadingText" class="info-loading">Memuat data periode...</div>
    </div>

    <!-- Form Input Target (Contoh Fokus Cabang / PSM) -->
    <div class="form-group">
        <label for="inputTebusMurahTarget">Target Tebus Murah:</label>
        <input type="number" id="inputTebusMurahTarget" placeholder="Masukkan jumlah target...">
    </div>

    <div class="form-group">
        <label for="inputSerbaGratisTarget">Target Serba Gratis:</label>
        <input type="number" id="inputSerbaGratisTarget" placeholder="Masukkan jumlah target...">
    </div>

    <!-- Tombol Simpan -->
    <button type="button" id="btnSimpan" onclick="simpanTargetPeriode()">Simpan Target Periode Ini</button>
</div>

<script>
    // URL Web App Google Apps Script Anda yang sudah aktif
    const scriptURL = "https://script.google.com/macros/s/AKfycbxYjtMqkKz_QmgTtJGIa5VzqqyBxaGx1CD2-5sKLgADtb6hoGUtAwB9WScug8HuQwa9/exec";

    // FUNGSI MEMUAT DATA OTOMATIS SAAT TOKO ATAU PERIODE DIGANTI
    function muatTargetPeriode() {
        const selectToko = document.getElementById('selectToko');
        const selectPeriode = document.getElementById('periodeTarget');
        const loadingText = document.getElementById('loadingText');

        const kodeTokoFull = selectToko.value;
        const kodeToko = kodeTokoFull.split('|')[0].trim(); // Ambil kode depannya saja (misal: C624)
        const periodeVal = selectPeriode.value;
        const idKey = kodeToko + "_" + periodeVal; // Hasilnya misal: C624_1-15

        loadingText.style.display = "block";

        fetch(scriptURL + "?idKey=" + encodeURIComponent(idKey))
        .then(response => response.json())
        .then(data => {
            loadingText.style.display = "none";
            if (data) {
                // Jika data ditemukan di database, tampilkan di form
                document.getElementById('inputTebusMurahTarget').value = data.tebusMurahTarget || "";
                document.getElementById('inputSerbaGratisTarget').value = data.serbaGratisTarget || "";
            } else {
                // Jika belum ada isinya (bersih), kosongkan form
                document.getElementById('inputTebusMurahTarget').value = "";
                document.getElementById('inputSerbaGratisTarget').value = "";
            }
        })
        .catch(error => {
            loadingText.style.display = "none";
            console.error('Gagal memuat data:', error);
        });
    }

    // FUNGSI MENYIMPAN TARGET PERIODE KE GOOGLE SHEETS
    function simpanTargetPeriode() {
        const selectToko = document.getElementById('selectToko');
        const selectPeriode = document.getElementById('periodeTarget');
        const btnSimpan = document.getElementById('btnSimpan');

        const kodeTokoFull = selectToko.value;
        const kodeToko = kodeTokoFull.split('|')[0].trim();
        const periodeVal = selectPeriode.value;
        const idKey = kodeToko + "_" + periodeVal;

        // Kumpulkan data input form
        const formData = {
            tebusMurahTarget: document.getElementById('inputTebusMurahTarget').value,
            serbaGratisTarget: document.getElementById('inputSerbaGratisTarget').value
        };

        const payload = {
            idKey: idKey,
            kodeToko: kodeToko,
            periode: periodeVal,
            formData: formData
        };

        btnSimpan.innerText = "Menyimpan...";
        btnSimpan.disabled = true;

        fetch(scriptURL, {
            method: 'POST',
            body: JSON.stringify(payload)
        })
        .then(response => response.json())
        .then(result => {
            btnSimpan.innerText = "Simpan Target Periode Ini";
            btnSimpan.disabled = false;
            alert("Berhasil! Target untuk periode " + periodeVal + " tersimpan aman.");
        })
        .catch(error => {
            btnSimpan.innerText = "Simpan Target Periode Ini";
            btnSimpan.disabled = false;
            console.error('Gagal menyimpan:', error);
            alert("Terjadi kesalahan saat menyimpan data.");
        });
    }

    // Jalankan fungsi muat data otomatis saat halaman pertama dibuka atau pilihan diubah
    window.addEventListener('DOMContentLoaded', () => {
        muatTargetPeriode(); // Muat data awal saat halaman diload

        document.getElementById('selectToko').addEventListener('change', muatTargetPeriode);
        document.getElementById('periodeTarget').addEventListener('change', muatTargetPeriode);
    });
</script>

</body>
</html>
