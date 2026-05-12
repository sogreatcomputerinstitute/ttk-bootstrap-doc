# TTKBootstrap Complete Guide

## Table of Contents
1. [Introduction](#introduction)
2. [Installation](#installation)
3. [Getting Started](#getting-started)
4. [Themes](#themes)
5. [Components](#components)
6. [Advanced Usage](#advanced-usage)
7. [Best Practices](#best-practices)

---

## Introduction

**TTKBootstrap** is a modern, responsive theme for Python's Tkinter library. It brings Bootstrap-inspired styling to Tkinter applications, making it easy to create professional-looking GUI applications with minimal effort.

### Key Features
- 🎨 Pre-built Bootstrap themes (light, dark, and more)
- 🎯 Simple and intuitive API
- 📱 Responsive design support
- 🚀 Modern, professional appearance
- 🔧 Easy customization

---

## Installation

### Step 1: Install via pip
```bash
pip install ttkbootstrap
```

### Step 2: Verify Installation
```python
import ttkbootstrap as ttk
print(ttk.__version__)
```

---

## Getting Started

### Basic Application Structure

```python
import ttkbootstrap as ttk
from ttkbootstrap.constants import *

# Create the main window
root = ttk.Window(themename="darkly")
root.title("My TTKBootstrap App")
root.geometry("400x300")

# Create a label
label = ttk.Label(root, text="Welcome to TTKBootstrap!", font=("Helvetica", 14))
label.pack(pady=20)

# Create a button
button = ttk.Button(root, text="Click Me!")
button.pack(pady=10)

# Run the application
root.mainloop()
```

### Available Themes
TTKBootstrap comes with several built-in themes:

| Theme Name | Style | Best For |
|-----------|-------|----------|
| darkly | Dark theme | Modern applications |
| superhero | Dark blue theme | Professional apps |
| flatly | Light theme | Minimal design |
| litera | Light theme | Clean interface |
| minty | Mint green theme | Health/wellness apps |
| pulse | Dark purple theme | Modern, vibrant apps |
| sandstone | Beige theme | Traditional look |
| simplex | Light theme | Simple applications |
| solar | Dark theme | Night mode apps |
| united | Blue theme | Corporate apps |

---

## Components

### 1. Button

#### Basic Button
```python
import ttkbootstrap as ttk
from ttkbootstrap.constants import *

root = ttk.Window(themename="darkly")

def on_click():
    print("Button clicked!")

button = ttk.Button(
    root,
    text="Click Me",
    command=on_click,
    bootstyle="primary"
)
button.pack(pady=10)

root.mainloop()
```

#### Button Styles (bootstyle)
- `primary` - Main action button (blue)
- `secondary` - Secondary action (gray)
- `success` - Success/confirmation (green)
- `danger` - Destructive action (red)
- `warning` - Warning action (orange)
- `info` - Information (light blue)
- `light` - Light button
- `dark` - Dark button
- `outline-*` - Outline variants (e.g., `outline-primary`)

#### Full Button Example
```python
button = ttk.Button(
    root,
    text="Primary Button",
    bootstyle="primary",
    width=20,
    cursor="hand2"
)
button.pack(pady=5)
```

---

### 2. Label

#### Basic Label
```python
label = ttk.Label(
    root,
    text="Hello, World!",
    font=("Helvetica", 12),
    foreground="white"
)
label.pack(pady=10)
```

#### Label with Different Styles
```python
# Primary style label
label_primary = ttk.Label(root, text="Primary", bootstyle="primary")
label_primary.pack()

# Success style label
label_success = ttk.Label(root, text="Success", bootstyle="success")
label_success.pack()

# Danger style label
label_danger = ttk.Label(root, text="Danger", bootstyle="danger")
label_danger.pack()
```

---

### 3. Entry (Text Input)

#### Basic Entry
```python
entry = ttk.Entry(root)
entry.pack(pady=10, padx=10, fill="x")

# Get value
value = entry.get()

# Set value
entry.insert(0, "Default text")

# Clear value
entry.delete(0, "end")
```

#### Entry with Label
```python
label = ttk.Label(root, text="Username:")
label.pack(anchor="w", padx=10)

entry = ttk.Entry(root)
entry.pack(pady=5, padx=10, fill="x")
```

#### Entry Validation Example
```python
def validate_email():
    email = entry.get()
    if "@" in email:
        print("Valid email")
    else:
        print("Invalid email")

label = ttk.Label(root, text="Email:")
label.pack(anchor="w", padx=10)

entry = ttk.Entry(root)
entry.pack(pady=5, padx=10, fill="x")

button = ttk.Button(root, text="Validate", command=validate_email)
button.pack(pady=10)
```

---

### 4. Button Group (Grouped Buttons)

```python
import ttkbootstrap as ttk
from ttkbootstrap.constants import *

root = ttk.Window(themename="darkly")

# Create a frame for grouping
button_frame = ttk.Frame(root)
button_frame.pack(pady=20)

# Create grouped buttons
btn1 = ttk.Button(button_frame, text="Left", bootstyle="primary")
btn1.grid(row=0, column=0)

btn2 = ttk.Button(button_frame, text="Middle", bootstyle="primary")
btn2.grid(row=0, column=1)

btn3 = ttk.Button(button_frame, text="Right", bootstyle="primary")
btn3.grid(row=0, column=2)

root.mainloop()
```

---

### 5. Checkbox

#### Basic Checkbox
```python
# Create a variable to track the checkbox state
check_var = ttk.IntVar()

checkbox = ttk.Checkbutton(
    root,
    text="I agree",
    variable=check_var,
    bootstyle="primary"
)
checkbox.pack(pady=10)

# Get checkbox value
value = check_var.get()  # 0 or 1
```

#### Multiple Checkboxes
```python
options = ["Option 1", "Option 2", "Option 3"]
check_vars = []

for option in options:
    var = ttk.IntVar()
    check_vars.append(var)
    
    cb = ttk.Checkbutton(
        root,
        text=option,
        variable=var,
        bootstyle="info"
    )
    cb.pack(anchor="w", padx=20)
```

---

### 6. Radio Button

#### Basic Radio Button
```python
# Create a variable to track selection
radio_var = ttk.StringVar(value="option1")

radio1 = ttk.Radiobutton(
    root,
    text="Option 1",
    variable=radio_var,
    value="option1",
    bootstyle="success"
)
radio1.pack(anchor="w", padx=20)

radio2 = ttk.Radiobutton(
    root,
    text="Option 2",
    variable=radio_var,
    value="option2",
    bootstyle="success"
)
radio2.pack(anchor="w", padx=20)

# Get selected value
selected = radio_var.get()
```

---

### 7. Combobox (Dropdown)

#### Basic Combobox
```python
combo_var = ttk.StringVar()

combobox = ttk.Combobox(
    root,
    textvariable=combo_var,
    values=["Python", "Java", "C++", "JavaScript"],
    state="readonly"
)
combobox.pack(pady=10, padx=10, fill="x")

# Set default value
combobox.current(0)

# Get selected value
selected = combo_var.get()
```

#### Editable Combobox
```python
combo = ttk.Combobox(
    root,
    values=["Option 1", "Option 2", "Option 3"],
    state="normal"  # Allows typing
)
combo.pack(pady=10)
```

---

### 8. Frame

#### Basic Frame
```python
# Main frame
main_frame = ttk.Frame(root, padding=20)
main_frame.pack(fill="both", expand=True)

# Create content inside the frame
label = ttk.Label(main_frame, text="Content in frame")
label.pack()
```

#### Frame with Border
```python
frame = ttk.Frame(root, padding=10, relief="ridge", bootstyle="primary")
frame.pack(pady=20, padx=10, fill="both", expand=True)

label = ttk.Label(frame, text="Frame with border")
label.pack()
```

---

### 9. Separator

```python
# Horizontal separator
separator = ttk.Separator(root, orient="horizontal")
separator.pack(fill="x", pady=10)

# Vertical separator
separator_v = ttk.Separator(root, orient="vertical")
separator_v.pack(side="left", fill="y", padx=10)
```

---

### 10. Progressbar

#### Basic Progressbar
```python
progress = ttk.Progressbar(
    root,
    length=300,
    mode="determinate",
    maximum=100,
    value=50,
    bootstyle="success"
)
progress.pack(pady=20)
```

#### Indeterminate Progressbar
```python
progress = ttk.Progressbar(
    root,
    length=300,
    mode="indeterminate",
    bootstyle="info"
)
progress.pack(pady=20)
progress.start()
```

#### Updating Progressbar
```python
import time

progress = ttk.Progressbar(
    root,
    length=300,
    mode="determinate",
    maximum=100,
    bootstyle="primary"
)
progress.pack(pady=20)

def update_progress():
    progress['value'] = 0
    for i in range(101):
        progress['value'] = i
        root.update()
        time.sleep(0.05)

button = ttk.Button(root, text="Start", command=update_progress)
button.pack()
```

---

### 11. Scale (Slider)

#### Basic Scale
```python
scale_var = ttk.DoubleVar(value=50)

scale = ttk.Scale(
    root,
    from_=0,
    to=100,
    variable=scale_var,
    orient="horizontal"
)
scale.pack(pady=20, padx=20, fill="x")

# Get value
value = scale_var.get()
```

#### Vertical Scale
```python
scale_v = ttk.Scale(
    root,
    from_=0,
    to=100,
    orient="vertical",
    bootstyle="info"
)
scale_v.pack(side="left", padx=20, fill="y")
```

---

### 12. Spinbox

#### Basic Spinbox
```python
spin_var = ttk.IntVar(value=0)

spinbox = ttk.Spinbox(
    root,
    from_=0,
    to=100,
    variable=spin_var,
    bootstyle="primary"
)
spinbox.pack(pady=10)

# Get value
value = spin_var.get()
```

---

### 13. Text Widget

#### Basic Text Widget
```python
text = ttk.Text(
    root,
    height=10,
    width=40
)
text.pack(pady=10, padx=10, fill="both", expand=True)

# Insert text
text.insert("1.0", "Hello, World!")

# Get all text
content = text.get("1.0", "end-1c")

# Clear text
text.delete("1.0", "end")
```

---

### 14. Listbox

#### Basic Listbox
```python
listbox = ttk.Listbox(root, height=10)
listbox.pack(pady=10, padx=10, fill="both", expand=True)

# Add items
items = ["Item 1", "Item 2", "Item 3"]
for item in items:
    listbox.insert("end", item)

# Get selected item
selected = listbox.curselection()
if selected:
    item = listbox.get(selected[0])
```

#### Listbox with Scrollbar
```python
frame = ttk.Frame(root)
frame.pack(fill="both", expand=True)

scrollbar = ttk.Scrollbar(frame)
scrollbar.pack(side="right", fill="y")

listbox = ttk.Listbox(frame, yscrollcommand=scrollbar.set)
listbox.pack(side="left", fill="both", expand=True)

scrollbar.config(command=listbox.yview)

# Add items
for i in range(50):
    listbox.insert("end", f"Item {i+1}")
```

---

### 15. Menu & Menubar

#### Basic Menu
```python
def on_file_new():
    print("New file")

def on_file_exit():
    root.quit()

menubar = ttk.Menu(root)
root.config(menu=menubar)

# File menu
file_menu = ttk.Menu(menubar, tearoff=0)
menubar.add_cascade(label="File", menu=file_menu)
file_menu.add_command(label="New", command=on_file_new)
file_menu.add_separator()
file_menu.add_command(label="Exit", command=on_file_exit)

# Edit menu
edit_menu = ttk.Menu(menubar, tearoff=0)
menubar.add_cascade(label="Edit", menu=edit_menu)
edit_menu.add_command(label="Copy")
edit_menu.add_command(label="Paste")
```

---

### 16. Message/Dialog (Message Box)

#### Info Message
```python
from ttkbootstrap.dialogs import Messagebox

root = ttk.Window(themename="darkly")

def show_info():
    Messagebox.show_info(
        title="Information",
        message="This is an info message",
        parent=root
    )

button = ttk.Button(root, text="Show Info", command=show_info)
button.pack(pady=20)
```

#### Confirmation Dialog
```python
from ttkbootstrap.dialogs import Messagebox

def show_confirm():
    answer = Messagebox.show_question(
        title="Confirm",
        message="Do you want to continue?",
        buttons=["Yes", "No"],
        parent=root
    )
    print(f"Answer: {answer}")

button = ttk.Button(root, text="Confirm", command=show_confirm)
button.pack(pady=20)
```

---

### 17. Notebook (Tabs)

#### Basic Notebook
```python
notebook = ttk.Notebook(root)
notebook.pack(fill="both", expand=True, pady=10, padx=10)

# Create tabs
tab1 = ttk.Frame(notebook)
notebook.add(tab1, text="Tab 1")

tab2 = ttk.Frame(notebook)
notebook.add(tab2, text="Tab 2")

# Add content to tabs
label1 = ttk.Label(tab1, text="Content for Tab 1")
label1.pack(pady=20)

label2 = ttk.Label(tab2, text="Content for Tab 2")
label2.pack(pady=20)
```

#### Tab Management
```python
# Select a tab programmatically
notebook.select(0)  # Select first tab

# Get current tab
current = notebook.index(notebook.select())

# Remove a tab
notebook.forget(1)  # Remove second tab
```

---

### 18. Treeview (Table/List)

#### Basic Treeview
```python
# Create Treeview
tree = ttk.Treeview(
    root,
    columns=("Name", "Age", "City"),
    height=10
)
tree.pack(pady=10, padx=10, fill="both", expand=True)

# Define headings
tree.column("#0", width=0, stretch="no")
tree.column("Name", anchor="w", width=100)
tree.column("Age", anchor="center", width=50)
tree.column("City", anchor="w", width=100)

tree.heading("#0", text="ID", anchor="w")
tree.heading("Name", text="Name", anchor="w")
tree.heading("Age", text="Age", anchor="center")
tree.heading("City", text="City", anchor="w")

# Add data
data = [
    ("1", "John", "30", "New York"),
    ("2", "Jane", "25", "Los Angeles"),
    ("3", "Bob", "35", "Chicago"),
]

for row in data:
    tree.insert("", "end", text=row[0], values=(row[1], row[2], row[3]))

# Get selected item
def get_selected():
    selected = tree.selection()
    if selected:
        item = tree.item(selected[0])
        print(item["values"])

button = ttk.Button(root, text="Get Selected", command=get_selected)
button.pack()
```

---

## Themes

### Switching Themes

#### Static Theme (on startup)
```python
root = ttk.Window(themename="darkly")
```

#### Dynamic Theme Switching
```python
import ttkbootstrap as ttk

root = ttk.Window(themename="darkly")
root.geometry("400x300")

def change_theme(theme_name):
    root.style.theme_use(theme_name)

theme_frame = ttk.Frame(root)
theme_frame.pack(pady=20)

for theme in ["darkly", "superhero", "flatly", "minty"]:
    btn = ttk.Button(
        theme_frame,
        text=theme.capitalize(),
        command=lambda t=theme: change_theme(t)
    )
    btn.pack(side="left", padx=5)

root.mainloop()
```

### Available Color Bootstyles
- `primary` - Blue
- `secondary` - Gray
- `success` - Green
- `danger` - Red
- `warning` - Orange
- `info` - Light Blue
- `light` - Light Gray
- `dark` - Dark Gray

---

## Advanced Usage

### Create a Complete Application

```python
import ttkbootstrap as ttk
from ttkbootstrap.constants import *
from ttkbootstrap.dialogs import Messagebox

class TodoApp:
    def __init__(self, root):
        self.root = root
        self.root.title("Todo App")
        self.root.geometry("500x400")
        
        # Title
        title = ttk.Label(
            root,
            text="My Todo App",
            font=("Helvetica", 16, "bold"),
            bootstyle="primary"
        )
        title.pack(pady=20)
        
        # Input frame
        input_frame = ttk.Frame(root)
        input_frame.pack(pady=10, padx=10, fill="x")
        
        self.entry = ttk.Entry(input_frame)
        self.entry.pack(side="left", fill="x", expand=True, padx=5)
        
        add_btn = ttk.Button(
            input_frame,
            text="Add",
            command=self.add_todo,
            bootstyle="success"
        )
        add_btn.pack(side="left", padx=5)
        
        # Listbox frame
        list_frame = ttk.Frame(root)
        list_frame.pack(pady=10, padx=10, fill="both", expand=True)
        
        scrollbar = ttk.Scrollbar(list_frame)
        scrollbar.pack(side="right", fill="y")
        
        self.listbox = ttk.Listbox(list_frame, yscrollcommand=scrollbar.set)
        self.listbox.pack(side="left", fill="both", expand=True)
        
        scrollbar.config(command=self.listbox.yview)
        
        # Button frame
        btn_frame = ttk.Frame(root)
        btn_frame.pack(pady=10)
        
        delete_btn = ttk.Button(
            btn_frame,
            text="Delete",
            command=self.delete_todo,
            bootstyle="danger"
        )
        delete_btn.pack(side="left", padx=5)
        
        clear_btn = ttk.Button(
            btn_frame,
            text="Clear All",
            command=self.clear_todos,
            bootstyle="warning"
        )
        clear_btn.pack(side="left", padx=5)
    
    def add_todo(self):
        task = self.entry.get()
        if task:
            self.listbox.insert("end", task)
            self.entry.delete(0, "end")
    
    def delete_todo(self):
        selected = self.listbox.curselection()
        if selected:
            self.listbox.delete(selected[0])
    
    def clear_todos(self):
        answer = Messagebox.show_question(
            title="Confirm",
            message="Clear all todos?",
            buttons=["Yes", "No"],
            parent=self.root
        )
        if answer == "Yes":
            self.listbox.delete(0, "end")

if __name__ == "__main__":
    root = ttk.Window(themename="darkly")
    app = TodoApp(root)
    root.mainloop()
```

---

## Best Practices

### 1. **Use Proper Naming Conventions**
```python
# Good
primary_button = ttk.Button(root, text="Submit", bootstyle="primary")
error_label = ttk.Label(root, text="Error", bootstyle="danger")

# Avoid
btn = ttk.Button(root, text="Submit")
lbl = ttk.Label(root, text="Error")
```

### 2. **Organize with Frames**
```python
# Good - organize related widgets
form_frame = ttk.Frame(root, padding=10)
form_frame.pack(fill="x")

button_frame = ttk.Frame(root, padding=10)
button_frame.pack(fill="x")

# Place related widgets in their frames
ttk.Label(form_frame, text="Name:").pack()
ttk.Entry(form_frame).pack()
```

### 3. **Use Variables for State Management**
```python
# Good - track state with variables
username_var = ttk.StringVar()
password_var = ttk.StringVar()

username_entry = ttk.Entry(root, textvariable=username_var)
password_entry = ttk.Entry(root, textvariable=password_var, show="*")
```

### 4. **Create Reusable Components**
```python
class FormField:
    def __init__(self, parent, label_text, **kwargs):
        self.frame = ttk.Frame(parent)
        self.frame.pack(fill="x", pady=5)
        
        ttk.Label(self.frame, text=label_text).pack(anchor="w")
        self.var = ttk.StringVar()
        self.entry = ttk.Entry(self.frame, textvariable=self.var, **kwargs)
        self.entry.pack(fill="x")
    
    def get(self):
        return self.var.get()
    
    def set(self, value):
        self.var.set(value)
```

### 5. **Handle Events Properly**
```python
# Good - use descriptive function names
def on_button_click():
    print("Button clicked")

def on_entry_change(event):
    value = event.widget.get()
    print(f"Entry changed: {value}")

button = ttk.Button(root, text="Click", command=on_button_click)
entry = ttk.Entry(root)
entry.bind("<KeyRelease>", on_entry_change)
```

### 6. **Use Consistent Styling**
```python
# Define style constants
PRIMARY_STYLE = "primary"
SUCCESS_STYLE = "success"
ERROR_STYLE = "danger"
WARNING_STYLE = "warning"

# Use them consistently
submit_btn = ttk.Button(root, text="Submit", bootstyle=PRIMARY_STYLE)
success_label = ttk.Label(root, text="Success!", bootstyle=SUCCESS_STYLE)
error_label = ttk.Label(root, text="Error!", bootstyle=ERROR_STYLE)
```

### 7. **Responsive Layout**
```python
# Use proper geometry managers
root.columnconfigure(0, weight=1)
root.rowconfigure(1, weight=1)

frame = ttk.Frame(root)
frame.grid(row=0, column=0, sticky="ew", padx=10, pady=10)

text = ttk.Text(root)
text.grid(row=1, column=0, sticky="nsew", padx=10, pady=10)
```

---

## Troubleshooting

### Issue: Theme not applying
**Solution:** Make sure to set the theme when creating the Window:
```python
root = ttk.Window(themename="darkly")  # Set theme here
```

### Issue: Widgets not appearing
**Solution:** Ensure you call `pack()`, `grid()`, or `place()`:
```python
button = ttk.Button(root, text="Click")
button.pack()  # Don't forget this!
```

### Issue: Colors not showing correctly
**Solution:** Use bootstyle parameter:
```python
button = ttk.Button(root, text="Click", bootstyle="primary")
```

### Issue: Entry widget not responsive
**Solution:** Use StringVar to track changes:
```python
var = ttk.StringVar()
entry = ttk.Entry(root, textvariable=var)
entry.pack()
```

---

## Resources

- **Official Documentation:** https://ttkbootstrap.readthedocs.io/
- **GitHub Repository:** https://github.com/Israel-Dryer/ttkbootstrap
- **Tkinter Documentation:** https://docs.python.org/3/library/tkinter.html

---

## Summary

TTKBootstrap makes it easy to create modern, professional-looking GUI applications with Python. By following the patterns and examples in this guide, you can quickly build sophisticated user interfaces. Remember to:

✅ Choose appropriate themes for your application  
✅ Use descriptive variable and function names  
✅ Organize widgets with frames  
✅ Use bootstyle for consistent styling  
✅ Test your application across different themes  

Happy coding! 🚀
