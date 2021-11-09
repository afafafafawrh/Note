### @Html.ActionLink

```C#
@Html.ActionLink("( display name )", "action", "controller",(html attribute)

Example:
@Html.ActionLink("new Item name", "Index", "Item", new { area = "" }, new { @class = "navbar-brand" }) 

//There is a controller name ItemController , action mean Action Result method
// *the name of the view page should equal to the name of Action Result Method.
//* The Folder name in "Views" is also equal to the name of the controller
              
                 
```

For example:

In ItemController 

```c#
public class ItemController : Controller
{
    // GET: Item
    public ActionResult Index()
    {
        ViewBag.Message = "Index";
        return View();
    }
}
//There is a folder call "Item" in Views folder, and the "Item" folder contains Index.cshtml view page.
```



