# Cours de Programmation Python - POO et SOLID

Cours complet sur la Programmation Orientée Objet et les principes SOLID en Python.

## Démarrage rapide

### 1. Réorganiser le projet (si nécessaire)

Si votre projet est en désordre, exécutez le script de réorganisation :

```bash
chmod +x reorganize.sh
./reorganize.sh
```

### 2. Installer Quarto

Si ce n'est pas déjà fait :
- [Télécharger Quarto](https://quarto.org/docs/get-started/)

### 3. Prévisualiser le site

```bash
quarto preview
```

Cela ouvrira votre navigateur avec une prévisualisation en direct du site.

### 4. Générer le site statique

```bash
quarto render
```

Les fichiers HTML seront générés dans le dossier `_site/`.

## Structure du projet

```
lesson/
├── _quarto.yml              # Configuration Quarto
├── index.qmd                # Page d'accueil
├── cours/                   # Tous les cours
│   └── poo-solid/          # Cours POO et SOLID
│       ├── index.qmd       # Contenu principal
│       └── exercices.qmd   # Exercices pratiques
├── notebooks/               # Notebooks Jupyter par thématique
│   ├── poo/                # Notebooks POO et SOLID
│   │   ├── cours_poo_solid_complet.ipynb
│   │   └── preparation_cours.ipynb
│   └── [autres_cours]/     # Futurs cours
├── _site/                   # Site généré (git ignoré)
├── .quarto/                 # Cache Quarto (git ignoré)
└── README.md               # Ce fichier
```

## Contenu du cours

### Programmation Orientée Objet
- Classes et instances
- Méthodes magiques (`__str__`, `__eq__`)
- Dataclasses
- Encapsulation
- Héritage
- Polymorphisme

### Décorateurs Python
- `@property` - Propriétés gérées
- `@staticmethod` - Méthodes utilitaires
- `@classmethod` - Méthodes de classe
- `@abstractmethod` - Classes abstraites

### Principes SOLID
- **S** - Single Responsibility Principle
- **O** - Open/Closed Principle
- **L** - Liskov Substitution Principle
- **I** - Interface Segregation Principle
- **D** - Dependency Inversion Principle

## Utilisation

### Pour suivre les cours

1. **Version web** : Accédez au site publié sur GitHub Pages
2. **Version notebook** : aller sur le lien blinder du cours
3. **Exercices** : Consultez la page d'exercices pour pratiquer

### Pour modifier / créer un cours

1. Modifiez les fichiers `.qmd` pour personnaliser le contenu
2. Ajoutez de nouveaux chapitres dans le dossier `cours/`
3. Mettez à jour `_quarto.yml` pour refléter la nouvelle structure

## Publication sur GitHub Pages

### Configuration automatique

1. Dans votre dépôt GitHub, allez dans **Settings** > **Pages**
2. Source : **Deploy from a branch**
3. Branch : **main**, Folder : **/ (root)** ou **/docs** selon votre config

### Méthode avec GitHub Actions (recommandée)

Créez `.github/workflows/publish.yml` :

```yaml
name: Publish Quarto Site

on:
  push:
    branches: [main]

jobs:
  build-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - uses: quarto-dev/quarto-actions/setup@v2
      
      - name: Render Quarto Project
        run: quarto render
      
      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./_site
```

## Personnalisation

### Modifier le thème

Dans `_quarto.yml`, changez le thème :

```yaml
format:
  html:
    theme: 
      light: flatly  # ou: cosmo, united, journal, etc.
      dark: darkly
```

### Ajouter un nouveau cours

1. Créez un nouveau dossier : `cours/nouveau-cours/`
2. Ajoutez un fichier `index.qmd`
3. Mettez à jour `_quarto.yml` 
4. Faites uv pip compile pyproject.toml -o requirements.txt:

```yaml
website:
  navbar:
    left:
      - text: "Cours"
        menu:
          - text: "POO et SOLID"
            href: cours/poo-solid/index.qmd
          - text: "Nouveau Cours"
            href: cours/nouveau-cours/index.qmd
```

### Ajouter un notebook pour un nouveau cours

Créez un dossier dans `notebooks/` :

```bash
mkdir -p notebooks/nouveau_cours
# Ajoutez vos notebooks .ipynb dans ce dossier
```

## Dépendances Python (pour les notebooks)

Si vous voulez exécuter les notebooks :

```bash
pip install jupyter notebook
```

## Contribution

Les contributions sont les bienvenues. N'hésitez pas à :
- Signaler des erreurs
- Proposer des améliorations
- Ajouter des exemples

## Licence

[Votre licence ici]

## Contact

[Vos informations de contact]
