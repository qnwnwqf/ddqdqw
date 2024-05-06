import pygame
import random
pygame.init()
WHITE = (255, 255, 255)
BLACK = (0, 0, 0)
SCREEN_WIDTH = 800
SCREEN_HEIGHT = 600
screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))
pygame.display.set_caption("Крокодільчик")


class Crocodile(pygame.sprite.Sprite):
    def __init__(self):
        super().__init__()
        self.image = pygame.Surface((50, 50))
        self.image.fill(BLACK)
        self.rect = self.image.get_rect()
        self.rect.center = (SCREEN_WIDTH // 2, SCREEN_HEIGHT // 2)


def main():
    clock = pygame.time.Clock()

    crocodile = Crocodile()

    all_sprites = pygame.sprite.Group()
    all_sprites.add(crocodile)

    running = True
    while running:
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                running = False


        keys = pygame.key.get_pressed()
        if keys[pygame.K_LEFT]:
            crocodile.rect.x -= 5
        elif keys[pygame.K_RIGHT]:
            crocodile.rect.x += 5
        elif keys[pygame.K_UP]:
            crocodile.rect.y -= 5
        elif keys[pygame.K_DOWN]:
            crocodile.rect.y += 5

      
        screen.fill(WHITE)
        all_sprites.draw(screen)
        pygame.display.flip()

    
        clock.tick(60)

    pygame.quit()

if __name__ == "__main__":
    main()

