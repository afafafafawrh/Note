### @Html.ActionLink

```
@Html.ActionLink("( display name )", "action", "controller",(html attribute)
Example:
@Html.ActionLink("new Item name", "Index", "Item", new { area = "" }, new { @class = "navbar-brand" })

```

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
```

