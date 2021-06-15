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

# ActionSheetAsync

```c#
// document
Task<string> ActionSheetAsync(string title, string cancel, string destructive, CancellationToken? cancelToken = null, params string[] buttons);

//popup menu at the middle
var cancelSrc = new CancellationTokenSource();
var result = await UserDialogs.Instance.ActionSheetAsync("Test Title", "Cancel", "Destroy", cancelSrc.Token, "Button1", "Button2", "Button3");
UserDialogs.Instance.Alert(result);
```

# PromptAsync & property

```c#
public class PromptConfig : IStandardDialogConfig, IAndroidStyleDialogConfig
{
    public static string DefaultOkText { get; set; } = "Ok";
    public static string DefaultCancelText { get; set; } = "Cancel";
    public static int? DefaultAndroidStyleId { get; set; }
    public static int? DefaultMaxLength { get; set; }

    public string Title { get; set; }
    public string Message { get; set; }
    public Action<PromptResult> OnAction { get; set; }

    public bool IsCancellable { get; set; } = true;
    public string Text { get; set; }

    public string OkText { get; set; } = DefaultOkText;
    public string CancelText { get; set; } = DefaultCancelText;
    public string Placeholder { get; set; }
    public int? MaxLength { get; set; } = DefaultMaxLength;
    public int? AndroidStyleId { get; set; } = DefaultAndroidStyleId;
    public InputType InputType { get; set; } = InputType.Default;
    public AutoCorrectionConfig AutoCorrectionConfig { get; set; } = AutoCorrectionConfig.Default;
    //public bool UwpCancelOnEscKey { get; set; }
    //public bool UwpSubmitOnEnterKey { get; set; }
    public Action<PromptTextChangedArgs> OnTextChanged { get; set; }


    public PromptConfig SetAction(Action<PromptResult> action)
    {
        this.OnAction = action;
        return this;
    }


    public PromptConfig SetTitle(string title)
    {
        this.Title = title;
        return this;
    }


    public PromptConfig SetMessage(string message)
    {
        this.Message = message;
        return this;
    }


    public PromptConfig SetCancellable(bool cancel)
    {
        this.IsCancellable = cancel;
        return this;
    }


    public PromptConfig SetOkText(string text)
    {
        this.OkText = text;
        return this;
    }


    public PromptConfig SetMaxLength(int maxLength)
    {
        this.MaxLength = maxLength;
        return this;
    }


    public PromptConfig SetText(string text)
    {
        this.Text = text;
        return this;
    }


    public PromptConfig SetCancelText(string cancelText)
    {
        this.IsCancellable = true;
        this.CancelText = cancelText;
        return this;
    }


    public PromptConfig SetPlaceholder(string placeholder)
    {
        this.Placeholder = placeholder;
        return this;
    }


    public PromptConfig SetInputMode(InputType inputType)
    {
        this.InputType = inputType;
        return this;
    }


    public PromptConfig SetOnTextChanged(Action<PromptTextChangedArgs> onChange)
    {
        this.OnTextChanged = onChange;
        return this;
    }
}
```



# PromptAsync Declare

```C#
var input = await UserDialogs.Instance.PromptAsync(new PromptConfig()
{
    Title = "This is title",
    Message = "This is message",
    AutoCorrectionConfig = AutoCorrectionConfig.Yes,
    Placeholder = "input something",
    OkText = "OKK",
    CancelText = "Cancel",
    OnTextChanged = args => {
        args.IsValid = args.Value.Equals("GOOD");
    }
});
Console.WriteLine(input.Text); // print input
```

