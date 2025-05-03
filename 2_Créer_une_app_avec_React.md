<<<<<<< HEAD
## 📘 2. Créer une app avec React
=======
# 📘 2. Créer une app avec React
>>>>>>> 4f132a7bf197bf994ea4249e75a8f92d1e6aa83c

### 🧠 Qu'est-ce qu'une application web ?

Une **application web** est un programme accessible via un navigateur. Contrairement à un site web classique qui affiche simplement des pages statiques (HTML/CSS), une app web peut :
- gérer des interactions complexes (formulaires, navigation dynamique…),
- afficher du contenu personnalisé,
- communiquer avec un serveur via des API (backend),
- modifier l’interface sans recharger la page (grâce à JavaScript et souvent un framework comme **React**).

👉 Exemples : Gmail, Trello, Google Docs, Spotify Web.

---

### 📦 Un **bundler**, qu’est-ce que c’est ?

Un **bundler** est un outil qui :
- regroupe tous les fichiers (`.js`, `.jsx`, `.css`, `.svg`…),
- les transforme (transpile du JSX en JS, SCSS en CSS, etc.),
- optimise (compression, minification…),
- prépare le projet pour le développement *et* la production.

👉 Les plus connus :
- **Webpack** (utilisé par Create React App),
- **Vite** (rapide, moderne),
- **Parcel**, **Rollup**...

---

### ⚛️ Utiliser React **sans un bundler**

Oui, c’est possible ! On peut utiliser React en important directement les scripts via un CDN :

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>React sans bundler</title>
    <script src="https://unpkg.com/react@18/umd/react.development.js" crossorigin></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js" crossorigin></script>
    <script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
  </head>
  <body>
    <div id="root"></div>
    <script type="text/babel">
      const App = () => <h1>Hello React sans bundler 👋</h1>;
      ReactDOM.createRoot(document.getElementById('root')).render(<App />);
    </script>
  </body>
</html>
```

✅ C’est bien pour apprendre, mais pas adapté pour une vraie app car :
- pas d’optimisation,
- pas de gestion de fichiers,
- pas de modules modernes,
- pas de compilation automatique.

---

### ⚙️ Créer une app React avec **Vite** + explication de l’architecture

#### 📦 Étapes d'installation

```bash
npm create vite@latest mon-app-react
cd mon-app-react
npm install
npm run dev
```

> Sélectionne `React` puis `JavaScript` ou `TypeScript`.

---

#### 🗂️ Architecture des dossiers

```plaintext
mon-app-react/
├── node_modules/         → Dépendances installées
├── public/               → Fichiers statiques (favicon, images, etc.)
│   └── vite.svg
├── src/                  → Ton code source
│   ├── App.jsx           → Composant principal
│   ├── main.jsx          → Point d'entrée React (montage dans index.html)
│   └── index.css         → Styles globaux
├── .gitignore            → Fichiers à ignorer par Git
├── index.html            → Fichier HTML principal, utilisé par Vite
├── package.json          → Infos du projet + dépendances
├── tailwind.config.js    → (si tu utilises Tailwind)
├── postcss.config.js     → (si tu utilises Tailwind ou PostCSS)
└── vite.config.js        → Configuration spécifique de Vite
```

---

#### 🎯 Ce que fait chaque fichier :
- **`main.jsx`** : le fichier qui lance React, il rend `<App />` dans le DOM.
- **`App.jsx`** : ton composant principal, point de départ de l'interface.
- **`index.html`** : seul fichier HTML, Vite injecte le JS dedans.
- **`vite.config.js`** : permet de personnaliser le comportement de Vite.

---