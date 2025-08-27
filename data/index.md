---
title: "Jeux de données"
layout: single
permalink: /data/
classes: wide
---

<!-- ===== Onglets lieux (tu pourras en ajouter d'autres plus tard) ===== -->
<nav class="tabs">
  <a class="tab active" href="#matapedia">Matapédia</a>
  <!-- Exemples futurs :
  <a class="tab" href="#rimouski">Rimouski</a>
  <a class="tab" href="#chaudiere">Chaudière</a>
  -->
</nav>

<section id="matapedia" class="tab-pane active">

### Matapédia — aperçu

<!-- GIF hébergé dans un autre repo GitHub public -->
<div class="media-row">
  <figure>
    <img
      src="https://raw.githubusercontent.com/OWNER/REPO/BRANCH/path/to/matapedia-preview.gif"
      alt="Aperçu caméra — Matapédia"
      loading="lazy"
    />
    <figcaption>GIF d’aperçu (source : autre dépôt public GitHub)</figcaption>
  </figure>
</div>

<!-- Carte Leaflet (statique, sans clé) -->
<div id="map-matapedia" class="map"></div>

<script>
  // Leaflet carte simple
  document.addEventListener("DOMContentLoaded", function () {
    if (!window.L) return;
    const map = L.map('map-matapedia', { scrollWheelZoom: false }).setView([48.35349918652086, -67.22255497464408], 12);
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      maxZoom: 18,
      attribution: '&copy; OpenStreetMap'
    }).addTo(map);
    L.marker([48.35349918652086, -67.22255497464408]).addTo(map).bindPopup('Matapédia — site test');
  });
</script>

#### Téléchargements

<p class="note">Chaque cellule pointe vers un CSV hébergé sur un autre dépôt GitHub public (utilise de préférence <code>https://raw.githubusercontent.com/...</code>).</p>

<table class="dataset-table">
  <thead>
    <tr>
      <th>Jeu de données</th>
      <th>Staging</th>
      <th>Production</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Brut</strong></td>
      <td><a href="https://raw.githubusercontent.com/OWNER-STAGING/REPO-STAGING/BRANCH/data/matapedia_brut.csv">CSV brut (staging)</a></td>
      <td><a href="https://raw.githubusercontent.com/OWNER-PROD/REPO-PROD/BRANCH/data/matapedia_brut.csv">CSV brut (prod)</a></td>
    </tr>
    <tr>
      <td><strong>Vue posttraitée</strong></td>
      <td><a href="https://raw.githubusercontent.com/OWNER-STAGING/REPO-STAGING/BRANCH/data/matapedia_vue_posttraitee.csv">CSV vue posttraitée (staging)</a></td>
      <td><a href="https://raw.githubusercontent.com/OWNER-PROD/REPO-PROD/BRANCH/data/matapedia_vue_posttraitee.csv">CSV vue posttraitée (prod)</a></td>
    </tr>
    <tr>
      <td><strong>Débit traité</strong></td>
      <td><a href="https://raw.githubusercontent.com/OWNER-STAGING/REPO-STAGING/BRANCH/data/matapedia_debit_traite.csv">CSV débit traité (staging)</a></td>
      <td><a href="https://raw.githubusercontent.com/OWNER-PROD/REPO-PROD/BRANCH/data/matapedia_debit_traite.csv">CSV débit traité (prod)</a></td>
    </tr>
  </tbody>
</table>

</section>

<!-- ===== Styles légers ===== -->
<style>
/* Onglets */
.tabs { display:flex; gap:.5rem; margin: .5rem 0 1rem; border-bottom:1px solid #e8e8e8; }
.tab {
  padding:.5rem .9rem; border:1px solid #e8e8e8; border-bottom:none; border-radius:10px 10px 0 0;
  text-decoration:none; background:#fafafa; color:inherit;
}
.tab.active { background:#fff; font-weight:600; }

/* Panneaux */
.tab-pane { display:none; }
.tab-pane.active { display:block; }

/* Media & carte */
.media-row { margin: .6rem 0 1rem; }
.media-row figure { margin:0; }
.media-row img {
  display:block; max-width:100%; height:auto; border-radius:14px; box-shadow:0 8px 20px rgba(0,0,0,.06);
}
.map { width:100%; height:340px; border-radius:14px; margin: .8rem 0 1.2rem; box-shadow:0 8px 20px rgba(0,0,0,.06); }

/* Tableau datasets */
.dataset-table { width:100%; border-collapse:collapse; }
.dataset-table th, .dataset-table td { padding:.6rem .7rem; border-top:1px solid #eee; }
.dataset-table thead th { background:#f7f9fb; text-align:left; }
.dataset-table a { text-decoration:none; }
</style>

<!-- ===== JS onglets (prêt pour plusieurs lieux) ===== -->
<script>
document.addEventListener('DOMContentLoaded', () => {
  const tabs = document.querySelectorAll('.tabs .tab');
  const panes = document.querySelectorAll('.tab-pane');
  tabs.forEach(tab => {
    tab.addEventListener('click', (e) => {
      e.preventDefault();
      const target = tab.getAttribute('href');
      tabs.forEach(t => t.classList.remove('active'));
      panes.forEach(p => p.classList.remove('active'));
      tab.classList.add('active');
      document.querySelector(target).classList.add('active');
      history.replaceState(null, '', target); // hash propre
    });
  });
  // activer via hash si présent
  if (location.hash) {
    const link = document.querySelector(`.tabs .tab[href="${location.hash}"]`);
    if (link) link.click();
  }
});
</script>

<!-- ===== Leaflet CDN (cartes) ===== -->
<link
  rel="stylesheet"
  href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
  integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY="
  crossorigin=""
/>
<script
  src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"
  integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo="
  crossorigin=""
></script>
