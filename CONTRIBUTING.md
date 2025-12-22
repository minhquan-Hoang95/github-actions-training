# Guide de contribution

Merci de votre intérêt pour contribuer à ce projet de formation GitHub Actions !

## Comment contribuer

### Signaler un problème

1. Vérifiez que le problème n'a pas déjà été signalé
2. Créez une issue avec un titre clair
3. Décrivez le problème et les étapes pour le reproduire

### Proposer une amélioration

1. Forkez le dépôt
2. Créez une branche (`git checkout -b feature/amelioration`)
3. Commitez vos changements (`git commit -m 'feat: ajout de...'`)
4. Pushez (`git push origin feature/amelioration`)
5. Ouvrez une Pull Request

## Structure d'un TP

Chaque TP doit suivre cette structure :

```
tp-XX-nom-du-tp/
├── README.md           # Énoncé avec tutoriels
├── challenge/
│   ├── README.md       # Instructions du challenge
│   ├── .github/
│   │   └── workflows/  # Workflows à compléter
│   └── validate.sh     # Script de validation
└── solution/           # Solution (optionnel, pour les formateurs)
```

## Conventions

### Commits

Suivez [Conventional Commits](https://www.conventionalcommits.org/) :

- `feat:` nouvelle fonctionnalité
- `fix:` correction de bug
- `docs:` documentation
- `chore:` maintenance

### Style

- Markdown pour les README
- YAML valide pour les workflows (utilisez actionlint)
- Exemples testables et reproductibles

## Tests

Avant de soumettre, vérifiez que :

1. Les workflows sont syntaxiquement valides
2. Les tests de validation passent
3. La documentation est à jour
