<!DOCTYPE html>
<html lang="ckb">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
    <title>7AJI-IOS - خەزێنەی ئەپ و یارییەکان</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: -apple-system, 'Helvetica Neue', 'Segoe UI', Roboto, sans-serif;
        }
        body {
            background: linear-gradient(145deg, #0a0a0a 0%, #1a1a2e 100%);
            min-height: 100vh;
            padding: 20px;
        }
        .container {
            max-width: 500px;
            margin: 0 auto;
        }
        .header {
            text-align: center;
            margin-bottom: 20px;
        }
        .header h1 {
            font-size: 32px;
            font-weight: 800;
            background: linear-gradient(135deg, #FF6B6B, #4ECDC4);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin-bottom: 8px;
        }
        .lang-switch {
            display: flex;
            justify-content: center;
            gap: 12px;
            margin: 15px 0;
        }
        .lang-btn {
            background: rgba(255,255,255,0.15);
            border: none;
            padding: 6px 16px;
            border-radius: 30px;
            color: white;
            font-weight: 600;
            cursor: pointer;
            transition: 0.2s;
            font-size: 14px;
        }
        .lang-btn.active {
            background: #007AFF;
        }
        .welcome-section {
            margin-bottom: 25px;
        }
        .welcome-card {
            background: linear-gradient(135deg, rgba(255,107,107,0.25), rgba(78,205,196,0.25));
            backdrop-filter: blur(12px);
            border-radius: 32px;
            padding: 30px 20px;
            text-align: center;
            border: 1px solid rgba(255,255,255,0.15);
            box-shadow: 0 8px 25px rgba(0,0,0,0.2);
        }
        .welcome-icon {
            font-size: 60px;
            margin-bottom: 10px;
            display: inline-block;
            animation: heartbeat 1s ease-in-out infinite, rainbowGlow 2.5s infinite;
            cursor: default;
        }
        @keyframes heartbeat {
            0%, 100% { transform: scale(1); }
            25% { transform: scale(1.2); }
            35% { transform: scale(1.1); }
            45% { transform: scale(1.25); }
            55% { transform: scale(1.1); }
        }
        @keyframes rainbowGlow {
            0% { text-shadow: 0 0 3px #ff3b3b; }
            25% { text-shadow: 0 0 8px #ff9f3b; }
            50% { text-shadow: 0 0 8px #3bff3b; }
            75% { text-shadow: 0 0 8px #3b9fff; }
            100% { text-shadow: 0 0 3px #ff3b3b; }
        }
        .welcome-text h3 {
            font-size: 28px;
            font-weight: 800;
            background: linear-gradient(135deg, #FFFFFF, #FFD93D);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin: 0;
            letter-spacing: 1px;
        }
        .app-card {
            background: rgba(30,30,50,0.9);
            backdrop-filter: blur(10px);
            border-radius: 24px;
            padding: 16px;
            margin-bottom: 16px;
            display: flex;
            align-items: center;
            gap: 15px;
            border: 1px solid rgba(255,255,255,0.1);
        }
        .app-icon {
            width: 60px;
            height: 60px;
            border-radius: 16px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 28px;
            font-weight: bold;
            color: white;
            background: linear-gradient(135deg, #667eea, #764ba2);
            background-size: cover;
            background-position: center;
        }
        .app-info {
            flex: 1;
        }
        .app-name {
            font-size: 20px;
            font-weight: 700;
            color: white;
        }
        .app-status {
            font-size: 13px;
            color: #4CD964;
            margin: 4px 0;
        }
        .rating {
            color: #FFD93D;
            font-size: 12px;
        }
        .download-btn {
            background: linear-gradient(135deg, #007AFF, #5856D6);
            border: none;
            padding: 10px 20px;
            border-radius: 30px;
            color: white;
            font-weight: 600;
            font-size: 14px;
            cursor: pointer;
        }
        .download-btn:active {
            transform: scale(0.95);
        }
        .admin-panel {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 1000;
        }
        .admin-toggle {
            background: #FF3B30;
            width: 55px;
            height: 55px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
            border: none;
            color: white;
        }
        .admin-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.95);
            backdrop-filter: blur(15px);
            z-index: 2000;
            display: none;
            justify-content: center;
            align-items: center;
            padding: 20px;
            overflow-y: auto;
        }
        .admin-modal.active {
            display: flex;
        }
        .admin-content.new-style {
            background: linear-gradient(145deg, #1a1a2e, #16213e);
            border-radius: 32px;
            padding: 24px;
            width: 100%;
            max-width: 450px;
            max-height: 90vh;
            overflow-y: auto;
            color: white;
        }
        .admin-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }
        .logout-small {
            background: #FF3B30 !important;
            padding: 8px 16px !important;
            width: auto !important;
            font-size: 13px !important;
        }
        .form-group {
            margin-bottom: 18px;
        }
        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-size: 14px;
            color: #aaa;
            font-weight: 500;
        }
        .form-group input, .form-group select, .form-group textarea {
            width: 100%;
            padding: 14px;
            border-radius: 16px;
            background: #0f0f1a;
            border: 1px solid rgba(255,255,255,0.1);
            color: white;
            font-size: 15px;
        }
        .form-group textarea {
            resize: vertical;
            font-family: inherit;
        }
        .form-row {
            display: flex;
            gap: 15px;
        }
        .form-group.half {
            flex: 1;
        }
        .image-picker {
            display: flex;
            gap: 15px;
            align-items: center;
            flex-wrap: wrap;
        }
        .image-preview {
            width: 70px;
            height: 70px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            border-radius: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 32px;
            background-size: cover;
            background-position: center;
        }
        .image-options {
            flex: 1;
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
        }
        .small-btn {
            background: #2a2a3e;
            padding: 8px 12px;
            border-radius: 25px;
            font-size: 12px;
            width: auto;
            display: inline-flex;
            align-items: center;
            gap: 5px;
            border: none;
            color: white;
            cursor: pointer;
        }
        .small-btn.upload {
            background: #4CD964;
        }
        .small-btn.camera {
            background: #FF9500;
        }
        .image-url-input {
            margin-top: 8px;
            width: 100%;
        }
        .type-switch {
            display: flex;
            gap: 10px;
            background: #0f0f1a;
            border-radius: 30px;
            padding: 4px;
        }
        .type-option {
            flex: 1;
            background: transparent;
            border: none;
            padding: 10px;
            border-radius: 26px;
            color: #aaa;
            cursor: pointer;
            font-weight: 600;
        }
        .type-option.active {
            background: #007AFF;
            color: white;
        }
        .submit-btn {
            background: linear-gradient(135deg, #4CD964, #007AFF);
            font-size: 16px;
            padding: 14px;
            margin-top: 10px;
            border: none;
            border-radius: 30px;
            color: white;
            font-weight: bold;
            width: 100%;
            cursor: pointer;
        }
        .admin-list {
            margin-top: 20px;
        }
        .admin-item {
            background: #0f0f1a;
            border-radius: 20px;
            padding: 14px;
            margin-bottom: 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border: 1px solid rgba(255,255,255,0.05);
        }
        .delete-btn {
            background: #FF3B30;
            padding: 8px 16px;
            border-radius: 20px;
            font-size: 12px;
            width: auto;
            border: none;
            color: white;
            cursor: pointer;
        }
        .close-btn {
            background: #555;
            margin-top: 15px;
            padding: 12px;
            border-radius: 30px;
            width: 100%;
            border: none;
            color: white;
            cursor: pointer;
        }
        .app-type {
            font-size: 10px;
            color: #FF9500;
        }
        @media (max-width: 500px) {
            body { padding: 15px; }
            .download-btn { padding: 8px 16px; font-size: 12px; }
            .app-name { font-size: 17px; }
            .welcome-text h3 { font-size: 22px; }
        }
    </style>
</head>
<body>
<div class="container">
    <div class="header">
        <h1>📱 7AJI-IOS</h1>
        <div class="lang-switch">
            <button class="lang-btn" data-lang="ckb">کوردی</button>
            <button class="lang-btn" data-lang="ar">العربية</button>
            <button class="lang-btn" data-lang="en">English</button>
        </div>
    </div>

    <div class="welcome-section">
        <div class="welcome-card">
            <div class="welcome-icon">🫶</div>
            <div class="welcome-text">
                <h3 id="welcomeTitle">WELCOME to 7AJI-IOS</h3>
            </div>
        </div>
    </div>

    <div id="appsList"></div>
</div>

<div class="admin-panel">
    <button class="admin-toggle" id="adminToggleBtn">⚙️</button>
</div>

<div class="admin-modal" id="adminModal">
    <div class="admin-content new-style">
        <div id="adminLoginView">
            <h3 id="loginTitle">🔐 چوونەژوورەوەی بەڕێوەبەر</h3>
            <input type="password" id="adminPassword" placeholder="تێپەڕەوشە">
            <button id="loginBtn" class="submit-btn">چوونەژوورەوە</button>
            <button class="close-btn" id="closeModalBtn">داخستن</button>
        </div>
        <div id="adminDashboardView" style="display:none;">
            <div class="admin-header">
                <h3 id="dashboardTitle">✨ زیادکردن / دەستکاری ئەپ</h3>
                <button id="logoutBtn" class="logout-small">🚪 دەرچوون</button>
            </div>
            
            <div class="form-group">
                <label>📱 ناوی ئەپ / یاری</label>
                <input type="text" id="appName" placeholder="بۆ نموونە: Facebook, Instagram...">
            </div>
            
            <div class="form-group">
                <label>🔗 لینکی ڕاستەوخۆی داونلۆد</label>
                <input type="url" id="appLink" placeholder="https://example.com/app.ipa">
            </div>
            
            <div class="form-group">
                <label>📝 وەسفی ئەپ و تایبەتمەندییەکان</label>
                <textarea id="appDescription" rows="3" placeholder="ئەم ئەپە چی دەکات؟ چی تایبەتمەندی هەیە؟"></textarea>
            </div>
            
            <div class="form-group">
                <label>🖼️ وێنەی ئەپ (لۆگۆ)</label>
                <div class="image-picker">
                    <div class="image-preview" id="imagePreview">
                        <span>📱</span>
                    </div>
                    <div class="image-options">
                        <button type="button" id="selectEmojiBtn" class="small-btn">😊 ئیمۆجی</button>
                        <button type="button" id="selectColorBtn" class="small-btn">🎨 ڕەنگ</button>
                        <button type="button" id="uploadImageBtn" class="small-btn upload">📸 هەڵبژاردن لە گەلەری</button>
                        <button type="button" id="cameraImageBtn" class="small-btn camera">📷 وێنەگرتن</button>
                        <input type="url" id="imageUrl" placeholder="یان لینکی وێنە..." class="image-url-input">
                    </div>
                </div>
                <input type="file" id="fileInput" accept="image/*" style="display:none">
                <input type="file" id="cameraInput" accept="image/*" capture="environment" style="display:none">
            </div>
            
            <div class="form-row">
                <div class="form-group half">
                    <label>⭐ ڕیتینگ</label>
                    <input type="number" id="appRating" placeholder="1-5" step="0.1" min="1" max="5">
                </div>
                <div class="form-group half">
                    <label>📌 دۆخ</label>
                    <select id="appStatus">
                        <option value="Working">✅ Working</option>
                        <option value="Unlock all Features">🔓 Unlock all Features</option>
                        <option value="Beta">⚠️ Beta</option>
                    </select>
                </div>
            </div>
            
            <div class="form-group">
                <label>🎮 جۆر</label>
                <div class="type-switch">
                    <button type="button" class="type-option active" data-type="app">📱 ئەپ</button>
                    <button type="button" class="type-option" data-type="game">🎮 یاری</button>
                </div>
                <input type="hidden" id="appType" value="app">
            </div>
            
            <button id="addAppBtn" class="submit-btn">✅ زیادکردن</button>
            
            <h4 id="currentAppsTitle" style="margin-top:25px;">📋 ئەپ و یارییەکان</h4>
            <div id="adminAppsList" class="admin-list"></div>
            
            <button class="close-btn" id="closeModalBtn2">داخستن</button>
        </div>
    </div>
</div>

<script>
    let apps = [];

    const translations = {
        ckb: {
            welcomeTitle: "WELCOME to 7AJI-IOS",
            downloadBtn: "داونلۆد",
            noLinkMsg: "⚠️ هیچ لینکێکی ڕاستەوخۆ نییە بۆ ",
            addLinkMsg: "تکایە لینکێکی ڕاستەوخۆ زیاد بکە",
            loginTitle: "🔐 چوونەژوورەوەی بەڕێوەبەر",
            dashboardTitle: "✨ زیادکردن / دەستکاری ئەپ",
            currentAppsTitle: "📋 ئەپ و یارییەکان",
            deleteConfirm: "سڕینەوە؟",
            addedSuccess: "✅ زیاد کرا!",
            wrongPass: "تێپەڕەوشە هەڵەیە!",
            placeholderName: "ناوی ئەپ/یاری",
            placeholderStatus: "دۆخ",
            placeholderRating: "ڕیتینگ (1-5)",
            placeholderLink: "لینکی ڕاستەوخۆ"
        },
        ar: {
            welcomeTitle: "WELCOME to 7AJI-IOS",
            downloadBtn: "تحميل",
            noLinkMsg: "⚠️ لا يوجد رابط مباشر لـ ",
            addLinkMsg: "الرجاء إضافة رابط صحيح",
            loginTitle: "🔐 دخول الأدمن",
            dashboardTitle: "✨ إضافة / تعديل تطبيق",
            currentAppsTitle: "📋 التطبيقات",
            deleteConfirm: "حذف؟",
            addedSuccess: "✅ تمت الإضافة!",
            wrongPass: "كلمة مرور خاطئة!",
            placeholderName: "اسم التطبيق",
            placeholderStatus: "الحالة",
            placeholderRating: "التقييم",
            placeholderLink: "الرابط المباشر"
        },
        en: {
            welcomeTitle: "WELCOME to 7AJI-IOS",
            downloadBtn: "Download",
            noLinkMsg: "⚠️ No direct link for ",
            addLinkMsg: "Please add a valid Direct Link",
            loginTitle: "🔐 Admin Login",
            dashboardTitle: "✨ Add / Edit App",
            currentAppsTitle: "📋 Apps & Games",
            deleteConfirm: "Delete?",
            addedSuccess: "✅ Added!",
            wrongPass: "Wrong password!",
            placeholderName: "App/Game Name",
            placeholderStatus: "Status",
            placeholderRating: "Rating (1-5)",
            placeholderLink: "Direct Link"
        }
    };

    let currentLang = "ckb";

    function updateUI() {
        const t = translations[currentLang];
        document.getElementById("welcomeTitle").innerText = t.welcomeTitle;
        document.getElementById("loginTitle").innerText = t.loginTitle;
        document.getElementById("dashboardTitle").innerText = t.dashboardTitle;
        document.getElementById("currentAppsTitle").innerText = t.currentAppsTitle;
        renderApps();
        if(document.getElementById("adminAppsList").children.length > 0) renderAdminList();
    }

    function loadData() {
        const saved = localStorage.getItem("7aji_ios_apps");
        if(saved) apps = JSON.parse(saved);
        else {
            apps = [
                { name: "Facebook", status: "Working", rating: 4.5, link: "#", description: "Social Media App", iconData: "https://upload.wikimedia.org/wikipedia/commons/5/51/Facebook_f_logo.png", iconType: "url", type: "app" },
                { name: "Instagram", status: "Working", rating: 4.8, link: "#", description: "Photo & Video Sharing", iconData: "https://upload.wikimedia.org/wikipedia/commons/9/95/Instagram_logo_2022.svg", iconType: "url", type: "app" },
                { name: "Gbox", status: "Working", rating: 4.0, link: "#", description: "", iconData: "📦", iconType: "emoji", type: "app" }
            ];
            saveData();
        }
    }
    function saveData() { localStorage.setItem("7aji_ios_apps", JSON.stringify(apps)); }
    loadData();

    function getStars(rating) {
        const full = Math.floor(rating);
        let stars = "★".repeat(full);
        if(rating % 1 >= 0.5) stars += "½";
        stars += "☆".repeat(5 - Math.ceil(rating));
        return stars;
    }
    function escapeHtml(str) {
        if(!str) return "";
        return str.replace(/[&<>]/g, m => m === '&' ? '&amp;' : m === '<' ? '&lt;' : '&gt;');
    }

    function getAppIconHTML(app) {
        if(app.iconType === "url" && app.iconData && app.iconData.startsWith("http")) {
            return `<div class="app-icon" style="background-image: url('${escapeHtml(app.iconData)}'); background-size: cover; background-position: center; font-size: 0;"></div>`;
        } else if(app.iconType === "dataUrl" && app.iconData && app.iconData.startsWith("data:image")) {
            return `<div class="app-icon" style="background-image: url('${app.iconData}'); background-size: cover; background-position: center; font-size: 0;"></div>`;
        } else {
            let emoji = app.iconData || (app.type === "game" ? "🎮" : "📱");
            return `<div class="app-icon" style="font-size:28px; background: linear-gradient(135deg, #667eea, #764ba2);">${emoji}</div>`;
        }
    }

    function renderApps() {
        const container = document.getElementById("appsList");
        if(!container) return;
        container.innerHTML = "";
        const t = translations[currentLang];
        apps.forEach(app => {
            const card = document.createElement("div");
            card.className = "app-card";
            card.innerHTML = `
                ${getAppIconHTML(app)}
                <div class="app-info">
                    <div class="app-name">${escapeHtml(app.name)} <span class="app-type">${app.type === "game" ? "🎮 یاری" : "📱 ئەپ"}</span></div>
                    <div class="app-status">${escapeHtml(app.status)}</div>
                    <div class="rating">⭐ ${app.rating.toFixed(1)} (${getStars(app.rating)})</div>
                    ${app.description ? `<div style="font-size:11px; color:#888; margin-top:4px;">${escapeHtml(app.description.substring(0, 50))}</div>` : ''}
                </div>
                <button class="download-btn" data-link="${escapeHtml(app.link)}" data-name="${escapeHtml(app.name)}">${t.downloadBtn}</button>
            `;
            container.appendChild(card);
        });
        document.querySelectorAll('.download-btn').forEach(btn => {
            btn.addEventListener('click', () => {
                const link = btn.getAttribute('data-link');
                const name = btn.getAttribute('data-name');
                if(link && link !== "#") window.location.href = link;
                else alert(translations[currentLang].noLinkMsg + name + "\n" + translations[currentLang].addLinkMsg);
            });
        });
    }

    function renderAdminList() {
        const container = document.getElementById("adminAppsList");
        if(!container) return;
        container.innerHTML = "";
        apps.forEach((app, idx) => {
            const div = document.createElement("div");
            div.className = "admin-item";
            div.innerHTML = `
                <div><strong>${escapeHtml(app.name)}</strong> (${app.type === "game" ? "یاری" : "ئەپ"}) - ⭐ ${app.rating}<br><small>${escapeHtml(app.link.substring(0, 35))}</small></div>
                <button class="delete-btn" data-idx="${idx}">سڕینەوە</button>
            `;
            container.appendChild(div);
        });
        document.querySelectorAll('.delete-btn').forEach(btn => {
            btn.addEventListener('click', () => {
                if(confirm(translations[currentLang].deleteConfirm)) {
                    apps.splice(parseInt(btn.getAttribute('data-idx')), 1);
                    saveData();
                    renderApps();
                    renderAdminList();
                }
            });
        });
    }

    const modal = document.getElementById("adminModal");
    const loginView = document.getElementById("adminLoginView");
    const dashboardView = document.getElementById("adminDashboardView");
    let isLoggedIn = false;

    document.getElementById("adminToggleBtn").onclick = () => {
        if(isLoggedIn) {
            dashboardView.style.display = "block";
            loginView.style.display = "none";
            renderAdminList();
        } else {
            loginView.style.display = "block";
            dashboardView.style.display = "none";
            document.getElementById("adminPassword").value = "";
        }
        modal.classList.add("active");
    };
    const closeModal = () => modal.classList.remove("active");
    document.getElementById("closeModalBtn").onclick = closeModal;
    document.getElementById("closeModalBtn2").onclick = closeModal;
    document.getElementById("loginBtn").onclick = () => {
        if(document.getElementById("adminPassword").value === "7aji2024") {
            isLoggedIn = true;
            loginView.style.display = "none";
            dashboardView.style.display = "block";
            renderAdminList();
        } else alert(translations[currentLang].wrongPass);
    };
    document.getElementById("logoutBtn").onclick = () => { isLoggedIn = false; closeModal(); };
    
    document.querySelectorAll(".type-option").forEach(btn => {
        btn.onclick = () => {
            document.querySelectorAll(".type-option").forEach(b => b.classList.remove("active"));
            btn.classList.add("active");
            document.getElementById("appType").value = btn.getAttribute("data-type");
        };
    });

    // Image handling
    const fileInput = document.getElementById("fileInput");
    const cameraInput = document.getElementById("cameraInput");
    const imagePreview = document.getElementById("imagePreview");
    let currentIconData = null;
    let currentIconType = "emoji";

    function updatePreview(data, type) {
        if(type === "emoji") {
            imagePreview.innerHTML = `<span>${data}</span>`;
            imagePreview.style.background = "linear-gradient(135deg, #667eea, #764ba2)";
            imagePreview.style.backgroundSize = "cover";
        } else if(type === "color") {
            imagePreview.innerHTML = `<span>📱</span>`;
            imagePreview.style.background = data;
            imagePreview.style.backgroundSize = "cover";
        } else if(type === "url") {
            imagePreview.innerHTML = ``;
            imagePreview.style.backgroundImage = `url('${data}')`;
            imagePreview.style.backgroundSize = "cover";
            imagePreview.style.backgroundPosition = "center";
        } else if(type === "dataUrl") {
            imagePreview.innerHTML = ``;
            imagePreview.style.backgroundImage = `url('${data}')`;
            imagePreview.style.backgroundSize = "cover";
            imagePreview.style.backgroundPosition = "center";
        }
        currentIconData = data;
        currentIconType = type;
    }

    document.getElementById("selectEmojiBtn").onclick = () => {
        const emojis = ["📱", "🎮", "⚽", "🎬", "📷", "🎵", "🔊", "💡", "🔥", "⭐", "❤️", "🫶", "🎯", "🕹️", "📺", "𝑓", "📘", "📸", "💬", "▶️"];
        const emoji = prompt(`هەڵبژێرە ئیمۆجییەک:\n${emojis.join(" ")}`, "📱");
        if(emoji && emoji.length <= 2) {
            updatePreview(emoji, "emoji");
        }
    };
    
    document.getElementById("selectColorBtn").onclick = () => {
        const color = prompt("ڕەنگی پشتی بۆ ئایکۆنەکە (وەک #FF6B6B یان red):", "#667eea");
        if(color) {
            updatePreview(color, "color");
        }
    };

    document.getElementById("uploadImageBtn").onclick = () => {
        fileInput.click();
    };
    
    document.getElementById("cameraImageBtn").onclick = () => {
        cameraInput.click();
    };
    
    function handleImageFile(file, isCamera = false) {
        if(!file) return;
        const reader = new FileReader();
        reader.onload = function(e) {
            updatePreview(e.target.result, "dataUrl");
        };
        reader.readAsDataURL(file);
    }
    
    fileInput.onchange = (e) => {
        if(e.target.files && e.target.files[0]) {
            handleImageFile(e.target.files[0], false);
        }
        fileInput.value = "";
    };
    
    cameraInput.onchange = (e) => {
        if(e.target.files && e.target.files[0]) {
            handleImageFile(e.target.files[0], true);
        }
        cameraInput.value = "";
    };
    
    document.getElementById("imageUrl").addEventListener("change", (e) => {
        const url = e.target.value.trim();
        if(url && (url.startsWith("http") || url.startsWith("https"))) {
            updatePreview(url, "url");
        }
    });
    
    document.getElementById("addAppBtn").onclick = () => {
        const name = document.getElementById("appName").value.trim();
        const link = document.getElementById("appLink").value.trim();
        const description = document.getElementById("appDescription").value.trim();
        const rating = parseFloat(document.getElementById("appRating").value);
        const status = document.getElementById("appStatus").value;
        const type = document.getElementById("appType").value;
        
        let iconData = currentIconData;
        let iconType = currentIconType;
        
        if(!iconData) {
            iconData = type === "game" ? "🎮" : "📱";
            iconType = "emoji";
        }
        
        if(!name || !link || isNaN(rating) || rating < 1 || rating > 5) {
            alert("تکایە ناو، لینک و ڕیتینگێکی دروست پڕبکەوە");
            return;
        }
        
        apps.push({ name, status, rating, link, description, iconData, iconType, type });
        saveData();
        renderApps();
        renderAdminList();
        
        document.getElementById("appName").value = "";
        document.getElementById("appLink").value = "";
        document.getElementById("appDescription").value = "";
        document.getElementById("appRating").value = "";
        document.getElementById("imageUrl").value = "";
        updatePreview(null, "emoji");
        currentIconData = null;
        currentIconType = "emoji";
        imagePreview.innerHTML = `<span>📱</span>`;
        imagePreview.style.background = "linear-gradient(135deg, #667eea, #764ba2)";
        
        alert(translations[currentLang].addedSuccess);
    };

    document.querySelectorAll(".lang-btn").forEach(btn => {
        btn.onclick = () => {
            document.querySelectorAll(".lang-btn").forEach(b => b.classList.remove("active"));
            btn.classList.add("active");
            currentLang = btn.getAttribute("data-lang");
            updateUI();
        };
    });
    document.querySelector(".lang-btn[data-lang='ckb']").classList.add("active");
    updateUI();
</script>
</body>
</html>
