# 🧩 Les Template Strings en JavaScript

## Qu’est-ce que c’est ?

Les **template strings** (ou *template literals*) sont une façon moderne d’écrire des chaînes de caractères en JavaScript (introduites avec ES6). 

Elles offrent une syntaxe plus pratique, surtout pour :
- insérer des variables (interpolation)
- écrire des chaînes sur plusieurs lignes
- améliorer la lisibilité du code

Elles utilisent des **backticks** : `` ` `` au lieu de simples ou doubles guillemets.

---

## ✅ Syntaxe de base

```js
const nom = "Alice";
const message = `Bonjour, ${nom} !`;
console.log(message); // Bonjour, Alice !
```

## Avantages

### 1. Interpolation de variables

```js
const produit = "chaussures";
const prix = 59.99;

const phrase = `Le produit ${produit} coûte ${prix}€`;
console.log(phrase);
```

---

### 2. Chaînes multi-lignes

```js

const texte = `Ceci est une chaîne
écrite sur plusieurs
lignes.`;
console.log(texte);
```
---

### 3. Intégration d'expressions

```js

const a = 4;
const b = 6;

const resultat = `Le résultat est : ${a + b}`;
console.log(resultat); // Le résultat est : 10
```