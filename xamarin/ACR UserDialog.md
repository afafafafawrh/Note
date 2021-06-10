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

