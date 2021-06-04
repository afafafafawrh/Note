### ToolbarItem

```c#
Use NavigationPage if toolBar is not showing in main Page
p.s.  MainPage = new NavigationPage(new ToolBarPage());
```



```c#
<ContentPage.ToolbarItems>
        <ToolbarItem Text="Item1"
                     IconImageSource="image"
                     Order="Primary"
                     Priority="0"/>
                     
        <ToolbarItem Text="Item1"
                     IconImageSource="image"
                     Order="Primary"
                     Priority="0"/>
                     
        <ToolbarItem Text="Item1"
                     IconImageSource="image"
                     Order="Primary"
                     Priority="0"/>          
</ContentPage.ToolbarItems>
<ContentPage.Content>
</ContentPage.Content>
```



### When the Order is Secondary:

It will show three dot at the top right corner like popup menu.

