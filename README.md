# not-remember
import pygame
import pygame.midi
from pygame.locals import *

# Initialize Pygame
pygame.init()
pygame.midi.init()

# Set up the screen
SCREEN_WIDTH = 800
SCREEN_HEIGHT = 400
WHITE = (255, 255, 255)
BLACK = (0, 0, 0)
screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))
pygame.display.set_caption("Simple Piano")

# Set up the piano keys
KEY_WIDTH = SCREEN_WIDTH // 14
KEY_HEIGHT = SCREEN_HEIGHT // 2
KEY_COLOR = WHITE
BLACK_KEY_COLOR = BLACK
keys = []

for i in range(14):
    if i % 7 in {0, 3}:
        keys.append(pygame.Rect(i * KEY_WIDTH, 0, KEY_WIDTH, KEY_HEIGHT))
    else:
        keys.append(pygame.Rect(i * KEY_WIDTH - KEY_WIDTH // 4, 0, KEY_WIDTH // 2, KEY_HEIGHT // 2))

# Main loop
running = True
while running:
    screen.fill(BLACK)

    # Draw keys
    for key in keys:
        pygame.draw.rect(screen, KEY_COLOR, key)

    # Check for events
    for event in pygame.event.get():
        if event.type == QUIT:
            running = False
        elif event.type == KEYDOWN:
            if event.key == K_a:
                print("C")
            elif event.key == K_w:
                print("C#")
            elif event.key == K_s:
                print("D")
            elif event.key == K_e:
                print("D#")
            elif event.key == K_d:
                print("E")
            elif event.key == K_f:
                print("F")
            elif event.key == K_t:
                print("F#")
            elif event.key == K_g:
                print("G")
            elif event.key == K_y:
                print("G#")
            elif event.key == K_h:
                print("A")
            elif event.key == K_u:
                print("A#")
            elif event.key == K_j:
                print("B")
            elif event.key == K_k:
                print("C (high octave)")

    pygame.display.flip()

# Clean up
pygame.midi.quit()
pygame.quit()
