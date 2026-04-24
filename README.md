<!DOCTYPE html>
<html lang="uz">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Студент Кундалиги</title>
    <style>
        :root {
            --primary: #3b82f6;
            --dark: #0f172a;
            --light: #f8fafc;
            --accent: #10b981;
        }
        body { 
            font-family: 'Segoe UI', Tahoma, sans-serif; 
            background-color: #e5e7eb; 
            margin: 0; padding: 15px;
            display: flex; justify-content: center;
        }
        .app-container {
            width: 100%; max-width: 650px;
            background: white; border-radius: 24px;
            box-shadow: 0 20px 50px rgba(0,0,0,0.15); overflow: hidden;
        }
        .header {
            background: var(--dark); color: white; padding: 25px; text-align: center;
        }
        .date-badge {
            background: rgba(255,255,255,0.1); padding: 8px 15px;
            border-radius: 50px; font-size: 14px; display: inline-block; margin-bottom: 10px;
        }
        .quote-box {
            padding: 15px; background: #f1f5f9; font-size: 13px;
            color: #475569; text-align: center; font-style: italic;
        }
        table { width: 100%; border-collapse: collapse; }
        th { 
            background: #f8fafc; color: #64748b; font-size: 12px;
            text-transform: uppercase; padding: 12px; border-bottom: 2px solid #e2e8f0;
        }
        td { padding: 15px 10px; border-bottom: 1px solid #f1f5f9; text-align: center; }
        .tr-col { width: 40px; font-weight: bold; color: var(--primary); }
        .subject-col { text-align: left; padding-left: 15px; }
        .subject-name { font-weight: 600; color: var(--dark); display: block; }
        .topic-name { font-size: 12px; color: #64748b; margin-top: 3px; display: block; }
        
        .timer-box {
            background: var(--primary); color: white; padding: 10px;
            text-align: center; font-weight: bold; font-size: 14px;
        }
        tr:hover { background: #f9fafb; }
    </style>
</head>
<body>

<div class="app-container">
    <div class="header">
        <div class="date-badge" id="currentDate">Юкланмоқда...</div>
        <h2 style="margin:0">📓 ДАРС ЖАДВАЛИ</h2>
    </div>

    <div class="timer-box" id="timer">
        ⏳ Дарс жараёни кузатилмоқда...
    </div>

    <table>
        <thead>
            <tr>
                <th>Т/Р</th>
                <th class="subject-col">Фан номи ва Мавзу</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td class="tr-col">1</td>
                <td class="subject-col">
                    <span class="subject-name">Iqtisodiyot nazariyasi 2</span>
                    <span class="topic-name">Мавзу: Бозор мувозанати ва нарх шаклланиши</span>
                </td>
            </tr>
            <tr>
                <td class="tr-col">2</td>
                <td class="subject-col">
                    <span class="subject-name">Xorijiy til 2</span>
                    <span class="topic-name">Мавзу: Intermediate Grammar Review</span>
                </td>
            </tr>
            <tr>
                <td class="tr-col">3</td>
                <td class="subject-col">
                    <span class="subject-name">O‘zbek (rus) tili</span>
                    <span class="topic-name">Мавзу: Соҳавий терминлар билан ишлаш</span>
                </td>
            </tr>
            <tr>
                <td class="tr-col">4</td>
                <td class="subject-col">
                    <span class="subject-name">Dinshunoslik</span>
                    <span class="topic-name">Мавзу: Жаҳон динлари тарихи</span>
                </td>
            </tr>
            <tr>
                <td class="tr-col">5</td>
                <td class="subject-col">
                    <span class="subject-name">Jismoniy madaniyat va sport</span>
                    <span class="topic-name">Мавзу: Енгил атлетика машғулотлари</span>
                </td>
            </tr>
            <tr>
                <td class="tr-col">6</td>
                <td class="subject-col">
                    <span class="subject-name">Akademik ko‘nikmalar</span>
                    <span class="topic-name">Мавзу: Тайм-менежмент ва самарадорлик</span>
                </td>
            </tr>
            <tr>
                <td class="tr-col">7</td>
                <td class="subject-col">
                    <span class="subject-name">Amaliy matematika 2</span>
                    <span class="topic-name">Мавзу: Дифференциал тенгламалар</span>
                </td>
            </tr>
        </tbody>
    </table>

    <div class="quote-box">
        "Илмдан бошқа нажот йўқ ва бўлмагай." — Имом Бухорий
    </div>
</div>

<script>
    // Сана ва ҳафта кунини янгилаш
    function updateDate() {
        const ҳозир = new Date();
        const вариантлар = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
        document.getElementById('currentDate').innerText = ҳозир.toLocaleDateString('uz-UZ', вариантлар);
    }

    // Таймер функцияси (намунавий)
    function updateTimer() {
        const соат = new Date().getHours();
        let хабар = "";
        if (соат >= 8 && соат < 13) хабар = "📖 Ҳозир дарслар вақти. Диққат қилинг!";
        else if (соат >= 13 && соат < 14) хабар = "☕ Тушлик вақти. Ёқимли иштаҳа!";
        else хабар = "🏠 Дарслар тугаган. Мустақил таълим вақти!";
        document.getElementById('timer').innerText = хабар;
    }

    updateDate();
    updateTimer();
    setInterval(updateTimer, 60000);
</script>

</body>
</html>
