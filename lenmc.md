<!DOCTYPE html>
<html lang="pl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>LenMc.pl - BoxPvP</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600;700;900&family=Bebas+Neue&display=swap" rel="stylesheet">

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Montserrat', sans-serif;
      overflow-x: hidden;
      background: #f5c400;
      color: white;
      min-height: 100vh;
      position: relative;
    }

    body::before {
      content: "";
      position: fixed;
      inset: 0;
      background:
        linear-gradient(rgba(0,0,0,0.72), rgba(0,0,0,0.8)),
        url('https://images.unsplash.com/photo-1606144042614-b2417e99c4e3?q=80&w=2070&auto=format&fit=crop');
      background-size: cover;
      background-position: center;
      z-index: -3;
      filter: saturate(1.2);
    }

    .particles {
      position: fixed;
      inset: 0;
      overflow: hidden;
      z-index: -2;
    }

    .particle {
      position: absolute;
      width: 8px;
      height: 8px;
      background: rgba(255,255,255,0.5);
      border-radius: 50%;
      animation: float 10s linear infinite;
    }

    @keyframes float {
      from {
        transform: translateY(100vh) scale(0);
        opacity: 0;
      }
      20% {
        opacity: 1;
      }
      to {
        transform: translateY(-10vh) scale(1.3);
        opacity: 0;
      }
    }

    header {
      width: 100%;
      position: fixed;
      top: 0;
      left: 0;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 20px 40px;
      z-index: 100;
      backdrop-filter: blur(10px);
      background: rgba(0,0,0,0.2);
      border-bottom: 1px solid rgba(255,255,255,0.1);
    }

    .logo {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .logo img {
      width: 65px;
      height: 65px;
      border-radius: 16px;
      object-fit: cover;
      border: 3px solid #ffd900;
      box-shadow: 0 0 25px rgba(255,217,0,0.7);
    }

    .logo span {
      font-size: 28px;
      font-weight: 900;
      color: white;
      letter-spacing: 2px;
      text-shadow: 0 0 10px rgba(255,255,255,0.5);
    }

    nav {
      display: flex;
      gap: 20px;
    }

    nav button {
      background: white;
      color: black;
      border: none;
      padding: 14px 30px;
      border-radius: 14px;
      font-weight: 700;
      font-size: 16px;
      cursor: pointer;
      transition: 0.35s ease;
      position: relative;
      overflow: hidden;
    }

    nav button::before {
      content: "";
      position: absolute;
      inset: 0;
      background: linear-gradient(90deg, transparent, rgba(255,255,255,0.7), transparent);
      transform: translateX(-100%);
    }

    nav button:hover::before {
      animation: shine 1s ease;
    }

    @keyframes shine {
      100% {
        transform: translateX(100%);
      }
    }

    nav button:hover {
      transform: translateY(-4px) scale(1.05);
      box-shadow: 0 10px 30px rgba(255,255,255,0.4);
      background: #fff8cf;
    }

    .hero {
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      text-align: center;
      padding: 120px 20px 60px;
      position: relative;
    }

    .wave-title {
      font-size: clamp(70px, 16vw, 200px);
      font-family: 'Bebas Neue', sans-serif;
      color: white;
      letter-spacing: 12px;
      position: relative;
      animation: wave 3s ease-in-out infinite;
      text-shadow:
        0 0 15px rgba(255,255,255,0.7),
        0 0 30px rgba(255,217,0,0.8),
        0 0 50px rgba(255,255,255,0.4);
      border: 6px solid white;
      padding: 20px 50px;
      border-radius: 35px;
      backdrop-filter: blur(10px);
      background: rgba(255,255,255,0.08);
      cursor: pointer;
      transition: 0.4s ease;
    }

    .wave-title:hover {
      transform: scale(1.05);
      box-shadow: 0 0 40px rgba(255,255,255,0.5);
    }

    @keyframes wave {
      0%,100% {
        transform: translateY(0px) rotate(-1deg);
      }
      50% {
        transform: translateY(-10px) rotate(1deg);
      }
    }

    .subtext {
      margin-top: 20px;
      font-size: 20px;
      color: #fff2a6;
      font-weight: 600;
      letter-spacing: 2px;
    }

    .menu-box {
      margin-top: 45px;
      display: flex;
      gap: 25px;
      opacity: 0;
      transform: translateY(40px);
      pointer-events: none;
      transition: 0.7s ease;
      flex-wrap: wrap;
      justify-content: center;
    }

    .menu-box.active {
      opacity: 1;
      transform: translateY(0);
      pointer-events: all;
    }

    .menu-card {
      width: 260px;
      padding: 30px;
      border-radius: 24px;
      background: rgba(255,255,255,0.12);
      backdrop-filter: blur(14px);
      border: 2px solid rgba(255,255,255,0.25);
      transition: 0.4s ease;
      cursor: pointer;
      box-shadow: 0 10px 30px rgba(0,0,0,0.3);
    }

    .menu-card:hover {
      transform: translateY(-10px) scale(1.04);
      border-color: #ffe14d;
      box-shadow: 0 0 30px rgba(255,217,0,0.6);
    }

    .menu-card h3 {
      font-size: 28px;
      margin-bottom: 12px;
    }

    .menu-card p {
      color: #f2f2f2;
      line-height: 1.5;
    }

    .panel {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%) scale(0.8);
      width: min(900px, 92%);
      max-height: 85vh;
      overflow-y: auto;
      background: rgba(0,0,0,0.88);
      border: 4px solid #ffd900;
      border-radius: 30px;
      padding: 35px;
      z-index: 999;
      opacity: 0;
      pointer-events: none;
      transition: 0.45s ease;
      backdrop-filter: blur(14px);
      box-shadow: 0 0 50px rgba(255,217,0,0.5);
    }

    .panel.active {
      opacity: 1;
      pointer-events: all;
      transform: translate(-50%, -50%) scale(1);
    }

    .panel h2 {
      font-size: 42px;
      margin-bottom: 25px;
      color: #ffd900;
      text-align: center;
      text-shadow: 0 0 15px rgba(255,217,0,0.6);
    }

    .rules-box {
      background: rgba(255,217,0,0.1);
      border: 2px solid #ffd900;
      border-radius: 20px;
      padding: 25px;
      line-height: 1.9;
      font-size: 16px;
      white-space: pre-line;
    }

    .discord-box {
      text-align: center;
      padding: 30px;
      background: rgba(255,255,255,0.08);
      border-radius: 24px;
      border: 2px solid white;
    }

    .discord-box p {
      font-size: 22px;
      margin-bottom: 25px;
    }

    .discord-btn,
    .ip-btn,
    .close-btn {
      border: none;
      cursor: pointer;
      transition: 0.35s ease;
      font-weight: 700;
    }

    .discord-btn,
    .ip-btn {
      background: white;
      color: black;
      padding: 16px 35px;
      border-radius: 16px;
      font-size: 18px;
      display: inline-block;
      text-decoration: none;
      margin-top: 10px;
    }

    .discord-btn:hover,
    .ip-btn:hover {
      transform: scale(1.06);
      background: #ffe14d;
      box-shadow: 0 0 30px rgba(255,217,0,0.5);
    }

    .ip-section {
      margin-top: 35px;
      text-align: center;
    }

    .ip-info {
      margin-top: 10px;
      color: #fff1a8;
      font-size: 14px;
      letter-spacing: 1px;
    }

    .close-btn {
      position: absolute;
      top: 18px;
      right: 18px;
      width: 45px;
      height: 45px;
      border-radius: 50%;
      background: white;
      color: black;
      font-size: 20px;
    }

    .close-btn:hover {
      transform: rotate(180deg) scale(1.1);
      background: #ffd900;
    }

    footer {
      width: 100%;
      text-align: center;
      padding: 25px;
      background: rgba(0,0,0,0.5);
      backdrop-filter: blur(10px);
      border-top: 1px solid rgba(255,255,255,0.15);
      color: #fff0a1;
      font-weight: 600;
      letter-spacing: 1px;
    }

    ::-webkit-scrollbar {
      width: 10px;
    }

    ::-webkit-scrollbar-thumb {
      background: #ffd900;
      border-radius: 20px;
    }

    @media (max-width: 768px) {
      header {
        padding: 15px 20px;
      }

      .logo span {
        display: none;
      }

      nav button {
        padding: 12px 18px;
        font-size: 14px;
      }

      .wave-title {
        padding: 18px 24px;
        letter-spacing: 6px;
      }

      .panel {
        padding: 22px;
      }

      .panel h2 {
        font-size: 30px;
      }
    }
  </style>
</head>
<body>

  <div class="particles" id="particles"></div>

  <header>
    <div class="logo">
      <img src="Zrzut_ekranu_2026-05-13_170959.png" alt="Logo LenMc">
      <span>LENMC.PL</span>
    </div>

    <nav>
      <button onclick="openPanel('rulesPanel')">Regulamin</button>
      <button onclick="openPanel('discordPanel')">Server DC</button>
    </nav>
  </header>

  <section class="hero">
    <div class="wave-title" onclick="toggleMenu()">
      WIĘCEJ
    </div>

    <p class="subtext">Najlepszy klimat BoxPvP • LenMc.pl</p>

    <div class="menu-box" id="menuBox">
      <div class="menu-card" onclick="openPanel('rulesPanel')">
        <h3>📜 Regulamin</h3>
        <p>Sprawdź wszystkie zasady obowiązujące na serwerze LenMc.</p>
      </div>

      <div class="menu-card" onclick="openPanel('discordPanel')">
        <h3>💬 Server DC</h3>
        <p>Dołącz do społeczności Discord i graj razem z ekipą.</p>
      </div>

      <div class="menu-card">
        <h3>⚔️ BoxPvP</h3>
        <p>Dynamiczna rozgrywka, epickie walki i najlepszy serwer PvP.</p>
      </div>
    </div>

    <div class="ip-section">
      <button class="ip-btn" onclick="copyIP()">LenMc.pl</button>
      <div class="ip-info">Kliknij aby skopiować IP</div>
    </div>
  </section>

  <div class="panel" id="rulesPanel">
    <button class="close-btn" onclick="closePanels()">✕</button>
    <h2>Regulamin servera LenMc</h2>

    <div class="rules-box">
§1. Postanowienia ogólne
1.1. Korzystając z trybu, gracz akceptuje poniższy regulamin
1.2. Administracja zastrzega sobie prawo do modyfikacji regulaminu w dowolnym momencie
1.3. Nieznajomość regulaminu nie zwalnia z odpowiedzialności

§2. Zasady ogólne trybu BoxPvP
2.1. Zabrania się używania cheatów, modów lub zewnętrznych narzędzi
2.2. Wszelkie formy toksyczności, czy mowy nienawiści są zabronione
2.3. Zakaz wykorzystywania błędów mechanik serwera, które nie zostały wcześniej zgłoszone. Każdy błąd powinien zostać zgłoszony administracji
2.4. Zakazuje się podszywania pod innych graczy i administrację
2.5. Handel przedmiotami i kontami za realną walutę jest zakazane
2.6. Zabroniona jest współpraca z cheaterem (osobą, która używa niedozwolonych modyfikacji)

§3. Komunikacja
4.1. Używanie wulgaryzmów, obraźliwych tekstów czy spamu w czacie gry jest zakazane
4.2. Zakaz reklamy innych serwerów Minecraft
4.3. Wszelkie zgłoszenia błędów, cheaterów czy problemów z rozgrywką powinny być kierowane bezpośrednio do administracji TYLKO I WYŁĄCZNIE poprzez kanał głosowy, bądź kanał ⁠Brak dostępu

§4. Administracja
4.1. Wszelkie prośby o unbana/unmute powinny być kierowane do rang wyższych TYLKO I WYŁĄCZNIE na kanale ⁠
4.2. Administracja nie ponosi odpowiedzialności za utracone przedmioty w grze, wynikające z śmierci, błędów gry czy innych zdarzeń

§5. Kary
5.1. Wysokość kary zależy od decyzji administracji i może się różnić w zależności od sytuacji
5.2. Powtarzające się wykroczenia mogą skutkować zaostrzeniem kary

§6. Postanowienia końcowe
6.1. Gra na serwerze jest równoznaczna z akceptacją regulaminu
6.2. Wszelkie pytania dotyczące regulaminu należy kierować do administracji
6.3. Regulamin wchodzi w życie z dniem publikacji na serwerze
    </div>
  </div>

  <div class="panel" id="discordPanel">
    <button class="close-btn" onclick="closePanels()">✕</button>
    <h2>Server Discord</h2>

    <div class="discord-box">
      <p>Kliknij aby przejść na discord servera</p>

      <a href="https://discord.gg/48zJUStp" target="_blank" class="discord-btn">
        Dołącz na Discord
      </a>
    </div>
  </div>

  <footer>
    alifeste - LenMc.pl
  </footer>

  <script>
    const menuBox = document.getElementById('menuBox');

    function toggleMenu() {
      menuBox.classList.toggle('active');
    }

    function openPanel(id) {
      closePanels();
      document.getElementById(id).classList.add('active');
    }

    function closePanels() {
      document.querySelectorAll('.panel').forEach(panel => {
        panel.classList.remove('active');
      });
    }

    function copyIP() {
      navigator.clipboard.writeText('LenMc.pl');
      const info = document.querySelector('.ip-info');
      info.innerText = 'IP zostało skopiowane!';

      setTimeout(() => {
        info.innerText = 'Kliknij aby skopiować IP';
      }, 2500);
    }

    window.addEventListener('click', (e) => {
      document.querySelectorAll('.panel').forEach(panel => {
        if (e.target === panel) {
          panel.classList.remove('active');
        }
      });
    });

    const particles = document.getElementById('particles');

    for (let i = 0; i < 45; i++) {
      const particle = document.createElement('div');
      particle.classList.add('particle');

      particle.style.left = Math.random() * 100 + 'vw';
      particle.style.animationDuration = (Math.random() * 8 + 6) + 's';
      particle.style.animationDelay = Math.random() * 5 + 's';
      particle.style.opacity = Math.random();

      particles.appendChild(particle);
    }
  </script>
</body>
</html>
