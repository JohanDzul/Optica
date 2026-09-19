<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Óptica geométrica: la física de cómo viaja la luz</title>
<meta name="description" content="Aprende óptica geométrica con ejemplos resueltos y simuladores: reflexión, ley de Snell, lentes, espejos, telescopio, fibra óptica, láser y tiempo de vuelo.">
<meta name="robots" content="index, follow">
<meta name="author" content="Johan Leander Dzul López, Clara de Asís Vazquez Martín, Mia Guadalupe Ortiz Pereira, Alberto Vidal Puch Salas, Jose Armando Uc Cardenas">
<meta property="og:type" content="website">
<meta property="og:locale" content="es_MX">
<meta property="og:title" content="Óptica geométrica: la física de cómo viaja la luz">
<meta property="og:description" content="Fórmulas, ejemplos resueltos y un laboratorio virtual con simuladores de Snell, lentes, fibra óptica y láser.">
<meta name="theme-color" content="#120E2E">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:opsz,wght@12..96,500;12..96,700;12..96,800&family=Figtree:wght@400;500;600&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#F6F4FF; --surface:#FFFFFF; --ink:#1D1846; --muted:#5B5687; --line:#DDD8F5;
  --accent:#5B3DF5; --accent-ink:#FFFFFF; --soft:#ECE8FF; --code:#F0EDFF;
  --ray-in:#E07B00; --ray-ref:#2F6FE4; --ray-rfr:#1E9E6E;
  --hero-bg:#120E2E; --hero-ink:#F1EEFF;
  --spec:linear-gradient(90deg,#E5484D,#F2994A,#F5D547,#3FB68B,#3B82F6,#7C4DFF);
  --display:'Bricolage Grotesque','Trebuchet MS','Segoe UI',system-ui,sans-serif;
  --body:'Figtree','Segoe UI',system-ui,-apple-system,Arial,sans-serif;
}
@media (prefers-color-scheme: dark){
  :root:not([data-theme="light"]){
    --bg:#120E2E; --surface:#1C1745; --ink:#F1EEFF; --muted:#B0AADB; --line:#332C6B;
    --accent:#9D8CFF; --accent-ink:#120E2E; --soft:#251F58; --code:#241E56;
    --ray-in:#FFB454; --ray-ref:#6FA3FF; --ray-rfr:#4FD6A0;
  }
}
:root[data-theme="dark"]{
  --bg:#120E2E; --surface:#1C1745; --ink:#F1EEFF; --muted:#B0AADB; --line:#332C6B;
  --accent:#9D8CFF; --accent-ink:#120E2E; --soft:#251F58; --code:#241E56;
  --ray-in:#FFB454; --ray-ref:#6FA3FF; --ray-rfr:#4FD6A0;
}
*{box-sizing:border-box}
html{scroll-behavior:smooth;scroll-padding-top:70px}
body{margin:0;background:var(--bg);color:var(--ink);font-family:var(--body);font-size:1.06rem;line-height:1.65}
img,svg{max-width:100%}
a{color:var(--accent)}
:focus-visible{outline:3px solid var(--accent);outline-offset:3px;border-radius:4px}
h1,h2,h3{font-family:var(--display);line-height:1.12;margin:0 0 .5em;letter-spacing:-.01em}
h2{font-size:clamp(1.9rem,4.5vw,2.8rem);font-weight:800}
h3{font-size:1.35rem;font-weight:700;margin-top:1.6em}
p{margin:0 0 1em;max-width:68ch}
.wrap{max-width:1080px;margin:0 auto;padding:0 20px}

/* Navegación */
nav{position:sticky;top:0;z-index:20;background:var(--hero-bg);border-bottom:3px solid transparent;border-image:var(--spec) 1}
nav .wrap{display:flex;align-items:center;gap:18px;padding-top:10px;padding-bottom:10px}
.brand{font-family:var(--display);font-weight:800;color:var(--hero-ink);text-decoration:none;white-space:nowrap;font-size:1.1rem}
.links{display:flex;gap:4px;overflow-x:auto;scrollbar-width:none;margin-left:auto}
.links::-webkit-scrollbar{display:none}
.links a{color:#CFC9FF;text-decoration:none;padding:6px 12px;border-radius:99px;white-space:nowrap;font-size:.95rem;font-weight:500}
.links a:hover{background:rgba(255,255,255,.12);color:#fff}

/* Portada */
.hero{background:radial-gradient(900px 500px at 78% 55%,#2A1F7A 0%,transparent 65%),radial-gradient(600px 400px at 5% 0%,#1D2B6B 0%,transparent 60%),var(--hero-bg);color:var(--hero-ink);padding:64px 0 56px;overflow:hidden}
.hero .wrap{display:grid;grid-template-columns:1.05fr .95fr;gap:32px;align-items:center}
.hero h1{font-size:clamp(2.3rem,6vw,4.2rem);font-weight:800;margin-bottom:.4em}
.hero p.lead{font-size:1.2rem;color:#D8D3FF;max-width:46ch}
.cta{display:flex;flex-wrap:wrap;gap:12px;margin:26px 0 30px}
.btn{display:inline-block;padding:12px 22px;border-radius:99px;font-weight:600;text-decoration:none;font-family:var(--body)}
.btn.main{background:#fff;color:#1D1846}
.btn.main:hover{background:#F5D547}
.btn.ghost{border:2px solid rgba(255,255,255,.4);color:#fff}
.btn.ghost:hover{border-color:#fff;background:rgba(255,255,255,.1)}
.authors-hero{border-top:1px solid rgba(255,255,255,.18);padding-top:16px}
.authors-hero b{display:block;font-family:var(--display);margin-bottom:8px;color:#fff}
.chips{display:flex;flex-wrap:wrap;gap:8px;list-style:none;margin:0;padding:0}
.chips li{background:rgba(255,255,255,.1);border:1px solid rgba(255,255,255,.2);padding:4px 12px;border-radius:99px;font-size:.92rem;color:#EDEAFF}
.prism{width:100%;height:auto}
.beam{stroke-dasharray:260;stroke-dashoffset:260;animation:draw 1.3s ease-out .3s forwards}
.fan{opacity:0;animation:show 1.2s ease-out 1.5s forwards}
@keyframes draw{to{stroke-dashoffset:0}}
@keyframes show{to{opacity:1}}
@media (prefers-reduced-motion: reduce){
  .beam{animation:none;stroke-dashoffset:0}.fan{animation:none;opacity:1}
  html{scroll-behavior:auto}
}

/* Secciones */
section{padding:72px 0}
section:nth-of-type(even){background:var(--surface)}
.sec-head{display:flex;flex-direction:column;margin-bottom:28px}
.sec-head .bar{width:88px;height:6px;border-radius:6px;background:var(--spec);margin-bottom:16px}
.sec-head p{color:var(--muted);font-size:1.12rem}
.two{display:grid;grid-template-columns:1fr 1fr;gap:34px;align-items:start}
.formula{font-family:Cambria,'Times New Roman',Georgia,serif;font-size:1.3rem;font-style:italic;background:var(--code);border-left:6px solid var(--accent);padding:14px 20px;margin:14px 0 18px;border-radius:0 12px 12px 0;overflow-x:auto}
.formula sub,.formula sup{font-size:.7em}
.frac{display:inline-flex;flex-direction:column;vertical-align:middle;text-align:center;margin:0 .25em;font-size:.95em}
.frac>span:first-child{border-bottom:1.5px solid currentColor;padding:0 .3em .06em}
.frac>span:last-child{padding:.06em .3em 0}
.fact{display:flex;gap:14px;align-items:flex-start;background:linear-gradient(135deg,rgba(245,213,71,.22),rgba(242,153,74,.16));border:1px solid rgba(242,153,74,.5);border-radius:16px;padding:16px 20px;margin:22px 0;max-width:72ch}
.fact svg{flex:none;width:34px;height:34px}
.fact p{margin:0}
table{border-collapse:collapse;width:100%;max-width:520px;margin:10px 0 22px;font-size:.98rem}
th,td{padding:8px 12px;text-align:left;border-bottom:1px solid var(--line)}
th{font-family:var(--display)}
.tblwrap{overflow-x:auto}
.example{background:var(--surface);border:1px solid var(--line);border-radius:16px;padding:6px 22px 14px;margin:20px 0}
section:nth-of-type(even) .example{background:var(--bg)}
.example summary{cursor:pointer;font-family:var(--display);font-weight:700;padding:14px 0;font-size:1.1rem}
.example ol{margin:0 0 6px;padding-left:1.3em}
.example li{margin:.35em 0}
.example .res{font-weight:600;background:var(--soft);padding:10px 14px;border-radius:10px;margin-top:10px}
.figure{background:var(--hero-bg);border-radius:20px;padding:14px;color:#fff}
.figure figcaption{font-size:.9rem;color:#CFC9FF;padding:8px 6px 2px}
.tags{display:flex;flex-wrap:wrap;gap:8px;margin:6px 0 14px;padding:0;list-style:none}
.tags li{background:var(--soft);padding:4px 12px;border-radius:99px;font-size:.92rem}

/* Laboratorio */
.lab{background:var(--surface);border:1px solid var(--line);border-radius:22px;padding:24px;margin:26px 0}
section:nth-of-type(even) .lab{background:var(--bg)}
.lab h3{margin-top:0}
.lab-grid{display:grid;grid-template-columns:minmax(0,1.25fr) minmax(0,1fr);gap:24px;align-items:start}
.controls{display:grid;gap:14px}
label{display:flex;flex-direction:column;gap:4px;font-weight:600;font-size:.96rem}
label output{font-weight:500;color:var(--accent)}
select,input[type=number]{font:inherit;padding:8px 10px;border-radius:10px;border:1.5px solid var(--line);background:var(--surface);color:var(--ink);width:100%}
input[type=range]{width:100%;accent-color:var(--accent)}
.stage{background:#120E2E;border-radius:16px;overflow:hidden}
.stage svg{display:block;width:100%;height:auto}
.readout{background:var(--soft);border-radius:14px;padding:14px 16px;font-size:1rem}
.readout p{margin:.2em 0;max-width:none}
.readout strong{font-family:var(--display)}
.legend{display:flex;flex-wrap:wrap;gap:14px;font-size:.9rem;margin-top:8px}
.legend i{display:inline-block;width:22px;height:4px;border-radius:4px;margin-right:6px;vertical-align:middle}
.badge{display:inline-block;padding:2px 10px;border-radius:99px;font-weight:600;font-size:.9rem}
.ok{background:rgba(30,158,110,.2);color:var(--ray-rfr)}
.warn{background:rgba(229,72,77,.18);color:#E5484D}

/* Referencias y equipo */
.refs{padding-left:0;list-style:none;counter-reset:r}
.refs li{counter-increment:r;padding:10px 0 10px 46px;position:relative;border-bottom:1px solid var(--line);max-width:80ch}
.refs li::before{content:"[" counter(r) "]";position:absolute;left:0;font-family:var(--display);font-weight:700;color:var(--accent)}
.team{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:18px;margin-top:10px}
.member{text-align:center;padding:10px}
.avatar{width:104px;height:104px;border-radius:50%;margin:0 auto 12px;display:grid;place-items:center;font-family:var(--display);font-weight:800;font-size:1.9rem;color:#fff;box-shadow:0 0 0 5px var(--bg),0 0 0 8px var(--c)}
section:nth-of-type(even) .avatar{box-shadow:0 0 0 5px var(--surface),0 0 0 8px var(--c)}
.member b{font-family:var(--display);font-size:1.08rem;display:block;line-height:1.25}
footer{background:var(--hero-bg);color:#CFC9FF;padding:34px 0;text-align:center;border-top:4px solid transparent;border-image:var(--spec) 1}
footer p{margin:.3em auto}

@media (max-width:820px){
  .hero .wrap,.two,.lab-grid{grid-template-columns:1fr}
  .hero{padding-top:40px}
  section{padding:52px 0}
  .brand{font-size:1rem}
}
.refs a{overflow-wrap:anywhere}
</style>
</head>
<body>

<nav aria-label="Navegación principal">
  <div class="wrap">
    <a class="brand" href="#inicio">Óptica en acción</a>
    <div class="links">
      <a href="#fundamentos">Fundamentos</a>
      <a href="#sistemas">Sistemas ópticos</a>
      <a href="#tecnologias">Tecnologías</a>
      <a href="#laboratorio">Laboratorio</a>
      <a href="#referencias">Referencias</a>
      <a href="#equipo">Equipo</a>
    </div>
  </div>
</nav>

<header class="hero" id="inicio">
  <div class="wrap">
    <div>
      <h1>Óptica geométrica: la física de cómo viaja la luz</h1>
      <p class="lead">Espejos, lentes, telescopios, fibra óptica y láser explicados con fórmulas, ejemplos resueltos y simuladores que puedes mover tú mismo.</p>
      <div class="cta">
        <a class="btn main" href="#fundamentos">Empezar a explorar</a>
        <a class="btn ghost" href="#laboratorio">Ir al laboratorio</a>
      </div>
      <div class="authors-hero">
        <b>Proyecto de Física realizado por:</b>
        <ul class="chips">
          <li>Johan Leander Dzul López</li>
          <li>Clara de Asís Vazquez Martín</li>
          <li>Mia Guadalupe Ortiz Pereira</li>
          <li>Alberto Vidal Puch Salas</li>
          <li>Jose Armando Uc Cardenas</li>
        </ul>
      </div>
    </div>

    <!-- Ilustración: un prisma separa la luz blanca en colores -->
    <svg class="prism" viewBox="0 0 520 420" role="img" aria-label="Un rayo de luz blanca entra a un prisma y sale separado en los colores del arcoíris">
      <defs>
        <linearGradient id="glass" x1="0" y1="0" x2="1" y2="1">
          <stop offset="0" stop-color="#ffffff" stop-opacity=".35"/>
          <stop offset="1" stop-color="#9D8CFF" stop-opacity=".15"/>
        </linearGradient>
        <filter id="glow" x="-20%" y="-20%" width="140%" height="140%"><feGaussianBlur stdDeviation="3"/></filter>
      </defs>
      <g fill="#fff" opacity=".7">
        <circle cx="40" cy="60" r="1.6"/><circle cx="120" cy="30" r="1.2"/><circle cx="470" cy="50" r="1.6"/>
        <circle cx="430" cy="130" r="1.2"/><circle cx="70" cy="370" r="1.4"/><circle cx="300" cy="30" r="1.2"/>
        <circle cx="490" cy="210" r="1.2"/><circle cx="200" cy="390" r="1.6"/>
      </g>
      <line class="beam" x1="10" y1="236" x2="216" y2="203" stroke="#fff" stroke-width="7" stroke-linecap="round" filter="url(#glow)" opacity=".8"/>
      <line class="beam" x1="10" y1="236" x2="216" y2="203" stroke="#fff" stroke-width="4" stroke-linecap="round"/>
      <polygon points="260,120 170,276 350,276" fill="url(#glass)" stroke="#E8E4FF" stroke-width="2.5" stroke-linejoin="round"/>
      <line x1="216" y1="203" x2="311" y2="208" stroke="#fff" stroke-width="3" opacity=".85"/>
      <g class="fan" stroke-width="4" stroke-linecap="round">
        <line x1="311" y1="208" x2="505" y2="272" stroke="#E5484D"/>
        <line x1="311" y1="208" x2="505" y2="288" stroke="#F2994A"/>
        <line x1="311" y1="208" x2="505" y2="304" stroke="#F5D547"/>
        <line x1="311" y1="208" x2="505" y2="320" stroke="#3FB68B"/>
        <line x1="311" y1="208" x2="505" y2="336" stroke="#3B82F6"/>
        <line x1="311" y1="208" x2="505" y2="352" stroke="#7C4DFF"/>
      </g>
    </svg>
  </div>
</header>

<main>

<!-- ============ 1. FUNDAMENTOS ============ -->
<section id="fundamentos">
  <div class="wrap">
    <div class="sec-head">
      <span class="bar"></span>
      <h2>Fundamentos y propagación de la luz</h2>
      <p>Antes de hablar de lentes y láseres necesitamos entender qué es la luz, cuánto corre y qué le pasa cuando cambia de medio.</p>
    </div>

    <div class="two">
      <div>
        <h3>¿Qué es la luz?</h3>
        <p>La luz visible es una onda electromagnética con longitudes de onda de unos 380 nm (violeta) a 750 nm (rojo). Se comporta como onda (se difracta e interfiere) y también como partícula (los fotones). En la <b>óptica geométrica</b> ignoramos su naturaleza ondulatoria y la representamos con <b>rayos</b>: líneas que indican hacia dónde viaja la energía [1].</p>

        <h3>Propagación rectilínea</h3>
        <p>En un medio homogéneo (mismo material en todos los puntos) y transparente, la luz viaja en línea recta. Por eso existen las sombras nítidas, los eclipses y la cámara oscura. Cuando la luz llega a otro medio, la trayectoria cambia: se refleja, se refracta o ambas cosas [1].</p>
      </div>
      <div>
        <h3>Velocidad de la luz</h3>
        <p>En el vacío, la luz viaja a <i>c</i> = 299 792 458 m/s (≈ 3 × 10<sup>8</sup> m/s). En un material es más lenta. El <b>índice de refracción</b> <i>n</i> mide cuánto:</p>
        <div class="formula"><i>n</i> = <span class="frac"><span><i>c</i></span><span><i>v</i></span></span> &nbsp;&nbsp;⇒&nbsp;&nbsp; <i>v</i> = <span class="frac"><span><i>c</i></span><span><i>n</i></span></span></div>
        <div class="tblwrap">
        <table>
          <thead><tr><th>Medio</th><th>n</th><th>v (m/s)</th></tr></thead>
          <tbody>
            <tr><td>Vacío</td><td>1.000</td><td>3.00 × 10<sup>8</sup></td></tr>
            <tr><td>Aire</td><td>1.0003</td><td>≈ 3.00 × 10<sup>8</sup></td></tr>
            <tr><td>Agua</td><td>1.33</td><td>2.25 × 10<sup>8</sup></td></tr>
            <tr><td>Vidrio común</td><td>1.50</td><td>2.00 × 10<sup>8</sup></td></tr>
            <tr><td>Diamante</td><td>2.42</td><td>1.24 × 10<sup>8</sup></td></tr>
          </tbody>
        </table>
        </div>
      </div>
    </div>

    <div class="fact" role="note">
      <svg viewBox="0 0 24 24" fill="none" stroke="#E07B00" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><circle cx="12" cy="12" r="4"/><path d="M12 2v3M12 19v3M2 12h3M19 12h3M4.9 4.9l2.1 2.1M17 17l2.1 2.1M4.9 19.1L7 17M17 7l2.1-2.1"/></svg>
      <p><b>Dato curioso:</b> la luz del Sol tarda unos 8 minutos y 20 segundos en llegar a la Tierra. Si el Sol se apagara ahora, lo veríamos brillar durante ese tiempo.</p>
    </div>

    <details class="example" open>
      <summary>Ejemplo 1: ¿cuánto tarda la luz del Sol en llegar a la Tierra?</summary>
      <ol>
        <li>Distancia Tierra–Sol: <i>d</i> ≈ 1.496 × 10<sup>11</sup> m.</li>
        <li>Como la luz viaja en línea recta a velocidad constante: <i>t</i> = <i>d</i> / <i>c</i>.</li>
        <li>Sustituimos: <i>t</i> = 1.496 × 10<sup>11</sup> m ÷ 2.998 × 10<sup>8</sup> m/s ≈ 499 s.</li>
      </ol>
      <div class="res">Resultado: 499 s ≈ 8.3 minutos.</div>
    </details>

    <details class="example">
      <summary>Ejemplo 2: velocidad de la luz en el agua</summary>
      <ol>
        <li>Índice de refracción del agua: <i>n</i> = 1.33.</li>
        <li>Usamos <i>v</i> = <i>c</i> / <i>n</i>.</li>
        <li><i>v</i> = 3.00 × 10<sup>8</sup> ÷ 1.33 ≈ 2.26 × 10<sup>8</sup> m/s.</li>
      </ol>
      <div class="res">Resultado: la luz va al 75 % de su velocidad en el vacío.</div>
    </details>

    <div class="two" style="margin-top:34px">
      <div>
        <h3>Ley de la reflexión</h3>
        <p>Cuando un rayo incide sobre una superficie lisa, el rayo reflejado sale con el mismo ángulo que el incidente. Los ángulos se miden respecto a la <b>normal</b> (la perpendicular a la superficie), y los tres —rayo incidente, reflejado y normal— están en el mismo plano.</p>
        <div class="formula">θ<sub>i</sub> = θ<sub>r</sub></div>
        <p>Si la superficie es rugosa, la reflexión es <b>difusa</b>: cada rayo cumple la ley, pero las normales apuntan en direcciones distintas. Así podemos ver los objetos desde cualquier ángulo.</p>
      </div>
      <div>
        <h3>Refracción y ley de Snell</h3>
        <p>Al pasar de un medio a otro, la luz cambia de velocidad y, si incide en ángulo, cambia de dirección. Snell describe cuánto:</p>
        <div class="formula"><i>n</i><sub>1</sub> sen θ<sub>1</sub> = <i>n</i><sub>2</sub> sen θ<sub>2</sub></div>
        <p>Si <i>n</i><sub>2</sub> &gt; <i>n</i><sub>1</sub>, el rayo se acerca a la normal (aire a vidrio). Si <i>n</i><sub>2</sub> &lt; <i>n</i><sub>1</sub>, se aleja (vidrio a aire). Es lo que hace que un lápiz parezca “quebrado” dentro de un vaso de agua.</p>
      </div>
    </div>

    <details class="example" open>
      <summary>Ejemplo 3: rayo que entra del aire al vidrio</summary>
      <ol>
        <li>Datos: <i>n</i><sub>1</sub> = 1.00 (aire), <i>n</i><sub>2</sub> = 1.50 (vidrio), θ<sub>1</sub> = 30°.</li>
        <li>Snell: sen θ<sub>2</sub> = (<i>n</i><sub>1</sub> sen θ<sub>1</sub>) / <i>n</i><sub>2</sub> = (1.00 × 0.500) / 1.50 = 0.333.</li>
        <li>θ<sub>2</sub> = arcsen(0.333) ≈ 19.5°.</li>
      </ol>
      <div class="res">Resultado: el rayo se dobla hacia la normal y sigue a 19.5°.</div>
    </details>

    <details class="example">
      <summary>Ejemplo 4: índice de refracción de un medio desconocido</summary>
      <ol>
        <li>Un rayo pasa del aire a un líquido con θ<sub>1</sub> = 45° y se refracta con θ<sub>2</sub> = 32°.</li>
        <li>Despejamos: <i>n</i><sub>2</sub> = <i>n</i><sub>1</sub> sen θ<sub>1</sub> / sen θ<sub>2</sub> = (1.00 × 0.707) / 0.530.</li>
        <li><i>n</i><sub>2</sub> ≈ 1.33.</li>
      </ol>
      <div class="res">Resultado: el líquido es compatible con agua (<i>n</i> = 1.33).</div>
    </details>

    <p>¿Quieres verlo en movimiento? En el <a href="#laboratorio">laboratorio virtual</a> puedes cambiar el ángulo y los materiales y ver cómo se mueven los rayos.</p>

    <div class="lab" id="lab-vel">
      <h3>Mini calculadora: velocidad de la luz en un material</h3>
      <div class="lab-grid" style="grid-template-columns:1fr 1fr">
        <div class="controls">
          <label for="vmat">Material
            <select id="vmat">
              <option value="1.0003">Aire (n = 1.0003)</option>
              <option value="1.33" selected>Agua (n = 1.33)</option>
              <option value="1.47">Fibra óptica, núcleo (n = 1.47)</option>
              <option value="1.50">Vidrio (n = 1.50)</option>
              <option value="2.42">Diamante (n = 2.42)</option>
            </select>
          </label>
        </div>
        <div class="readout" aria-live="polite" id="vout"></div>
      </div>
    </div>
  </div>
</section>

<!-- ============ 2. SISTEMAS ÓPTICOS ============ -->
<section id="sistemas">
  <div class="wrap">
    <div class="sec-head">
      <span class="bar"></span>
      <h2>Sistemas ópticos y dispositivos</h2>
      <p>Espejos y lentes controlan la luz para formar imágenes. Con ellos se construyen cámaras, microscopios y telescopios.</p>
    </div>

    <div class="two">
      <div>
        <h3>Espejos</h3>
        <p>Un espejo plano forma una imagen virtual, derecha y del mismo tamaño, a la misma distancia detrás del espejo. Un espejo esférico tiene radio de curvatura <i>R</i> y distancia focal:</p>
        <div class="formula"><i>f</i> = <span class="frac"><span><i>R</i></span><span>2</span></span></div>
        <p>El espejo <b>cóncavo</b> converge los rayos (linternas, telescopios reflectores). El <b>convexo</b> los diverge y da un campo de visión amplio (retrovisores) [1].</p>
      </div>
      <div>
        <h3>Lentes delgadas</h3>
        <p>La lente <b>convergente</b> (más gruesa al centro) hace que rayos paralelos se junten en el foco. La <b>divergente</b> (más delgada al centro) los separa. Ambas obedecen la ecuación gaussiana, igual que los espejos:</p>
        <div class="formula"><span class="frac"><span>1</span><span><i>f</i></span></span> = <span class="frac"><span>1</span><span><i>d</i><sub>o</sub></span></span> + <span class="frac"><span>1</span><span><i>d</i><sub>i</sub></span></span> &nbsp;&nbsp;&nbsp; <i>m</i> = − <span class="frac"><span><i>d</i><sub>i</sub></span><span><i>d</i><sub>o</sub></span></span></div>
        <p>La forma newtoniana usa distancias medidas desde los focos: <b><i>x</i> · <i>x</i>′ = <i>f</i><sup>2</sup></b>.</p>
      </div>
    </div>

    <h3>Trazado de rayos: tres rayos y ya tienes la imagen</h3>
    <p>Para ubicar la imagen de un punto basta dibujar dos o tres rayos “especiales”. Para una lente convergente:</p>
    <ol>
      <li>Un rayo paralelo al eje se refracta y pasa por el foco.</li>
      <li>Un rayo que pasa por el centro de la lente no se desvía.</li>
      <li>Un rayo que pasa por el foco de entrada sale paralelo al eje.</li>
    </ol>
    <p>Donde se cruzan los rayos está la imagen. Si nunca se cruzan, se prolongan hacia atrás y la imagen es virtual. Compruébalo en el <a href="#laboratorio">simulador de lentes</a>.</p>

    <p><b>Convención de signos usada en este sitio:</b> <i>d</i><sub>o</sub> es positiva; <i>f</i> es positiva en lentes convergentes y negativa en divergentes; <i>d</i><sub>i</sub> positiva indica imagen real (del lado opuesto al objeto) y negativa, imagen virtual.</p>

    <details class="example" open>
      <summary>Ejemplo 5: imagen de una lente convergente</summary>
      <ol>
        <li>Datos: <i>f</i> = 10 cm, <i>d</i><sub>o</sub> = 30 cm.</li>
        <li>1/<i>d</i><sub>i</sub> = 1/<i>f</i> − 1/<i>d</i><sub>o</sub> = 1/10 − 1/30 = 3/30 − 1/30 = 2/30.</li>
        <li><i>d</i><sub>i</sub> = 15 cm.</li>
        <li><i>m</i> = −<i>d</i><sub>i</sub>/<i>d</i><sub>o</sub> = −15/30 = −0.5.</li>
      </ol>
      <div class="res">Resultado: imagen real, invertida y a la mitad del tamaño, a 15 cm de la lente.</div>
    </details>

    <details class="example">
      <summary>Ejemplo 6: espejo cóncavo</summary>
      <ol>
        <li>Datos: <i>R</i> = 40 cm y objeto a <i>d</i><sub>o</sub> = 60 cm. Entonces <i>f</i> = <i>R</i>/2 = 20 cm.</li>
        <li>1/<i>d</i><sub>i</sub> = 1/20 − 1/60 = 3/60 − 1/60 = 2/60.</li>
        <li><i>d</i><sub>i</sub> = 30 cm y <i>m</i> = −30/60 = −0.5.</li>
      </ol>
      <div class="res">Resultado: imagen real e invertida, a 30 cm del espejo, de la mitad del tamaño.</div>
    </details>

    <h3>El telescopio</h3>
    <div class="two">
      <div>
        <p>Un telescopio junta la luz de objetos lejanos y la presenta más grande al ojo. El <b>refractor</b> (tipo Kepler) usa dos lentes convergentes: el <b>objetivo</b> (distancia focal grande) forma una imagen intermedia y el <b>ocular</b> (focal corta) la amplía. El <b>reflector</b> (tipo Newton) sustituye el objetivo por un espejo cóncavo, que es más fácil de fabricar en tamaños grandes [2].</p>
        <p>Cuando el telescopio está enfocado en objetos muy lejanos, el aumento angular es:</p>
        <div class="formula"><i>M</i> = − <span class="frac"><span><i>f</i><sub>o</sub></span><span><i>f</i><sub>e</sub></span></span></div>
        <p>El signo negativo indica que la imagen se ve invertida.</p>
      </div>
      <figure class="figure" style="margin:0">
        <svg viewBox="0 0 440 210" role="img" aria-label="Esquema de un telescopio refractor con objetivo y ocular">
          <line x1="10" y1="105" x2="430" y2="105" stroke="#5B5687" stroke-dasharray="4 4"/>
          <path d="M120 40 Q140 105 120 170 Q100 105 120 40Z" fill="#9D8CFF" fill-opacity=".45" stroke="#CFC9FF" stroke-width="2"/>
          <path d="M340 70 Q352 105 340 140 Q328 105 340 70Z" fill="#9D8CFF" fill-opacity=".45" stroke="#CFC9FF" stroke-width="2"/>
          <g stroke="#F5D547" stroke-width="2.2" fill="none">
            <line x1="10" y1="70" x2="120" y2="70"/><line x1="120" y1="70" x2="290" y2="105"/><line x1="290" y1="105" x2="340" y2="115"/>
            <line x1="10" y1="140" x2="120" y2="140"/><line x1="120" y1="140" x2="290" y2="105"/><line x1="290" y1="105" x2="340" y2="95"/>
          </g>
          <g stroke="#3FB68B" stroke-width="2.2"><line x1="340" y1="115" x2="430" y2="150"/><line x1="340" y1="95" x2="430" y2="60"/></g>
          <circle cx="290" cy="105" r="4" fill="#fff"/>
          <text x="120" y="195" fill="#E9E6FF" font-size="13" text-anchor="middle">Objetivo</text>
          <text x="340" y="165" fill="#E9E6FF" font-size="13" text-anchor="middle">Ocular</text>
          <text x="290" y="92" fill="#E9E6FF" font-size="12" text-anchor="middle">Imagen intermedia</text>
        </svg>
        <figcaption>Los rayos de un objeto lejano llegan casi paralelos. Salen paralelos otra vez, pero con mayor inclinación.</figcaption>
      </figure>
    </div>

    <details class="example" open>
      <summary>Ejemplo 7: aumento de un telescopio refractor</summary>
      <ol>
        <li>Datos: <i>f</i><sub>o</sub> = 1000 mm, <i>f</i><sub>e</sub> = 25 mm.</li>
        <li><i>M</i> = −<i>f</i><sub>o</sub>/<i>f</i><sub>e</sub> = −1000/25 = −40.</li>
        <li>Si cambiamos a un ocular de 10 mm: <i>M</i> = −1000/10 = −100.</li>
      </ol>
      <div class="res">Resultado: 40× con el ocular de 25 mm y 100× con el de 10 mm.</div>
    </details>
  </div>
</section>

<!-- ============ 3. TECNOLOGÍAS AVANZADAS ============ -->
<section id="tecnologias">
  <div class="wrap">
    <div class="sec-head">
      <span class="bar"></span>
      <h2>Tecnologías avanzadas: fibra óptica y láser</h2>
      <p>La misma ley de Snell que dobla un rayo en el agua sostiene el internet del mundo y los sensores que miden distancias con luz.</p>
    </div>

    <h3>Reflexión interna total</h3>
    <p>Si la luz va de un medio con mayor índice a uno con menor índice (<i>n</i><sub>1</sub> &gt; <i>n</i><sub>2</sub>), el rayo se aleja de la normal. Al aumentar el ángulo de incidencia llega un valor, el <b>ángulo crítico</b>, en que el rayo refractado sale rasante (90°). Con ángulos mayores no hay refracción: toda la luz se refleja. Eso es la <b>reflexión interna total</b> [1], [3].</p>
    <div class="formula">θ<sub>c</sub> = arcsen <span class="frac"><span><i>n</i><sub>2</sub></span><span><i>n</i><sub>1</sub></span></span> &nbsp;&nbsp;&nbsp;(<i>n</i><sub>1</sub> &gt; <i>n</i><sub>2</sub>)</div>

    <div class="two">
      <div>
        <h3>Fibra óptica</h3>
        <p>Una fibra tiene un <b>núcleo</b> de vidrio con índice <i>n</i><sub>1</sub> rodeado por un <b>revestimiento</b> con índice un poco menor, <i>n</i><sub>2</sub>. La luz entra por un extremo y rebota por reflexión interna total hasta salir por el otro, incluso si la fibra se curva.</p>
        <p>La <b>apertura numérica</b> indica el ángulo máximo de entrada, medido desde el aire, para que el rayo quede atrapado:</p>
        <div class="formula">AN = sen θ<sub>máx</sub> = √(<i>n</i><sub>1</sub><sup>2</sup> − <i>n</i><sub>2</sub><sup>2</sup>)</div>
      </div>
      <div>
        <h3>¿Por qué se usa en telecomunicaciones?</h3>
        <ul class="tags">
          <li>Muy alta capacidad de datos</li>
          <li>Baja atenuación en largas distancias</li>
          <li>Inmune a interferencia eléctrica</li>
          <li>Ligera y delgada</li>
        </ul>
        <p>Pulsos de luz infrarroja (típicamente 1310 nm y 1550 nm) representan los ceros y unos. Con esta técnica funcionan el internet doméstico, los cables submarinos entre continentes y las redes de las centrales telefónicas.</p>
      </div>
    </div>

    <details class="example" open>
      <summary>Ejemplo 8: ángulo crítico en una interfaz vidrio–aire</summary>
      <ol>
        <li>Datos: <i>n</i><sub>1</sub> = 1.50 (vidrio), <i>n</i><sub>2</sub> = 1.00 (aire).</li>
        <li>θ<sub>c</sub> = arcsen(<i>n</i><sub>2</sub>/<i>n</i><sub>1</sub>) = arcsen(1.00/1.50) = arcsen(0.667).</li>
      </ol>
      <div class="res">Resultado: θ<sub>c</sub> ≈ 41.8°. Con incidencia mayor, la luz no sale del vidrio.</div>
    </details>

    <details class="example">
      <summary>Ejemplo 9: fibra óptica con núcleo 1.48 y revestimiento 1.46</summary>
      <ol>
        <li>Ángulo crítico en la pared: θ<sub>c</sub> = arcsen(1.46/1.48) = arcsen(0.9865) ≈ 80.6°.</li>
        <li>Apertura numérica: AN = √(1.48<sup>2</sup> − 1.46<sup>2</sup>) = √(2.1904 − 2.1316) = √0.0588 ≈ 0.243.</li>
        <li>Ángulo máximo de aceptación: θ<sub>máx</sub> = arcsen(0.243) ≈ 14.0°.</li>
      </ol>
      <div class="res">Resultado: para quedar guiada, la luz debe entrar dentro de un cono de 14° respecto al eje.</div>
    </details>

    <h3>El láser</h3>
    <div class="two">
      <div>
        <p>LASER significa <i>Light Amplification by Stimulated Emission of Radiation</i>: amplificación de luz por emisión estimulada de radiación. Un átomo excitado puede liberar un fotón cuando otro fotón de la misma energía pasa cerca. El fotón nuevo sale idéntico al primero: misma frecuencia, fase y dirección [4], [5].</p>
        <p>Para lograr esto se necesitan tres ingredientes:</p>
        <ul>
          <li>Un <b>medio activo</b> (gas, cristal o semiconductor).</li>
          <li>Una fuente de <b>bombeo</b> de energía que provoque una <b>inversión de población</b> (más átomos excitados que en reposo).</li>
          <li>Una <b>cavidad resonante</b>, dos espejos entre los que la luz rebota y se amplifica; uno es parcialmente transparente y deja salir el haz.</li>
        </ul>
      </div>
      <div>
        <p>La luz láser es:</p>
        <ul class="tags">
          <li>Monocromática</li>
          <li>Coherente</li>
          <li>Muy direccional</li>
          <li>De alta intensidad</li>
        </ul>
        <p>Estas propiedades permiten enviar el haz muy lejos casi sin ensancharse, y por eso sirve para medir distancias.</p>
      </div>
    </div>

    <h3>Telemetría láser y tiempo de vuelo (ToF)</h3>
    <p>Un telémetro emite un pulso, espera su eco y mide el tiempo <i>t</i> que tardó en ir y volver. Como recorrió la distancia dos veces [6]:</p>
    <div class="formula"><i>d</i> = <span class="frac"><span><i>c</i> · <i>t</i></span><span>2</span></span></div>

    <details class="example" open>
      <summary>Ejemplo 10: tiempo de vuelo de un pulso láser</summary>
      <ol>
        <li>Un telémetro apunta a una pared a <i>d</i> = 150 m.</li>
        <li>El pulso recorre ida y vuelta: 2<i>d</i> = 300 m.</li>
        <li><i>t</i> = 2<i>d</i>/<i>c</i> = 300 ÷ (3 × 10<sup>8</sup>) = 1 × 10<sup>−6</sup> s.</li>
      </ol>
      <div class="res">Resultado: 1 µs. Cada nanosegundo de diferencia equivale a 15 cm de distancia, por eso los sensores ToF usan electrónica muy rápida.</div>
    </details>

    <h3>Optomecatrónica: donde la luz se une a las máquinas</h3>
    <p>La optomecatrónica combina óptica, mecánica y electrónica. Algunos ejemplos reales:</p>
    <ul>
      <li><b>Sensores LiDAR y ToF</b> en robots aspiradora, drones y vehículos autónomos: miden la distancia a los obstáculos [6].</li>
      <li><b>Encoders ópticos</b> que cuentan las vueltas de un motor con un haz y un disco ranurado.</li>
      <li><b>Corte y grabado láser</b> en máquinas CNC e impresión 3D [5].</li>
      <li><b>Alineación y metrología</b>: nivelación de maquinaria y medición de piezas con precisión micrométrica.</li>
    </ul>
    <div class="fact" role="note">
      <svg viewBox="0 0 24 24" fill="none" stroke="#E07B00" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><circle cx="12" cy="12" r="4"/><path d="M12 2v3M12 19v3M2 12h3M19 12h3M4.9 4.9l2.1 2.1M17 17l2.1 2.1M4.9 19.1L7 17M17 7l2.1-2.1"/></svg>
      <p><b>Dato curioso:</b> desde la Luna, un pulso láser dirigido a los reflectores dejados por las misiones Apolo tarda unos 2.5 segundos en ir y volver. Así se ha medido la distancia Tierra–Luna con precisión de milímetros.</p>
    </div>
  </div>
</section>

<!-- ============ 4. LABORATORIO ============ -->
<section id="laboratorio">
  <div class="wrap">
    <div class="sec-head">
      <span class="bar"></span>
      <h2>Laboratorio virtual</h2>
      <p>Mueve los controles y mira cómo cambian los rayos y los resultados. Los cálculos usan las mismas fórmulas de las secciones anteriores.</p>
    </div>

    <!-- Snell -->
    <div class="lab" id="lab-snell">
      <h3>1. Reflexión, refracción y ley de Snell</h3>
      <div class="lab-grid">
        <div>
          <div class="stage">
            <svg viewBox="0 0 400 300" role="img" aria-label="Simulación de un rayo incidente, uno reflejado y uno refractado en una interfaz">
              <rect x="0" y="0" width="400" height="150" fill="#2B2470"/>
              <rect x="0" y="150" width="400" height="150" fill="#4A3FA8" fill-opacity=".8"/>
              <line x1="0" y1="150" x2="400" y2="150" stroke="#CFC9FF" stroke-width="2"/>
              <line x1="200" y1="20" x2="200" y2="280" stroke="#CFC9FF" stroke-dasharray="6 6" stroke-width="1.5"/>
              <text x="10" y="24" fill="#E9E6FF" font-size="13" id="tn1">Medio 1</text>
              <text x="10" y="290" fill="#E9E6FF" font-size="13" id="tn2">Medio 2</text>
              <line id="rRef" x1="200" y1="150" x2="200" y2="20" stroke="#6FA3FF" stroke-width="4" stroke-linecap="round" opacity=".9"/>
              <line id="rRfr" x1="200" y1="150" x2="200" y2="280" stroke="#4FD6A0" stroke-width="4" stroke-linecap="round"/>
              <line id="rInc" x1="200" y1="150" x2="200" y2="20" stroke="#FFB454" stroke-width="4" stroke-linecap="round"/>
            </svg>
          </div>
          <div class="legend">
            <span><i style="background:#E07B00"></i>Incidente</span>
            <span><i style="background:#2F6FE4"></i>Reflejado</span>
            <span><i style="background:#1E9E6E"></i>Refractado</span>
          </div>
        </div>
        <div>
          <div class="controls">
            <label for="n1">Medio 1 (arriba)
              <select id="n1">
                <option value="1">Aire (1.00)</option>
                <option value="1.33">Agua (1.33)</option>
                <option value="1.5" selected>Vidrio (1.50)</option>
                <option value="2.42">Diamante (2.42)</option>
              </select>
            </label>
            <label for="n2">Medio 2 (abajo)
              <select id="n2">
                <option value="1" selected>Aire (1.00)</option>
                <option value="1.33">Agua (1.33)</option>
                <option value="1.5">Vidrio (1.50)</option>
                <option value="2.42">Diamante (2.42)</option>
              </select>
            </label>
            <label for="ang">Ángulo de incidencia <output id="angv">30°</output>
              <input type="range" id="ang" min="0" max="89" value="30">
            </label>
          </div>
          <div class="readout" id="snellOut" aria-live="polite" style="margin-top:14px"></div>
        </div>
      </div>
    </div>

    <!-- Lentes -->
    <div class="lab" id="lab-lens">
      <h3>2. Trazado de rayos en una lente delgada</h3>
      <div class="lab-grid">
        <div>
          <div class="stage">
            <svg viewBox="0 0 600 300" role="img" aria-label="Trazado de rayos en una lente delgada con objeto e imagen">
              <line x1="0" y1="150" x2="600" y2="150" stroke="#5B5687" stroke-width="1.5"/>
              <g id="lensDyn"></g>
            </svg>
          </div>
          <div class="legend">
            <span><i style="background:#FFB454"></i>Rayo paralelo al eje</span>
            <span><i style="background:#4FD6A0"></i>Rayo por el centro</span>
            <span>Línea punteada: prolongación (imagen virtual)</span>
          </div>
        </div>
        <div>
          <div class="controls">
            <label for="ltype">Tipo de lente
              <select id="ltype">
                <option value="conv" selected>Convergente</option>
                <option value="div">Divergente</option>
              </select>
            </label>
            <label for="lf">Distancia focal <output id="lfv">10 cm</output>
              <input type="range" id="lf" min="5" max="20" step="1" value="10">
            </label>
            <label for="ldo">Distancia del objeto <output id="ldov">30 cm</output>
              <input type="range" id="ldo" min="4" max="45" step="0.5" value="30">
            </label>
          </div>
          <div class="readout" id="lensOut" aria-live="polite" style="margin-top:14px"></div>
        </div>
      </div>
    </div>

    <!-- Fibra -->
    <div class="lab" id="lab-fiber">
      <h3>3. Fibra óptica: ¿el rayo se queda atrapado?</h3>
      <div class="lab-grid">
        <div>
          <div class="stage">
            <svg viewBox="0 0 600 200" role="img" aria-label="Rayo de luz dentro de una fibra óptica">
              <rect x="0" y="0" width="600" height="200" fill="#120E2E"/>
              <rect x="40" y="40" width="520" height="120" fill="#2B2470"/>
              <rect x="40" y="70" width="520" height="60" fill="#5B4BD1" fill-opacity=".75"/>
              <line x1="40" y1="70" x2="560" y2="70" stroke="#CFC9FF" stroke-width="1.2" stroke-dasharray="5 4"/>
              <line x1="40" y1="130" x2="560" y2="130" stroke="#CFC9FF" stroke-width="1.2" stroke-dasharray="5 4"/>
              <text x="48" y="58" fill="#E9E6FF" font-size="12">Revestimiento</text>
              <text x="48" y="106" fill="#E9E6FF" font-size="12" fill-opacity=".9">Núcleo</text>
              <polyline id="fAir" fill="none" stroke="#FFB454" stroke-width="3" stroke-linecap="round" points=""/>
              <polyline id="fRay" fill="none" stroke="#FFB454" stroke-width="3.5" stroke-linecap="round" stroke-linejoin="round" points=""/>
              <polyline id="fEsc" fill="none" stroke="#FF6B6B" stroke-width="3" stroke-linecap="round" points=""/>
            </svg>
          </div>
        </div>
        <div>
          <div class="controls">
            <label for="fcore">Índice del núcleo <output id="fcorev">1.48</output>
              <input type="range" id="fcore" min="1.40" max="1.60" step="0.01" value="1.48">
            </label>
            <label for="fclad">Índice del revestimiento <output id="fcladv">1.46</output>
              <input type="range" id="fclad" min="1.30" max="1.59" step="0.01" value="1.46">
            </label>
            <label for="fang">Ángulo de entrada (desde el aire) <output id="fangv">10°</output>
              <input type="range" id="fang" min="0" max="40" step="1" value="10">
            </label>
          </div>
          <div class="readout" id="fiberOut" aria-live="polite" style="margin-top:14px"></div>
        </div>
      </div>
    </div>

    <!-- ToF -->
    <div class="lab" id="lab-tof">
      <h3>4. Telémetro láser: tiempo de vuelo</h3>
      <div class="lab-grid" style="grid-template-columns:1fr 1fr">
        <div class="controls">
          <label for="tofd">Distancia al objeto (m)
            <input type="number" id="tofd" min="0" step="any" value="150">
          </label>
          <label for="toft">O ingresa el tiempo medido (ns)
            <input type="number" id="toft" min="0" step="any" value="1000">
          </label>
        </div>
        <div class="readout" id="tofOut" aria-live="polite"></div>
      </div>
    </div>
  </div>
</section>

<!-- ============ REFERENCIAS ============ -->
<section id="referencias">
  <div class="wrap">
    <div class="sec-head">
      <span class="bar"></span>
      <h2>Referencias</h2>
      <p>Fuentes en español, con enlace, en formato IEEE. Los números entre corchetes en el texto remiten a esta lista.</p>
    </div>
    <ol class="refs">
      <li>Universidad de Sonora, “Óptica: Tema 10, Óptica geométrica”, <i>Física II</i>, apuntes de curso, s. f. [En línea]. Disponible en: <a href="https://dcbs.fisica.uson.mx/archivos/fisica2/10-fisica_II.pdf" target="_blank" rel="noopener">https://dcbs.fisica.uson.mx/archivos/fisica2/10-fisica_II.pdf</a></li>
      <li>Fundación Descubre, “Telescopios: óptica”, <i>El Séptimo Cielo</i>, s. f. [En línea]. Disponible en: <a href="https://elseptimocielo.fundaciondescubre.es/disfruta-del-universo/astronomia-para-principiantes/telescopios-optica/" target="_blank" rel="noopener">https://elseptimocielo.fundaciondescubre.es/disfruta-del-universo/astronomia-para-principiantes/telescopios-optica/</a></li>
      <li>Universitat de València, “Demo 123. Fibra óptica”, <i>FISICADEMOS: Demostraciones experimentales de Física</i>, s. f. [En línea]. Disponible en: <a href="https://www.uv.es/uvweb/fisica/es/demostraciones-experimentales-fisica-aula/catalogo-demos/optica/fibra-optica-1286111789106/DemoExp.html?id=1286111064948" target="_blank" rel="noopener">https://www.uv.es/uvweb/fisica/es/demostraciones-experimentales-fisica-aula/catalogo-demos/optica/fibra-optica-1286111789106/DemoExp.html?id=1286111064948</a></li>
      <li>H. E. Ibarra Villalón, O. Pottiez y A. Gómez Vieyra, “El camino hacia la luz láser”, <i>Revista Mexicana de Física E</i>, vol. 64, n.º 2, pp. 100–107, dic. 2018. [En línea]. Disponible en: <a href="https://www.scielo.org.mx/scielo.php?script=sci_arttext&amp;pid=S1870-35422018000200100" target="_blank" rel="noopener">https://www.scielo.org.mx/scielo.php?script=sci_arttext&amp;pid=S1870-35422018000200100</a></li>
      <li>J. Esténoz Valenzuela, “Estudio sobre las aplicaciones industriales del láser”, Proyecto Fin de Carrera, Universidad de Zaragoza, Zaragoza, España, mar. 2011. [En línea]. Disponible en: <a href="https://zaguan.unizar.es/record/5646/files/TAZ-PFC-2011-098.pdf" target="_blank" rel="noopener">https://zaguan.unizar.es/record/5646/files/TAZ-PFC-2011-098.pdf</a></li>
      <li>L. A. Orta Méndez, “Telemetría láser”, Trabajo de Fin de Grado, Universidad de La Laguna, La Laguna, España, jul. 2015. [En línea]. Disponible en: <a href="https://riull.ull.es/xmlui/bitstream/handle/915/1188/Telemetria%20Laser.pdf?sequence=1" target="_blank" rel="noopener">https://riull.ull.es/xmlui/bitstream/handle/915/1188/Telemetria%20Laser.pdf?sequence=1</a></li>
    </ol>
  </div>
</section>

<!-- ============ EQUIPO ============ -->
<section id="equipo">
  <div class="wrap">
    <div class="sec-head">
      <span class="bar"></span>
      <h2>Nuestro equipo</h2>
      <p>Cinco estudiantes, un mismo objetivo: que la óptica se entienda y dé ganas de seguir explorando.</p>
    </div>
    <div class="team">
      <div class="member"><div class="avatar" style="--c:#E5484D;background:#E5484D" aria-hidden="true">JD</div><b>Johan Leander Dzul López</b></div>
      <div class="member"><div class="avatar" style="--c:#E07B00;background:#E07B00" aria-hidden="true">CV</div><b>Clara de Asís Vazquez Martín</b></div>
      <div class="member"><div class="avatar" style="--c:#1E9E6E;background:#1E9E6E" aria-hidden="true">MO</div><b>Mia Guadalupe Ortiz Pereira</b></div>
      <div class="member"><div class="avatar" style="--c:#3B82F6;background:#3B82F6" aria-hidden="true">AP</div><b>Alberto Vidal Puch Salas</b></div>
      <div class="member"><div class="avatar" style="--c:#7C4DFF;background:#7C4DFF" aria-hidden="true">JU</div><b>Jose Armando Uc Cardenas</b></div>
    </div>
  </div>
</section>

</main>

<footer>
  <div class="wrap">
    <p><b>Óptica en acción</b> — Proyecto de Física</p>
    <p>Johan Leander Dzul López, Clara de Asís Vazquez Martín, Mia Guadalupe Ortiz Pereira, Alberto Vidal Puch Salas y Jose Armando Uc Cardenas</p>
  </div>
</footer>

<script>
(function(){
  var $ = function(id){ return document.getElementById(id); };
  var C = 299792458;
  var rad = function(d){ return d*Math.PI/180; };
  var deg = function(r){ return r*180/Math.PI; };
  var NS = 'http://www.w3.org/2000/svg';

  /* ---- Velocidad en un material ---- */
  function vel(){
    var n = parseFloat($('vmat').value);
    var v = C/n;
    $('vout').innerHTML = '<p>Velocidad: <strong>' + (v/1e8).toFixed(3) + ' × 10<sup>8</sup> m/s</strong></p>' +
      '<p>Equivale al <strong>' + (100/n).toFixed(1) + ' %</strong> de <i>c</i>.</p>';
  }
  $('vmat').addEventListener('change', vel); vel();

  /* ---- Snell ---- */
  function names(n){
    if(n===1) return 'Aire (1.00)'; if(n===1.33) return 'Agua (1.33)';
    if(n===1.5) return 'Vidrio (1.50)'; return 'Diamante (2.42)';
  }
  function setLine(id,x1,y1,x2,y2){
    var l=$(id); l.setAttribute('x1',x1); l.setAttribute('y1',y1); l.setAttribute('x2',x2); l.setAttribute('y2',y2);
  }
  function snell(){
    var n1=parseFloat($('n1').value), n2=parseFloat($('n2').value), a=parseInt($('ang').value,10);
    $('angv').textContent = a+'°';
    $('tn1').textContent = 'Medio 1: '+names(n1);
    $('tn2').textContent = 'Medio 2: '+names(n2);
    var t1=rad(a), L=130, ox=200, oy=150;
    setLine('rInc', ox-L*Math.sin(t1), oy-L*Math.cos(t1), ox, oy);
    setLine('rRef', ox, oy, ox+L*Math.sin(t1), oy-L*Math.cos(t1));
    var s2 = n1*Math.sin(t1)/n2, html='';
    if(s2<=1){
      var t2=Math.asin(s2);
      setLine('rRfr', ox, oy, ox+L*Math.sin(t2), oy+L*Math.cos(t2));
      $('rRfr').style.display='';
      html += '<p>Ángulo refractado: <strong>θ₂ = '+deg(t2).toFixed(1)+'°</strong></p>';
      html += '<p><span class="badge ok">Hay refracción</span></p>';
    } else {
      $('rRfr').style.display='none';
      html += '<p>Ángulo refractado: <strong>no existe</strong></p>';
      html += '<p><span class="badge warn">Reflexión interna total</span></p>';
    }
    if(n1>n2){
      html += '<p>Ángulo crítico: <strong>θc = '+deg(Math.asin(n2/n1)).toFixed(1)+'°</strong></p>';
    } else {
      html += '<p>Como n₁ ≤ n₂ no hay ángulo crítico: siempre se refracta.</p>';
    }
    html += '<p>Ángulo reflejado: <strong>θᵣ = '+a+'°</strong></p>';
    $('snellOut').innerHTML = html;
  }
  ['n1','n2','ang'].forEach(function(id){ $(id).addEventListener('input', snell); });
  snell();

  /* ---- Lente delgada ---- */
  function mk(tag, attrs){
    var e=document.createElementNS(NS,tag);
    for(var k in attrs){ e.setAttribute(k, attrs[k]); }
    return e;
  }
  function lens(){
    var conv = $('ltype').value==='conv';
    var fabs = parseFloat($('lf').value);
    var F = conv ? fabs : -fabs;
    var d = parseFloat($('ldo').value);
    $('lfv').textContent = fabs+' cm';
    $('ldov').textContent = d+' cm';
    var S=6, cx=300, cy=150, ho=4, yo=cy-ho*S, xr=590;
    var g=$('lensDyn'); while(g.firstChild) g.removeChild(g.firstChild);

    // Lente
    var path = conv ? 'M300 40 Q334 150 300 260 Q266 150 300 40Z'
                    : 'M284 40 Q306 150 284 260 L316 260 Q294 150 316 40Z';
    g.appendChild(mk('path',{d:path,fill:'#9D8CFF','fill-opacity':'.4',stroke:'#CFC9FF','stroke-width':'2'}));

    // Focos
    [-1,1].forEach(function(s){
      var fx = cx + s*fabs*S;
      g.appendChild(mk('circle',{cx:fx,cy:cy,r:4,fill:'#F5D547'}));
      var t=mk('text',{x:fx,y:cy+20,fill:'#F5D547','font-size':'12','text-anchor':'middle'}); t.textContent='F';
      g.appendChild(t);
    });

    // Objeto
    var ox = cx - d*S;
    g.appendChild(mk('line',{x1:ox,y1:cy,x2:ox,y2:yo,stroke:'#fff','stroke-width':'4','stroke-linecap':'round'}));
    g.appendChild(mk('circle',{cx:ox,cy:yo,r:5,fill:'#fff'}));

    var inf = Math.abs(1/F - 1/d) < 1e-9;
    var di=null, m=null;
    if(!inf){ di = 1/(1/F - 1/d); m = -di/d; }
    var virtual = (di!==null && di<0);

    // Rayo 1: paralelo al eje, luego pasa (o parece venir) del foco
    var s = F>0 ? 1 : -1;
    var d1x = Math.abs(F)*S, d1y = s*(cy-yo);
    var t1 = (xr-cx)/d1x;
    var e1 = [xr, yo + t1*d1y];
    g.appendChild(mk('line',{x1:ox,y1:yo,x2:cx,y2:yo,stroke:'#FFB454','stroke-width':'2.5'}));
    // Rayo 2: por el centro
    var t2 = (xr-cx)/(d*S);
    var e2 = [xr, cy + t2*(cy-yo)];
    g.appendChild(mk('line',{x1:ox,y1:yo,x2:cx,y2:cy,stroke:'#4FD6A0','stroke-width':'2.5'}));

    var xi, yi;
    if(!inf){
      xi = cx + di*S; yi = cy - (m*ho)*S;
      if(virtual){
        g.appendChild(mk('line',{x1:cx,y1:yo,x2:xi,y2:yi,stroke:'#FFB454','stroke-width':'2','stroke-dasharray':'5 4'}));
        g.appendChild(mk('line',{x1:cx,y1:cy,x2:xi,y2:yi,stroke:'#4FD6A0','stroke-width':'2','stroke-dasharray':'5 4'}));
      }
    }
    g.appendChild(mk('line',{x1:cx,y1:yo,x2:e1[0],y2:e1[1],stroke:'#FFB454','stroke-width':'2.5'}));
    g.appendChild(mk('line',{x1:cx,y1:cy,x2:e2[0],y2:e2[1],stroke:'#4FD6A0','stroke-width':'2.5'}));

    if(!inf){
      var at={x1:xi,y1:cy,x2:xi,y2:yi,stroke:'#FF8FB1','stroke-width':'4','stroke-linecap':'round'};
      if(virtual) at['stroke-dasharray']='6 5';
      g.appendChild(mk('line',at));
      g.appendChild(mk('circle',{cx:xi,cy:yi,r:5,fill:'#FF8FB1'}));
    }

    var out;
    if(inf){
      out = '<p><strong>El objeto está en el foco.</strong></p><p>Los rayos salen paralelos y la imagen se forma en el infinito.</p>';
    } else {
      var nat = virtual ? 'virtual' : 'real';
      var ori = m>0 ? 'derecha' : 'invertida';
      var am = Math.abs(m);
      var siz = Math.abs(am-1)<0.005 ? 'del mismo tamaño' : (am>1 ? 'mayor' : 'menor');
      out = '<p>Distancia de la imagen: <strong>dᵢ = '+di.toFixed(1)+' cm</strong></p>'+
            '<p>Aumento: <strong>m = '+m.toFixed(2)+'</strong></p>'+
            '<p>La imagen es <strong>'+nat+'</strong>, <strong>'+ori+'</strong> y <strong>'+siz+'</strong>.</p>';
      if(Math.abs(xi-cx)>300 || Math.abs(yi-cy)>150){
        out += '<p>La imagen se sale del dibujo, pero el cálculo sigue siendo válido.</p>';
      }
    }
    $('lensOut').innerHTML = out;
  }
  ['ltype','lf','ldo'].forEach(function(id){ $(id).addEventListener('input', lens); });
  lens();

  /* ---- Fibra óptica ---- */
  function fiber(){
    var nc=parseFloat($('fcore').value), nl=parseFloat($('fclad').value), a=parseInt($('fang').value,10);
    if(nl>=nc){ nl = Math.round((nc-0.01)*100)/100; $('fclad').value = nl; }
    $('fcorev').textContent = nc.toFixed(2);
    $('fcladv').textContent = nl.toFixed(2);
    $('fangv').textContent = a+'°';

    var thc = Math.asin(nl/nc);
    var NA = Math.sqrt(nc*nc - nl*nl);
    var thmax = Math.asin(Math.min(1,NA));
    var th1 = Math.asin(Math.sin(rad(a))/nc);      // ángulo con el eje dentro del núcleo
    var cosT = Math.cos(th1);                       // sen del ángulo de incidencia en la pared
    var guided = cosT >= nl/nc;

    // Dibujo
    var x=60, y=100, dir=-1, pts=[[x,y]], esc=[], tan=Math.tan(th1), xEnd=560;
    // rayo en el aire
    var ta = rad(a);
    $('fAir').setAttribute('points', (10)+','+(100+50*Math.tan(ta))+' 60,100');
    if(tan<1e-6){
      pts.push([xEnd,y]);
    } else {
      var guard=0;
      while(x<xEnd && guard<200){
        guard++;
        var target = dir===-1 ? 70 : 130;
        var dx = Math.abs(target-y)/tan;
        if(x+dx>xEnd){
          pts.push([xEnd, y + dir*(xEnd-x)*tan]);
          break;
        }
        x += dx; y = target; pts.push([x,y]);
        if(guided){ dir = -dir; }
        else {
          var phi1 = Math.PI/2 - th1;
          var sphi2 = nc*Math.sin(phi1)/nl;
          var phi2 = Math.asin(Math.min(1,sphi2));
          esc = [[x,y],[x+60*Math.sin(phi2), y + dir*60*Math.cos(phi2)]];
          break;
        }
      }
    }
    $('fRay').setAttribute('points', pts.map(function(p){return p[0].toFixed(1)+','+p[1].toFixed(1);}).join(' '));
    $('fEsc').setAttribute('points', esc.map(function(p){return p[0].toFixed(1)+','+p[1].toFixed(1);}).join(' '));

    var html = '<p>Ángulo crítico: <strong>θc = '+deg(thc).toFixed(1)+'°</strong></p>'+
      '<p>Apertura numérica: <strong>AN = '+NA.toFixed(3)+'</strong></p>'+
      '<p>Ángulo máximo de entrada: <strong>'+deg(thmax).toFixed(1)+'°</strong></p>'+
      '<p>Ángulo dentro del núcleo: <strong>'+deg(th1).toFixed(1)+'°</strong> respecto al eje</p>'+
      '<p>' + (guided ? '<span class="badge ok">El rayo queda guiado</span>' : '<span class="badge warn">El rayo se escapa al revestimiento</span>') + '</p>';
    $('fiberOut').innerHTML = html;
  }
  ['fcore','fclad','fang'].forEach(function(id){ $(id).addEventListener('input', fiber); });
  fiber();

  /* ---- Tiempo de vuelo ---- */
  function fmtT(t){
    if(t<1e-6) return (t*1e9).toFixed(2)+' ns';
    if(t<1e-3) return (t*1e6).toFixed(3)+' µs';
    return (t*1e3).toFixed(3)+' ms';
  }
  function tofFromD(){
    var d=parseFloat($('tofd').value);
    if(isNaN(d)||d<0){ $('tofOut').innerHTML='<p>Escribe una distancia mayor o igual a 0.</p>'; return; }
    var t=2*d/C; $('toft').value = +(t*1e9).toPrecision(6);
    $('tofOut').innerHTML = '<p>Distancia: <strong>'+d+' m</strong></p><p>Tiempo de ida y vuelta: <strong>'+fmtT(t)+'</strong></p><p>Fórmula: t = 2d / c</p>';
  }
  function tofFromT(){
    var tn=parseFloat($('toft').value);
    if(isNaN(tn)||tn<0){ $('tofOut').innerHTML='<p>Escribe un tiempo mayor o igual a 0.</p>'; return; }
    var d=C*tn*1e-9/2; $('tofd').value = +d.toPrecision(6);
    $('tofOut').innerHTML = '<p>Tiempo medido: <strong>'+tn+' ns</strong></p><p>Distancia al objeto: <strong>'+d.toFixed(3)+' m</strong></p><p>Fórmula: d = c · t / 2</p>';
  }
  $('tofd').addEventListener('input', tofFromD);
  $('toft').addEventListener('input', tofFromT);
  tofFromD();
})();
</script>
</body>
</html>
