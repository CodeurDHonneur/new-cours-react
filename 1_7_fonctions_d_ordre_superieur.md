### Définition : 

Une fonction d’ordre supérieur (Higher-Order Function) est une fonction qui :

1. prend une ou plusieurs fonctions en argument

2. retourne une fonction

3. ou fait les deux en même temps

Ce type de fonction est un pilier de la programmation fonctionnelle, très courant en JavaScript moderne.

### Pourquoi est-ce utile ?

* Rendre ton code plus flexible
* Éviter la répétition
* Travailler plus facilement avec des listes, des événements, des timers, etc.

### Exemples : 

#### Cas 1 : Elle prend une fonction en paramètre

```js
function appliquerOperation(x, y, operation) {
  return operation(x, y);
}

const resultat = appliquerOperation(4, 2, (a, b) => a + b);
console.log(resultat); // 6

```
Utile pour :

* Appliquer dynamiquement une logique

* Personnaliser un comportement selon le besoin

#### Cas 2 : Elle retourne une fonction

```js
function saluerAvec(prefixe) {
  return function(nom) {
    return `${prefixe}, ${nom} !`;
  };
}

const saluerBonjour = saluerAvec("Bonjour");
console.log(saluerBonjour("Sophie")); // Bonjour, Sophie !
```

Utile pour :

* Créer des fonctions personnalisées

* Garder un "contexte" en mémoire (fermeture ou closure)
 
#### Cas 3 : Elle prend une fonction et retourne une autre fonction

```js
function loggerEtExécuter(fonctionOriginale) {
  return function(...args) {
    console.log("Arguments reçus :", args);
    const resultat = fonctionOriginale(...args);
    console.log("Résultat :", resultat);
    return resultat;
  };
}

const addition = (a, b) => a + b;
const additionAvecLogs = loggerEtExécuter(addition);

additionAvecLogs(3, 5);
// Console : Arguments reçus : [3, 5]
// Console : Résultat : 8

```

Utile pour :

* Ajouter des comportements autour d’une fonction (log, sécurité, validation…)

* Créer des **wrappers** dynamiques et propres

Exemple : **SÉCURITÉ : Protéger l’accès à une fonction**

```js
function avecAuth(fn) {
  return function (user, ...args) {
    if (!user || !user.estAdmin) {
      throw new Error("Accès refusé !");
    }
    return fn(...args);
  };
}

const supprimerUtilisateur = (id) => `Utilisateur ${id} supprimé`;
const supprimerAvecAuth = avecAuth(supprimerUtilisateur);

const admin = { nom: "Alice", estAdmin: true };
supprimerAvecAuth(admin, 42); // OK ✅

const visiteur = { nom: "Bob", estAdmin: false };
supprimerAvecAuth(visiteur, 42); // ❌ Erreur : Accès refusé

```