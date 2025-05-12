# 🧩 Modules principaux du framework Hive

Le framework Hive est composé de plusieurs modules distincts et spécialisés. Chacun d’eux est responsable d’un ensemble précis de fonctionnalités. Cette séparation permet une maintenance plus simple, une meilleure évolutivité et une meilleure organisation du code.

---

## 📦 Liste des modules

### 1. `Collector`

> **Objectif :** Simplifie la création et manipulation de tables dans la base de données.

- Génération automatique de tables.
- Insertion, mise à jour, suppression de lignes.
- Abstraction pour ne pas avoir à écrire directement des requêtes SQL.
- Utilisé en support pour d’autres modules (Player, Item, etc.).

---

### 2. `Inventory`

> **Objectif :** Gère les inventaires en dehors du joueur (coffres, véhicules, shops...).

- Création d’inventaires temporaires ou persistants.
- Manipulation (ajout, retrait, transfert d’objets).
- Système de slots, poids ou autres contraintes (selon la config).
- Interactions avec les modules `Collector` et `Item`.

---

### 3. `Item`

> **Objectif :** Centralise la logique autour des objets utilisables en jeu.

- Déclaration et enregistrement des objets.
- Rendre un objet utilisable via une fonction serveur/client.
- Permet de jeter, transférer ou utiliser des objets depuis un inventaire.
- Fournit un système d’actions personnalisables selon l’objet.

---

### 4. `Player`

> **Objectif :** Gère tout ce qui est relatif au joueur.

- Inventaire du joueur (connecté à `Inventory`).
- Données bancaires, argent liquide.
- Apparence / skin (intégration possible avec skinchanger ou autre).
- Système de sauvegarde et chargement des données.
- Hooks pour les événements comme connexion, déconnexion, respawn.

---

### 5. `Vehicles`

> **Objectif :** Encadre la gestion des véhicules dans le serveur.

- Enregistrement des véhicules en base.
- Spawn / delete des véhicules.
- Récupération de données (propriétaire, modèle, customisation).
- Interaction avec l’inventaire (coffre du véhicule).
- Prise en charge des véhicules de joueurs ou de société.

---

## Modules disponibles

| Module      | Dépend de…        | Contexte    |
|-------------|-------------------|------------|
| Inventory   | Collector, Item   | Server |
| Item        | Aucun             | Server |
| Player      | Inventory, Item   | Server |
| Vehicles    | Player, Inventory | Server |
| [Collector](modules/collector.lua) | Aucun             | Server |

---

## 📖 Voir aussi

- [📄 Structure du framework](pages/structure.md)
- [📦 Liste des exports disponibles](pages/api.md)
- [📡 Liste des événements](pages/events.md)