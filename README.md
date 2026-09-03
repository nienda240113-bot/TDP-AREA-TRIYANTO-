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
        .btn-orange { background-color: #d35400; margin-bottom: 10px; }
        pre { background: #f1f1f1; padding: 10px; border-radius: 4px; white-space: pre-wrap; word-wrap: break-word; font-family: Arial, sans-serif; font-size: 0.8rem; border: 1px solid #ddd; max-height: 350px; overflow-y: auto; }
        fieldset { border: 1px solid #ddd; border-radius: 6px; padding: 8px; margin-bottom: 10px; }
        legend { font-weight: bold; font-size: 0.85rem; color: #2980b9; }
        .loading { display: none; text-align: center; color: #e67e22; font-weight: bold; margin-top: 8px; }
        .info-periode { font-size: 0.75rem; color: #c0392b; margin-bottom: 6px; font-style: italic; }
        .table-input { width: 100%; border-collapse: collapse; margin-bottom: 5px; font-size: 0.8rem; }
        .table-input th { background-color: #16a085; color: white; padding: 6px 4px; text-align: center; border: 1px solid #1abc9c; }
        .table-input td { padding: 4px; border: 1px solid #ddd; text-align: center; }
        .table-input input { text-align: center; margin-bottom: 0; padding: 5px; font-size: 0.85rem; }
        .table-input td:first-child { text-align: left; padding-left: 4px; }
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

        <div class="row-group" style="margin-top: 8px;">
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

        <div id="singleStoreSection">
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
                <optio
