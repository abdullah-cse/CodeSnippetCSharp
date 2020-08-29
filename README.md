# CodeSnippet C#
#### Snippet of C# code to use other C# Project. All of Code Snippet are written in Markdown Format.

# Minimize Window
```csharp
private void buttonMin_Click(object sender, EventArgs e)
        {
            //Minimize the Window
            WindowState = FormWindowState.Minimized;
        }
```

# Maximize & Back to Normal Screen
```csharp
/using [Namespace যা হবে].Properties;	//আইকন বদলাতে এটা রেফারেন্সে দিতে হবে।
//Maximize Window and Back to Normal Screen
        private void buttonMax_Click(object sender, EventArgs e)
        {          
            if (WindowState==FormWindowState.Normal)
            {
                //Not to cover Taskbar.
		  MaximizedBounds = Screen.FromHandle(Handle).WorkingArea;    
                WindowState = FormWindowState.Maximized;
                buttonMax.Image = Resources.ic_Normal;
            }
            else
            {
                //Window is Maximized, so make it Normal
                WindowState = FormWindowState.Normal;
                buttonMax.Image = Resources.ic_Maximized;
            }
        }
```


# Exit Application
```csharp
 private void buttonExit_Click(object sender, EventArgs e)
        {
            Application.Exit();
        }
 ```
 
 
