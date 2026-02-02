---
layout: post
title:  " F1 Game Project (gameloop, drawing and turning basics)"
---
This is the documentation for my A level F1 game project. This is a module of my Computer Science course to develop an extended project. I picked to make a top down F1 racing game. Here is a prototype version I made using functions I found online and following tutorials from YouTube. I made this to learn more about the complicated functions and scripts I would need to implement into the final design.

This is the first stages of the game, and it is completely unplayable. This was made to develop an understanding about the basics of pygame. This code focuses on drawing the actual assets, creating a game loop and a complicated function that allows the car to turn without causing complications that would otherwise be faced such as the car turning and moving x,y positions.
```python
import pygame
import time
import math
from funcs import scale_image



#imports all the assets and assigns them to a constant variable
GRASS = scale_image(pygame.image.load("images/grass.jpg"), 2.5)
TRACK = scale_image(pygame.image.load("images/track.png"), 0.9)

TRACK_BORDER = scale_image(pygame.image.load("images/track-border.png"), 0.9)
FINISH = pygame.image.load("images/finish.png")

RED_CAR = scale_image(pygame.image.load("images/red-car.png"), 0.55)
GREEN_CAR = scale_image(pygame.image.load("images/green-car.png"), 0.55)

WIDTH, HEIGHT = TRACK.get_width(), TRACK.get_height()
WIN = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Racing Game!")

#variable for the maximum speed of the program
FPS = 60

#function for rotating the car without problems occuring
def blit_rotate_center(win, image, top_Left, angle):
    rotated_image = pygame.transform.rotate(image, angle)
    new_rect = rotated_image.get_rect(center=image.get_rect(topleft = top_Left).center)
    win.blit(rotated_image, new_rect.topleft)

#creates a class that can be applied to any of the cars
class AbstractCar:

    def __init__(self, max_vel, rotation_vel): #defines the variables for the car
       #applies all of the atrributes to the car
        self.img = self.IMG
        self.max_vel = max_vel
        self.vel = 0
        self.rotation_vel = rotation_vel
        self.angle = 0
        self.x, self.y = self.START_POS
    
    #function for rotating the car
    def rotate(self, left=False, right=False):
        if left == True:
            self.angle += self.rotation_vel
        elif right == False:
            self.angle -= self.rotation_vel

    
    def draw(self, win):
        blit_rotate_center(win, self.img, (self.x, self.y), self.angle)

#creates a class specifically for the player car and uses the abstract class to apply the attributes without repitition
class PlayerCar(AbstractCar):
    IMG = RED_CAR
    START_POS = (180, 200)


def draw(win, images, player_car): #function that draws the images
    for img, pos in images:
        win.blit(img, pos)

    player_car.draw(win)
    pygame.display.update()

run = True #sets run variable to be true so the game loop can run
clock = pygame.time.Clock() #creates the clock
images = [(GRASS, (0, 0)), (TRACK, (0, 0))] #the images that will be drawn
player_car = PlayerCar(4, 4)


while run == True:
    clock.tick(FPS) #sets the maximum speed of the program to be the value of FPS variable
    draw(WIN, images, player_car)

    for event in pygame.event.get(): #responsible for closing the program
        if event.type == pygame.QUIT: 
            run = False
            break

pygame.quit()
```
This is the external file I used for some functions:
```python
import pygame

def scale_image(img, factor):
    size = round(img.get_width() * factor), round(img.get_height() * factor)
    return pygame.transform.scale(img, size)
```
This was one of my first time using object oriented programming rather than functional programming. The core principles of OOP (object oriented programming) are that you define the attributes of an element using class functions. This is especially useful in game development when you want to have different characters with different attributes for example.