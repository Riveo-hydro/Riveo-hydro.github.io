---
title: "Jeux de données"
layout: single
permalink: /data/
classes: wide
---

<!-- ===== Onglets lieux ===== -->
<nav class="tabs">
  <a class="tab active" href="#matapedia">Matapédia</a>
  <!-- futurs onglets :
  <a class="tab" href="#rimouski">Rimouski</a>
  <a class="tab" href="#chaudiere">Chaudière</a>
  -->
</nav>

<section id="matapedia" class="tab-pane active">
  <h3>Matapédia</h3>

  <!-- GIF hébergé dans un autre repo GitHub public -->
  <div class="media-row">
    <figure>
      <img
        src="https://raw.githubusercontent.com/OWNER/REPO/BRANCH/path/to/matapedia-preview.gif"
        alt="Aperçu caméra — Matapédia"
        loading="lazy"
      />
      <figcaption>GIF d’aperçu de la rivière</figcaption>
    </figure>
  </div>

  <!-- Carte Leaflet -->
  <div id="map-matapedia" class="map"></div>

  <script>
    document.addEventListener("DOMContentLoaded", function () {
      if (!window.L) return;
      const map = L.map('map-matapedia', { scrollWheelZoom: false }).setView([48.35349918652086, -67.22255497464408], 8);
      L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
        maxZoom: 18,
        attribution: '&copy; OpenStreetMap'
      }).addTo(map);
      L.marker([48.35349918652086, -67.22255497464408]).addTo(map).bindPopup('Matapédia — site test');
    });
  </script>

  <h4>Galerie</h4>
  <div class="gallery">
    <figure>
      <img src="https://raw.githubusercontent.com/Riveo-hydro/Publication/refs/heads/main/Colvert/Prod/SIM1/images/latest.png" alt="Rivière Matapédia - Dernière prise">
      <figcaption>Dernière prise</figcaption>
    </figure>
    <figure>
      <img src="https://raw.githubusercontent.com/Riveo-hydro/Publication/refs/heads/main/Colvert/Prod/SIM1/images/2h.png" alt="Rivière Matapédia - 2 h">
      <figcaption>2 h</figcaption>
    </figure>
    <figure>
      <img src="https://raw.githubusercontent.com/Riveo-hydro/Publication/refs/heads/main/Colvert/Prod/SIM1/images/5h.png" alt="Rivière Matapédia - 5 h">
      <figcaption>5 h</figcaption>
    </figure>
    <figure>
      <img src="https://raw.githubusercontent.com/Riveo-hydro/Publication/refs/heads/main/Colvert/Prod/SIM1/images/10h.png" alt="Rivière Matapédia - 10 h">
      <figcaption>10 h</figcaption>
    </figure>
    <figure>
      <img src="https://raw.githubusercontent.com/Riveo-hydro/Publication/refs/heads/main/Colvert/Prod/SIM1/images/24h.png" alt="Rivière Matapédia - 24 h">
      <figcaption>24 h</figcaption>
    </figure>
    <figure>
      <img src="https://raw.githubusercontent.com/Riveo-hydro/Publication/refs/heads/main/Colvert/Prod/SIM1/images/48h.png" alt="Rivière Matapédia - 48 h">
      <figcaption>48 h</figcaption>
    </figure>
  </div>

  <h4>Téléchargements</h4>

  <p class="note">Chaque cellule pointe vers un CSV hébergé sur le dépot de publication.</p>

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
        <td><a href="https://raw.githubusercontent.com/Riveo-hydro/Publication/main/Colvert/Staging/brut.csv">CSV brut (staging)</a></td>
    <td><span class="btn is-disabled" aria-disabled="true" title="Bientôt disponible">CSV brut (prod)</span></td>
    </tr>
    <tr>
        <td><strong>Vue posttraitée</strong></td>
        <td><a href="https://raw.githubusercontent.com/Riveo-hydro/Publication/main/Colvert/Staging/mesures_agregees.csv">CSV vue posttraitée (staging)</a></td>
        <td><span class="btn is-disabled" aria-disabled="true" title="Bientôt disponible">CSV vue posttraitée (prod)</span></td>
    </tr>
    <tr>
        <td><strong>Débit traité</strong></td>
        <td><span class="btn is-disabled" aria-disabled="true" title="Bientôt disponible">CSV débit traité (staging)</span></td>
        <td><span class="btn is-disabled" aria-disabled="true" title="Bientôt disponible">CSV débit traité (prod)</span></td>
      </tr>
    </tbody>
  </table>
</section>

<!-- ===== Styles légers ===== -->
<style>
/* Onglets */
.tabs { display:flex; gap:.5rem; margin:.5rem 0 1rem; border-bottom:1px solid #e8e8e8; }
.tab {
  padding:.5rem .9rem; border:1px solid #e8e8e8; border-bottom:none; border-radius:10px 10px 0 0;
  text-decoration:none; background:#fafafa; color:inherit;
}
.tab.active { background:#fff; font-weight:600; }

/* Panneaux */
.tab-pane { display:none; }
.tab-pane.active { display:block; }

/* Media & carte */
.media-row { margin:.6rem 0 1rem; }
.media-row figure { margin:0; }
.media-row img {
  display:block; max-width:100%; height:auto; border-radius:14px; box-shadow:0 8px 20px rgba(0,0,0,.06);
}
.map { width:100%; height:340px; border-radius:14px; margin:.8rem 0 1.2rem; box-shadow:0 8px 20px rgba(0,0,0,.06); }

/* Galerie */
.gallery {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
  margin: 1.2rem 0;
}

@media (max-width: 900px) {
  .gallery {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 600px) {
    .gallery {
      grid-template-columns: 1fr;
    }
}

.gallery figure {
  position: flex !important;
  flex-direction: column !important;
  margin: 0 !important;
  border-radius: 14px;
  overflow: hidden;
  box-shadow: 0 6px 14px rgba(0,0,0,0.08);
  background: #fff;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.gallery figure:hover {
  transform: translateY(-4px);
  box-shadow: 0 10px 20 px rgba(0,0,0,0.12);
}

.gallery img {
  width: 100% !important;
  aspect-ratio: 16 / 9;
  object-fit: cover;
  display: block;
}

.gallery figcaption {
    display: block !important;
    visibility: visible !important;
    opacity: 1 !important;
    position: relative !important;
    padding: 0.5rem 0.7rem;
    font-size: 0.9rem;
    color: #555;
    background: #fafafa;
    text-align: center;
    border-top: 1px solid #eee;
}

/* Tableau datasets */
.dataset-table { width:100%; border-collapse:collapse; }
.dataset-table th, .dataset-table td { padding:.6rem .7rem; border-top:1px solid #eee; }
.dataset-table thead th { background:#f7f9fb; text-align:left; }
.dataset-table a { text-decoration:none; }
</style>

<!-- ===== JS onglets ===== -->
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
      history.replaceState(null, '', target);
    });
  });
  if (location.hash) {
    const link = document.querySelector(`.tabs .tab[href="${location.hash}"]`);
    if (link) link.click();
  }
});
</script>

<!-- ===== Leaflet CDN ===== -->
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
