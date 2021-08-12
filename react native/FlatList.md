array Data

```js
const[people,setPeople] = useState([
    {name: '', id:1},
    {name: '', id:2},
    {name: '', id:3},
    {name: '', id:4},
    {name: '', id:5},
    {name: '', id:6},
    {name: '', id:7},
    {name: '', id:8},
  ]);
```

## FlatList  remderItem

```js
renderItem({ item, index, separators });
```

## FlatList declare

```js
 <FlatList
    keyExtractor = {(item)=>item.id}
    data = {people}
    renderItem = {({item})=> (
        <Text style = {styles.itemLayout}> {item.name} </Text>
	)}
/>
```



## Actually equal to 

```js
<FlatList
    keyExtractor = {(item)=>item.id}
    data = {people}
    renderItem={(props) => ( 
        <Text style={styles.itemLayout}>{props.item.name}</Text>
    )}
/>

```



## Destructuring practice for me

```js
<FlatList
    keyExtractor = {(item)=>item.id}
    data = {people}
    renderItem = {({item : {name} })=> (
        <Text style = {styles.itemLayout}>{name}</Text>
    )}
/>
```

