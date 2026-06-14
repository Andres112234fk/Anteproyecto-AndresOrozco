<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Pitch – Monografía Sesgos Cognitivos | Kolbe</title>

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/reveal.js/4.6.1/reveal.min.css">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&family=Syne:wght@700;800&display=swap" rel="stylesheet">

<style>
:root {
  --verde:  #00C9A7;
  --rojo:   #E05A4E;
  --blanco: #F0EEE9;
  --gris:   #8A8A9A;
  --fondo:  #070710;
  --card:   #10101A;
  --borde:  rgba(255,255,255,0.07);
  --oro:    #F5A623;
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

.reveal-viewport { background: var(--fondo); }
.reveal { font-family: 'Inter', sans-serif; color: var(--blanco); }
.reveal .slides { text-align: left; }
.reveal .slides section { padding: 0; overflow: hidden; }
.reveal .progress { color: var(--verde); height: 3px; }
.reveal .controls { color: var(--verde); }

/* ── TIPOGRAFÍA ── */
.display {
  font-family: 'Syne', sans-serif;
  font-weight: 800;
  letter-spacing: -0.025em;
  line-height: 1.05;
}
.eyebrow {
  font-size: 10px;
  font-weight: 600;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--verde);
  margin-bottom: 16px;
  display: block;
}

/* ── LAYOUT ── */
.slide-inner {
  position: relative;
  width: 100%;
  height: 100%;
  padding: 44px 64px 40px;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  overflow: hidden;
  z-index: 2;
}
.slide-bg {
  position: absolute;
  inset: 0;
  z-index: 0;
  overflow: hidden;
}
.slide-bg + * { position: relative; z-index: 2; }

/* Slide number */
.snum {
  position: absolute;
  top: 24px;
  right: 28px;
  font-size: 11px;
  color: rgba(138,138,154,0.5);
  letter-spacing: 0.08em;
  z-index: 10;
}

/* ── TIMER ── */
#timer {
  position: fixed;
  bottom: 16px;
  right: 22px;
  font-family: 'Syne', sans-serif;
  font-size: 13px;
  font-weight: 700;
  color: var(--gris);
  z-index: 9999;
  letter-spacing: 0.06em;
  cursor: pointer;
  transition: color 0.3s;
  background: rgba(7,7,16,0.8);
  padding: 6px 14px;
  border-radius: 999px;
  border: 1px solid var(--borde);
}
#timer.warn   { color: var(--oro); border-color: rgba(245,166,35,0.3); }
#timer.danger { color: var(--rojo); border-color: rgba(224,90,78,0.4); }

/* ══════════════════════════════════════
   SLIDE 1 · GANCHO
══════════════════════════════════════ */
#s1 .framing-split {
  display: grid;
  grid-template-columns: 1fr 1px 1fr;
  margin-top: 28px;
  height: 300px;
  flex-shrink: 0;
}
#s1 .split-line {
  background: linear-gradient(to bottom, transparent, var(--verde) 30%, var(--verde) 70%, transparent);
  width: 1px;
  transition: background 0.6s;
}
#s1 .option { padding: 24px 36px; display: flex; flex-direction: column; justify-content: center; }
#s1 .opt-tag {
  font-size: 10px; font-weight: 600; letter-spacing: 0.16em;
  text-transform: uppercase; margin-bottom: 14px;
}
#s1 .opt-a .opt-tag { color: var(--verde); }
#s1 .opt-b .opt-tag { color: var(--rojo); }
#s1 .opt-text {
  font-family: 'Syne', sans-serif;
  font-weight: 700; font-size: 26px; line-height: 1.25; color: var(--blanco);
}
#s1 .opt-sub { font-size: 12px; color: var(--gris); margin-top: 10px; line-height: 1.5; }
#s1 .pregunta-hint {
  margin-top: 20px;
  font-size: 13px; color: var(--gris); font-style: italic;
  border-top: 1px solid var(--borde); padding-top: 16px;
}

/* ══════════════════════════════════════
   SLIDE 2 · REVELACIÓN
══════════════════════════════════════ */
#s2 .reveal-pill {
  display: inline-block;
  background: rgba(0,201,167,0.1);
  border: 1px solid rgba(0,201,167,0.3);
  border-radius: 999px;
  padding: 7px 18px;
  font-size: 12px; color: var(--verde); margin-bottom: 20px;
}
#s2 .headline {
  font-family: 'Syne', sans-serif;
  font-weight: 700; font-size: 30px; line-height: 1.25; margin-bottom: 8px;
}
#s2 .sub { font-size: 13px; color: var(--gris); margin-bottom: 28px; line-height: 1.6; }
#s2 .stat-row {
  display: grid; grid-template-columns: 1fr 1fr; gap: 40px; margin-top: 4px;
}
#s2 .big-num {
  font-family: 'Syne', sans-serif;
  font-weight: 800; font-size: 96px; line-height: 1; letter-spacing: -0.04em;
}
#s2 .big-num.verde { color: var(--verde); }
#s2 .big-num.rojo  { color: var(--rojo); }
#s2 .stat-desc { font-size: 13px; color: var(--gris); margin-top: 6px; line-height: 1.6; }

/* ══════════════════════════════════════
   SLIDE 3 · GLOBALES
══════════════════════════════════════ */
#s3 .source-grid {
  display: grid; grid-template-columns: 1fr 1fr; gap: 18px; margin-top: 24px;
}
.scard {
  background: var(--card);
  border: 1px solid var(--borde);
  border-radius: 14px; padding: 24px 26px;
  position: relative; overflow: hidden;
}
.scard::before {
  content: '';
  position: absolute; top: 0; left: 0; right: 0; height: 2px;
  background: linear-gradient(90deg, var(--verde), transparent);
}
.scard .inst { font-size: 10px; letter-spacing: 0.13em; text-transform: uppercase; color: var(--verde); font-weight: 600; margin-bottom: 8px; }
.scard .num { font-family: 'Syne', sans-serif; font-weight: 800; font-size: 52px; line-height: 1; letter-spacing: -0.03em; color: var(--blanco); margin-bottom: 6px; }
.scard .num span { color: var(--verde); font-size: 30px; }
.scard .desc { font-size: 12.5px; color: var(--gris); line-height: 1.6; }
.scard .cite { font-size: 10px; color: rgba(138,138,154,0.5); margin-top: 10px; font-style: italic; }

/* ══════════════════════════════════════
   SLIDE 4 · LATAM + COLOMBIA
══════════════════════════════════════ */
#s4 .region-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 18px; margin-top: 22px; }
.rcard {
  background: var(--card); border: 1px solid var(--borde);
  border-radius: 14px; padding: 24px 26px; position: relative; overflow: hidden;
}
.rcard.latam::before { content:''; position:absolute; top:0; left:0; right:0; height:2px; background: linear-gradient(90deg,var(--oro),transparent); }
.rcard.col::before   { content:''; position:absolute; top:0; left:0; right:0; height:2px; background: linear-gradient(90deg,var(--verde),transparent); }
.rcard .rlabel { font-size: 10px; letter-spacing: 0.14em; text-transform: uppercase; font-weight: 600; margin-bottom: 10px; }
.rcard.latam .rlabel { color: var(--oro); }
.rcard.col   .rlabel { color: var(--verde); }
.rcard .rnum { font-family: 'Syne', sans-serif; font-weight: 800; font-size: 60px; line-height: 1; letter-spacing: -0.03em; margin-bottom: 6px; }
.rcard.latam .rnum { color: var(--oro); }
.rcard.col   .rnum { color: var(--verde); }
.rcard .rdesc { font-size: 12.5px; color: var(--gris); line-height: 1.6; }
.rcard .rcite { font-size: 10px; color: rgba(138,138,154,0.45); margin-top: 8px; font-style: italic; }
#s4 .bridge {
  margin-top: 18px; padding: 14px 22px;
  border-left: 3px solid var(--verde); background: rgba(0,201,167,0.05);
  border-radius: 0 10px 10px 0; font-size: 13.5px; color: var(--blanco); line-height: 1.6;
}

/* ══════════════════════════════════════
   SLIDE 5 · PREGUNTA + OBJ GENERAL
══════════════════════════════════════ */
#s5 .pbox {
  margin-top: 20px; padding: 26px 30px;
  border: 1px solid rgba(0,201,167,0.3); border-radius: 14px;
  background: rgba(0,201,167,0.04);
}
#s5 .pbox p {
  font-family: 'Syne', sans-serif; font-weight: 700;
  font-size: 18px; line-height: 1.5; color: var(--blanco);
}
#s5 .pbox em { color: var(--verde); font-style: normal; }
#s5 .obj-title { font-size: 10px; letter-spacing: 0.14em; text-transform: uppercase; color: var(--gris); font-weight: 600; margin: 22px 0 12px; }
#s5 .etapas { display: grid; grid-template-columns: repeat(3,1fr); gap: 12px; }
#s5 .etapa { background: var(--card); border: 1px solid var(--borde); border-radius: 12px; padding: 16px 18px; }
#s5 .enum { font-family: 'Syne', sans-serif; font-size: 26px; font-weight: 800; color: var(--verde); margin-bottom: 4px; }
#s5 .elabel { font-size: 13px; font-weight: 600; color: var(--blanco); margin-bottom: 4px; }
#s5 .edesc { font-size: 11.5px; color: var(--gris); line-height: 1.5; }

/* ══════════════════════════════════════
   SLIDE 6 · TIPO + ENFOQUE + CIERRE
══════════════════════════════════════ */
#s6 .tgrid { display: grid; grid-template-columns: 1fr 1fr; gap: 14px; margin-top: 22px; }
.tcard { background: var(--card); border: 1px solid var(--borde); border-radius: 12px; padding: 20px 22px; }
.ttag {
  display: inline-block; font-size: 9px; letter-spacing: 0.14em;
  text-transform: uppercase; font-weight: 600; padding: 3px 10px;
  border-radius: 999px; margin-bottom: 10px;
}
.tcard:nth-child(1) .ttag,.tcard:nth-child(2) .ttag { background: rgba(0,201,167,0.12); color: var(--verde); }
.tcard:nth-child(3) .ttag,.tcard:nth-child(4) .ttag { background: rgba(245,166,35,0.12); color: var(--oro); }
.tname { font-family: 'Syne', sans-serif; font-size: 18px; font-weight: 700; color: var(--blanco); margin-bottom: 6px; }
.tdesc { font-size: 12px; color: var(--gris); line-height: 1.6; }
#s6 .cierre {
  margin-top: 18px; padding: 16px 22px;
  background: linear-gradient(135deg, rgba(0,201,167,0.08), rgba(0,201,167,0.02));
  border-radius: 10px; border: 1px solid rgba(0,201,167,0.18);
  font-size: 13.5px; color: var(--blanco); line-height: 1.6; font-style: italic;
}

/* ══════════════════════════════════════
   FRAGMENT ANIMATIONS
══════════════════════════════════════ */
.reveal .fragment {
  opacity: 0;
  transform: translateY(18px);
  transition: opacity 0.55s cubic-bezier(0.16,1,0.3,1),
              transform 0.55s cubic-bezier(0.16,1,0.3,1);
}
.reveal .fragment.visible { opacity: 1; transform: translateY(0); }

.reveal .fragment.from-left {
  opacity: 0; transform: translateX(-24px);
}
.reveal .fragment.from-left.visible { opacity: 1; transform: translateX(0); }

.reveal .fragment.from-right {
  opacity: 0; transform: translateX(24px);
}
.reveal .fragment.from-right.visible { opacity: 1; transform: translateX(0); }

.reveal .fragment.scale-in {
  opacity: 0; transform: scale(0.88);
  transition: opacity 0.5s ease, transform 0.5s cubic-bezier(0.34,1.56,0.64,1);
}
.reveal .fragment.scale-in.visible { opacity: 1; transform: scale(1); }

/* Canvas backgrounds */
canvas.bg-canvas {
  position: absolute; inset: 0; width: 100%; height: 100%;
  pointer-events: none; z-index: 0;
}
</style>
</head>
<body>

<div id="timer">▶ 3:00</div>

<div class="reveal">
<div class="slides">

<!-- ══════════════════════════════════════════
     SLIDE 1 · EL GANCHO — cerebro dividido
══════════════════════════════════════════ -->
<section id="s1" data-transition="fade" data-transition-speed="slow">
  <canvas class="bg-canvas" id="bg1"></canvas>
  <div class="slide-inner">
    <span class="snum">1 / 6</span>
    <span class="eyebrow">Experimento en vivo</span>
    <h2 class="display" style="font-size:36px;">Dos productos.<br>El mismo precio.<br><span style="color:var(--verde);">¿Cuál elegirían?</span></h2>

    <div id="s1" class="framing-split">
      <div class="option opt-a fragment from-left" data-fragment-index="1">
        <span class="opt-tag">Opción A</span>
        <p class="opt-text">"90% libre<br>de grasa"</p>
        <p class="opt-sub">Galletas empaquetadas · $3.200</p>
      </div>
      <div class="split-line"></div>
      <div class="option opt-b fragment from-right" data-fragment-index="1">
        <span class="opt-tag">Opción B</span>
        <p class="opt-text">"contiene<br>10% de grasa"</p>
        <p class="opt-sub">Galletas empaquetadas · $3.200</p>
      </div>
    </div>

    <p class="pregunta-hint fragment" data-fragment-index="2">
      Confíen en su instinto. El cerebro ya decidió.
    </p>
  </div>
</section>

<!-- ══════════════════════════════════════════
     SLIDE 2 · REVELACIÓN — partículas
══════════════════════════════════════════ -->
<section id="s2" data-transition="fade" data-transition-speed="slow">
  <canvas class="bg-canvas" id="bg2"></canvas>
  <div class="slide-inner">
    <span class="snum">2 / 6</span>
    <div class="reveal-pill fragment scale-in" data-fragment-index="0">Son exactamente el mismo producto.</div>
    <h2 class="headline">El cerebro eligió. Sin datos.<br>Solo por el <span style="color:var(--verde);">encuadre.</span></h2>
    <p class="sub">Tversky & Kahneman lo demostraron en 1981. Misma situación, distinto framing:</p>
    <div class="stat-row">
      <div class="fragment from-left" data-fragment-index="1">
        <div class="big-num verde" id="count72">0%</div>
        <p class="stat-desc">eligió la opción con framing <strong style="color:var(--verde);">positivo</strong></p>
      </div>
      <div class="fragment from-right" data-fragment-index="2">
        <div class="big-num rojo" id="count22">0%</div>
        <p class="stat-desc">eligió la misma opción con framing <strong style="color:var(--rojo);">negativo</strong></p>
      </div>
    </div>
  </div>
</section>

<!-- ══════════════════════════════════════════
     SLIDE 3 · GLOBALES — red de nodos
══════════════════════════════════════════ -->
<section id="s3" data-transition="fade" data-transition-speed="slow">
  <canvas class="bg-canvas" id="bg3"></canvas>
  <div class="slide-inner">
    <span class="snum">3 / 6</span>
    <span class="eyebrow">Escala global</span>
    <h2 class="display" style="font-size:28px;">El problema está documentado<br>a nivel mundial.</h2>
    <div class="source-grid">
      <div class="scard fragment" data-fragment-index="1">
        <div class="inst">Universidad de Queensland · 2025</div>
        <div class="num">53<span> estudios</span></div>
        <div class="desc">El mayor análisis sistemático de su tipo. Cómo los sesgos impactan la toma de decisiones en estudiantes — <strong style="color:var(--blanco);">10.941 participantes</strong> en total.</div>
        <div class="cite">Swaryandini & Noetel, 2025</div>
      </div>
      <div class="scard fragment" data-fragment-index="2">
        <div class="inst">Reuters Institute · Oxford · 2025</div>
        <div class="num">58<span>%</span></div>
        <div class="desc">de la población global <strong style="color:var(--blanco);">no distingue qué es verdadero</strong> de lo falso al consumir noticias online. +4 pts vs 2022.</div>
        <div class="cite">Digital News Report 2025 · 48 países</div>
      </div>
    </div>
  </div>
</section>

<!-- ══════════════════════════════════════════
     SLIDE 4 · LATAM + COLOMBIA — mapa
══════════════════════════════════════════ -->
<section id="s4" data-transition="fade" data-transition-speed="slow">
  <canvas class="bg-canvas" id="bg4"></canvas>
  <div class="slide-inner">
    <span class="snum">4 / 6</span>
    <span class="eyebrow">Más cerca de casa</span>
    <h2 class="display" style="font-size:28px;">Latinoamérica y Colombia<br>no son la excepción.</h2>
    <div class="region-grid">
      <div class="rcard latam fragment from-left" data-fragment-index="1">
        <div class="rlabel">Latinoamérica · Chile</div>
        <div class="rnum">94%</div>
        <div class="rdesc">de universitarios buscó <strong style="color:var(--blanco);">solo información que confirmara</strong> sus hipótesis. Solo el 6% contrastó fuentes.</div>
        <div class="rcite">Castro et al., 2019 · 3 universidades · 198 estudiantes</div>
      </div>
      <div class="rcard col fragment from-right" data-fragment-index="2">
        <div class="rlabel">Colombia · Pasto</div>
        <div class="rnum">72%</div>
        <div class="rdesc">de estudiantes de bachillerato en grados 9°–11° en <strong style="color:var(--blanco);">nivel indeciso</strong> en sus patrones globales de toma de decisiones.</div>
        <div class="rcite">Flórez-Madroñero & Pantoja-Solarte, 2024 · 50 estudiantes</div>
      </div>
    </div>
    <div class="bridge fragment" data-fragment-index="3">
      Y todo esto ocurre también aquí — en los pasillos del <strong>Colegio Bilingüe Maximiliano Kolbe.</strong> Solo que aún no hay datos que lo confirmen.
    </div>
  </div>
</section>

<!-- ══════════════════════════════════════════
     SLIDE 5 · PREGUNTA + OBJ GENERAL — espiral
══════════════════════════════════════════ -->
<section id="s5" data-transition="fade" data-transition-speed="slow">
  <canvas class="bg-canvas" id="bg5"></canvas>
  <div class="slide-inner">
    <span class="snum">5 / 6</span>
    <span class="eyebrow">Pregunta problema</span>
    <div class="pbox">
      <p>¿De qué manera el <em>sesgo de anclaje</em> hace a los jóvenes de bachillerato del Colegio Bilingüe Maximiliano Kolbe susceptibles al <em>framing</em> en sus decisiones relacionales?</p>
    </div>
    <div class="obj-title">Objetivo general · Experimento de tres etapas</div>
    <div class="etapas">
      <div class="etapa fragment scale-in" data-fragment-index="1">
        <div class="enum">01</div>
        <div class="elabel">Exposición</div>
        <div class="edesc">Exponer al sesgo mediante escenarios con framing positivo y negativo.</div>
      </div>
      <div class="etapa fragment scale-in" data-fragment-index="2">
        <div class="enum">02</div>
        <div class="elabel">Medición</div>
        <div class="edesc">Medir susceptibilidad con formulario mixto y registro de observaciones.</div>
      </div>
      <div class="etapa fragment scale-in" data-fragment-index="3">
        <div class="enum">03</div>
        <div class="elabel">Re-exposición</div>
        <div class="edesc">Aplicar nuevamente el experimento tras concientización sobre el sesgo.</div>
      </div>
    </div>
  </div>
</section>

<!-- ══════════════════════════════════════════
     SLIDE 6 · TIPO + ENFOQUE + CIERRE
══════════════════════════════════════════ -->
<section id="s6" data-transition="fade" data-transition-speed="slow">
  <canvas class="bg-canvas" id="bg6"></canvas>
  <div class="slide-inner">
    <span class="snum">6 / 6</span>
    <span class="eyebrow">Diseño investigativo</span>
    <h2 class="display" style="font-size:24px;">Tipo y enfoque</h2>
    <div class="tgrid">
      <div class="tcard fragment" data-fragment-index="1">
        <span class="ttag">Tipo</span>
        <div class="tname">Cuasi-experimental</div>
        <div class="tdesc">Se interviene directamente sobre las variables mediante el experimento de tres etapas, sin asignación aleatoria.</div>
      </div>
      <div class="tcard fragment" data-fragment-index="2">
        <span class="ttag">Alcance</span>
        <div class="tname">Correlacional</div>
        <div class="tdesc">Determina si existe relación entre el nivel de anclaje del estudiante y su susceptibilidad al framing.</div>
      </div>
      <div class="tcard fragment" data-fragment-index="3">
        <span class="ttag">Enfoque</span>
        <div class="tname">Cuantitativo</div>
        <div class="tdesc">Datos numéricos de escenarios hipotéticos para identificar correlaciones entre variables.</div>
      </div>
      <div class="tcard fragment" data-fragment-index="4">
        <span class="ttag">Enfoque</span>
        <div class="tname">Cualitativo</div>
        <div class="tdesc">Perspectivas y experiencias del grupo focal para una visión holística del problema.</div>
      </div>
    </div>
    <div class="cierre fragment" data-fragment-index="5">
      "El cerebro de sus estudiantes toma decisiones relacionales todos los días bajo influencia del framing. Esta investigación lo va a demostrar con evidencia propia del Kolbe."
    </div>
  </div>
</section>

</div>
</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/reveal.js/4.6.1/reveal.min.js"></script>
<script>
Reveal.initialize({
  hash: false,
  controls: true,
  progress: true,
  center: false,
  transition: 'fade',
  transitionSpeed: 'slow',
  backgroundTransition: 'fade',
  width: 1100,
  height: 620,
  margin: 0.04,
});

/* ══════════════════════════════════════
   TIMER
══════════════════════════════════════ */
const timerEl = document.getElementById('timer');
const TOTAL = 180;
let elapsed = 0, timerInterval = null, running = false;
const pad = n => String(n).padStart(2,'0');

function tickTimer() {
  elapsed++;
  const rem = TOTAL - elapsed;
  if (rem < 0) {
    const over = elapsed - TOTAL;
    timerEl.textContent = '⚠ +' + Math.floor(over/60) + ':' + pad(over%60);
    timerEl.className = 'danger'; return;
  }
  timerEl.textContent = '⏱ ' + Math.floor(rem/60) + ':' + pad(rem%60);
  timerEl.className = rem <= 30 ? 'danger' : rem <= 60 ? 'warn' : '';
}
function startTimer() { if (!running) { running = true; timerInterval = setInterval(tickTimer, 1000); } }
function resetTimer() { clearInterval(timerInterval); running = false; elapsed = 0; timerEl.textContent = '▶ 3:00'; timerEl.className = ''; }
timerEl.addEventListener('click', () => running ? resetTimer() : startTimer());
Reveal.on('slidechanged', e => { if (e.indexh >= 1 && !running) startTimer(); });
Reveal.on('fragmentshown', () => { if (!running) startTimer(); });
document.addEventListener('keydown', e => {
  if (e.key === 't' || e.key === 'T') resetTimer();
  if (e.key === 's' || e.key === 'S') startTimer();
});

/* ══════════════════════════════════════
   COUNTER ANIMATION — slide 2
══════════════════════════════════════ */
function animateCount(el, target, suffix, duration) {
  const start = performance.now();
  function step(now) {
    const p = Math.min((now - start) / duration, 1);
    const ease = 1 - Math.pow(1 - p, 3);
    el.textContent = Math.round(ease * target) + suffix;
    if (p < 1) requestAnimationFrame(step);
    else el.textContent = target + suffix;
  }
  requestAnimationFrame(step);
}

Reveal.on('fragmentshown', event => {
  const f = event.fragment;
  if (f.dataset.fragmentIndex === '1' && Reveal.getCurrentSlide().id === 's2') {
    setTimeout(() => animateCount(document.getElementById('count72'), 72, '%', 900), 100);
  }
  if (f.dataset.fragmentIndex === '2' && Reveal.getCurrentSlide().id === 's2') {
    setTimeout(() => animateCount(document.getElementById('count22'), 22, '%', 900), 100);
  }
});

/* ══════════════════════════════════════
   CANVAS BACKGROUNDS
══════════════════════════════════════ */

/* ── BG1: Cerebro geométrico dividido ── */
(function() {
  const canvas = document.getElementById('bg1');
  const ctx = canvas.getContext('2d');
  let W, H, raf;

  function resize() {
    W = canvas.width  = canvas.offsetWidth;
    H = canvas.height = canvas.offsetHeight;
  }

  function hexToRgb(hex) {
    const r = parseInt(hex.slice(1,3),16),
          g = parseInt(hex.slice(3,5),16),
          b = parseInt(hex.slice(5,7),16);
    return `${r},${g},${b}`;
  }

  // Nodos del cerebro — dos grupos (izquierdo verde, derecho rojo)
  const nodes = [];
  function buildNodes() {
    nodes.length = 0;
    const cx = W / 2, cy = H / 2;
    for (let i = 0; i < 38; i++) {
      const side = i < 19 ? -1 : 1;
      const angle = Math.random() * Math.PI * 2;
      const r = 60 + Math.random() * 180;
      nodes.push({
        x: cx + side * (40 + Math.abs(Math.cos(angle)) * r * 0.7),
        y: cy + Math.sin(angle) * r * 0.55,
        r: 2 + Math.random() * 2.5,
        side,
        pulse: Math.random() * Math.PI * 2,
        speed: 0.012 + Math.random() * 0.018,
        alpha: 0.3 + Math.random() * 0.4,
      });
    }
  }

  let t = 0;
  function draw() {
    ctx.clearRect(0,0,W,H);
    t += 0.008;

    // Glow center line
    const lg = ctx.createLinearGradient(W/2, H*0.1, W/2, H*0.9);
    lg.addColorStop(0, 'transparent');
    lg.addColorStop(0.5, 'rgba(0,201,167,0.08)');
    lg.addColorStop(1, 'transparent');
    ctx.fillStyle = lg;
    ctx.fillRect(W/2-1, 0, 2, H);

    // Connections
    for (let i = 0; i < nodes.length; i++) {
      for (let j = i+1; j < nodes.length; j++) {
        const a = nodes[i], b = nodes[j];
        if (a.side !== b.side) continue;
        const dist = Math.hypot(a.x-b.x, a.y-b.y);
        if (dist > 160) continue;
        const alpha = (1 - dist/160) * 0.18;
        const col = a.side === -1 ? '0,201,167' : '224,90,78';
        ctx.beginPath();
        ctx.moveTo(a.x, a.y);
        ctx.lineTo(b.x, b.y);
        ctx.strokeStyle = `rgba(${col},${alpha})`;
        ctx.lineWidth = 0.8;
        ctx.stroke();
      }
    }

    // Nodes
    nodes.forEach(n => {
      n.pulse += n.speed;
      const glow = 0.5 + 0.5 * Math.sin(n.pulse);
      const col = n.side === -1 ? '0,201,167' : '224,90,78';
      const grad = ctx.createRadialGradient(n.x,n.y,0,n.x,n.y,n.r*4);
      grad.addColorStop(0, `rgba(${col},${n.alpha * glow})`);
      grad.addColorStop(1, `rgba(${col},0)`);
      ctx.fillStyle = grad;
      ctx.beginPath();
      ctx.arc(n.x, n.y, n.r*4, 0, Math.PI*2);
      ctx.fill();
      ctx.fillStyle = `rgba(${col},${0.7 * glow})`;
      ctx.beginPath();
      ctx.arc(n.x, n.y, n.r, 0, Math.PI*2);
      ctx.fill();
    });

    raf = requestAnimationFrame(draw);
  }

  window.addEventListener('resize', () => { resize(); buildNodes(); });
  resize(); buildNodes();

  Reveal.on('slidechanged', e => {
    if (e.indexh === 0) { if (!raf) draw(); }
    else { cancelAnimationFrame(raf); raf = null; }
  });
  draw();
})();

/* ── BG2: Partículas flotantes ── */
(function() {
  const canvas = document.getElementById('bg2');
  const ctx = canvas.getContext('2d');
  let W, H, raf2;
  const particles = [];

  function resize() {
    W = canvas.width  = canvas.offsetWidth;
    H = canvas.height = canvas.offsetHeight;
  }

  function spawnParticle(side) {
    return {
      x: side === 0 ? W*0.25 : W*0.75,
      y: H * 0.5,
      vx: (Math.random()-0.5)*1.6 + (side === 0 ? -0.4 : 0.4),
      vy: (Math.random()-0.5)*1.6 - 0.3,
      life: 1,
      decay: 0.006 + Math.random()*0.008,
      r: 1.5 + Math.random()*3,
      col: side === 0 ? '0,201,167' : '224,90,78',
    };
  }

  let t2 = 0;
  function draw2() {
    ctx.clearRect(0,0,W,H);
    t2++;
    if (t2 % 3 === 0) { particles.push(spawnParticle(0)); particles.push(spawnParticle(1)); }

    // Radial glow BG
    const rg0 = ctx.createRadialGradient(W*0.25,H*0.5,0,W*0.25,H*0.5,200);
    rg0.addColorStop(0,'rgba(0,201,167,0.05)'); rg0.addColorStop(1,'transparent');
    ctx.fillStyle = rg0; ctx.fillRect(0,0,W,H);
    const rg1 = ctx.createRadialGradient(W*0.75,H*0.5,0,W*0.75,H*0.5,200);
    rg1.addColorStop(0,'rgba(224,90,78,0.05)'); rg1.addColorStop(1,'transparent');
    ctx.fillStyle = rg1; ctx.fillRect(0,0,W,H);

    for (let i = particles.length-1; i >= 0; i--) {
      const p = particles[i];
      p.x += p.vx; p.y += p.vy; p.life -= p.decay;
      if (p.life <= 0) { particles.splice(i,1); continue; }
      ctx.beginPath();
      ctx.arc(p.x, p.y, p.r, 0, Math.PI*2);
      ctx.fillStyle = `rgba(${p.col},${p.life*0.7})`;
      ctx.fill();
    }
    raf2 = requestAnimationFrame(draw2);
  }

  window.addEventListener('resize', resize);
  resize();

  Reveal.on('slidechanged', e => {
    if (e.indexh === 1) { if (!raf2) draw2(); }
    else { cancelAnimationFrame(raf2); raf2 = null; particles.length = 0; }
  });
})();

/* ── BG3: Red de nodos globales ── */
(function() {
  const canvas = document.getElementById('bg3');
  const ctx = canvas.getContext('2d');
  let W, H, raf3;
  const pts = [];

  function resize() {
    W = canvas.width  = canvas.offsetWidth;
    H = canvas.height = canvas.offsetHeight;
    pts.length = 0;
    for (let i = 0; i < 45; i++) {
      pts.push({
        x: Math.random()*W, y: Math.random()*H,
        vx: (Math.random()-0.5)*0.25,
        vy: (Math.random()-0.5)*0.25,
        r: 1+Math.random()*2,
      });
    }
  }

  function draw3() {
    ctx.clearRect(0,0,W,H);
    pts.forEach(p => {
      p.x += p.vx; p.y += p.vy;
      if (p.x < 0||p.x > W) p.vx *= -1;
      if (p.y < 0||p.y > H) p.vy *= -1;
    });
    for (let i = 0; i < pts.length; i++) {
      for (let j = i+1; j < pts.length; j++) {
        const d = Math.hypot(pts[i].x-pts[j].x, pts[i].y-pts[j].y);
        if (d > 140) continue;
        ctx.beginPath();
        ctx.moveTo(pts[i].x,pts[i].y);
        ctx.lineTo(pts[j].x,pts[j].y);
        ctx.strokeStyle = `rgba(0,201,167,${(1-d/140)*0.12})`;
        ctx.lineWidth = 0.8; ctx.stroke();
      }
      ctx.beginPath();
      ctx.arc(pts[i].x,pts[i].y,pts[i].r,0,Math.PI*2);
      ctx.fillStyle = 'rgba(0,201,167,0.35)'; ctx.fill();
    }
    raf3 = requestAnimationFrame(draw3);
  }

  window.addEventListener('resize', resize);
  resize();
  Reveal.on('slidechanged', e => {
    if (e.indexh === 2) { if (!raf3) draw3(); }
    else { cancelAnimationFrame(raf3); raf3 = null; }
  });
})();

/* ── BG4: Líneas que convergen (mapa abstracto) ── */
(function() {
  const canvas = document.getElementById('bg4');
  const ctx = canvas.getContext('2d');
  let W, H, raf4, t4 = 0;

  function resize() {
    W = canvas.width  = canvas.offsetWidth;
    H = canvas.height = canvas.offsetHeight;
  }

  const lines = Array.from({length: 18}, (_,i) => ({
    angle: (i/18)*Math.PI*2,
    len: 0,
    maxLen: 180 + Math.random()*120,
    speed: 0.8 + Math.random()*0.6,
    col: i < 9 ? '245,166,35' : '0,201,167',
    w: 0.6 + Math.random(),
  }));

  function draw4() {
    ctx.clearRect(0,0,W,H);
    t4 += 0.012;
    const cx = W*0.72, cy = H*0.5;

    lines.forEach(l => {
      if (l.len < l.maxLen) l.len += l.speed;
      const x2 = cx + Math.cos(l.angle + t4*0.05) * l.len;
      const y2 = cy + Math.sin(l.angle + t4*0.05) * l.len * 0.6;
      const grad = ctx.createLinearGradient(cx,cy,x2,y2);
      grad.addColorStop(0,`rgba(${l.col},0.4)`);
      grad.addColorStop(1,`rgba(${l.col},0)`);
      ctx.beginPath(); ctx.moveTo(cx,cy); ctx.lineTo(x2,y2);
      ctx.strokeStyle = grad; ctx.lineWidth = l.w; ctx.stroke();
    });

    // Center dot
    const rg = ctx.createRadialGradient(cx,cy,0,cx,cy,30);
    rg.addColorStop(0,'rgba(0,201,167,0.4)'); rg.addColorStop(1,'transparent');
    ctx.fillStyle = rg; ctx.beginPath(); ctx.arc(cx,cy,30,0,Math.PI*2); ctx.fill();
    ctx.fillStyle='rgba(0,201,167,0.9)'; ctx.beginPath(); ctx.arc(cx,cy,4,0,Math.PI*2); ctx.fill();

    raf4 = requestAnimationFrame(draw4);
  }

  window.addEventListener('resize', resize);
  resize();
  Reveal.on('slidechanged', e => {
    if (e.indexh === 3) { if (!raf4) draw4(); }
    else { cancelAnimationFrame(raf4); raf4 = null; }
  });
})();

/* ── BG5: Espiral de anclaje ── */
(function() {
  const canvas = document.getElementById('bg5');
  const ctx = canvas.getContext('2d');
  let W, H, raf5, t5 = 0;

  function resize() {
    W = canvas.width  = canvas.offsetWidth;
    H = canvas.height = canvas.offsetHeight;
  }

  function draw5() {
    ctx.clearRect(0,0,W,H);
    t5 += 0.008;
    const cx = W*0.78, cy = H*0.5;
    ctx.save();
    ctx.translate(cx, cy);
    ctx.rotate(t5);

    for (let arm = 0; arm < 3; arm++) {
      ctx.rotate((Math.PI*2)/3);
      ctx.beginPath();
      for (let i = 0; i < 120; i++) {
        const angle = (i/120)*Math.PI*4;
        const r = i*1.6;
        const x = Math.cos(angle)*r;
        const y = Math.sin(angle)*r;
        if (i===0) ctx.moveTo(x,y); else ctx.lineTo(x,y);
      }
      const grad = ctx.createLinearGradient(0,0,120,0);
      grad.addColorStop(0,'rgba(0,201,167,0.5)');
      grad.addColorStop(1,'rgba(0,201,167,0)');
      ctx.strokeStyle = grad;
      ctx.lineWidth = 1.2; ctx.stroke();
    }
    ctx.restore();

    // Anchor symbol subtle
    ctx.fillStyle = 'rgba(0,201,167,0.04)';
    ctx.font = `bold ${H*0.6}px serif`;
    ctx.textAlign = 'center';
    ctx.textBaseline = 'middle';
    ctx.fillText('⚓', cx, cy);

    raf5 = requestAnimationFrame(draw5);
  }

  window.addEventListener('resize', resize);
  resize();
  Reveal.on('slidechanged', e => {
    if (e.indexh === 4) { if (!raf5) draw5(); }
    else { cancelAnimationFrame(raf5); raf5 = null; }
  });
})();

/* ── BG6: Grid de células que se llenan ── */
(function() {
  const canvas = document.getElementById('bg6');
  const ctx = canvas.getContext('2d');
  let W, H, raf6, t6 = 0;
  const cells = [];

  function resize() {
    W = canvas.width  = canvas.offsetWidth;
    H = canvas.height = canvas.offsetHeight;
    cells.length = 0;
    const sz = 52, cols = Math.ceil(W/sz)+1, rows = Math.ceil(H/sz)+1;
    for (let r = 0; r < rows; r++) {
      for (let c = 0; c < cols; c++) {
        cells.push({ x: c*sz, y: r*sz, sz, fill: Math.random()*0.12, speed: 0.001+Math.random()*0.002, phase: Math.random()*Math.PI*2 });
      }
    }
  }

  function draw6() {
    ctx.clearRect(0,0,W,H);
    t6 += 0.015;
    cells.forEach(c => {
      c.fill = 0.03 + 0.04 * Math.sin(t6 + c.phase);
      ctx.strokeStyle = `rgba(0,201,167,${c.fill*2})`;
      ctx.lineWidth = 0.5;
      ctx.strokeRect(c.x, c.y, c.sz-2, c.sz-2);
    });
    raf6 = requestAnimationFrame(draw6);
  }

  window.addEventListener('resize', resize);
  resize();
  Reveal.on('slidechanged', e => {
    if (e.indexh === 5) { if (!raf6) draw6(); }
    else { cancelAnimationFrame(raf6); raf6 = null; }
  });
})();

</script>
</body>
</html># Anteproyecto-AndresOrozco
