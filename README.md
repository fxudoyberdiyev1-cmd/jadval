<!DOCTYPE html>
<html lang="uz">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Дарс Жадвали</title>
    <style>
        :root { --primary: #2563eb; --dark: #1e293b; --bg: #f8fafc; }
        body { font-family: sans-serif; background: var(--bg); margin: 0; padding: 20px; display: flex; flex-direction: column; align-items: center; }
        .container { width: 100%; max-width: 550px; background: white; border-radius: 20px; box-shadow: 0 10px 25px rgba(0,0,0,0.1); overflow: hidden; }
        .header { background: var(--dark); color: white; padding: 25px; text-align: center; }
        table { width: 100%; border-collapse: collapse; }
        td { padding: 15px 20px; border-bottom: 1px solid #f1f5f9; }
        .num-badge { background: #eff6ff; color: var(--primary); width: 28px; height: 28px; display: flex; align-items: center; justify-content: center; border-radius: 8px; font-weight: bold; }
        .subject-name { font-weight: 600; color: var(--dark); font-size: 15px; }
        .topic-text { display: block; color: #64748b; font-size: 13px; font-style: italic; margin-top: 4px; }
        
        /* Таҳрирлаш панели */
        .admin-panel { margin-top: 20px; padding: 15px; background: #fff; border-radius: 12px; box-shadow: 0 4px 10px rgba(0,0,0,0.05); width: 100%; max-width: 520px; display: none; }
        .admin-panel input { width: 90%; padding: 8px; margin: 5px 0; border: 1px solid #ddd; border-radius: 5px; }
        .edit-btn { margin-top: 20px; background: none; border: none; color: #94a3b8; cursor: pointer; font-size: 12px; }
        .save-btn { background: var(--primary); color: white; border: none; padding: 10px 20px; border-radius: 5px; cursor: pointer; width: 100%; margin-top: 10px; }
    </style>
</head>
<body>

    <div class="container">
        <div class="header"><h2>📅 ДАРС ЖАДВАЛИ</h2></div>
        <table id="scheduleTable">
            </table>
    </div>

    <button class="edit-btn" onclick="toggleAdmin()">⚙️ Мавзуларни ўзгартириш</button>

    <div class="admin-panel" id="adminPanel">
        <h3>Мавзуларни ёзинг:</h3>
        <div id="inputsContainer"></div>
        <button class="save-btn" onclick="saveTopics()">✅ Сақлаш ва Кўриш</button>
    </div>

    <script>
        const subjects = [
            "Iqtisodiyot nazariyasi 2",
            "Xorijiy til 2",
            "O‘zbek (rus) tili",
            "Dinshunoslik",
            "Jismoniy madaniyat va sport",
            "Akademik ko‘nikmalar",
            "Amaliy matematika 2"
        ];

        // Маълумотларни юклаш
        function loadData() {
            const table = document.getElementById('scheduleTable');
            const inputs = document.getElementById('inputsContainer');
            table.innerHTML = '';
            inputs.innerHTML = '';

            subjects.forEach((s, i) => {
                const savedTopic = localStorage.getItem('topic' + i) || "Мавзу киритилмаган";
                
                // Жадвални чиқариш
                table.innerHTML += `
                    <tr>
                        <td style="width:40px"><div class="num-badge">${i+1}</div></td>
                        <td>
                            <span class="subject-name">${s}</span>
                            <span class="topic-text" id="t${i}">${savedTopic}</span>
                        </td>
                    </tr>`;

                // Инпутларни чиқариш
                inputs.innerHTML += `
                    <div>
                        <label>${i+1}. ${s}</label><br>
                        <input type="text" id="input${i}" value="${savedTopic}">
                    </div><br>`;
            });
        }

        function toggleAdmin() {
            const panel = document.getElementById('adminPanel');
            panel.style.display = panel.style.display === 'block' ? 'none' : 'block';
        }

        function saveTopics() {
            subjects.forEach((s, i) => {
                const val = document.getElementById('input' + i).value;
                localStorage.setItem('topic' + i, val);
            });
            alert("Мавзулар сақланди!");
            location.reload();
        }

        loadData();
    </script>
</body>
</html>
