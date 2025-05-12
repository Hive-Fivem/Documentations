# Module Collector

Le module **Collector** permet de créer et manipuler facilement des tables en base de données en définissant dynamiquement leur structure depuis le code Lua.

## Sommaire

- Création d'un Collector
- Types de colonnes supportés
- Méthodes disponibles
  - insert
  - find
  - findAll
  - update
  - delete

---

## Création d'un Collector

```lua
UserCollector = Hive.Collector.new(
    "users",
    {
        id = { type = "uid" },
        name = { type = "string", length = 255 },
        age = { type = "number", length = 11 },
        is_admin = { type = "boolean", default = false },
        settings = { type = "table" }
    },
    "id" -- colonne primaire
)
```

Ce code créera automatiquement la table users si elle n'existe pas déjà.


---

## Types de colonnes supportés

| Type    | SQL généré                   | Description                                     |
|---------|------------------------------|-------------------------------------------------|
| `uid`   | INT AUTO_INCREMENT           | Identifiant unique, utilisé comme clé primaire  |
| `string`| VARCHAR(n)                   | Texte (n caractères max, ex. 255)               |
| `number`| INT(n)                       | Nombre entier (n = taille, ex. 11)              |
| `boolean`| TINYINT(1)                  | Vrai (1) ou Faux (0), booléen                   |
| `table` | LONGTEXT                     | Données complexes (encodées en JSON)            |

---

## Méthodes disponibles

### - Collector:insert(table)

Insère une ligne dans la table.

```lua
UserCollector:insert({
    name = "John Doe",
    age = 28,
    is_admin = true
})
```

### - Collector:find(whereTable, callback)

Recherche une ou plusieurs lignes correspondant à un filtre.

```lua
UserCollector:find({ name = "John Doe" }, function(results)
    if #results > 0 then
        print("Utilisateur trouvé :", results[1].name)
    end
end)
```

### - Collector:findAll()

Récupère toutes les lignes de la table.

```lua
UserCollector:findAll(function(results)
    for _, row in pairs(results) do
        print(row.name)
    end
end)
```

### - Collector:update(whereTable, newValueTable)

Met à jour une ou plusieurs lignes.

```lua
UserCollector:update(
    { name = "John Doe" }, -- filtre
    { age = 30 }           -- nouvelles valeurs
)
```

### - Collector:delete(whereTable)

Supprime une ou plusieurs lignes.

```lua
UserCollector:delete({ name = "John Doe" })
```

---

## Remarques

Toutes les requêtes sont exécutées en interne via MySQL.prepare ou MySQL.query.

Le module attend que la table soit correctement initialisée avant toute opération.


---