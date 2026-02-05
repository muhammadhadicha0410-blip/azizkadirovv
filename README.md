<!DOCTYPE html>
<html lang="uz">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AZIZBEK | Digital Card</title>
    <style>
        /* Umumiy ko'rinish (Dark Mode) */
        body {
            background-color: #0f0f0f;
            color: #ffffff;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
        }

        .card {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            padding: 40px;
            border-radius: 20px;
            text-align: center;
            width: 320px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }

        /* Oligarh uslubidagi Logo */
        .logo {
            font-size: 50px;
            font-weight: bold;
            background: linear-gradient(45deg, #d4af37, #f9f295, #b38728);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 10px;
            letter-spacing: 5px;
        }

        h1 { margin: 10px 0; font-size: 24px; letter-spacing: 2px; }
        p { color: #888; margin-bottom: 30px; }

        /* Tugmalar */
        .links-container a {
            display: block;
            background: #ffffff;
            color: #000;
            text-decoration: none;
            padding: 12px;
            margin: 10px 0;
            border-radius: 10px;
            font-weight: bold;
            transition: 0.3s;
        }

        .links-container a:hover {
            transform: scale(1.05);
            background: #d4af37;
        }

        /* Admin Panel qismi */
        .admin-btn {
            margin-top: 30px;
            font-size: 12px;
            color: #444;
            cursor: pointer;
            border: none;
            background: none;
        }

        #admin-panel {
            display: none;
            margin-top: 20px;
            border-top: 1px solid #333;
            padding-top: 20px;
        }

        input {
            width: 90%;
            padding: 10px;
            margin: 5px 0;
            border-radius: 5px;
            border: 1px solid #333;
            background: #222;
            color: #fff;
        }

        .save-btn {
            background: #28a745 !important;
            color: white !important;
            cursor: pointer;
        }
    </style>
</head>
<body>

<div class="card">
    <div class="logo">A</div>
    <h1 id="display-name">AZIZBEK</h1>
    <p id="display-phone">+998 90 123 45 67</p>

    <div class="links-container" id="links-list">
        </div>

    <button class="admin-btn" onclick="toggleAdmin()">Admin Sozlamalar</button>

    <div id="admin-panel">
        <input type="text" id="input-tg" placeholder="Telegram username (masalan: azizbek)">
        <input type="text" id="input-inst" placeholder="Instagram username">
        <button class="save-btn" onclick="saveData()">Saqlash</button>
    </div>
</div>

<script>
    // Ma'lumotlarni yuklash
    function loadData() {
        const tg = localStorage.getItem('tg') || '';
        const inst = localStorage.getItem('inst') || '';
        const list = document.getElementById('links-list');
        list.innerHTML = '';

        if(tg) {
            list.innerHTML += `<a href="https://t.me/${tg}" target="_blank">Telegram</a>`;
        }
        if(inst) {
            list.innerHTML += `<a href="https://instagram.com/${inst}" target="_blank">Instagram</a>`;
        }
    }

    // Admin panelni ochish/yopish
    function toggleAdmin() {
        const panel = document.getElementById('admin-panel');
        panel.style.display = panel.style.display === 'block' ? 'none' : 'block';
    }

    // Ma'lumotlarni saqlash
    function saveData() {
        const tg = document.getElementById('input-tg').value;
        const inst = document.getElementById('input-inst').value;
        
        localStorage.setItem('tg', tg);
        localStorage.setItem('inst', inst);
        
        alert("Ma'lumotlar saqlandi!");
        loadData();
        toggleAdmin();
    }

    // Sahifa yuklanganda ishga tushadi
    loadData();
</script>

</body>
</html>
