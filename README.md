<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Report Sales Shift & Rekap 20 Toko</title>
    <style>
        body { font-family: Arial, sans-serif; line-height: 1.25; color: #333; max-width: 680px; margin: 0 auto; padding: 12px; background-color: #f4f6f9; }
        h1 { font-size: 1.2rem; color: #2c3e50; border-bottom: 2px solid #3498db; padding-bottom: 8px; text-align: center; }
        .card { background: #fff; padding: 12px; border-radius: 8px; box-shadow: 0 2px 4px rgba(0,0,0,0.1); margin-bottom: 12px; }
        label { display: block; margin-bottom: 4px; font-weight: bold; font-size: 0.8rem; }
        select, input { width: 100%; padding: 7px; margin-bottom: 8px; border: 1px solid #ccc; border-radius: 4px; box-sizing: border-box; font-size: 0.85rem; }
        .row-group { display: flex; gap: 8px; }
        .row-group > div { flex: 1; }
        button { background-color: #27ae60; color: white; padding: 10px; border: none; border-radius: 4px; cursor: pointer; width: 100%; font-weight: bold; font-size: 0.95rem; margin-top: 5px; }
        button:hover { background-color: #219653; }
        .btn-blue { background-color: #2980b9; margin-top: 10px; }
        .btn-blue:hover { background-color: #1f618d; }
        .btn-orange { background-color: #d35400; margin-bottom: 10px; }
        .btn-orange:hover { background-color: #b94000; }
        pre { background: #f1f1f1; padding: 10px; border-radius: 4px; white-space: pre-wrap; word-wrap: break-word; font-family: Arial, sans-serif; font-size: 0.8rem; border: 1px solid #ddd; }
        fieldset { border: 1px solid #ddd; border-radius: 6px; padding: 8px; margin-bottom: 10px; }
        legend { font-weight: bold; font-size: 0.85rem; color: #2980b9; }
        .loading { display: none; text-align: center; color: #e67e22; font-weight: bold; margin-top: 8px; }
        
        /* Styling Tabel Input */
        .table-input { width: 100%; border-collapse: collapse; margin-bottom: 5px; font-size: 0.8rem; }
        .table-input th { background-color: #16a085; color: white; padding: 6px 4px; text-align: center; border: 1px solid #1abc9c; }
        .table-input td { padding: 4px; border: 1px solid #ddd; text-align: center; }
        .table-input input { text-align: center; margin-bottom: 0; padding: 5px; font-size: 0.85rem; }
        .table-input td:first-child { text-align: left; font-weight: bold; padding-left: 6px; color: #2c3e50; }
    </style>
</head>
<body>

    <h1>Input Report Sales & Rekap Area</h1>

    <div class="card">
        <label for="modeReport">Pilih Jenis Laporan:</label>
        <select id="modeReport" onchange="toggleMode()">
            <option value="single">1. Laporan Per Toko (Shift)</option>
            <option value="rekap">2. Rekap Gabungan 20 Toko Area</option>
        </select>

        <div class="row-group">
            <div>
                <label for="periode">Periode:</label>
                <input type="date" id="periode" onchange="hitungOtomatisSingle()">
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

        <div id="singleStoreSection">
            <label for="selectStore">Pilih Toko:</label>
            <select id="selectStore" onchange="gantiPilihanToko()">
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
    <div class="card" id="formPerToko">
        <fieldset>
            <legend>💰 REVENUE (Net Sales)</legend>
            <div class="row-group">
                <div><label>Time Factor (%):</label><input type="text" id="revTimeFactor" value="6,66%" oninput="hitungOtomatisSingle()"></div>
                <div><label>Actual (Rp):</label><input type="text" id="revActual" value="0" oninput="hitungOtomatisSingle()"></div>
            </div>
            <div class="row-group">
                <div><label>Target MTD (Rp):</label><input type="text" id="revTargetMtd" value="0" oninput="hitungOtomatisSingle()"></div>
                <div><label>Target TF (Rp) - Auto:</label><input type="text" id="revTargetTf" value="0" readonly style="background-color: #e9ecef;"></div>
            </div>
            <div class="row-group">
                <div><label>Ach MTD (%):</label><input type="text" id="revAchMtd" value="0%" readonly style="background-color: #e9ecef;"></div>
                <div><label>Ach TF (%):</label><input type="text" id="revAchTf" value="0%" readonly style="background-color: #e9ecef;"></div>
            </div>
            <div class="row-group">
                <div><label>GAP to Target (Rp):</label><input type="text" id="revGapTarget" value="0" readonly style="background-color: #e9ecef;"></div>
                <div><label>GAP to TF (Rp):</label><input type="text" id="revGapTf" value="0" readonly style="background-color: #e9ecef;"></div>
            </div>
        </fieldset>

        <fieldset>
            <legend>FOKUS CABANG</legend>
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
                    <tr><td>TEBUS MURAH</td><td><input type="text" id="fokus1_t" value="0"></td><td><input type="text" id="fokus1_s" value="0"></td><td><input type="text" id="fokus1_p" value="0%"></td></tr>
                    <tr><td>SERBA GRATIS</td><td><input type="text" id="fokus2_t" value="0"></td><td><input type="text" id="fokus2_s" value="0"></td><td><input type="text" id="fokus2_p" value="0%"></td></tr>
                    <tr><td>SUEUGEER</td><td><input type="text" id="fokus3_t" value="0"></td><td><input type="text" id="fokus3_s" value="0"></td><td><input type="text" id="fokus3_p" value="0%"></td></tr>
                    <tr><td>PROMO CEBAN</td><td><input type="text" id="fokus4_t" value="0"></td><td><input type="text" id="fokus4_s" value="0"></td><td><input type="text" id="fokus4_p" value="0%"></td></tr>
                </tbody>
            </table>
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
            <legend>PSM (Product Sales Mission)</legend>
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
                    <tr><td>Bango</td><td><input type="text" id="psm1_t" value="0"></td><td><input type="text" id="psm1_a" value="0"></td><td><input type="text" id="psm1_p" value="0%"></td></tr>
                    <tr><td>Daia</td><td><input type="text" id="psm2_t" value="0"></td><td><input type="text" id="psm2_a" value="0"></td><td><input type="text" id="psm2_p" value="0%"></td></tr>
                    <tr><td>Enaak</td><td><input type="text" id="psm3_t" value="0"></td><td><input type="text" id="psm3_a" value="0"></td><td><input type="text" id="psm3_p" value="0%"></td></tr>
                    <tr><td>Garnier</td><td><input type="text" id="psm4_t" value="0"></td><td><input type="text" id="psm4_a" value="0"></td><td><input type="text" id="psm4_p" value="0%"></td></tr>
                    <tr><td>Le mineral</td><td><input type="text" id="psm5_t" value="0"></td><td><input type="text" id="psm5_a" value="0"></td><td><input type="text" id="psm5_p" value="0%"></td></tr>
                    <tr><td>Lifebuoy</td><td><input type="text" id="psm6_t" value="0"></td><td><input type="text" id="psm6_a" value="0"></td><td><input type="text" id="psm6_p" value="0%"></td></tr>
                    <tr><td>Nipis madu</td><td><input type="text" id="psm7_t" value="0"></td><td><input type="text" id="psm7_a" value="0"></td><td><input type="text" id="psm7_p" value="0%"></td></tr>
                    <tr><td>Taro</td><td><input type="text" id="psm8_t" value="0"></td><td><input type="text" id="psm8_a" value="0"></td><td><input type="text" id="psm8_p" value="0%"></td></tr>
                    <tr>
                        <td><input type="text" id="psm9_name" placeholder="Item Lainnya..." style="text-align: left;"></td>
                        <td><input type="text" id="psm9_t" value="0"></td>
                        <td><input type="text" id="psm9_a" value="0"></td>
                        <td><input type="text" id="psm9_p" value="0%"></td>
                    </tr>
                </tbody>
            </table>
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

        <button onclick="processData('single')">Generate & Simpan Data Toko</button>
    </div>

    <!-- INPUT REKAP 20 TOKO -->
    <div class="card" id="formRekapArea" style="display:none;">
        <button class="btn-orange" onclick="hitungRekapOtomatis()">⚡ Hitung Rekap Otomatis dari Data 20 Toko</button>
        
        <fieldset>
            <legend>REVENUE REKAP AREA</legend>
            <div class="row-group">
                <div><label>Time Factor (%):</label><input type="text" id="rekTimeFactor" value="6,66%"></div>
                <div><label>Actual:</label><input type="text" id="rekActual" value="0"></div>
            </div>
            <div class="row-group">
                <div><label>Target MTD:</label><input type="text" id="rekTargetMtd" value="0"></div>
                <div><label>Target Time Factor:</label><input type="text" id="rekTargetTf" value="0"></div>
            </div>
            <div class="row-group">
                <div><label>Achievement MTD (%):</label><input type="text" id="rekAchMtd" value="0%"></div>
                <div><label>Achievement Time Factor (%):</label><input type="text" id="rekAchTf" value="0%"></div>
            </div>
            <div class="row-group">
                <div><label>Gap to Target:</label><input type="text" id="rekGapTarget" value="0"></div>
                <div><label>Gap to Time Factor:</label><input type="text" id="rekGapTf" value="0"></div>
            </div>
        </fieldset>

        <fieldset>
            <legend>FOKUS CABANG REKAP</legend>
            <label>1. Tebus Murah:</label><input type="text" id="rfokus1" value="0/0/0%">
            <label>2. Serba Gratis:</label><input type="text" id="rfokus2" value="0/0/0%">
            <label>3. Sueuger:</label><input type="text" id="rfokus3" value="0/0/0%">
            <label>4. Promo Ceban:</label><input type="text" id="rfokus4" value="0/0/0%">
            <label>5. PSM:</label><input type="text" id="rfokus5" value="0/0/0%">
        </fieldset>

        <fieldset>
            <legend>MEMBER REKAP</legend>
            <label>1. Actual New Member:</label><input type="text" id="rmemberNew" value="0/0/0%">
            <label>2. Kontribusi Struk Member:</label><input type="text" id="rmemberStruk" value="0/0/0%">
        </fieldset>

        <fieldset>
            <legend>CATEGORY REKAP</legend>
            <label>1. Toys (NS):</label><input type="text" id="rcat1" value="0/0/0%">
            <label>2. HBPL (NS):</label><input type="text" id="rcat2" value="0/0/0%">
        </fieldset>

        <fieldset>
            <legend>E-COMMERCE REKAP</legend>
            <label>Fee Base (Rp):</label><input type="text" id="rFeeBase" value="0">
        </fieldset>

        <button onclick="processData('rekap')">Generate Rekap & Kirim ke Cloud</button>
    </div>

    <div class="card">
        <label>Hasil Format WhatsApp:</label>
        <pre id="outputResult"></pre>
        <div id="loadingStatus" class="loading">Sedang mengirim data ke Cloud Google Sheets...</div>
        <button class="btn-blue" onclick="copyResult()">Salin Teks WhatsApp</button>
    </div>

    <script>
        document.getElementById('periode').value = '2026-09-02';
        const WEB_APP_URL = "https://script.google.com/macros/s/AKfycbzgTnGqr8MIEnz-mvl4s_kDpEp_9IssduKsGswjCM1XYhvUHM8FqGsUFuPLRLxmcbvp/exec";

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

        function formatDateID(dateString) {
            if (!dateString) return '';
            const parts = dateString.split('-');
            if (parts.length === 3) {
                const months = {
                    '01': 'JANUARI', '02': 'FEBRUARI', '03': 'MARET', '04': 'APRIL',
                    '05': 'MEI', '06': 'JUNI', '07': 'JULI', '08': 'AGUSTUS',
                    '09': 'SEPTEMBER', '10': 'OKTOBER', '11': 'NOVEMBER', '12': 'DESEMBER'
                };
                return parts[2] + ' ' + (months[parts[1]] || parts[1]) + ' ' + parts[0];
            }
            return dateString;
        }

        function parseNum(val) {
            if (!val) return 0;
            return parseFloat(val.toString().replace(/\./g, '').replace(/,/g, '.')) || 0;
        }

        function formatNum(num) {
            return Math.round(num).toLocaleString('id-ID');
        }

        // Mengubah target MTD otomatis saat toko dipilih
        function gantiPilihanToko() {
            const select = document.getElementById('selectStore');
            const selectedOption = select.options[select.selectedIndex];
            const targetMtd = selectedOption.getAttribute('data-target') || '0';
            
            document.getElementById('revTargetMtd').value = formatNum(parseInt(targetMtd, 10));
            
            // Kosongkan nilai Actual dan lainnya agar bersih dari data sebelumnya
            document.getElementById('revActual').value = '0';
            document.getElementById('fokus1_t').value = '0'; document.getElementById('fokus1_s').value = '0';
            document.getElementById('fokus2_t').value = '0'; document.getElementById('fokus2_s').value = '0';
            document.getElementById('fokus3_t').value = '0'; document.getElementById('fokus3_s').value = '0';
            document.getElementById('fokus4_t').value = '0'; document.getElementById('fokus4_s').value = '0';
            document.getElementById('memberNew').value = '0';
            document.getElementById('memberStruk').value = '0';
            document.getElementById('totalStruk').value = '0';
            document.getElementById('cat1').value = '0';
            document.getElementById('cat2').value = '0';
            document.getElementById('feeBase').value = '0';

            hitungOtomatisSingle();
        }

        function hitungOtomatisSingle() {
            const tglVal = document.getElementById('periode').value;
            let hariKe = 2;
            if (tglVal) {
                const parts = tglVal.split('-');
                if (parts.length === 3) hariKe = parseInt(parts[2], 10) || 1;
            }

            const tfPersenInput = parseNum(document.getElementById('revTimeFactor').value);
            const targetMtd = parseNum(document.getElementById('revTargetMtd').value);
            const actual = parseNum(document.getElementById('revActual').value);

            const multiplierTf = (tfPersenInput / 100) * hariKe;
            const targetTf = Math.round(targetMtd * multiplierTf);

            const achMtd = targetMtd > 0 ? ((actual / targetMtd) * 100).toFixed(1).replace('.', ',') + '%' : '0%';
            const achTf = targetTf > 0 ? ((actual / targetTf) * 100).toFixed(1).replace('.', ',') + '%' : '0%';
            
            const gapTarget = targetMtd - actual;
            const gapTf = targetTf - actual;

            document.getElementById('revTargetTf').value = formatNum(targetTf);
            document.getElementById('revAchMtd').value = achMtd;
            document.getElementById('revAchTf').value = achTf;
            document.getElementById('revGapTarget').value = formatNum(gapTarget);
            document.getElementById('revGapTf').value = formatNum(gapTf);
        }

        function simpanDataTokoAktif() {
            const storeKey = document.getElementById('selectStore').value;
            const dataToko = {
                targetMtd: parseNum(document.getElementById('revTargetMtd').value),
                targetTf: parseNum(document.getElementById('revTargetTf').value),
                actual: parseNum(document.getElementById('revActual').value),
                
                f1_t: parseNum(document.getElementById('fokus1_t').value),
                f1_s: parseNum(document.getElementById('fokus1_s').value),
                f2_t: parseNum(document.getElementById('fokus2_t').value),
                f2_s: parseNum(document.getElementById('fokus2_s').value),
                f3_t: parseNum(document.getElementById('fokus3_t').value),
                f3_s: parseNum(document.getElementById('fokus3_s').value),
                f4_t: parseNum(document.getElementById('fokus4_t').value),
                f4_s: parseNum(document.getElementById('fokus4_s').value),

                psm_t: (parseNum(document.getElementById('psm1_t').value) + parseNum(document.getElementById('psm2_t').value) + parseNum(document.getElementById('psm3_t').value) + parseNum(document.getElementById('psm4_t').value) + parseNum(document.getElementById('psm5_t').value) + parseNum(document.getElementById('psm6_t').value) + parseNum(document.getElementById('psm7_t').value) + parseNum(document.getElementById('psm8_t').value)),
                psm_a: (parseNum(document.getElementById('psm1_a').value) + parseNum(document.getElementById('psm2_a').value) + parseNum(document.getElementById('psm3_a').value) + parseNum(document.getElementById('psm4_a').value) + parseNum(document.getElementById('psm5_a').value) + parseNum(document.getElementById('psm6_a').value) + parseNum(document.getElementById('psm7_a').value) + parseNum(document.getElementById('psm8_a').value)),

                mNew: parseNum(document.getElementById('memberNew').value),
                mStruk: parseNum(document.getElementById('memberStruk').value),
                tStruk: parseNum(document.getElementById('totalStruk').value),

                cat1: parseNum(document.getElementById('cat1').value),
                cat2: parseNum(document.getElementById('cat2').value),
                feeBase: parseNum(document.getElementById('feeBase').value)
            };
            localStorage.setItem('toko_' + storeKey, JSON.stringify(dataToko));
        }

        function hitungRekapOtomatis() {
            let totTargetMtd = 0, totTargetTf = 0, totActual = 0;
            let f1_t = 0, f1_s = 0, f2_t = 0, f2_s = 0, f3_t = 0, f3_s = 0, f4_t = 0, f4_s = 0;
            let psm_t = 0, psm_a = 0;
            let mNew = 0, mStruk = 0, tStruk = 0;
            let cat1 = 0, cat2 = 0, feeBase = 0;
            let countTersimpan = 0;

            const selectOptions = document.getElementById('selectStore').options;
            for (let i = 0; i < selectOptions.length; i++) {
                const key = 'toko_' + selectOptions[i].value;
                const saved = localStorage.getItem(key);
                if (saved) {
                    countTersimpan++;
                    const d = JSON.parse(saved);
                    totTargetMtd += d.targetMtd;
                    totTargetTf += d.targetTf;
                    totActual += d.actual;
                    f1_t += d.f1_t; f1_s += d.f1_s;
                    f2_t += d.f2_t; f2_s += d.f2_s;
                    f3_t += d.f3_t; f3_s += d.f3_s;
                    f4_t += d.f4_t; f4_s += d.f4_s;
                    psm_t += d.psm_t; psm_a += d.psm_a;
                    mNew += d.mNew; mStruk += d.mStruk; tStruk += d.tStruk;
                    cat1 += d.cat1; cat2 += d.cat2; feeBase += d.feeBase;
                }
            }

            if (countTersimpan === 0) {
                alert("Belum ada data toko yang disimpan! Silakan isi dan klik 'Generate & Simpan Data Toko' minimal untuk beberapa toko terlebih dahulu.");
                return;
            }

            const achMtd = totTargetMtd > 0 ? ((totActual / totTargetMtd) * 100).toFixed(1).replace('.', ',') + '%' : '0%';
            const achTf = totTargetTf > 0 ? ((totActual / totTargetTf) * 100).toFixed(1).replace('.', ',') + '%' : '0%';
            const gapTarget = totTargetMtd - totActual;
            const gapTf = totTargetTf - totActual;

            document.getElementById('rekTargetMtd').value = formatNum(totTargetMtd);
            document.getElementById('rekTargetTf').value = formatNum(totTargetTf);
            document.getElementById('rekActual').value = formatNum(totActual);
            document.getElementById('rekAchMtd').value = achMtd;
            document.getElementById('rekAchTf').value = achTf;
            document.getElementById('rekGapTarget').value = formatNum(gapTarget);
            document.getElementById('rekGapTf').value = formatNum(gapTf);

            document.getElementById('rfokus1').value = `${f1_t}/${f1_s}/${f1_t > 0 ? Math.round((f1_s/f1_t)*100) : 0}%`;
            document.getElementById('rfokus2').value = `${f2_t}/${f2_s}/${f2_t > 0 ? Math.round((f2_s/f2_t)*100) : 0}%`;
            document.getElementById('rfokus3').value = `${f3_t}/${f3_s}/${f3_t > 0 ? Math.round((f3_s/f3_t)*100) : 0}%`;
            document.getElementById('rfokus4').value = `${f4_t}/${f4_s}/${f4_t > 0 ? Math.round((f4_s/f4_t)*100) : 0}%`;
            document.getElementById('rfokus5').value = `${psm_t}/${psm_a}/${psm_t > 0 ? Math.round((psm_a/psm_t)*100) : 0}%`;

            document.getElementById('rmemberNew').value = `${mNew}/0/0%`;
            document.getElementById('rmemberStruk').value = `${tStruk}/${mStruk}/${tStruk > 0 ? Math.round((mStruk/tStruk)*100) : 0}%`;

            document.getElementById('rcat1').value = `${cat1}/0/0%`;
            document.getElementById('rcat2').value = `${cat2}/0/0%`;

            document.getElementById('rFeeBase').value = formatNum(feeBase);

            alert(`Berhasil merangkum data dari ${countTersimpan} toko yang sudah diisi!`);
        }

        function getVal(id) {
            return document.getElementById(id) ? document.getElementById(id).value : '';
        }

        function processData(type) {
            const periodeRaw = getVal('periode');
            const periode = formatDateID(periodeRaw);
            const wh = getVal('wh');
            const am = getVal('am');
            const ac = getVal('ac');
            
            let text = "";
            let jenisLaporan = "";
            let kodeToko = "-";
            let namaToko = "-";
            let shiftInfo = "-";

            if (type === 'single') {
                simpanDataTokoAktif();
                const shift = getVal('shift');
                const storeVal = getVal('selectStore').split('|');
                kodeToko = storeVal[0];
                namaToko = storeVal[1];
                jenisLaporan = "Laporan Per Toko (Shift)";
                shiftInfo = "Shift " + shift;

                const f1 = `${getVal('fokus1_t')}/${getVal('fokus1_s')}/${getVal('fokus1_p')}`;
                const f2 = `${getVal('fokus2_t')}/${getVal('fokus2_s')}/${getVal('fokus2_p')}`;
                const f3 = `${getVal('fokus3_t')}/${getVal('fokus3_s')}/${getVal('fokus3_p')}`;
                const f4 = `${getVal('fokus4_t')}/${getVal('fokus4_s')}/${getVal('fokus4_p')}`;

                const p1 = `${getVal('psm1_t')} - ${getVal('psm1_a')} - ${getVal('psm1_p')}`;
                const p2 = `${getVal('psm2_t')} - ${getVal('psm2_a')} - ${getVal('psm2_p')}`;
                const p3 = `${getVal('psm3_t')} - ${getVal('psm3_a')} - ${getVal('psm3_p')}`;
                const p4 = `${getVal('psm4_t')} - ${getVal('psm4_a')} - ${getVal('psm4_p')}`;
                const p5 = `${getVal('psm5_t')} - ${getVal('psm5_a')} - ${getVal('psm5_p')}`;
                const p6 = `${getVal('psm6_t')} - ${getVal('psm6_a')} - ${getVal('psm6_p')}`;
                const p7 = `${getVal('psm7_t')} - ${getVal('psm7_a')} - ${getVal('psm7_p')}`;
                const p8 = `${getVal('psm8_t')} - ${getVal('psm8_a')} - ${getVal('psm8_p')}`;
                
                let p9Text = "";
                const p9NameVal = getVal('psm9_name');
                if (p9NameVal) {
                    p9Text = `\n9. ${p9NameVal.toUpperCase()}: ${getVal('psm9_t')} - ${getVal('psm9_a')} - ${getVal('psm9_p')}`;
                }

                const mNew = getVal('memberNew');
                const mStruk = getVal('memberStruk');
                const tStruk = getVal('totalStruk');
                const mPersen = Math.round((mStruk/(tStruk||1))*100);

                text = `*REPORT SALES SHIFT ${shift}*\n` +
                       `PERIODE : ${periode}\n` +
                       `WH : ${wh}\n` +
                       `AM : ${am}\n` +
                       `AC : ${ac}\n` +
                       `KD Toko : ${kodeToko}\n` +
                       `Nama Toko : ${namaToko}\n` +
                       `Shift : ${shift}\n` +
                       `======================\n` +
                       `*REVENUE*\n` +
                       `1. NET SALES\n` +
                       `- Time factor : ${getVal('revTimeFactor')}\n` +
                       `- TARGET  MTD : ${getVal('revTargetMtd')}\n` +
                       `- Target Time Factor: ${getVal('revTargetTf')}\n` +
                       `- ACTUAL : ${getVal('revActual')}\n` +
                       `- ACHIVE MTD : ${getVal('revAchMtd')}\n` +
                       `- AChieved Time Factor : ${getVal('revAchTf')}\n` +
                       `- GAP TO TARGET : ${getVal('revGapTarget')}\n` +
                       `- GAP To Time Factor: ${getVal('revGapTf')}\n` +
                       `*FOKUS CABANG*\n` +
                       `======================\n` +
                       ` TARGET/SALES/\tACV%\n` +
                       `1. TEBUS MURAH (QTY REDEEM)\t: ${f1}\n` +
                       `2. SERBA GRATIS (PAKET)\t: ${f2}\n` +
                       `3. SUEGER\t: ${f3}\n` +
                       `4. PROMO CEBAN\t: ${f4}\n` +
                       `*MEMBER*\n` +
                       `1. Actual NEW MEMBER : ${mNew}/0/0%\n` +
                       `2. Konstribusi struk Member : ${tStruk}/${mStruk}/${mPersen}%\n` +
                       `======================\n` +
                       `*PSM*\n` +
                       `(In Qty).( Target - actual - %)\n` +
                       `1. BANGO: ${p1}\n` +
                       `2. DAIA: ${p2}\n` +
                       `3. ENAKK: ${p3}\n` +
                       `4. GARNIER: ${p4}\n` +
                       `5. LE MINERALE: ${p5}\n` +
                       `6. LIFEBUOY: ${p6}\n` +
                       `7. NIPIS MADU: ${p7}\n` +
                       `8. TARO: ${p8}` + p9Text + `\n` +
                       `======================\n` +
                       `*CATEGORY*\t(Rupiah)\n` +
                       `( Sales )\n` +
                       `1. TOYS (NS): ${getVal('cat1')}\n` +
                       `2. HBPL (NS): ${getVal('cat2')}\n` +
                       `======================\n` +
                       `*E-COMMERCE*\n` +
                       `1. FEE BASE (RP)\t: ${getVal('feeBase')}\n` +
                       `Terimakasih`;
            } else {
                jenisLaporan = "Rekap Gabungan 20 Toko Area";
                shiftInfo = "All Area";

                text = `*REPORT SALES*\n` +
                       `PERIODE : ${periode}\n` +
                       `WH : ${wh}\n` +
                       `AM : ${am}\n` +
                       `AC  : ${ac}\n` +
                       `======================\n` +
                       `*REVENUE*\n` +
                       `1. NET SALES\t\n` +
                       `- Time factor : ${getVal('rekTimeFactor')}\n` +
                       `- TARGET  MTD : ${getVal('rekTargetMtd')}\n` +
                       `- Target Time Factor : ${getVal('rekTargetTf')}\n` +
                       `- ACTUAL : ${getVal('rekActual')}\n` +
                       `- ACHIVE MTD :${getVal('rekAchMtd')}\n` +
                       `- Achieved Time Factor :${getVal('rekAchTf')}\n` +
                       `- GAP TO TARGET : ${getVal('rekGapTarget')}\n` +
                       `- GAP To Time Factor : ${getVal('rekGapTf')}\n` +
                       `======================\n` +
                       `*FOKUS CABANG*\n` +
                       `\tTARGET/SALES/\tACV%\n` +
                       `1. \tTEBUS MURAH (QTY REDEEM) : ${getVal('rfokus1')}\n` +
                       `2. \tSERBA GRATIS (PAKET) : ${getVal('rfokus2')}\n` +
                       `3. SEUUGER : ${getVal('rfokus3')}\n` +
                       `4. PROMO CEBAN : ${getVal('rfokus4')}\n` +
                       `5. PSM : ${getVal('rfokus5')}\n` +
                       `*MEMBER*\n` +
                       `1. \tActual NEW MEMBER :\t${getVal('rmemberNew')}\n` +
                       `2. \tKonstribusi struk Member \t: ( Struk MEMBER : Total struk :${getVal('rmemberStruk')}\n` +
                       `*CATEGORY*\t(Rupiah)\n` +
                       `( Sales )\n` +
                       `1. \tTOYS (NS)\t : ${getVal('rcat1')}\n` +
                       `2. TELUR : ${getVal('rcat2')}\n` +
                       `======================\n` +
                       `*E-COMMERCE*\n` +
                       `1. \tFEE BASE (RP)\t : ${getVal('rFeeBase')}\n` +
                       `Terimakasih`;
            }

            document.getElementById('outputResult').innerText = text;

            document.getElementById('loadingStatus').style.display = 'block';

            const payload = {
                jenisLaporan: jenisLaporan,
                kodeToko: kodeToko,
                namaToko: namaToko,
                periode: periode,
                shiftInfo: shiftInfo,
                hasilText: text
            };

            fetch(WEB_APP_URL, {
                method: 'POST',
                mode: 'no-cors',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify(payload)
            })
            .then(() => {
                document.getElementById('loadingStatus').style.display = 'none';
                alert("Report berhasil digenerate dan data otomatis tersimpan aman di Cloud Google Sheets!");
            })
            .catch((error) => {
                document.getElementById('loadingStatus').style.display = 'none';
                alert("Gagal mengirim ke cloud: " + error);
            });
        }

        function copyResult() {
            const text = document.getElementById('outputResult').innerText;
            navigator.clipboard.writeText(text).then(() => {
                alert('Teks format WhatsApp berhasil disalin!');
            });
        }

        window.onload = function() {
            gantiPilihanToko(); // Set target awal sesuai toko pertama
        };
    </script>
</body>
</html>
