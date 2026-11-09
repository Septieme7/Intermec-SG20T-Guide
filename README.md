# Résolution du conflit Ctrl+J - Scanner Intermec SG20T

[![GitHub repo](https://img.shields.io/badge/GitHub-Intermec--SG20T--Guide-181717?style=plastic&logo=github)](https://github.com/Septieme7/Intermec-SG20T-Guide.git)
[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-En%20ligne-06b6d4?style=plastic&logo=github)](https://septieme7.github.io/Intermec-SG20T-Guide/)

## Le Pourquoi de ce projet

J'ai créé ce tutoriel pour documenter et partager la solution à un problème particulièrement frustrant que j'ai rencontré lors de l'intégration d'un scanner de codes-barres Intermec SG20T dans une application web.

Lorsqu'on utilise ce type de matériel (qui émule un clavier USB classique, ou HID) sur un navigateur basé sur Chromium comme Brave ou Chrome, chaque scan déclenchait l'ouverture intempestive de l'onglet des téléchargements.

En analysant la chaîne de communication, j'ai compris que le scanner envoyait par défaut un suffixe `Carriage Return + Line Feed` (CR+LF). Le caractère `LF` (Line Feed) est interprété par le navigateur comme le raccourci clavier `Ctrl+J`, d'où l'ouverture de la page de téléchargements.

## Les aides apportées

Ce guide interactif a pour but d'aider les développeurs et intégrateurs qui font face au même blocage :

- **Compréhension de la cause racine** : J'explique clairement l'interaction entre un scanner HID, les caractères de contrôle (CR/LF) et le comportement natif des navigateurs web.
- **Solution matérielle définitive** : Je détaille ma méthode pour reconfigurer le scanner à la source (via l'utilitaire EasySet de Honeywell), en créant une commande personnalisée pour n'envoyer que le `CR`, éliminant ainsi le conflit sans compromettre la validation des formulaires.
- **Sécurité applicative (React)** : J'ai également inclus un extrait de code pour les développeurs souhaitant ajouter une sécurité logicielle (interception de l'événement `keydown`) afin de rendre l'application autonome, quel que soit le matériel utilisé.
- **Accessibilité** : Le tutoriel est disponible en version bilingue (Français/Anglais) et propose un confort de lecture optimal grâce à un thème sombre et un thème clair.

## Utilisation

Le tutoriel est directement consultable en ligne sur [GitHub Pages](https://septieme7.github.io/Intermec-SG20T-Guide/). 

Si vous souhaitez le consulter ou l'héberger localement, clonez simplement ce dépôt et ouvrez le fichier `index.html` dans votre navigateur.