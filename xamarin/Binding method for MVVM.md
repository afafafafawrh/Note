#### Binding method for MVVM

```c#
x:Name="itemPage"
Command ="{Binding Source={x:Reference (name)}, Path=BindingContext.(Command)"}
Example:
SearchCommand="{Binding Source={x:Reference itemPage},
                Path=BindingContext.SearchCommand}
```



#### RelativeSource AncestorType

no Binding.Command

```c#

Command = "{Binding Source={RelativeSource AncestorType={x:Type (page) }}, Path=(Command)}"
Example:
SearchCommand="{Binding Source={RelativeSource 
                AncestorType={x:Type local:ItemDisplayPageViewModel}},
                Path=SearchCommand}"
```

