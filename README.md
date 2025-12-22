# TP GitHub Actions pour Dev & Ops

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
- **act** pour tester les workflows localement
- **actionlint** pour valider la syntaxe des workflows

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
2. **Testez localement avec `act`** : plus rapide que de pousser à chaque fois
3. **Validez vos workflows avec `actionlint`** : détecte les erreurs avant le push
4. **Utilisez les logs** : `ACTIONS_RUNNER_DEBUG=true` pour le debug
5. **Commitez souvent** : un commit = une étape fonctionnelle
6. **Sécurité d'abord** : ne jamais commiter de secrets !

## Outils de développement local

Cette section détaille les outils pour travailler efficacement sur vos workflows
**sans avoir à pousser sur GitHub à chaque modification**.

### actionlint — Valider la syntaxe des workflows

[actionlint](https://github.com/rhysd/actionlint) est un linter qui détecte les
erreurs de syntaxe, les problèmes de sécurité et les mauvaises pratiques dans
vos fichiers workflow.

**Installation :**

```bash
# Linux (téléchargement direct)
curl -sL https://github.com/rhysd/actionlint/releases/download/v1.7.7/actionlint_1.7.7_linux_amd64.tar.gz | tar xz -C /tmp
sudo mv /tmp/actionlint /usr/local/bin/

# Vérifier l'installation
actionlint --version

# macOS
brew install actionlint

# Windows (avec scoop)
scoop install actionlint
```

**Utilisation :**

```bash
# Valider tous les workflows du projet
actionlint

# Valider un workflow spécifique
actionlint .github/workflows/ci.yml

# Afficher les erreurs au format JSON (pour intégration CI)
actionlint -format json
```

**Exemple de sortie :**

```
.github/workflows/ci.yml:15:9: property "runs-on" is required
.github/workflows/ci.yml:23:17: "actions/checkout@v3" should be pinned by SHA
```

**Intégration VS Code :**
Installez l'extension [actionlint](https://marketplace.visualstudio.com/items?itemName=arahata.linter-actionlint)
pour voir les erreurs directement dans l'éditeur.

**Ce que actionlint détecte :**

| Type d'erreur | Exemple |
|---------------|---------|
| Syntaxe YAML invalide | Indentation incorrecte, caractères spéciaux |
| Propriétés manquantes | `runs-on` oublié dans un job |
| Expressions invalides | `${{ secrets.TOKEN }` (accolade manquante) |
| Actions non épinglées | `uses: actions/checkout@v4` (recommande SHA) |
| Permissions trop larges | `permissions: write-all` |
| Shells non supportés | `shell: zsh` sur un runner ubuntu |

---

### Vérifier le code Python avant de créer le workflow

Avant de créer votre workflow CI, assurez-vous que le code Python fonctionne
localement. Voici la procédure complète :

**1. Se placer dans le dossier du challenge :**

```bash
cd tp-01-premier-workflow/challenge
```

**2. Créer un environnement virtuel (recommandé) :**

```bash
# Créer l'environnement
python3 -m venv .venv

# Activer l'environnement
source .venv/bin/activate  # Linux/macOS
# ou
.venv\Scripts\activate     # Windows
```

**3. Installer les dépendances :**

```bash
pip install -r requirements.txt
```

**4. Vérifier la syntaxe Python (sans exécuter) :**

```bash
# Vérifier la syntaxe de tous les fichiers Python
python3 -m py_compile src/*.py tests/*.py

# Si aucune erreur n'apparaît, la syntaxe est correcte
```

**5. Lancer les tests localement :**

```bash
# Exécuter pytest
pytest

# Avec plus de détails
pytest -v

# Voir la couverture de code
pytest --cov=src
```

**6. Vérifier le style du code (optionnel mais recommandé) :**

```bash
# Installer les linters
pip install ruff black

# Vérifier le style avec ruff
ruff check .

# Formater le code avec black
black --check .  # Vérifier seulement
black .          # Appliquer le formatage
```

**Exemple de session complète :**

```bash
$ cd tp-01-premier-workflow/challenge
$ python3 -m venv .venv && source .venv/bin/activate
$ pip install -r requirements.txt
...
$ pytest -v
========================= test session starts ==========================
collected 4 items

tests/test_calculator.py::test_add PASSED                         [ 25%]
tests/test_calculator.py::test_subtract PASSED                    [ 50%]
tests/test_calculator.py::test_multiply PASSED                    [ 75%]
tests/test_calculator.py::test_divide PASSED                      [100%]

========================== 4 passed in 0.02s ===========================
```

Si tous les tests passent localement, vous pouvez créer votre workflow CI !

---

### act — Exécuter les workflows localement

[act](https://github.com/nektos/act) permet d'exécuter vos workflows GitHub Actions
sur votre machine, sans pousser sur GitHub. Idéal pour le développement itératif.

**Installation :**

```bash
# Linux
curl -s https://raw.githubusercontent.com/nektos/act/master/install.sh | sudo bash

# macOS
brew install act

# Windows
choco install act-cli
```

**Pré-requis :** Docker doit être installé et en cours d'exécution.

**Première utilisation :**

```bash
# Lancer le workflow par défaut (événement push)
act

# act vous demandera quelle image Docker utiliser :
# - Micro   : ~200MB, fonctionnalités limitées
# - Medium  : ~500MB, bon compromis (recommandé)
# - Large   : ~18GB, image complète comme GitHub
```

**Commandes courantes :**

```bash
# Lister les workflows disponibles
act -l

# Exécuter un événement spécifique
act push                    # Simule un push
act pull_request            # Simule une PR
act workflow_dispatch       # Déclenche manuellement

# Exécuter un job spécifique
act -j test                 # Lance uniquement le job "test"

# Exécuter un workflow spécifique
act -W .github/workflows/ci.yml

# Mode verbose (voir les commandes exécutées)
act -v

# Passer des secrets (ne pas les mettre en clair dans l'historique !)
act -s MY_SECRET=value
act --secret-file .secrets  # Fichier .secrets (à ajouter au .gitignore !)
```

**Gestion des runners self-hosted :**

Si votre workflow utilise `runs-on: self-hosted`, act ne peut pas l'exécuter
directement. Mappez-le vers une image Docker :

```bash
# Mapper self-hosted vers ubuntu-latest
act -P self-hosted=ghcr.io/catthehacker/ubuntu:act-latest

# Mapper plusieurs runners
act -P ubuntu-latest=ghcr.io/catthehacker/ubuntu:act-latest \
    -P self-hosted=ghcr.io/catthehacker/ubuntu:act-latest
```

**Fichier de configuration `.actrc` :**

Créez un fichier `.actrc` à la racine du projet pour éviter de répéter les options :

```bash
# .actrc
-P ubuntu-latest=ghcr.io/catthehacker/ubuntu:act-latest
-P ubuntu-24.04=ghcr.io/catthehacker/ubuntu:act-24.04
--secret-file .secrets
```

**Limitations de act :**

- ❌ Pas de support pour les services Docker (`services:`)
- ❌ Les caches GitHub (`actions/cache`) ne fonctionnent pas
- ❌ Pas d'accès aux secrets GitHub (il faut les passer manuellement)
- ❌ Certaines actions du Marketplace peuvent ne pas fonctionner

---

### OpenSSF Scorecard — Auditer la sécurité du projet

[Scorecard](https://github.com/ossf/scorecard) analyse les bonnes pratiques de
sécurité d'un projet open source et attribue un score de 0 à 10.

**Installation :**

```bash
# Linux/macOS (via Go)
go install github.com/ossf/scorecard/v5/cmd/scorecard@latest

# Ou téléchargement direct
curl -sL https://github.com/ossf/scorecard/releases/download/v5.0.0/scorecard_5.0.0_linux_amd64.tar.gz | tar xz
sudo mv scorecard /usr/local/bin/
```

**Utilisation :**

```bash
# Analyser un repo GitHub
scorecard --repo=github.com/stephrobert/github-actions-training

# Afficher les détails de chaque check
scorecard --repo=github.com/stephrobert/github-actions-training --show-details

# Analyser le repo local (nécessite un remote GitHub)
scorecard --local .
```

**Checks importants pour GitHub Actions :**

| Check | Description | Comment améliorer |
|-------|-------------|-------------------|
| Token-Permissions | Permissions minimales | Ajouter `permissions:` explicites |
| Pinned-Dependencies | Actions épinglées par SHA | Utiliser `@sha256:...` au lieu de `@v1` |
| Security-Policy | Fichier SECURITY.md | Créer `.github/SECURITY.md` |
| Dependency-Update-Tool | Mises à jour auto | Configurer Dependabot |
| SAST | Analyse statique | Ajouter CodeQL |

---

### Workflow de développement recommandé

Voici le workflow idéal pour développer un fichier GitHub Actions :

```bash
# 1. Créer/modifier le workflow
vim .github/workflows/ci.yml

# 2. Valider la syntaxe
actionlint .github/workflows/ci.yml

# 3. Tester localement (itérer jusqu'à ce que ça marche)
act -j mon-job -v

# 4. Commiter et pousser
git add .github/workflows/ci.yml
git commit -m "feat: add CI workflow"
git push

# 5. Vérifier sur GitHub Actions
gh run watch

# 6. (Optionnel) Vérifier le score de sécurité
scorecard --local=./ --show-details
```

## Ressources complémentaires

### Documentation officielle

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Workflow syntax reference](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions)
- [Security hardening](https://docs.github.com/en/actions/security-guides/security-hardening-for-github-actions)

### Mon blog

- [GitHub Actions](https://blog.stephane-robert.info/docs/pipeline-cicd/github/)
- [Sécurité CI/CD](https://blog.stephane-robert.info/docs/pipeline-cicd/github/securite/)
- [Supply Chain](https://blog.stephane-robert.info/docs/securiser/supply-chain/)

## Contribution

Les contributions sont les bienvenues ! Consultez [CONTRIBUTING.md](CONTRIBUTING.md)
pour les guidelines.

## Licence

Ce projet est sous licence MIT. Voir [LICENSE](LICENSE) pour plus de détails.
