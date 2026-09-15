# Design Draft – Carbon-ia

Ce document décrit l’architecture technique initiale du projet Carbon-ia. Il sert de base pour le développement du MVP et pour l’évolution future du projet.

## 1. Architecture générale
Carbon-ia repose sur trois composants principaux :
1. Extension navigateur (capture des requêtes IA).
2. Backend local (calcul CO₂, stockage, API).
3. Interface web (visualisation, historique, recommandations).

## 2. Extension navigateur
- Analyse des requêtes envoyées aux modèles IA.
- Extraction des tokens, du modèle utilisé, du contexte.
- Envoi des données au backend local via API.
- Fonctionne sur Chrome, Firefox, Edge.

## 3. Backend local
Langage MVP : Python.
Évolution possible : Rust (module de calcul optimisé).

Fonctions :
- Calcul CO₂/token selon facteurs scientifiques.
- Calcul énergétique détaillé (IA + utilisateur).
- Stockage local (SQLite).
- API REST pour frontend et extension.
- Module de comparaison cloud/local.

## 4. Modèle de calcul
Le modèle de calcul repose sur plusieurs catégories de facteurs :

### 4.1 Facteurs IA (cloud ou local)
- kWh/token selon le modèle IA.
- Intensité carbone du fournisseur cloud.
- Efficacité énergétique du matériel (GPU, CPU).
- Facteurs eau (optionnel).

### 4.2 Facteurs utilisateur (poste local)
- Consommation électrique du PC (idle, charge IA).
- Type d’alimentation :
  - secteur classique,
  - batterie,
  - alimentation externe,
  - alimentation stabilisée.
- Origine du courant :
  - mix énergétique local,
  - renouvelable vs non-renouvelable,
  - intensité carbone régionale.
- Géolocalisation (pays, région, fournisseur d’électricité).

### 4.3 Facteurs scientifiques
- Facteurs CO₂/kWh issus de bases reconnues :
  - IEA,
  - IPCC,
  - ADEME,
  - fournisseurs cloud (AWS, GCP, Azure).
- Facteurs eau/token selon publications récentes.
- Facteurs énergétiques des GPU (TDP, efficacité).

### 4.4 Sorties du modèle
- CO₂ estimé (g, kg).
- Énergie consommée (Wh, kWh).
- Eau virtuelle (L).
- Score de sobriété IA.
- Comparaison cloud vs local.

## 5. Interface web
- Dashboard minimaliste.
- Graphiques temporels.
- Historique des requêtes.
- Recommandations de sobriété.
- Mode offline.

## 6. Évolutions futures
- Modules Rust pour calcul haute performance.
- Intégration LM Studio / Ollama.
- API publique.
- Mode entreprise (MSP).
- Export des données.
- Facteurs énergétiques dynamiques selon géolocalisation.
