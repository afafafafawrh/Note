##### Simple method: passing value from controller to View

##### In Controller using ViewBag.value

```c#
public ActionResult Index(){
     ViewBag.test1 = "i am test1";
     ViewBag.animal = "i am animal";
     return View();
}
```

##### In View

```
<p>Test data: @ViewBag.test1</p>
<p>Animal : @ViewBag.animal</p>
```

##### Pass object

```
Item class:
public class Item{
    public string name { get; set; }
    public int price { get; set; }
}
```

```c#
public ActionResult Index(){
   List<Item> items = new List<Item>() {
       new Item(){
           name = "item1",
           price = 10
       },
       new Item() {
           name = "item2",
           price = 20
       },
       new Item() {
           name = "item3",
           price = 20
       }
   };
   ViewBag.itemList = items;
   return View();
}
```

In View

```html
<tbody>
    @foreach(var item in ViewBag.itemList)
    {
    <tr>
        <td>@item.name</td>
        <td>
            @if (item.price > 15)
            {
            	<p>@item.price</p>
            }
            else
            {
            	<p>5</p>
            }
        </td>
    </tr>
    }
</tbody>
```

