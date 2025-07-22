<h1 align="center">Jedha's ML Engineer Certificate</h1>
<h2 align="center">Bloc 1: Build & Manage a Data Infrastructure</h2>

<p align="center"><strong>Case Study:</strong></p>
<p align="center">Data Collection & Management – <em>Plan Your Trip with Kayak</em> 🧳</p>
<br>

---

### 🏢 Contexte de l'entreprise

**Kayak** est un moteur de recherche de voyages fondé en 2004. Il permet aux utilisateurs de comparer des offres (vols, hôtels, voitures, etc.) pour organiser leurs voyages au meilleur prix.

Depuis son rachat par **Booking Holdings**, Kayak est intégré dans un écosystème avec :
- Booking.com  
- Priceline  
- Agoda  
- OpenTable  
- Rentalcars.com

Avec plus de **300 M$ de revenus par an**, Kayak est une référence mondiale dans la planification de voyages.

---

### 🎯 Objectif du projet

L’équipe marketing de Kayak a révélé deux constats clés :
- **70 % des utilisateurs** souhaitent plus d’infos pratiques sur leur destination.
- Les utilisateurs font davantage confiance à des données produites par Kayak.

> L’objectif est donc de construire une **infrastructure de données** permettant de recommander automatiquement les **meilleures destinations françaises** et **meilleurs hôtels**, selon :
- la **météo des 7 prochains jours**
- la **qualité des hôtels** (notes, localisation, description)

---

### 📦 Données utilisées

- **35 villes françaises** issues de _OneWeekIn.com_
- **Coordonnées GPS** via l’API **Nominatim (OpenStreetMap)**  
- **Données météo** via l’API **OpenWeatherMap** (One Call 3.0)
- **Données hôtelières** extraites via **scraping de Booking.com** :
  - Nom de l’hôtel
  - Lien Booking
  - Coordonnées (latitude, longitude)
  - Note moyenne
  - Description

> ⚠️ **Booking.com interdit le scraping dans ses conditions d'utilisation.**  
> Le scraping a été réalisé à des fins **strictement pédagogiques et non commerciales**.  
> Aucun contenu sensible ni volumineux provenant de Booking.com n’est publié dans ce dépôt.

---

### ⚙️ Pipeline ETL

#### 🔹 **EXTRACT**
- Coordonnées GPS via **Nominatim**
- Prévisions météo (7 jours) via **OpenWeatherMap**
- Informations hôtelières via **Scrapy**

#### 🔹 **TRANSFORM**
- Calcul d’un **indice de météo agréable**
- Nettoyage des données météo et hôtelières
- Association des hôtels aux villes (via `city_id`)
- Génération d’un fichier consolidé au format `.csv`

#### 🔹 **LOAD**
- Sauvegarde du `.csv` dans un **bucket AWS S3**
- Chargement des données dans une **base PostgreSQL hébergée sur AWS RDS**

---

### 🗺️ Visualisation

#### 📍 Carte 1 : Top 5 des villes avec la meilleure météo
- Créée avec **Plotly Express**
- Affichage dynamique selon les prévisions météo agrégées

#### 🏨 Carte 2 : Top 20 hôtels (par ville)
- Réalisée avec **Streamlit** + **Folium**
- Carte interactive filtrée par ville
- Chaque hôtel affiche :
  - Nom, note, description
  - 🔗 Lien direct vers Booking.com

---

### 🛠️ Technologies utilisées

| Outil / Tech       | Rôle                              |
|--------------------|-----------------------------------|
| Python             | Langage principal                 |
| Pandas             | Manipulation des données          |
| Aiohttp / Asyncio  | Appels API non bloquants          |
| Scrapy             | Extraction des données hôtelières |
| OpenWeatherMap API | Données météo                     |
| Nominatim API      | Géocodage                         |
| Plotly             | Visualisation météo               |
| Folium             | Carte interactive hôtels          |
| Streamlit          | Interface utilisateur             |
| AWS S3             | Lac de données (stockage CSV)     |
| AWS RDS (Postgres) | Base de données relationnelle     |

---

### 📬 Livrables

- ✅ Un fichier `.csv` enrichi, **stocké dans S3** (non publié ici pour des raisons légales)
- ✅ Une **base PostgreSQL (RDS)** contenant les données nettoyées
- ✅ Deux cartes interactives :
  - Top 5 **destinations météo**
  - Top 20 **hôtels** pour chaque ville

> 🛡️ Les fichiers `.csv`, `.json` et `.env` **ne sont pas présents dans ce dépôt** pour des raisons de sécurité, de confidentialité et de respect des CGU des services utilisés. Un fichier d’exemple ou un script de génération peut être utilisé pour tester l’application.

---

### ✅ Critères respectés

| Critère                                 | Statut      |
|-----------------------------------------|-------------|
| Simplicité de l'infrastructure          | ✅ OK (S3 + RDS) |
| Stockage évolutif et scalable           | ✅ OK (S3, Big Data Ready) |
| Coût maîtrisé                           | ✅ OK (services cloud à la demande) |
| Qualité & structuration des données     | ✅ OK (APIs fiables + nettoyage) |
| Accessibilité & rapidité des données    | ✅ OK (RDS + SQL) |
| Fiabilité du pipeline ETL               | ✅ OK (asynchrone + loggé) |
| Conformité RGPD                         | ✅ Aucune donnée personnelle collectée ou stockée |

---

### 📅 Période d’analyse météo : 24/04/2025 - 30/04/2025

---

### 📎 Mentions légales

- Ce projet est réalisé **dans un cadre pédagogique uniquement**.
- Les données météorologiques et géographiques sont issues de sources **publiques** (OpenWeatherMap, OpenStreetMap).
- Aucune donnée personnelle n’est collectée, stockée ni traitée.
