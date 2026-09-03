<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MONITORING SALES AREA TRIYANTO</title>
    <!-- Tailwind CSS untuk Tampilan Modern & Canggih -->
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Inter', sans-serif; background-color: #f8fafc; color: #1e293b; line-height: 1.4; }
        .card-modern { background: #ffffff; border-radius: 1rem; box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.05), 0 2px 4px -2px rgb(0 0 0 / 0.05); border: 1px solid #e2e8f0; margin-bottom: 1rem; padding: 1.25rem; }
        fieldset { border: 1px solid #cbd5e1; border-radius: 0.75rem; padding: 1rem; margin-bottom: 1rem; background: #ffffff; }
        legend { font-weight: 600; font-size: 0.85rem; color: #2563eb; background: #eff6ff; padding: 0.25rem 0.75rem; border-radius: 9999px; border: 1px solid #bfdbfe; }
        input, select { width: 100%; padding: 0.6rem 0.75rem; margin-top: 0.25rem; margin-bottom: 0.75rem; border: 1px solid #cbd5e1; border-radius: 0.55rem; box-sizing: border-box; font-size: 0.875rem; background-color: #f8fafc; transition: all 0.2s; }
        input:focus, select:focus { outline: none; border-color: #2563eb; background-color: #ffffff; box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1); }
        label { display: block; font-weight: 600; font-size: 0.75rem; color: #475569; text-transform: uppercase; letter-spacing: 0.025em; }
        .row-group { display: flex; gap: 0.75rem; }
        .row-group > div { flex: 1; }
        button { background-color: #16a34a; color: white; padding: 0.75rem 1rem; border: none; border-radius: 0.65rem; cursor: pointer; width: 100%; font-weight: 600; font-size: 0.9rem; transition: background-color 0.2s, transform 0.1s; box-shadow: 0 4px 6px -1px rgba(22, 163, 74, 0.2); }
        button:hover { background-color: #15803d; }
        button:active { transform: scale(0.98); }
        .btn-blue { background-color: #2563eb; box-shadow: 0 4px 6px -1px rgba(37, 99, 235, 0.2); }
        .btn-blue:hover { background-color: #1d4ed8; }
        .btn-orange { background-color: #ea580c; box-shadow: 0 4px 6px -1px rgba(234, 88, 12, 0.2); margin-bottom: 0.75rem; }
        .btn-orange:hover { background-color: #c2410c; }
        .btn-purple { background-color: #7c3aed; box-shadow: 0 4px 6px -1px rgba(124, 58, 237, 0.2); margin-top: 0.5rem; margin-bottom: 0.75rem; }
        .btn-purple:hover { background-color: #6d28d9; }
        
        /* Teks Hasil Format WhatsApp Terang, Hitam Pekat, dan Tebal */
        pre { background: #ffffff; color: #000000 !important; font-weight: 700 !important; padding: 1rem; border-radius: 0.75rem; white-space: pre-wrap; word-wrap: break-word; font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace; font-size: 0.8rem; border: 1px solid #334155; max-height: 380px; overflow-y: auto; -webkit-text-fill-color: #000000 !important; }
        
        .loading { display: none; text-align: center; color: #d97706; font-weight: 600; font-size: 0.85rem; margin-top: 0.5rem; }
        .info-periode { font-size: 0.75rem; color: #dc2626; margin-bottom: 0.5rem; font-style: italic; font-weight: 500; }
        .table-input { width: 100%; border-collapse: collapse; margin-bottom: 0.5rem; font-size: 0.8rem; }
        .table-input th { background-color: #0d9488; color: white; padding: 0.5rem 0.25rem; text-align: center; border: 1px solid #14b8a6; font-size: 0.75rem; }
        .table-input td { padding: 0.35rem; border: 1px solid #e2e8f0; text-align: center; }
        .table-input input { text-align: center; margin-bottom: 0; padding: 0.4rem; font-size: 0.8rem; }
        .table-input td:first-child { text-align: left; padding-left: 0.5rem; }
    </style>
</head>
<body class="max-w-xl mx-auto p-3 sm:p-4">

    <!-- Header Judul -->
    <header class="text-center my-4 pb-3 border-b-2 border-blue-600">
        <h1 class="text-xl sm:text-2xl font-bold text-slate-800 tracking-wide">MONITORING SALES AREA TRIYANTO</h1>
        <p class="text-xs text-slate-500 mt-1 font-medium">Sistem Pelaporan & Rekapitulasi Toko Terintegrasi Cloud</p>
    </header>

    <div class="card-modern">
        <label for="modeReport">Pilih Jenis Laporan:</label>
        <select id="modeReport" onchange="toggleMode()">
            <option value="single">1. Laporan Per Toko (Shift)</option>
            <option value="rekap">2. Rekap Gabungan 20 Toko Area</option>
        </select>

        <div class="row-group mt-2">
            <div>
                <label for="periode">Periode (Tanggal Laporan):</label>
                <input type="date" id="periode" onchange="muatDataDariCloud()">
            </div>
            <div>
                <label for="shift" id="labelShift">Shift:</label>
                <input type="text" id="shift" value="2">
            </div>
        </div>

        <div class="row-group">
            <div>
                <label for="wh">WH:</label>
                <input type="text" id="wh" value="Bekasi">
            </div>
            <div>
                <label for="am">AM:</label>
                <input type="text" id="am" value="SRD">
            </div>
        </div>

        <label for="ac">AC:</label>
        <input type="text" id="ac" value="TRIYANTO">

        <div id="singleStoreSection" class="mt-1">
            <label for="selectStore">Pilih Toko:</label>
            <select id="selectStore" onchange="muatDataDariCloud()">
                <option value="CI30|STTD" data-target="222241060">CI30 - STTD (222.241.060)</option>
                <option value="CG54|MM2100" data-target="517228948">CG54 - MM2100 (517.228.948)</option>
                <option value="CG76|SPBU MM2100" data-target="318065515">CG76 - SPBU MM2100 (318.065.515)</option>
                <option value="CA71|WARUNG SENGON" data-target="257174148">CA71 - WARUNG SENGON (257.174.148)</option>
                <option value="C965|CIBUNTU" data-target="453303178">C965 - CIBUNTU (453.303.178)</option>
                <option value="CI15|RAYA PASAR SETU" data-target="219614971">CI15 - RAYA PASAR SETU (219.614.971)</option>
                <option value="CF50|DANAU INDAH" data-target="261984389">CF50 - DANAU INDAH (261.984.389)</option>
                <option value="C560|RAWA JULANG" data-target="244431245">C560 - RAWA JULANG (244.431.245)</option>
                <option value="CH41|KP. MARIUK" data-target="367249845">CH41 - KP. MARIUK (367.249.845)</option>
                <option value="CC21|RAYA KP. UTAN" data-target="329236895">CC21 - RAYA KP. UTAN (329.236.895)</option>
                <option value="C624|RAWA BANTENG" data-target="401328356">C624 - RAWA BANTENG (401.328.356)</option>
                <option value="CE47|MEKARWANGI" data-target="453977596">CE47 - MEKARWANGI (453.977.596)</option>
                <option value="CI54|RAWA JULANG BARU" data-target="194499104">CI54 - RAWA JULANG BARU (194.499.104)</option>
                <option value="C574|SUKADANAU 2" data-target="566487491">C574 - SUKADANAU 2 (566.487.491)</option>
                <option value="CG86|JARAKOSTA" data-target="269656078">CG86 - JARAKOSTA (269.656.078)</option>
                <option value="CH81|CIKEDOKAN SUKADANAU" data-target="371794096">CH81 - CIKEDOKAN SUKADANAU (371.794.096)</option>
                <option value="CA94|KP TANGSI" data-target="227022310">CA94 - KP TANGSI (227.022.310)</option>
                <option value="C935|TLAJUNG 2" data-target="316405150">C935 - TLAJUNG 2 (316.405.150)</option>
                <option value="CI84|TELAJUNG KAWASAN" data-target="328916205">CI84 - TELAJUNG KAWASAN (328.916.205)</option>
                <option value="C573|GRAHA MUSTIKA MEDIA" data-target="275823672">C573 - GRAHA MUSTIKA MEDIA (275.823.672)</option>
            </select>
        </div>
    </div>

    <!-- INPUT DETAIL PER TOKO -->
    <div class="card-modern" id="formPerToko">
        <fieldset>
            <legend>💰 REVENUE (Net Sales - Target MTD & Actual)</legend>
            <div class="row-group">
                <div><label>Time Factor (%):</label><input type="text" id="revTimeFactor" value="6,66%" oninput="hitungOtomatisSingle()"></div>
                <div><label>Actual (Rp):</label><input type="text" id="revActual" value="0" oninput="hitungOtomatisSingle()"></div>
            </div>
            <div class="row-group">
                <div><label>Target MTD (Rp):</label><input type="text" id="revTargetMtd" value="0" oninput="hitungOtomatisSingle()"></div>
                <div><label>Target TF (Rp) - Auto:</label><input type="text" id="revTargetTf" value="0" readonly style="background-color: #f1f5f9;"></div>
            </div>
            <div class="row-group">
                <div><label>Ach MTD (%):</label><input type="text" id="revAchMtd" value="0%" readonly style="background-color: #f1f5f9;"></div>
                <div><label>Ach TF (%):</label><input type="text" id="revAchTf" value="0%" readonly style="background-color: #f1f5f9;"></div>
            </div>
            <div class="row-group">
                <div><label>GAP to Target (Rp):</label><input type="text" id="revGapTarget" value="0" readonly style="background-color: #f1f5f9;"></div>
                <div><label>GAP to TF (Rp):</label><input type="text" id="revGapTf" value="0" readonly style="background-color: #f1f5f9;"></div>
            </div>
        </fieldset>

        <fieldset>
            <legend>FOKUS CABANG</legend>
            <div class="info-periode">📅 Target Berlaku Dari Tanggal: 
                <select id="rangeFokus" style="display:inline-block; width: 140px; padding: 3px; font-size: 0.8rem; margin-bottom: 0;">
                    <option value="1-15">Tanggal 1 s.d 15</option>
                    <option value="16-31">Tanggal 16 s.d 31</option>
                    <option value="1-31">Full 1 Bulan (1-31)</option>
                </select>
            </div>
            <table class="table-input">
                <thead>
                    <tr>
                        <th style="width: 40%;">Nama Program</th>
                        <th style="width: 20%;">Target</th>
                        <th style="width: 20%;">Sales</th>
                        <th style="width: 20%;">%</th>
                    </tr>
                </thead>
                <tbody>
                    <tr><td>TEBUS MURAH</td><td><input type="text" id="fokus1_t" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="fokus1_s" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="fokus1_p" value="0%" readonly style="background-color: #f1f5f9;"></td></tr>
                    <tr><td>SERBA GRATIS</td><td><input type="text" id="fokus2_t" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="fokus2_s" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="fokus2_p" value="0%" readonly style="background-color: #f1f5f9;"></td></tr>
                    <tr><td>SUEUGEER</td><td><input type="text" id="fokus3_t" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="fokus3_s" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="fokus3_p" value="0%" readonly style="background-color: #f1f5f9;"></td></tr>
                    <tr><td>PROMO CEBAN</td><td><input type="text" id="fokus4_t" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="fokus4_s" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="fokus4_p" value="0%" readonly style="background-color: #f1f5f9;"></td></tr>
                </tbody>
            </table>
            <button class="btn-purple" onclick="simpanBagianSpecific('Fokus Cabang')">💾 Simpan Data Fokus Cabang ke Cloud</button>
        </fieldset>

        <fieldset>
            <legend>MEMBER & STRUK</legend>
            <div class="row-group">
                <div><label>Actual New Member:</label><input type="text" id="memberNew" value="0"></div>
                <div><label>Struk Member:</label><input type="text" id="memberStruk" value="0"></div>
                <div><label>Total Struk:</label><input type="text" id="totalStruk" value="0"></div>
            </div>
        </fieldset>

        <fieldset>
            <legend>PSM</legend>
            <div class="info-periode">📅 Target Berlaku Dari Tanggal: 
                <select id="rangePsm" style="display:inline-block; width: 155px; padding: 3px; font-size: 0.8rem; margin-bottom: 0;">
                    <option value="1-15">Tanggal 1 s.d 15</option>
                    <option value="16-23">Tanggal 16 s.d 23</option>
                    <option value="24-31">Tanggal 24 s.d 30/31</option>
                    <option value="1-31">Full 1 Bulan (1-31)</option>
                </select>
            </div>
            <table class="table-input">
                <thead>
                    <tr>
                        <th style="width: 40%;">Nama Item PSM</th>
                        <th style="width: 20%;">Target</th>
                        <th style="width: 20%;">Actual</th>
                        <th style="width: 20%;">%</th>
                    </tr>
                </thead>
                <tbody>
                    <tr><td><input type="text" id="psm1_name" value="BANGO" style="text-align: left; font-weight: bold;"></td><td><input type="text" id="psm1_t" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="psm1_a" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="psm1_p" value="0%" readonly style="background-color: #f1f5f9;"></td></tr>
                    <tr><td><input type="text" id="psm2_name" value="DAIA" style="text-align: left; font-weight: bold;"></td><td><input type="text" id="psm2_t" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="psm2_a" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="psm2_p" value="0%" readonly style="background-color: #f1f5f9;"></td></tr>
                    <tr><td><input type="text" id="psm3_name" value="ENAAK" style="text-align: left; font-weight: bold;"></td><td><input type="text" id="psm3_t" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="psm3_a" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="psm3_p" value="0%" readonly style="background-color: #f1f5f9;"></td></tr>
                    <tr><td><input type="text" id="psm4_name" value="GARNIER" style="text-align: left; font-weight: bold;"></td><td><input type="text" id="psm4_t" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="psm4_a" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="psm4_p" value="0%" readonly style="background-color: #f1f5f9;"></td></tr>
                    <tr><td><input type="text" id="psm5_name" value="LE MINERAL" style="text-align: left; font-weight: bold;"></td><td><input type="text" id="psm5_t" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="psm5_a" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="psm5_p" value="0%" readonly style="background-color: #f1f5f9;"></td></tr>
                    <tr><td><input type="text" id="psm6_name" value="LIFEBUOY" style="text-align: left; font-weight: bold;"></td><td><input type="text" id="psm6_t" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="psm6_a" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="psm6_p" value="0%" readonly style="background-color: #f1f5f9;"></td></tr>
                    <tr><td><input type="text" id="psm7_name" value="NIPIS MADU" style="text-align: left; font-weight: bold;"></td><td><input type="text" id="psm7_t" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="psm7_a" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="psm7_p" value="0%" readonly style="background-color: #f1f5f9;"></td></tr>
                    <tr><td><input type="text" id="psm8_name" value="TARO" style="text-align: left; font-weight: bold;"></td><td><input type="text" id="psm8_t" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="psm8_a" value="0" oninput="hitungOtomatisSingle()"></td><td><input type="text" id="psm8_p" value="0%" readonly style="background-color: #f1f5f9;"></td></tr>
                    <tr>
                        <td><input type="text" id="psm9_name" value="" placeholder="Item Lainnya..." style="text-align: left; font-weight: bold;"></td>
                        <td><input type="text" id="psm9_t" value="0" oninput="hitungOtomatisSingle()"></td>
                        <td><input type="text" id="psm9_a" value="0" oninput="hitungOtomatisSingle()"></td>
                        <td><input type="text" id="psm9_p" value="0%" readonly style="background-color: #f1f5f9;"></td>
                    </tr>
                </tbody>
            </table>
            <button class="btn-purple" onclick="simpanBagianSpecific('PSM')">💾 Simpan Data PSM ke Cloud</button>
        </fieldset>

        <fieldset>
            <legend>CATEGORY (Rupiah Sales)</legend>
            <label>1. Toys (NS):</label><input type="text" id="cat1" value="0">
            <label>2. HBPL (NS):</label><input type="text" id="cat2" value="0">
        </fieldset>

        <fieldset>
            <legend>E-COMMERCE</legend>
            <label>Fee Base (Rp):</label><input type="text" id="feeBase" value="0">
        </fieldset>

        <button onclick="processData('single')">Generate & Simpan Semua ke Cloud</button>
    </div>

    <!-- INPUT REKAP 20 TOKO AREA -->
    <div class="card-modern" id="formRekapArea" style="display:none;">
        <fieldset>
            <legend>📊 GENERATE REKAP GABUNGAN 20 TOKO</legend>
            <p style="font-size: 0.8rem; color: #475569; margin-bottom: 0.75rem;">
                Fitur ini akan menarik seluruh data ke-20 toko yang sudah tersimpan di Cloud pada tanggal periode di atas, lalu merangkum totalnya menjadi format laporan area resmi.
            </p>
            <button class="btn-orange" onclick="generateRekapArea()">Tarik Data & Generate Rekap 20 Toko</button>
        </fieldset>
    </div>

    <div class="card-modern">
        <label>Hasil Format WhatsApp:</label>
        <pre id="outputResult"></pre>
        <div id="loadingStatus" class="loading">Sedang memproses data dengan Cloud...</div>
        <button class="btn-blue mt-3" onclick="copyResult()">Salin Teks WhatsApp</button>
    </div>

    <script>
        const WEB_APP_URL = "https://script.google.com/macros/s/AKfycbxYjtMqkKz_QmgTtJGIa5VzqqyBxaGx1CD2-5sKLgADtb6hoGUtAwB9WScug8HuQwa9/exec";

        function setTanggalOtomatisHP() {
            const today = new Date();
            const yyyy = today.getFullYear();
            const mm = String(today.getMonth() + 1).padStart(2, '0');
            const dd = String(today.getDate()).padStart(2, '0');
            document.getElementById('periode').value = `${yyyy}-${mm}-${dd}`;
        }

        function toggleMode() {
            const mode = document.getElementById('modeReport').value;
            if (mode === 'single') {
                document.getElementById('singleStoreSection').style.display = 'block';
                document.getElementById('formPerToko').style.display = 'block';
                document.getElementById('formRekapArea').style.display = 'none';
                document.getElementById('shift').style.display = 'block';
                document.getElementById('labelShift').style.display = 'block';
            } else {
                document.getElementById('singleStoreSection').style.display = 'none';
                document.getElementById('formPerToko').style.display = 'none';
                document.getElementById('formRekapArea').style.display = 'block';
                document.getElementById('shift').style.display = 'none';
                document.getElementById('labelShift').style.display = 'none';
            }
        }

        setTanggalOtomatisHP();

        // 1. FUNGSI RESET FORM KETIKA PINDAH TOKO / TANGGAL
        function resetFormToko() {
            // Reset Fokus Cabang
            for(let i=1; i<=4; i++) {
                document.getElementById(`fokus${i}_t`).value = "0";
                document.getElementById(`fokus${i}_s`).value = "0";
                document.getElementById(`fokus${i}_p`).value = "0%";
            }
            // Reset PSM
            for(let i=1; i<=9; i++) {
                if(document.getElementById(`psm${i}_t`)) document.getElementById(`psm${i}_t`).value = "0";
                if(document.getElementById(`psm${i}_a`)) document.getElementById(`psm${i}_a`).value = "0";
                if(document.getElementById(`psm${i}_p`)) document.getElementById(`psm${i}_p`).value = "0%";
            }
            // Reset Revenue & Lainnya
            document.getElementById('revActual').value = "0";
            document.getElementById('revTargetMtd').value = "0";
            document.getElementById('memberNew').value = "0";
            document.getElementById('memberStruk').value = "0";
            document.getElementById('totalStruk').value = "0";
            document.getElementById('cat1').value = "0";
            document.getElementById('cat2').value = "0";
            document.getElementById('feeBase').value = "0";
        }

        // 2. FUNGSI AMBIL DATA DARI CLOUD BERDASARKAN TOKO & TANGGAL
        function muatDataDariCloud() {
            const storeVal = document.getElementById('selectStore').value;
            const periode = document.getElementById('periode').value;
            const loading = document.getElementById('loadingStatus');

            // Kosongkan form dulu sebagai indikator awal perpindahan toko
            resetFormToko();

            loading.style.display = 'block';
            loading.innerText = "Memuat data toko dari Cloud...";

            // Mengirim request GET/POST untuk mengambil data toko tertentu
            fetch(`${WEB_APP_URL}?action=get&store=${encodeURIComponent(storeVal)}&periode=${periode}`)
            .then(res => res.json())
            .then(data => {
                loading.style.display = 'none';
                if (data && data.success && data.found) {
                    // Jika data toko tersebut ditemukan di cloud pada tanggal itu, isi otomatis form
                    const d = data.payload;
                    if(d.revActual) document.getElementById('revActual').value = d.revActual;
                    if(d.revTargetMtd) document.getElementById('revTargetMtd').value = d.revTargetMtd;
                    
                    // Isi data fokus cabang jika ada
                    if(d.fokus) {
                        for(let i=1; i<=4; i++) {
                            if(d.fokus[`t${i}`]) document.getElementById(`fokus${i}_t`).value = d.fokus[`t${i}`];
                            if(d.fokus[`s${i}`]) document.getElementById(`fokus${i}_s`).value = d.fokus[`s${i}`];
                        }
                    }
                    // Isi data PSM jika ada
                    if(d.psm) {
                        for(let i=1; i<=9; i++) {
                            if(d.psm[`t${i}`]) document.getElementById(`psm${i}_t`).value = d.psm[`t${i}`];
                            if(d.psm[`a${i}`]) document.getElementById(`psm${i}_a`).value = d.psm[`a${i}`];
                        }
                    }
                    alert(`✅ Data toko ${storeVal} untuk tanggal ${periode} berhasil dimuat.`);
                } else {
                    // Jika belum ada data tersimpan di tanggal itu, form tetap bersih (0)
                    console.log("Belum ada data tersimpan untuk toko & tanggal ini.");
                }
                hitungOtomatisSingle();
            })
            .catch(err => {
                loading.style.display = 'none';
                console.log("Mode offline atau belum ada data tersimpan di Cloud.");
                hitungOtomatisSingle();
            });
        }

        // 3. FUNGSI SIMPAN DATA KE CLOUD
        function processData(type) {
            const loading = document.getElementById('loadingStatus');
            loading.style.display = 'block';
            loading.innerText = "Sedang mengirim data ke Cloud...";

            const storeVal = document.getElementById('selectStore').value;
            const periode = document.getElementById('periode').value;

            // Mengumpulkan seluruh data per toko
            const payload = {
                action: 'save',
                periode: periode,
                store: storeVal,
                shift: document.getElementById('shift').value,
                wh: document.getElementById('wh').value,
                am: document.getElementById('am').value,
                ac: document.getElementById('ac').value,
                revActual: document.getElementById('revActual').value,
                revTargetMtd: document.getElementById('revTargetMtd').value,
                fokus: {
                    t1: document.getElementById('fokus1_t').value, s1: document.getElementById('fokus1_s').value,
                    t2: document.getElementById('fokus2_t').value, s2: document.getElementById('fokus2_s').value,
                    t3: document.getElementById('fokus3_t').value, s3: document.getElementById('fokus3_s').value,
                    t4: document.getElementById('fokus4_t').value, s4: document.getElementById('fokus4_s').value,
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
                }
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
                
                document.getElementById('outputResult').innerText = 
`LAPORAN SALES PER TOKO
Tanggal : ${periode}
Toko    : ${storeVal}
Status  : DATA BERHASIL DISIMPAN TERPISAH DI CLOUD ☁️`;
            })
            .catch(error => {
                loading.style.display = 'none';
                alert("❌ Gagal menyimpan ke Cloud. Periksa koneksi internet Anda.");
                console.error(error);
            });
        }

        function simpanBagianSpecific(bagian) {
            processData('single');
        }

        function generateRekapArea() {
            alert("Menarik rekap 20 toko dari Cloud...");
        }

        function copyResult() {
            const text = document.getElementById('outputResult').innerText;
            navigator.clipboard.writeText(text).then(() => {
                alert("Teks WhatsApp berhasil disalin!");
            });
        }

        function hitungOtomatisSingle() {
            // Kalkulasi persentase otomatis per item
            for(let i=1; i<=4; i++) {
                let t = parseFloat(document.getElementById(`fokus${i}_t`).value.replace(/\./g,'')) || 0;
                let s = parseFloat(document.getElementById(`fokus${i}_s`).value.replace(/\./g,'')) || 0;
                let p = t > 0 ? ((s / t) * 100).toFixed(1) + '%' : '0%';
                document.getElementById(`fokus${i}_p`).value = p;
            }
            for(let i=1; i<=9; i++) {
                let tElem = document.getElementById(`psm${i}_t`);
                let aElem = document.getElementById(`psm${i}_a`);
                let pElem = document.getElementById(`psm${i}_p`);
                if(tElem && aElem && pElem) {
                    let t = parseFloat(tElem.value.replace(/\./g,'')) || 0;
                    let a = parseFloat(aElem.value.replace(/\./g,'')) || 0;
                    let p = t > 0 ? ((a / t) * 100).toFixed(1) + '%' : '0%';
                    pElem.value = p;
                }
            }
        }
    </script>
</body>
</html>
