<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <title>Guru-Scheduler: Master Engine</title>
    <script src="database.js"></script>
    <style>
        :root { --main: #002366; --red: #c62828; }
        body { font-family: 'Segoe UI', Arial; margin: 0; display: flex; height: 100vh; background: #f4f7f6; }
        .sidebar { width: 450px; background: white; border-right: 3px solid var(--main); display: flex; flex-direction: column; box-shadow: 4px 0 10px rgba(0,0,0,0.1); }
        .sidebar-head { background: var(--main); color: white; padding: 15px; text-align: center; }
        .nav-zone { padding: 12px; background: #fffde7; border-bottom: 2px solid #ddd; }
        .bank-area { flex-grow: 1; overflow-y: auto; padding: 15px; }
        .chapter-title { background: #e3f2fd; color: #0d47a1; padding: 10px; margin: 20px 0 10px; border-left: 6px solid var(--main); font-weight: bold; position: sticky; top: 0; }
        .q-card { background: #fff; border: 1px solid #ddd; padding: 12px; margin-bottom: 10px; border-radius: 8px; display: flex; gap: 12px; cursor: pointer; }
        .q-card:hover { border-color: var(--red); background: #fff8f8; }
        .preview-pane { flex-grow: 1; overflow-y: auto; padding: 40px 20px; background: #525659; }
        .a4-page { background: white; width: 210mm; min-height: 297mm; margin: 0 auto; padding: 20mm; box-shadow: 0 0 30px rgba(0,0,0,0.6); box-sizing: border-box; }
        .p-header { text-align: center; border-bottom: 4px double black; margin-bottom: 15px; }
        .p-meta { display: flex; justify-content: space-between; font-weight: bold; border-bottom: 1px solid black; padding-bottom: 5px; margin-bottom: 25px; }
        .sec-banner { text-align: center; font-weight: bold; margin: 30px 0 15px; border: 1px solid black; padding: 6px; background: #f0f0f0; }
        .q-row { display: flex; justify-content: space-between; margin-bottom: 18px; font-size: 14pt; line-height: 1.6; page-break-inside: avoid; }
        select, input { width: 100%; padding: 12px; margin: 5px 0; border-radius: 5px; border: 1px solid #ccc; font-weight: bold; }
        .btn-print { background: var(--red); color: white; padding: 15px; font-size: 18px; border: none; width: 100%; cursor: pointer; font-weight: bold; }
        @media print { .sidebar { display: none; } .preview-pane { background: white; padding: 0; } .a4-page { box-shadow: none; width: 100%; margin: 0; padding: 10mm; } }
    </style>
</head>
<body>
<div class="sidebar">
    <div class="sidebar-head"><h2 style="margin:0;">GURU-SCHEDULER</h2></div>
    <div class="nav-zone">
        <input type="text" id="schName" placeholder="स्कूल का नाम लिखें..." oninput="autoSave()">
        <div style="display:flex; gap:8px; margin-top:8px;">
            <select id="selClass" onchange="fetchData()">
                <option value="6">कक्षा 6</option><option value="7">कक्षा 7</option><option value="8">कक्षा 8</option>
            </select>
            <select id="selSub" onchange="fetchData()">
                <option value="Science">विज्ञान</option><option value="Hindi">हिन्दी</option>
                <option value="Maths">गणित</option><option value="SST">सामाजिक विज्ञान</option>
            </select>
        </div>
    </div>
    <div class="bank-area" id="bankList"></div>
    <button class="btn-print" onclick="window.print()">🖨️ प्रिंट निकालें</button>
</div>
<div class="preview-pane">
    <div class="a4-page">
        <div class="p-header"><h1 id="disp-sch">SCHOOL NAME</h1><p>वार्षिक परीक्षा 2025-26</p></div>
        <div class="p-meta">
            <span>विषय: <span id="disp-sub">---</span></span>
            <span>कक्षा: <span id="disp-class">---</span></span>
        </div>
        <div id="paper-body"></div>
    </div>
</div>
<script>
    let selections = JSON.parse(localStorage.getItem('guru_sel')) || [];
    function fetchData() {
        const key = `${document.getElementById('selClass').value}-${document.getElementById('selSub').value}`;
        const area = document.getElementById('bankList');
        area.innerHTML = "";
        const data = masterDB[key];
        if(!data) { area.innerHTML = "डेटा लोड हो रहा है..."; return; }
        for(let ch in data) {
            area.innerHTML += `<div class="chapter-title">${ch}</div>`;
            data[ch].forEach(q => {
                const checked = selections.includes(q.id) ? "checked" : "";
                area.innerHTML += `<div class="q-card"><input type="checkbox" id="q-${q.id}" ${checked} onchange="toggleQ('${q.id}')">
                <div onclick="document.getElementById('q-${q.id}').click()"><b>[${q.t}-${q.m}अंक]</b><br>${q.q}</div></div>`;
            });
        }
        autoSave(); renderPaper();
    }
    function toggleQ(id) {
        const idx = selections.indexOf(id);
        idx > -1 ? selections.splice(idx, 1) : selections.push(id);
        localStorage.setItem('guru_sel', JSON.stringify(selections));
        renderPaper();
    }
    function renderPaper() {
        const body = document.getElementById('paper-body');
        body.innerHTML = "";
        let selectedData = [];
        for(let k in masterDB) { for(let ch in masterDB[k]) { masterDB[k][ch].forEach(q => { if(selections.includes(q.id)) selectedData.push(q); }); } }
        ["MCQ", "Short", "Long"].forEach(type => {
            const filtered = selectedData.filter(x => x.t === type);
            if(filtered.length > 0) {
                body.innerHTML += `<div class="sec-banner">${type}</div>`;
                filtered.forEach((item, i) => { body.innerHTML += `<div class="q-row"><span><b>Q.${i+1}.</b> ${item.q}</span><span>[${item.m}]</span></div>`; });
            }
        });
    }
    function autoSave() {
        const name = document.getElementById('schName').value;
        document.getElementById('disp-sch').innerText = name || "SCHOOL NAME";
        document.getElementById('disp-sub').innerText = document.getElementById('selSub').value;
        document.getElementById('disp-class').innerText = document.getElementById('selClass').value;
    }
    fetchData();
</script>
</body>
</html>
