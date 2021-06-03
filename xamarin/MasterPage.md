### Master Page Sample Code:

```
<MasterDetailPage .....>
    <MasterDetailPage.Master>
        <ContentPage BackgroundColor="Gray" Title="Master Page">
            <ContentPage.Content>
                <StackLayout>   
                    <Label Text="Master Page"/>
                </StackLayout>
            </ContentPage.Content>
        </ContentPage>
    </MasterDetailPage.Master>
    <MasterDetailPage.Detail>
        <ContentPage>
            <ContentPage.Content>
                <StackLayout>
                    <Label Text="Detail Page"/>
                </StackLayout>
            </ContentPage.Content>
        </ContentPage>
    </MasterDetailPage.Detail>
</MasterDetailPage>
```



### Combine with tabbed page

```c#
<MasterDetailPage.Detail>
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
</MasterDetailPage.Detail>
```

