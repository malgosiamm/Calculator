# -*- coding: utf-8 -*-
from Tkinter import*

calculator = Tk() 

menubar = Menu(calculator)

def appear(x): 
   return lambda: results.insert(END, x) 

def Zero(): 
   results.insert(END, "0") 
def Refresh():
   results.delete(0, END)
def Equals(): 
   try: 
       result = eval(results.get()) 
   except: 
       result = "Invalid sum" 
   results.delete(0, END) 
   results.insert(0, result)
def Dot():
	results.insert(END, ".")
def Times():
   results.insert(END, "*")
def Divide():
   results.insert(END, "/")
def Plus():
   results.insert(END, "+")
def Minus():
   results.insert(END, "-")
def Delete():
   results.delete(-1)

screen = Frame(calculator)
buttons = Frame(calculator)
screen.grid(column=0, row=0, padx=0, pady=0)
buttons.grid(column=0, row=1, padx=1)

numbers = StringVar()
results = Entry(screen, textvariable=numbers, width=24)
results.pack()
results.grid(column=0, row=0)

numbers=["7", "4", "1", "8", "5", "2", "9", "6", "3"] 

for index in range(9): 
   n=numbers[index] 
   Button(buttons, text=n, 
command=appear(n), relief=GROOVE).grid(row=index%3, column=index/3)

delete= Button(buttons, text="←", command=Delete) 
delete.grid(column=3, row=3)

times = Button(buttons, text="*", command=Times) 
times.grid(column=3, row=1)

divide = Button(buttons, text="/", command=Divide) 
divide.grid(column=4, row=1)

plus = Button(buttons, text="+", command=Plus) 
plus.grid(column=3, row=2)

minus = Button(buttons, text="-", command=Minus) 
minus.grid(column=4, row=2)

zero= Button(buttons, text="0", command=Zero) 
zero.grid(column=0, row=3)

refresh= Button(buttons, text="AC", command=Refresh) 
refresh.grid(column=2, row=3)

dot= Button(buttons, text=".", command=Dot) 
dot.grid(column=1, row=3)

equals= Button(buttons, text="=", command=Equals) 
equals.grid(column=4, row=3)


calculator.config(menu=menubar) 
calculator.mainloop()
