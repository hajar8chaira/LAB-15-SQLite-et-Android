# LAB 15 - Persistance locale des données : SQLite et Android
**Cours :** Programmation Mobile : Android avec Java  
**Étudiant :** Hajar Chaira

---

## 1. Objectif pédagogique
L'objectif de ce laboratoire est de réaliser une application Android autonome intégrant une base de données embarquée SQLite. L'application permet d'assurer le stockage local et la persistance des données relatives aux étudiants. Elle met en œuvre le schéma classique du cycle CRUD (création, recherche, affichage et suppression) entièrement hors-ligne, directement sur le support de stockage du périphérique mobile, à travers une architecture applicative propre et structurée en couches.

---

## 2. Aperçu visuel du projet et Démonstration

### Captures d'écran de l'exécution du projet

| Ajout d'étudiant | Recherche d'étudiant | Suppression locale |
| :---: | :---: | :---: |
| ![Ajout et Validation](img-lab15-dev/1.png) | ![Recherche par ID](img-lab15-dev/2.png) | ![Suppression et Nettoyage](img-lab15-dev/3.png) |
| Formulaire d'insertion de l'étudiant avec affichage de la notification de confirmation d'ajout | Saisie de l'identifiant recherché pour extraire et afficher dynamiquement le nom et le prénom | Suppression immédiate de la ligne sélectionnée avec effichage d'état et mise à jour de la liste |

---

## 3. Démonstration Vidéo
La vidéo ci-dessous présente le fonctionnement de l'application en temps réel : l'ajout d'étudiants via le formulaire, la recherche instantanée de leurs fiches par identifiant unique et la suppression réussie des enregistrements de la base de données SQLite locale.

<video src="img-lab15-dev/video.mp4" controls="controls" style="max-width: 100%;">
</video>

---

## 4. Architecture et Réalisation minimale

### Étape 1 : Modélisation Métier
Une structure de classe simple a été créée pour représenter les entités stockées. L'objet comprend des attributs distincts pour l'identifiant unique (clé primaire auto-incrémentée par SQLite), le nom et le prénom, associés à des accesseurs standards.

### Étape 2 : Création de la Base de données (SQLiteOpenHelper)
Un gestionnaire de base de données dérivé de la classe Android native de persistance initialise le fichier de stockage nommé de façon autonome. Il s'occupe de la construction automatique de la table locale à l'initialisation de l'application et de sa mise à niveau en cas de restructuration du schéma SQL.

### Étape 3 : Implémentation du Service d'Accès aux Données
Un service intermédiaire encapsule la logique d'interrogation de la base de données SQLite :
* **Écriture :** Enregistre les nouveaux champs de données par le biais de structures de valeurs normalisées.
* **Lecture :** Exécute des sélections ciblées sur des tables à l'aide de curseurs de parcours afin de reconstituer les objets métier de manière asynchrone.
* **Mise à jour et Suppression :** Gère la suppression des lignes correspondantes selon l'identifiant fourni.

### Étape 4 : Interface et Gestion des Événements
L'interface graphique est agencée verticalement dans un modèle de conteneur linéaire simple. Elle réunit des zones de texte guidées et des champs d'édition pour la saisie, associés à des déclencheurs d'événements. Les écouteurs d'événements valident les entrées utilisateurs, exécutent les transactions en base de données SQLite via le service dédié et informent l'utilisateur par des messages d'alerte temporaires.

---

## 5. Compétences acquises
* **Gestion autonome de la persistance :** Initialisation et manipulation de bases de données relationnelles locales embarquées sous Android sans faire appel à des serveurs distants.
* **Structuration et découplage :** Conception d'applications mobiles scindées en couches étanches séparant l'interface graphique du moteur persistant de données.
* **Résilience logicielle :** Intégration de vérifications d'entrées préventives pour éliminer les risques de plantages lors de requêtes infructueuses ou vides.

---
**Rapport de TP - 2026**
