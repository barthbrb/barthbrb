from tkinter import*
from random import*
from PIL import Image, ImageTk

def ship(numFrame):
    can.delete('all')
    numFrame=numFrame+1
    can.create_image(coordonnee[0],coordonnee[1],anchor=NW,image=vaisseau)
    if coordonnee[0]>500 or coordonnee[0]<1:
        position='neutral'
    if direction=='right':
        coordonnee[0]+=20
    if direction=='left':
        coordonnee[0]-=20
    if direction=='neutral':
        coordonnee[0]+=0
        coordonnee[1]+=0
        print(coordonnee)
    tk.after(100,lambda:ship(numFrame))


    
def right(event):#defnition du mouvement a droite
    global direction
    direction='right'
    #print(direction)
 

def left(event):#definition du mouvement a gauche
    global direction
    direction='left'
    #print(direction)


tk=Tk()
can=Canvas(tk,width=500,height=500, bg='black')
can.pack()
coordonnee=[225,350]
direction='neutral'
vaisseau_png=Image.open('vaisseau.png')
vaisseau=ImageTk.PhotoImage(vaisseau_png)
ship(0)
tk.bind('<d>',right)
tk.bind('<q>',left)

tk.mainloop()
