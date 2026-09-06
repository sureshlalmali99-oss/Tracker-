<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Transformation Tracker</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        :root {
            --primary: #f95700;
            --primary-dark: #ea580c;
            --green: #10b981;
            --red: #ef4444;
            --bg: #f8fafc;
            --card: #ffffff;
            --border: #e2e8f0;
            --text: #1e293b;
            --muted: #64748b;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
        }

        body {
            background: var(--bg);
            color: var(--text);
            padding: 10px;
        }

        .wrap {
            max-width: 1250px;
            margin: 0 auto;
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .card {
            background: var(--card);
            border: 1px solid var(--border);
            border-radius: 8px;
            padding: 12px;
        }

        .banner {
            background: linear-gradient(135deg, var(--primary), var(--primary-dark));
            color: #fff;
            border-radius: 8px;
            padding: 14px 16px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 8px;
        }

        .banner h1 {
            font-size: 1.2rem;
            font-weight: 800;
        }

        .banner p {
            font-size: 0.75rem;
            opacity: 0.95;
        }

        .btns {
            display: flex;
            gap: 6px;
        }

        .btn {
            border: none;
            padding: 6px 12px;
            border-radius: 5px;
            font-size: 0.75rem;
            font-weight: 700;
            cursor: pointer;
        }

        .btn-w { background: #fff; color: var(--primary-dark); }
        .btn-r { background: rgba(255,255,255,0.25); color: #fff; }

        .profile-row {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(130px, 1fr));
            gap: 8px;
            margin-bottom: 10px;
        }

        .field {
            display: flex;
            flex-direction: column;
            gap: 3px;
        }

        .field label {
            font-size: 0.65rem;
            font-weight: 700;
            color: var(--muted);
            text-transform: uppercase;
        }

        .field input {
            padding: 6px 8px;
            border: 1px solid var(--border);
            border-radius: 5px;
            font-size: 0.8rem;
            outline: none;
        }

        .stats-row {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
            gap: 8px;
        }

        .stat-box {
            background: #ecfdf5;
            border: 1px solid #a7f3d0;
            color: #065f46;
            border-radius: 6px;
            padding: 8px;
            text-align: center;
        }

        .stat-box .val {
            font-size: 1.15rem;
            font-weight: 800;
        }

        .stat-box .lbl {
            font-size: 0.62rem;
            font-weight: 700;
            text-transform: uppercase;
        }

        .heading {
            font-size: 0.82rem;
            font-weight: 800;
            color: var(--primary-dark);
            border-bottom: 2px solid #ffedd5;
            padding-bottom: 4px;
            margin-bottom: 8px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .h-scroll {
            overflow-x: auto;
            border: 1px solid var(--border);
            border-radius: 6px;
            background: #fff;
        }

        table {
            border-collapse: collapse;
            font-size: 0.72rem;
            text-align: center;
            white-space: nowrap;
            width: 100%;
        }

        th, td {
            padding: 5px 6px;
            border: 1px solid var(--border);
            min-width: 52px;
        }

        .sticky-col {
            position: sticky;
            left: 0;
            background: #f8fafc;
            font-weight: 700;
            text-align: left;
            z-index: 1;
            min-width: 180px;
            color: var(--text);
            border-right: 2px solid var(--border);
        }

        table input {
            width: 50px;
            padding: 3px;
            text-align: center;
            border: 1px solid var(--border);
            border-radius: 3px;
            font-size: 0.72rem;
        }

        .photos-strip {
            display: flex;
            gap: 8px;
            overflow-x: auto;
            padding: 4px;
        }

        .photo-card {
            min-width: 78px;
            width: 78px;
            border: 1.5px dashed #94a3b8;
            border-radius: 5px;
            padding: 4px;
            text-align: center;
            cursor: pointer;
            background: #fafafa;
            flex-shrink: 0;
        }

        .photo-card img {
            width: 100%;
            height: 58px;
            object-fit: cover;
            border-radius: 4px;
            display: none;
        }

        .photo-card span {
            font-size: 0.62rem;
            color: var(--muted);
            font-weight: 700;
            display: block;
            margin-top: 2px;
        }

        .day-cell {
            width: 22px;
            height: 22px;
            border: 1px solid var(--border);
            border-radius: 3px;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            font-size: 0.68rem;
            font-weight: 800;
            cursor: pointer;
            user-select: none;
            background: #fff;
        }

        .day-cell.done {
            background: var(--green);
            color: #fff;
            border-color: var(--green);
        }

        .day-cell.missed {
            background: var(--red);
            color: #fff;
            border-color: var(--red);
        }
    </style>
</head>
<body>

<div class="wrap">

    <div class="banner">
        <div>
            <h1>12-WEEK TRANSFORMATION TRACKER</h1>
            <p>Fat Loss, Yoga & Daily Habits Protocol</p>
        </div>
        <div class="btns">
            <button class="btn btn-w" onclick="window.print()">Download PDF / Print</button>
            <button class="btn btn-r" onclick="resetAll()">Reset All</button>
        </div>
    </div>

    <div class="card">
        <div class="profile-row">
            <div class="field">
                <label>Name</label>
                <input type="text" id="p_name" placeholder="Suresh Mali" oninput="saveAndCalc()">
            </div>
            <div class="field">
                <label>Start Date</label>
                <input type="date" id="p_date" oninput="saveAndCalc()">
            </div>
            <div class="field">
                <label>Starting Weight (kg)</label>
                <input type="number" step="0.1" id="p_start_wt" placeholder="122.8" oninput="saveAndCalc()">
            </div>
            <div class="field">
                <label>Goal Weight (kg)</label>
                <input type="number" step="0.1" id="p_goal_wt" placeholder="90" oninput="saveAndCalc()">
            </div>
            <div class="field">
                <label>Start Waist (inch)</label>
                <input type="number" step="0.1" id="p_start_waist" placeholder="50" oninput="saveAndCalc()">
            </div>
            <div class="field">
                <label>Start Belly (inch)</label>
                <input type="number" step="0.1" id="p_start_belly" placeholder="56" oninput="saveAndCalc()">
            </div>
        </div>

        <div class="stats-row">
            <div class="stat-box">
                <div class="val" id="st_lost_wt">0.0 kg</div>
                <div class="lbl">Total Weight Lost</div>
            </div>
            <div class="stat-box">
                <div class="val" id="st_rem_wt">0.0 kg</div>
                <div class="lbl">Remaining Weight</div>
            </div>
            <div class="stat-box">
                <div class="val" id="st_lost_waist">0.0 in</div>
                <div class="lbl">Total Waist Lost</div>
            </div>
            <div class="stat-box">
                <div class="val" id="st_lost_belly">0.0 in</div>
                <div class="lbl">Total Belly Lost</div>
            </div>
        </div>
    </div>

    <div class="card">
        <div class="heading">
            <span>📊 12-WEEK WEIGHT & MEASUREMENT MAP</span>
        </div>
        <div class="h-scroll">
            <table>
                <thead>
                    <tr id="w_head">
                        <th class="sticky-col">Metric / Week</th>
                    </tr>
                </thead>
                <tbody>
                    <tr id="row_date"><td class="sticky-col">📅 Result Date</td></tr>
                    <tr id="row_wt"><td class="sticky-col">⚖️ Actual Weight (kg)</td></tr>
                    <tr id="row_diff"><td class="sticky-col">📉 Lost This Week</td></tr>
                    <tr id="row_waist"><td class="sticky-col">📏 Waist (inches)</td></tr>
                    <tr id="row_belly"><td class="sticky-col">📍 Belly / Navel (inches)</td></tr>
                </tbody>
            </table>
        </div>
    </div>

    <div class="card">
        <div class="heading">
            <span>📷 WEEKLY PROGRESS PHOTOS (12 WEEKS)</span>
        </div>
        <div class="photos-strip" id="photo_row"></div>
    </div>

    <div class="card">
        <div class="heading">
            <span>🗓️ DAILY PROTOCOL MATRIX (8 DAYS CYCLE)</span>
            <button class="btn btn-w" style="border:1px solid var(--primary); color:var(--primary);" onclick="reset8Days()">🔄 Reset 8 Days</button>
        </div>
        <div class="h-scroll">
            <table>
                <thead>
                    <tr id="mat_head">
                        <th class="sticky-col">Daily Protocol</th>
                    </tr>
                </thead>
                <tbody id="mat_body"></tbody>
            </table>
        </div>
    </div>

    <div class="card">
        <div class="heading">
            <span>📈 DAILY HABITS SCORE GRAPH (0 TO 6 SCORE)</span>
        </div>
        <div style="height: 180px; width: 100%;">
            <canvas id="scoreChart"></canvas>
        </div>
    </div>

</div>

<script>
    const rules = [
        { id: 1, name: "1. 5:00 AM Wake Up ⏰" },
        { id: 2, name: "2. Surya Namaskar (Daily Reps) 🧘" },
        { id: 3, name: "3. Clean Diet (Calorie Deficit) 🥗" },
        { id: 4, name: "4. 3-4 Litres Water Intake 💧" },
        { id: 5, name: "5. Balasana (Child's Pose) 🙇" },
        { id: 6, name: "6. Shavasana (Body Relaxation) 🛌" }
    ];

    let habits = JSON.parse(localStorage.getItem('tr_h8')) || {};
    let photos = JSON.parse(localStorage.getItem('tr_p12')) || {};
    let chart = null;

    function initTable() {
        const head = document.getElementById('w_head');
        const rD = document.getElementById('row_date');
        const rW = document.getElementById('row_wt');
        const rDf = document.getElementById('row_diff');
        const rWs = document.getElementById('row_waist');
        const rB = document.getElementById('row_belly');

        for (let i = 1; i <= 12; i++) {
            head.innerHTML += `<th>W${i}</th>`;
            rD.innerHTML += `<td><input type="text" id="wd_${i}" placeholder="DD/MM" oninput="saveAndCalc()"></td>`;
            rW.innerHTML += `<td><input type="number" step="0.1" id="ww_${i}" placeholder="0.0" oninput="saveAndCalc()"></td>`;
            rDf.innerHTML += `<td id="wdiff_${i}" style="font-weight:700;">-</td>`;
            rWs.innerHTML += `<td><input type="number" step="0.1" id="wws_${i}" placeholder="0.0" oninput="saveAndCalc()"></td>`;
            rB.innerHTML += `<td><input type="number" step="0.1" id="wb_${i}" placeholder="0.0" oninput="saveAndCalc()"></td>`;
        }
    }

    function initPhotos() {
        const row = document.getElementById('photo_row');
        for (let i = 1; i <= 12; i++) {
            const el = document.createElement('div');
            el.className = 'photo-card';
            el.innerHTML = `
                <input type="file" id="pf_${i}" accept="image/*" style="display:none" onchange="upImg(event, ${i})">
                <img id="pv_${i}">
                <span id="pt_${i}">Week ${i}</span>
            `;
            el.onclick = () => document.getElementById(`pf_${i}`).click();
            row.appendChild(el);
        }
    }

    function upImg(e, i) {
        const file = e.target.files[0];
        if (file) {
            const reader = new FileReader();
            reader.onload = function(evt) {
                photos[`w_${i}`] = evt.target.result;
                try { localStorage.setItem('tr_p12', JSON.stringify(photos)); } catch(err) {}
                setImg(i, evt.target.result);
            };
            reader.readAsDataURL(file);
        }
    }

    function setImg(i, src) {
        const img = document.getElementById(`pv_${i}`);
        if (img && src) { img.src = src; img.style.display = 'block'; }
    }

    function initMatrix() {
        const head = document.getElementById('mat_head');
        const body = document.getElementById('mat_body');
        head.innerHTML = `<th class="sticky-col">Daily Protocol</th>`;

        for (let d = 1; d <= 8; d++) {
            head.innerHTML += `<th>${d}</th>`;
        }

        body.innerHTML = '';
        rules.forEach(r => {
            const tr = document.createElement('tr');
            let h = `<td class="sticky-col">${r.name}</td>`;
            for (let d = 1; d <= 8; d++) {
                const state = habits[`r${r.id}_d${d}`] || '';
                let cls = 'day-cell';
                let sym = '';
                if (state === 'done') { cls += ' done'; sym = '✔'; }
                if (state === 'missed') { cls += ' missed'; sym = '✖'; }
                h += `<td><div class="${cls}" onclick="toggleHabit(${r.id}, ${d}, this)">${sym}</div></td>`;
            }
            tr.innerHTML = h;
            body.appendChild(tr);
        });
    }

    function toggleHabit(rId, d, el) {
        const k = `r${rId}_d${d}`;
        if (!el.classList.contains('done') && !el.classList.contains('missed')) {
            el.className = 'day-cell done'; el.innerText = '✔'; habits[k] = 'done';
        } else if (el.classList.contains('done')) {
            el.className = 'day-cell missed'; el.innerText = '✖'; habits[k] = 'missed';
        } else {
            el.className = 'day-cell'; el.innerText = ''; delete habits[k];
        }
        localStorage.setItem('tr_h8', JSON.stringify(habits));
        updateChart();
    }

    function reset8Days() {
        if (confirm("Reset current 8-day cycle?")) {
            for (let r = 1; r <= 6; r++) {
                for (let d = 1; d <= 8; d++) {
                    delete habits[`r${r}_d${d}`];
                }
            }
            localStorage.setItem('tr_h8', JSON.stringify(habits));
            initMatrix();
            updateChart();
        }
    }

    function initChart() {
        const ctx = document.getElementById('scoreChart').getContext('2d');
        const grad = ctx.createLinearGradient(0, 0, 0, 160);
        grad.addColorStop(0, 'rgba(249, 87, 0, 0.4)');
        grad.addColorStop(1, 'rgba(249, 87, 0, 0.0)');

        chart = new Chart(ctx, {
            type: 'line',
            data: {
                labels: ['1','2','3','4','5','6','7','8'],
                datasets: [{
                    label: 'Score (0 to 6)',
                    data: [0,0,0,0,0,0,0,0],
                    borderColor: '#f95700',
                    borderWidth: 2,
                    backgroundColor: grad,
                    fill: true,
                    tension: 0.35,
                    pointBackgroundColor: '#f95700',
                    pointRadius: 3
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                scales: { y: { min: 0, max: 6, ticks: { stepSize: 1 } } }
            }
        });
        updateChart();
    }

    function updateChart() {
        if (!chart) return;
        const scores = [];
        for (let d = 1; d <= 8; d++) {
            let sc = 0;
            rules.forEach(r => { if (habits[`r${r.id}_d${d}`] === 'done') sc++; });
            scores.push(sc);
        }
        chart.data.datasets[0].data = scores;
        chart.update();
    }

    function saveAndCalc() {
        const sW = parseFloat(document.getElementById('p_start_wt').value) || 0;
        const gW = parseFloat(document.getElementById('p_goal_wt').value) || 0;
        const sWs = parseFloat(document.getElementById('p_start_waist').value) || 0;
        const sB = parseFloat(document.getElementById('p_start_belly').value) || 0;

        let prev = sW;
        let lastW = sW;
        let lastWs = sWs;
        let lastB = sB;

        for (let i = 1; i <= 12; i++) {
            const wVal = parseFloat(document.getElementById(`ww_${i}`).value);
            const wsVal = parseFloat(document.getElementById(`wws_${i}`).value);
            const bVal = parseFloat(document.getElementById(`wb_${i}`).value);
            const diffEl = document.getElementById(`wdiff_${i}`);

            if (!isNaN(wVal) && wVal > 0) {
                const diff = (prev - wVal).toFixed(1);
                diffEl.innerText = diff > 0 ? `-${diff} kg` : (diff < 0 ? `+${Math.abs(diff)} kg` : '0.0 kg');
                diffEl.style.color = diff > 0 ? 'var(--green)' : (diff < 0 ? 'var(--red)' : 'inherit');
                prev = wVal;
                lastW = wVal;
            } else {
                diffEl.innerText = '-';
            }
            if (!isNaN(wsVal) && wsVal > 0) lastWs = wsVal;
            if (!isNaN(bVal) && bVal > 0) lastB = bVal;
        }

        document.getElementById('st_lost_wt').innerText = (sW > 0 && lastW > 0) ? `${(sW - lastW).toFixed(1)} kg` : '0.0 kg';
        document.getElementById('st_rem_wt').innerText = (gW > 0 && lastW > 0) ? `${Math.max(0, (lastW - gW)).toFixed(1)} kg` : '0.0 kg';
        document.getElementById('st_lost_waist').innerText = (sWs > 0 && lastWs > 0) ? `${(sWs - lastWs).toFixed(1)} in` : '0.0 in';
        document.getElementById('st_lost_belly').innerText = (sB > 0 && lastB > 0) ? `${(sB - lastB).toFixed(1)} in` : '0.0 in';

        const data = {
            name: document.getElementById('p_name').value,
            date: document.getElementById('p_date').value,
            sW, gW, sWs, sB,
            rows: {}
        };
        for (let i = 1; i <= 12; i++) {
            data.rows[i] = {
                d: document.getElementById(`wd_${i}`).value,
                w: document.getElementById(`ww_${i}`).value,
                ws: document.getElementById(`wws_${i}`).value,
                b: document.getElementById(`wb_${i}`).value
            };
        }
        localStorage.setItem('tr_main', JSON.stringify(data));
    }

    function loadData() {
        const d = JSON.parse(localStorage.getItem('tr_main'));
        if (d) {
            document.getElementById('p_name').value = d.name || '';
            document.getElementById('p_date').value = d.date || '';
            document.getElementById('p_start_wt').value = d.sW || '';
            document.getElementById('p_goal_wt').value = d.gW || '';
            document.getElementById('p_start_waist').value = d.sWs || '';
            document.getElementById('p_start_belly').value =
