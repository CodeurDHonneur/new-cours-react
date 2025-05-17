La **persistance des données** dans React est essentielle pour garder des informations même quand on navigue entre les pages ou quand on actualise.
Voici un **cours complet** en utilisant le **composant `Profil`** comme base et en intégrant un **Provider de contexte** + **localStorage** pour persister les données.

---

## 📘 Objectif du cours

> Permettre à l'utilisateur de modifier son profil (nom, email...)
> et que ces informations restent disponibles même après actualisation de la page (persistance locale).

---

## 🧩 Étapes de mise en œuvre

### 1. Créer le **Contexte global (`UserContext.jsx`)**

```jsx
import { createContext, useState, useEffect } from "react";

// Création du contexte
export const UserContext = createContext();

// Provider global
export function UserProvider({ children }) {
  const [user, setUser] = useState({
    name: "",
    email: "",
    bio: ""
  });

  // Charger les données depuis localStorage au démarrage
  useEffect(() => {
    const storedUser = localStorage.getItem("user");
    if (storedUser) {
      setUser(JSON.parse(storedUser));
    }
  }, []);

  // Sauvegarder automatiquement dans localStorage à chaque modification
  useEffect(() => {
    localStorage.setItem("user", JSON.stringify(user));
  }, [user]);

  return (
    <UserContext.Provider value={{ user, setUser }}>
      {children}
    </UserContext.Provider>
  );
}
```

---

### 2. Utiliser le Provider dans `App.jsx`

```jsx
import { BrowserRouter, Routes, Route } from "react-router-dom";
import { UserProvider } from "./context/UserContext";
import Profil from "./pages/Profil";
import Parametres from "./pages/Parametres";
import Layout from "./components/Layout"; // avec Outlet

function App() {
  return (
    <UserProvider>
      <BrowserRouter>
        <Routes>
          <Route path="/" element={<Layout />}>
            <Route path="profil" element={<Profil />} />
            <Route path="parametres" element={<Parametres />} />
          </Route>
        </Routes>
      </BrowserRouter>
    </UserProvider>
  );
}

export default App;
```

---

### 3. Créer le composant `Profil.jsx` (modification + persistance)

```jsx
import { useContext, useState, useEffect } from "react";
import { UserContext } from "../context/UserContext";

function Profil() {
  const { user, setUser } = useContext(UserContext);
  const [formData, setFormData] = useState(user);

  // Réinitialiser le formulaire si les données changent (par navigation)
  useEffect(() => {
    setFormData(user);
  }, [user]);

  const handleChange = (e) => {
    const { name, value } = e.target;
    setFormData(prev => ({ ...prev, [name]: value }));
  };

  const handleSave = () => {
    setUser(formData); // Met à jour le contexte (et donc le localStorage)
    alert("Profil mis à jour !");
  };

  return (
    <div style={styles.container}>
      <h2>Mon Profil</h2>
      <div style={styles.card}>
        <label>Nom :</label>
        <input name="name" value={formData.name} onChange={handleChange} />

        <label>Email :</label>
        <input name="email" value={formData.email} onChange={handleChange} />

        <label>Bio :</label>
        <textarea name="bio" value={formData.bio} onChange={handleChange} />

        <button style={styles.btn} onClick={handleSave}>Enregistrer</button>
      </div>
    </div>
  );
}

const styles = {
  container: { padding: "20px" },
  card: {
    display: "flex",
    flexDirection: "column",
    gap: "10px",
    backgroundColor: "#f5f5f5",
    padding: "20px",
    maxWidth: "400px",
    borderRadius: "10px"
  },
  btn: {
    marginTop: "10px",
    padding: "10px",
    backgroundColor: "#0077cc",
    color: "white",
    border: "none",
    borderRadius: "5px"
  }
};

export default Profil;
```

---

## ✅ Résultat

* ✔️ Les infos utilisateur sont modifiables via un formulaire.
* ✔️ Elles sont stockées dans le **contexte React** (`UserContext`).
* ✔️ Elles sont **persistées dans `localStorage`**, donc disponibles même après un `F5`.

---

## 🔍 Récapitulatif des notions apprises

| Concept React            | Ce qu'on a fait                               |
| ------------------------ | --------------------------------------------- |
| `createContext()`        | Créer un état global partagé                  |
| `useContext()`           | Accéder/modifier les données partagées        |
| `useEffect()`            | Lire et écrire dans le `localStorage`         |
| `useState()`             | Stocker les valeurs dans le formulaire        |
| `localStorage` (Web API) | Persister les données même après rechargement |

---

