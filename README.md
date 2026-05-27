<!DOCTYPE html>
<html lang="ku">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
    <title>7AJI-IOS | دابەزاندنی IPA بە بەستەری ڕاستەوخۆ</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        *{margin:0;padding:0;box-sizing:border-box;}
        body{background:radial-gradient(circle at 20% 30%,#0b0e17,#03050a);font-family:'Inter',sans-serif;color:#eef2ff;min-height:100vh;padding:24px;}
        .glass-container{max-width:1300px;margin:0 auto;}
        .silver-header{background:rgba(15,20,32,0.65);backdrop-filter:blur(16px);border-radius:56px;padding:20px 32px;margin-bottom:32px;border:1px solid rgba(210,220,255,0.3);display:flex;flex-wrap:wrap;justify-content:space-between;align-items:center;}
        .logo-area h1{font-size:1.9rem;font-weight:800;background:linear-gradient(135deg,#FFF,#b9c4f0);-webkit-background-clip:text;background-clip:text;color:transparent;}
        .logo-area p{font-size:0.8rem;color:#a7b3da;}
        .admin-trigger{background:rgba(60,70,110,0.6);border:1px solid rgba(200,210,255,0.5);padding:10px 24px;border-radius:60px;cursor:pointer;transition:0.2s;}
        .admin-trigger:hover{background:rgba(100,115,170,0.8);}
        .files-section{background:rgba(12,16,27,0.55);backdrop-filter:blur(12px);border-radius:52px;padding:28px 24px;margin-bottom:30px;}
        .section-title{font-size:1.7rem;font-weight:700;margin-bottom:20px;border-left:4px solid #cbd5ff;padding-left:20px;}
        .grid-ipa{display:grid;grid-template-columns:repeat(auto-fill,minmax(320px,1fr));gap:22px;}
        .ipa-card{background:rgba(20,26,45,0.7);border-radius:38px;padding:20px;border:1px solid rgba(210,215,250,0.25);transition:0.2s;}
        .ipa-card:hover{transform:translateY(-4px);border-color:rgba(210,220,255,0.7);}
        .ipa-name{font-weight:800;font-size:1.2rem;word-break:break-all;margin-bottom:8px;}
        .ipa-meta{font-size:0.7rem;color:#b7c3ea;margin:10px 0;}
        .btn-download{background:linear-gradient(95deg,#2a2f48,#1a1e32);border:none;padding:12px 0;width:100%;border-radius:44px;color:white;font-weight:600;cursor:pointer;margin-top:12px;transition:0.2s;font-family:inherit;text-align:center;display:block;text-decoration:none;}
        .btn-download:hover{background:#3e4570;transform:scale(1.01);}
        .admin-overlay{position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.8);backdrop-filter:blur(10px);z-index:1000;display:flex;align-items:center;justify-content:center;visibility:hidden;opacity:0;transition:0.2s;}
        .admin-overlay.active{visibility:visible;opacity:1;}
        .admin-panel{background:#0f1322e6;backdrop-filter:blur(28px);border-radius:64px;width:90%;max-width:650px;padding:32px;border:1px solid silver;max-height:90vh;overflow-y:auto;}
        .admin-panel h2{margin-bottom:20px;}
        .admin-panel h3{margin:20px 0 10px 0;}
        .admin-input{background:#1e233b;border:1px solid #5e6b9b;padding:14px 18px;border-radius:48px;width:100%;margin:12px 0;color:white;font-size:1rem;}
        .admin-btn{background:#2c3353;border:none;padding:12px 18px;border-radius:44px;font-weight:bold;margin-right:12px;cursor:pointer;color:white;}
        .file-list-admin{max-height:300px;overflow-y:auto;margin:20px 0;background:#090c18;border-radius:32px;padding:10px;}
        .admin-file-item{display:flex;justify-content:space-between;align-items:center;padding:10px 12px;border-bottom:1px solid #2f3760;flex-wrap:wrap;gap:8px;}
        .admin-file-info{flex:1;min-width:180px;}
        .close-admin{float:right;font-size:28px;cursor:pointer;color:#aaa;}
        .close-admin:hover{color:white;}
        footer{text-align:center;margin-top:20px;font-size:0.75rem;opacity:0.7;}
        .toast-msg{position:fixed;bottom:30px;left:50%;transform:translateX(-50%);background:#1e2a3a;backdrop-filter:blur(12px);padding:10px 22px;border-radius:60px;z-index:1100;}
        hr{margin:20px 0;border-color:#2f3760;}
        .helper-note{background:rgba(0,0,0,0.4);border-radius:24px;padding:12px;margin-top:15px;font-size:0.7rem;color:#a0a8c5;}
        @media (max-width:650px){.silver-header{flex-direction:column;gap:15px;align-items:start;}}
    </style>
</head>
<body>
<div class="glass-container">
    <div class="silver-header">
        <div class="logo-area">
            <h1><i class="fas fa-gem"></i> 7AJI-IOS</h1>
            <p>بەستەری ڕاستەوخۆی دابەزاندنی IPA • بۆ هەموو بەکارهێنەران</p>
        </div>
        <div class="admin-trigger" id="openAdminBtn">
            <i class="fas fa-lock"></i> پەڕەی ئەدمین <i class="fas fa-user-shield"></i>
        </div>
    </div>

    <div class="files-section">
        <div class="section-title">
            <i class="fas fa-mobile-alt"></i> فایلەکانی IPA بۆ دابەزاندن
        </div>
        <div id="ipaGrid" class="grid-ipa">
            <div class="ipa-card" style="text-align:center;"><i class="fas fa-spinner fa-pulse"></i> بارکردنی لیست...</div>
        </div>
    </div>
    <footer>
        <i class="fas fa-shield-alt"></i> 7AJI-IOS • بەستەری ڕاستەوخۆی دابەزاندن • تەنها ئەدمین دەتوانێت زیاد/سڕینەوە بکات
    </footer>
</div>

<!-- پەڕەی ئەدمین بۆ زیادکردنی بەستەری ڕاستەوخۆی IPA -->
<div id="adminOverlay" class="admin-overlay">
    <div class="admin-panel">
        <span class="close-admin" id="closeAdminBtn">&times;</span>
        <h2><i class="fas fa-crown"></i> بەڕێوەبەری بەستەرەکانی 7AJI-IOS</h2>
        <input type="password" id="adminPassInput" class="admin-input" placeholder="نهێنی‌وشەی ئەدمین">
        <button id="loginAdminBtn" class="admin-btn"><i class="fas fa-key"></i> چوونەژوورە</button>
        
        <div id="adminContent" style="display: none; margin-top: 20px;">
            <h3><i class="fas fa-plus-circle"></i> زیادکردنی بەستەری نوێی IPA</h3>
            <input type="text" id="ipaNameInput" class="admin-input" placeholder="ناوی فایل (نموونە: Spotify_Premium.ipa)">
            <input type="url" id="ipaUrlInput" class="admin-input" placeholder="بەستەری ڕاستەوخۆی دابەزاندن (https://... .ipa)">
            <input type="text" id="ipaVersionInput" class="admin-input" placeholder="وەشان (ئارەزوومەندانە) - نموونە: 9.1.52">
            <button id="addLinkBtn" class="admin-btn"><i class="fas fa-save"></i> زیادکردنی بەستەر</button>
            
            <div class="helper-note">
                <i class="fas fa-info-circle"></i> <strong>چۆن بەستەری ڕاستەوخۆ وەربگرم؟</strong><br>
                • <strong>GitHub Releases:</strong> فایلەکە باربکە، دوای ئازادکردن کلیکی ڕاست لەسەر "Download" و "Copy link address"<br>
                • <strong>Google Drive:</strong> بەستەری هاوبەشکردن و "uc?id=XXX&export=download"<br>
                • <strong>Dropbox:</strong> "?dl=0" بگۆڕە بە "?dl=1"
            </div>
            
            <hr>
            <h3><i class="fas fa-trash-alt"></i> بەڕێوەبردنی بەستەرەکان</h3>
            <div id="adminFileList" class="file-list-admin"></div>
            <button id="logoutAdminBtn" class="admin-btn"><i class="fas fa-sign-out-alt"></i> دەرچوون</button>
        </div>
    </div>
</div>

<script>
    // -------------------- بەستەری ڕاستەوخۆ بۆ IPA --------------------
    // هەموو بەستەرەکان لە Local Storage دەپارێزرێن (بێ وەستان و بۆ هەموو بەکارهێنەران)
    const STORAGE_KEY = '7AJI_IOS_DIRECT_LINKS';
    const ADMIN_PASSWORD = '7aji2025silver';
    
    let currentAdmin = false;
    let ipaLinks = [];

    // بارکردنی بەستەرەکان لە Local Storage
    function loadLinks() {
        const stored = localStorage.getItem(STORAGE_KEY);
        if (stored) {
            ipaLinks = JSON.parse(stored);
        } else {
            // بەستەری نموونەیی (تۆ دەتوانیت بیسڕیتەوە)
            ipaLinks = [
                {
                    id: Date.now(),
                    name: "Spotify Premium Modified.ipa",
                    url: "https://github.com/rileytestut/Delta/releases/download/1.5.3/Delta.ipa",
                    version: "1.5.3",
                    dateAdded: new Date().toISOString()
                }
            ];
            saveLinks();
        }
        renderPublicGrid();
    }

    function saveLinks() {
        localStorage.setItem(STORAGE_KEY, JSON.stringify(ipaLinks));
    }

    // زیادکردنی بەستەری نوێ
    function addLink(name, url, version) {
        if (!name || !url) return false;
        const newLink = {
            id: Date.now(),
            name: name.trim(),
            url: url.trim(),
            version: version || '1.0',
            dateAdded: new Date().toISOString()
        };
        ipaLinks.push(newLink);
        saveLinks();
        renderPublicGrid();
        if (currentAdmin) renderAdminList();
        return true;
    }

    // سڕینەوەی بەستەر
    function deleteLink(id) {
        ipaLinks = ipaLinks.filter(link => link.id !== id);
        saveLinks();
        renderPublicGrid();
        if (currentAdmin) renderAdminList();
    }

    // نمایش بەستەرەکان بۆ هەموو بەکارهێنەران (دابەزاندنی ڕاستەوخۆ)
    function renderPublicGrid() {
        const gridDiv = document.getElementById('ipaGrid');
        
        if (ipaLinks.length === 0) {
            gridDiv.innerHTML = `<div class="ipa-card" style="grid-column:1/-1; text-align:center;"><i class="fas fa-info-circle"></i> هیچ بەستەرێک زیاد نەکراوە. ئەدمین دەتوانێت زیاد بکات.</div>`;
            return;
        }
        
        let html = '';
        ipaLinks.forEach(link => {
            html += `
                <div class="ipa-card">
                    <div class="ipa-name"><i class="fas fa-link"></i> ${escapeHtml(link.name)}</div>
                    <div class="ipa-meta"><i class="fas fa-code-branch"></i> وەشان: ${escapeHtml(link.version)} • ${new Date(link.dateAdded).toLocaleDateString()}</div>
                    <a href="${escapeHtml(link.url)}" target="_blank" rel="noopener noreferrer" class="btn-download" style="display:block; text-align:center; text-decoration:none;">
                        <i class="fas fa-cloud-download-alt"></i> دابەزاندنی ${escapeHtml(link.name)}
                    </a>
                </div>
            `;
        });
        gridDiv.innerHTML = html;
    }

    // نمایش بۆ ئەدمین (بۆ سڕینەوە)
    function renderAdminList() {
        const container = document.getElementById('adminFileList');
        
        if (ipaLinks.length === 0) {
            container.innerHTML = '<em>هیچ بەستەرێک نییە، بەستەرێک زیاد بکە</em>';
            return;
        }
        
        let html = '';
        ipaLinks.forEach(link => {
            html += `
                <div class="admin-file-item">
                    <div class="admin-file-info">
                        <strong><i class="fas fa-file"></i> ${escapeHtml(link.name)}</strong><br>
                        <small>وەشان: ${escapeHtml(link.version)} • ${new Date(link.dateAdded).toLocaleString()}</small><br>
                        <small style="color:#7c8ab5; word-break:break-all;">${escapeHtml(link.url.substring(0, 70))}...</small>
                    </div>
                    <div class="admin-file-actions">
                        <button class="delete-single-btn" data-id="${link.id}" style="background:#883344;border:none;padding:6px 14px;border-radius:30px;color:white;cursor:pointer;"><i class="fas fa-trash"></i> سڕینەوە</button>
                    </div>
                </div>
            `;
        });
        container.innerHTML = html;
        
        document.querySelectorAll('.delete-single-btn').forEach(btn => {
            btn.addEventListener('click', (e) => {
                const id = Number(btn.getAttribute('data-id'));
                if (confirm('دڵنیای لە سڕینەوەی ئەم بەستەرە؟')) {
                    deleteLink(id);
                    showToast('بەستەرەکە سڕایەوە');
                    renderAdminList();
                }
            });
        });
    }

    function escapeHtml(str) {
        if (!str) return '';
        return str.replace(/[&<>]/g, function(m) {
            if (m === '&') return '&amp;';
            if (m === '<') return '&lt;';
            if (m === '>') return '&gt;';
            return m;
        });
    }

    function showToast(msg) {
        let toast = document.querySelector('.toast-msg');
        if (toast) toast.remove();
        let div = document.createElement('div');
        div.className = 'toast-msg';
        div.innerHTML = `<i class="fas fa-bell"></i> ${msg}`;
        document.body.appendChild(div);
        setTimeout(() => div.remove(), 2500);
    }

    // ---------- ئەدمین UI ----------
    const adminOverlay = document.getElementById('adminOverlay');
    const openAdminBtn = document.getElementById('openAdminBtn');
    const closeAdminBtn = document.getElementById('closeAdminBtn');
    const loginBtn = document.getElementById('loginAdminBtn');
    const adminPassInput = document.getElementById('adminPassInput');
    const adminContentDiv = document.getElementById('adminContent');
    const logoutAdmin = document.getElementById('logoutAdminBtn');
    const addLinkBtn = document.getElementById('addLinkBtn');
    const ipaNameInput = document.getElementById('ipaNameInput');
    const ipaUrlInput = document.getElementById('ipaUrlInput');
    const ipaVersionInput = document.getElementById('ipaVersionInput');

    openAdminBtn.onclick = () => {
        if (currentAdmin) {
            adminContentDiv.style.display = 'block';
            renderAdminList();
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
    adminOverlay.onclick = (e) => { if (e.target === adminOverlay) adminOverlay.classList.remove('active'); };
    
    loginBtn.onclick = () => {
        if (adminPassInput.value === ADMIN_PASSWORD) {
            currentAdmin = true;
            adminContentDiv.style.display = 'block';
            adminPassInput.style.display = 'none';
            loginBtn.style.display = 'none';
            renderAdminList();
            showToast('بەخێربێیت ئەدمین، دەتوانیت بەستەری IPA زیاد بکەیت');
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
    
    addLinkBtn.onclick = () => {
        if (!currentAdmin) {
            showToast('پێویستە بچیتە ژوورەوە وەک ئەدمین');
            return;
        }
        const name = ipaNameInput.value.trim();
        const url = ipaUrlInput.value.trim();
        const version = ipaVersionInput.value.trim();
        
        if (!name) {
            showToast('تکایە ناوی فایل بنووسە');
            return;
        }
        if (!url) {
            showToast('تکایە بەستەری ڕاستەوخۆی دابەزاندن بنووسە');
            return;
        }
        
        addLink(name, url, version || '1.0');
        showToast(`بەستەری ${name} زیاد کرا`);
        ipaNameInput.value = '';
        ipaUrlInput.value = '';
        ipaVersionInput.value = '';
        renderAdminList();
    };
    
    // دەستپێکردن
    window.addEventListener('load', () => {
        loadLinks();
        currentAdmin = false;
    });
</script>
</body>
</html>
