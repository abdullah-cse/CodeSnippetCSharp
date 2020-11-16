# CodeSnippet C#
#### Snippet of C# code to use other C# Project. All of Code Snippet are written in Markdown Format.

# 1. Minimize Window
```csharp
private void buttonMin_Click(object sender, EventArgs e)
        {
            //Minimize the Window
            WindowState = FormWindowState.Minimized;
        }
```



# 2. Maximize & Back to Normal Screen
```csharp
using [Namespace যা হবে].Properties;	//আইকন বদলাতে এটা রেফারেন্সে দিতে হবে।
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




# 3. Exit Application
```csharp
 private void buttonExit_Click(object sender, EventArgs e)
        {
            Application.Exit();
        }
 ```



# 4. Dragging Window from Panel
```csharp

using System.Runtime.InteropServices;

  [DllImport("user32.DLL", EntryPoint = "ReleaseCapture")]
  private extern static void ReleaseCapture();
  [DllImport("user32.DLL", EntryPoint = "SendMessage")]
  private extern static void SendMessage(System.IntPtr hWnd, int wMsg, int wParam, int lParam);

        private void panel1_MouseDown(object sender, MouseEventArgs e)	// Panel1 means from which panel
        {
            ReleaseCapture();
            SendMessage(this.Handle, 0x112, 0xf012, 0);
        }
```




# 5. Play Music
```csharp
using System.Media;
SoundPlayer saplay = new SoundPlayer(@"LocationofMedia.wav");
saplay.Play();
//There are lot of method also, see SoundPlay Windows Repo
```




# 6. Form opening inside a panel
```csharp
private Form activeForm = null;
        private void openChildForm(Form ChildForm)
        {
            if (activeForm != null)
                activeForm.Close();
            activeForm = ChildForm;
            ChildForm.TopLevel = false;
            ChildForm.FormBorderStyle = FormBorderStyle.None;
            ChildForm.Dock = DockStyle.Fill;
            panelChildForm.Controls.Add(ChildForm);
            panelChildForm.Tag = ChildForm;
            ChildForm.BringToFront();
            ChildForm.Show();
        }
//Open About Form to know who are behind the sence
private void btnAbout_Click(object sender, EventArgs e)
        {
            //Open About Form to know who are behind the sence
            openChildForm(new About());
        }
```



# 7. Custom Shortcut
```csharp
// In Form_Load event,  Add Key Preview
this.KeyPreview=true;


// In Form_Keydown Add the following Code
if (e.Control == true && e.KeyCode == Keys.N)	//Here, We used 'N' as Shortcut Key
            {
                button2.PerformClick();
            }

```
# 8. Digital Clock in C# Form
* Add a timerClock Event
* In timerClock_Tick, Write code
* In Home_Load, start the timerClock

```csharp
//In Form Load event
private void Home_Load(object sender, EventArgs e)
        {
            timerClock.Start();     //To Show Current Date & Time from System.
        }
 private void timerClock_Tick(object sender, EventArgs e)
        {
            //Date & Time update every 100 ms, by this method
            labelTime.Text = DateTime.Now.ToString("HH:mm:ss");     //"HH"24 Hour Format, "hh" 12 Hour Format
            labelDate.Text = DateTime.Now.ToString("dd MMMM, yyyy");
        }
```
# 9. TextBox only accepting Number & Backspace
```csharp
	//সিরিয়াল নাম্বারের ঘরে শুধুমাত্র নাম্বার আর Backspace গ্রহনযোগ্য।
        //Backspace এজন্য, কোন সংখ্যা লিখলে যেন মোছা যায়।
        // এখানে ৮ হলো Backspace Key Code Constant
       private void textBoxSerial_KeyPress(object sender, KeyPressEventArgs e)
        {
            Char chr = e.KeyChar;
            if (!Char.IsDigit(chr) && chr != 8)
            {
                {
                    e.Handled = true;
                    MessageBox.Show("Only Number is accepted");
                }
            }
        }
```
