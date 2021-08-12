import usesState:

```js
import { useState } from 'react';
```



declare:

```js
const[name,setName] = useState(value);
eg:
const[name,setName] = useState('test');
```



set

```js
const clickFunction = () =>{
    setName('testtest');
}
```

view

```js
<Button title='click me' onPress={clickFunction}/>
```

