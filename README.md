<!DOCTYPE html>
<html lang="ku">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>7AJI-IOS - دابەزاندنی IPA</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background: linear-gradient(145deg, #0a0f1a 0%, #07111f 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            animation: bgMove 8s infinite alternate;
        }

        @keyframes bgMove {
            0% { background-position: 0% 0%; }
            100% { background-position: 100% 100%; }
        }

        .card {
            max-width: 480px;
            width: 100%;
            background: rgba(15, 20, 35, 0.85);
            backdrop-filter: blur(20px);
            border-radius: 64px;
            padding: 40px 28px 50px;
            text-align: center;
            box-shadow: 0 30px 50px rgba(0,0,0,0.5), 0 0 0 1px rgba(0, 255, 255, 0.3);
            transition: all 0.3s ease;
            animation: floatCard 3s ease-in-out infinite;
        }

        @keyframes floatCard {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-8px); }
            100% { transform: translateY(0px); }
        }

        .logo {
            font-size: 58px;
            font-weight: 800;
            background: linear-gradient(135deg, #00e6ff, #0077ff, #b200ff);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin-bottom: 10px;
            letter-spacing: 2px;
            text-shadow: 0 0 20px rgba(0,200,255,0.5);
        }

        .sub {
            color: #6c8cff;
            font-size: 14px;
            background: rgba(0,200,255,0.15);
            display: inline-block;
            padding: 6px 18px;
            border-radius: 30px;
            margin-bottom: 20px;
        }

        .welcome {
            background: rgba(0, 100, 255, 0.15);
            padding: 24px 16px;
            border-radius: 48px;
            margin: 25px 0;
            border: 1px solid rgba(0, 230, 255, 0.4);
        }

        .welcome h2 {
            font-size: 28px;
            color: white;
            margin-bottom: 10px;
        }

        .welcome h2 span {
            color: #0cf;
            text-shadow: 0 0 5px cyan;
        }

        .welcome p {
            color: #bcd0ff;
            font-size: 16px;
        }

        .btn {
            display: block;
            background: linear-gradient(90deg, #0066ff, #00ccff);
            padding: 18px 20px;
            margin: 20px 0;
            border-radius: 60px;
            font-size: 24px;
            font-weight: bold;
            color: white;
            text-decoration: none;
            box-shadow: 0 10px 25px rgba(0,150,255,0.5);
            transition: 0.2s;
            border: none;
            cursor: pointer;
        }

        .btn:active {
            transform: scale(0.97);
        }

        .secure {
            background: rgba(0,0,0,0.5);
            border-radius: 40px;
            padding: 12px;
            font-size: 13px;
            color: #8aa9ff;
            border: 1px dashed #0cf;
            margin-top: 15px;
        }

        footer {
            font-size: 11px;
            color: #4a6085;
            margin-top: 25px;
        }

        @keyframes pulse {
            0% { opacity: 0.7; }
            100% { opacity: 1; }
        }
    </style>
</head>
<body>

<div class="card">
    <div class="logo">7AJI-IOS</div>
    <div class="sub">⚡ IPA DIRECT ⚡</div>

    <div class="welcome">
        <h2>✨ بەخێربێیت بۆ <span>7AJI-IOS</span> ✨</h2>
        <p>باشترین شوێن بۆ دابەزاندنی <strong style="color:#0cf;">فایلی IPA</strong> بۆ ئایفۆن و ئایپاد.<br>
        تەنها یەک کلیک، دابەزاندنی ڕاستەوخۆ و پارێزراو.</p>
    </div>

    <!-- لینکی ڕاستەوخۆی دابەزاندن - بەبێ هیچ ڕیڤۆ یان بەربەست -->
    <a href="https://github.com/TelegramMessenger/Telegram-iOS/releases/download/8.0/Telegram_iOS.ipa" id="downloadBtn" class="btn">
        📲 دابەزاندنی IPA ئێستا
    </a>

    <div class="secure">
        🔐 دابەزاندنی ئەمین و نهێنی | فایلەکە بە تەواوی سەلامەتە | پشتگیری iOS 15+ 🔐
    </div>
    <footer>
        7AJI-IOS • دابەزاندن بە یەک کلیک • هیچ ڕیکلام یان ڕیڤۆ نییە
    </footer>
</div>

<script>
    // هیچ ڕیڤۆ یان پۆپئاپێک نییە - تەنها ئاگاداری بەکارهێنەر بۆ دابەزاندنی ڕاستەوخۆ
    const btn = document.getElementById('downloadBtn');
    
    // ئەمە تەنها کلیکێکی ئاساییە، بەبێ هیچ دەستکارییەک
    // لینکەکە ڕاستەوخۆ دەچێت بۆ فایلی IPA - تۆ دەتوانیت لینکی خۆت دابنێیت
    // بەڵام ئێستا نموونەیەکە بۆ Telegram IPA کە ڕاستەوخۆ دابەزێت
    btn.addEventListener('click', function(e) {
        // هیچ blocking process نییە، ڕێگە بە دابەزاندن دەدات
        console.log('دابەزاندن دەستی پێکرد...');
    });
</script>

</body>
</html>
