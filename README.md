 <!DOCTYPE html>
<html lang="ku">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
    <title>7AJI-IOS | دابەزاندنی IPAی سلڤەر | بەڕێوەبەری فایل</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,600;14..32,700;14..32,800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: radial-gradient(circle at 20% 30%, #0b0e17, #03050a);
            font-family: 'Inter', system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
            color: #eef2ff;
            min-height: 100vh;
            padding: 24px;
            position: relative;
            overflow-x: auto;
        }

        /* سلڤەر شەپۆل */
        body::before {
            content: '';
            position: fixed;
            width: 150%;
            height: 150%;
            top: -25%;
            left: -25%;
            background: radial-gradient(ellipse at 30% 50%, rgba(192, 200, 240, 0.08) 0%, rgba(40, 45, 80, 0) 70%);
            pointer-events: none;
            z-index: 0;
            animation: slowDrift 24s infinite alternate;
        }

        @keyframes slowDrift {
            0% { transform: translate(0,0) scale(1); opacity: 0.5; }
            100% { transform: translate(2%, 1%) scale(1.1); opacity: 1; }
        }

        .glass-container {
            max-width: 1300px;
            margin: 0 auto;
            position: relative;
            z-index: 10;
        }

        /* سلڤەر کارتەکان */
        .silver-header {
            background: rgba(15, 20, 32, 0.65);
            backdrop-filter: blur(16px);
            border-radius: 56px;
            padding: 20px 32px;
            margin-bottom: 32px;
            border: 1px solid rgba(210, 220, 255, 0.3);
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 15px 35px rgba(0,0,0,0.3);
        }

        .logo-area h1 {
            font-size: 1.9rem;
            font-weight: 800;
            background: linear-gradient(135deg, #FFFFFF, #b9c4f0);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        .logo-area p {
            font-size: 0.8rem;
            color: #a7b3da;
        }

        .admin-trigger {
            background: rgba(60, 70, 110, 0.6);
            border: 1px solid rgba(200, 210, 255, 0.5);
            padding: 10px 24px;
            border-radius: 60px;
            cursor: pointer;
            transition: 0.2s;
            font-weight: 500;
        }
        .admin-trigger:hover {
            background: rgba(100, 115, 170, 0.8);
            transform: scale(0.97);
        }

        /* کارتی فایلەکان (ڕووکاری گشتی) */
        .files-section {
            background: rgba(12, 16, 27, 0.55);
            backdrop-filter: blur(12px);
            border-radius: 52px;
            border: 1px solid rgba(180, 190, 230, 0.4);
            padding: 28px 24px;
            margin-bottom: 30px;
        }

        .section-title {
            font-size: 1.7rem;
            font-weight: 700;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 12px;
            border-left: 4px solid #cbd5ff;
            padding-left: 20px;
        }

        .grid-ipa {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 22px;
            margin-top: 10px;
        }

        .ipa-card {
            background: rgba(20, 26, 45, 0.7);
            border-radius: 38px;
            padding: 20px;
            border: 1px solid rgba(210, 215, 250, 0.25);
            transition: all 0.2s;
            backdrop-filter: blur(4px);
        }
        .ipa-card:hover {
            border-color: rgba(210, 220, 255, 0.7);
            transform: translateY(-4px);
            background: rgba(28, 34, 58, 0.8);
        }
        .ipa-name {
            font-weight: 800;
            font-size: 1.25rem;
            word-break: break-all;
            margin-bottom: 8px;
        }
        .ipa-meta {
            font-size: 0.7rem;
            color: #b7c3ea;
            margin: 10px 0;
        }
        .btn-download {
            background: linear-gradient(95deg, #2a2f48, #1a1e32);
            border: none;
            padding: 10px 0;
            width: 100%;
            border-radius: 44px;
            color: white;
            font-weight: 600;
            cursor: pointer;
            margin-top: 12px;
            transition: 0.2s;
            font-family: inherit;
        }
        .btn-download:hover {
            background: #3e4570;
        }

        /* پەڕەی ئەدمین (modal-like) */
        .admin-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.75);
            backdrop-filter: blur(10px);
            z-index: 1000;
            display: flex;
            align-items: center;
            justify-content: center;
            visibility: hidden;
            opacity: 0;
            transition: 0.2s;
        }
        .admin-overlay.active {
            visibility: visible;
            opacity: 1;
        }
        .admin-panel {
            background: #0f1322e6;
            backdrop-filter: blur(28px);
            border-radius: 64px;
            width: 90%;
            max-width: 600px;
            padding: 32px;
            border: 1px solid silver;
            box-shadow: 0 30px 50px black;
        }
        .admin-panel h2 {
            margin-bottom: 20px;
        }
        .admin-input {
            background: #1e233b;
            border: 1px solid #5e6b9b;
            padding: 14px 18px;
            border-radius: 48px;
            width: 100%;
            margin: 12px 0;
            color: white;
            font-size: 1rem;
        }
        .admin-btn {
            background: #2c3353;
            border: none;
            padding: 12px 18px;
            border-radius: 44px;
            font-weight: bold;
            margin-right: 12px;
            cursor: pointer;
        }
        .danger-btn {
            background: #632c3c;
        }
        .file-list-admin {
            max-height: 200px;
            overflow-y: auto;
            margin: 20px 0;
            background: #090c18;
            border-radius: 32px;
            padding: 10px;
        }
        .admin-file-item {
            display: flex;
            justify-content: space-between;
            padding: 8px 12px;
            border-bottom: 1px solid #2f3760;
        }
        .close-admin {
            float: right;
            font-size: 26px;
            cursor: pointer;
        }

        @media (max-width: 650px) {
            .silver-header { flex-direction: column; gap: 15px; align-items: start; }
            .section-title { font-size: 1.3rem; }
        }
        .toast-msg {
            position: fixed;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            background: #1e2a3a;
            backdrop-filter: blur(12px);
            padding: 10px 22px;
            border-radius: 60px;
            z-index: 1100;
            color: white;
            border-left: 5px solid silver;
        }
        footer {
            text-align: center;
            margin-top: 20px;
            font-size: 0.75rem;
            opacity: 0.7;
        }
    </style>
</head>
<body>
<div class="glass-container">
    <div class="silver-header">
        <div class="logo-area">
            <h1><i class="fas fa-gem"></i> 7AJI-IOS</h1>
            <p>دابەزاندنی IPAی سلڤەر | بەڕێوەبەری فایلەکان | تەنها ئەدمین دەتوانێت زیاد/سڕینەوە بکات</p>
        </div>
        <div class="admin-trigger" id="openAdminBtn">
            <i class="fas fa-lock"></i> پەڕەی ئەدمین <i class="fas fa-user-shield"></i>
        </div>
    </div>

    <!-- نمایش فایلەکانی IPA -->
    <div class="files-section">
        <div class="section-title">
            <i class="fas fa-mobile-alt"></i> فایلە بەردەستەکانی IPA • 7AJI-IOS
        </div>
        <div id="ipaGrid" class="grid-ipa">
            <!-- کارتەکان لێرە بە داینامیک نمایش دەکرێن -->
            <div class="ipa-card" style="text-align:center; justify-content:center;"><i class="fas fa-spinner fa-pulse"></i> بارکردن...</div>
        </div>
    </div>
    <footer>
        <i class="fas fa-shield-alt"></i> سیستمە پارێزراوی 7AJI-IOS • تەنها ئەدمین دەتوانێت فایل زیاد/سڕینەوە بکات
    </footer>
</div>

<!-- ئەدمین پۆرتاڵ -->
<div id="adminOverlay" class="admin-overlay">
    <div class="admin-panel">
        <span class="close-admin" id="closeAdminBtn">&times;</span>
        <h2><i class="fas fa-crown"></i> بەڕێوەبەری 7AJI-IOS</h2>
        <input type="password" id="adminPassInput" class="admin-input" placeholder="نهێنی‌وشەی ئەدمین">
        <button id="loginAdminBtn" class="admin-btn"><i class="fas fa-key"></i> چوونەژوورە</button>
        <div id="adminContent" style="display: none; margin-top: 20px;">
            <h3><i class="fas fa-upload"></i> زیادکردنی IPAی نوێ</h3>
            <input type="file" id="ipaFileUpload" accept=".ipa" class="admin-input">
            <button id="uploadIpaBtn" class="admin-btn"><i class="fas fa-cloud-upload-alt"></i> بارکردن</button>
            
            <h3 style="margin-top: 24px;"><i class="fas fa-trash-alt"></i> سڕینەوەی فایلەکان</h3>
            <div id="adminFileList" class="file-list-admin">هیچ فایلێک نییە</div>
            <button id="logoutAdminBtn" class="admin-btn" style="background:#373d66;"><i class="fas fa-sign-out-alt"></i> دەرچوون</button>
        </div>
    </div>
</div>

<script>
    // -------------------- سیستەمی بەڕێوەبردنی فایلەکان بە IndexedDB (بێ وەستان) --------------------
    // تەواوی فایلەکانی IPA لە ناوخۆی IndexedDB دەپارێزین. بەم شێوەیە، دوای داخستنی وێبسایت فایلەکان نامێنن؟
    // IndexedDB بەردەوامە و هەر لەسەر browser به‌دی دەمێنێت. بۆ ئەوەی بەڕاستی "بێ وەستان" بێت، database local storage + IndexedDB.
    // بەڵام ئێمە فایلەکان و metadata لە IndexedDB دەخەینەوە، هەر بۆیە دوای refresh هەموو فایلەکان دەمێننەوە. وەک بەڕێوەبەرێکی خۆجێی.
    
    const DB_NAME = '7AJI_IOS_DB';
    const DB_VERSION = 2;
    const STORE_NAME = 'ipa_files';
    const ADMIN_PASSWORD = '7aji2025silver'; // پاسپۆرتی ئەدمین - دەتوانی بیگۆڕیت بە شتێکی تایبەت

    let db = null;
    let currentAdmin = false; // ئایا ئەدمین چووە ژوورەوە
    let ipaList = []; // هەڵگرتنی لیستی فایلەکان بۆ نمایش

    // کردنەوە و دروستکردنی داتابەیس
    function initDB() {
        return new Promise((resolve, reject) => {
            const request = indexedDB.open(DB_NAME, DB_VERSION);
            request.onerror = (e) => reject('IndexedDB هەڵەیە');
            request.onsuccess = (e) => {
                db = e.target.result;
                resolve(db);
            };
            request.onupgradeneeded = (e) => {
                const dbUp = e.target.result;
                if (!dbUp.objectStoreNames.contains(STORE_NAME)) {
                    const store = dbUp.createObjectStore(STORE_NAME, { keyPath: 'id', autoIncrement: true });
                    store.createIndex('filename', 'filename', { unique: false });
                }
            };
        });
    }

    // زیادکردنی فایلێکی IPA بە dataURL یان بلۆب
    async function addIPAFile(file) {
        return new Promise((resolve, reject) => {
            const reader = new FileReader();
            reader.onload = (e) => {
                const fileData = e.target.result; // base64 یان dataURL
                const newItem = {
                    filename: file.name,
                    data: fileData,
                    size: file.size,
                    uploadedAt: new Date().toISOString(),
                    mime: file.type || 'application/octet-stream'
                };
                const transaction = db.transaction([STORE_NAME], 'readwrite');
                const store = transaction.objectStore(STORE_NAME);
                const request = store.add(newItem);
                request.onsuccess = () => resolve(true);
                request.onerror = (err) => reject(err);
            };
            reader.onerror = (err) => reject(err);
            reader.readAsDataURL(file);
        });
    }

    // هەموو فایلەکان وەرگرە
    async function getAllIPAFiles() {
        return new Promise((resolve, reject) => {
            const transaction = db.transaction([STORE_NAME], 'readonly');
            const store = transaction.objectStore(STORE_NAME);
            const request = store.getAll();
            request.onsuccess = () => {
                const files = request.result || [];
                resolve(files);
            };
            request.onerror = (e) => reject(e);
        });
    }

    // سڕینەوەی فایل بە ID
    async function deleteIPAFile(id) {
        return new Promise((resolve, reject) => {
            const transaction = db.transaction([STORE_NAME], 'readwrite');
            const store = transaction.objectStore(STORE_NAME);
            const request = store.delete(id);
            request.onsuccess = () => resolve(true);
            request.onerror = (e) => reject(e);
        });
    }

    // نمایش فایلەکان لە grid گشتی
    async function renderPublicGrid() {
        const gridDiv = document.getElementById('ipaGrid');
        if (!gridDiv) return;
        const files = await getAllIPAFiles();
        ipaList = files;
        if (!files.length) {
            gridDiv.innerHTML = `<div class="ipa-card" style="grid-column:1/-1; text-align:center;"><i class="fas fa-info-circle"></i> هیچ فایلێکی IPA بارنەکراوە. ئەدمین دەتوانێت زیاد بکات.</div>`;
            return;
        }
        let html = '';
        files.forEach(file => {
            const sizeMB = (file.size / (1024*1024)).toFixed(2);
            html += `
                <div class="ipa-card">
                    <div class="ipa-name"><i class="fas fa-file-code"></i> ${escapeHtml(file.filename)}</div>
                    <div class="ipa-meta"><i class="fas fa-database"></i> ${sizeMB} MB • ${new Date(file.uploadedAt).toLocaleString()}</div>
                    <button class="btn-download" data-id="${file.id}" data-filename="${escapeHtml(file.filename)}" data-data="${file.data}"><i class="fas fa-download"></i> دابەزاندن</button>
                </div>
            `;
        });
        gridDiv.innerHTML = html;
        // گرێدانی ڕووداوی دابەزاندن
        document.querySelectorAll('.btn-download').forEach(btn => {
            btn.addEventListener('click', (e) => {
                const id = btn.getAttribute('data-id');
                const filename = btn.getAttribute('data-filename');
                const base64Data = btn.getAttribute('data-data');
                if (base64Data) {
                    downloadFromBase64(base64Data, filename);
                } else {
                    // ئەگەر نەبوو، هەوڵبدە لە لیستەوە وەریبگرێت
                    const fileItem = ipaList.find(f => f.id == id);
                    if (fileItem && fileItem.data) downloadFromBase64(fileItem.data, fileItem.filename);
                    else showToast('هەڵە، فایل دەستنەکەوت');
                }
            });
        });
    }

    function downloadFromBase64(base64Data, filename) {
        const link = document.createElement('a');
        link.href = base64Data;
        link.download = filename;
        document.body.appendChild(link);
        link.click();
        document.body.removeChild(link);
        showToast(`دابەزاندنی ${filename} دەستیپێکرد`);
    }

    function escapeHtml(str) {
        if(!str) return '';
        return str.replace(/[&<>]/g, function(m) {
            if(m === '&') return '&amp;';
            if(m === '<') return '&lt;';
            if(m === '>') return '&gt;';
            return m;
        });
    }

    // نمایش لیستی فایلەکان لە ناو ئەدمین بۆ سڕینەوە
    async function renderAdminFileList() {
        const container = document.getElementById('adminFileList');
        if (!container) return;
        const files = await getAllIPAFiles();
        if (!files.length) {
            container.innerHTML = '<em>هیچ فایلێک نییە، فایلێکی IPA باربکە</em>';
            return;
        }
        let html = '';
        files.forEach(file => {
            html += `
                <div class="admin-file-item">
                    <span><i class="fas fa-archive"></i> ${escapeHtml(file.filename)} (${(file.size/1048576).toFixed(2)} MB)</span>
                    <button class="delete-single-btn" data-id="${file.id}" style="background:#883344;border:none;padding:4px 12px;border-radius:30px;color:white;cursor:pointer;"><i class="fas fa-trash"></i> سڕینەوە</button>
                </div>
            `;
        });
        container.innerHTML = html;
        document.querySelectorAll('.delete-single-btn').forEach(btn => {
            btn.addEventListener('click', async (e) => {
                const id = Number(btn.getAttribute('data-id'));
                if(confirm('دڵنیای لە سڕینەوەی ئەم فایلە؟')) {
                    await deleteIPAFile(id);
                    showToast('فایلەکە سڕایەوە');
                    await renderPublicGrid();
                    if(currentAdmin) await renderAdminFileList();
                }
            });
        });
    }

    async function uploadNewFile(file) {
        if(!file || !file.name.endsWith('.ipa')) {
            showToast('تکایە تەنها فایلی .ipa هەڵبژێرە');
            return false;
        }
        await addIPAFile(file);
        showToast(`فایلی ${file.name} بە سەرکەوتوو بارکرا`);
        await renderPublicGrid();
        if(currentAdmin) await renderAdminFileList();
        return true;
    }

    // Toast سادە
    function showToast(msg) {
        let toast = document.querySelector('.toast-msg');
        if(toast) toast.remove();
        let div = document.createElement('div');
        div.className = 'toast-msg';
        div.innerHTML = `<i class="fas fa-bell"></i> ${msg}`;
        document.body.appendChild(div);
        setTimeout(() => div.remove(), 2500);
    }

    // بەشەکانی ئەدمین
    const adminOverlay = document.getElementById('adminOverlay');
    const openAdminBtn = document.getElementById('openAdminBtn');
    const closeAdminBtn = document.getElementById('closeAdminBtn');
    const loginBtn = document.getElementById('loginAdminBtn');
    const adminPassInput = document.getElementById('adminPassInput');
    const adminContentDiv = document.getElementById('adminContent');
    const uploadIpa = document.getElementById('uploadIpaBtn');
    const fileUploadInput = document.getElementById('ipaFileUpload');
    const logoutAdmin = document.getElementById('logoutAdminBtn');

    openAdminBtn.onclick = () => {
        if(currentAdmin) {
            // ڕاستەوخۆ نمایشی پانێڵ
            adminContentDiv.style.display = 'block';
            renderAdminFileList();
            adminOverlay.classList.add('active');
            adminPassInput.style.display = 'none';
            loginBtn.style.display = 'none';
        } else {
            adminPassInput.style.display = 'block';
            loginBtn.style.display = 'inline-block';
            adminContentDiv.style.display = 'none';
            adminPassInput.value = '';
            adminOverlay.classList.add('active');
        }
    };
    closeAdminBtn.onclick = () => adminOverlay.classList.remove('active');
    adminOverlay.onclick = (e) => { if(e.target === adminOverlay) adminOverlay.classList.remove('active'); };

    loginBtn.onclick = () => {
        const pass = adminPassInput.value;
        if(pass === ADMIN_PASSWORD) {
            currentAdmin = true;
            adminContentDiv.style.display = 'block';
            adminPassInput.style.display = 'none';
            loginBtn.style.display = 'none';
            renderAdminFileList();
            showToast('بەخێربێیت ئەدمین، دەتوانیت فایلەکان بەڕێوەبەیت');
        } else {
            showToast('نهێنی‌وشە هەڵەیە');
        }
    };
    logoutAdmin.onclick = () => {
        currentAdmin = false;
        adminContentDiv.style.display = 'none';
        adminPassInput.style.display = 'block';
        loginBtn.style.display = 'inline-block';
        adminOverlay.classList.remove('active');
        showToast('دەرچووت لە بەشی ئەدمین');
    };
    uploadIpa.onclick = () => {
        if(!currentAdmin) { showToast('پێویستە بچیتە ژوورەوە وەک ئەدمین'); return; }
        const file = fileUploadInput.files[0];
        if(file) uploadNewFile(file);
        else showToast('فایلێک هەڵبژێرە');
        fileUploadInput.value = '';
    };

    // دەستپێکردن
    window.addEventListener('load', async () => {
        await initDB();
        await renderPublicGrid();
        currentAdmin = false;
    });
</script>
</body>
</html>
