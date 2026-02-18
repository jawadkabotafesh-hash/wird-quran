<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>وردي اليومي - قراءة الورد</title>
    <style>
        body { font-family: 'Arial', sans-serif; text-align: center; background: #0f2027; color: white; padding: 20px; margin: 0; }
        .card { background: rgba(255, 255, 255, 0.1); padding: 20px; border-radius: 15px; backdrop-filter: blur(10px); }
        h1 { color: #2ecc71; }
        .quran-container { margin-top: 20px; width: 100%; height: 600px; border-radius: 10px; overflow: hidden; border: 2px solid #2ecc71; }
        iframe { width: 100%; height: 100%; border: none; }
    </style>
</head>
<body>

    <div class="card">
        <h1>ورد القرآن اليومي 📖</h1>
        <p id="date-display"></p>
        <p id="wird-info" style="font-size: 1.2rem; font-weight: bold;"></p>
        
        <div class="quran-container">
            <iframe id="quran-frame" src=""></iframe>
        </div>
    </div>

    <script>
        // مصفوفة الأجزاء الـ 30
        const juzzInfo = [
            "الجزء 1", "الجزء 2", "الجزء 3", "الجزء 4", "الجزء 5",
            "الجزء 6", "الجزء 7", "الجزء 8", "الجزء 9", "الجزء 10",
            "الجزء 11", "الجزء 12", "الجزء 13", "الجزء 14", "الجزء 15",
            "الجزء 16", "الجزء 17", "الجزء 18", "الجزء 19", "الجزء 20",
            "الجزء 21", "الجزء 22", "الجزء 23", "الجزء 24", "الجزء 25",
            "الجزء 26", "الجزء 27", "الجزء 28", "الجزء 29", "الجزء 30"
        ];

        const today = new Date();
        const start = new Date(today.getFullYear(), 0, 0);
        const diff = today - start;
        const dayOfYear = Math.floor(diff / (1000 * 60 * 60 * 24));
        
        // حساب الجزء (كل يوم جزء، ويعيد الكرة بعد 30 يوم)
        const currentJuzIndex = (dayOfYear % 30); 
        const juzNumber = currentJuzIndex + 1;

        // تحديث النصوص
        document.getElementById("date-display").innerText = "تاريخ اليوم: " + today.toLocaleDateString('ar-EG');
        document.getElementById("wird-info").innerText = "وردك اليوم: " + juzzInfo[currentJuzIndex];

        // تحديث رابط المصحف ليفتح الجزء المطلوب مباشرة
        // نستخدم رابط quran.com ونحدد الجزء (Juz)
        document.getElementById("quran-frame").src = "https://quran.com/juz/" + juzNumber;
    </script>
</body>
</html>
