<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TDP-AREA-TRIYANTO-</title>
    <!-- CSS / Tampilan lama Anda tetap di sini -->
</head>
<body>

    <!-- SEMUA TAMPILAN HTML ASLI ANDA TETAP DI SINI (JANGAN DIUBAH) -->

    <!-- BAGIAN SCRIPT JS (PASTIKAN ADA TAG <script> DI LUARNYA SEPERTI INI) -->
    <script>
        const WEB_APP_URL = "https://script.google.com/macros/s/AKfycbwUPlJnPcClGwFrhk29A-1zgtIsN1d_dxrnyOhXFPSe57yhEfscL0BLK30gt5elFY-S/exec";

        // 1. Otomatis cek data tersimpan saat halaman dibuka/di-refresh
        window.addEventListener('DOMContentLoaded', () => {
            const savedStoreCode = localStorage.getItem('activeStoreCode');
            if (savedStoreCode) {
                const selectElement = document.getElementById('select-store');
                if (selectElement) selectElement.value = savedStoreCode;
                loadDataFromCloud(savedStoreCode);
            }
        });

        // 2. Fungsi saat pilihan toko diubah
        function handleStoreChange() {
            const storeCode = document.getElementById('select-store').value;
            if (storeCode) {
                localStorage.setItem('activeStoreCode', storeCode);
                loadDataFromCloud(storeCode);
            } else {
                clearScreenInputs();
            }
        }

        // 3. Fungsi untuk menarik data dari Google Sheets
        async function loadDataFromCloud(storeCode) {
            try {
                let response = await fetch(`${WEB_APP_URL}?storeCode=${storeCode}`);
                let result = await response.json();
                
                if (result.status === "success" && result.data) {
                    let data = result.data;
                    if (data.fokusCabang) {
                        if(document.getElementById('target-tebus-murah')) document.getElementById('target-tebus-murah').value = data.fokusCabang.tebusMurah || 0;
                        if(document.getElementById('target-serba-gratis')) document.getElementById('target-serba-gratis').value = data.fokusCabang.serbaGratis || 0;
                        if(document.getElementById('target-sueugeer')) document.getElementById('target-sueugeer').value = data.fokusCabang.sueugeer || 0;
                        if(document.getElementById('target-promo-ceban')) document.getElementById('target-promo-ceban').value = data.fokusCabang.promoCeban || 0;
                    }
                } else {
                    clearScreenInputs();
                }
            } catch (error) {
                console.error("Gagal memuat data:", error);
            }
        }

        // 4. Fungsi untuk Menyimpan Data
        async function saveDataToCloud() {
            const storeCode = document.getElementById('select-store').value;
            if (!storeCode) {
                alert("Pilih kode toko terlebih dahulu!");
                return;
            }

            const payloadData = {
                fokusCabang: {
                    tebusMurah: document.getElementById('target-tebus-murah') ? document.getElementById('target-tebus-murah').value : 0,
                    serbaGratis: document.getElementById('target-serba-gratis') ? document.getElementById('target-serba-gratis').value : 0,
                    sueugeer: document.getElementById('target-sueugeer') ? document.getElementById('target-sueugeer').value : 0,
                    promoCeban: document.getElementById('target-promo-ceban') ? document.getElementById('target-promo-ceban').value : 0
                }
            };

            try {
                let response = await fetch(WEB_APP_URL, {
                    method: 'POST',
                    body: JSON.stringify({ storeCode: storeCode, payload: payloadData })
                });
                let result = await response.json();
                if (result.status === "success") {
                    alert("Target & Fokus Cabang berhasil disimpan ke Cloud & Layar!");
                } else {
                    alert("Gagal menyimpan: " + result.message);
                }
            } catch (err) {
                console.error(err);
                alert("Terjadi kesalahan koneksi.");
            }
        }

        function clearScreenInputs() {
            if(document.getElementById('target-tebus-murah')) document.getElementById('target-tebus-murah').value = 0;
            if(document.getElementById('target-serba-gratis')) document.getElementById('target-serba-gratis').value = 0;
            if(document.getElementById('target-sueugeer')) document.getElementById('target-sueugeer').value = 0;
            if(document.getElementById('target-promo-ceban')) document.getElementById('target-promo-ceban').value = 0;
        }
    </script>
</body>
</html>
