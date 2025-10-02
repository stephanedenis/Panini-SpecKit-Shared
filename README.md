# PaniniFS-SpecKit-Shared

Repository central pour configurations GitHub Spec-Kit partagées dans l'écosystème Panini (14+ projets).

**Version**: 1.0.0  
**Maintainer**: @stephanedenis  
**License**: Apache 2.0

---

## 🎯 Purpose

Ce repository contient les configurations, règles et templates **partagés** entre tous les projets de l'écosystème Panini. Il est intégré comme **Git submodule** dans chaque projet pour assurer la cohérence des standards de développement.

### Projets Utilisant ce Shared Repository

1. **Panini** (main) - Projet principal 50k+ files
2. **PaniniFS-Research** - Recherche compression sémantique
3. **Panini-OntoWave** - Analyse ondes sémantiques (projet pilote)
4. **PaniniFS** - Filesystem virtuel basé grammaire Pāṇini
5. **PaniniFS-AttributionRegistry** - Registre attributions contributeurs
6. **PaniniFS-AutonomousMissions** - Système missions autonomes
7. **PaniniFS-CloudOrchestrator** - Orchestrateur cloud
8. **PaniniFS-SemanticCore** - Noyau opérations sémantiques
9. **Panini-Gest** - Gestion projet
10. ... et 5+ autres projets

---

## 📁 Structure

```
PaniniFS-SpecKit-Shared/
├── .specify/                    # Configuration Spec-Kit
│   ├── memory/
│   │   └── constitution.md
│   ├── scripts/
│   └── templates/
├── constitutions/               # Constitutions partagées
│   └── panini-universal-constitution.md
├── templates/                   # Templates Spec-Kit
│   ├── feature-spec-template.md
│   ├── api-spec-template.md
│   └── refactor-spec-template.md
├── rules/                       # Règles YAML partagées
│   ├── code-standards.yml
│   ├── conventional-commits.yml
│   └── pull-requests.yml
├── README.md                    # Ce fichier
└── CHANGELOG.md                 # Historique versions
```

---

## 🚀 Installation dans un Projet

### Étape 1 : Ajouter comme Submodule

```bash
cd /path/to/your/project
git submodule add https://github.com/stephanedenis/PaniniFS-SpecKit-Shared.git .specify/shared
git submodule update --init --recursive
```

### Étape 2 : Créer `.specify/config.yml`

```yaml
# .specify/config.yml
shared_constitution: .specify/shared/constitutions/panini-universal-constitution.md
project_constitution: .specify/memory/constitution.md

rules:
  - .specify/shared/rules/code-standards.yml
  - .specify/shared/rules/conventional-commits.yml
  - .specify/shared/rules/pull-requests.yml

templates:
  feature: .specify/shared/templates/feature-spec-template.md
  api: .specify/shared/templates/api-spec-template.md
```

### Étape 3 : Référencer dans Constitution Projet

```markdown
<!-- Dans .specify/memory/constitution.md -->

# Constitution [Votre Projet]

## Base Universelle
Cette constitution étend la [Constitution Universelle Panini](../shared/constitutions/panini-universal-constitution.md).

## Spécificités Projet
[Vos règles spécifiques...]
```

### Étape 4 : Commit & Push

```bash
git add .gitmodules .specify/shared .specify/config.yml
git commit -m "🔗 Intégrer PaniniFS-SpecKit-Shared via submodule"
git push origin main
```

---

## 🔄 Synchroniser avec Latest Version

Quand le shared repository est mis à jour :

```bash
cd /path/to/your/project

# Mettre à jour le submodule vers la dernière version
git submodule update --remote .specify/shared

# Vérifier les changements
git diff .specify/shared

# Commit la mise à jour
git add .specify/shared
git commit -m "⬆️ Sync PaniniFS-SpecKit-Shared vers latest"
git push origin main
```

---

## 📋 Contenu

### Constitution Universelle
[`constitutions/panini-universal-constitution.md`](constitutions/panini-universal-constitution.md)

Définit les principes architecturaux, standards de développement, et processus communs à tous les projets Panini :
- Mission & Vision écosystème
- Principes architecturaux (séparation concerns, universalité, réversibilité)
- Standards techniques (Python 3.11+, ISO 8601, Git conventional commits)
- Workflow Spec-Driven (issue → /constitution → /specify → /plan → /implement)
- Métriques & KPIs (compression ≥40%, latency <100ms, coverage ≥80%)

### Templates Spec-Kit

#### Feature Specification
[`templates/feature-spec-template.md`](templates/feature-spec-template.md)

Template standardisé pour spécifier nouvelles fonctionnalités :
- Objectif & problème à résoudre
- Requirements fonctionnels & non-fonctionnels
- Design technique & architecture
- User stories & acceptance criteria
- Testing strategy & success metrics
- Implementation plan & risks

#### API Specification
[`templates/api-spec-template.md`](templates/api-spec-template.md)

Template pour spécifier APIs REST/GraphQL (à créer).

### Règles Partagées

#### Code Standards
[`rules/code-standards.yml`](rules/code-standards.yml)

Standards de qualité code :
- Formatting (black, pylint)
- Type hints requis
- Docstrings Google style
- Test coverage ≥80%

#### Conventional Commits
[`rules/conventional-commits.yml`](rules/conventional-commits.yml)

Format commits Git standardisé :
```
type(scope): description

feat: Nouvelle fonctionnalité
fix: Correction bug
docs: Documentation
refactor: Refactorisation
test: Tests
chore: Maintenance
```

#### Pull Requests
[`rules/pull-requests.yml`](rules/pull-requests.yml)

Processus code review :
- 2 reviewers minimum
- Tests CI/CD passent
- Documentation mise à jour
- CHANGELOG.md modifié

---

## 🛠️ Maintenance

### Modifier la Constitution Universelle

1. Créer issue GitHub expliquant la modification
2. Créer PR avec changements dans `constitutions/`
3. Review par maintainers
4. Vote si changement majeur
5. Merge + tag nouvelle version
6. Notifier tous les projets de mettre à jour submodule

### Ajouter un Nouveau Template

1. Créer le template dans `templates/`
2. Documenter dans ce README
3. Créer PR + review
4. Merge + tag version MINOR

### Modifier une Règle YAML

1. Issue GitHub avec justification
2. PR avec modification dans `rules/`
3. Tester sur projet pilote (Panini-OntoWave)
4. Merge si validation OK
5. Tag version PATCH

---

## 📊 Versioning

Semantic Versioning : `MAJOR.MINOR.PATCH`

- **MAJOR** : Breaking change (ex: renommer règle, supprimer template)
- **MINOR** : Nouveau template, nouvelle règle (backward-compatible)
- **PATCH** : Correction typo, amélioration doc

### Releases
- [v1.0.0] - 2025-10-02 : Initial release (constitution + 3 règles YAML + 2 templates)

---

## 🤝 Contributing

Ce repository est **central** pour l'écosystème Panini. Toute modification doit :

1. **Créer issue GitHub** expliquant besoin
2. **Tester sur projet pilote** (Panini-OntoWave)
3. **PR avec review** par au moins 2 maintainers
4. **Documentation** mise à jour (README, CHANGELOG)
5. **Notification** tous les projets dépendants

### Contact
- **Maintainer** : @stephanedenis
- **Issues** : https://github.com/stephanedenis/PaniniFS-SpecKit-Shared/issues
- **Discussions** : GitHub Discussions

---

## 📚 References

- [GitHub Spec-Kit Official](https://github.com/github/spec-kit)
- [Spec-Kit Documentation](https://github.com/github/spec-kit/tree/main/docs)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [Semantic Versioning](https://semver.org/)

---

## 📄 License

Apache License 2.0 - See [LICENSE](LICENSE) file for details.

---

**Dernière mise à jour** : 2025-10-02  
**Version** : 1.0.0  
**Projets intégrés** : 1/14 (PaniniFS-Research) - Migration en cours
