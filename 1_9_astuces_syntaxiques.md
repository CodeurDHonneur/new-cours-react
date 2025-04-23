### Astuce 1 

```js
const user1 = {
    name: "John Doe",
    age: 42
}

const userProperties = {
    city: "Lausane",
    country: "Suisse"
}

const mergeObject = {
    ...user1,
    ...userProperties
}
```


### Astuce 2

```js
function createUser(firstName, lastName, age, email, password){
    firstName,
    lastName,
    age,
    email,
    password
}

createUser("John", "Doe", 25, "jean@gmail.com", "psw");

//Si il y a plus de deux arguments pour une fonction, l'idéal est d'utiliser la syntaxe de destruturing

function createUser({firstName, lastName, age, email, password}){
    firstName,
    lastName,
    age,
    email,
    password
}

createUser({
    firstName: "John", 
    lastName: "Doe", 
    age: 25, 
    email: "jean@gmail.com", 
    password: "psw"
    });
```


### Astuce 3 

```js
const users = [
    {
        id: 1,
        name: "Michel",
        age: 55
    },
    {
        id: 2,
        name: "Jean",
        age: 77
    }
];


for(let i = 0; i < users.length; i++){
    console.log(`Je me nomme ${users[i].name} et j'ai ${users[i].age} ans`);
}

//Plus explicite et plus simple
for(const { name, age } of users){
    console.log(`Je me nomme ${users[i].name} et j'ai ${users[i].age} ans`);
}

//Dans le cas où on voudrait travailler avec des index
for(const [index, { name, age }] of Object.entries(users)){
    console.log(`${index} - Je me nomme  ${users[i].name} et j'ai ${users[i].age} ans`);
}

```

### Astuce 4 
```js
const usersEmpty = [undefined, null, undefined];

const isEmpty = (arr) => {
    let empty = true;

    //impératif
    for(const item of arr){
        if(item){ //Nous définissons clairement ce qui est fait pour chaque étape
            empty = false;
        }
    }

    return empty;
}

console.log(isEmpty(usersEmpty));

    //déclaratif
const isEmpty = (arr) => {
    
    return !arr.some(v => Boolean(v)); //ou plus simplement !arr.some(Boolean);
}
```


### Astuce 5 : 

```js
const users = [
    {
        id: 1,
        name: "Michel",
        age: 55
    },
    {
        id: 2,
        name: "Didier",
        age: 34
    },
    {
        id: 3,
        name: "Jean",
        age: 77
    },
];

const deleteUser = (users, id) => {
    return users.filter((user) => user.id !== id);
}

const addUser = (users, user) => {
    if(user.find((u) => u.id === user.id)) {
        return users.map((u) => {
            if(u.id === user.id) {
                return user;
            }
            return u;
        });
    }
    return [...users, user];
}

const updateUser = (users, user) => {
    return users.map((u) => {
        if(u.id === user.id){
            return user;
        }
        return u;
    })
}

//Transformer le tableau en Map
const usersMap = new Map(users.map(user => [user.id, user]));

/**
 * sortie
 * Map {
  1 => { id: 1, name: "Michel", age: 55 },
  2 => { id: 2, name: "Didier", age: 34 },
  3 => { id: 3, name: "Jean", age: 77 }
}
 */

//les mêmes méthodes mais cette fois avec Map
const addOrUpdateUser = (usersMap, user) => {
  usersMap.set(user.id, user);
}

const deleteUser = (usersMap, id) => {
  usersMap.delete(id);
}

const user = usersMap.get(2); // rapide et clair

```


### Astuce 6 : 

```js
const array = Array.from({
    length: 10
}, (v, i) => i);
console.log(array); // [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```


### Astuce 7 : 

```js
    const users = [
    {
        id: 1,
        name: "Michel",
        age: 55
    },
    {
        id: 2,
        name: "Didier",
        age: 34
    },
    {
        id: 3,
        name: "Jean",
        age: 77
    },
];

console.table(users);
```