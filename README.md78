<!DOCTYPE html>
<html lang="ku">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
    <title>7AJI-IOS - دابەزاندنی IPA</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; -webkit-tap-highlight-color: transparent; }
        body {
            background: #0b0f1a;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, sans-serif;
            padding: 24px 16px 40px;
            color: #f0f3fa;
        }
        .main-card {
            max-width: 560px;
            margin: 0 auto;
            background: rgba(18, 24, 38, 0.9);
            backdrop-filter: blur(24px);
            border-radius: 56px;
            padding: 24px 20px 34px;
            box-shadow: 0 20px 45px rgba(0,0,0,0.5);
            border: 1px solid #2f3d70;
        }
        h1 {
            font-size: 2.5rem;
            background: linear-gradient(135deg, #fff, #6e8eff);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            text-align: center;
        }
        .badge {
            text-align: center;
            margin: 8px 0 20px;
            font-size: 0.75rem;
            color: #9aafe6;
        }
        .add-area {
            background: #0f1422;
            border-radius: 40px;
            padding: 18px;
            margin-bottom: 28px;
        }
        input, textarea {
            width: 100%;
            background: #070b16;
            border: 1px solid #2a345a;
            border-radius: 44px;
            padding: 14px 18px;
            color: white;
            font-size: 0.9rem;
            margin-bottom: 12px;
        }
        textarea { border-radius: 28px; min-height: 80px; }
        button {
            background: linear-gradient(95deg, #3b6aff, #8a5eff);
            border: none;
            border-radius: 44px;
            padding: 14px;
            font-weight: bold;
            color: white;
            width: 100%;
            font-size: 1rem;
            cursor: pointer;
        }
        button:active { transform: scale(0.97); }
        .app-item {
            background: #0c1120;
            border-radius: 34px;
            padding: 14px;
            margin-bottom: 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            border: 1px solid #2c3760;
        }
        .app-name {
            font-weight: bold;
            display: flex;
            gap: 8px;
            align-items: center;
            flex-wrap: wrap;
        }
        .protect {
            background: #1e7a5a30;
            font-size: 0.6rem;
            padding: 3px 10px;
            border-radius: 30px;
            color: #7effcf;
        }
        .app-url {
            font-size: 0.65rem;
            color: #97a7d1;
            word-break: break-all;
            margin-top: 5px;
        }
        .btn-down {
            background: #1e2b50;
            padding: 8px 14px;
            border-radius: 40px;
            text-decoration: none;
            color: #c1d5ff;
            font-size: 0.75rem;
            font-weight: 600;
            display: inline-block;
        }
        .btn-del {
            background: rgba(255, 70, 100, 0.2);
            border: none;
            padding: 8px 14px;
            border-radius: 40px;
            color: #ff9eaf;
            margin-left: 8px;
        }
        .empty {
            text-align: center;
            padding: 40px;
            color: #7f8db0;
        }
        footer {
            text-align: center;
            font-size: 0.65rem;
            margin-top: 24px;
            color: #6a78a2;
        }
        .note {
            background: #ffbd3310;
            border-left: 3px solid #ffae42;
            padding: 8px;
            font-size: 0.7rem;
            border-radius: 20px;
            margin-top: 14px;
        }
    </style>
</head>
<body>
<div class="main-card">
    <h1>7AJI‑IOS</h1>
    <div class="badge">🛡️ دابەزاندنی IPA • پارێزراو لە ڕیڤۆک و کراک</div>

    <div class="add-area">
        <input type="text" id="appName" placeholder="ناوی بەرنامە یان یاری ...">
        <textarea id="ipaLink" placeholder="لینکی ڕاستەوخۆی فایل .IPA (https://... .ipa)"></textarea>
        <button id="addBtn">➕ زیادکردن و پاراستن</button>
        <div class="note">🔐 هەموو داتاکان لەسەر ئامێری خۆت دەپارێزرێن • هیچ سێرڤەرێک نییە بۆ ڕیڤۆک</div>
    </div>

    <div id="listArea"></div>
    <footer>7AJI-IOS • دەسکاری تەواو • بەبێ ڕیڤۆک • هەرگیز لاناچێت</footer>
</div>

<script>
    (function(){
        const KEY = "7AJI_LOCAL_IPA";
        let apps = [];

        function isValidLink(url) {
            if(!url || typeof url !== "string") return false;
            let u = url.toLowerCase();
            if(!u.includes(".ipa")) return false;
            if(u.startsWith("javascript:") || u.startsWith("data:") || u.startsWith("vbscript:")) return false;
            try {
                let uri = new URL(url);
                return (uri.protocol === "https:" || uri.protocol === "http:");
            } catch(e) { return false; }
        }

        function sanitize(str) {
            if(!str) return "بێ ناو";
            return str.replace(/[&<>]/g, function(m){
                return m === '&' ? '&amp;' : (m === '<' ? '&lt;' : '&gt;');
            }).substring(0, 55);
        }

        function save() {
            let clean = apps.filter(a => a && a.name && a.url && isValidLink(a.url));
            localStorage.setItem(KEY, JSON.stringify(clean));
            apps = clean;
            render();
        }

        function load() {
            let raw = localStorage.getItem(KEY);
            if(raw) {
                try {
                    let parsed = JSON.parse(raw);
                    if(Array.isArray(parsed)) {
                        apps = parsed.filter(a => a && a.name && a.url && isValidLink(a.url));
                    } else { apps = []; }
                } catch(e) { apps = []; }
            }
            if(apps.length === 0) {
                apps = [
                    { name: "uYouEnhanced (YouTube++)", url: "https://github.com/example/uYouPlus.ipa" },
                    { name: "Dopamine IPA", url: "https://github.com/example/dopamine.ipa" }
                ];
                save();
            } else { render(); }
        }

        function addApp() {
            let name = document.getElementById("appName").value.trim();
            let link = document.getElementById("ipaLink").value.trim();
            if(!name) { alert("تکایە ناوێک بنووسە"); return; }
            if(!link) { alert("لینکی ڕاستەوخۆی .IPA پێویستە"); return; }
            if(!isValidLink(link)) { alert("❌ لینکەکە نادروستە! دەبێت https://... .ipa بێت"); return; }
            apps.unshift({ name: sanitize(name), url: link });
            save();
            document.getElementById("appName").value = "";
            document.getElementById("ipaLink").value = "";
        }

        function downloadItem(url, name) {
            if(!isValidLink(url)) { alert("ئەم لینکە پارێزراو نییە"); return; }
            let a = document.createElement('a');
            a.href = url;
            a.download = name.replace(/[^a-z0-9]/gi, '_') + ".ipa";
            a.target = "_blank";
            a.rel = "noopener noreferrer";
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            let msg = document.createElement('div');
            msg.innerText = `✅ دابەزاندنی ${name} دەستی پێکرد`;
            msg.style.position = "fixed";
            msg.style.bottom = "20px";
            msg.style.left = "16px";
            msg.style.right = "16px";
            msg.style.backgroundColor = "#1c274f";
            msg.style.padding = "12px";
            msg.style.borderRadius = "60px";
            msg.style.textAlign = "center";
            msg.style.zIndex = "999";
            document.body.appendChild(msg);
            setTimeout(() => msg.remove(), 2000);
        }

        function deleteApp(idx) {
            if(confirm("سڕینەوەی ئەم بەرنامەیە؟")) {
                apps.splice(idx, 1);
                save();
            }
        }

        function render() {
            let container = document.getElementById("listArea");
            if(!container) return;
            if(apps.length === 0) {
                container.innerHTML = `<div class="empty">🛡️ هیچ بەرنامەیەک نییە، سەرەتا زیاد بکە</div>`;
                return;
            }
            let html = "";
            for(let i=0; i<apps.length; i++) {
                let app = apps[i];
                let shortUrl = app.url.length > 55 ? app.url.slice(0,52)+"..." : app.url;
                html += `
                    <div class="app-item">
                        <div style="flex:2">
                            <div class="app-name">
                                ${sanitize(app.name)}
                                <span class="protect">🔒 پارێزراو لە ڕیڤۆک</span>
                            </div>
                            <div class="app-url">${sanitize(shortUrl)}</div>
                        </div>
                        <div style="display: flex; margin-top: 8px;">
                            <a class="btn-down" href="#" data-url="${app.url.replace(/"/g, '&quot;')}" data-name="${sanitize(app.name)}">📥 دابەزاندن</a>
                            <button class="btn-del" data-idx="${i}">سڕینەوە</button>
                        </div>
                    </div>
                `;
            }
            container.innerHTML = html;

            document.querySelectorAll('.btn-down').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    e.preventDefault();
                    let url = btn.getAttribute('data-url');
                    let name = btn.getAttribute('data-name');
                    if(url && name) downloadItem(url, name);
                });
            });
            document.querySelectorAll('.btn-del').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    let idx = btn.getAttribute('data-idx');
                    if(idx !== null) deleteApp(parseInt(idx));
                });
            });
        }

        window.addEventListener('DOMContentLoaded', () => {
            load();
            document.getElementById("addBtn").addEventListener("click", addApp);
            // پاراستن لە دەستکاری کۆنسۆڵ
            if(window.console && console.clear) console.clear = function(){};
            setInterval(() => {
                let check = localStorage.getItem(KEY);
                if(check) {
                    try {
                        let parsed = JSON.parse(check);
                        if(!Array.isArray(parsed)) load();
                        else {
                            for(let item of parsed) {
                                if(item.url && !isValidLink(item.url)) { load(); break; }
                            }
                        }
                    } catch(e) { load(); }
                }
            }, 3000);
        });
    })();
</script>
</body>
</html>
