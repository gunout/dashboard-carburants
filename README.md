<div align="center">

# ⛽ Dashboard Carburants France

**Dashboard interactif des prix des carburants en France — Données officielles en temps réel**

[![Données](https://img.shields.io/badge/Données-data.economie.gouv.fr-blue)](https://data.economie.gouv.fr)
[![API](https://img.shields.io/badge/API-Opendatasoft%20v2.1-green)](https://data.economie.gouv.fr/api/explore/v2.1)
[![Licence](https://img.shields.io/badge/Licence-MIT-yellow)](LICENSE)
[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Live-brightgreen)](https://gunout.github.io/dashboard-carburants/)
[![Stations](https://img.shields.io/badge/Stations-9%20800%2B-orange)]()
[![Mise à jour](https://img.shields.io/badge/Mise%20à%20jour-10%20min-red)]()

[🚀 Voir le dashboard](https://gunout.github.io/dashboard-carburants/) · [📊 Source des données](https://data.economie.gouv.fr) · [🐛 Signaler un bug](https://github.com/gunout/dashboard-carburants/issues)

</div>

---

## 📋 Table des matières

- [À propos](#-à-propos)
- [Fonctionnalités](#-fonctionnalités)
- [Sources de données](#-sources-de-données)
- [Captures d'écran](#-captures-décran)
- [Installation](#-installation)
- [Utilisation](#-utilisation)
- [Technologies](#-technologies)
- [Structure du projet](#-structure-du-projet)
- [Contribution](#-contribution)
- [Licence](#-licence)

---

## 🎯 À propos

Ce dashboard permet de **visualiser en temps réel les prix des carburants** dans les **9 800+ stations-service** de France métropolitaine et d'Outre-mer. Il utilise les données officielles du Ministère de l'Économie, des Finances et de la Souveraineté industrielle et énergétique, publiées sur la plateforme **data.economie.gouv.fr**.

Les prix sont mis à jour **toutes les 10 minutes** par les stations elles-mêmes, conformément à la réglementation française.

### 🎨 Thème Bleu Blanc Rouge

Le dashboard arbore les couleurs de la République française :
- 🔵 **Bleu** `#0055A4` — Confiance, données officielles
- ⚪ **Blanc** `#FFFFFF` — Clarté, transparence
- 🔴 **Rouge** `#EF4135` — Urgence, alertes prix

---

## ✨ Fonctionnalités

### 🗺️ Cartographie interactive
- **9 800+ stations** affichées sur une carte Leaflet
- **3 fonds de carte** : Standard (OSM), Sombre (CARTO), Satellite (Esri)
- **Clustering intelligent** : regroupement automatique des stations proches
- **Code couleur par prix** : vert (pas cher), jaune (moyen), rouge (cher)

### 🔍 Filtres puissants
| Filtre | Description |
|---|---|
| **Recherche texte** | Ville, code postal ou adresse |
| **Carburant** | Gazole, SP95, SP98, E10, E85, GPLc |
| **Département** | Liste dynamique des 96 départements |
| **Prix maximum** | Seuil configurable en €/L |
| **Services** | Boutique, lavage, gonflage, toilettes |

### 📊 Statistiques en temps réel
- Nombre de stations filtrées
- Prix moyen, minimum et maximum
- Graphique de répartition par carburant
- Histogramme de distribution des prix

### ⚡ Performance
- **Pagination automatique** : 100 enregistrements par requête
- **Chargement progressif** avec barre de progression
- **Clustering** pour afficher des milliers de marqueurs sans ralentissement
- **Filtres en temps réel** (debounce 300 ms)

---

## 📊 Sources de données

### API principale

GET   
    
    https://data.economie.gouv.fr/api/explore/v2.1/catalog/datasets/


| Paramètre | Valeur | Description |
|---|---|---|
| `limit` | 100 | Enregistrements par requête |
| `offset` | variable | Pagination |
| `where` | ODSQL | Filtres optionnels |
| `order_by` | `gazole_prix` | Tri optionnel |

### Champs utilisés

| Champ | Type | Description |
|---|---|---|
| `id` | string | Identifiant de la station |
| `geom` | geo_point_2d | Coordonnées GPS (lat, lon) |
| `cp` | string | Code postal |
| `ville` | string | Nom de la commune |
| `adresse` | string | Adresse complète |
| `gazole_prix` | float | Prix du Gazole (€/L) |
| `sp95_prix` | float | Prix du SP95 (€/L) |
| `sp98_prix` | float | Prix du SP98 (€/L) |
| `e10_prix` | float | Prix du E10 (€/L) |
| `e85_prix` | float | Prix du E85 (€/L) |
| `gplc_prix` | float | Prix du GPLc (€/L) |
| `services` | array | Services disponibles |

### Documentation officielle

- 📖 [API Opendatasoft Explore v2.1](https://help.opendatasoft.com/apis/ods-explore-v2/)
- 📊 [Dataset sur data.economie.gouv.fr](https://data.economie.gouv.fr/explore/dataset/prix-des-carburants-en-france-flux-instantane-v2/)
- 🏛️ [Site officiel prix-carburants.gouv.fr](https://www.prix-carburants.gouv.fr/)

---

## 🖼️ Captures d'écran

<img width="1800" height="802" alt="Screenshot 2026-09-17 at 08-59-11 🇫🇷 Dashboard Carburants France — Prix en temps réel" src="https://github.com/user-attachments/assets/61a7bff6-a1a0-4a48-bc9c-c4bb2e2bd322" />
<img width="1800" height="802" alt="Screenshot 2026-09-17 at 09-00-05 🇫🇷 Dashboard Carburants France — Prix en temps réel" src="https://github.com/user-attachments/assets/8872b574-22b5-4f03-af47-2655f8541dbb" />



---


### Vue carte
```text
╔══════════════════════════════════════════════════════════════════════════════════════════════╗
║  ▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬  BLEU  ▬▬▬▬▬▬▬▬  BLANC  ▬▬▬▬▬▬▬▬  ROUGE  ▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬     ║
║                                                                                              ║
║  ⛽ Dashboard Carburants France                    Actualisé : 17/09/2026 14:32    ● LIVE    ║
║  🇫🇷 Données officielles · data.economie.gouv.fr              Source : prix-des-carburants…   ║
║                                                                                              ║
╠═══════════════════════════════╦══════════════════════════════════════════════════════════════╣
║  🔍 RECHERCHE                 ║                                                              ║
║  ┌─────────────────────────┐  ║   ┌──────────┐  ┌──────────┐  ┌──────────┐                   ║
║  │ Ville, code postal…     │  ║   │🗺️Standard│  │🌙 Sombre │ │🛰️Satellite│                 ║
║  └─────────────────────────┘  ║   └──────────┘  └──────────┘  └──────────┘                   ║
║                               ║                                                              ║
║  ⛽ CARBURANT                  ║                                                             ║
║  ┌─────────────────────────┐  ║                                                              ║
║  │ Tous les carburants  ▾  │  ║                    🗺️  CARTE INTERACTIVE                     ║
║  └─────────────────────────┘  ║                                                              ║
║                               ║        🔵 🔵 🔴 🔵 🟡 🔴 🔵 🔵 🟡 🔵 🟢 🔴 🔵 🟡      ║
║  📍 DÉPARTEMENT                ║      🔵 🟡 🔴 🔵 🟢 🟡 🔵 🔴 🔵 🟡 🟢 🔵 🔴 🔵 🟡    ║
║  ┌─────────────────────────┐  ║    🔴 🔵 🟢 🟡 🔵 🔴 🔵 🟡 🟢 🔵 🔴 🔵 🟡 🔵 🟢       ║
║  │ Tous les départements ▾ │  ║      🟡 🔵 🔴 🔵 🟢 🟡 🔵 🔴 🔵 🟡 🟢 🔵 🔴 🔵        ║
║  └─────────────────────────┘  ║        🟢 🟡 🔵 🔴 🔵 🟡 🟢 🔵 🔴 🔵 🟡 🔵             ║
║                               ║                    🔵 🔴 🔵 🟡 🟢 🔵 🔴                   ║
║  💰 PRIX MAXIMUM (€/L)         ║                                                             ║
║  ┌─────────────────────────┐  ║                                                              ║
║  │ Ex: 1.80                │  ║                    ┌───────────────────────┐                 ║
║  └─────────────────────────┘  ║                    │    9 805              │                 ║
║                               ║                    │  stations affichées   │                 ║
║ 🏪 SERVICES                  ║                     │                      │                  ║
║  ┌─────────────────────────┐  ║                    │ 💰 Pas cher  →  Cher  │                 ║
║  │ Tous                 ▾  │  ║                    │ ▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬    │                 ║
║  └─────────────────────────┘  ║                    │ 🟢   🟡   🔴        │                  ║
║                               ║                    └─────────────────────  ┘                 ║
║  ┌───────────┬───────────┐    ║                                                              ║
║  │ STATIONS  │ PRIX MOY. │    ║                                                              ║
║  │  9 805    │  1.724 €  │    ║                                                              ║
║  │  (bleu)   │           │    ║                                                              ║
║  ├───────────┼───────────┤    ║                                                              ║
║  │ PRIX MIN  │ PRIX MAX  │    ║                                                              ║
║  │  1.489 €  │  2.150 €  │    ║                                                              ║
║  │  (vert)   │  (rouge)  │    ║                                                              ║
║  └───────────┴───────────┘    ║                                                              ║
║                               ║                                                              ║
║  📊 RÉPARTITION PAR CARBURANT ║                                                              ║
║  ┌─────────────────────────┐  ║                                                              ║
║  │ ████████████ Gazole     │  ║                                                              ║
║  │ ██████████ SP95         │  ║                                                              ║
║  │ ████████ SP98           │  ║                                                              ║
║  │ ██████ E10              │  ║                                                              ║
║  │ ██ E85                  │  ║                                                              ║
║  │ █ GPLc                  │  ║                                                              ║
║  └─────────────────────────┘  ║                                                              ║
║                               ║                                                              ║
║ 📈 DISTRIBUTION DES PRIX      ║                                                              ║
║  ┌─────────────────────────┐  ║                                                              ║
║  │      ╱╲                 │  ║                                                              ║
║  │    ╱    ╲               │  ║                                                              ║
║  │  ╱        ╲___          │  ║                                                              ║
║  │╱              ╲___╱     │  ║                                                              ║
║  └─────────────────────────┘  ║                                                              ║
║                               ║                                                              ║
║  ┌─────────────────────────┐  ║                                                              ║
║  │Réinitialiser les filtres│  ║                                                              ║
║  └─────────────────────────┘  ║                                                              ║
╚═══════════════════════════════╩══════════════════════════════════════════════════════════════╝
```

---

## 🚀 Installation

### Option 1 : GitHub Pages (recommandé)

1. **Forkez** ce dépôt
2. Allez dans **Settings** → **Pages**
3. Source : **Deploy from a branch** → `main` → `/ (root)`
4. Accédez à `https://VOTRE-PSEUDO.github.io/dashboard-carburants/`

### Option 2 : En local

```bash
# Cloner le dépôt
git clone https://github.com/gunout/dashboard-carburants.git
cd dashboard-carburants

# Lancer un serveur local
python3 -m http.server 8000
# ou
npx serve .

# Ouvrir http://localhost:8000

```
Aucune installation de dépendances n'est nécessaire : le dashboard est 100 % statique (HTML/CSS/JS) et utilise des CDN pour Leaflet et Chart.js.

📖 Utilisation
🔍 Rechercher une station

    Tapez une ville (ex. Lyon), un code postal (ex. 69001) ou une adresse dans le champ de recherche

    Les marqueurs se filtrent automatiquement

    Cliquez sur un marqueur pour voir les prix de tous les carburants

⛽ Filtrer par carburant

    Sélectionnez un carburant dans le menu déroulant

    La carte se met à jour avec le code couleur correspondant

    Les statistiques (moyenne, min, max) se recalculent

📍 Filtrer par département

    Choisissez un département (ex. 69 pour le Rhône)

    Seules les stations de ce département s'affichent

💰 Trouver les stations les moins chères

    Sélectionnez un carburant (ex. Gazole)

    Les stations avec les prix les plus bas apparaissent en vert

    Cliquez sur une station verte pour voir son prix exact

🗺️ Changer de fond de carte

Utilisez les boutons en haut à gauche de la carte :

    🗺️ Standard : OpenStreetMap (routes, villes, labels)

    🌙 Sombre : CARTO Dark Matter (adapté au thème sombre)

    🛰️ Satellite : Esri World Imagery (vue aérienne)

🛠️ Technologies
Technologie	Version	Usage
HTML5	—	Structure
CSS3	—	Design responsive, thème Bleu Blanc Rouge
JavaScript	ES2020+	Logique, fetch API
Leaflet	1.9.4	Cartographie interactive
Leaflet.markercluster	1.5.3	Clustering de marqueurs
Chart.js	4.4.0	Graphiques statistiques
Opendatasoft API	v2.1	Source de données
Pourquoi ces choix ?

    Leaflet : bibliothèque cartographique légère (42 KB), open source, sans clé API

    OpenStreetMap : fond de carte gratuit, collaboratif, sans limite d'usage

    Chart.js : graphiques simples et performants, adaptés au thème sombre

    Opendatasoft : API REST standardisée, CORS activé, données officielles

📁 Structure du projet


    dashboard-carburants/
    ├── index.html          # Dashboard complet (fichier unique)
    ├── README.md           # Documentation (ce fichier)
    └── LICENSE             # Licence MIT

Le projet est volontairement mono-fichier : tout le code (HTML, CSS, JS) est dans index.html pour faciliter le déploiement et la maintenance.
🤝 Contribution

Les contributions sont les bienvenues ! Voici comment procéder :

    Forkez le projet

    Créez une branche (git checkout -b feature/amelioration)

    Committez vos changements (git commit -m 'Ajout fonctionnalité X')

    Pushez (git push origin feature/amelioration)

    Ouvrez une Pull Request

Idées d'amélioration

    □

    Ajouter un mode comparaison entre deux carburants
    □

    Intégrer les prix historiques (évolution sur 30 jours)
    □

    Ajouter un export CSV des stations filtrées
    □

    Implémenter un calculateur de plein (coût pour X litres)
    □

    Ajouter une API de notification pour les baisses de prix
    □

    Support du mode clair (light theme)

📄 Licence

Ce projet est sous licence MIT. Voir le fichier LICENSE pour plus de détails.
🙏 Remerciements

    Ministère de l'Économie pour la publication des données ouvertes

    Opendatasoft pour l'infrastructure API

    OpenStreetMap et CARTO pour les fonds de carte

    Leaflet et Chart.js pour les bibliothèques open source

    La communauté open data française

---


<div align="center">

### 🇫🇷 Gunout · 2026

![Made in France](https://img.shields.io/badge/Made_in-France-002395?style=flat-square&labelColor=FFFFFF&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA5MDAgNjAwIj48cmVjdCB3aWR0aD0iOTAwIiBoZWlnaHQ9IjYwMCIgZmlsbD0iIzAwMjM5NSIvPjxyZWN0IHdpZHRoPSI5MDAiIGhlaWdodD0iNDAwIiB5PSIxMDAiIGZpbGw9IiNmZmYiLz48cmVjdCB3aWR0aD0iOTAwIiBoZWlnaHQ9IjIwMCIgeT0iNDAwIiBmaWxsPSIjZWQyOTM5Ii8+PC9zdmc+)
![GitHub](https://img.shields.io/badge/GitHub-gunout-181717?style=flat-square&logo=github&logoColor=white)
![Year](https://img.shields.io/badge/2026-ED2939?style=flat-square&labelColor=FFFFFF)

<sub>© 2026 <strong>gunout</strong> — Tous droits réservés.</sub>

</div>
--- 

