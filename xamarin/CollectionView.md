# Collection View

use ObservableCollection for update item.



## SelectedItem

```
 SelectedItem="{Binding (value)}"
```

## SelectedChange simple Sample getting data

```C#
 private void CollectionView_SelectionChanged(object sender, SelectionChangedEventArgs e)
        {

            if (e.CurrentSelection.Count == 0)
                return;
            var item = e.CurrentSelection;
            String msg = String.Empty;
            for(int i = 0; i < item.Count; i++)
            {
                var temp = item[i] as Item;
                msg += $"{temp.name} ";
            }
            DisplayAlert("Select ", msg, "OK");
}
```

## Group

```
IsGrouped="True"
```

##### Create group Class

```
class ItemGroup : ObservableCollection<Item>
    {
        public String key { get; set; }

        public ItemGroup(string name) {
            key = name;
        }
}
```

```c#
public ObservableCollection<ItemGroup> itemGroups { get; set; }
ItemsSource="{Binding itemGroups}

//In DataTemplate name , rank , point are in Item class
<Frame CornerRadius="10" >
      <StackLayout HorizontalOptions="Center">
             <StackLayout Orientation="Horizontal">
                     <Label Text="{Binding name}"/>
                     <Label Text="{Binding rank}"/>
              </StackLayout>
                     <Label Text="{Binding point}"/>
      </StackLayout>
</Frame>

```

#### Group Header

```c#
 <CollectionView.GroupHeaderTemplate>
      <DataTemplate>
           <Label Text="{Binding key}"/>
      </DataTemplate>
 </CollectionView.GroupHeaderTemplate>
```



## Header and Footer

```c#
<CollectionView.Header>
       <StackLayout>
           <Label Text="HIHIHIHIIHIHI i am header "/>
       </StackLayout>
</CollectionView.Header>

<CollectionView.Footer>
       <StackLayout>
            <Button Text="Load more "></Button>
        </StackLayout>
</CollectionView.Footer>
```



## Item

```c#
<CollectionView.ItemTemplate>
	<DataTemplate>
	</DataTemplate>
</CollectionView.ItemTemplate>
```



## SwipeView

if there is some error in swipeView , add 

```
 Forms.SetFlags("SwipeView_Experimental");
```

in MainActivity.cs

```c#
<SwipeView>
	<SwipeView.RightItems>
        <SwipeItems>
            <SwipeItem BackgroundColor="Green"
                       Text="OK"/>
            <SwipeItem BackgroundColor="Red"
                       Text="Cancel"/>
         </SwipeItems>
	</SwipeView.RightItems>
    <Grid>
    </Grid>
</SwipeView>
    
```

