---
layout: home
title: "Rivéo"
excerpt: "Suivi des rivières par caméra — publication ouverte des jeux de données"


permalink: /
header:
  overlay_color: "#000"
  overlay_filter: "0.45"
  overlay_image: /assets/images/logo.png 
  actions:
    - label: "Jeux de données"
      url: "{{ site.baseurl }}/data/"
    - label: "Documentation"
      url: "{{ site.baseurl }}/docs/"
excerpt: "Rivéo observe, calcule et publie automatiquement des indicateurs hydrologiques à partir de caméras fixes — les résultats sont disponibles en CSV/JSON et visualisables en ligne."
---
## À propos

**Rivéo** est une application de **suivi des rivières par caméra**.  
Notre objectif : fournir des **mesures continues, traçables et accessibles** pour la recherche, la sécurité civile et la gestion de l’eau.

Ce site GitHub Pages sert de **vitrine** et de **catalogue de données** :  
- publication automatique des **jeux de données** produits par le moteur (CSV / JSON) ;
- **visualisations** légères côté navigateur ;
- **documentation** d’installation, de calibration et d’utilisation.

## Comment ça marche

1. **Acquisition** — une caméra fixe capture des images/vidéos d’un tronçon de rivière.  
2. **Analyse** — le moteur Rivéo détecte les repères, estime **niveaux** et **vitesses** (ex. LSPIV) et applique des contrôles qualité.  
3. **Publication** — les résultats sont exportés en **CSV/JSON** et **publiés ici** avec une horodatation et des métadonnées.

---

Écris-nous : **riveo@USherbrooke.ca** 