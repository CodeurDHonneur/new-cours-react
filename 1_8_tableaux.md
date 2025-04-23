## Tableaux
### Définition : 
**Un tableau** en JavaScript est un objet utilisé pour stocker plusieurs valeurs dans une seule variable.

### Déclaration : 
Les tableaux peuvent être créés en utilisant des crochets `[]` ou le constructeur `Array`.

```js
// Utilisation des crochets
let fruits = ["pomme", "banane", "cerise"];

// Utilisation du constructeur Array
let nombres = new Array(1, 2, 3, 4, 5);
```
### Accéder aux données d'un tableau simple
Les tableaux sont indexés à partir de `zéro`: le premier élément d'un tableau a pour indice `0`, et la position du dernier élément est donnée par la propriété `.length` (propriété permettant d'avoir la taille d'un tableau) moins `1`.

**NB**: Si on utilise un indice en dehors de cet intervalle, le résultat sera `'undefined'`

```js
let fruits = ["pomme", "banane", "cerise"];
console.log(fruits[0]); // "pomme"
console.log(fruits[1]); // "banane"
console.log(fruits[2]) || console.log(fruits[fruits.length - 1]); // "cerise"

```

### Modifier les données d'un tableau simple

```js
let fruits = ["pomme", "banane", "cerise"]; 
fruits[0] = "avocat"; // Notre tableau vaudra maintenant ["avocat", "banane", "cerise"]
fruits[5] = "papaye"; // Notre tableau vaudra désormais ["avocat", "banane", "cerise", undefined, undefined, "papaye"]
```

**NB**: le tableau `fruits` est modifié pour inclure des valeurs `'undefined'` aux indices `3` et `4`, car ils n'ont pas été explicitement définis., mais il est important de noter que la création de `"trous"` dans un tableau (indices non définis) peut parfois conduire à des comportements inattendus ou à des difficultés lors de la manipulation du tableau.

### Tableaux imbriqués
Les tableaux peuvent contenir tout type de variables, y compris des tableaux. Quand un tableau ne contient que des variables qui sont à leur tour des tableaux, on parlera de tableauX `imbriqués` ou `multidimensionnels`

Exemple : 
```js
let matrice = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];

```

### Accéder aux données d'un tableau imbriqué
Considérant un tableau 2D, pour trouver un élément spécifique, vous devez d'abord choisir le bon sous-tableau, puis l'élément à l'intérieur de ce sous-tableau.

```js
let matrice = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];

// Accéder aux éléments
console.log(matrice[0][0]); // Affiche 1
console.log(matrice[1][2]); // Affiche 6
console.log(matrice[2][1]); // Affiche 8
```

// Modifier un élément

Avant => `console.log(matrice[0][1]);` // Affiche 2

```js
matrice[0][1] = 10;
```

Après => `console.log(matrice[0][1]);` // Affiche 10

### 10 Méthodes importantes sur les tableaux

#### 1. map()
Sert à transformer chaque élément d’une liste. 

Exemple : 
```js
const array1 = [1, 4, 9, 16];
const map1 = array1.map((x) => x * 2);
console.log(map1); //Réponse:  [2, 8, 18, 32]
```

#### 2. filter()

sert à examiner chaque élément d’une liste et à ne garder que ceux qui respectent une condition précise. 

Exemple : 

Tu as un panier de fruits : 🍎🍌🍎🍇🍌. 
Tu veux ne garder que les pommes 🍎. 

`filter()` va vérifier chaque fruit et garder seulement les pommes. 
Résultat : 🍎🍎.   
En résumé : `filter()` te permet de sélectionner dans une liste uniquement les éléments qui respectent une règle que tu définis. Tout le reste est ignoré.

#### 3. reduce() 
Sert à combiner tous les éléments pour en faire un seul (exemple : une somme). 

```js
const coins = [10, 20, 30];
const total = coins.reduce((sum, coin) => sum + coin, 0);
console.log(total); //
/**
 * Explication du code :
 * coins est ta liste : [10, 20, 30].
 * reduce() fonctionne comme ceci :
 * ** Début : La somme (sum) commence à 0. 
 * ** Étape 1 : Ajoute 10 → 0 + 10 = 10.
 * ** Étape 2 : Ajoute 20 → 10 + 20 = 30.
 * ** Étape 3 : Ajoute 30 → 30 + 30 = 60.
 * ** Résultat final : 60.
 */
   
```
#### 4. find() 
parcourt la liste et s’arrête dès qu’il trouve le premier élément qui correspond à ce que tu cherches. Tout ce qui vient après est ignoré.

Exemple :

```js
const age = [15, 18, 21, 14];
const fruitAdult = ages.find(age => age >= 18);
console.log(fruitAdult); //Affiche : 18
/**
 * Explication du code : 
 * ages : Ta liste des âges. 
 * find() : Cherche le premier âge qui est supérieur ou égal à 18.
 * Résultat : 18, car c’est le premier âge qui respecte la condition. 😊
 */
```
#### 5. push()
Sert à ajouter un élément à la fin d’une liste. 

```js
let fruits = ["pomme", "banane", "cerise"]; 

let countArray = fruits.push("avocat"); 
// frutis = ["pomme", "banane", "cerise", "avocat"] 
// countArray vaudra 4 (la nouvelle longueur du tableau)

const count = fruits.push("papaye", "ananas", "mandarine"); 
// fruits = ["pomme", "banane", "cerise", "avocat", "papaye", "ananas", "mandarine"]
count vaudra 7 (la nouvelle longueur du tableau)

```
#### 6. pop() 
Sert à retirer le dernier élément d’une liste. 

Exemple :

```js
let fruits = ["pomme", "banane", "orange"]; 
const removedFruit = fruits.pop();
console.log(fruits); // Affiche ["pomme", "banane"]
console.log(removedFruit); // Affiche : "orange"
/**
 * Explication du code : ["pomme", "banane", "orange"]. 
 * Tu veux enlever orange, qui est le dernier fruit. 
 * Résultat final : ["pomme", "banane"]
 */
```

#### 7. shift() 
La méthode `shift()` permet de retirer le premier élément d'un tableau et de renvoyer cet élément. Elle  modifie donc la longueur du tableau.

```js
let fruits = ["pomme", "banane", "cerise"]; 
const firstElement = fruits.shift();

// fruits = ["banane", "cerise"]
console.log(firstElement); // affiche "pomme"
```
#### 8. unshift() 
Cette méthode ajoute un ou plusieurs éléments au début d'un tableau et renvoie la nouvelle longueur du tableau.

```js
let fruits = ["pomme", "banane", "cerise"]; 
const count = fruits.unshift("papaye", "ananas");

// fruits = ["papaye", "ananas", "pomme", "banane", "cerise"]
console.log(count); // affiche 5

```

#### 9. slice() 
Sert à copier une partie d’une liste. 

Exemple :

```js
const fruits = ["pomme", "banane", "orange", "kiwi"];

const selectedFruits = fruits.slice(1, 3);
console.log(selectedFruits); //Affiche ["banane", "orange"]
/**
 * Explication du code :
 * Tu as une liste de fruits : ["pomme", "banane", "orange", "kiwi"].
 * Tu veux copier seulement banane et orange. 
 * Résultat final : ["banane", "orange"].
 */
```

#### 10. splice()
Sert à ajouter, enlever ou remplacer des éléments dans une liste. 

Exemple :

* Pour ajouter : 
```js
const fruits = ["pomme", "kiwi"];
fruits.splice(1, 0, "banane"); //a l'index 1, ajoute "banane"
console.log(fruits); // Affiche : ["pomme", "kiwi", "banane"]

/**
 * Explication du code : 
 * Tu as une liste de fruits : ["pomme", "kiwi"]. 
 * Tu veux ajouter banane entre pomme et kiwi. 
 * Résultat final : ["pomme", "banane", "kiwi"]. 
 */

```
* Pour enlever : 
```js
const fruits = ["pomme", "banane", "kiwi"];
fruits.splice(1, 1);
console.log(fruits); // Affiche : ["pomme", "kiwi"]
```


### Exercices 

##### Exercice 1 : Téléportation et Fusion

Difficulté: Medium

Il vous est donné deux tableaux et un index. Créez une fonction frankenSplice(arr1, arr2, index). Copiez dans l'ordre chaque élément du premier tableau dans le second tableau. Commencez par insérer les éléments à l'index n du second tableau. Retournez le tableau final. NB: Les tableaux de départ reste inchangés après l'exécution des fonctions.

Tests:

frankenSplice([1, 2, 3], [4, 5], 1) devrait retourner [4, 1, 2, 3, 5] frankenSplice([1, 2], ["a", "b"], 1) devrait retourner ["a", 1, 2, "b"] frankenSplice(["claw", "tentacle"], ["head", "shoulders", "knees", "toes"], 2) devrait retourner ["head", "shoulders", "claw", "tentacle", "knees", "toes"] Tous les éléments du premier tableau devrait être additionnés au second tout en respectant l'ordre de départ. frankenSplice([1, 2, 3, 4], [], 0) devrait retourner [1, 2, 3, 4]

##### Exercice 2 :  Où devrais-je être

Difficulté: Moyenne

Créez une fonction getIndexToIns(arr, toInsert). Renvoiez l'indice le plus bas auquel une valeur (deuxième argument) doit être insérée dans un tableau (premier argument) une fois qu'il a été trié. La valeur renvoyée doit être un nombre.

Par exemple, getIndexToIns([1,2,3,4], 1.5) doit retourner 1 car il est supérieur à 1(index 0), mais inférieur à 2(index 1).

De même, getIndexToIns([20,3,5], 19) devrait retourner 2 car une fois le tableau trié, il ressemblera à [3,5,20] et 19 est inférieur à 20 (index 2) et supérieur à 5 (index 1).

Tests:

getIndexToIns([10, 20, 30, 40, 50], 35) devrait renvoyer 3. getIndexToIns([10, 20, 30, 40, 50], 35) devrait renvoyer un nombre. getIndexToIns([10, 20, 30, 40, 50], 30) devrait renvoyer 2. getIndexToIns([10, 20, 30, 40, 50], 30) devrait renvoyer un nombre. getIndexToIns([40, 60], 50) devrait renvoyer 1. getIndexToIns([40, 60], 50) devrait renvoyer un nombre. getIndexToIns([3, 10, 5], 3) devrait renvoyer 0. getIndexToIns([3, 10, 5], 3) devrait renvoyer un nombre. getIndexToIns([5, 3, 20, 3], 5) devrait renvoyer 2. getIndexToIns([5, 3, 20, 3], 5) devrait renvoyer un nombre. getIndexToIns([2, 20, 10], 19) devrait renvoyer 2. getIndexToIns([2, 20, 10], 19) devrait renvoyer un nombre. getIndexToIns([2, 5, 10], 15) devrait renvoyer 3. getIndexToIns([2, 5, 10], 15) devrait renvoyer un nombre. getIndexToIns([], 1) devrait renvoyer 0. getIndexToIns([], 1) devrait renvoyer un nombre.