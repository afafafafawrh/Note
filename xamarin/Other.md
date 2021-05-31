### Binding in xaml

```
xmlns:local ="clr-namespace:test.ViewModel"
```



```c#
<ContentPage.BindingContext>
        <local:ItemDisplayPageViewModel/>
</ContentPage.BindingContext>
```



### OnPropertyChanged method

```c#
protected virtual void OnPropertyChanged([CallerMemberName] string propertyName = null){
        PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
}
```

```c#
public void OnPropertyChanged(String name) {
            PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(name));
}
```

