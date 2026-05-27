<!DOCTYPE html>
<html lang="ku">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
    <title>7AJI-IOS | بارکردن و دابەزاندنی IPA</title>
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
        .grid-ipa{display:grid;grid-template-columns:repeat(auto-fill,minmax(300px,1fr));gap:22px;}
        .ipa-card{background:rgba(20,26,45,0.7);border-radius:38px;padding:20px;border:1px solid rgba(210,215,250,0.25);transition:0.2s;}
        .ipa-card:hover{transform:translateY(-4px);border-color:rgba(210,220,255,0.7);}
        .ipa-name{font-weight:800;font-size:1.25rem;word-break:break-all;margin-bottom:8px;}
        .ipa-meta{font-size:0.7rem;color:#b7c3ea;margin:10px 0;}
        .btn-download{background:linear-gradient(95deg,#2a2f48,#1a1e32);border:none;padding:12px 0;width:100%;border-radius:44px;color:white;font-weight:600;cursor:pointer;margin-top:12px;transition:0.2s;font-family:inherit;text-align:center;display:block;text-decoration:none;}
        .btn-download:hover{background:#3e4570;}
        .admin-overlay{position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.8);backdrop-filter:blur(10px);z-index:1000;display:flex;align-items:center;justify-content:center;visibility:hidden;opacity:0;transition:0.2s;}
        .admin-overlay.active{visibility:visible;opacity:1;}
        .admin-panel{background:#0f1322e6;backdrop-filter:blur(28px);border-radius:64px;width:90%;max-width:600px;padding:32px;border:1px solid silver;}
        .admin-panel h2{margin-bottom:20px;}
        .admin-panel h3{margin:20px 0 10px 0;}
        .admin-input{background:#1e233b;border:1px solid #5e6b9b;padding:14px 18px;border-radius:48px;width:100%;margin:12px 0;color:white;font-size:1rem;}
        .admin-btn{background:#2c3353;border:none;padding:12px 18px;border-radius:44px;font-weight:bold;margin-right:12px;cursor:pointer;color:white;}
        .file-list-admin{max-height:250px;overflow-y:auto;margin:20px 0;background:#090c18;border-radius:32px;padding:10px;}
        .admin-file-item{display:flex;justify-content:space-between;align-items:center;padding:10px 12px;border-bottom:1px solid #2f3760;flex-wrap:wrap;gap:8px;}
        .admin-file-info{flex:1;min-width:150px;}
        .close-admin{float:right;font-size:28px;cursor:pointer;color:#aaa;}
        .close-admin:hover{color:white;}
        footer{text-align:center;margin-top:20px;font-size:0.75rem;opacity:0.7;}
        .toast-msg{position:fixed;bottom:30px;left:50%;transform:translateX(-50%);background:#1e2a3a;backdrop-filter:blur(12px);padding:10px 22px;border-radius:60px;z-index:1100;}
        hr{margin:20px 0;border-color:#2f3760;}
        @media (max-width:650px){.silver-header{flex-direction:column;gap:15px;align-items:start;}}
        .upload-area{margin:15px 0;padding:20px;border:2px dashed #5e6b9b;border-radius:40px;text-align:center;cursor:pointer;background:rgba(30,35,59,0.4);}
        .upload-area:hover{background:rgba(50,55,90,0.6);}
    </style>
</head>
<body>
<div class="glass-container">
    <div class="silver-header">
        <div class="logo-area">
            <h1><i class="fas fa-gem"></i> 7AJI-IOS</h1>
            <p>بارکردنی IPA لەلایەن ئەدمین • دابەزاندنی ڕاستەوخۆ بۆ بەکارهێنەران</p>
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
        <i class="fas fa-shield-alt"></i> سیستمە پارێزراوی 7AJI-IOS • تەنها ئەدمین دەتوانێت فایل بارکات/سڕینەوە
    </footer>
</div>

<!-- پەڕەی ئەدمین بۆ بارکردنی فایلی IPA -->
<div id="adminOverlay" class="admin-overlay">
    <div class="admin-panel">
        <span class="close-admin" id="closeAdminBtn">&times;</span>
        <h2><i class="fas fa-crown"></i> بەڕێوەبەری فایلەکانی 7AJI-IOS</h2>
        <input type="password" id="adminPassInput" class="admin-input" placeholder="نهێنی‌وشەی ئەدمین">
        <button id="loginAdminBtn" class="admin-btn"><i class="fas fa-key"></i> چوونەژوورە</button>
        
        <div id="adminContent" style="display: none; margin-top: 20px;">
            <h3><i class="fas fa-cloud-upload-alt"></i> بارکردنی فایلی IPAی نوێ</h3>
            <div class="upload-area" id="uploadArea">
                <i class="fas fa-upload" style="font-size: 32px; margin-bottom: 10px; display: block;"></i>
                کلیک بکە یان ڕایبکێشە بۆ بارکردنی فایلی .ipa
                <input type="file" id="ipaFileUpload" accept=".ipa" style="display: none;">
            </div>
            <div id="uploadProgress" style="display:none; margin:10px 0;"><progress id="progressBar" value="0" max="100" style="width:100%; height:8px; border-radius:10px;"></progress></div>
            
            <hr>
            <h3><i class="fas fa-trash-alt"></i> سڕینەوەی فایلەکان</h3>
            <div id="adminFileList" class="file-list-admin"></div>
            <button id="logoutAdminBtn" class="admin-btn"><i class="fas fa-sign-out-alt"></i> دەرچوون</button>
        </div>
    </div>
</div>

<script>
    // -------------------- سیستەمی بارکردنی فایل و بەستەری ڕاستەوخۆ --------------------
    // فایلەکان لە IndexedDB دەپارێزرێن، بەکارهێنەران دەتوانن بە بەستەری ڕاستەوخۆ دابەزێنن
    const DB_NAME = '7AJI_IOS_FILES_DB';
    const DB_VERSION = 1;
    const STORE_NAME = 'ipa_files';
    const ADMIN_PASSWORD = '7aji2025silver';
    
    let db = null;
    let currentAdmin = false;
    let ipaFiles = [];

    // کردنەوەی داتابەیس
    function initDB() {
        return new Promise((resolve, reject) => {
            const request = indexedDB.open(DB_NAME, DB_VERSION);
            request.onerror = () => reject('IndexedDB هەڵەیە');
            request.onsuccess = (e) => {
                db = e.target.result;
                resolve();
            };
            request.onupgradeneeded = (e) => {
                const dbUp = e.target.result;
                if (!dbUp.objectStoreNames.contains(STORE_NAME)) {
                    dbUp.createObjectStore(STORE_NAME, { keyPath: 'id', autoIncrement: true });
                }
            };
        });
    }

    // بارکردنی فایلێک بۆ داتابەیس
    function uploadFileToDB(file) {
        return new Promise((resolve, reject) => {
            const reader = new FileReader();
            reader.onload = (e) => {
                const fileData = e.target.result;
                const newItem = {
                    filename: file.name,
                    data: fileData,
                    size: file.size,
                    type: file.type,
                    uploadedAt: new Date().toISOString()
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
    function getAllFiles() {
        return new Promise((resolve, reject) => {
            const transaction = db.transaction([STORE_NAME], 'readonly');
            const store = transaction.objectStore(STORE_NAME);
            const request = store.getAll();
            request.onsuccess = () => resolve(request.result || []);
            request.onerror = (e) => reject(e);
        });
    }

    // سڕینەوەی فایل
    function deleteFile(id) {
        return new Promise((resolve, reject) => {
            const transaction = db.transaction([STORE_NAME], 'readwrite');
            const store = transaction.objectStore(STORE_NAME);
            const request = store.delete(id);
            request.onsuccess = () => resolve(true);
            request.onerror = (e) => reject(e);
        });
    }

    // نمایش فایلەکان بۆ هەموو بەکارهێنەران (دابەزاندنی ڕاستەوخۆ)
    async function renderPublicGrid() {
        const gridDiv = document.getElementById('ipaGrid');
        const files = await getAllFiles();
        ipaFiles = files;
        
        if (files.length === 0) {
            gridDiv.innerHTML = `<div class="ipa-card" style="grid-column:1/-1; text-align:center;"><i class="fas fa-info-circle"></i> هیچ فایلێک بارنەکراوە. ئەدمین دەتوانێت فایل بارکات.</div>`;
            return;
        }
        
        let html = '';
        files.forEach(file => {
            const sizeMB = (file.size / (1024 * 1024)).toFixed(2);
            html += `
                <div class="ipa-card">
                    <div class="ipa-name"><i class="fas fa-file-ipa"></i> ${escapeHtml(file.filename)}</div>
                    <div class="ipa-meta"><i class="fas fa-database"></i> ${sizeMB} MB • ${new Date(file.uploadedAt).toLocaleString()}</div>
                    <a class="btn-download" data-id="${file.id}" data-filename="${escapeHtml(file.filename)}" data-data="${file.data}" style="cursor:pointer;">
                        <i class="fas fa-download"></i> دابەزاندنی ${escapeHtml(file.filename)}
                    </a>
                </div>
            `;
        });
        gridDiv.innerHTML = html;
        
        // گرێدانی ڕووداوی دابەزاندن
        document.querySelectorAll('.btn-download').forEach(btn => {
            btn.addEventListener('click', (e) => {
                e.preventDefault();
                const id = btn.getAttribute('data-id');
                const filename = btn.getAttribute('data-filename');
                const base64Data = btn.getAttribute('data-data');
                if (base64Data) {
                    downloadFromBase64(base64Data, filename);
                } else {
                    const fileItem = ipaFiles.find(f => f.id == id);
                    if (fileItem && fileItem.data) {
                        downloadFromBase64(fileItem.data, fileItem.filename);
                    } else {
                        showToast('هەڵە، فایل دەستنەکەوت');
                    }
                }
            });
        });
    }

    // دابەزاندن لە base64
    function downloadFromBase64(base64Data, filename) {
        const link = document.createElement('a');
        link.href = base64Data;
        link.download = filename;
        document.body.appendChild(link);
        link.click();
        document.body.removeChild(link);
        showToast(`دابەزاندنی ${filename} دەستیپێکرد`);
    }

    // نمایش لیستی فایلەکان بۆ ئەدمین (بۆ سڕینەوە)
    async function renderAdminList() {
        const container = document.getElementById('adminFileList');
        const files = await getAllFiles();
        
        if (files.length === 0) {
            container.innerHTML = '<em>هیچ فایلێک نییە، فایلێکی IPA باربکە</em>';
            return;
        }
        
        let html = '';
        files.forEach(file => {
            const sizeMB = (file.size / (1024 * 1024)).toFixed(2);
            html += `
                <div class="admin-file-item">
                    <div class="admin-file-info">
                        <strong><i class="fas fa-archive"></i> ${escapeHtml(file.filename)}</strong><br>
                        <small>${sizeMB} MB • ${new Date(file.uploadedAt).toLocaleString()}</small>
                    </div>
                    <div class="admin-file-actions">
                        <button class="delete-single-btn" data-id="${file.id}" style="background:#883344;border:none;padding:6px 14px;border-radius:30px;color:white;cursor:pointer;"><i class="fas fa-trash"></i> سڕینەوە</button>
                    </div>
                </div>
            `;
        });
        container.innerHTML = html;
        
        document.querySelectorAll('.delete-single-btn').forEach(btn => {
            btn.addEventListener('click', async (e) => {
                const id = Number(btn.getAttribute('data-id'));
                if (confirm('دڵنیای لە سڕینەوەی ئەم فایلە؟')) {
                    await deleteFile(id);
                    showToast('فایلەکە سڕایەوە');
                    await renderPublicGrid();
                    if (currentAdmin) await renderAdminList();
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

    // بارکردنی فایل لە ڕێگەی هەڵبژاردن
    async function handleFileUpload(file) {
        if (!file || !file.name.endsWith('.ipa')) {
            showToast('تکایە تەنها فایلی .ipa هەڵبژێرە');
            return false;
        }
        
        const maxSize = 500 * 1024 * 1024; // 500MB
        if (file.size > maxSize) {
            showToast('قەبارەی فایل دەبێت کەمتر بێت لە 500MB');
            return false;
        }
        
        showToast(`بارکردنی ${file.name}...`);
        await uploadFileToDB(file);
        showToast(`فایلی ${file.name} بە سەرکەوتوو بارکرا`);
        await renderPublicGrid();
        if (currentAdmin) await renderAdminList();
        return true;
    }

    // ---------- ئەدمین UI ----------
    const adminOverlay = document.getElementById('adminOverlay');
    const openAdminBtn = document.getElementById('openAdminBtn');
    const closeAdminBtn = document.getElementById('closeAdminBtn');
    const loginBtn = document.getElementById('loginAdminBtn');
    const adminPassInput = document.getElementById('adminPassInput');
    const adminContentDiv = document.getElementById('adminContent');
    const logoutAdmin = document.getElementById('logoutAdminBtn');
    const fileUploadInput = document.getElementById('ipaFileUpload');
    const uploadArea = document.getElementById('uploadArea');

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
            showToast('بەخێربێیت ئەدمین، دەتوانیت فایلی IPA بارکەیت');
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
    
    // ڕێگای بارکردن
    uploadArea.onclick = () => fileUploadInput.click();
    fileUploadInput.onchange = async (e) => {
        if (!currentAdmin) {
            showToast('پێویستە بچیتە ژوورەوە وەک ئەدمین');
            return;
        }
        const file = e.target.files[0];
        if (file) await handleFileUpload(file);
        fileUploadInput.value = '';
    };
    
    // Drag & Drop بۆ بارکردن
    uploadArea.ondragover = (e) => {
        e.preventDefault();
        uploadArea.style.background = 'rgba(80, 90, 140, 0.6)';
    };
    uploadArea.ondragleave = (e) => {
        e.preventDefault();
        uploadArea.style.background = 'rgba(30, 35, 59, 0.4)';
    };
    uploadArea.ondrop = async (e) => {
        e.preventDefault();
        uploadArea.style.background = 'rgba(30, 35, 59, 0.4)';
        if (!currentAdmin) {
            showToast('پێویستە بچیتە ژوورەوە وەک ئەدمین');
            return;
        }
        const file = e.dataTransfer.files[0];
        if (file && file.name.endsWith('.ipa')) {
            await handleFileUpload(file);
        } else {
            showToast('تەنها فایلی .ipa پشتیوانی دەکرێت');
        }
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
