# TP GitHub Actions pour DevOps & Développeurs

[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/stephrobert/github-actions-training/badge)](https://scorecard.dev/viewer/?uri=github.com/stephrobert/github-actions-training)
[![SLSA 3](https://slsa.dev/images/gh-badge-level3.svg)](https://slsa.dev)

Bienvenue dans ce projet de **Travaux Pratiques GitHub Actions** !

Ces TP vous guideront dans l'apprentissage pratique de **GitHub Actions** pour
l'automatisation CI/CD. Chaque TP est organisé dans un **sous-dossier** avec son
propre énoncé et des tests de validation. Au début, les explications seront
détaillées, mais très vite, vous serez plus autonome.

## Pré-requis

### Compte GitHub

- Un compte **GitHub** (gratuit suffit pour commencer)
- Un dépôt de test (fork de ce projet ou nouveau dépôt)
- **GitHub CLI** installé (optionnel mais recommandé)

### Environnement local

- **Git** installé et configuré
- Un éditeur de code (VS Code recommandé avec l'extension GitHub Actions)
- **act** pour tester les workflows localement (optionnel)

**Installation de GitHub CLI :**

```bash
# Debian/Ubuntu
sudo apt install gh

# macOS
brew install gh

# Windows
winget install GitHub.cli
```

**Installation de act (tests locaux) :**

```bash
# Via curl
curl -s https://raw.githubusercontent.com/nektos/act/master/install.sh | sudo bash

# macOS
brew install act
```

**Vérifications rapides :**

```bash
git --version
gh --version
act --version  # optionnel
```

## Documentation obligatoire

Avant de commencer un TP, vous devez **lire la documentation** liée au sujet sur
[mon site de documentation](https://blog.stephane-robert.info/docs/pipeline-cicd/github/).

Chaque énoncé précisera quelle section lire.
**Aucune aide ne sera donnée sur des notions qui y sont expliquées.**

**Lectures recommandées :**

- [Tout savoir sur GitHub Actions CI/CD](https://blog.stephane-robert.info/docs/pipeline-cicd/github/)
- [Sécurité GitHub Actions](https://blog.stephane-robert.info/docs/pipeline-cicd/github/securite/)
- [Documentation officielle GitHub Actions](https://docs.github.com/en/actions)

## Structure du projet

Chaque TP est placé dans un **sous-dossier** indépendant :

```bash
/github-actions-training/
│
├── tp-01-premier-workflow/        # Créer son premier workflow
├── tp-02-events-triggers/         # Événements et déclencheurs
├── tp-03-contexts-expressions/    # Contexts et expressions
├── tp-04-variables-secrets/       # Variables et secrets
├── tp-05-matrix-strategy/         # Stratégies de matrix
├── tp-06-conditions-if/           # Conditions et contrôle de flux
├── tp-07-cache-artifacts/         # Cache et artifacts
├── tp-08-reusable-workflows/      # Workflows réutilisables
├── tp-09-composite-actions/       # Actions composites
├── tp-10-self-hosted-runners/     # Runners self-hosted
├── tp-11-securite-permissions/    # Sécurité et permissions
├── tp-12-oidc-cloud/              # OIDC et déploiements cloud
├── tp-13-attestations-slsa/       # Attestations et provenance SLSA
└── tp-14-projet-final/            # Projet de synthèse
```

## Parcours d'apprentissage

### 🟢 Niveau Débutant (TP 01-04)

Objectif : comprendre les bases de GitHub Actions

| TP | Sujet | Durée estimée |
|----|-------|---------------|
| 01 | Premier workflow | 30 min |
| 02 | Events et triggers | 45 min |
| 03 | Contexts et expressions | 1h |
| 04 | Variables et secrets | 45 min |

### 🟡 Niveau Intermédiaire (TP 05-09)

Objectif : maîtriser les patterns avancés

| TP | Sujet | Durée estimée |
|----|-------|---------------|
| 05 | Matrix strategy | 1h |
| 06 | Conditions et if | 45 min |
| 07 | Cache et artifacts | 1h |
| 08 | Reusable workflows | 1h30 |
| 09 | Composite actions | 1h |

### 🔴 Niveau Avancé (TP 10-14)

Objectif : sécuriser et industrialiser

| TP | Sujet | Durée estimée |
|----|-------|---------------|
| 10 | Self-hosted runners | 1h30 |
| 11 | Sécurité et permissions | 1h30 |
| 12 | OIDC et cloud | 1h30 |
| 13 | Attestations et SLSA | 2h |
| 14 | Projet final | 3h |

## Validation des exercices

Chaque TP contient :

1. **Un README.md** avec l'énoncé et les tutoriels
2. **Un dossier `challenge/`** avec un exercice à réaliser
3. **Des tests automatisés** pour valider votre travail

Pour valider un challenge :

```bash
cd tp-XX-xxx/challenge
# Suivre les instructions du README.md
# Puis exécuter les tests
./validate.sh
```

## Conseils pour réussir

1. **Lisez la doc avant de coder** : chaque TP indique les sections à lire
2. **Testez localement avec `act`** : plus rapide que de Pousser à chaque fois
3. **Utilisez les logs** : `ACTIONS_RUNNER_DEBUG=true` pour le debug
4. **Commitez souvent** : un commit = une étape fonctionnelle
5. **Sécurité d'abord** : ne jamais commiter de secrets !

## Ressources complémentaires

### Documentation officielle

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Workflow syntax reference](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions)
- [Security hardening](https://docs.github.com/en/actions/security-guides/security-hardening-for-github-actions)

### Outils utiles

- [act](https://github.com/nektos/act) - Exécuter les workflows localement
- [actionlint](https://github.com/rhysd/actionlint) - Linter pour workflows
- [GitHub Actions VS Code Extension](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-github-actions)

### Mon blog

- [GitHub Actions](https://blog.stephane-robert.info/docs/pipeline-cicd/github/)
- [Sécurité CI/CD](https://blog.stephane-robert.info/docs/pipeline-cicd/github/securite/)
- [Supply Chain](https://blog.stephane-robert.info/docs/securiser/supply-chain/)

## Contribution

Les contributions sont les bienvenues ! Consultez [CONTRIBUTING.md](CONTRIBUTING.md)
pour les guidelines.

## Licence

Ce projet est sous licence MIT. Voir [LICENSE](LICENSE) pour plus de détails.
