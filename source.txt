from tkinter import *
from tkinter.filedialog import askopenfilename
from tkinter.messagebox import showerror
import os, sys, shutil, os.path
import threading
import ctypes
import webbrowser




creators = ("created by bardiakzm ")
cr = (creators)
print(25*cr)

class StaticVariables:
   path = ""
   pathval = ""
   v = ""

def Double2Int(num):
    strNum = str(num)
    intNum = 0
    for i, c in enumerate(strNum):
        if c==".":
            intNum = int(strNum[:i]) 
    return intNum
def load_file():
   StaticVariables.path = askopenfilename(filetypes=(("Text files", "*.txt"),("All files", "*.*")))
   StaticVariables.pathval.set(StaticVariables.path)
   return
def Darsad(x,al):
   return (x*100)/al   
def NumsToArrays():
   if e1.get() is not None:
      num1 = int(e1.get())
      if e2.get() is not None:
         num2 = int(e2.get())
         

         if StaticVariables.path is None:
            ctypes.windll.user32.MessageBoxW(0, u"Please Choose the file",u"Information", 0)
         else:
            numbers = []
            text = ""
            Diffrent = 0
            if max(num1,num2) == num1 :
               ctypes.windll.user32.MessageBoxW(0, u"The first number is larger than the second number",u"Error", 0)
            else:
               Diffrent = num2-num1
               for x in range(num1,num2):
                  if x == num1:
                     text += str(x)+"\n"
                     text += str(x+1)+"\n"
                  else:
                     text += str(x+1)+"\n"
                  d = Darsad((x+1)-num1,Diffrent)
                  loading(Double2Int(d))

               
               f = open(StaticVariables.path, 'w')
               f.write(text)
               f.close()
      else:
         ctypes.windll.user32.MessageBoxW(0, u"Please Enter The Numbers",u"Information", 0)
   else:
      ctypes.windll.user32.MessageBoxW(0, u"Please Enter The Numbers",u"Information", 0)
   return

def loading(d):
   Loadings = ["█▒▒▒▒▒▒▒▒▒",
               "██▒▒▒▒▒▒▒▒",
               "███▒▒▒▒▒▒▒",
               "████▒▒▒▒▒▒",
               "█████▒▒▒▒▒",
               "██████▒▒▒▒",
               "███████▒▒▒",
               "████████▒▒",
               "█████████▒",
               "██████████"]
   
   
   if d < 10:
      StaticVariables.v.set(Loadings[0]+"  "+str(d)+"%")
   elif  d < 20:
      StaticVariables.v.set(Loadings[1]+"  "+str(d)+"%")
   elif  d < 30:
      StaticVariables.v.set(Loadings[2]+"  "+str(d)+"%")
   elif  d < 40:
      StaticVariables.v.set(Loadings[3]+"  "+str(d)+"%")
   elif  d < 50:
      StaticVariables.v.set(Loadings[4]+"  "+str(d)+"%")
   elif  d < 60:
      StaticVariables.v.set(Loadings[5]+"  "+str(d)+"%")
   elif  d < 70:
      StaticVariables.v.set(Loadings[6]+"  "+str(d)+"%")
   elif  d < 80:
      StaticVariables.v.set(Loadings[7]+"  "+str(d)+"%")
   elif  d < 90:
      StaticVariables.v.set(Loadings[8]+"  "+str(d)+"%")
   elif  d == 100:
      StaticVariables.v.set(Loadings[9]+"  "+str(d)+"%")
   return


def Start():
   threading.Thread(target=NumsToArrays).start()
   return
def runChannel():
   webbrowser.open('https://t.me/qbittm')

master = Tk()
master.title("Numbers Generator")
master.resizable(0, 0)

Label(master, text="Number 1 :").grid(row=0)
Label(master, text="Number 2 :").grid(row=1)
Label(master, text="File Path : ").grid(row=2)

StaticVariables.pathval = StringVar()
Label(master, textvariable=StaticVariables.pathval).grid(row=2,column=1)
StaticVariables.pathval.set("No File Selected")

StaticVariables.v = StringVar()
Label(master, textvariable=StaticVariables.v).grid(row=3,sticky=N+E+W+S,column=1)
StaticVariables.v.set("▒▒▒▒▒▒▒▒▒▒  0%")

e1 = Entry(master)
e2 = Entry(master)

e1.grid(row=0, column=1)
e2.grid(row=1, column=1)


Button(master, text='Quit', command=master.quit).grid(row=4, column=0, sticky=W, pady=5)
Button(master, text='Save', command=Start).grid(row=4, column=1, sticky=N, pady=5)
Button(master, text='https://github.com/bardiakzm', command=runChannel).grid(row=3, column=2, sticky=S+E, pady=5)
Button(master, text='where to save (.txt)', command=load_file).grid(row=4, column=2, sticky=S+E, pady=5)

mainloop()
