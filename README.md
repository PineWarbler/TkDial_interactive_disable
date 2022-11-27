# TkDial
**This is a library containing some circular rotatory dial-knob widgets for Tkinter. It can be used in place of normal sliders and scale.**

[![PyPI](https://img.shields.io/pypi/v/tkdial)](https://pypi.org/project/tkdial)
![Platform](https://img.shields.io/powershellgallery/p/Pester?color=blue)
[![Downloads](https://static.pepy.tech/personalized-badge/tkdial?period=total&units=international_system&left_color=green&right_color=brightgreen&left_text=Downloads)](https://pepy.tech/project/tkdial)

## Installation
```
pip install tkdial
```

# Dial Widget

## Usage

**Simple Example:**
```python
import tkinter as tk
from tkdial import Dial

app = tk.Tk()

dial = Dial(app)
dial.grid(padx=10, pady=10)

app.mainloop()
```
![Screenshot1](https://user-images.githubusercontent.com/89206401/202906601-89bd91ed-d685-4a4e-9ddc-7824f278ca4b.png)

### **Example 2**
```python
import tkinter as tk
from tkdial import Dial

app = tk.Tk()

# some color combinations
color_combinations = [("yellow", "red"), ("white", "cyan"), ("red", "pink"), ("black", "green"),
                    ("white", "black"), ("blue", "blue"), ("green", "green"), ("white", "pink"),
                    ("red", "black"), ("green", "cyan"), ("cyan","black"), ("pink", "blue")]

for i in range (12):
    dial = Dial(master=app, color_gradient=color_combinations[i],
                unit_length=10, radius=40, needle_color=color_combinations[i][1])
    if i<6:
        dial.grid(row=1, padx=10, pady=10, column=i)
    else:
        dial.grid(row=2, padx=10, pady=10, column=11-i)

app.mainloop()
```
![Screenshot2](https://user-images.githubusercontent.com/89206401/202906615-e4c484de-ed79-495e-b12f-d30b9d238eac.png)

### **Example 3**

**Implemented with [CustomTkinter](https://github.com/TomSchimansky/CustomTkinter)**

```python
import customtkinter
from tkdial import Dial

customtkinter.set_appearance_mode("Dark") 
              
app = customtkinter.CTk()
app.geometry("350x400")
                
app.grid_columnconfigure((0,1), weight=1)
app.grid_rowconfigure((0,1), weight=1)

frame_1 = customtkinter.CTkFrame(master=app)
frame_1.grid(padx=20, pady=20, sticky="nswe")

dial1 = Dial(master=frame_1, color_gradient=("green", "cyan"), bg="#2a2d2e",
             text_color="white", text="Current: ", unit_length=10, radius=50)
dial1.grid(padx=20, pady=20)

dial2 = Dial(master=frame_1, color_gradient=("yellow", "white"), bg="#2a2d2e",
             text_color="white", text="Position: ", unit_length=10, radius=50)
dial2.grid(padx=20, pady=20)

dial3 = Dial(master=frame_1, color_gradient=("white", "pink"), bg="#2a2d2e",
             text_color="white", text=" ", unit_length=10, radius=50)
dial3.grid(row=0, column=1, padx=20, pady=20)

dial4 = Dial(master=frame_1, color_gradient=("green", "green"), bg="#2a2d2e",
             text_color="white", text="", unit_width=15, radius=50)
dial4.grid(row=1, column=1, padx=20, pady=20)

app.mainloop()                  
```
![Screenshot 3](https://user-images.githubusercontent.com/89206401/202906638-a1c863b7-54b0-4e7a-9619-415e28b3ab51.png)

## Documentation
### Options:
  | Parameters  | Description |
  | -------- | ----------- |
  | _master_ | The master parameter is the parent widget |
  | _bg_  | The default background color of the dial widget |
  | _width_ | Define width of the widget manually (optional) |
  | _height_ | Define height of the widget manually (optional) |
  | _x_ | Determines the horizontal position of the dial in the canvas |
  | _y_ | Determines the vertical position of the dial in the canvas |
  | _start_ |  The start point of the range from where the needle will rotate |
  | _end_ |  The end point of the range |
  | _radius_ | Determines the distance of the unit lines between the center and the edge and also the length of the needle line |
  | _unit_length_ | Specify the length of the lines |
  | _unit_width_ | Specify the width of the lines |
  | _unit_color_ |  Specify the color of the unit lines |
  | _needle_color_ | Specify the color of the needle line |
  | _color_gradient_ | Specify which color gradient will be used for the units |
  | _text_ | A string that will be displayed under the dial object |
  | _text_color_ | Specify the color of the text that will be displayed under the dial object |
  | _text_font_ | Specify the font of the text that will be displayed under the dial object |
  | _integer_ | A boolean (True/False), displays only the integer value in text if True (default=False) |
  | _scroll_ | A boolean (True/False), enables mouse scroll in dial (default=True) |
  | _scroll_steps_ | Number of steps per scroll |
  | _state_ | Specify the state of the needle |
  | _command_ | Call a function whenever the needle is rotated |
  
### Methods:

  | Methods   | Description |
  |-----------|-------------|
  | _.get()_ | get the current value of the dial |
  | _.set()_ | set the value of the dial |
  | _.configure()_ | configure parameters of the dial |
 
# Scroll Knob

## Usage
**Simple Example**
```python
import tkinter
from tkdial import ScrollKnob
    
app = tkinter.Tk()

knob = ScrollKnob(app, start=0, end=100, steps=10)
knob.grid()
                
app.mainloop()      
```
![Simple Program](https://user-images.githubusercontent.com/89206401/204139370-73c66402-ec9a-4edc-9891-c63b209fd5e4.png)

### **Different Knob styles:**
```python
import customtkinter
from tkdial import ScrollKnob

app = customtkinter.CTk()
app.geometry("500x500")

knob1 = ScrollKnob(app, bg="#212325", radius=250, progress_color="#87ceeb", steps=10,
                 border_width=40, start_angle=90, inner_width=1, outer_width=1,
                 text_font="calibri 20", text_color="#87ceeb", bar_color="black")
knob1.grid(row=0, column=0)

knob2 = ScrollKnob(app, bg="#212325", radius=200, progress_color="#7eff00",
                 border_width=40, start_angle=90, inner_width=1, outer_width=0,
                 text_font="calibri 20", text_color="#7eff00", integer=True,
                 fg="#212325")
knob2.grid(row=1, column=0)

knob3 = ScrollKnob(app, bg="#212325", text=" ", radius=250, progress_color="white",
                   bar_color="#2937a6", border_width=30, start_angle=0, inner_width=5,
                   outer_width=0, text_font="calibri 20", steps=1, text_color="white", fg="#303ba1")
knob3.grid(row=0, column=1)

knob4 = ScrollKnob(app, bg=customtkinter.ThemeManager.theme["color"]["window_bg_color"][1],
                   text=" ", steps=10, radius=200, bar_color="#212325", progress_color="yellow",
                   outer_color="yellow", outer_length=10, border_width=30, start_angle=270,
                   inner_width=0, outer_width=5, text_font="calibri 20", text_color="white", fg="#212325")
knob4.grid(row=1, column=1)
                
app.mainloop()      
```
![Complex example](https://user-images.githubusercontent.com/89206401/204139428-c3c3c313-539f-4867-9d50-8876a19432ee.png)

## Documentation
### Options:
  | Parameters  | Description |
  | -------- | ----------- |
  | _master_ | The master parameter is the parent widget |
  | _bg_  | The default background color of the knob widget |
  | _width_ | Define width of the widget manually (optional) |
  | _height_ | Define height of the widget manually (optional) |
  | _start_ |  The start point of the range from where the bar will rotate |
  | _end_ |  The end point of the range |
  | _radius_ | Define the radius of the knob |
  | _border_width_ | Define the width of progress bar with respect to the outer and inner ring |
  | _start_angle_ | Determines the angle from where to rotate |
  | _text_ | A string that will be displayed on the knob |
  | _text_color_ | Specify the color of the text that will be displayed on the knob |
  | _text_font_ | Specify the font of the text that will be displayed on the knob |
  | _integer_ | A boolean (True/False), displays only the integer value in text if True (default=False) |
  | _fg_ | Define the color of the inner circle |
  | _progress_color_ | Define the color of the progress bar |
  | _bar_color_ | Define the color of the progress bar's background |
  | _inner_width_ | Specify the width of the inner ring |
  | _inner_color_ | Specify the color of the inner ring |
  | _outer_width_ | Specify the width of the outer ring |
  | _outer_length_ | Specify the distance between progress bar and outer ring |
  | _inner_color_ | Specify the color of the outer ring |
  | _steps_ | Number of steps per scroll |
  | _state_ | Specify the state of the needle |
  | _command_ | Call a function whenever the bar is moved |
  
### Methods:
  | Methods   | Description |
  |-----------|-------------|
  | _.get()_ | get the current value of the knob |
  | _.set()_ | set the value of the knob |
  | _.configure()_ | configure parameters of the knob | 
  
## Conclusion
This library is focused to create some circular widgets that can be used with Tkinter easily.
I hope it will be helpful for UI development in python.

**Want to contribute?** See [this](https://github.com/Akascape/TkDial/discussions/1)

[<img src="https://img.shields.io/badge/LICENSE-CC0_v0.1-informational?&color=blue&style=for-the-badge" width="200">](https://github.com/Akascape/TkDial/blob/main/LICENSE)
