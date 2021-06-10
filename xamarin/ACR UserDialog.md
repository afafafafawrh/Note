ACR UserDialogs

# Toast property and method

```C#

        public static ToastPosition? DefaultPosition { get; set; }
        //
        // Summary:
        //     The default toast background color. If not set, defaults very depending on platform.
        public static Color? DefaultBackgroundColor { get; set; }
        //
        // Summary:
        //     The default text color in the action button. If not set, defaults very depending
        //     on platform.
        public static Color? DefaultActionTextColor { get; set; }
        //
        // Summary:
        //     The default duration for how long the toast should remain on-screen. Defaults
        //     to 2.5 seconds
        public static TimeSpan DefaultDuration { get; set; }
        //
        // Summary:
        //     The default message text color to use. If not set, defaults very depending on
        //     platform.
        public static Color? DefaultMessageTextColor { get; set; }
        public ToastAction Action { get; set; }
        public string Message { get; set; }
        public Color? MessageTextColor { get; set; }
        public Color? BackgroundColor { get; set; }
        public ToastPosition? Position { get; set; } // ToastPosition.Top or ToastPosition.bottom
        public TimeSpan Duration { get; set; }
        public string Icon { get; set; }

        public ToastConfig SetAction(ToastAction action);
        public ToastConfig SetAction(Action<ToastAction> action);
        public ToastConfig SetBackgroundColor(Color color);
        public ToastConfig SetDuration(TimeSpan? duration = null);
        public ToastConfig SetDuration(int millis);
        public ToastConfig SetIcon(string icon);
        public ToastConfig SetMessageTextColor(Color color);
        public ToastConfig SetPosition(ToastPosition position);
```

## ToastAction

```c#
public string Text { get; set; }
public Color? TextColor { get; set; }
public Action Action { get; set; }

public ToastAction SetAction(Action action);
public ToastAction SetText(string text);
public ToastAction SetTextColor(Color color);
```

Create Toast

```c#
UserDialogs.Instance.Toast(
    new ToastConfig("This is Title")
    .SetDuration(TimeSpan.FromSeconds(3))
    .SetPosition(ToastPosition.Top)
    .SetAction(x => x
        .SetText("HIHIH")             
        .SetAction(() => UserDialogs.Instance.Alert("You clicked hi"))
     )
);
```

Other Way to create Toast

```c#
UserDialogs.Instance.Toast(
    new ToastConfig("This is Title") {
        Position = ToastPosition.Top,
        Duration = TimeSpan.FromSeconds(3),
        
        Action = new ToastAction {
        	Text = "HIHIH",
            Action = () => {
                UserDialogs.Instance.Alert("You clicked hi");
            }
		} 
	}
);         
```







# Progress

```c#
public class ProgressDialogConfig
{
    public ProgressDialogConfig();

    public static string DefaultCancelText { get; set; }
    public static string DefaultTitle { get; set; }
    public static MaskType DefaultMaskType { get; set; }
    public static bool UseAndroidImmersiveMode { get; set; }
    public string CancelText { get; set; }
    public string Title { get; set; }
    public bool AutoShow { get; set; }
    public bool IsDeterministic { get; set; }
    public MaskType MaskType { get; set; }
    public Action OnCancel { get; set; }

    public ProgressDialogConfig SetAutoShow(bool autoShow);
    public ProgressDialogConfig SetCancel(string cancelText = null, Action onCancel = null);
    public ProgressDialogConfig SetIsDeterministic(bool isDeterministic);
    public ProgressDialogConfig SetMaskType(MaskType maskType);
    public ProgressDialogConfig SetTitle(string title);
}
```





```C#
 var cancelSrc = new CancellationTokenSource();
var config = new ProgressDialogConfig()
    .SetTitle("i ma Title")
    .SetIsDeterministic(false)
    .SetMaskType(MaskType.Black)
    .SetCancel(onCancel: cancelSrc.Cancel);
```



Other way declare

```c#
var config = new ProgressDialogConfig()
{
    Title = "I am Title",
    OnCancel = cancelSrc.Cancel,
    IsDeterministic = false,
    MaskType = MaskType.None,
};
```

Finish Loading

```c#
using (UserDialogs.Instance.Progress(config)) {
    try{
    	await Task.Delay(TimeSpan.FromSeconds(3), cancelSrc.Token);
    }
    	catch { }
}
 UserDialogs.Instance.Alert(cancelSrc.IsCancellationRequested ? "Loading Cancelled" : "Loading Complete");
```



# Progress Bar



```c#
 var cancelled = false;
using (var dlg = UserDialogs.Instance.Progress("I am progree", () => cancelled = true)) { 

    while(!cancelled && dlg.PercentComplete < 100)
    {

        await Task.Delay(TimeSpan.FromMilliseconds(500));
        dlg.PercentComplete += 10;
    }
    UserDialogs.Instance.Alert(cancelled ? "Loading Cancelled" : "Loading Complete");
}

//using CancellationTokenSource
//change () => cancelled = true to  () => cancelSrc.Cancel()
//chagne while(!cancelled to cancelSrc.IsCancellationRequested 
//chage Alert(cancelled ?...) to  cancelSrc.IsCancellationRequested

```



# ActionSheet & property



```c#
public class ActionSheetConfig : IAndroidStyleDialogConfig
{
    public ActionSheetConfig();

    public static string DefaultCancelText { get; set; }
    public static int? DefaultAndroidStyleId { get; set; }
    public static bool DefaultUseBottomSheet { get; set; }
    public static string DefaultDestructiveText { get; set; }
    public static string DefaultItemIcon { get; set; }
    public int? AndroidStyleId { get; set; }
    public IList<ActionSheetOption> Options { get; set; }
    public ActionSheetOption Destructive { get; set; }
    public ActionSheetOption Cancel { get; set; }
    public string Message { get; set; }
    public string Title { get; set; }
    //
    // Summary:
    //     This icon is applied to the list items, not to destructive or cancel
    public string ItemIcon { get; set; }
    //
    // Summary:
    //     This only currently applies to android
    public bool UseBottomSheet { get; set; }

    public ActionSheetConfig Add(string text, Action action = null, string icon = null);
    public ActionSheetConfig SetCancel(string text = null, Action action = null, string icon = null);
    public ActionSheetConfig SetDestructive(string text = null, Action action = null, string icon = null);
    public ActionSheetConfig SetMessage(string msg);
    public ActionSheetConfig SetTitle(string title);
    public ActionSheetConfig SetUseBottomSheet(bool useBottomSheet);
}
```

## Declare 

```c#
var config = new ActionSheetConfig()
{
    UseBottomSheet = true,
    Message = "i am message",
};

config.Add("Item 1",
           () => click()
          );
config.Add("item 2",
           () => click()
          );
config.SetDestructive("Destruct", () => UserDialogs.Instance.Alert("Destructive BOOM Selected"), "user.png");
config.SetCancel("Cancel", () => UserDialogs.Instance.Alert("Click cancel Button"), "chat.png");

UserDialogs.Instance.ActionSheet(config);
```

![image-20210610171255673](C:\Users\cho\AppData\Roaming\Typora\typora-user-images\image-20210610171255673.png)