<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MONITORING SALES AREA TRIYANTO</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Inter', sans-serif; background-color: #f8fafc; color: #1e293b; line-height: 1.4; }
        .card-modern { background: #ffffff; border-radius: 1rem; box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.05); border: 1px solid #e2e8f0; margin-bottom: 1rem; padding: 1.25rem; }
        fieldset { border: 1px solid #cbd5e1; border-radius: 0.75rem; padding: 1rem; margin-bottom: 1rem; background: #ffffff; }
        legend { font-weight: 600; font-size: 0.85rem; color: #2563eb; background: #eff6ff; padding: 0.25rem 0.75rem; border-radius: 9999px; border: 1px solid #bfdbfe; }
        input, select { width: 100%; padding: 0.5rem 0.75rem; margin-top: 0.2rem; margin-bottom: 0.5rem; border: 1px solid #cbd5e1; border-radius: 0.55rem; box-sizing: border-box; font-size: 0.85rem; background-color: #f8fafc; transition: all 0.2s; }
        input:focus, select:focus { outline: none; border-color: #2563eb; background-color: #ffffff; box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1); }
        label { display: block; font-weight: 600; font-size: 0.75rem; color: #475569; text-transform: uppercase; letter-spacing: 0.025em; }
        .row-group { display: flex; gap: 0.75rem; }
        .row-group > div { flex: 1; }
        button { background-color: #16a34a; color: white; padding: 0.75rem 1rem; border: none; border-radius: 0.65rem; cursor: pointer; width: 100%; font-weight: 600; font-size: 0.9rem; transition: background-color 0.2s, transform 0.1s; box-shadow: 0 4px 6px -1px rgba(22, 163, 74, 0.2); }
        button:hover { background-color: #15803d; }
        pre { background: #ffffff; color: #000000 !important; font-weight: 700 !important; padding: 1rem; border-radius: 0.75rem; white-space: pre-wrap; font-family: monospace; font-size: 0.75rem; border: 1px solid #334155; }
        .loading { display: none; text-align: center; color: #d97706; font-weight: 600; font-size: 0.85rem; margin-top: 0.5rem; }
        .table-input { width: 100%; border-collapse: collapse; margin-bottom: 0.5rem; font-size: 0.8rem; }
        .table-input th { background-color: #0d9488; color: white; padding: 0.4rem; text-align: center; border: 1px solid #14b8a6; font-size: 0.75rem; }
        .table-input td { padding: 0.3rem; border: 1px solid #e2e8f0; text-align: center; }
        .table-input input { text-align: center; margin-bottom: 0; padding: 0.35rem; font-size: 0.8rem; }
        .table-input td:first-child { text-align: left; padding-left: 0.5rem; font-weight: 500; font-size: 0.75rem; }
    </style>
</head>
<body class="max-w-xl mx-auto p-3 sm:p-4">

    <header class="text-center my-4 pb-3 border-b-2 border-blue-600">
        <h1 class="text-xl sm:text-2xl font-bold text-slate-800">MONITORING SALES AREA TRIYANTO</h1>
        <p class="text-xs text-slate-500 mt-1 font-medium">Sistem Pelaporan & Rekapitulasi Toko Terintegrasi Cloud</p>
    </header>

    <!-- PILIHAN MODE LAPORAN -->
    <div class="card-modern border-blue-300 bg-blue-50/50">
        <label for="modeReport" class="text-blue-700">Pilih Jenis Mode:</label>
        <select id="modeReport" onchange="toggleModeReport()" class="bg-white font-semibold text-blue-900 border-blue-300">
            <option value="single">1. Input / Edit Per Toko</option>
            <option value="rekap">2. Rekap Gabungan 20 Toko Area</option>
        </select>
    </div>

    <div class="card-modern">
        <label for="periode">Periode (Tanggal Laporan):</label>
        <input type="date" id="periode" onchange="handlePeriodeChange()">

        <div class="row-group mt-2">
            <div><label>Shift:</label><input type="text" id="shift" value="2"></div>
            <div><label>WH:</label><input type="text" id="wh" value="Bekasi"></div>
        </div>

        <div class="row-group">
            <div><label>AM:</label><input type="text" id="am" value="SRD"></div>
            <div><label>AC:</label><input type="text" id="ac" value="TRIYANTO"></div>
        </div>

        <div id="containerSelectStore">
            <label for="selectStore">Pilih Toko:</label>
            <select id="selectStore" onchange="muatDataDariCloud()">
                <option value="CI30|STTD">CI30 - STTD</option>
                <option value="CG54|MM2100">CG54 - MM2100</option>
                <option value="CG76|SPBU MM2100">CG76 - SPBU MM2100</option>
                <option value="CA71|WARUNG SENGON">CA71 - WARUNG SENGON</option>
                <option value="C965|CIBUNTU">C965 - CIBUNTU</option>
                <option value="CI15|RAYA PASAR SETU">CI15 - RAYA PASAR SETU</option>
                <option value="CF50|DANAU INDAH">CF50 - DANAU INDAH</option>
                <option value="C560|RAWA JULANG">C560 - RAWA JULANG</option>
                <option value="CH41|KP. MARIUK">CH41 - KP. MARIUK</option>
                <option value="CC21|RAYA KP. UTAN">CC21 - RAYA KP. UTAN</option>
                <option value="C624|RAWA BANTENG">C624 - RAWA BANTENG</option>
                <option value="CE47|MEKARWANGI">CE47 - MEKARWANGI</option>
                <option value="CI54|RAWA JULANG BARU">CI54 - RAWA JULANG BARU</option>
                <option value="C574|SUKADANAU 2">C574 - SUKADANAU 2</option>
                <option value="CG86|JARAKOSTA">CG86 - JARAKOSTA</option>
                <option value="CH81|CIKEDOKAN SUKADANAU">CH81 - CIKEDOKAN SUKADANAU</option>
                <option value="CA94|KP TANGSI">CA94 - KP TANGSI</option>
                <option value="C935|TLAJUNG 2">C935 - TLAJUNG 2</option>
                <option value="CI84|TELAJUNG KAWASAN">CI84 - TELAJUNG KAWASAN</option>
                <option value="C573|GRAHA MUSTIKA MEDIA">C573 - GRAHA MUSTIKA MEDIA</option>
            </select>
        </div>
    </div>

    <!-- FORM INPUT PER TOKO -->
    <div class="card-modern" id="formPerToko">
        <fieldset>
            <legend>💰 REVENUE / NET SALES</legend>
            <div class="row-group">
                <div><label>Time Factor (%):</label><input type="text" id="revTimeFactor" value="3.3"></div>
                <div><label>Actual Sales (Rp):</label><input type="text" id="revActual" value="0"></div>
            </div>
            <div class="row-group">
                <div><label>Target MTD (Rp):</label><input type="text" id="revTargetMtd" value="0"></div>
                <div><label>Target Time Factor (Rp):</label><input type="text" id="revTargetTf" value="0"></div>
            </div>
        </fieldset>

        <fieldset>
            <legend>FOKUS CABANG</legend>
            <table class="table-input">
                <thead>
                    <tr><th>Nama Program</th><th>Target</th><th>Sales</th></tr>
                </thead>
                <tbody>
                    <tr><td>TEBUS MURAH</td><td><input type="text" id="fokus1_t" value="0"></td><td><input type="text" id="fokus1_s" value="0"></td></tr>
                    <tr><td>SERBA GRATIS</td><td><input type="text" id="fokus2_t" value="0"></td><td><input type="text" id="fokus2_s" value="0"></td></tr>
                    <tr><td>SUEUGEER</td><td><input type="text" id="fokus3_t" value="0"></td><td><input type="text" id="fokus3_s" value="0"></td></tr>
                    <tr><td>PROMO CEBAN</td><td><input type="text" id="fokus4_t" value="0"></td><td><input type="text" id="fokus4_s" value="0"></td></tr>
                </tbody>
            </table>
        </fieldset>

        <fieldset>
            <legend>MEMBER & STRUK</legend>
            <div class="row-group">
                <div><label>Actual New Member:</label><input type="text" id="memNew" value="0"></div>
                <div><label>Struk Member:</label><input type="text" id="memStruk" value="0"></div>
            </div>
            <div><label>Total Struk Keseluruhan:</label><input type="text" id="memTotalStruk" value="0"></div>
        </fieldset>

        <fieldset>
            <legend>PSM (PRODUK SPECIAL MINGGUAN)</legend>
            <table class="table-input">
                <thead>
                    <tr><th>Item PSM</th><th>Target</th><th>Actual</th></tr>
                </thead>
                <tbody>
                    <tr><td>Bango</td><td><input type="text" id="psm1_t" value="0"></td><td><input type="text" id="psm1_a" value="0"></td></tr>
                    <tr><td>Daia</td><td><input type="text" id="psm2_t" value="0"></td><td><input type="text" id="psm2_a" value="0"></td></tr>
                    <tr><td>Enaak</td><td><input type="text" id="psm3_t" value="0"></td><td><input type="text" id="psm3_a" value="0"></td></tr>
                    <tr><td>Garnier</td><td><input type="text" id="psm4_t" value="0"></td><td><input type="text" id="psm4_a" value="0"></td></tr>
                    <tr><td>Le Minerale</td><td><input type="text" id="psm5_t" value="0"></td><td><input type="text" id="psm5_a" value="0"></td></tr>
                    <tr><td>Lifebuoy</td><td><input type="text" id="psm6_t" value="0"></td><td><input type="text" id="psm6_a" value="0"></td></tr>
                    <tr><td>Nipis Madu</td><td><input type="text" id="psm7_t" value="0"></td><td><input type="text" id="psm7_a" value="0"></td></tr>
                    <tr><td>Taro</td><td><input type="text" id="psm8_t" value="0"></td><td><input type="text" id="psm8_a" value="0"></td></tr>
                    <tr><td>PAM Lain</td><td><input type="text" id="psm9_t" value="0"></td><td><input type="text" id="psm9_a" value="0"></td></tr>
                </tbody>
            </table>
        </fieldset>

        <fieldset>
            <legend>CATEGORY & E-COMMERCE</legend>
            <div class="row-group">
                <div><label>Toys (NS):</label><input type="text" id="catToys" value="0"></div>
                <div><label>HBPL (NS):</label><input type="text" id="catHbpl" value="0"></div>
            </div>
            <div class="row-group mt-2">
                <div><label>Telur (Sales):</label><input type="text" id="catTelur" value="0"></div>
                <div><label>Fee Base E-Commerce (Rp):</label><input type="text" id="ecomFee" value="0"></div>
            </div>
        </fieldset>

        <button onclick="simpanKeCloud()">💾 Simpan Semua Data ke Cloud & Generate WA</button>
    </div>

    <!-- PREVIEW / STATUS -->
    <div class="card-modern">
        <label>Status / Preview WhatsApp:</label>
        <pre id="outputResult">Belum ada data dikirim.</pre>
        <div id="loadingStatus" class="loading">Memuat data dari Cloud...</div>
    </div>

    <script>
        const WEB_APP_URL = "https://script.google.com/macros/s/AKfycbwgUCeDwAHOdjK6WmZ0RrUpQ1fzpI0jBQx7lggkYC4U7CZfwcV52s59WQ_DPyaAFrDi/exec";

        function setTanggalOtomatis() {
            const today = new Date();
            const yyyy = today.getFullYear();
            const mm = String(today.getMonth() + 1).padStart(2, '0');
            const dd = String(today.getDate()).padStart(2, '0');
            document.getElementById('periode').value = `${yyyy}-${mm}-${dd}`;
            muatDataDariCloud();
        }

        function resetForm() {
            document.getElementById('revTimeFactor').value = "3.3";
            document.getElementById('revActual').value = "0";
            document.getElementById('revTargetMtd').value = "0";
            document.getElementById('revTargetTf').value = "0";
            for(let i=1; i<=4; i++) {
                document.getElementById(`fokus${i}_t`).value = "0";
                document.getElementById(`fokus${i}_s`).value = "0";
            }
            document.getElementById('memNew').value = "0";
            document.getElementById('memStruk').value = "0";
            document.getElementById('memTotalStruk').value = "0";
            for(let i=1; i<=9; i++) {
                document.getElementById(`psm${i}_t`).value = "0";
                document.getElementById(`psm${i}_a`).value = "0";
            }
            document.getElementById('catToys').value = "0";
            document.getElementById('catHbpl').value = "0";
            document.getElementById('catTelur').value = "0";
            document.getElementById('ecomFee').value = "0";
        }

        function toggleModeReport() {
            const mode = document.getElementById('modeReport').value;
            const formToko = document.getElementById('formPerToko');
            const selectStoreContainer = document.getElementById('containerSelectStore');

            if (mode === 'rekap') {
                formToko.style.display = 'none';
                selectStoreContainer.style.display = 'none';
                tarikRekapArea();
            } else {
                formToko.style.display = 'block';
                selectStoreContainer.style.display = 'block';
                muatDataDariCloud();
            }
        }

        function handlePeriodeChange() {
            const mode = document.getElementById('modeReport').value;
            if (mode === 'rekap') {
                tarikRekapArea();
            } else {
                muatDataDariCloud();
            }
        }

        function hitungPersen(target, actual) {
            let t = parseFloat(String(target).replace(/\./g,'')) || 0;
            let a = parseFloat(String(actual).replace(/\./g,'')) || 0;
            if (t === 0) return "0%";
            return Math.round((a / t) * 100) + "%";
        }

        function formatRupiah(angka) {
            let num = parseFloat(String(angka).replace(/\./g,'')) || 0;
            return num.toLocaleString('id-ID');
        }

        // Ambil data per toko dari Cloud
        function muatDataDariCloud() {
            const storeVal = document.getElementById('selectStore').value;
            const periode = document.getElementById('periode').value;
            const loading = document.getElementById('loadingStatus');

            resetForm();
            loading.style.display = 'block';

            fetch(`${WEB_APP_URL}?action=get&store=${encodeURIComponent(storeVal)}&periode=${periode}`)
            .then(res => res.json())
            .then(data => {
                loading.style.display = 'none';
                if (data.success && data.found) {
                    const d = data.payload;
                    if(d.revTimeFactor) document.getElementById('revTimeFactor').value = d.revTimeFactor;
                    if(d.revActual) document.getElementById('revActual').value = d.revActual;
                    if(d.revTargetMtd) document.getElementById('revTargetMtd').value = d.revTargetMtd;
                    if(d.revTargetTf) document.getElementById('revTargetTf').value = d.revTargetTf;
                    
                    if(d.fokus) {
                        for(let i=1; i<=4; i++) {
                            if(d.fokus[`t${i}`]) document.getElementById(`fokus${i}_t`).value = d.fokus[`t${i}`];
                            if(d.fokus[`s${i}`]) document.getElementById(`fokus${i}_s`).value = d.fokus[`s${i}`];
                        }
                    }
                    if(d.member) {
                        if(d.member.new) document.getElementById('memNew').value = d.member.new;
                        if(d.member.struk) document.getElementById('memStruk').value = d.member.struk;
                        if(d.member.totalStruk) document.getElementById('memTotalStruk').value = d.member.totalStruk;
                    }
                    if(d.psm) {
                        for(let i=1; i<=9; i++) {
                            if(d.psm[`t${i}`]) document.getElementById(`psm${i}_t`).value = d.psm[`t${i}`];
                            if(d.psm[`a${i}`]) document.getElementById(`psm${i}_a`).value = d.psm[`a${i}`];
                        }
                    }
                    if(d.category) {
                        if(d.category.toys) document.getElementById('catToys').value = d.category.toys;
                        if(d.category.hbpl) document.getElementById('catHbpl').value = d.category.hbpl;
                        if(d.category.telur) document.getElementById('catTelur').value = d.category.telur;
                    }
                    if(d.ecomFee) document.getElementById('ecomFee').value = d.ecomFee;

                    generatePreviewWA(storeVal, periode, d);
                    document.getElementById('outputResult').innerText += `\n(Data toko ${storeVal} berhasil dimuat dari Cloud)`;
                } else {
                    document.getElementById('outputResult').innerText = `Belum ada data tersimpan untuk toko ini pada tanggal ${periode}.`;
                }
            })
            .catch(err => {
                loading.style.display = 'none';
                console.error(err);
            });
        }

        function generatePreviewWA(storeVal, periode, d) {
            let storeParts = storeVal.split('|');
            let kdStore = storeParts[0];
            let namaStore = storeParts[1];

            let tMtd = parseFloat(String(d.revTargetMtd).replace(/\./g,'')) || 0;
            let aMtd = parseFloat(String(d.revActual).replace(/\./g,'')) || 0;
            let gapMtd = tMtd - aMtd;
            let acvMtd = tMtd > 0 ? Math.round((aMtd / tMtd) * 100) : 0;

            let tTf = parseFloat(String(d.revTargetTf).replace(/\./g,'')) || 0;
            let gapTf = tTf - aMtd;
            let acvTf = tTf > 0 ? Math.round((aMtd / tTf) * 100) : 0;

            let f = d.fokus || {};
            let m = d.member || {};
            let p = d.psm || {};
            let c = d.category || {};

            let teksWA = `REPORT SALES HARIAN\n` +
            `PERIODE : ${periode}\n` +
            `WH : ${d.wh || 'Bekasi'}\n` +
            `AM : ${d.am || 'SRD'}\n` +
            `AC : ${d.ac || 'TRIYANTO'}\n` +
            `KD Toko : ${kdStore}\n` +
            `Nama Toko : ${namaStore}\n` +
            `Shift : ${d.shift || '2'}\n` +
            `======================\n\n` +
            `*REVENUE*\n` +
            `1. NET SALES\n` +
            `- Time factor: ${d.revTimeFactor}%\n` +
            `- TARGET MTD :Rp ${formatRupiah(d.revTargetMtd)}\n` +
            `- Target Time Factor: Rp ${formatRupiah(d.revTargetTf)}\n` +
            `- ACTUAL :Rp ${formatRupiah(d.revActual)}\n` +
            `- ACHIVE MTD: ${acvMtd}%\n` +
            `- Achieved Time Factor : ${acvTf}%\n` +
            `- GAP TO TARGET :Rp ${formatRupiah(gapMtd)}\n` +
            `- GAP To Time Factor: Rp ${formatRupiah(gapTf)}\n\n` +
            `*FOKUS CABANG*\n` +
            `======================\n` +
            `TARGET/ACTUAL/ACV%\n` +
            `1. TEBUS MURAH : ${f.t1 || 0}/${f.s1 || 0}/${hitungPersen(f.t1, f.s1)}\n` +
            `2. SERBA GRATIS : ${f.t2 || 0}/${f.s2 || 0}/${hitungPersen(f.t2, f.s2)}\n` +
            `3. SUUEGEER : ${f.t3 || 0}/${f.s3 || 0}/${hitungPersen(f.t3, f.s3)}\n` +
            `4. PROMO CEBAN : ${f.t4 || 0}/${f.s4 || 0}/${hitungPersen(f.t4, f.s4)}\n` +
            `======================\n` +
            `*MEMBER*\n` +
            `1. Actual NEW MEMBER : ${m.new || 0}\n` +
            `2. Konstribusi struk Member : (Struk MEMBER : Total struk = ${m.struk || 0}/${m.totalStruk || 0}/${hitungPersen(m.totalStruk, m.struk)}\n` +
            `======================\n` +
            `*PSM* (In Qty).\n` +
            `(Target - Actual - %)\n` +
            `Bango : ${p.t1 || 0}/${p.a1 || 0}/${hitungPersen(p.t1, p.a1)}\n` +
            `Daia : ${p.t2 || 0}/${p.a2 || 0}/${hitungPersen(p.t2, p.a2)}\n` +
            `Enaak : ${p.t3 || 0}/${p.a3 || 0}/${hitungPersen(p.t3, p.a3)}\n` +
            `Garnier : ${p.t4 || 0}/${p.a4 || 0}/${hitungPersen(p.t4, p.a4)}\n` +
            `Le Minerale : ${p.t5 || 0}/${p.a5 || 0}/${hitungPersen(p.t5, p.a5)}\n` +
            `Lifebuoy : ${p.t6 || 0}/${p.a6 || 0}/${hitungPersen(p.t6, p.a6)}\n` +
            `Nipis Madu : ${p.t7 || 0}/${p.a7 || 0}/${hitungPersen(p.t7, p.a7)}\n` +
            `Taro : ${p.t8 || 0}/${p.a8 || 0}/${hitungPersen(p.t8, p.a8)}\n` +
            `PAM LAIN: ${p.t9 || 0}/${p.a9 || 0}/${hitungPersen(p.t9, p.a9)}\n` +
            `======================\n` +
            `*CATEGORY* (Rupiah / Sales)\n` +
            `1. TOYS (NS) : Rp ${formatRupiah(c.toys || 0)}\n` +
            `2. HBPL (NS) : Rp ${formatRupiah(c.hbpl || 0)}\n` +
            `3. TELUR : ${c.telur || 0}\n` +
            `======================\n` +
            `*E-COMMERCE*\n` +
            `1. FEE BASE (RP) : Rp ${formatRupiah(d.ecomFee || 0)}\n\n` +
            `Terimakasih`;

            document.getElementById('outputResult').innerText = teksWA;
        }

        // Tarik rekap gabungan 20 toko area
        function tarikRekapArea() {
            const periode = document.getElementById('periode').value;
            const loading = document.getElementById('loadingStatus');
            loading.style.display = 'block';
            loading.innerText = "Menarik rekapitulasi 20 toko dari Cloud...";

            fetch(`${WEB_APP_URL}?action=rekapArea&periode=${periode}`)
            .then(res => res.json())
            .then(data => {
                loading.style.display = 'none';
                if(data.success) {
                    let totalActualSemuaToko = 0;
                    let totalTargetSemuaToko = 0;
                    let rincianTeks = `📊 *REKAP AREA SALES TRIYANTO*\n📅 Tanggal: ${periode}\n----------------------------------\n`;
                    
                    if (data.rekapList.length === 0) {
                        rincianTeks += `Belum ada data toko yang tersimpan pada tanggal ${periode}.`;
                    } else {
                        data.rekapList.forEach((item, index) => {
                            let p = item.payload;
                            let actual = parseFloat(String(p.revActual).replace(/\./g,'')) || 0;
                            let target = parseFloat(String(p.revTargetMtd).replace(/\./g,'')) || 0;
                            
                            totalActualSemuaToko += actual;
                            totalTargetSemuaToko += target;
                            
                            rincianTeks += `${index + 1}. Toko ${item.store}\n   Actual: Rp ${p.revActual} | Target: Rp ${p.revTargetMtd}\n`;
                        });
                        
                        rincianTeks += `----------------------------------\n`;
                        rincianTeks += `💰 *TOTAL ACTUAL AREA: Rp ${totalActualSemuaToko.toLocaleString('id-ID')}*\n`;
                        rincianTeks += `🎯 *TOTAL TARGET MTD: Rp ${totalTargetSemuaToko.toLocaleString('id-ID')}*`;
                    }
                    
                    document.getElementById('outputResult').innerText = rincianTeks;
                }
            })
            .catch(err => {
                loading.style.display = 'none';
                alert("Gagal menarik data rekap area.");
                console.error(err);
            });
        }

        // Simpan data per toko ke Cloud
        function simpanKeCloud() {
            const loading = document.getElementById('loadingStatus');
            loading.style.display = 'block';
            loading.innerText = "Menyimpan data ke Cloud...";

            const storeVal = document.getElementById('selectStore').value;
            const periode = document.getElementById('periode').value;

            const payload = {
                periode: periode,
                store: storeVal,
                shift: document.getElementById('shift').value,
                wh: document.getElementById('wh').value,
                am: document.getElementById('am').value,
                ac: document.getElementById('ac').value,
                revTimeFactor: document.getElementById('revTimeFactor').value,
                revActual: document.getElementById('revActual').value,
                revTargetMtd: document.getElementById('revTargetMtd').value,
                revTargetTf: document.getElementById('revTargetTf').value,
                fokus: {
                    t1: document.getElementById('fokus1_t').value, s1: document.getElementById('fokus1_s').value,
                    t2: document.getElementById('fokus2_t').value, s2: document.getElementById('fokus2_s').value,
                    t3: document.getElementById('fokus3_t').value, s3: document.getElementById('fokus3_s').value,
                    t4: document.getElementById('fokus4_t').value, s4: document.getElementById('fokus4_s').value,
                },
                member: {
                    new: document.getElementById('memNew').value,
                    struk: document.getElementById('memStruk').value,
                    totalStruk: document.getElementById('memTotalStruk').value
                },
                psm: {
                    t1: document.getElementById('psm1_t').value, a1: document.getElementById('psm1_a').value,
                    t2: document.getElementById('psm2_t').value, a2: document.getElementById('psm2_a').value,
                    t3: document.getElementById('psm3_t').value, a3: document.getElementById('psm3_a').value,
                    t4: document.getElementById('psm4_t').value, a4: document.getElementById('psm4_a').value,
                    t5: document.getElementById('psm5_t').value, a5: document.getElementById('psm5_a').value,
                    t6: document.getElementById('psm6_t').value, a6: document.getElementById('psm6_a').value,
                    t7: document.getElementById('psm7_t').value, a7: document.getElementById('psm7_a').value,
                    t8: document.getElementById('psm8_t').value, a8: document.getElementById('psm8_a').value,
                    t9: document.getElementById('psm9_t').value, a9: document.getElementById('psm9_a').value,
                },
                category: {
                    toys: document.getElementById('catToys').value,
                    hbpl: document.getElementById('catHbpl').value,
                    telur: document.getElementById('catTelur').value
                },
                ecomFee: document.getElementById('ecomFee').value
            };

            fetch(WEB_APP_URL, {
                method: 'POST',
                mode: 'no-cors',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify(payload)
            })
            .then(() => {
                loading.style.display = 'none';
                alert(`✅ Sukses! Data toko ${storeVal} berhasil disimpan ke Cloud.`);
                generatePreviewWA(storeVal, periode, payload);
            })
            .catch(error => {
                loading.style.display = 'none';
                alert("❌ Gagal menyimpan ke Cloud.");
                console.error(error);
            });
        }

        // Jalankan saat pertama kali halaman dibuka
        setTanggalOtomatis();
    </script>
</body>
</html>
