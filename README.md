        <div class="row-group">
            <div><label>Actual New Member:</label><input type="text" id="memberNew" value="0"></div>
            <div><label>Struk Member:</label><input type="text" id="memberStruk" value="0"></div>
            <div><label>Total Struk:</label><input type="text" id="totalStruk" value="0"></div>
        </div>
    </fieldset>

    <fieldset>
        <legend>PSM</legend>
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
                <tr><td><input type="text" id="psm1_name" value="BANGO" style="text-align: left; font-weight: bold;"></td><td><input type="text" id="psm1_t" value="0"></td><td><input type="text" id="psm1_a" value="0"></td><td><input type="text" id="psm1_p" value="0%"></td></tr>
                <tr><td><input type="text" id="psm2_name" value="DAIA" style="text-align: left; font-weight: bold;"></td><td><input type="text" id="psm2_t" value="0"></td><td><input type="text" id="psm2_a" value="0"></td><td><input type="text" id="psm2_p" value="0%"></td></tr>
                <tr><td><input type="text" id="psm3_name" value="ENAAK" style="text-align: left; font-weight: bold;"></td><td><input type="text" id="psm3_t" value="0"></td><td><input type="text" id="psm3_a" value="0"></td><td><input type="text" id="psm3_p" value="0%"></td></tr>
                <tr><td><input type="text" id="psm4_name" value="GARNIER" style="text-align: left; font-weight: bold;"></td><td><input type="text" id="psm4_t" value="0"></td><td><input type="text" id="psm4_a" value="0"></td><td><input type="text" id="psm4_p" value="0%"></td></tr>
                <tr><td><input type="text" id="psm5_name" value="LE MINERAL" style="text-align: left; font-weight: bold;"></td><td><input type="text" id="psm5_t" value="0"></td><td><input type="text" id="psm5_a" value="0"></td><td><input type="text" id="psm5_p" value="0%"></td></tr>
                <tr><td><input type="text" id="psm6_name" value="LIFEBUOY" style="text-align: left; font-weight: bold;"></td><td><input type="text" id="psm6_t" value="0"></td><td><input type="text" id="psm6_a" value="0"></td><td><input type="text" id="psm6_p" value="0%"></td></tr>
                <tr><td><input type="text" id="psm7_name" value="NIPIS MADU" style="text-align: left; font-weight: bold;"></td><td><input type="text" id="psm7_t" value="0"></td><td><input type="text" id="psm7_a" value="0"></td><td><input type="text" id="psm7_p" value="0%"></td></tr>
                <tr><td><input type="text" id="psm8_name" value="TARO" style="text-align: left; font-weight: bold;"></td><td><input type="text" id="psm8_t" value="0"></td><td><input type="text" id="psm8_a" value="0"></td><td><input type="text" id="psm8_p" value="0%"></td></tr>
                <tr>
                    <td><input type="text" id="psm9_name" value="" placeholder="Item Lainnya..." style="text-align: left; font-weight: bold;"></td>
                    <td><input type="text" id="psm9_t" value="0"></td>
                    <td><input type="text" id="psm9_a" value="0"></td>
                    <td><input type="text" id="psm9_p" value="0%"></td>
                </tr>
            </tbody>
        </table>
        <!-- Tombol simpan khusus PSM untuk toko yang sedang aktif -->
        <button class="btn-small" onclick="simpanBagianKhusus('psm')">💾 Simpan Target PSM Toko Ini</button>
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

<!-- INPUT REKAP 20 TOKO -->
<div class="card" id="formRekapArea" style="display:none;">
    <button class="btn-orange" onclick="hitungRekapOtomatis()">⚡ Hitung Rekap Otomatis</button>
    
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
    <div id="loadingStatus" class="loading">Sedang memproses data dengan Cloud...</div>
    <button class="btn-blue" onclick="copyResult()">Salin Teks WhatsApp</button>
</div>

<script>
    const WEB_APP_URL = "https://script.google.com/macros/s/AKfycbzgTnGqr8MIEnz-mvl4s_kDpEp_9IssduKsGswjCM1XYhvUHM8FqGsUFuPLRLxmcbvp/exec";

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

    // Fungsi vital: Otomatis menarik data spesifik milik toko & tanggal yang sedang dipilih dari Cloud
    function muatDataDariCloud() {
        const select = document.getElementById('selectStore');
        const selectedOption = select.options[select.selectedIndex];
        const kodeToko = select.value.split('|')[0];
        const tglVal = document.getElementById('periode').value;
        const defaultTargetMtd = selectedOption.getAttribute('data-target') || '0';

        document.getElementById('loadingStatus').innerText = "Memuat data " + kodeToko + " dari Cloud...";
        document.getElementById('loadingStatus').style.display = 'block';

        fetch(WEB_APP_URL + "?action=getData&periode=" + tglVal + "&kodeToko=" + kodeToko)
        .then(res => res.json())
        .then(d => {
            document.getElementById('loadingStatus').style.display = 'none';
            if (d && d.found) {
                // Jika data toko ini sudah pernah disimpan di cloud, tampilkan isinya
                document.getElementById('revTargetMtd').value = formatNum(d.targetMtd || parseInt(defaultTargetMtd, 10));
                document.getElementById('revActual').value = formatNum(d.actual || 0);

                document.getElementById('fokus1_t').value = d.f1_t || 0;
                document.getElementById('fokus1_s').value = d.f1_s || 0;
                document.getElementById('fokus2_t').value = d.f2_t || 0;
                document.getElementById('fokus2_s').value = d.f2_s || 0;
                document.getElementById('fokus3_t').value = d.f3_t || 0;
                document.getElementById('fokus3_s').value = d.f3_s || 0;
                document.getElementById('fokus4_t').value = d.f4_t || 0;
                document.getElementById('fokus4_s').value = d.f4_s || 0;

                for (let i = 1; i <= 9; i++) {
                    if (d['psm' + i + '_name']) document.getElementById('psm' + i + '_name').value = d['psm' + i + '_name'];
                    document.getElementById('psm' + i + '_t').value = d['psm' + i + '_t'] || 0;
                    document.getElementById('psm' + i + '_a').value = d['psm' + i + '_a'] || 0;
                }

                document.getElementById('memberNew').value = d.mNew || 0;
                document.getElementById('memberStruk').value = d.mStruk || 0;
                document.getElementById('totalStruk').value = d.tStruk || 0;
                document.getElementById('cat1').value = d.cat1 || 0;
                document.getElementById('cat2').value = d.cat2 || 0;
                document.getElementById('feeBase').value = d.feeBase || 0;
            } else {
                // Jika toko tersebut belum ada datanya di tanggal ini, inisialisasi awal bersih/default
                document.getElementById('revTargetMtd').value = formatNum(parseInt(defaultTargetMtd, 10));
                document.getElementById('revActual').value = '0';
                document.getElementById('memberNew').value = '0';
                document.getElementById('memberStruk').value = '0';
                document.getElementById('totalStruk').value = '0';
                document.getElementById('cat1').value = '0';
                document.getElementById('cat2').value = '0';
                document.getElementById('feeBase').value = '0';

                document.getElementById('fokus1_t').value = '0'; document.getElementById('fokus1_s').value = '0';
                document.getElementById('fokus2_t').value = '0'; document.getElementById('fokus2_s').value = '0';
                document.getElementById('fokus3_t').value = '0'; document.getElementById('fokus3_s').value = '0';
                document.getElementById('fokus4_t').value = '0'; document.getElementById('fokus4_s').value = '0';

                for (let i = 1; i <= 9; i++) {
                    document.getElementById('psm' + i + '_t').value = '0';
                    document.getElementById('psm' + i + '_a').value = '0';
                }
            }
            hitungOtomatisSingle();
        })
        .catch(() => {
            document.getElementById('loadingStatus').style.display = 'none';
            document.getElementById('revTargetMtd').value = formatNum(parseInt(defaultTargetMtd, 10));
            hitungOtomatisSingle();
        });
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

    // Fungsi untuk menyimpan bagian tertentu (Fokus/PSM) tanpa mengganggu toko lain di Cloud
    function simpanBagianKhusus(bagian) {
        const periodeRaw = getVal('periode');
        const storeVal = getVal('selectStore').split('|');
        const kodeToko = storeVal[0];
        const namaToko = storeVal[1];

        let payload = {
            jenisLaporan: "Simpan " + bagian.toUpperCase() + " " + kodeToko,
            kodeToko: kodeToko,
            namaToko: namaToko,
            periode: periodeRaw,
            targetMtd: parseNum(getVal('revTargetMtd')),
            actual: parseNum(getVal('revActual')),
            mNew: parseNum(getVal('memberNew')),
            mStruk: parseNum(getVal('memberStruk')),
            tStruk: parseNum(getVal('totalStruk')),
            cat1: parseNum(getVal('cat1')),
            cat2: parseNum(getVal('cat2')),
            feeBase: parseNum(getVal('feeBase'))
        };

        payload.f1_t = parseNum(getVal('fokus1_t')); payload.f1_s = parseNum(getVal('fokus1_s'));
        payload.f2_t = parseNum(getVal('fokus2_t')); payload.f2_s = parseNum(getVal('fokus2_s'));
        payload.f3_t = parseNum(getVal('fokus3_t')); payload.f3_s = parseNum(getVal('fokus3_s'));
        payload.f4_t = parseNum(getVal('fokus4_t')); payload.f4_s = parseNum(getVal('fokus4_s'));

        for (let i = 1; i <= 9; i++) {
            payload['psm' + i + '_name'] = getVal('psm' + i + '_name');
            payload['psm' + i + '_t'] = parseNum(getVal('psm' + i + '_t'));
            payload['psm' + i + '_a'] = parseNum(getVal('psm' + i + '_a'));
        }

        document.getElementById('loadingStatus').innerText = "Menyimpan " + bagian.toUpperCase() + " Toko " + kodeToko + " ke Cloud...";
        document.getElementById('loadingStatus').style.display = 'block';

        fetch(WEB_APP_URL, {
            method: 'POST',
            mode: 'no-cors',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify(payload)
        })
        .then(() => {
            document.getElementById('loadingStatus').style.display = 'none';
            alert("Berhasil! Target " + bagian.toUpperCase() + " untuk toko " + kodeToko + " aman tersimpan di Cloud.");
        })
        .catch((error) => {
            document.getElementById('loadingStatus').style.display = 'none';
            alert("Gagal menyimpan ke cloud: " + error);
        });
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

            const f1 = `${getVal('fokus1_t')}/${getVal('fokus1_s')}/${getVal('fokus1_p')}`;
            const f2 = `${getVal('fokus2_t')}/${getVal('fokus2_s')}/${getVal('fokus2_p')}`;
            const f3 = `${getVal('fokus3_t')}/${getVal('fokus3_s')}/${getVal('fokus3_p')}`;
            const f4 = `${getVal('fokus4_t')}/${getVal('fokus4_s')}/${getVal('fokus4_p')}`;

            let psmListText = "";
            for (let i = 1; i <= 8; i++) {
                const nameItem = getVal('psm' + i + '_name').toUpperCase();
                const pItem = `${getVal('psm' + i + '_t')} - ${getVal('psm' + i + '_a')} - ${getVal('psm' + i + '_p')}`;
                psmListText += `${i}. ${nameItem}: ${pItem}\n`;
            }
            
            const p9NameVal = getVal('psm9_name');
            if (p9NameVal) {
                psmListText += `9. ${p9NameVal.toUpperCase()}: ${getVal('psm9_t')} - ${getVal('psm9_a')} - ${getVal('psm9_p')}\n`;
            }
            psmListText = psmListText.trimEnd();

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
                   psmListText + `\n` +
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
            text = `*REPORT SALES*\nPERIODE : ${periode}\nTerimakasih`;
        }

        document.getElementById('outputResult').innerText = text;
        document.getElementById('loadingStatus').style.display = 'block';

        let payload = {
            jenisLaporan: jenisLaporan,
            kodeToko: kodeToko,
            namaToko: namaToko,
            periode: periodeRaw,
            shiftInfo: shiftInfo,
            hasilTest: text,
            targetMtd: parseNum(getVal('revTargetMtd')),
            actual: parseNum(getVal('revActual')),
            f1_t: parseNum(getVal('fokus1_t')), f1_s: parseNum(getVal('fokus1_s')),
            f2_t: parseNum(getVal('fokus2_t')), f2_s: parseNum(getVal('fokus2_s')),
            f3_t: parseNum(getVal('fokus3_t')), f3_s: parseNum(getVal('fokus3_s')),
            f4_t: parseNum(getVal('fokus4_t')), f4_s: parseNum(getVal('fokus4_s')),
            mNew: parseNum(getVal('memberNew')),
            mStruk: parseNum(getVal('memberStruk')),
            tStruk: parseNum(getVal('totalStruk')),
            cat1: parseNum(getVal('cat1')),
            cat2: parseNum(getVal('cat2')),
            feeBase: parseNum(getVal('feeBase'))
        };

        for (let i = 1; i <= 9; i++) {
            payload['psm' + i + '_name'] = getVal('psm' + i + '_name');
            payload['psm' + i + '_t'] = parseNum(getVal('psm' + i + '_t'));
            payload['psm' + i + '_a'] = parseNum(getVal('psm' + i + '_a'));
        }

        fetch(WEB_APP_URL, {
            method: 'POST',
            mode: 'no-cors',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify(payload)
        })
        .then(() => {
            document.getElementById('loadingStatus').style.display = 'none';
            alert("Data Seluruh Toko " + kodeToko + " Berhasil Disimpan Aman ke Cloud!");
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
        setTanggalOtomatisHP();
        muatDataDariCloud();
    };
</script>
