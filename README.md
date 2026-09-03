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
                <input type="date" id="periode">
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
            <select id="selectStore">
                <option value="C624|ROWOSARI (RWBT)">C624 - RWBT</option>
                <option value="C560|RAJ">C560 - RAJ</option>
                <option value="CH81|CDKS">CH81 - CDKS</option>
                <option value="CG76|SPMM">CG76 - SPMM</option>
                <option value="C573|GMM">C573 - GMM</option>
                <option value="CE47|MKRI">CE47 - MKRI</option>
                <option value="CI30|STTD">CI30 - STTD</option>
                <option value="CH41|KPMRK">CH41 - KPMRK</option>
                <option value="CG54|MM21">CG54 - MM21</option>
                <option value="C935|TLJ2">C935 - TLJ2</option>
                <option value="CA71|WSGN">CA71 - WSGN</option>
                <option value="C965|CIBUNTU (CBNU)">C965 - CBNU</option>
                <option value="CG86|JKST">CG86 - JKST</option>
                <option value="CA94|KPTI">CA94 - KPTI</option>
                <option value="C574|SKU">C574 - SKU</option>
                <option value="CI15|RPSU">CI15 - RPSU</option>
                <option value="CI54|RJLB">CI54 - RJLB</option>
                <option value="CF50|DNIA">CF50 - DNIA</option>
                <option value="CC21|KUTN">CC21 - KUTN</option>
                <option value="CI84|TLKW">CI84 - TLKW</option>
            </select>
        </div>
    </div>

    <!-- INPUT DETAIL PER TOKO -->
    <div class="card" id="formPerToko">
        <fieldset>
            <legend>REVENUE</legend>
            <label>Time Factor (%):</label><input type="text" id="revTimeFactor" value="6,66%">
            <label>Target MTD:</label><input type="text" id="revTargetMtd" value="453.303.178">
            <label>Target Time Factor:</label><input type="text" id="revTargetTf" value="15.009.307">
            <label>Actual:</label><input type="text" id="revActual" value="13.332.882">
            <label>Achievement MTD (%):</label><input type="text" id="revAchMtd" value="89%">
            <label>Achievement Time Factor (%):</label><input type="text" id="revAchTf" value="6,1%">
            <label>Gap to Target:</label><input type="text" id="revGapTarget" value="15.122.266">
            <label>Gap to Time Factor:</label><input type="text" id="revGapTf" value="423.432.458">
        </fieldset>

        <fieldset>
            <legend>FOKUS CABANG</legend>
            <table class="table-input">
                <thead>
                    <tr>
                        <th style="width: 37%;">Nama Program</th>
                        <th style="width: 21%;">Target</th>
                        <th style="width: 21%;">Sales</th>
                        <th style="width: 21%;">OnHand</th>
                    </tr>
                </thead>
                <tbody>
                    <tr><td>TEBUS MURAH</td><td><input type="text" id="fokus1_t" value="23"></td><td><input type="text" id="fokus1_s" value="30"></td><td><input type="text" id="fokus1_oh" value="0"></td></tr>
                    <tr><td>SERBA GRATIS</td><td><input type="text" id="fokus2_t" value="14"></td><td><input type="text" id="fokus2_s" value="6"></td><td><input type="text" id="fokus2_oh" value="0"></td></tr>
                    <tr><td>SUEUGEER</td><td><input type="text" id="fokus3_t" value="68"></td><td><input type="text" id="fokus3_s" value="19"></td><td><input type="text" id="fokus3_oh" value="0"></td></tr>
                    <tr><td>PROMO CEBAN</td><td><input type="text" id="fokus4_t" value="278"></td><td><input type="text" id="fokus4_s" value="0"></td><td><input type="text" id="fokus4_oh" value="0"></td></tr>
                </tbody>
            </table>
        </fieldset>

        <fieldset>
            <legend>MEMBER & STRUK</legend>
            <div class="row-group">
                <div>
                    <label>Actual New Member:</label>
                    <input type="text" id="memberNew" value="2">
                </div>
                <div>
                    <label>Struk Member:</label>
                    <input type="text" id="memberStruk" value="123">
                </div>
                <div>
                    <label>Total Struk:</label>
                    <input type="text" id="totalStruk" value="279">
                </div>
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
                    <tr><td>Bango</td><td><input type="text" id="psm1_t" value="22"></td><td><input type="text" id="psm1_a" value="1"></td><td><input type="text" id="psm1_p" value="5%"></td></tr>
                    <tr><td>Daia</td><td><input type="text" id="psm2_t" value="52"></td><td><input type="text" id="psm2_a" value="4"></td><td><input type="text" id="psm2_p" value="8%"></td></tr>
                    <tr><td>Enaak</td><td><input type="text" id="psm3_t" value="39"></td><td><input type="text" id="psm3_a" value="0"></td><td><input type="text" id="psm3_p" value="0%"></td></tr>
                    <tr><td>Garnier</td><td><input type="text" id="psm4_t" value="31"></td><td><input type="text" id="psm4_a" value="1"></td><td><input type="text" id="psm4_p" value="3%"></td></tr>
                    <tr><td>Le mineral</td><td><input type="text" id="psm5_t" value="265"></td><td><input type="text" id="psm5_a" value="15"></td><td><input type="text" id="psm5_p" value="6%"></td></tr>
                    <tr><td>Lifebuoy</td><td><input type="text" id="psm6_t" value="24"></td><td><input type="text" id="psm6_a" value="2"></td><td><input type="text" id="psm6_p" value="8%"></td></tr>
                    <tr><td>Nipis madu</td><td><input type="text" id="psm7_t" value="139"></td><td><input type="text" id="psm7_a" value="7"></td><td><input type="text" id="psm7_p" value="5%"></td></tr>
                    <tr><td>Taro</td><td><input type="text" id="psm8_t" value="59"></td><td><input type="text" id="psm8_a" value="4"></td><td><input type="text" id="psm8_p" value="7%"></td></tr>
                    <!-- Baris Tambahan Kosong -->
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
            <label>Fee Base (Rp):</label><input type="text" id="feeBase" value="250.000">
        </fieldset>

        <button onclick="processData('single')">Generate & Kirim ke Cloud</button>
    </div>

    <!-- INPUT REKAP 20 TOKO -->
    <div class="card" id="formRekapArea" style="display:none;">
        <fieldset>
            <legend>REVENUE REKAP AREA</legend>
            <label>Time Factor (%):</label><input type="text" id="rekTimeFactor" value="6,6%">
            <label>Target MTD:</label><input type="text" id="rekTargetMtd" value="6.596.440.254">
            <label>Target Time Factor:</label><input type="text" id="rekTargetTf" value="435.365.057">
            <label>Actual:</label><input type="text" id="rekActual" value="233.124.210">
            <label>Achievement MTD (%):</label><input type="text" id="rekAchMtd" value="3,53%">
            <label>Achievement Time Factor (%):</label><input type="text" id="rekAchTf" value="53,56%">
            <label>Gap to Target:</label><input type="text" id="rekGapTarget" value="6.363.316.044">
            <label>Gap to Time Factor:</label><input type="text" id="rekGapTf" value="202.240.847">
        </fieldset>

        <fieldset>
            <legend>FOKUS CABANG REKAP</legend>
            <label>1. Tebus Murah:</label><input type="text" id="rfokus1" value="412/237/57%">
            <label>2. Serba Gratis:</label><input type="text" id="rfokus2" value="288/129/45%">
            <label>3. Sueuger:</label><input type="text" id="rfokus3" value="826/256/31%">
            <label>4. Promo Ceban:</label><input type="text" id="rfokus4" value="1.322/22/2%">
            <label>5. PSM:</label><input type="text" id="rfokus5" value="1.420/609/43%">
        </fieldset>

        <fieldset>
            <legend>MEMBER REKAP</legend>
            <label>1. Actual New Member:</label><input type="text" id="rmemberNew" value="39/10/26%">
            <label>2. Kontribusi Struk Member:</label><input type="text" id="rmemberStruk" value="1.868/1.156/64%">
        </fieldset>

        <fieldset>
            <legend>CATEGORY REKAP</legend>
            <label>1. Toys (NS):</label><input type="text" id="rcat1" value="39/6/15%">
            <label>2. Telur:</label><input type="text" id="rcat2" value="516/57/11%">
        </fieldset>

        <fieldset>
            <legend>E-COMMERCE REKAP</legend>
            <label>Fee Base (Rp):</label><input type="text" id="rFeeBase" value="4.320.700">
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
                const shift = getVal('shift');
                const storeVal = getVal('selectStore').split('|');
                kodeToko = storeVal[0];
                namaToko = storeVal[1];
                jenisLaporan = "Laporan Per Toko (Shift)";
                shiftInfo = "Shift " + shift;

                const f1 = `${getVal('fokus1_t')}/${getVal('fokus1_s')}/${Math.round((getVal('fokus1_s')/(getVal('fokus1_t')||1))*100)}%`;
                const f2 = `${getVal('fokus2_t')}/${getVal('fokus2_s')}/${Math.round((getVal('fokus2_s')/(getVal('fokus2_t')||1))*100)}%`;
                const f3 = `${getVal('fokus3_t')}/${getVal('fokus3_s')}/${Math.round((getVal('fokus3_s')/(getVal('fokus3_t')||1))*100)}%`;
                const f4 = `${getVal('fokus4_t')}/${getVal('fokus4_s')}/${Math.round((getVal('fokus4_s')/(getVal('fokus4_t')||1))*100)}%`;

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
                       `(In Qty).
