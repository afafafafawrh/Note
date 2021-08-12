##### customerHeader.js in compontent folder

```js
import React, { useState } from 'react';
import { StyleSheet, Text, View } from 'react-native';

export default function customerHeader(){
    return (
        <View style = {styles.header}>  
            <Text> Header </Text>
        </View>
    )
}

const styles = StyleSheet.create({
    header:{
        padding: 20,
        marginTop:30,
        backgroundColor: 'pink',
    },
});

```

##### To use customer copontent

```js
import CustomerHeader from './component/customerHeader'; // the name must be start with capital letter

<View>
    <CustomerHeader/> 
<View>

```

##### Data array:

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

##### Customer component with parameter

```js
import React, { useState } from 'react';
import { StyleSheet, Text, TouchableOpacity } from 'react-native';

export default function CustomerItem( {item, clickFunction} ){ //put parameter in here, 

    return(
        <TouchableOpacity onPress = { () => clickFunction(item.id) }>
            <Text style = {styles.itemLayout}>{item.name}</Text>
        </TouchableOpacity>
    )
}
```



##### app.js View set parameter

```js
import CustomerItem from './component/CustomerItem';


const click = (id) => {
    console.log(id);     
}
reutrn(
    <View style={styles.container}>
        <FlatList
            keyExtractor = {(item)=>item.id}
            data = {people}
            renderItem = {( {item} )=> (
               <CustomerItem item = { item } clickFunction = { click } /> // set parameter
            )}
        />
    </View>
)
```



