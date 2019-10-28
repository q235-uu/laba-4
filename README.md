# laba-4
from tkinter import *
from random import randrange as rnd, choice
import time


def create_ball():
    global Aball
    print(Aball)
    c = 0
    for i in Aball:
        i.delete()
        i = Ball(rnd(100, 700), rnd(100, 500))
        Aball[c] = i
        print(i.placed)
        i.draw()
        c = c + 1
    root.after(1000, create_ball)


def update_ball():
    global moveball
    global c
    c.move(moveball.id, 10, 10)

    root.after(100,update_ball)


class Object:

    def __init__(self):
        pass

    def draw(self):
        pass


class Figure(Object):

    def __init__(self, color):
        pass


class Ball(Figure):
    placed = 0

    def __init__(self, x_coord, y_coord):
        self.r = rnd(20, 50)
        self.x = x_coord
        self.y = y_coord
        self.id = 0
        Ball.placed = Ball.placed + 1

    def draw(self):
        self.id = c.create_oval(self.x - self.r, self.y - self.r, self.x + self.r, self.y + self.r, fill=choice(cl))

    def delete(self):
        c.delete(self.id)



Aball = [ Ball(rnd(100, 700), rnd(100, 500)) ]
Aball.append( Ball(rnd(100, 700), rnd(100, 500)) )
root = Tk()
c = Canvas(root, width=800, height=700, bg='white')
c.pack()

cl = ['red', 'orange', 'yellow', 'green', 'blue']


print('new')
create_ball()

moveball = Ball(rnd(100, 700), rnd(100, 500))
moveball.draw()
update_ball()

root.mainloop()
