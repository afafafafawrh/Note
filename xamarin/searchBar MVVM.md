### SearchBar mvvm

Pass by value

you must use Text and Source={x:Reference}

```
SearchCommandParameter="{Binding Text, Source={x:Reference SearchBar}
```

other way: direct point to field 

```
Text = {Binding (value)}
```

