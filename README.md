# CompteurConges - Périodes Spéciales

Fichiers JSON de périodes spéciales (vacances scolaires, jours fériés...) importables dans l'application [CompteurConges](https://github.com/Silvers12/CompteurConges).

## Utilisation

Dans l'application CompteurConges :
1. Aller dans **Périodes spéciales**
2. Appuyer sur **Importer**
3. Choisir **Depuis le serveur**
4. Sélectionner le pays, la catégorie, puis le fichier souhaité

## Structure

```
├── index.json
├── france/
│   └── vacances_scolaires/
│       ├── zone_a_2026_2027.json
│       ├── zone_b_2026_2027.json
│       └── zone_c_2026_2027.json
└── ...
```

## Fichiers disponibles

### France - Vacances scolaires 2026-2027

| Fichier | Zone | Académies |
|---------|------|-----------|
| `zone_a_2026_2027.json` | Zone A | Besançon, Bordeaux, Clermont-Ferrand, Dijon, Grenoble, Limoges, Lyon, Poitiers |
| `zone_b_2026_2027.json` | Zone B | Aix-Marseille, Amiens, Lille, Nancy-Metz, Nantes, Nice, Normandie, Orléans-Tours, Reims, Rennes, Strasbourg |
| `zone_c_2026_2027.json` | Zone C | Créteil, Montpellier, Paris, Toulouse, Versailles |

Source : [Arrêté du 22 octobre 2025 - Légifrance](https://www.legifrance.gouv.fr/jorf/id/JORFTEXT000052416058)

## Format JSON

### Index (`index.json`)

```json
{
  "version": 1,
  "categories": [
    {
      "name": "France",
      "icon": "🇫🇷",
      "subcategories": [
        {
          "name": "Vacances Scolaires",
          "files": [
            {
              "name": "Zone A 2026-2027",
              "filename": "france/vacances_scolaires/zone_a_2026_2027.json",
              "description": "Besançon, Bordeaux, Lyon...",
              "count": 6
            }
          ]
        }
      ]
    }
  ]
}
```

### Fichier de périodes

```json
{
  "format": "CompteurConges_PeriodesSpeciales",
  "version": 1,
  "name": "Nom du fichier",
  "description": "Description",
  "periodes": [
    {
      "libelle": "Nom de la période",
      "dateDebut": "20261017",
      "dateFin": "20261102",
      "couleur": -26624,
      "chome": false
    }
  ]
}
```

| Champ | Type | Description |
|-------|------|-------------|
| `format` | string | Doit être `CompteurConges_PeriodesSpeciales` |
| `version` | int | Version du format (`1`) |
| `name` | string | Nom affiché dans la liste de sélection |
| `description` | string | Description du contenu |
| `periodes` | array | Liste des périodes |

### Champs d'une période

| Champ | Type | Description |
|-------|------|-------------|
| `libelle` | string | Nom de la période |
| `dateDebut` | string | Date de début au format `yyyyMMdd` |
| `dateFin` | string | Date de fin au format `yyyyMMdd` |
| `couleur` | int | Couleur Android (ARGB signé, ex: `-26624` = orange) |
| `chome` | boolean | `true` si la période est chômée |

## Contribuer

Pour ajouter de nouvelles périodes :
1. Créer un dossier `pays/categorie/` si nécessaire
2. Créer un fichier JSON respectant le format ci-dessus
3. Ajouter l'entrée correspondante dans `index.json`
4. Soumettre une Pull Request
