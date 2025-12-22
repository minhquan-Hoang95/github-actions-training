---
applyTo: "**"
description: "Instructions globales pour le projet de formation GitHub Actions"
---

# Instructions Copilot — Formation GitHub Actions

## Objectif du projet

Projet de **formation GitHub Actions** avec des TP progressifs.
Le contenu vise des lecteurs **débutants à avancés** : on explique, on illustre,
on fournit des exercices pratiques avec validation automatisée.

## Structure des TP

Chaque TP suit cette structure :

```
tp-XX-nom/
├── README.md           # Énoncé + tutoriels guidés
├── challenge/
│   ├── README.md       # Instructions du challenge
│   ├── .github/
│   │   └── workflows/  # Workflows à compléter/créer
│   └── validate.sh     # Script de validation
└── solution/           # Solution de référence (optionnel)
```

## Règles d'écriture

### Style pédagogique

- Français clair, pragmatique, accessible
- Pas de jargon sans explication préalable
- Chaque concept nouveau doit être illustré par un exemple
- Progression du simple au complexe

### README des TP

Structure obligatoire :

1. **Introduction** : problème concret à résoudre
2. **Objectifs** : ce que l'apprenant saura faire
3. **Pré-requis** : TP précédents, lectures recommandées
4. **Rappels** : concepts clés en résumé
5. **Tutoriels** : exercices guidés pas à pas
6. **Challenge** : exercice autonome
7. **Pour aller plus loin** : ressources complémentaires

### Workflows YAML

- Toujours commenter les lignes importantes
- Utiliser des noms explicites pour les jobs et steps
- Épingler les actions par SHA (sécurité)
- Permissions minimales explicites

Exemple de style :

```yaml
name: Build and Test

# Permissions minimales (bonne pratique sécurité)
permissions:
  contents: read

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      # Checkout du code source
      - uses: actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4.2.2

      # Installation des dépendances
      - name: Install dependencies
        run: npm ci
```

## Validation des challenges

Chaque challenge doit avoir :

1. **Des critères clairs** de réussite
2. **Un script `validate.sh`** qui vérifie le travail
3. **Des messages d'erreur explicites** pour guider l'apprenant

## Liens internes

Référencer systématiquement :

- La documentation du blog : `https://blog.stephane-robert.info/docs/pipeline-cicd/github/`
- La documentation officielle GitHub : `https://docs.github.com/en/actions`
- Les TP précédents quand pertinent

## Conventions de nommage

- Dossiers : `tp-XX-nom-en-kebab-case`
- Workflows : `nom-descriptif.yml`
- Pas d'espaces dans les noms de fichiers

## Ce qui est interdit

- Workflows qui exposent des secrets
- Exemples avec `permissions: write-all`
- Actions non épinglées par SHA dans les solutions
- Code non testé/non fonctionnel
