### Project Prerequisites
**Tkinter** is a standard GUI Python library that is one of the fastest and easiest ways to build GUI applications. <br>
**gTTS (Google Text-to-Speech)** is a Python library, which is a very easy library that converts the text into audio. <br>
The **playsound** module is used to play audio files. With this module, we can play a sound file with a single line of code. <br>

### Initializing window
```python
root = Tk()
root.geometry("350x300") 
root.configure(bg='ghost white')
root.title("TEXT TO SPEECH")
```
- **Tk()** to initialized tkinter which will be used for GUI <br>
- **geometry()** used to set the width and height of the window <br>
- **configure()** used to access window attributes <br>
- **bg** will used to set the color of the background <br>
- **title()** set the title of the window <br>

```python
Label(root, text = "TEXT_TO_SPEECH", font = "arial 20 bold", bg='white smoke').pack()
Label(text ="Avi", font = 'arial 15 bold', bg ='white smoke' , width = '20').pack(side = 'bottom')

Msg = StringVar()
Label(root,text ="Enter Text", font = 'arial 15 bold', bg ='white smoke').place(x=20,y=60)

entry_field = Entry(root, textvariable = Msg ,width ='50')
entry_field.place(x=20,y=100)
```
**Label()** widget is used to display one or more than one line of text that users can’t able to modify. <br>

- **root** is the name which we refer to our window <br>
- **text** which we display on the label <br>
- **font** in which the text is written <br>
- **pack** organized widget in block <br>
- **Msg** is a string type variable <br>
- **Entry()** used to create an input text field <br>
- **textvariable** used to retrieve the current text to entry widget <br>
- **place()** organizes widgets by placing them in a specific position in the parent widget <br>

### Function to Convert Text to Speech
```python
filename = 1
def Text_to_speech():
    global filename
    Message = entry_field.get()
    speech = gTTS(text = Message)
    speech.save(str(filename) + '.mp3')
    playsound(str(filename) + '.mp3')
    filename += 1
```
- **Message** variable will stores the value of entry_field <br>
- **text** is the sentences or text to be read. <br>
- **lang** takes the language to read the text. The default language is English. <br>
- **slow** use to reads text more slowly. The default is False. <br>

As we want the default value of lang, so no need to give that to gTTS. <br>

- **speech** stores the converted voice from the text <br>
- **speech.save(str(filename) + '.mp3')** will saves the converted file as a mp3 file and each time the Text_to_speech() function will execute the filename number will increased by 1 to solve the duplicate filename problem. <br>
- **playsound()** used to play the sound <br>

### Function to Exit
```python
def Exit():
    root.destroy()
```
**root.destroy()** will quit the program by stopping the mainloop(). <br>

### Function to Reset
```python
def Reset():
    Msg.set("")
```
**Reset** function set Msg variable to empty strings.

### Define Buttons
```python
Button(root, text = "PLAY", font = 'arial 15 bold' , command = Text_to_speech ,width = '4').place(x=25,y=140)

Button(root, font = 'arial 15 bold',text = 'RESET', width = '6' , command = Reset).place(x=100 , y = 140)

Button(root, font = 'arial 15 bold',text = 'EXIT', width = '4' , command = Exit, bg = 'OrangeRed1').place(x=250 , y = 140)
```
**Button()** widget used to display button on the window.

### Run Program
```python
root.mainloop()
```
**root.mainloop()** is a method that executes when we want to run our program.

### Output
- GUI
  <p align="left">
  <a href="https://github.com/sahaavi/Convert-Text-to-Speech/blob/main/Output/GUI.jpg"><img width src="https://github.com/sahaavi/Convert-Text-to-Speech/blob/main/Output/GUI.jpg?raw=true" alt="HackerRank" height="400" width="250" ></a>
    </p>
- [Sound](https://github.com/sahaavi/Convert-Text-to-Speech/blob/main/Output/1.mp3)
