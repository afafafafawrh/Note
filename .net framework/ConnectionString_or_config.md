##### Click web.config ->XML->Schema->use dotNetConfig. 

#### After this, you can add connectionStrings

```C#
<connectionStrings>
	<add name="testDatabase" connectionString="Data Source=connectionString;Initial Catalog=database;"/>
</connectionStrings>s
```

Create static connection String

```C#
using System.Configuration;

public static string GetConnection() {
    return ConfigurationManager.ConnectionStrings["testDatabase"].ConnectionString;
}
```

