# Classroom

Prototype front-end statique (HTML/CSS) d'une plateforme de classes virtuelles : connexion, tableau de bord administrateur et salle de classe en direct.

## Aperçu

- **`index.html`** : Écran de connexion.
- **`dashboard.html`** : Tableau de bord administrateur (statistiques, planning, classes en direct).
- **`classe.html`** : Salle de classe virtuelle (vidéo, participants, chat).

Aucune installation requise : il s'agit de pages HTML statiques avec une unique feuille de style, sans build ni backend.

## Lancer le projet

```bash
python -m http.server 8000
```

Puis ouvrir `http://localhost:8000/index.html`.

## Arborescence

```
classe-virtuelle/   
├──📄index.html       
├──📄dashboard.html    
├──📄classe.html      
├──📁css/              
│   └──📄style.css            
├──📁favicon/
│   ├──📄favicon.svg
│   ├──📄favicon.ico
│   ├──📄favicon-16x16.png
│   ├──📄favicon-32x32.png
│   ├──📄apple-touch-icon.png
│   ├──📄android-chrome-192x192.png
│   ├──📄android-chrome-512x512.png
│   └──📄site.webmanifest
├──📄.gitignore      
├──📄CLAUDE.md       
└──📄README.md       
```


