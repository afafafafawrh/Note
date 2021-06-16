Create page

```c#
<TabbedPage xmlns="http://xamarin.com/schemas/2014/forms"
            xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
            xmlns:android="clr-namespace:Xamarin.Forms.PlatformConfiguration.AndroidSpecific;assembly=Xamarin.Forms.Core"
            x:Class="SolutionName.pageName"
			android:TabbedPage.ToolbarPlacement="Bottom" // default top
            android:TabbedPage.BarItemColor="Black"     
            android:TabbedPage.BarSelectedItemColor="#71fc47" //click color
            android:TabbedPage.IsSmoothScrollEnabled="false" // switch page animation
			xmlns:(value)="">
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

YouPage should inheritance :TabbedPage

