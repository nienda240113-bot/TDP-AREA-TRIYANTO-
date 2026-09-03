<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Report Sales Shift & Rekap 20 Toko</title>
    <style>
        body { font-family: Arial, sans-serif; line-height: 1.25; color: #333; max-width: 650px; margin: 0 auto; padding: 15px; background-color: #f4f6f9; }
        h1 { font-size: 1.2rem; color: #2c3e50; border-bottom: 2px solid #3498db; padding-bottom: 8px; text-align: center; }
        .card { background: #fff; padding: 15px; border-radius: 8px; box-shadow: 0 2px 4px rgba(0,0,0,0.1); margin-bottom: 15px; }
        label { display: block; margin-bottom: 5px; font-weight: bold; font-size: 0.85rem; }
        select, input { width: 100%; padding: 8px; margin-bottom: 10px; border: 1px solid #ccc; border-radius: 4px; box-sizing: border-box; }
        .row-group { display: flex; gap: 10px; }
        .row-group > div { flex: 1; }
        button { background-color: #27ae60; color: white; padding: 10px; border: none; border-radius: 4px; cursor: pointer; width: 100%; font-weight: bold; font-size: 0.95rem; margin-top: 5px; }
        button:hover { background-color: #219653; }
        .btn-blue { background-color: #2980b9; margin-top: 10px; }
        .btn-blue:hover { background-color: #1f618d; }
        pre { background: #f1f1f1; padding: 12px; border-radius: 4px; white-space: pre-wrap; word-wrap: break-word; font-family: Arial, sans-serif; font-size: 0.85rem; border: 1px solid #ddd; }
        fieldset { border: 1px solid #ddd; border-radius: 6px; padding: 10px; margin-bottom: 12px; }
        legend { font-weight: bold; font-size: 0.85rem; color: #2980b9; }
        .loading { display: none; text-align: center; color: #e67e22; font-weight: bold; margin-top: 8px; }
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
            <legend>FOKUS CABANG (Format: Target/Sales/ACV%)</legend>
            <label>1. Tebus Murah:</label><input type="text" id="fokus1" value="23/30/33%">
            <label>2. Serba Gratis:</label><input type="text" id="fokus2" value="14/6/43%">
            <label>3. Sueger:</label><input type="text" id="fokus3" value="68/19/28%">
            <label>4. Promo Ceban:</label><input type="text" id="fokus4" value="278/0/0">
        </fieldset>

        <fieldset>
            <legend>MEMBER</legend>
            <label>1. Actual New Member:</label><input type="text" id="memberNew" value="2/0/0%">
            <label>2. Kontribusi Struk Member:</label><input type="text" id="memberStruk" value="279/123/44%">
        </fieldset>

        <fieldset>
            <legend>PSM (Format: Target/Actual/%)</legend>
            <label>1. Bango:</label><input type="text" id="psm1" value="22/1/5%">
            <label>2. Daia:</label><input type="text" id="psm2" value="52/4/8%">
            <label>3. Enakk:</label><input type="text" id="psm3" value="39/0/0">
            <label>4. Garnier:</label><input type="text" id="psm4" value="31/1/3%">
            <label>5. Le Minerale:</label><input type="text" id="psm5" value="265/15/6%">
            <label>6. Lifebuoy:</label><input type="text" id="psm6" value="24/2/8%">
            <label>7. Nipis Madu:</label><input type="text" id="psm7" value="139/7/5%">
            <label>8. Taro:</label><input type="text" id="psm8" value="59/4/7%">
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
        
        // URL Web App Anda sudah terpasang otomatis di sini:
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

        function processData(type) {
            const periodeRaw = document.getElementById('periode').value;
            const periode = formatDateID(periodeRaw);
            const wh = document.getElementById('wh').value;
            const am = document.getElementById('am').value;
            const ac = document.getElementById('ac').value;
            
            let text = "";
            let jenisLaporan = "";
            let kodeToko = "-";
            let namaToko = "-";
            let shiftInfo = "-";

            if (type === 'single') {
                const shift = document.getElementById('shift').value;
                const storeVal = document.getElementById('selectStore').value.split('|');
                kodeToko = storeVal[0];
                namaToko = storeVal[1];
                jenisLaporan = "Laporan Per Toko (Shift)";
                shiftInfo = "Shift " + shift;

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
                       `- Time factor : ${document.getElementById('revTimeFactor').value}\n` +
                       `- TARGET  MTD : ${document.getElementById('revTargetMtd').value}\n` +
                       `- Target Time Factor: ${document.getElementById('revTargetTf').value}\n` +
                       `- ACTUAL : ${document.getElementById('revActual').value}\n` +
                       `- ACHIVE MTD : ${document.getElementById('revAchMtd').value}\n` +
                       `- AChieved Time Factor : ${document.getElementById('revAchTf').value}\n` +
                       `- GAP TO TARGET : ${document.getElementById('revGapTarget').value}\n` +
                       `- GAP To Time Factor: ${document.getElementById('revGapTf').value}\n` +
                       `*FOKUS CABANG*\n` +
                       `======================\n` +
                       ` TARGET/SALES/\tACV%\n` +
                       `1. TEBUS MURAH (QTY REDEEM)\t: ${document.getElementById('fokus1').value}\n` +
                       `2. SERBA GRATIS (PAKET)\t: ${document.getElementById('fokus2').value}\n` +
                       `3. SUEGER\t: ${document.getElementById('fokus3').value}\n` +
                       `4. PROMO CEBAN\t: ${document.getElementById('fokus4').value}\n` +
                       `*MEMBER*\n` +
                       `1. Actual NEW MEMBER : ${document.getElementById('memberNew').value}\n` +
                       `2. Konstribusi struk Member : ${document.getElementById('memberStruk').value}\n` +
                       `======================\n` +
                       `*PSM*\n` +
                       `(In Qty).( Target - actual - %)\n` +
                       `1. BANGO: ${document.getElementById('psm1').value}\n` +
                       `2. DAIA: ${document.getElementById('psm2').value}\n` +
                       `3. ENAKK: ${document.getElementById('psm3').value}\n` +
                       `4. GARNIER: ${document.getElementById('psm4').value}\n` +
                       `5. LE MINERALE: ${document.getElementById('psm5').value}\n` +
                       `6. LIFEBUOY: ${document.getElementById('psm6').value}\n` +
                       `7. NIPIS MADU: ${document.getElementById('psm7').value}\n` +
                       `8. TARO: ${document.getElementById('psm8').value}\n` +
                       `======================\n` +
                       `*CATEGORY*\t(Rupiah)\n` +
                       `( Sales )\n` +
                       `1. TOYS (NS): ${document.getElementById('cat1').value}\n` +
                       `2. HBPL (NS): ${document.getElementById('cat2').value}\n` +
                       `======================\n` +
                       `*E-COMMERCE*\n` +
                       `1. FEE BASE (RP)\t: ${document.getElementById('feeBase').value}\n` +
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
                       `- Time factor : ${document.getElementById('rekTimeFactor').value}\n` +
                       `- TARGET  MTD : ${document.getElementById('rekTargetMtd').value}\n` +
                       `- Target Time Factor : ${document.getElementById('rekTargetTf').value}\n` +
                       `- ACTUAL : ${document.getElementById('rekActual').value}\n` +
                       `- ACHIVE MTD :${document.getElementById('rekAchMtd').value}\n` +
                       `- Achieved Time Factor :${document.getElementById('rekAchTf').value}\n` +
                       `- GAP TO TARGET : ${document.getElementById('rekGapTarget').value}\n` +
                       `- GAP To Time Factor : ${document.getElementById('rekGapTf').value}\n` +
                       `======================\n` +
                       `*FOKUS CABANG*\n` +
                       `\tTARGET/SALES/\tACV%\n` +
                       `1. \tTEBUS MURAH (QTY REDEEM) : ${document.getElementById('rfokus1').value}\n` +
                       `2. \tSERBA GRATIS (PAKET) : ${document.getElementById('rfokus2').value}\n` +
                       `3. SEUUGER : ${document.getElementById('rfokus3').value}\n` +
                       `4. PROMO CEBAN : ${document.getElementById('rfokus4').value}\n` +
                       `5. PSM : ${document.getElementById('rfokus5').value}\n` +
                       `*MEMBER*\n` +
                       `1. \tActual NEW MEMBER :\t${document.getElementById('rmemberNew').value}\n` +
                       `2. \tKonstribusi struk Member \t: ( Struk MEMBER : Total struk :${document.getElementById('rmemberStruk').value}\n` +
                       `*CATEGORY*\t(Rupiah)\n` +
                       `( Sales )\n` +
                       `1. \tTOYS (NS)\t : ${document.getElementById('rcat1').value}\n` +
                       `2. TELUR : ${document.getElementById('rcat2').value}\n` +
                       `======================\n` +
                       `*E-COMMERCE*\n` +
                       `1. \tFEE BASE (RP)\t : ${document.getElementById('rFeeBase').value}\n` +
                       `Terimakasih`;
            }

            document.getElementById('outputResult').innerText = text;

            // Kirim otomatis ke Cloud Google Sheets
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
            processData('single');
        };
    </script>
</body>
</html>
