# Structure du projet Carbon-ia — Explications

La structure du projet Carbon-ia est conçue pour séparer clairement les responsabilités, faciliter la contribution, et permettre une évolution progressive (exemple: Python → Rust, modules additionnels, extension navigateur, etc.).

## backend/
Contient le backend local responsable du calcul CO₂, du stockage et de l’API REST.
Séparé du frontend pour éviter les dépendances croisées et permettre une migration future vers Rust.
Ce dossier inclut :
- app.py : point d’entrée du backend
- core/ : logique métier (calcul, facteurs scientifiques)
- api/ : routes REST
- db.sqlite : stockage local

## extension/
Contient l’extension navigateur.
Séparée du backend car elle fonctionne dans un environnement totalement différent (WebExtension API).
Elle capture les requêtes IA et les envoie au backend local.

## frontend/
Interface web locale permettant de visualiser les données (historique, graphiques, recommandations).
Séparée du backend pour permettre une évolution indépendante (framework JS, design, etc.).

## data/
Contient les données scientifiques et énergétiques utilisées par le calcul :
- facteurs CO₂/kWh
- intensité carbone régionale
- consommation électrique des modèles IA
- consommation électrique utilisateur (appareil, alimentation, géographie)

Ce dossier est isolé pour permettre la mise à jour des données sans toucher au code.

## prototype/
Contient les démonstrations, maquettes, captures, GIFs, tests visuels.
Permet de documenter l’évolution du projet sans polluer le code.

## Pourquoi cette structure ?
- Séparation claire des responsabilités.
- Évolution progressive possible.
- Mise à jour indépendante des données scientifiques.
- Contribution facilitée : chaque dossier correspond à un domaine précis.
- Compatibilité avec les bonnes pratiques open-source.
