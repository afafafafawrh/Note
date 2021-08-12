

```js
const[age,setAge] = useState(10);


<TextInput
    multiline
    keyboardType = 'numeric'
    placeholder = 'input something'    
    onChangeText= { (val => setAge(val))}
/>
```

