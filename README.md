<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <title>Sido Anime</title>
    <style>
        body { background: #000; color: #fff; font-family: Arial, sans-serif; text-align: center; margin: 0; padding: 20px; }
        .grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(140px, 1fr)); gap: 15px; }
        .card { background: #1a1a1a; border-radius: 10px; padding: 10px; border: 1px solid #333; transition: 0.3s; }
        img { width: 100%; border-radius: 8px; height: 200px; object-fit: cover; }
        h1 { color: #ff4757; }
    </style>
</head>
<body>
    <h1>SIDO ANIME PRO</h1>
    <div id="grid" class="grid">جاري تحميل الأنمي...</div>
    <script>
        async function load() {
            try {
                const res = await fetch('https://api.jikan.moe/v4/top/anime?limit=15');
                const { data } = await res.json();
                document.getElementById('grid').innerHTML = data.map(a => `
                    <div class="card">
                        <img src="${a.images.jpg.image_url}">
                        <p style="font-size:12px; margin-top:10px;">${a.title}</p>
                    </div>
                `).join('');
            } catch (e) { document.getElementById('grid').innerHTML = "خطأ في الاتصال"; }
        }
        load();
    </script>
</body>
</html>
# animex-pro
