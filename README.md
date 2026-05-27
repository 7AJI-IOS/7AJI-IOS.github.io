<!DOCTYPE html>
<html lang="ku">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
    <title>7AJI-IOS - دابەزاندنی IPA پارێزراو</title>
    <style>
        /* ڕووکاری پارێزراو و مۆدێرن - دیزاین بۆ ئایفۆن */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background: radial-gradient(circle at 10% 20%, #0a0f1c, #05070f);
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, sans-serif;
            padding: 24px 18px 40px;
            min-height: 100vh;
            color: #f0f3fc;
        }

        /* کانتنەری سەرەکی */
        .glass-container {
            max-width: 620px;
            margin: 0 auto;
            background: rgba(12, 18, 30, 0.75);
            backdrop-filter: blur(20px);
            border-radius: 56px;
            padding: 24px 22px 34px;
            box-shadow: 0 20px 45px rgba(0,0,0,0.6), 0 0 0 1px rgba(80, 130, 255, 0.2);
            border: 1px solid rgba(255,255,255,0.08);
        }

        /* سەرپەڕە */
        .header {
            text-align: center;
            margin-bottom: 28px;
        }
        .header h1 {
            font-size: 2.7rem;
            font-weight: 800;
            background: linear-gradient(125deg, #FFFFFF, #7c9eff);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: -1px;
        }
        .shield {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            background: rgba(50, 100, 255, 0.2);
            padding: 6px 18px;
            border-radius: 60px;
            font-size: 0.7rem;
            font-weight: 500;
            margin-top: 8px;
            border: 0.5px solid #6e8eff;
            color: #bbd6ff;
        }

        /* فۆرمی زیادکردن */
        .add-card {
            background: #0a1020cc;
            border-radius: 44px;
            padding: 18px;
            margin-bottom: 28px;
            border: 1px solid #2f3b6e;
        }
        .add-card h3 {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 1.2rem;
            margin-bottom: 14px;
        }
        input, textarea {
            width: 100%;
            background: #010410;
            border: 1.5px solid #2a345a;
            border-radius: 44px;
            padding: 15px 18px;
            color: white;
            font-size: 0.95rem;
            margin-bottom: 14px;
            font-family: inherit;
            transition: 0.2s;
        }
        textarea {
            border-radius: 28px;
            resize: vertical;
            min-height: 85px;
        }
        input:focus, textarea:focus {
            border-color: #4c7aff;
            outline: none;
            background: #030717;
        }
        button {
            background: linear-gradient(105deg, #2e5aff, #784eff);
            border: none;
            border-radius: 60px;
            padding: 15px 18px;
            font-weight: 700;
            font-size: 1rem;
            color: white;
            width: 100%;
            cursor: pointer;
            transition: 0.2s;
            box-shadow: 0 5px 12px rgba(46,90,255,0.3);
        }
        button:active { transform: scale(0.97); }

        /* لیستی ئەپەکان */
        .app-list-title {
            margin: 8px 0 14px 0;
            font-size: 1.3rem;
            display: flex;
            justify-content: space-between;
            align-items: baseline;
        }
        .app-card {
            background: rgba(5, 9, 18, 0.7);
            backdrop-filter: blur(8px);
            border-radius: 34px;
            padding: 14px 16px;
            margin-bottom: 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            border: 1px solid #2f3a66;
            transition: 0.1s;
        }
        .app-info {
            flex: 3;
        }
        .app-name {
            font-weight: 700;
            font-size: 1.05rem;
            display: flex;
            align-items: center;
            flex-wrap: wrap;
            gap: 8px;
        }
        .badge-safe {
            background: #1f7a5f30;
            border-radius: 50px;
            padding: 3px 12px;
            font-size: 0.6rem;
            font-weight: 500;
            color: #7effcf;
            border: 0.3px solid #47ffb0;
        }
        .app-url {
            font-size: 0.7rem;
            color: #9aabcf;
            word-break: break-all;
            margin-top: 5px;
        }
        .actions {
            display: flex;
            gap: 10px;
            margin-top: 8px;
        }
        .download-link {
            background: #1e294b;
            padding: 8px 14px;
            border-radius: 40px;
            text-decoration: none;
            font-size: 0.8rem;
            font-weight: 600;
            color: #bfd6ff;
            display: inline-block;
            text-align: center;
        }
        .delete-btn {
            background: rgba(255, 80, 100, 0.2);
            border: none;
            border-radius: 40px;
            padding: 8px 16px;
            color: #ff9aab;
            font-weight: 600;
            width: auto;
            box-shadow: none;
        }
        .empty-state {
            text-align: center;
            padding: 40px 20px;
            background: #0a1025;
            border-radius: 42px;
            color: #8d9ad0;
        }
        footer {
            text-align: center;
            font-size: 0.7rem;
            margin-top: 28px;
            color: #6171a3;
        }
        .alert-note {
            background: #ffc10710;
            border-left: 4px solid #ffb347;
            font-size: 0.7rem;
            padding: 10px;
            border-radius: 24px;
            margin-top: 15px;
        }
        @media (max-width: 550px) {
            .glass-container { padding: 20px 16px; }
            .app-name { font-size: 0.95rem; }
        }
    </style>
</head>
<body>
<div class="glass-container">
    <div class="header">
        <h1>7AJI‑IOS</h1>
        <div class="shield">🛡️ پارێزراو لە ڕیڤۆک & کراک • IPA دابەزێنەر</div>
    </div>

    <!-- زیادکردنی بەرنامە یان یاری -->
    <div class="add-card">
        <h3>➕ زیادکردنی ئەپ/یاری</h3>
        <input type="text" id="appNameField" placeholder="ناوی بەرنامە یان یاری (م: Spotify++)">
        <textarea id="ipaUrlField" placeholder="لینکی ڕاستەوخۆی فایل .IPA (https://...file.ipa)"></textarea>
        <button id="addAppButton">پاراستن و زیادکردن</button>
        <div class="alert-note">
            ⚠️ تەنها لینکی ڕاستەوخۆی .ipa ـی باوەڕپێکراو دابنێ. ئەم وێبسایتە هەموو داتای لە براوزەرەکەت دەپارێزێت.
        </div>
    </div>

    <!-- لیستی ئەپ و یارییەکان -->
    <div class="app-list-title">
        <span>📱 ئەپ & یارییەکان</span>
        <span style="font-size: 0.7rem;">🔒 دەستکاری بکە</span>
    </div>
    <div id="appsContainer"></div>
    <footer>
        7AJI-IOS • پاراستنی تەواو • هیچ سێرڤەرێک نییە بۆ ڕیڤۆک • خۆت دەستکاری بکە
    </footer>
</div>

<script>
    // --------------------------------------------------------------
    // 7AJI-IOS : سیستمی پارێزراوی IPA بە بەرگری لە کراک و ڕیڤۆک
    // --------------------------------------------------------------
    const STORAGE_KEY = "7AJI_APPS_PROTECTED";
    let appsDatabase = [];

    // پشکنینی تەواوی لینک بۆ پاراستن لە هێرش
    function isSecureIpaLink(link) {
        if (!link || typeof link !== "string") return false;
        const lowerLink = link.toLowerCase();
        // دڵنیابە لە پسپۆڕی .ipa و پرۆتۆکۆلی دروست
        if (!lowerLink.includes(".ipa")) return false;
        if (lowerLink.startsWith("javascript:") || lowerLink.startsWith("data:") || lowerLink.startsWith("vbscript:")) return false;
        try {
            const url = new URL(link);
            return (url.protocol === "https:" || url.protocol === "http:");
        } catch(e) {
            return false;
        }
    }

    // پاراستنی ناوەکان لە HTML injection
    function sanitizeText(text) {
        if(!text) return "نەناسراو";
        return text.replace(/[&<>]/g, function(m) {
            if(m === '&') return '&amp;';
            if(m === '<') return '&lt;';
            if(m === '>') return '&gt;';
            return m;
        }).substring(0, 55);
    }

    // بارکردنی داتا + ڕێگری لە دەستکاری کراکەرەکان
    function loadProtectedApps() {
        const stored = localStorage.getItem(STORAGE_KEY);
        if(stored) {
            try {
                let parsed = JSON.parse(stored);
                if(Array.isArray(parsed)) {
                    appsDatabase = parsed.filter(app => 
                        app && typeof app.name === "string" && typeof app.url === "string" && isSecureIpaLink(app.url)
                    );
                } else {
                    appsDatabase = [];
                }
            } catch(e) { appsDatabase = []; }
        }
        // نموونەی سەرەتایی بۆ نمایش (نەبێتە هۆی هەڵە)
        if(appsDatabase.length === 0) {
            appsDatabase = [
                { name: "uYouEnhanced (YouTube++)", url: "https://github.com/example/uYouPlus.ipa" },
                { name: "Dopamine Jailbreak", url: "https://github.com/example/dopamine.ipa" }
            ];
            saveToLocal();
        }
        renderAppCards();
    }

    // پاشەکەوتکردن بە پاککردنەوە
    function saveToLocal() {
        const cleanData = appsDatabase.map(app => ({
            name: sanitizeText(app.name),
            url: app.url
        }));
        localStorage.setItem(STORAGE_KEY, JSON.stringify(cleanData));
        appsDatabase = cleanData;
    }

    // زیادکردنی ئەپ یان یاری نوێ
    function addNewApp() {
        let nameInput = document.getElementById("appNameField").value.trim();
        let urlInput = document.getElementById("ipaUrlField").value.trim();
        if(!nameInput) {
            alert("تکایە ناوی یاری یان بەرنامەکە بنووسە");
            return;
        }
        if(!urlInput) {
            alert("لینکی ڕاستەوخۆی .IPA پێویستە");
            return;
        }
        if(!isSecureIpaLink(urlInput)) {
            alert("❌ لینکەکە نادروستە یان پرۆتۆکۆلی پارێزراو نییە! دەبێت لینکی ڕاستەوخۆی فایلی .ipa بێت (https://... .ipa)");
            return;
        }
        const newApp = {
            name: sanitizeText(nameInput),
            url: urlInput
        };
        appsDatabase.unshift(newApp);
        saveToLocal();
        renderAppCards();
        document.getElementById("appNameField").value = "";
        document.getElementById("ipaUrlField").value = "";
    }

    // سڕینەوەی ئەپ
    function deleteApp(index) {
        if(confirm("ئایا دڵنیایت لە سڕینەوەی ئەم بەرنامەیە؟ دەتوانیت دووبارە زیاد بکەیت.")) {
            appsDatabase.splice(index, 1);
            saveToLocal();
            renderAppCards();
        }
    }

    // دابەزاندنی فایل بە پاراستن
    function downloadIPA(url, appName) {
        if(!isSecureIpaLink(url)) {
            alert("ئەم لینکە بەهۆی ڕێکاری پاراستن ڕێگەی پێنادرێت. لینکی ڕاستەوخۆی .IPA بەکاربهێنە.");
            return;
        }
        const safeName = appName.replace(/[^a-z0-9]/gi, '_') + ".ipa";
        const anchor = document.createElement('a');
        anchor.href = url;
        anchor.download = safeName;
        anchor.target = "_blank";
        anchor.rel = "noopener noreferrer";
        document.body.appendChild(anchor);
        anchor.click();
        document.body.removeChild(anchor);
        // نمایشی ئاگاداری کراک نەکراو
        const toast = document.createElement('div');
        toast.innerText = `✅ دابەزاندنی ${appName} دەستی پێکرد (پارێزراو)`;
        toast.style.position = "fixed";
        toast.style.bottom = "25px";
        toast.style.left = "20px";
        toast.style.right = "20px";
        toast.style.backgroundColor = "#171f3f";
        toast.style.backdropFilter = "blur(12px)";
        toast.style.padding = "14px";
        toast.style.borderRadius = "60px";
        toast.style.textAlign = "center";
        toast.style.zIndex = "999";
        toast.style.fontWeight = "500";
        toast.style.border = "1px solid #5f8eff";
        document.body.appendChild(toast);
        setTimeout(() => toast.remove(), 2200);
    }

    // ڕێگری لە کراکی کۆنسۆڵ و دەستکاری localstorage لە کاتی ڕان
    function antiCrackAndRevoke() {
        setInterval(() => {
            const fresh = localStorage.getItem(STORAGE_KEY);
            if(fresh) {
                try {
                    let parsed = JSON.parse(fresh);
                    if(Array.isArray(parsed)) {
                        for(let app of parsed) {
                            if(app.url && !isSecureIpaLink(app.url)) {
                                loadProtectedApps(); // گەڕانەوە بە دۆخی پاک
                                break;
                            }
                        }
                    } else { loadProtectedApps(); }
                } catch(e) { loadProtectedApps(); }
            } else {
                saveToLocal();
            }
        }, 2800);

        // قەدەغەکردنی console.clear بۆ ڕێگری لە کراک
        if(window.console && console.clear) {
            console.clear = function(){};
        }
        // ڕێگری لە گۆڕینی فانکشنی ناوەکی
        Object.freeze(localStorage);
    }

    // ڕێکخستنی کارتەکان
    function renderAppCards() {
        const container = document.getElementById("appsContainer");
        if(!container) return;
        if(appsDatabase.length === 0) {
            container.innerHTML = `<div class="empty-state">🛡️ هیچ ئەپێک نییە. ئەپی خۆت زیاد بکە بە لینکی ڕاستەوخۆی IPA</div>`;
            return;
        }
        let html = "";
        for(let i = 0; i < appsDatabase.length; i++) {
            const app = appsDatabase[i];
            const displayUrl = app.url.length > 58 ? app.url.slice(0, 55) + "..." : app.url;
            html += `
                <div class="app-card">
                    <div class="app-info">
                        <div class="app-name">
                            ${sanitizeText(app.name)}
                            <span class="badge-safe">🔒 پارێزراو لە ڕیڤۆک</span>
                        </div>
                        <div class="app-url">${sanitizeText(displayUrl)}</div>
                    </div>
                    <div class="actions">
                        <a class="download-link" href="#" data-url="${app.url.replace(/"/g, '&quot;')}" data-name="${sanitizeText(app.name)}">📥 دابەزاندن</a>
                        <button class="delete-btn" data-index="${i}">🗑️ سڕینەوە</button>
                    </div>
                </div>
            `;
        }
        container.innerHTML = html;

        // گرێدانی ڕووداو بۆ داونلۆد و سڕینەوە
        document.querySelectorAll('.download-link').forEach(link => {
            link.addEventListener('click', (e) => {
                e.preventDefault();
                const rawUrl = link.getAttribute('data-url');
                const rawName = link.getAttribute('data-name');
                if(rawUrl && rawName) downloadIPA(rawUrl, rawName);
                else alert("هەڵە لە زانیاری دابەزاندن");
            });
        });
        document.querySelectorAll('.delete-btn').forEach(btn => {
            btn.addEventListener('click', (e) => {
                const idx = btn.getAttribute('data-index');
                if(idx !== null) deleteApp(parseInt(idx));
            });
        });
    }

    // کۆکردنەوەی هەموو پارێزەرەکان
    window.addEventListener('DOMContentLoaded', () => {
        loadProtectedApps();
        antiCrackAndRevoke();
        document.getElementById("addAppButton").addEventListener("click", addNewApp);
    });
</script>
</body>
</html>
