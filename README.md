<!DOCTYPE html>
<html lang="ckb">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover, user-scalable=no">
    <title>7AJI-IOS | کۆگای کراوە</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            background: radial-gradient(circle at 10% 20%, #0a0f1a 0%, #000000 100%);
            color: #ffffff;
            padding-bottom: 100px;
            min-height: 100vh;
        }

        body::before {
            content: "";
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at 30% 40%, rgba(10, 132, 255, 0.06) 0%, transparent 60%);
            pointer-events: none;
            z-index: 0;
        }

        body::after {
            content: "";
            position: fixed;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle at 40% 50%, rgba(0, 150, 255, 0.04), rgba(255, 50, 50, 0.03), transparent 70%);
            animation: slowRotate 30s linear infinite;
            pointer-events: none;
            z-index: 0;
        }

        @keyframes slowRotate {
            0% { transform: translate(0%, 0%) rotate(0deg); }
            100% { transform: translate(5%, 5%) rotate(360deg); }
        }

        .container {
            max-width: 500px;
            margin: 0 auto;
            padding: 12px 16px 30px;
            position: relative;
            z-index: 2;
        }

        .hacked-header {
            text-align: center;
            margin: 10px 0 20px 0;
        }

        .hacked-text {
            font-size: 52px;
            font-weight: 900;
            letter-spacing: 4px;
            background: linear-gradient(135deg, #ff3366, #ff6633, #ff0000);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            animation: hackedGlow 1.5s ease-in-out infinite;
            font-family: monospace;
        }

        @keyframes hackedGlow {
            0% { text-shadow: 0 0 5px #ff3366; }
            50% { text-shadow: 0 0 25px #ff6633; }
            100% { text-shadow: 0 0 5px #ff3366; }
        }

        .hero-card {
            background: rgba(12, 18, 28, 0.7);
            backdrop-filter: blur(20px);
            border-radius: 48px;
            padding: 25px 20px;
            margin: 8px 0 28px 0;
            text-align: center;
            border: 1px solid rgba(255, 51, 102, 0.4);
        }

        .animated-line {
            display: flex;
            justify-content: center;
            align-items: center;
            flex-wrap: wrap;
            gap: 8px;
            direction: rtl;
            margin-bottom: 10px;
        }

        .word {
            display: inline-block;
            font-size: 28px;
            font-weight: 800;
            animation: floatWord 1.5s ease-in-out infinite;
            background: linear-gradient(135deg, #ffffff, #3aa8ff);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .word-special {
            display: inline-block;
            font-size: 34px;
            font-weight: 900;
            animation: bounceGlow 1.2s ease-in-out infinite;
            background: linear-gradient(135deg, #ffcc33, #ff9933);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        @keyframes bounceGlow {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-6px); }
            100% { transform: translateY(0px); }
        }

        @keyframes floatWord {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-4px); }
            100% { transform: translateY(0px); }
        }

        .hero-number {
            font-size: 32px;
            font-weight: 900;
            background: linear-gradient(135deg, #ffb347, #ff7e05);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin: 10px 0;
        }

        .hero-badge {
            background: rgba(255, 51, 102, 0.2);
            padding: 6px 16px;
            border-radius: 60px;
            font-size: 12px;
            display: inline-block;
            margin: 5px;
        }

        /* دوگمەی نهێنی ئەدمن */
        .admin-secret-btn {
            position: fixed;
            bottom: 120px;
            right: 15px;
            background: rgba(0,0,0,0.6);
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            cursor: pointer;
            z-index: 150;
            backdrop-filter: blur(10px);
            border: 1px solid #ff3366;
        }

        /* Modal پەسوۆرد */
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.95);
            z-index: 400;
            display: flex;
            align-items: center;
            justify-content: center;
            visibility: hidden;
            backdrop-filter: blur(10px);
        }
        .modal.open { visibility: visible; }
        .modal-content {
            background: #1a1a2e;
            padding: 30px;
            border-radius: 40px;
            width: 85%;
            max-width: 320px;
            text-align: center;
            border: 1px solid #ff3366;
        }
        .modal-content input {
            width: 100%;
            padding: 14px;
            margin: 15px 0;
            background: #2a2a3e;
            border: 1px solid #ff3366;
            border-radius: 30px;
            color: white;
            font-size: 16px;
        }
        .modal-content button {
            background: #ff3366;
            border: none;
            padding: 12px;
            border-radius: 40px;
            color: white;
            font-weight: bold;
            width: 100%;
            cursor: pointer;
        }

        /* پانێڵی ئەدمن */
        .admin-panel {
            position: fixed;
            top: 0;
            right: -100%;
            width: 90%;
            max-width: 400px;
            height: 100vh;
            background: rgba(10, 10, 20, 0.98);
            backdrop-filter: blur(25px);
            z-index: 500;
            padding: 80px 16px 20px;
            transition: 0.3s;
            overflow-y: auto;
            border-left: 2px solid #ff3366;
        }
        .admin-panel.open { right: 0; }
        .admin-panel h3 {
            color: #ff3366;
            margin-bottom: 15px;
            font-size: 20px;
        }
        .admin-panel input, .admin-panel select, .admin-panel textarea {
            width: 100%;
            padding: 12px;
            margin: 8px 0;
            background: #2a2a3e;
            border: 1px solid #ff3366;
            border-radius: 16px;
            color: white;
            font-size: 14px;
        }
        .admin-panel button {
            background: #ff3366;
            padding: 12px;
            border-radius: 30px;
            width: 100%;
            margin: 8px 0;
            border: none;
            color: white;
            font-weight: bold;
            cursor: pointer;
        }
        .admin-panel .close-btn {
            position: absolute;
            top: 15px;
            right: 15px;
            background: none;
            font-size: 28px;
            width: auto;
        }
        .image-preview-area {
            background: rgba(255,51,102,0.1);
            border-radius: 20px;
            padding: 15px;
            margin: 10px 0;
            text-align: center;
        }
        .preview-img {
            width: 70px;
            height: 70px;
            border-radius: 18px;
            background: #2a2a3e;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 10px;
            overflow: hidden;
        }
        .preview-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        .upload-btns {
            display: flex;
            gap: 10px;
            margin: 10px 0;
        }
        .upload-btns button {
            background: #3a3a4e;
            margin: 0;
            padding: 8px;
        }
        .admin-item {
            background: rgba(255,51,102,0.1);
            padding: 10px;
            margin: 8px 0;
            border-radius: 16px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        /* کارتەکان */
        .section {
            margin-bottom: 32px;
        }
        .section-header {
            display: flex;
            justify-content: space-between;
            align-items: baseline;
            margin-bottom: 14px;
        }
        .section-header h3 {
            font-size: 20px;
            direction: rtl;
        }
        .scroll-horizontal {
            display: flex;
            gap: 14px;
            overflow-x: auto;
            padding-bottom: 8px;
        }
        .app-card, .big-app-card {
            background: rgba(28, 28, 30, 0.7);
            backdrop-filter: blur(12px);
            border-radius: 24px;
            flex-shrink: 0;
            padding: 12px;
            border: 0.5px solid rgba(255,51,102,0.2);
        }
        .app-card { width: 130px; text-align: center; }
        .big-app-card { width: 215px; }
        .app-icon {
            width: 70px;
            height: 70px;
            margin: 0 auto 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            background: rgba(44,44,46,0.8);
            border-radius: 18px;
            overflow: hidden;
        }
        .app-icon img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        .app-icon span {
            font-size: 38px;
        }
        .big-icon {
            width: 52px;
            height: 52px;
            background: rgba(44,44,46,0.8);
            border-radius: 16px;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }
        .big-icon img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        .big-icon span {
            font-size: 28px;
        }
        .big-app-row {
            display: flex;
            align-items: center;
            gap: 12px;
        }
        .big-info {
            flex: 1;
        }
        .big-title {
            font-weight: 600;
            font-size: 14px;
        }
        .big-sub {
            font-size: 10px;
            color: #aaa;
        }
        .get-btn, .big-get {
            background: linear-gradient(135deg, #ff3366, #cc0044);
            padding: 6px 14px;
            border-radius: 40px;
            font-size: 12px;
            font-weight: bold;
            cursor: pointer;
            display: inline-block;
            margin-top: 8px;
            text-align: center;
        }
        .tab-bar {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(10,10,15,0.95);
            backdrop-filter: blur(25px);
            border-top: 1px solid rgba(255,51,102,0.5);
            display: flex;
            justify-content: space-around;
            padding: 14px 20px 28px;
            z-index: 100;
        }
        .tab-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 6px;
            font-size: 12px;
            color: #8e8e93;
            cursor: pointer;
        }
        .tab-item.active { color: #ff3366; }
        .toast {
            position: fixed;
            bottom: 110px;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(0,0,0,0.9);
            padding: 10px 24px;
            border-radius: 50px;
            font-size: 13px;
            color: #ff3366;
            z-index: 200;
            opacity: 0;
            border: 0.5px solid #ff3366;
            white-space: nowrap;
        }
    </style>
</head>
<body>

<div class="admin-secret-btn" id="secretAdminBtn">🔐</div>

<div class="modal" id="passwordModal">
    <div class="modal-content">
        <h3>🔒 ئەدمن پانێڵ</h3>
        <input type="password" id="adminPassword" placeholder="پەسوۆرد">
        <button id="submitPasswordBtn">داخڵ بە</button>
    </div>
</div>

<div class="admin-panel" id="adminPanel">
    <button class="close-btn" id="closeAdminBtn">✖</button>
    <h3>➕ زیادکردنی بەرنامە</h3>
    <input type="text" id="appName" placeholder="ناوی بەرنامە (م: Facebook)">
    
    <div class="image-preview-area">
        <label>🖼️ لۆگۆی بەرنامە:</label>
        <div class="preview-img" id="imagePreview">📦</div>
        <input type="text" id="appIconUrl" placeholder="بەستەری وێنە (https://...)" style="margin-bottom: 8px;">
        <div class="upload-btns">
            <button id="uploadFileBtn">📁 بارکردن لە فایل</button>
        </div>
        <input type="file" id="fileInput" accept="image/*" style="display: none;">
        <small>دەتوانیت بەستەر بنوسیت یان وێنە باربکەیت</small>
    </div>

    <select id="appType">
        <option value="normal">Apps for You (بچووک)</option>
        <option value="tweaked">Tweaked Apps (گەورە)</option>
        <option value="recent">Recently Updated (گەورە)</option>
    </select>
    <input type="text" id="appDesc" placeholder="وەسف (تەنها بۆ گەورە)">
    <input type="text" id="appUrl" placeholder="بەستەری دابه‌زاندن (URL)">
    <button id="addAppBtn">➕ زیاد بکە</button>

    <h3>🗑️ سڕینەوە</h3>
    <select id="deleteSelect"></select>
    <button id="deleteAppBtn">🗑️ سڕینەوە</button>

    <h3>📋 هەموو بەرنامەکان</h3>
    <div id="adminItemList"></div>
    <p style="font-size:11px; margin-top:15px; color:#888;">🔒 پەسوۆرد: 7AJI2024</p>
</div>

<div class="container">
    <div class="hacked-header"><div class="hacked-text">🔥 7AJI-IOS 🔥</div></div>
    <div class="hero-card">
        <div class="animated-line"><span class="word-special">بگەڕێ</span><span class="word">له</span><span class="word">سۆرس</span><span class="word">زیاتر</span><span class="word">له</span></div>
        <div class="hero-number">🔥 100,000 هەزار بەرنامە 🔥</div>
        <div><span class="hero-badge">🚀 کاراوه‌ بو هه‌موو ئایفۆنێک</span><span class="hero-badge">Cracked iOS Store</span></div>
    </div>
    <div class="section"><div class="section-header"><h3>📱 Apps for You</h3></div><div class="scroll-horizontal" id="appsForYou"></div></div>
    <div class="section"><div class="section-header"><h3>🔓 Tweaked Apps</h3></div><div class="scroll-horizontal" id="tweakedApps"></div></div>
    <div class="section"><div class="section-header"><h3>🔄 Recently Updated</h3></div><div class="scroll-horizontal" id="recentlyUpdated"></div></div>
</div>

<div class="tab-bar">
    <div class="tab-item active"><div class="tab-icon">🏠</div><span>Home</span></div>
    <div class="tab-item"><div class="tab-icon">📦</div><span>Apps</span></div>
    <div class="tab-item"><div class="tab-icon">🔍</div><span>Search</span></div>
    <div class="tab-item"><div class="tab-icon">👑</div><span>VIP</span></div>
    <div class="tab-item"><div class="tab-icon">⚙️</div><span>More</span></div>
</div>
<div id="toastMsg" class="toast"></div>

<script>
    let appsData = {
        normal: [
            { name: "Facebook", icon: "https://upload.wikimedia.org/wikipedia/commons/5/51/Facebook_f_logo_2019.svg", url: "#" },
            { name: "Instagram", icon: "https://upload.wikimedia.org/wikipedia/commons/e/e7/Instagram_logo_2016.svg", url: "#" },
            { name: "WhatsApp", icon: "https://upload.wikimedia.org/wikipedia/commons/6/6b/WhatsApp.svg", url: "#" },
            { name: "Telegram", icon: "https://upload.wikimedia.org/wikipedia/commons/8/82/Telegram_logo.svg", url: "#" }
        ],
        tweaked: [
            { name: "NIVI+", icon: "🎧", desc: "Premium Unlocked", url: "#" },
            { name: "Zen7 VPN", icon: "🔒", desc: "VIP Servers", url: "#" }
        ],
        recent: [
            { name: "Snapchat Unban", icon: "👻", sub: "IP + Hidden", url: "#" },
            { name: "Clash Royale", icon: "⚔️", sub: "Unlimited", url: "#" }
        ]
    };

    let pendingImageData = null; // بۆ هەڵگرتنی وێنەی base64 یان URL

    function saveToLocal() { localStorage.setItem("7AJI_APPS_V3", JSON.stringify(appsData)); }
    function loadFromLocal() { const s = localStorage.getItem("7AJI_APPS_V3"); if (s) appsData = JSON.parse(s); }

    function renderIcon(icon) {
        if (!icon) return '<span>📦</span>';
        if (icon.startsWith("http")) return `<img src="${icon}" onerror="this.style.display='none'; this.parentElement.innerHTML='📦'">`;
        if (icon.startsWith("data:image")) return `<img src="${icon}">`;
        return `<span>${icon}</span>`;
    }

    function renderNormal() {
        const container = document.getElementById('appsForYou');
        container.innerHTML = '';
        appsData.normal.forEach(app => {
            const card = document.createElement('div');
            card.className = 'app-card';
            card.innerHTML = `
                <div class="app-icon">${renderIcon(app.icon)}</div>
                <div class="app-name">${app.name}</div>
                <div class="get-btn" data-url="${app.url}" data-name="${app.name}">GET</div>
            `;
            container.appendChild(card);
        });
        attachGetButtons();
    }

    function renderTweaked() {
        const container = document.getElementById('tweakedApps');
        container.innerHTML = '';
        appsData.tweaked.forEach(app => {
            const card = document.createElement('div');
            card.className = 'big-app-card';
            card.innerHTML = `
                <div class="big-app-row">
                    <div class="big-icon">${renderIcon(app.icon)}</div>
                    <div class="big-info"><div class="big-title">${app.name}</div><div class="big-sub">${app.desc || ''}</div></div>
                    <div class="big-get" data-url="${app.url}" data-name="${app.name}">GET</div>
                </div>
            `;
            container.appendChild(card);
        });
        attachBigGetButtons();
    }

    function renderRecent() {
        const container = document.getElementById('recentlyUpdated');
        container.innerHTML = '';
        appsData.recent.forEach(app => {
            const card = document.createElement('div');
            card.className = 'big-app-card';
            card.innerHTML = `
                <div class="big-app-row">
                    <div class="big-icon">${renderIcon(app.icon)}</div>
                    <div class="big-info"><div class="big-title">${app.name}</div><div class="big-sub">${app.sub || ''}</div></div>
                    <div class="big-get" data-url="${app.url}" data-name="${app.name}">GET</div>
                </div>
            `;
            container.appendChild(card);
        });
        attachBigGetButtons();
    }

    function attachGetButtons() {
        document.querySelectorAll('.get-btn, .big-get').forEach(btn => {
            btn.onclick = (e) => {
                e.stopPropagation();
                const url = btn.getAttribute('data-url');
                const name = btn.getAttribute('data-name');
                if (url && url !== "#") { window.open(url, '_blank'); showToast(`📥 دابه‌زاندنی ${name}`); }
                else showToast(`⚠️ بەستەر نییە بۆ ${name}`);
            };
        });
    }
    function attachBigGetButtons() { attachGetButtons(); }

    function updateAdminList() {
        const container = document.getElementById('adminItemList');
        const select = document.getElementById('deleteSelect');
        container.innerHTML = ''; select.innerHTML = '';
        const all = [...appsData.normal.map(a=>({...a, type:'normal'})), ...appsData.tweaked.map(a=>({...a, type:'tweaked'})), ...appsData.recent.map(a=>({...a, type:'recent'}))];
        all.forEach((app) => {
            const div = document.createElement('div');
            div.className = 'admin-item';
            div.innerHTML = `<span>${typeof app.icon === 'string' && app.icon.length<20 ? app.icon : '🖼️'} ${app.name} (${app.type})</span><button onclick="editApp('${app.type}', '${app.name.replace(/'/g, "\\'")}')">✏️</button>`;
            container.appendChild(div);
            const opt = document.createElement('option');
            opt.value = `${app.type}|${app.name}`;
            opt.textContent = `${app.name} (${app.type})`;
            select.appendChild(opt);
        });
    }

    window.editApp = (type, name) => {
        const idx = appsData[type].findIndex(a => a.name === name);
        if (idx === -1) return;
        const app = appsData[type][idx];
        const newUrl = prompt("بەستەری دابه‌زاندن:", app.url);
        if (newUrl !== null) app.url = newUrl;
        const newName = prompt("ناوی نوێ:", app.name);
        if (newName !== null) app.name = newName;
        const newIcon = prompt("لۆگۆ (بەستەری وێنە یان ئیمۆجی):", app.icon);
        if (newIcon !== null) app.icon = newIcon;
        saveToLocal();
        renderAll();
        showToast("✅ دەستکاری کرا");
    };

    function renderAll() { renderNormal(); renderTweaked(); renderRecent(); updateAdminList(); }

    // بارکردنی وێنە لە فایل
    const fileInput = document.getElementById('fileInput');
    const uploadBtn = document.getElementById('uploadFileBtn');
    const appIconUrl = document.getElementById('appIconUrl');
    const imagePreview = document.getElementById('imagePreview');

    uploadBtn.onclick = () => fileInput.click();
    fileInput.onchange = (e) => {
        const file = e.target.files[0];
        if (file && file.type.startsWith('image/')) {
            const reader = new FileReader();
            reader.onload = function(ev) {
                const base64 = ev.target.result;
                pendingImageData = base64;
                imagePreview.innerHTML = `<img src="${base64}" style="width:100%;height:100%;object-fit:cover;">`;
                appIconUrl.value = base64;
            };
            reader.readAsDataURL(file);
        } else { showToast("⚠️ تکایە وێنە هەڵبژێرە"); }
    };

    appIconUrl.oninput = function() {
        let val = this.value;
        if (val.startsWith("http") || val.startsWith("data:image")) {
            imagePreview.innerHTML = `<img src="${val}" style="width:100%;height:100%;object-fit:cover;" onerror="this.parentElement.innerHTML='📦'">`;
        } else {
            imagePreview.innerHTML = val || "📦";
        }
    };

    document.getElementById('addAppBtn').onclick = () => {
        let name = document.getElementById('appName').value.trim();
        let icon = document.getElementById('appIconUrl').value.trim();
        let type = document.getElementById('appType').value;
        let desc = document.getElementById('appDesc').value.trim();
        let url = document.getElementById('appUrl').value.trim();
        if (!name) { showToast("⚠️ ناو بنووسە"); return; }
        let newApp = { name, icon: icon || "📦", url: url || "#" };
        if (type === 'normal') appsData.normal.push(newApp);
        else if (type === 'tweaked') appsData.tweaked.push({ ...newApp, desc: desc || "Cracked" });
        else appsData.recent.push({ ...newApp, sub: desc || "Updated" });
        saveToLocal(); renderAll();
        showToast(`➕ ${name} زیاد کرا`);
        document.getElementById('appName').value = '';
        document.getElementById('appIconUrl').value = '';
        document.getElementById('appDesc').value = '';
        document.getElementById('appUrl').value = '';
        imagePreview.innerHTML = "📦";
        pendingImageData = null;
    };

    document.getElementById('deleteAppBtn').onclick = () => {
        let val = document.getElementById('deleteSelect').value;
        if (!val) return;
        let [type, name] = val.split('|');
        let idx = appsData[type].findIndex(a => a.name === name);
        if (idx !== -1) appsData[type].splice(idx, 1);
        saveToLocal(); renderAll();
        showToast("🗑️ سڕایەوە");
    };

    function showToast(msg) {
        const toast = document.getElementById('toastMsg');
        toast.textContent = msg;
        toast.style.opacity = '1';
        setTimeout(() => toast.style.opacity = '0', 2000);
    }

    // ئەدمن نهێنی
    const secretBtn = document.getElementById('secretAdminBtn');
    const modal = document.getElementById('passwordModal');
    const adminPanel = document.getElementById('adminPanel');
    const closeAdmin = document.getElementById('closeAdminBtn');
    const submitPass = document.getElementById('submitPasswordBtn');
    const passInput = document.getElementById('adminPassword');

    secretBtn.onclick = () => modal.classList.add('open');
    submitPass.onclick = () => {
        if (passInput.value === "7AJI2024") {
            modal.classList.remove('open');
            adminPanel.classList.add('open');
            passInput.value = "";
        } else { showToast("❌ پەسوۆرد هەڵەیە"); }
    };
    closeAdmin.onclick = () => adminPanel.classList.remove('open');

    loadFromLocal(); renderAll();
    document.querySelectorAll('.tab-item').forEach(t => t.onclick = function() {
        document.querySelectorAll('.tab-item').forEach(tab=>tab.classList.remove('active'));
        this.classList.add('active');
        showToast(`✨ بەشی ${this.querySelector('span').innerText}`);
    });
</script>
</body>
</html>
