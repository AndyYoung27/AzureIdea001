import pygame
import random

pygame.init()

size = (1440,960)

screen = pygame.display.set_mode(size)
pygame.display.set_caption("Snow Animation")
bg = pygame.image.load("泠然.JPG")

snow_list = []

for i in range(200):
    x = random.randrange(0,size[0])
    y = random.randrange(0,size[1])
    sx = random.randint(-1,1)
    sy = random.randint(3,6)
    snow_list.append([x,y,sx,sy])

clock = pygame.time.Clock()

done = False
while not done:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            done = True
    screen.blit(bg,(0,0))

    for i in range(len(snow_list)):
        pygame.draw.circle(screen,(255,255,255),snow_list[i][:2],snow_list[i][3]-3)

        snow_list[i][0] += snow_list[i][2]
        snow_list[i][1] += snow_list[i][3]

        if snow_list[i][1] > size[1]:
            snow_list[i][1] = random.randrange(-50,-10)
            snow_list[i][0] = random.randrange(0,size[0])

    pygame.display.flip()
    clock.tick(20)

pygame.quit()
