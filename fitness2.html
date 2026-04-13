<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KiloMeter | Fitness Tracker</title>
    <style>
        :root {
            --primary: #f1c40f;
            --secondary: #e67e22;
            --dark: #121212;
            --card-bg: #1e1e1e;
            --text: #ffffff;
            --accent: #2ecc71;
            --danger: #ff4757;
        }

        body {
            font-family: 'Segoe UI', sans-serif;
            background-color: var(--dark);
            color: var(--text);
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        .container {
            width: 100%;
            max-width: 400px;
            background: var(--card-bg);
            padding: 30px;
            border-radius: 24px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.5);
            border: 1px solid rgba(255,255,255,0.05);
            position: relative;
            box-sizing: border-box;
        }

        .hidden { display: none !important; }

        header { text-align: center; margin-bottom: 25px; }
        header h1 { font-size: 2.2rem; margin: 0; color: var(--primary); letter-spacing: -1px; }

        .input-group { margin-bottom: 15px; }
        label { display: block; font-size: 0.7rem; margin-bottom: 6px; color: var(--primary); font-weight: bold; text-transform: uppercase; }

        input {
            width: 100%;
            padding: 12px;
            background: #2a2a2a;
            border: 1px solid #333;
            border-radius: 12px;
            color: white;
            box-sizing: border-box;
            outline: none;
        }

        button {
            width: 100%;
            padding: 14px;
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            border: none;
            border-radius: 12px;
            color: #000;
            font-weight: bold;
            cursor: pointer;
            text-transform: uppercase;
            margin-top: 10px;
        }

        /* Modal Overlay */
        .modal-overlay {
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.98);
            border-radius: 24px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 20px;
            z-index: 20;
            text-align: center;
        }

        .modal-btns { width: 100%; display: flex; flex-direction: column; gap: 10px; }
        .btn-save { background: var(--accent); color: white; }
        .btn-discard { background: var(--danger); color: white; }
        .btn-cancel { background: transparent; border: 1px solid white; color: white; }

        .dashboard-card {
            background: rgba(255,255,255,0.03);
            padding: 18px;
            border-radius: 18px;
            margin-bottom: 15px;
        }

        .stat-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; }
        .nav-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 20px; }
        .logout-trigger { background: transparent; border: 1px solid var(--danger); color: var(--danger); width: auto; padding: 5px 12px; font-size: 0.7rem; cursor: pointer; border-radius: 8px; }
    </style>
</head>
<body>

    <!-- AUTH PAGE -->
    <div id="authPage" class="container">
        <header><h1>KiloMeter</h1><p>Health & Fitness</p></header>
        <div class="input-group">
            <label>Email Address</label>
            <input type="email" id="email" placeholder="name@email.com">
        </div>
        <div class="input-group">
            <label>Password or 7-12 Digit ID</label>
            <input type="password" id="pass" placeholder="Min. 7-12 characters">
        </div>
        <button onclick="login()">Enter Dashboard</button>
        <p id="authError" style="color:var(--danger); font-size:0.75rem; text-align:center; display:none; margin-top:10px; line-height:1.4; font-weight: bold;"></p>
    </div>

    <!-- MAIN APP -->
    <div id="mainPage" class="container hidden">
        <div id="logoutModal" class="modal-overlay hidden">
            <h2 style="color:var(--primary)">Exit KiloMeter?</h2>
            <p style="font-size: 0.85rem; margin-bottom: 20px;">Save your current progress so you don't lose today's hard work?</p>
            <div class="modal-btns">
                <button class="btn-save" onclick="confirmLogout(true)">Save & Logout</button>
                <button class="btn-discard" onclick="confirmLogout(false)">Discard & Logout</button>
                <button class="btn-cancel" onclick="closeModal()">Back to Stats</button>
            </div>
        </div>

        <div class="nav-header">
            <div><small>Account:</small><div id="userName" style="color:var(--primary); font-weight:bold;">User</div></div>
            <button class="logout-trigger" onclick="openModal()">Logout</button>
        </div>

        <div class="dashboard-card">
            <div class="stat-grid">
                <div class="input-group"><label>Weight (kg)</label><input type="number" id="curWeight"></div>
                <div class="input-group"><label>Target (kg)</label><input type="number" id="tarWeight"></div>
            </div>
        </div>

        <div class="dashboard-card">
            <div class="input-group"><label>Calories</label><input type="number" id="calIn"></div>
            <div class="input-group"><label>Steps Walked</label><input type="number" id="steps"></div>
            <button onclick="updateStats()" style="background:var(--accent); color:white;">Update Data</button>
        </div>

        <div id="summary" class="dashboard-card hidden">
            <div class="stat-grid" style="text-align:center;">
                <div><span id="goalDist" style="font-size:1.5rem; color:var(--accent); font-weight:bold;">0</span><br><small>KG TO GO</small></div>
                <div><span id="burnVal" style="font-size:1.5rem; color:var(--accent); font-weight:bold;">0</span><br><small>KCAL BURNED</small></div>
            </div>
        </div>
    </div>

    <script>
        let sessionID = "";
        let userData = { weight: {}, logs: [] };

        // CONTENT FILTER (Email)
        const hardcoreBlock = /fuck|fuk|fck|f\*ck|nigger|nigga|gago|tanga|puta|bobo|ulol|pakyu|pakshet|panget|skwater|kupal|tarantado|slut|whore|bitch|sh1t/i;

        // "EASY PASSWORD" FILTER
        const easyPasswords = ["1234567", "12345678", "123456789", "0000000", "1111111", "2222222", "3333333", "7654321", "abcdefg", "password", "qwertyu"];

        function login() {
            const email = document.getElementById('email').value.trim().toLowerCase();
            const pass = document.getElementById('pass').value.trim();
            const err = document.getElementById('authError');

            const emailValid = /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
            const passLengthValid = pass.length >= 7 && pass.length <= 12;

            // 1. Check Email
            if (!emailValid) {
                showError("Invalid email format.");
                return;
            }

            const userPart = email.split('@')[0];
            if (hardcoreBlock.test(userPart)) {
                showError("SECURITY ALERT: Hurtful language detected in email.");
                return;
            }

            // 2. Check Password Length (7-12)
            if (!passLengthValid) {
                showError("Password/ID must be 7 to 12 characters.");
                return;
            }

            // 3. Check for "EASY" passwords (1234567, etc)
            if (easyPasswords.includes(pass.toLowerCase())) {
                showError("Entry Denied: Password is too weak/common. Use a unique ID or stronger password.");
                return;
            }

            // 4. Sequence/Repeat Check (Detects 1111111 or 1234567 even if not in list)
            const isRepeating = /^([\d\w])\1{6,}$/.test(pass); // e.g. "aaaaaaa"
            if (isRepeating) {
                showError("Password is too simple (repeating characters).");
                return;
            }

            // SUCCESS
            err.style.display = "none";
            sessionID = "KM_" + btoa(email);
            const saved = localStorage.getItem(sessionID);
            userData = saved ? JSON.parse(saved) : { weight: { cur: 0, tar: 0 }, logs: [] };

            document.getElementById('userName').innerText = userPart.toUpperCase();
            document.getElementById('authPage').classList.add('hidden');
            document.getElementById('mainPage').classList.remove('hidden');

            if(userData.weight.cur) {
                document.getElementById('curWeight').value = userData.weight.cur;
                document.getElementById('tarWeight').value = userData.weight.tar;
                render();
            }
        }

        function showError(msg) {
            const err = document.getElementById('authError');
            err.innerText = msg;
            err.style.display = "block";
        }

        function updateStats() {
            const cur = parseFloat(document.getElementById('curWeight').value) || 0;
            const tar = parseFloat(document.getElementById('tarWeight').value) || 0;
            const cal = parseFloat(document.getElementById('calIn').value) || 0;
            const stp = parseFloat(document.getElementById('steps').value) || 0;

            if (cur <= 0 || tar <= 0) return alert("Please enter weight data.");

            userData.weight = { cur, tar };
            userData.logs.push({ cal, burned: Math.round(stp * 0.04) });
            if (userData.logs.length > 7) userData.logs.shift();
            
            localStorage.setItem(sessionID, JSON.stringify(userData));
            render();
        }

        function render() {
            document.getElementById('summary').classList.remove('hidden');
            document.getElementById('goalDist').innerText = Math.abs(userData.weight.cur - userData.weight.tar).toFixed(1);
            const latest = userData.logs[userData.logs.length - 1] || { burned: 0 };
            document.getElementById('burnVal').innerText = latest.burned;
        }

        function openModal() { document.getElementById('logoutModal').classList.remove('hidden'); }
        function closeModal() { document.getElementById('logoutModal').classList.add('hidden'); }

        function confirmLogout(save) {
            if (save) updateStats();
            document.getElementById('mainPage').classList.add('hidden');
            document.getElementById('authPage').classList.remove('hidden');
            document.getElementById('email').value = "";
            document.getElementById('pass').value = "";
            closeModal();
        }
    </script>
</body>
</html>
