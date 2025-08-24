---
layout: home
title: "Derniers résultats"
excerpt: "Site auto-déployé avec Jekyll + Minimal Mistakes"
---

Bienvenue 👋  
Ce site publie automatiquement les dernières données.

- Données CSV : [`/data/mesures.csv`]({{ site.baseurl }}/data/mesures.csv)
- Exemple de graphique et tableau ci-dessous (lecture du CSV côté navigateur).

<div id="plot" style="height:360px;"></div>
<table id="tbl" class="table table-sm"></table>

<script>
// Petit viewer CSV (vanilla JS) + trace simple (sans lib externe)
async function run() {
  const res = await fetch('{{ site.baseurl }}/data/mesures.csv');
  const text = await res.text();
  const [head, ...rows] = text.trim().split('\n').map(l => l.split(','));
  const thead = `<thead><tr>${head.map(h=>`<th>${h}</th>`).join('')}</tr></thead>`;
  const tbody = `<tbody>${
    rows.map(r=>`<tr>${r.map(c=>`<td>${c}</td>`).join('')}</tr>`).join('')
  }</tbody>`;
  document.getElementById('tbl').innerHTML = thead + tbody;

  // Micro-graphique HTML (sans lib): on trace la 2e colonne comme sparkline
  const y = rows.map(r => parseFloat(r[1]));
  const w = 600, h = 120, max = Math.max(...y), min = Math.min(...y);
  const pts = y.map((v,i)=>{
    const x = Math.round(i*(w-10)/(y.length-1))+5;
    const yy = h-5 - Math.round((v-min)*(h-10)/(max-min || 1));
    return `${x},${yy}`;
  }).join(' ');
  document.getElementById('plot').innerHTML =
    `<svg width="${w}" height="${h}"><polyline points="${pts}" fill="none" stroke="currentColor" stroke-width="2"/></svg>`;
}
run();
</script>
