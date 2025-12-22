---
applyTo: "**/.github/workflows/*.yml"
description: "Instructions pour les workflows GitHub Actions"
---

# Instructions pour les workflows GitHub Actions

## Bonnes pratiques obligatoires

### 1. Permissions explicites

Toujours déclarer les permissions au niveau workflow ET job :

```yaml
# Niveau workflow : permissions minimales par défaut
permissions:
  contents: read

jobs:
  build:
    runs-on: ubuntu-latest
    # Niveau job : permissions spécifiques si nécessaire
    permissions:
      contents: read
      packages: write
```

### 2. Actions épinglées par SHA

Ne JAMAIS utiliser de tags mutables (`@v4`, `@main`, `@latest`) :

```yaml
# ❌ Dangereux
- uses: actions/checkout@v4

# ✅ Sécurisé (SHA + commentaire version)
- uses: actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4.2.2
```

### 3. Noms explicites

```yaml
jobs:
  # Nom du job explicite
  build-and-test:
    runs-on: ubuntu-latest
    steps:
      # Chaque step doit avoir un nom
      - name: Checkout repository
        uses: actions/checkout@...

      - name: Setup Node.js
        uses: actions/setup-node@...
```

### 4. Commentaires pédagogiques

Pour les TP, commenter chaque section importante :

```yaml
# Déclencheurs : quand le workflow s'exécute
on:
  push:
    branches: [main]  # Sur push vers main
  pull_request:
    branches: [main]  # Sur PR vers main

# Variables d'environnement globales
env:
  NODE_VERSION: '20'
```

## Structure recommandée

```yaml
name: Nom descriptif du workflow

# 1. Permissions (toujours explicites)
permissions:
  contents: read

# 2. Déclencheurs
on:
  push:
    branches: [main]

# 3. Variables d'environnement globales (optionnel)
env:
  KEY: value

# 4. Jobs
jobs:
  job-name:
    runs-on: ubuntu-latest
    steps:
      - name: Step description
        run: echo "Hello"
```

## Patterns interdits

- `permissions: write-all`
- `pull_request_target` avec checkout du fork
- Secrets dans les logs (`echo ${{ secrets.XXX }}`)
- `continue-on-error: true` sans justification
