<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Tainted Dead God</title>
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link href="https://fonts.googleapis.com/css2?family=Creepster&family=Inter:wght@400;600;800;900&display=swap" rel="stylesheet" />
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" />
    <style>
        /* ===== БАЗА ===== */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html, body {
            width: 100%;
            min-height: 100vh;
        }

        body {
            font-family: 'Inter', sans-serif;
            color: #f0ddd0;
            min-height: 100vh;
            position: relative;
            background: #0d0505 url('https://media1.tenor.com/m/ffhuaRkEl1EAAAAC/isaac-the-binding-of-isaac.gif') center/cover fixed;
        }

        /* Затемнение */
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(13, 5, 5, 0.75);
            z-index: 0;
        }

        /* Весь контент поверх затемнения */
        header,
        .container,
        footer {
            position: relative;
            z-index: 1;
        }

        /* ===== ШАПКА (ПОЛНОСТЬЮ ПРОЗРАЧНАЯ) ===== */
        header {
            background: transparent !important;
            backdrop-filter: none !important;
            border-bottom: none !important;
            padding: 14px 40px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 15px;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: none !important;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 14px;
            text-decoration: none;
        }

        /* ===== ПЕНТАГРАММА С МИГАНИЕМ ===== */
        .pentagram-icon {
            width: 44px;
            height: 44px;
            flex-shrink: 0;
            transition: 0.3s;
            animation: pentagramPulse 2.5s ease-in-out infinite;
        }

        @keyframes pentagramPulse {
            0%, 100% {
                filter: drop-shadow(0 0 15px rgba(200, 30, 40, 0.4));
                opacity: 0.9;
            }
            30% {
                filter: drop-shadow(0 0 30px rgba(200, 30, 40, 0.7));
                opacity: 1;
            }
            60% {
                filter: drop-shadow(0 0 10px rgba(200, 30, 40, 0.2));
                opacity: 0.7;
            }
            80% {
                filter: drop-shadow(0 0 40px rgba(220, 40, 50, 0.9));
                opacity: 1;
            }
        }

        .logo:hover .pentagram-icon {
            animation: none;
            filter: drop-shadow(0 0 50px rgba(220, 40, 50, 1));
            transform: rotate(15deg) scale(1.1);
        }

        .logo-text {
            font-size: 26px;
            font-weight: 900;
            letter-spacing: 0.5px;
        }

        .logo-text .tainted {
            color: #ff2233;
            text-shadow: 0 0 30px rgba(255, 30, 40, 0.4);
        }
        .logo-text .dead {
            color: #cc8899;
        }
        .logo-text .god {
            color: #ff6644;
            text-shadow: 0 0 30px rgba(255, 80, 50, 0.3);
        }

        /* ===== НАВИГАЦИЯ (БЕЗ ФОНА) ===== */
        nav {
            display: flex;
            gap: 6px;
            flex-wrap: wrap;
        }

        nav a {
            color: #aa7788;
            text-decoration: none;
            padding: 8px 18px;
            border-radius: 40px;
            font-weight: 600;
            font-size: 14px;
            transition: 0.25s;
            letter-spacing: 0.3px;
            border: none;
            outline: none;
            background: transparent !important;
            background-color: transparent !important;
            cursor: pointer;
        }

        nav a:hover,
        nav a.active {
            color: #ffddcc;
            background: transparent !important;
            background-color: transparent !important;
            box-shadow: none;
            border: none;
            outline: none;
            text-shadow: 0 0 20px rgba(255, 30, 40, 0.4);
        }

        /* Замок у закрытых вкладок */
        nav a.locked {
            color: #665555;
            cursor: not-allowed;
        }

        nav a.locked:hover {
            color: #885566;
            text-shadow: none;
        }

        /* ===== КОНТЕЙНЕР ===== */
        .container {
            max-width: 1100px;
            margin: 0 auto;
            padding: 40px 20px 60px;
        }

        /* ===== ГЕРОЙ ===== */
        .hero {
            text-align: center;
            padding: 60px 20px 40px;
            position: relative;
        }

        .hero::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 60%;
            height: 2px;
            background: linear-gradient(90deg, transparent, #cc2233, transparent);
        }

        .hero h1 {
            font-family: 'Creepster', cursive;
            font-size: 52px;
            letter-spacing: 3px;
            margin-bottom: 10px;
        }

        .hero h1 .tainted-h {
            color: #ff2233;
            text-shadow: 0 0 50px rgba(255, 30, 40, 0.4);
        }
        .hero h1 .dead-h {
            color: #cc8899;
        }
        .hero h1 .god-h {
            color: #ff6644;
            text-shadow: 0 0 50px rgba(255, 80, 50, 0.3);
        }

        .hero .sub {
            font-size: 16px;
            letter-spacing: 6px;
            text-transform: uppercase;
            color: #883344;
            margin-bottom: 16px;
        }

        .hero p {
            max-width: 600px;
            margin: 0 auto 24px;
            font-size: 17px;
            line-height: 1.7;
            color: #bb8899;
        }

        .hero p strong {
            color: #ff4455;
        }

        /* ===== СЕТКА КАРТОЧЕК ===== */
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 24px;
            margin-top: 50px;
        }

        .card {
            background: rgba(18, 6, 6, 0.85);
            backdrop-filter: blur(4px);
            border: 1px solid #331115;
            border-left: 5px solid #cc2233;
            border-radius: 16px;
            padding: 28px 24px;
            transition: 0.3s;
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.5);
        }

        .card:hover {
            border-color: #ff4455;
            border-left-color: #ff3344;
            transform: translateY(-6px);
            box-shadow: 0 14px 40px rgba(0, 0, 0, 0.6), 0 0 40px rgba(200, 30, 40, 0.08);
            background: rgba(30, 10, 10, 0.92);
        }

        .card .icon {
            font-size: 32px;
            color: #ff3344;
            margin-bottom: 12px;
            display: block;
        }

        .card h3 {
            font-size: 22px;
            font-weight: 800;
            color: #f0ddd0;
            margin-bottom: 8px;
        }

        .card p {
            color: #aa7788;
            line-height: 1.6;
            font-size: 15px;
        }

        /* ===== ССЫЛКА В КАРТОЧКЕ ===== */
        .card .link {
            display: inline-block;
            margin-top: 14px;
            color: #ff6644;
            font-weight: 600;
            text-decoration: none;
            transition: 0.2s;
            font-size: 14px;
            border-bottom: 1px solid transparent;
            cursor: pointer;
        }

        .card .link:hover {
            color: #ff8877;
            border-bottom-color: #ff4455;
            transform: translateX(4px);
        }

        /* ===== ПОПАП "В РАЗРАБОТКЕ" ===== */
        .popup-overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 999;
            background: rgba(0, 0, 0, 0.7);
            backdrop-filter: blur(4px);
            align-items: center;
            justify-content: center;
        }

        .popup-overlay.active {
            display: flex;
        }

        .popup {
            background: #1a0a0a;
            border: 2px solid #cc2233;
            border-radius: 24px;
            padding: 40px 50px;
            max-width: 400px;
            text-align: center;
            box-shadow: 0 0 60px rgba(200, 30, 40, 0.3);
            animation: popupBounce 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
        }

        @keyframes popupBounce {
            0% { transform: scale(0.7); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        .popup .lock-icon {
            font-size: 48px;
            color: #cc2233;
            margin-bottom: 16px;
        }

        .popup h2 {
            font-family: 'Creepster', cursive;
            font-size: 28px;
            color: #ff4455;
            margin-bottom: 8px;
        }

        .popup p {
            color: #bb8899;
            font-size: 16px;
            margin-bottom: 20px;
        }

        .popup .close-btn {
            background: #cc2233;
            color: #fff;
            border: none;
            padding: 10px 36px;
            border-radius: 40px;
            font-weight: 700;
            font-size: 15px;
            cursor: pointer;
            transition: 0.2s;
        }

        .popup .close-btn:hover {
            background: #ff3344;
            transform: scale(1.05);
        }

        /* ===== ФУТЕР ===== */
        footer {
            border-top: 2px solid #1a0808;
            text-align: center;
            padding: 30px 20px;
            color: #883344;
            font-size: 13px;
            letter-spacing: 0.5px;
            margin-top: 20px;
        }

        footer span {
            color: #ff3344;
        }
        footer i {
            color: #ff3344;
        }
        footer strong {
            color: #ff6677;
        }

        /* ===== АДАПТИВ ===== */
        @media (max-width: 700px) {
            header {
                padding: 12px 20px;
                flex-direction: column;
                align-items: stretch;
            }
            .logo {
                justify-content: center;
            }
            nav {
                justify-content: center;
            }
            .hero h1 {
                font-size: 34px;
            }
            .hero .sub {
                font-size: 12px;
                letter-spacing: 4px;
            }
            .grid {
                grid-template-columns: 1fr;
            }
            .pentagram-icon {
                width: 36px;
                height: 36px;
            }
            .logo-text {
                font-size: 20px;
            }
            .popup {
                padding: 30px 20px;
                margin: 0 20px;
            }
        }

        @media (max-width: 400px) {
            .hero h1 {
                font-size: 26px;
            }
            nav a {
                font-size: 12px;
                padding: 6px 12px;
            }
        }
    </style>
</head>
<body>

    <!-- ===== ШАПКА ===== -->
    <header>
        <a href="#" class="logo">
            <svg class="pentagram-icon" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
                <circle cx="50" cy="50" r="44" fill="none" stroke="rgba(200,30,40,0.2)" stroke-width="1.5"/>
                <circle cx="50" cy="50" r="36" fill="none" stroke="rgba(200,30,40,0.1)" stroke-width="1"/>
                <polygon points="
                    50,6 
                    63,34 
                    94,34 
                    70,54 
                    80,84 
                    50,66 
                    20,84 
                    30,54 
                    6,34 
                    37,34
                " fill="rgba(200,30,40,0.08)" stroke="#ff2233" stroke-width="2.5" stroke-linejoin="round"/>
                <polygon points="
                    50,94 
                    37,66 
                    6,66 
                    30,46 
                    20,16 
                    50,34 
                    80,16 
                    70,46 
                    94,66 
                    63,66
                " fill="none" stroke="rgba(200,30,40,0.15)" stroke-width="1.2" stroke-dasharray="2 4"/>
                <circle cx="50" cy="50" r="3" fill="rgba(255,30,40,0.5)" stroke="#ff2233" stroke-width="1"/>
                <circle cx="28" cy="28" r="1.5" fill="rgba(200,30,40,0.3)"/>
                <circle cx="72" cy="28" r="1.5" fill="rgba(200,30,40,0.3)"/>
                <circle cx="50" cy="80" r="1.5" fill="rgba(200,30,40,0.3)"/>
            </svg>

            <span class="logo-text">
                <span class="tainted">Tainted</span>
                <span class="dead">Dead</span>
                <span class="god">God</span>
            </span>
        </a>

        <nav>
            <a href="#" class="active" data-page="home"><i class="fas fa-home"></i> Главная</a>
            <a href="#" class="locked" data-page="history"><i class="fas fa-lock"></i> История</a>
            <a href="#" class="locked" data-page="mods"><i class="fas fa-lock"></i> Моды</a>
            <a href="#" class="locked" data-page="secrets"><i class="fas fa-lock"></i> Секреты</a>
        </nav>
    </header>

    <!-- ===== ПОПАП ===== -->
    <div class="popup-overlay" id="popup">
        <div class="popup">
            <div class="lock-icon"><i class="fas fa-lock"></i></div>
            <h2>В разработке</h2>
            <p>Этот раздел пока закрыт. Скоро всё будет!</p>
            <button class="close-btn" id="closePopup">Понял</button>
        </div>
    </div>

    <!-- ===== ОСНОВНОЙ КОНТЕНТ ===== -->
    <main class="container">

        <!-- ГЕРОЙ -->
        <section class="hero">
            <h1>
                <span class="tainted-h">Tainted</span>
                <span class="dead-h">Dead</span>
                <span class="god-h">God</span>
            </h1>
            <div class="sub">✦ КРОВАВЫЙ ПУТЬ К АБСОЛЮТУ ✦</div>
            <p>
                Всё, что нужно знать о <strong>The Binding of Isaac</strong>: 
                лор, секреты, моды и достижение Dead God.
            </p>
        </section>

        <!-- КАРТОЧКИ -->
        <div class="grid">
            <div class="card">
                <span class="icon"><i class="fas fa-scroll"></i></span>
                <h3>История и лор</h3>
                <p>
                    Все концовки, теории происхождения Айзека, 
                    скрытые смыслы и хронология событий.
                </p>
                <a class="link" data-locked="true">Читать →</a>
            </div>

            <div class="card">
                <span class="icon"><i class="fas fa-tools"></i></span>
                <h3>Модификации</h3>
                <p>
                    ТОП-10 модов, гайды по установке, 
                    как создать свой предмет или персонажа.
                </p>
                <a class="link" data-locked="true">Изучить →</a>
            </div>

            <div class="card">
                <span class="icon"><i class="fas fa-question"></i></span>
                <h3>Секреты</h3>
                <p>
                    Тайные комнаты, символы, пасхалки, 
                    как открыть Tainted-персонажей и получить Dead God.
                </p>
                <a class="link" data-locked="true">Раскрыть →</a>
            </div>
        </div>

    </main>

    <!-- ===== ФУТЕР ===== -->
    <footer>
        <p>
            <i class="fas fa-skull"></i> Рофл на рофле · 
            <span>⛧</span> 2026 <strong>Tainted Dead God</strong> · 
            <i class="fas fa-heart" style="color:#ff3344;"></i>
        </p>
    </footer>

    <!-- ===== СКРИПТ ===== -->
    <script>
        const popup = document.getElementById('popup');
        const closeBtn = document.getElementById('closePopup');

        function showPopup() {
            popup.classList.add('active');
        }

        function hidePopup() {
            popup.classList.remove('active');
        }

        // Закрытие по кнопке
        closeBtn.addEventListener('click', hidePopup);

        // Закрытие по клику на фон
        popup.addEventListener('click', function(e) {
            if (e.target === this) hidePopup();
        });

        // Закрытие по ESC
        document.addEventListener('keydown', function(e) {
            if (e.key === 'Escape') hidePopup();
        });

        // ===== ВСЕ ЗАКРЫТЫЕ ВКЛАДКИ =====
        document.querySelectorAll('nav a.locked').forEach(link => {
            link.addEventListener('click', function(e) {
                e.preventDefault();
                showPopup();
            });
        });

        // ===== КАРТОЧКИ (тоже показывают попап) =====
        document.querySelectorAll('.card .link[data-locked="true"]').forEach(link => {
            link.addEventListener('click', function(e) {
                e.preventDefault();
                showPopup();
            });
        });

        // Главная вкладка — просто заглушка (ничего не делает)
        document.querySelector('nav a.active')?.addEventListener('click', function(e) {
            e.preventDefault();
            // Можно оставить пустым или добавить скролл к верху
            window.scrollTo({ top: 0, behavior: 'smooth' });
        });
    </script>

</body>
</html>
