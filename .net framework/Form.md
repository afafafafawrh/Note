After clicked Add View in controller, some code will be generated actomatically. This is a from.

```C#
using (Html.BeginForm()) 
{
    @Html.AntiForgeryToken()
    
    <div class="form-horizontal">
        <h4>Product</h4>
        <hr />
        @Html.ValidationSummary(true, "", new { @class = "text-danger" })
        <div class="form-group">
            @Html.LabelFor(model => model.name, htmlAttributes: new { @class = "control-label col-md-2" })
            <div class="col-md-10">
                @Html.EditorFor(model => model.name, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model => model.name, "", new { @class = "text-danger" })
            </div>
        </div>

        <div class="form -group">
            @Html.LabelFor(model => model.price, htmlAttributes: new { @class = "control-label col-md-2" })
            <div class="col-md-10">
                @Html.EditorFor(model => model.price, new { htmlAttributes = new { @class = "form-control" } })
               
                @Html.ValidationMessageFor(model => model.price, "", new { @class = "text-danger" })
            </div>
        </div>

        <div class="form-group">
            <div class="col-md-offset-2 col-md-10">
                <input type="submit" value="Create" class="btn btn-default" />
            </div>
        </div>
    </div>
}

```

To call the function of controller after submit:

##### Method 1  create same ActionResult to your View

```c#
public ActionResult Create() { // form page
    return View();
}
[HttpPost]
public ActionResult Create(Product product) {
    return Content("Click save");
}
```

##### Method 2

```c#
@using (Html.BeginForm("action","controller")) //modify this statment
eg: @using (Html.BeginForm("SaveProduct","Product")) //modify this statment

```



To call the action with parameter

```C#
//View
@using (Html.BeginForm("TestFunction", "Product")) {
    <input type="text" id ="search" name="input"> //name should match the parameter name
    <input type="submit" value="serach">
}

//ProductCroller
public ActionResult TestFunction(string input) { //match with this
    return Content(input);
}
```

