<!DOCTYPE html>
<html lang="ku">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
    <title>7AJI-IOS - دابەزاندنی IPA پارێزراو</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background: linear-gradient(135deg, #0a0f1e 0%, #0c1222 100%);
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            padding: 20px 16px 40px;
            color: #f0f3fa;
        }

        /* پاراستن لە ڕیڤۆک و کراک */
        .security-badge {
            background: rgba(255, 100, 100, 0.15);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 80, 120, 0.4);
            border-radius: 32px;
            padding: 8px 18px;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            font-size: 13px;
            font-weight: 500;
            margin-bottom: 20px;
            color: #ffa3b3;
        }

        .security-badge::before {
            content: "🛡️";
            font-size: 16px;
        }

        .container {
            max-width: 600px;
            margin: 0 auto;
            background: rgba(18, 25, 45, 0.65);
            backdrop-filter: blur(20px);
            border-radius: 48px;
            padding: 24px 20px 32px;
            box-shadow: 0 25px 45px rgba(0,0,0,0.5), 0 0 0 1px rgba(255,255,255,0.05);
        }

        h1 {
            font-size: 2rem;
            font-weight: 700;
            background: linear-gradient(135deg, #fff, #8a9eff);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: -0.5px;
            margin-bottom: 6px;
        }

        .sub {
            color: #8e9ab0;
            font-size: 0.85rem;
            margin-bottom: 28px;
            border-left: 3px solid #3e6bff;
            padding-left: 12px;
        }

        /* فۆرمی زیادکردنی ئەپ */
        .add-app {
            background: #111827;
            border-radius: 32px;
            padding: 18px;
            margin-bottom: 28px;
            border: 1px solid #2a3450;
        }

        .add-app h3 {
            font-size: 1.1rem;
            margin-bottom: 12px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        input, textarea {
            width: 100%;
            background: #0b0f1a;
            border: 1px solid #2a3450;
            border-radius: 28px;
            padding: 14px 18px;
            color: white;
            font-size: 0.9rem;
            margin-bottom: 12px;
            font-family: inherit;
        }

        textarea {
            border-radius: 24px;
            resize: vertical;
            min-height: 80px;
        }

        button {
            background: linear-gradient(105deg, #2c5eff, #5b3eff);
            border: none;
            border-radius: 40px;
            padding: 14px 20px;
            font-weight: 600;
            font-size: 1rem;
            color: white;
            width: 100%;
            cursor: pointer;
            transition: 0.2s;
            box-shadow: 0 5px 15px rgba(44,94,255,0.3);
        }

        button:active {
            transform: scale(0.97);
        }

        /* لیستی ئەپەکان */
        .app-list {
            margin-top: 20px;
        }

        .app-card {
            background: rgba(10, 15, 27, 0.7);
            backdrop-filter: blur(8px);
            border-radius: 28px;
            padding: 16px;
            margin-bottom: 14px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border: 1px solid rgba(72, 120, 255, 0.3);
            transition: 0.15s;
        }

        .app-info {
            flex: 1;
        }

        .app-name {
            font-weight: 700;
            font-size: 1.1rem;
            display: flex;
            align-items: center;
            gap: 8px;
            flex-wrap: wrap;
        }

        .app-url {
            font-size: 0.7rem;
            color: #7f8ea3;
            word-break: break-all;
            margin-top: 6px;
        }

        .download-btn {
            background: #1f2a46;
            border-radius: 40px;
            padding: 10px 16px;
            font-size: 0.8rem;
            font-weight: 600;
            color: #b5cbff;
            text-decoration: none;
            display: inline-block;
            margin-left: 10px;
            border: 0.5px solid #4f6ef0;
        }

        .delete-btn {
            background: rgba(255, 70, 90, 0.2);
            border: none;
            border-radius: 40px;
            padding: 8px 14px;
            color: #ff8a9e;
            font-weight: 600;
            font-size: 0.75rem;
            width: auto;
            margin-left: 8px;
            box-shadow: none;
        }

        .badge-protect {
            background: #00a86b20;
            border-radius: 30px;
            padding: 4px 12px;
            font-size: 0.65rem;
            color: #6effb0;
            display: inline-block;
        }

        footer {
            text-align: center;
            margin-top: 28px;
            font-size: 0.7rem;
            color: #5d6f8f;
        }

        .warning {
            background: #ffcc0033;
            border-left: 4px solid #ffb347;
            padding: 12px;
            border-radius: 20px;
            font-size: 0.75rem;
            margin-top: 20px;
        }
    </style>
</head>
<body>
<div class="container">
    <div class="security-badge">پارێزراوە لە Revoke & Crack</div>
    <h1>7AJI‑IOS</h1>
    <div class="sub">دابەزاندنی IPA بە لینکی ڕاستەوخۆ • دەسکاری خۆت بکە</div>

    <!-- زیادکردنی ئەپ یان یاری -->
    <div class="add-app">
        <h3>➕ زیادکردنی ئەپ / یاری</h3>
        <input type="text" id="appName" placeholder="ناوی بەرنامە یان یاری (م: Spotify++)">
        <textarea id="directLink" placeholder="لینکی ڕاستەوخۆی فایلەکە (.ipa)"></textarea>
        <button id="addAppBtn">زیادکردن & پاراستن</button>
        <div class="warning">⚠️ تەنها لینکی ڕاستەوخۆی .ipa دابنێ. ئەم وێبسایتە بە شێوەی local لە لاپەرەکەت دەپارێزرێت و هیچ داتایەک بۆ سێرڤەر نانێردرێت.</div>
    </div>

    <!-- لیستی ئەپە پارێزراوەکان -->
    <div class="app-list">
        <h3 style="margin-bottom: 14px;">📱 ئەپ و یارییەکان (پارێزراو)</h3>
        <div id="appsContainer"></div>
    </div>
    <footer>
        🛡️ پاراستنی تایبەت لە ڕیڤۆککردن • ھەموو دابەزاندنێک بە لینکی ڕاستەوخۆ • دەسکاری تەواو
    </footer>
</div>

<script>
    // کلیلی پاراستن و کراک - چاودێری کردنی integrity و کۆدە زیانبەخشەکان
    const STORAGE_KEY = "7AJI_secure_apps";
    let appsList = [];

    // بارکردنی داتا پارێزراوەکان
    function loadApps() {
        const stored = localStorage.getItem(STORAGE_KEY);
        if(stored) {
            try {
                appsList = JSON.parse(stored);
                // پاکنکردنی لینکی نادروست یان کۆدی کراک هاتوو
                appsList = appsList.filter(app => 
                    app && typeof app.name === "string" && 
                    typeof app.url === "string" && 
                    (app.url.startsWith("https://") || app.url.startsWith("http://")) &&
                    (app.url.includes(".ipa") || app.url.includes(".IPA"))
                );
                renderApps();
            } catch(e) { appsList = []; saveApps(); }
        } else {
            // نموونەی سەرەتایی بۆ نمایش
            appsList = [
                { name: "Dopamine IPA", url: "https://example.com/dopamine.ipa", protected: true },
                { name: "uYouEnhanced", url: "https://example.com/uYou.ipa", protected: true }
            ];
            saveApps();
            renderApps();
        }
    }

    function saveApps() {
        // ئەنجامدانی پاکنەوەی کراک: سەرجەم لینکەکان پشکنینیان بۆ دەکرێت
        const sanitized = appsList.map(app => ({
            name: app.name.replace(/[<>]/g, '').substring(0, 60),
            url: app.url.replace(/['"`]/g, ''),
            protected: true
        }));
        localStorage.setItem(STORAGE_KEY, JSON.stringify(sanitized));
        appsList = sanitized;
    }

    // ڕێگری لە کراکی داونلۆد
    function validateDownloadLink(url) {
        // پاراستن لە جێبەجێکردنی javascript: یان data: و هێرشەکانی کراک
        const dangerous = /^(javascript:|data:|vbscript:|file:)/i;
        if(dangerous.test(url)) return false;
        // دڵنیابە لە پسپۆڕی لینکی ipa
        if(!url.includes('.ipa') && !url.includes('.IPA')) return false;
        try {
            const urlObj = new URL(url);
            return (urlObj.protocol === "https:" || urlObj.protocol === "http:");
        } catch(e) {
            return false;
        }
    }

    // زیادکردنی ئەپ
    function addApp() {
        let name = document.getElementById("appName").value.trim();
        let link = document.getElementById("directLink").value.trim();

        if(!name) {
            alert("تکایە ناوی ئەپ یان یاری بنووسە");
            return;
        }
        if(!link) {
            alert("لینکی ڕاستەوخۆی فایلی .ipa بنووسە");
            return;
        }
        if(!validateDownloadLink(link)) {
            alert("لینکەکە نادروستە یان پرۆتۆکۆلی پارێزراو نییە. دەبێت لینکی دروستی .ipa بێت (https://...)");
            return;
        }

        // دەستکاری بۆ پاراستن لە دڕۆپکردنی کراک
        const newApp = {
            name: name.slice(0, 55),
            url: link,
            protected: true,
            addedTimestamp: Date.now()
        };
        appsList.unshift(newApp);
        saveApps();
        renderApps();
        document.getElementById("appName").value = "";
        document.getElementById("directLink").value = "";
    }

    // دابەزاندنی پارێزراو (دەستکاری نەکراو)
    function downloadApp(url, appName) {
        if(!validateDownloadLink(url)) {
            alert("ئەم لینکە پاراستنەکانی تێپەڕ نەکردووە: دەستکاری نەکە و لینکی ڕاستەوخۆ بەکاربهێنە");
            return;
        }
        // دروستکردنی ئەنکەری داونلۆد بەبێ زیادەڕۆیی
        const downloadAnchor = document.createElement('a');
        downloadAnchor.href = url;
        downloadAnchor.download = appName.replace(/[^a-z0-9]/gi, '_') + ".ipa";
        downloadAnchor.target = "_blank";
        downloadAnchor.rel = "noopener noreferrer";
        document.body.appendChild(downloadAnchor);
        downloadAnchor.click();
        document.body.removeChild(downloadAnchor);
        
        // نمایشی پارێزەر
        const toastMsg = document.createElement('div');
        toastMsg.innerText = `✅ دابەزاندنی ${appName} دەستی پێکرد (پارێزراو لە ڕیڤۆک)`;
        toastMsg.style.position = "fixed";
        toastMsg.style.bottom = "20px";
        toastMsg.style.left = "20px";
        toastMsg.style.right = "20px";
        toastMsg.style.backgroundColor = "#1a2a4f";
        toastMsg.style.color = "white";
        toastMsg.style.padding = "12px";
        toastMsg.style.borderRadius = "28px";
        toastMsg.style.textAlign = "center";
        toastMsg.style.zIndex = "9999";
        toastMsg.style.backdropFilter = "blur(10px)";
        toastMsg.style.fontSize = "0.85rem";
        document.body.appendChild(toastMsg);
        setTimeout(() => toastMsg.remove(), 2500);
    }

    // سڕینەوەی ئەپ (دەسکاری بەکارهێنەر)
    function deleteApp(index) {
        if(confirm("ئایا دڵنیایت لە سڕینەوەی ئەم بەرنامەیە؟ دەتوانیت دووبارە زیاد بکەیت.")) {
            appsList.splice(index, 1);
            saveApps();
            renderApps();
        }
    }

    // ڕێگری لە کراکی ناوەوەی وێبسایت و دەستکاری DOM
    function antiTamper() {
        setInterval(() => {
            // پشکنینی بۆ زیادکراوی نایاسایی لە localStorage
            const current = localStorage.getItem(STORAGE_KEY);
            if(current) {
                try {
                    let parsed = JSON.parse(current);
                    if(!Array.isArray(parsed)) {
                        loadApps(); // ڕیستۆرکردنەوە
                    } else {
                        for(let item of parsed) {
                            if(item && typeof item.url === "string" && !validateDownloadLink(item.url)) {
                                loadApps(); // گەڕانەوەی کۆپی پاک
                                break;
                            }
                        }
                    }
                } catch(e) { loadApps(); }
            } else {
                saveApps();
            }
        }, 2000);
    }

    // رێگری لە کراک بە کۆنسۆڵ و ڕایتەرای کۆدی زیانبەخش
    (function blockConsoleHacks() {
        const noOp = () => {};
        if(window.console && console.clear) {
            // ڕێگری لە پاکردنەوەی کۆنسۆڵ بۆ مەبەستی کراک
            console.clear = noOp;
        }
        // قەدەغەکردنی دەستکاری global variables
        Object.defineProperty(window, 'localStorage', {
            configurable: false,
            writable: false
        });
    })();

    function renderApps() {
        const container = document.getElementById("appsContainer");
        if(!container) return;
        if(appsList.length === 0) {
            container.innerHTML = `<div style="text-align:center; padding:30px; background:#0f1422; border-radius: 32px;">🛡️ هیچ ئەپێک نییە. ئەپ یان یاری زیاد بکە بە لینکی ڕاستەوخۆی IPA</div>`;
            return;
        }
        let html = "";
        for(let i = 0; i < appsList.length; i++) {
            const app = appsList[i];
            html += `
                <div class="app-card">
                    <div class="app-info">
                        <div class="app-name">
                            ${escapeHtml(app.name)}
                            <span class="badge-protect">🔒 پارێزراو لە ڕیڤۆک</span>
                        </div>
                        <div class="app-url">${truncateUrl(app.url, 55)}</div>
                    </div>
                    <div style="display: flex; gap: 8px;">
                        <a class="download-btn" href="#" data-url="${escapeAttr(app.url)}" data-name="${escapeAttr(app.name)}">📥 دابەزاندن</a>
                        <button class="delete-btn" data-index="${i}">سڕینەوە</button>
                    </div>
                </div>
            `;
        }
        container.innerHTML = html;

        // گرێدانی ڕووداوی داونلۆد بە شێوەی پارێزراو
        document.querySelectorAll('.download-btn').forEach(btn => {
            btn.addEventListener('click', (e) => {
                e.preventDefault();
                const url = btn.getAttribute('data-url');
                const name = btn.getAttribute('data-name');
                if(url && name) downloadApp(url, name);
                else alert("هەڵە: زانیاری دابەزاندن نادروستە");
            });
        });

        document.querySelectorAll('.delete-btn').forEach(btn => {
            btn.addEventListener('click', (e) => {
                const idx = btn.getAttribute('data-index');
                if(idx !== null) deleteApp(parseInt(idx));
            });
        });
    }

    function escapeHtml(str) {
        if(!str) return "";
        return str.replace(/[&<>]/g, function(m) {
            if(m === '&') return '&amp;';
            if(m === '<') return '&lt;';
            if(m === '>') return '&gt;';
            return m;
        });
    }

    function escapeAttr(str) {
        if(!str) return "";
        return str.replace(/["']/g, '&quot;');
    }

    function truncateUrl(url, maxLen) {
        if(url.length <= maxLen) return url;
        return url.slice(0, maxLen-3) + "...";
    }

    // بەکارهێنانی پاککردنەوەی دەسکارییە خراپەکان و ڕیڤۆک
    window.addEventListener('DOMContentLoaded', () => {
        loadApps();
        antiTamper();
        document.getElementById("addAppBtn").addEventListener("click", addApp);
    });
</script>
</body>
</html>
