##### In RouteConfig

```C#
public static void RegisterRoutes(RouteCollection routes)
{
    routes.IgnoreRoute("{resource}.axd/{*pathInfo}");

    routes.MapRoute(
        name: "Default",
        url: "{controller}/{action}/{id}",
        defaults: new { controller = "Home", action = "Index", id = UrlParameter.Optional}
    );
}
```

#### You can access the page through inputting the correct URL.

##### For example

##### Student Conroller:

```c#
public class StudentController : Controller
{
    public ActionResult Test(int id) { // it should match the Parameter name with RouteConfig : 
       								   // url:{controller}/{action}/{id}". id = int id other varible name will get error
        return Content("Test "+ id);
    }     
}
```

##### you can access the page by https://localhost:port/Student/Test/1



##### There are two method to create custom URL calling

#### Method 1

```c#
routes.MapRoute(
    "test",
    "student/testing/{month}/{year}",                
    new { controller = "Student", action = "Test"}
);
```

##### StudentController

```C#
public ActionResult Test(int month,int year) {
    return Content("month " + month + " year " + year);
}
```

You can access the page by https://localhost:port/student/testing/10/20

#### Method 2:

```C#
routes.MapMvcAttributeRoutes();//adding this in RouteConfig.

[Route("student/testing/{month}/{year}")] //adding this
public ActionResult Test(int month,int year) {
    return Content("month " + month + " year " + year);
}

//Range ,min, max,Regex
[Route("student/testing/{month:int:range(1,12)}/{year:min(1990)}")] //adding this
```

You can access the page by https://localhost:port/student/testing/10/20

