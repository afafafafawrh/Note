# RefreshView (not finish)

```
<RefreshView IsRefreshing="{Binding IsRefresh}"
                         Command="{Binding RefreshCommand}">
</RefreshView>
```

# Command

```c#
 RefreshCommand = new Command(async () =>
            {
                IsRefresh = true;
                await Task.Delay(2000);
                IsRefresh = false;
});
```

