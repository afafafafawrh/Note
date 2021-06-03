Create page

```c#
<TabbedPage android:TabbedPage.ToolbarPlacement="Bottom" // default top
            android:TabbedPage.BarItemColor="Black"     
            android:TabbedPage.BarSelectedItemColor="#71fc47" //click color
            android:TabbedPage.IsSmoothScrollEnabled="false"> // switch page animation
			xmlns:(value)=""
    <NavigationPage Title="(name)" IconImageSource="(sourceImage)">
        <x:Arguments>
            <(value):(Page)/>
        </x:Arguments>
    </NavigationPage>
    <NavigationPage Title="name" IconImageSource="(sourceImage)">
        <x:Arguments>
            <(value):(Page)/>
        </x:Arguments>
    </NavigationPage>
    <NavigationPage Title="name" IconImageSource="(sourceImage)">
        <x:Arguments>
            <(value):(Page)/>
        </x:Arguments>
    </NavigationPage>
</TabbedPage>
```

