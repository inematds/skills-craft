# BUILD-SPEC — Curso "Criando Agent Skills" (formato INEMA.CLUB)

Você (subagente) vai construir páginas HTML de UMA trilha deste curso. Siga este spec ao pé da letra. Não invente estrutura nova — copie os esqueletos abaixo e preencha o conteúdo.

## Identidade do curso
- Título curto (nav/logo): `Criando Skills` · emoji `🛠️`
- Título completo: "Criando Agent Skills — Do Catálogo à Sua Primeira Skill"
- Footer (todas as páginas): `Criando Agent Skills · <a href="https://inema.club" class="text-sky-400 hover:text-sky-300">INEMA.CLUB</a> · 2026 · Dados coletados do skills.sh`
- Idioma: PT-BR. Tom: direto, técnico, sem encheção.

## Trilhas e cores (Tailwind)
| Trilha | Slug | Tema | Cor | accent (texto/bg/border/gradiente) |
|---|---|---|---|---|
| T1 | trilha1 | Panorama do Ecossistema | emerald | text-emerald-400 / bg-emerald-500/20 / border-emerald-500/30 / from-emerald-900/30 |
| T2 | trilha2 | Qualidade & As Melhores | blue | text-blue-400 / bg-blue-500/20 / border-blue-500/30 / from-blue-900/30 |
| T3 | trilha3 | Anatomia de uma Skill | purple | text-purple-400 / bg-purple-500/20 / border-purple-500/30 / from-purple-900/30 |
| T4 | trilha4 | Como Criar (o loop) | amber | text-amber-400 / bg-amber-500/20 / border-amber-500/30 / from-amber-900/30 |
| T5 | trilha5 | O Que Pensar | teal | text-teal-400 / bg-teal-500/20 / border-teal-500/30 / from-teal-900/30 |
| botão "próximo" usa a cor da PRÓXIMA trilha. Cor secundária dos SVGs = ciano `#38bdf8`. |

## Regras OBRIGATÓRIAS (checklist INEMA)
1. Botões de ação alinhados à ESQUERDA: `flex justify-start`.
2. Indicador de tópico = número em círculo `<span class="w-6 h-6 rounded-full ...">1</span>` (NUNCA seta ▶).
3. No index, cada tópico expansível tem 3 seções: **O que é / Por que aprender / Conceitos-chave**.
4. Link INEMA.CLUB presente em TODAS as páginas com `text-sky-400`.
5. Light mode CSS completo (use o bloco `<style>` deste spec inteiro — já tem base + acentos + sem-gradiente + nav).
6. Título do módulo `text-2xl font-bold` (h3 nos cards; h1 `text-3xl sm:text-4xl` no header do módulo).
7. Cores corretas da trilha em tudo.
8. Theme toggle funcionando (use o JS deste spec).
9. No index da trilha: CADA card de módulo tem `<a href="modulo-X-Y.html" ...>Ver Completo</a>` + botão `Ver em Modal`.
10. MÍNIMO 6 tópicos por módulo (no index expansível E na página do módulo: 6 seções `topico-N`).
11. **Mapa da trilha** OBRIGATÓRIO no index: `<h2>Mapa da trilha</h2>` + grid de cards-âncora. Cada card: header `justify-between` (X.Y esq + duração dir) + emoji+título + subtítulo PUNCHY. NÃO usar "Navegação Rápida".
12. NAV completo em TODAS as páginas (use o bloco deste spec). Trilha ativa destacada.
13. PROFUNDIDADE módulo: 6-8 seções com VARIEDADE (≥2 grids ✓/✗, ≥1 timeline/lista numerada, ≥2 tip boxes, ≥1 code box). ~400-700 linhas.
14. Bordas suavizadas dark já estão no CSS (border-dark-600 + divide).
15. Divisor "Conteúdo detalhado": h2 simples se usar.
16. SVG futurista: ≥1 diagrama SVG inline por MÓDULO (cor da trilha + ciano, glow, `role="img"`+`aria-label`, `w-full h-auto`) e 1 hero SVG no index da trilha.

## Caminhos (a partir de site/)
- index da trilha: `site/curso/trilhaN/index.html` → logo/INEMA → `../../index.html`; nav trilhas → `../trilhaM/index.html`; módulos → `modulo-N-Y.html`.
- módulo: `site/curso/trilhaN/modulo-N-Y.html` → logo → `../../index.html`; nav trilhas → `../trilhaM/index.html`; voltar → `index.html`.

---

## BLOCO A — `<head>` (idêntico em toda página; só muda `<title>`)
```html
<!DOCTYPE html>
<html lang="pt-BR" class="dark">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{{TITLE}} | Criando Skills</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = { darkMode: 'class', theme: { extend: { colors: { primary: '#FACC15', dark: { 900: '#111827', 800: '#1f2937', 700: '#374151', 600: '#4b5563' } } } } }
  </script>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
  <style>
    body { font-family: 'Inter', sans-serif; }
    .dark body { background-color: #111827; }
    .topic-explanation { display: none; }
    .topic-explanation.active { display: block; }
    html:not(.dark) body { background-color: #f8fafc; }
    html:not(.dark) .bg-dark-900 { background-color: #ffffff; }
    html:not(.dark) .bg-dark-800 { background-color: #f9fafb; }
    html:not(.dark) .bg-dark-700 { background-color: #f3f4f6; }
    html:not(.dark) .bg-dark-600 { background-color: #e5e7eb; }
    html:not(.dark) .text-neutral-100 { color: #111827; }
    html:not(.dark) .text-neutral-300 { color: #4b5563; }
    html:not(.dark) .text-neutral-400 { color: #6b7280; }
    html:not(.dark) .text-neutral-500 { color: #9ca3af; }
    html:not(.dark) .border-dark-600 { border-color: #d1d5db; }
    html:not(.dark) .border-dark-700 { border-color: #e5e7eb; }
    html:not(.dark) .text-emerald-400 { color: #059669; }
    html:not(.dark) .text-blue-400 { color: #2563eb; }
    html:not(.dark) .text-purple-400 { color: #7c3aed; }
    html:not(.dark) .text-amber-400 { color: #b45309; }
    html:not(.dark) .text-teal-400 { color: #0d9488; }
    html:not(.dark) .bg-emerald-500\/20 { background-color: rgba(5,150,105,.12); }
    html:not(.dark) .bg-blue-500\/20 { background-color: rgba(37,99,235,.12); }
    html:not(.dark) .bg-purple-500\/20 { background-color: rgba(124,58,237,.12); }
    html:not(.dark) .bg-amber-500\/20 { background-color: rgba(180,83,9,.12); }
    html:not(.dark) .bg-teal-500\/20 { background-color: rgba(13,148,136,.12); }
    html:not(.dark) [class*="bg-gradient-to"] { background-image: none !important; }
    html:not(.dark) .text-primary { color: #a16207; }
    html:not(.dark) .text-sky-400 { color: #0369a1; }
    html:not(.dark) .text-yellow-400 { color: #a16207; }
    html:not(.dark) .hover\:text-sky-300:hover { color: #0284c7; }
    html:not(.dark) .hover\:text-yellow-300:hover { color: #854d0e; }
    html:not(.dark) .bg-dark-900\/95 { background-color: rgba(255,255,255,.95); }
    .dark .border-dark-600 { border-color: #374151; }
    .dark .divide-dark-600 > :not([hidden]) ~ :not([hidden]) { border-color: #374151; }
  </style>
</head>
<body class="bg-dark-900 text-neutral-100 min-h-screen">
```

## BLOCO B — NAV (idêntico em toda página). Destaque a trilha ATIVA trocando suas classes para `text-{cor}-400 bg-{cor}-500/10` e as outras ficam `text-neutral-400 hover:text-{cor}-400 hover:bg-{cor}-500/10`.
```html
  <nav class="sticky top-0 z-50 bg-dark-900/95 backdrop-blur-sm border-b border-dark-600">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between items-center h-14">
        <div class="flex items-center space-x-4">
          <a href="../../index.html" class="flex items-center space-x-2 text-yellow-400 hover:text-yellow-300">
            <span class="text-2xl">🛠️</span><span class="font-bold text-lg hidden sm:inline">Criando Skills</span>
          </a>
          <span class="text-neutral-600">|</span>
          <a href="https://inema.club" target="_blank" class="text-sky-400 hover:text-sky-300 text-sm font-medium">INEMA.CLUB</a>
        </div>
        <div class="flex items-center space-x-1 sm:space-x-2">
          <a href="../trilha1/index.html" class="px-2 py-1.5 rounded-lg text-xs font-semibold text-neutral-400 hover:text-emerald-400 hover:bg-emerald-500/10 transition-colors"><span class="sm:hidden">T1</span><span class="hidden sm:inline">Panorama</span></a>
          <a href="../trilha2/index.html" class="px-2 py-1.5 rounded-lg text-xs font-semibold text-neutral-400 hover:text-blue-400 hover:bg-blue-500/10 transition-colors"><span class="sm:hidden">T2</span><span class="hidden sm:inline">Qualidade</span></a>
          <a href="../trilha3/index.html" class="px-2 py-1.5 rounded-lg text-xs font-semibold text-neutral-400 hover:text-purple-400 hover:bg-purple-500/10 transition-colors"><span class="sm:hidden">T3</span><span class="hidden sm:inline">Anatomia</span></a>
          <a href="../trilha4/index.html" class="px-2 py-1.5 rounded-lg text-xs font-semibold text-neutral-400 hover:text-amber-400 hover:bg-amber-500/10 transition-colors"><span class="sm:hidden">T4</span><span class="hidden sm:inline">Criar</span></a>
          <a href="../trilha5/index.html" class="px-2 py-1.5 rounded-lg text-xs font-semibold text-neutral-400 hover:text-teal-400 hover:bg-teal-500/10 transition-colors"><span class="sm:hidden">T5</span><span class="hidden sm:inline">Pensar</span></a>
          <button id="theme-toggle" class="p-2 rounded-lg bg-dark-700 hover:bg-dark-600 transition-colors ml-2">
            <svg id="theme-toggle-dark-icon" class="hidden w-5 h-5 text-neutral-300" fill="currentColor" viewBox="0 0 20 20"><path d="M17.293 13.293A8 8 0 016.707 2.707a8.001 8.001 0 1010.586 10.586z"></path></svg>
            <svg id="theme-toggle-light-icon" class="hidden w-5 h-5 text-neutral-300" fill="currentColor" viewBox="0 0 20 20"><path d="M10 2a1 1 0 011 1v1a1 1 0 11-2 0V3a1 1 0 011-1zm4 8a4 4 0 11-8 0 4 4 0 018 0zm-.464 4.95l.707.707a1 1 0 001.414-1.414l-.707-.707a1 1 0 00-1.414 1.414zm2.12-10.607a1 1 0 010 1.414l-.706.707a1 1 0 11-1.414-1.414l.707-.707a1 1 0 011.414 0zM17 11a1 1 0 100-2h-1a1 1 0 100 2h1zm-7 4a1 1 0 011 1v1a1 1 0 11-2 0v-1a1 1 0 011-1zM5.05 6.464A1 1 0 106.465 5.05l-.708-.707a1 1 0 00-1.414 1.414l.707.707zm1.414 8.486l-.707.707a1 1 0 01-1.414-1.414l.707-.707a1 1 0 011.414 1.414zM4 11a1 1 0 100-2H3a1 1 0 000 2h1z" fill-rule="evenodd" clip-rule="evenodd"></path></svg>
          </button>
        </div>
      </div>
    </div>
  </nav>
```

## BLOCO C — FOOTER + JS

### Footer (toda página)
```html
  <footer class="border-t border-dark-600 py-8 mt-12">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 text-center text-neutral-500 text-sm">
      <p>Criando Agent Skills · <a href="https://inema.club" class="text-sky-400 hover:text-sky-300">INEMA.CLUB</a> · 2026 · Dados coletados do skills.sh</p>
    </div>
  </footer>
```

### JS para INDEX da trilha (toggle de tópico + modal + tema)
```html
  <script>
    function toggleTopic(button){const i=button.closest('.topic-item');const e=i.querySelector('.topic-explanation');const c=button.closest('.bg-dark-800');c.querySelectorAll('.topic-explanation.active').forEach(x=>{if(x!==e)x.classList.remove('active')});e.classList.toggle('active');}
    function openModal(id){const m=document.getElementById(id);if(m){m.classList.remove('hidden');document.body.style.overflow='hidden';}}
    function closeModal(){document.querySelectorAll('.modal').forEach(m=>m.classList.add('hidden'));document.body.style.overflow='auto';}
    document.addEventListener('keydown',e=>{if(e.key==='Escape')closeModal();});
    const themeToggle=document.getElementById('theme-toggle'),d=document.getElementById('theme-toggle-dark-icon'),l=document.getElementById('theme-toggle-light-icon'),html=document.documentElement;
    if(localStorage.getItem('theme')==='light'){d.classList.remove('hidden');html.classList.remove('dark');}else{l.classList.remove('hidden');}
    themeToggle.addEventListener('click',()=>{d.classList.toggle('hidden');l.classList.toggle('hidden');html.classList.toggle('dark');localStorage.setItem('theme',html.classList.contains('dark')?'dark':'light');});
  </script>
</body></html>
```

### JS para MÓDULO (só tema)
```html
  <script>
    const themeToggle=document.getElementById('theme-toggle'),d=document.getElementById('theme-toggle-dark-icon'),l=document.getElementById('theme-toggle-light-icon'),html=document.documentElement;
    if(localStorage.getItem('theme')==='light'){d.classList.remove('hidden');html.classList.remove('dark');}else{l.classList.remove('hidden');}
    themeToggle.addEventListener('click',()=>{d.classList.toggle('hidden');l.classList.toggle('hidden');html.classList.toggle('dark');localStorage.setItem('theme',html.classList.contains('dark')?'dark':'light');});
  </script>
</body></html>
```

---

## ESQUELETO 1 — INDEX DA TRILHA (`site/curso/trilhaN/index.html`)
Ordem: BLOCO A + BLOCO B (trilha ativa destacada) + header + main(cards de módulo + mapa da trilha + nav prev/next) + modais (1 por módulo, com iframe) + BLOCO C(footer + JS index).

Header:
```html
  <header class="bg-gradient-to-br from-{COR}-900/30 via-dark-800 to-dark-800 py-12 border-b border-dark-600">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
      <span class="inline-block px-3 py-1 bg-{COR}-500/20 text-{COR}-400 text-xs font-semibold rounded-full mb-4">TRILHA N</span>
      <h1 class="text-3xl sm:text-4xl font-bold mb-4">{EMOJI} {TÍTULO}</h1>
      <p class="text-lg text-neutral-400 max-w-3xl">{SUBTÍTULO}</p>
      <!-- HERO SVG da trilha aqui (w-full h-auto max-w-2xl my-6) -->
      <div class="grid grid-cols-4 gap-4 mt-8 max-w-2xl"> <!-- 4 stat boxes: Módulos / Tópicos / Duração / Nível --> </div>
    </div>
  </header>
```
Card de módulo (repita por módulo; 6 tópicos cada, 3 seções por tópico):
```html
  <div class="bg-dark-800 rounded-xl border border-dark-600 mb-6">
    <div class="p-6 border-b border-dark-600">
      <div class="flex items-center justify-between mb-2"><span class="text-{COR}-400 font-bold">N.Y</span><span class="text-xs text-neutral-500">~XX min</span></div>
      <h3 class="text-2xl font-bold mb-2">{EMOJI} {TÍTULO MÓDULO}</h3>
      <p class="text-neutral-400 text-sm">{resumo}</p>
    </div>
    <div class="divide-y divide-dark-600">
      <!-- repita 6x: -->
      <div class="topic-item">
        <button onclick="toggleTopic(this)" class="w-full px-6 py-4 flex items-center space-x-3 hover:bg-dark-700/50 transition-colors text-left">
          <span class="w-6 h-6 rounded-full bg-{COR}-500/20 text-{COR}-400 text-sm font-bold flex items-center justify-center flex-shrink-0">1</span>
          <span class="text-lg">{emoji}</span>
          <div><span class="font-medium">{título tópico}</span><span class="text-neutral-500 text-sm ml-2">- {subtítulo}</span></div>
        </button>
        <div class="topic-explanation px-6 pb-4"><div class="bg-dark-700/50 rounded-lg p-4 space-y-3 ml-9">
          <div><span class="text-{COR}-400 font-semibold">O que é:</span><p class="text-neutral-300 text-sm">...</p></div>
          <div><span class="text-{COR}-400 font-semibold">Por que aprender:</span><p class="text-neutral-300 text-sm">...</p></div>
          <div><span class="text-{COR}-400 font-semibold">Conceitos-chave:</span><p class="text-neutral-300 text-sm">... · ... · ...</p></div>
        </div></div>
      </div>
    </div>
    <div class="p-4 bg-dark-700/30 flex justify-start space-x-3">
      <button onclick="openModal('modal-N-Y')" class="px-4 py-2 text-sm bg-dark-600 hover:bg-dark-500 rounded-lg transition-colors">Ver em Modal</button>
      <a href="modulo-N-Y.html" class="px-4 py-2 text-sm bg-{COR}-600 hover:bg-{COR}-500 text-white rounded-lg transition-colors">Ver Completo</a>
    </div>
  </div>
```
Mapa da trilha (depois dos cards):
```html
  <h2 class="text-2xl font-bold mb-6 mt-12">Mapa da trilha</h2>
  <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 mb-8">
    <a href="modulo-N-Y.html" class="block bg-dark-800 rounded-xl border border-dark-600 p-5 hover:border-{COR}-400 transition-colors">
      <div class="flex items-center justify-between mb-2"><span class="text-{COR}-400 font-bold text-sm">N.Y</span><span class="text-xs text-neutral-500">~XX min</span></div>
      <div class="font-semibold mb-1">{emoji} {título}</div>
      <p class="text-neutral-400 text-sm">{subtítulo PUNCHY}</p>
    </a>
  </div>
```
Nav prev/next (fim do main):
```html
  <div class="flex flex-col sm:flex-row justify-between gap-4 mt-8">
    <a href="../../index.html" class="px-6 py-3 bg-dark-700 text-neutral-300 rounded-lg font-semibold hover:bg-dark-600 transition-colors text-center">← Início</a>
    <a href="../trilha{N+1}/index.html" class="px-6 py-3 bg-{PRÓXIMA-COR}-600 text-white rounded-lg font-semibold hover:bg-{PRÓXIMA-COR}-500 transition-colors text-center">Trilha {N+1} →</a>
  </div>
```
Modal (1 por módulo, antes do footer):
```html
  <div id="modal-N-Y" class="modal hidden fixed inset-0 z-50 flex items-center justify-center p-2 sm:p-4 bg-black/80" onclick="if(event.target===this)closeModal()">
    <div class="bg-dark-800 rounded-xl w-full max-w-6xl h-[95vh] flex flex-col border border-dark-600">
      <div class="p-4 border-b border-dark-600 flex justify-between items-center flex-shrink-0">
        <div class="flex items-center space-x-3"><span class="text-{COR}-400 font-bold">N.Y</span><span class="font-semibold">{título}</span></div>
        <button onclick="closeModal()" class="text-neutral-400 hover:text-white text-2xl leading-none">&times;</button>
      </div>
      <iframe src="modulo-N-Y.html" class="flex-1 w-full rounded-b-xl"></iframe>
    </div>
  </div>
```

## ESQUELETO 2 — MÓDULO (`site/curso/trilhaN/modulo-N-Y.html`)
Ordem: BLOCO A + BLOCO B + breadcrumb + header + main(6-8 seções topico-N + SVG + resumo + nav) + BLOCO C(footer + JS módulo).

Breadcrumb:
```html
  <nav class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 py-4">
    <div class="flex items-center space-x-2 text-sm text-neutral-400">
      <a href="../../index.html" class="hover:text-{COR}-400">Início</a><span>/</span>
      <a href="index.html" class="hover:text-{COR}-400">Trilha N</a><span>/</span>
      <span class="text-{COR}-400">Módulo N.Y</span>
    </div>
  </nav>
```
Header (com 4 stat boxes: Tópicos / Minutos / Nível / Tipo):
```html
  <header class="bg-gradient-to-br from-{COR}-900/30 via-dark-800 to-dark-800 py-12 border-b border-dark-600">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
      <span class="inline-block px-3 py-1 bg-{COR}-500/20 text-{COR}-400 text-xs font-semibold rounded-full mb-4">MÓDULO N.Y</span>
      <h1 class="text-3xl sm:text-4xl font-bold mb-4">{EMOJI} {TÍTULO}</h1>
      <p class="text-lg text-neutral-400 max-w-3xl">{subtítulo}</p>
      <div class="grid grid-cols-4 gap-4 mt-8 max-w-2xl"> <!-- 4 boxes --> </div>
    </div>
  </header>
```
Seção de tópico (repita 6-8x, VARIE os componentes internos — não repita o mesmo molde):
```html
  <section id="topico-1" class="mb-16">
    <div class="flex items-center space-x-4 mb-6">
      <span class="flex items-center justify-center w-12 h-12 rounded-full bg-{COR}-500/20 text-{COR}-400 font-bold text-xl">1</span>
      <h2 class="text-2xl font-bold">{emoji} {título}</h2>
    </div>
    <p class="text-neutral-300 mb-6 leading-relaxed">...</p>
    <!-- AQUI varie: card conceito (bg-gradient-to-br from-{COR}-900/30...), grid 2col ✓/✗ (red-900/20 + {COR}-900/20),
         code box (bg-dark-800 font-mono), tip box (bg-primary/10 border-primary/40), timeline/lista numerada -->
  </section>
```
Componentes prontos para variar:
- **Grid ✓/✗**: `<div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-6">` com card `bg-red-900/20 border-red-500/30` (✗ vermelho) e card `bg-{COR}-900/20 border-{COR}-500/30` (✓ cor da trilha).
- **Code box**: `<div class="bg-dark-800 border border-dark-600 rounded-xl p-6 mb-6 font-mono text-sm"><p class="text-neutral-500 mb-3">label:</p><pre class="text-neutral-300 leading-relaxed">...</pre></div>`.
- **Tip box**: `<div class="bg-primary/10 rounded-xl border border-primary/40 p-6"><h3 class="text-lg font-semibold text-primary mb-3"><span class="mr-2">💡</span> Dica</h3><p class="text-neutral-300 text-sm">...</p></div>`.
- **Card conceito**: `<div class="bg-gradient-to-br from-{COR}-900/30 to-dark-800 rounded-xl border border-{COR}-500/30 p-6 mb-6">...`.
- **Timeline/passos**: lista de `<div class="flex items-start space-x-4">` com círculo numerado `flex-shrink-0 w-12 h-12 rounded-full bg-{COR}-500/20`.

SVG ilustrativo (≥1 por módulo, inline, no meio do conteúdo):
```html
  <svg viewBox="0 0 600 200" role="img" aria-label="{descrição}" class="w-full h-auto my-6">
    <defs><filter id="g{N}{Y}"><feGaussianBlur stdDeviation="2.5" result="b"/><feMerge><feMergeNode in="b"/><feMergeNode in="SourceGraphic"/></feMerge></filter></defs>
    <!-- formas com fill/stroke da cor da trilha (ex emerald #10b981, blue #3b82f6, purple #a855f7, amber #f59e0b, teal #14b8a6) + ciano #38bdf8; opacity baixa nos fills; filter glow nas linhas -->
  </svg>
```
Resumo + nav (fim):
```html
  <section class="mb-12">
    <div class="bg-gradient-to-br from-{COR}-900/40 via-dark-800 to-dark-800 rounded-xl border border-{COR}-500/30 p-8">
      <h2 class="text-2xl font-bold mb-6 flex items-center"><span class="mr-3">✅</span> Resumo do Módulo</h2>
      <div class="space-y-4 mb-8"> <!-- 5-6 itens: ✓ + <strong>ponto</strong> + explicação --> </div>
      <div class="bg-dark-800/50 rounded-lg p-4 mb-8"><h3 class="font-semibold text-{COR}-400 mb-2">Próximo:</h3><p class="text-neutral-300">{próximo módulo ou trilha}</p></div>
      <div class="flex flex-col sm:flex-row gap-4">
        <a href="index.html" class="flex-1 text-center px-6 py-3 bg-dark-700 text-neutral-300 rounded-lg font-semibold hover:bg-dark-600 transition-colors">← Voltar para Trilha N</a>
        <a href="{próximo}" class="flex-1 text-center px-6 py-3 bg-{COR}-600 text-white rounded-lg font-semibold hover:bg-{COR}-500 transition-colors">Próximo →</a>
      </div>
    </div>
  </section>
```

## DADOS REAIS para citar (do harvest do skills.sh — use números exatos)
- Catálogo: **39.366 skills**, **5.075 repos fonte**, **53,9M instalações somadas**, 16 grupos.
- Lei de potência: 60,2% têm <100 installs; 30,8% entre 100-999; 7,7% entre 1k-9,9k; 1,1% entre 10k-99k; só **0,3% (131 skills)** têm 100k+. As **top 100 = 43,7%** de todos os installs.
- TOP geral: find-skills 1.802.925 (vercel-labs/skills) · frontend-design 488.299 (anthropics/skills) · vercel-react-best-practices 443.261 (vercel-labs/agent-skills) · microsoft-foundry 360.755 · azure-ai 358.744 · web-design-guidelines 358.627 (vercel-labs/agent-skills).
- Grupos por volume de instalação (count / installs): AI/LLM/Agents 12.693 / 12,9M · Web&Frontend 4.694 / 4,5M · DevOps&Cloud 907 / 8,3M · Dev Tooling&Code 796 / 4,4M · Marketing&SEO 582 / 2,3M · Media&Creative 550 / 1,85M · Docs&Content 364 / 1,49M · Backend&APIs 2.685 / 1,38M · Automation&Workflows 336 / 1,03M · Data&Databases 1.385 / 0,79M · Security 512 / 0,70M · Testing&QA 1.339 / 0,60M · Office&Files 249 / 0,24M · Finance&Business 310 / 0,21M · Productivity&PM 92 / 0,21M.
- Exemplos por grupo (nome / installs / fonte):
  - Web: frontend-design 488k anthropics · vercel-react-best-practices 443k vercel-labs · web-design-guidelines 358k vercel-labs.
  - Data: supabase-postgres-best-practices 203k supabase · supabase 99k · neon-postgres 38k neondatabase.
  - AI/Agents: agent-browser 332k vercel-labs · skill-creator 246k anthropics · vercel-composition-patterns 195k vercel-labs.
  - Testing: test-driven-development 107k obra/superpowers · playwright-best-practices 45k.
  - DevOps: microsoft-foundry/azure-ai/azure-deploy/azure-diagnostics/azure-prepare ~358-360k microsoft/azure-skills.
  - Marketing: marketing-psychology 84k · programmatic-seo · ab-test-setup 52k (coreyhaines31/marketingskills).
  - Office: lark-slides 139k larksuite/cli · slidev antfu/skills.
  - Finance: stripe-best-practices stripe/ai.
- Anatomia (canônico Anthropic skill-creator): SKILL.md = frontmatter YAML (name + description obrigatórios) + corpo Markdown. Progressive disclosure 3 níveis: (1) metadata name+description ~100 palavras sempre no contexto; (2) corpo do SKILL.md <500 linhas quando dispara; (3) bundled resources (scripts/ references/ assets/) sob demanda. description é o gatilho — deve dizer O QUE faz E QUANDO usar, e ser um pouco "pushy" (Claude tende a subdisparar). Imperativo, explique o PORQUÊ em vez de MUSTs em maiúscula.
- Loop de criação: capturar intent → escrever draft → 2-3 test prompts realistas → rodar com-skill vs baseline → avaliar (qualitativo + evals quantitativos) → generalizar do feedback, manter enxuto, explicar o porquê, extrair scripts repetidos → repetir → otimizar description (queries should-trigger / should-not-trigger, near-misses) → empacotar.
```
