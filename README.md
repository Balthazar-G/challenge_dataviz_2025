# 🏘️ Challenge Data Visualisation 2025 — Institut des Actuaires

> **Évaluation vs Vulnérabilité : Le marché immobilier face à l'aveuglement climatique**

---

## 📌 Présentation du projet

Ce projet a été réalisé dans le cadre du **Challenge Data Visualisation 2025** organisé par l'Institut des Actuaires. Il explore la dynamique du **marché immobilier français** face aux **risques climatiques croissants**, en croisant deux sources de données majeures :

- 🌍 **Géorisques** — données de risques naturels (Retrait-Gonflement des Argiles et Inondations par Remontée de Nappes)
- 🏠 **DVF (Demandes de Valeurs Foncières)** — données de transactions immobilières

La question centrale de ce rapport est : **le marché immobilier est-il "aveugle" aux périls climatiques qui s'intensifient ?**

---

## 🗂️ Structure du rapport

### 1. 🔧 Préparation des données
Construction d'un score de risque unique et comparable par commune, via une méthodologie en trois étapes :
- **Pondération** actuarielle des niveaux d'aléa
- **Agrégation** surfacique : `Score = Σ(Surface Exposée × Poids) / Surface Totale`
- **Normalisation** min-max sur une échelle de 1 à 10

### 2. 🗺️ Cartographie des risques
Cartographies interactives multi-échelles (communes / départements / régions) des risques :
- Risque Argile (Retrait-Gonflement des Argiles)
- Risque Nappes (Inondations par Remontée de Nappes)

### 3. 🔥 Analyse du risque combiné
Score combiné `(Argile × Nappes)` pour capturer les effets non-linéaires de cumul. Validation statistique par **analyse de copules** (Clayton, Gumbel, Frank), qui confirme une **dépendance dans les queues supérieures** : les zones à fort risque argile sont aussi, de manière disproportionnée, exposées au risque nappes.

### 4. 📈 Analyse descriptive des données foncières (DVF)
Exploration du marché immobilier : distribution des prix au m², comparaison maisons/appartements, analyse régionale, saisonnalité des transactions.

### 5. 🎯 L'Indice de Myopie : croisement risques × marché
Carte à bulles confrontant le **score de risque combiné** et le **volume de capitaux exposés** (montant total des transactions). Révèle les zones de cumul — là où le marché concentre des enjeux financiers élevés malgré une exposition climatique forte.

### 6. 💡 Conclusion : de l'analyse à l'action
Implications pour les assureurs : pilotage des risques, stratégie RSE, anticipation des problèmes d'assurabilité.

### 7. 🧮 Applications actuarielles
Deux applications pratiques :

- **7.1 Tarification** — Simulation d'une prime de risque climatique annuelle par commune, illustrant l'impact d'une tarification au risque individuel vs la mutualisation du régime Cat' Nat'.
- **7.2 Gestion des risques** — Estimation du capital exposé par niveau de risque, outil d'aide au pilotage de la solvabilité.

---

## 🛠️ Stack technique

| Outil | Usage |
|---|---|
| **R** | Traitement des données et analyses statistiques |
| **R Markdown / Quarto** | Génération du rapport HTML interactif |
| **Leaflet** | Cartographies interactives multi-couches |
| **ggplot2 / ggridges** | Visualisations statistiques avancées |
| **copula** (package R) | Modélisation des dépendances entre risques |
| **Scripts `01_prepare_data.R`…** | Pré-calculs externalisés pour performance |

---

## 📁 Fichiers

```
.
├── index.html              # Rapport interactif final
├── 01_prepare_data.R       # Préparation et scoring des données risques
├── rapport_2025.Rmd        # Source R Markdown
└── README.md
```

---

## 📊 Sources de données

| Source | Description | Lien |
|---|---|---|
| **Géorisques** | Aléas RGA et Remontée de Nappes par commune | [georisques.gouv.fr](https://www.georisques.gouv.fr) |
| **DVF** | Demandes de Valeurs Foncières (transactions immobilières) | [data.gouv.fr](https://www.data.gouv.fr/fr/datasets/demandes-de-valeurs-foncieres/) |

---

## 🔑 Résultats clés

- ✅ Dépendance statistiquement significative entre risques Argile et Nappes (copule de Gumbel, queue supérieure)
- ✅ Volume de transactions **en hausse dans les zones à risque élevé**, signe d'un probable aveuglement climatique du marché
- ✅ Primes simulées allant de **~150 € à plus de 550 €/an** selon les communes, matérialisant les zones à risque d'inassurabilité

---

## 📄 Licence

Les données utilisées sont en open data :
- DVF sous [Licence Ouverte / Open Licence v2.0](https://www.etalab.gouv.fr/licence-ouverte-open-licence) (Etalab)
- Géorisques sous [Licence Ouverte v2.0](https://www.georisques.gouv.fr/mentions-legales)
