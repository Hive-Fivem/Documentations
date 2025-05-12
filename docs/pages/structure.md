# 🧩 Structure du Framework Hive

Le framework **Hive** repose sur une structure organisée par contexte : `client`, `server`, `shared`, et `stream`.

Chaque dossier contient des sous-modules ou des fonctions spécifiques à son environnement, facilitant la séparation logique et la maintenabilité.

---

## 📦 Détail des dossiers

### `client/`

> Contient toute la logique exécutée côté client.

- **classes/** : Définitions orientées objet spécifiques client (UI, états…).
- **events/** : Gestion des événements `RegisterNetEvent`, `AddEventHandler`, etc.
- **exports/** : Fonctions exposées aux autres ressources depuis le client.
- **main.lua** : Point d'entrée principal client, init et configuration.

### `server/`

> Contient toute la logique côté serveur, accès base de données, gestion de l’état global.

- **classes/** : Entités serveur (joueur, véhicule, job…).
- **collectors/** : Modules de récupération d’infos (ex : inventaire DB, logs).
- **events/** : Gestion des événements serveur (`RegisterServerEvent`, etc.).
- **exports/** : Fonctions exportées côté serveur.
- **Items.lua** : Déclaration des items utilisables dans le framework.
- **main.lua** : Point d’entrée serveur du framework Hive.

### `shared/`

> Fichiers communs aux deux contextes (client et serveur). Types, énumérations, constantes, etc.

### `stream/`

> Contient les fichiers streamables : objets, ytd/yft, maps, sons, etc.

---

## 🔁 Flux de chargement

> Le framework est conçu pour être chargé via un seul `ensure HiveFramework` dans le `server.cfg`. Aucun fichier externe à modifier pour chaque nouveau module.

---

## 📖 Aller plus loin

- [Liste des événements](pages/events.md)
- [Exports disponibles](pages/api.md)