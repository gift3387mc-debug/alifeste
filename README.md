[indexx.html.html](https://github.com/user-attachments/files/27778565/indexx.html.html)
<!DOCTYPE html>
<html lang="pl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>LenMC.pl</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Poppins', sans-serif;
    }

    body {
      background: #ffffff;
      color: #111;
      overflow-x: hidden;
    }

    .top-bar {
      width: 100%;
      height: 8px;
      background: #ffd000;
    }

    header {
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      text-align: center;
      padding: 20px;
      background: linear-gradient(to bottom, #ffffff 0%, #fff8d6 100%);
    }

    .logo {
      font-size: 80px;
      font-weight: 700;
      color: #111;
      margin-bottom: 15px;
    }

    .subtitle {
      font-size: 20px;
      color: #444;
      max-width: 700px;
      margin-bottom: 40px;
    }

    .ip-box {
      background: white;
      border: 2px solid #ffd000;
      padding: 18px 40px;
      border-radius: 18px;
      cursor: pointer;
      transition: 0.3s;
      box-shadow: 0 10px 30px rgba(0,0,0,0.08);
      margin-bottom: 20px;
    }

    .ip-box:hover {
      transform: translateY(-5px);
      background: #fff9df;
    }

    .ip-title {
      font-size: 28px;
      font-weight: 700;
    }

    .ip-desc {
      font-size: 14px;
      color: #666;
      margin-top: 5px;
    }

    .copy-message {
      position: fixed;
      bottom: 30px;
      right: 30px;
      background: #111;
      color: white;
      padding: 14px 22px;
      border-radius: 12px;
      opacity: 0;
      pointer-events: none;
      transition: 0.3s;
      z-index: 999;
    }

    .copy-message.show {
      opacity: 1;
    }

    .more-btn {
      margin-top: 25px;
      padding: 15px 45px;
      background: #ffd000;
      color: #111;
      border: none;
      border-radius: 14px;
      font-size: 18px;
      font-weight: 600;
      cursor: pointer;
      transition: 0.3s;
      box-shadow: 0 10px 25px rgba(255,208,0,0.4);
    }

    .more-btn:hover {
      transform: scale(1.05);
    }

    .menu {
      display: none;
      margin-top: 25px;
      flex-direction: column;
      gap: 15px;
      width: 260px;
    }

    .menu a {
      text-decoration: none;
      background: white;
      color: #111;
      padding: 15px;
      border-radius: 14px;
      font-weight: 600;
      border: 2px solid #ffd000;
      transition: 0.3s;
      box-shadow: 0 10px 25px rgba(0,0,0,0.05);
    }

    .menu a:hover {
      background: #ffd000;
      transform: translateY(-3px);
    }

    section {
      padding: 100px 20px;
    }

    .section-title {
      text-align: center;
      font-size: 42px;
      margin-bottom: 15px;
      font-weight: 700;
    }

    .section-subtitle {
      text-align: center;
      color: #555;
      margin-bottom: 60px;
      font-size: 18px;
    }

    .rekrutacje-grid {
      max-width: 1200px;
      margin: auto;
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 30px;
    }

    .card {
      background: white;
      border-radius: 24px;
      padding: 35px;
      box-shadow: 0 15px 40px rgba(0,0,0,0.08);
      border: 2px solid #ffe167;
      transition: 0.3s;
    }

    .card:hover {
      transform: translateY(-8px);
    }

    .card h3 {
      font-size: 32px;
      margin-bottom: 15px;
    }

    .card ul {
      margin-top: 20px;
      padding-left: 20px;
      color: #444;
      line-height: 1.9;
    }

    .apply-btn {
      display: inline-block;
      margin-top: 25px;
      padding: 14px 28px;
      background: #ffd000;
      color: #111;
      border-radius: 12px;
      text-decoration: none;
      font-weight: 700;
      transition: 0.3s;
    }

    .apply-btn:hover {
      transform: scale(1.05);
    }

    .rules {
      max-width: 1100px;
      margin: auto;
      background: white;
      border-radius: 24px;
      padding: 40px;
      box-shadow: 0 15px 40px rgba(0,0,0,0.08);
      line-height: 2;
      white-space: pre-line;
      border: 2px solid #ffe167;
    }

    footer {
      background: #ffd000;
      text-align: center;
      padding: 25px;
      font-weight: 600;
      font-size: 17px;
    }

    html {
      scroll-behavior: smooth;
    }

    @media(max-width: 768px) {
      .logo {
        font-size: 52px;
      }

      .subtitle {
        font-size: 17px;
      }

      .section-title {
        font-size: 32px;
      }
    }
  </style>
</head>
<body>

  <div class="top-bar"></div>

  <header>
    <div class="logo">LENMC.PL</div>
    <div class="subtitle">
      Najlepszy serwer Minecraft w Polsce. Dołącz do społeczności LenMC i rozpocznij swoją przygodę już teraz!
    </div>

    <div class="ip-box" onclick="copyIP()">
      <div class="ip-title">lenmc.pl</div>
      <div class="ip-desc">Kliknij aby skopiować IP</div>
    </div>

    <button class="more-btn" onclick="toggleMenu()">Więcej</button>

    <div class="menu" id="menu">
      <a href="#rekrutacja">Rekrutacja</a>
      <a href="#regulamin">Regulamin</a>
      <button onclick="window.open('https://discord.gg/48zJUStp', '_blank')" style="text-decoration: none; background: white; color: #111; padding: 15px; border-radius: 14px; font-weight: 600; border: 2px solid #ffd000; transition: 0.3s; box-shadow: 0 10px 25px rgba(0,0,0,0.05); cursor:pointer;">Discord</button>
    </div>
  </header>

  <section id="rekrutacja">
    <h2 class="section-title">Rekrutacja</h2>
    <p class="section-subtitle">
      Spróbuj swoich sił w rekrutacji i zostań pomocnikiem na najlepszym serwerze minecraft w Polsce!
    </p>

    <div class="rekrutacje-grid">

      <div class="card">
        <h3>ChatMod</h3>
        <ul>
          <li>Ukończone 13 lat</li>
          <li>Znajomość regulaminu serwera</li>
          <li>Znajomość ortografii i interpunkcji</li>
          <li>Posiadanie sprawnego mikrofonu</li>
        </ul>

        <button class="apply-btn" onclick="window.open('https://docs.google.com/forms/d/e/1FAIpQLSc4uTqb2ujWZjl8MVit8SwVXUYrRZby90BMaar0lw-sUfhXkw/viewform?usp=dialog', '_blank')">
          Aplikuj
        </button>
      </div>

      <div class="card">
        <h3>Helper</h3>
        <ul>
          <li>Ukończone 13 lat</li>
          <li>Znajomość regulaminu serwera</li>
          <li>Znajomość ortografii i interpunkcji</li>
          <li>Posiadanie sprawnego mikrofonu</li>
          <li>Możliwość nagrywania ekranu w dobrej jakości</li>
          <li>Brak ostatnio otrzymanych lub aktualnie trwających kar na koncie</li>
        </ul>

        <button class="apply-btn" onclick="window.open('https://docs.google.com/forms/d/e/1FAIpQLSf9sLV_VEbViZ-kgPA8GM5zZMl_kok2ZkDtsdgiCk-RYaq2Bg/viewform?usp=dialog', '_blank')">
          Aplikuj
        </button>
      </div>

      <div class="card">
        <h3>Developer</h3>
        <ul>
          <li>Ukończone 13 lat</li>
          <li>Umiejętność zrobienia pluginu/bota</li>
          <li>Posiadanie sprawnego mikrofonu</li>
          <li>Możliwość nagrywania ekranu w dobrej jakości</li>
          <li>Brak ostatnio otrzymanych lub aktualnie trwających kar na koncie</li>
        </ul>

        <button class="apply-btn" onclick="window.open('https://docs.google.com/forms/d/e/1FAIpQLSc3UgsKfxDIov-96GpVYvf4SpvHM3GCm-HyaH2D06wwhWg3pA/viewform?usp=dialog', '_blank')">
          Aplikuj
        </button>
      </div>

    </div>
  </section>

  <section id="regulamin">
    <h2 class="section-title">Regulamin</h2>

    <div class="rules">
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
2.6. Zabroniona jest współpraca z cheaterem

§3. Komunikacja
3.1. Używanie wulgaryzmów, obraźliwych tekstów czy spamu w czacie gry jest zakazane
3.2. Zakaz reklamy innych serwerów Minecraft
3.3. Wszelkie zgłoszenia błędów, cheaterów czy problemów z rozgrywką powinny być kierowane bezpośrednio do administracji

§4. Administracja
4.1. Wszelkie prośby o unbana/unmute powinny być kierowane do rang wyższych
4.2. Administracja nie ponosi odpowiedzialności za utracone przedmioty w grze

§5. Kary
5.1. Wysokość kary zależy od decyzji administracji i może się różnić w zależności od sytuacji
5.2. Powtarzające się wykroczenia mogą skutkować zaostrzeniem kary

§6. Postanowienia końcowe
6.1. Gra na serwerze jest równoznaczna z akceptacją regulaminu
6.2. Wszelkie pytania dotyczące regulaminu należy kierować do administracji
6.3. Regulamin wchodzi w życie z dniem publikacji na serwerze
    </div>
  </section>

  <footer>
    alifeste - lenmc.pl
  </footer>

  <div class="copy-message" id="copyMessage">
    Pomyślnie skopiowano IP
  </div>

  <script>
    function toggleMenu() {
      const menu = document.getElementById('menu');
      if(menu.style.display === 'flex') {
        menu.style.display = 'none';
      } else {
        menu.style.display = 'flex';
      }
    }

    function copyIP() {
      navigator.clipboard.writeText('LenMc.aternos.me');

      const message = document.getElementById('copyMessage');
      message.classList.add('show');

      setTimeout(() => {
        message.classList.remove('show');
      }, 2500);
    }
  </script>

</body>
</html>
