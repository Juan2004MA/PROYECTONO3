# PROYECTONO.3
# PROYECTO NO.3
## José Miguel Marroquín (7690-23-16393)
## Juan José Marroquín (7690-23-16393)

```py

import tkinter as tk
from tkinter import filedialog
from tkinter import scrolledtext
from tkinter import messagebox
import os

 
def open_file():
    file_path = filedialog.askopenfilename(filetypes=[("Text files", "*.txt *.cpp *.cs *.py")])
    if file_path:
        with open(file_path, 'r') as file:
            text.delete('1.0', tk.END)
            text.insert(tk.INSERT, file.read())
        current_file.set(file_path)

def save_file():
    if current_file.get():
        with open(current_file.get(), 'w') as file:
            file.write(text.get('1.0', tk.END))
        messagebox.showinfo("Guardar", "Archivo guardado con éxito.")
    else:
        save_file_as()

def save_file_as():
    file_path = filedialog.asksaveasfilename(defaultextension=".txt", filetypes=[("Text files", "*.txt")])
    if file_path:
        with open(file_path, 'w') as file:
            file.write(text.get('1.0', tk.END))
        current_file.set(file_path)
        messagebox.showinfo("Guardar como", "Archivo guardado con éxito.")

def undo():
    text.edit_undo()

def redo():
    text.edit_redo()

def show_info():
    info = "Esta es una aplicación de ejemplo para leer, editar y guardar archivos de texto.\n\n"
    info += "Versión: 1.0\n"
    info += "Licencia: MIT\n"
    messagebox.showinfo("Información", info)


root = tk.Tk()
root.title("Editor de Texto")
root.geometry("1060x800")


current_file = tk.StringVar()


menu = tk.Menu(root)
root.config(menu=menu)

file_menu = tk.Menu(menu)
menu.add_cascade(label="Archivo", menu=file_menu)
file_menu.add_command(label="Abrir", command=open_file)
file_menu.add_command(label="Guardar", command=save_file)
file_menu.add_command(label="Guardar como", command=save_file_as)

edit_menu = tk.Menu(menu)
menu.add_cascade(label="Editar", menu=edit_menu)
edit_menu.add_command(label="Deshacer", command=undo)
edit_menu.add_command(label="Rehacer", command=redo)

help_menu = tk.Menu(menu)
menu.add_cascade(label="Ayuda", menu=help_menu)
help_menu.add_command(label="Información", command=show_info)

text = scrolledtext.ScrolledText(root, wrap=tk.WORD)
text.pack(expand=True, fill="both")

root.mainloop()
```

[presiona para ingresar a nuestro video](https://youtu.be/MXb7gCxh8d0?feature=shared )
