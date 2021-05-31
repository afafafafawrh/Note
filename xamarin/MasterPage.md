### Master Page Sample Code:

```
<MasterDetailPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="test.MasterPage">
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

