# Spread syntax(...)

```js
let arr1 = [0, 1, 2];
let arr2 = [3, 4, 5];
arr1 = [...,arr1 ...arr2];
// Array [0, 1, 2, 3, 4, 5]

let arr1 = [{name: 'user1'},{name: 'user2'},{name: 'user2'}];
let arr2 = [3, 4, 5];
arr1 = [...arr1, ...arr2];
//Array [Object { name: "user1" }, Object { name: "user2" }, Object { name: "user2" }, 3, 4, 5]

let arr1 = [{name: 'user1'},{name: 'user2'},{name: 'user3'}];
let data = {name:'user2', age: '10'}

arr1 = [data, ...arr1];
//Array [Object { name: "user2", age: "10" }, Object { name: "user1" }, Object { name: "user2" }, Object { name: "user3" }]
```



```js

```

