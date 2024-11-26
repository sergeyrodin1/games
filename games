import pygame
import sys

# Инициализация Pygame
pygame.init()

# Размер окна
WIDTH, HEIGHT = 800, 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Лабиринт от 2-го лица")

# Цвета
WHITE = (255, 255, 255)
BLACK = (0, 0, 0)
RED = (255, 0, 0)
BLUE = (0, 0, 255)
GREEN = (0, 255, 0)

# Игрок
player_size = 30
player_pos = [50, 50]
player_speed = 5

# Лабиринт (прямоугольники - стены)
walls = [
    pygame.Rect(100, 0, 20, 500),
    pygame.Rect(200, 100, 20, 500),
    pygame.Rect(300, 0, 20, 400),
    pygame.Rect(400, 200, 20, 400),
    pygame.Rect(500, 0, 20, 300),
]

# Финишная точка
finish = pygame.Rect(700, 500, 50, 50)

# Шрифт
font = pygame.font.Font(None, 36)

# Главный цикл игры
clock = pygame.time.Clock()
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
    
    # Управление игроком
    keys = pygame.key.get_pressed()
    if keys[pygame.K_w]:
        player_pos[1] -= player_speed
    if keys[pygame.K_s]:
        player_pos[1] += player_speed
    if keys[pygame.K_a]:
        player_pos[0] -= player_speed
    if keys[pygame.K_d]:
        player_pos[0] += player_speed

    # Проверка на столкновение со стенами
    player_rect = pygame.Rect(player_pos[0], player_pos[1], player_size, player_size)
    for wall in walls:
        if player_rect.colliderect(wall):
            # Откат позиции при столкновении
            if keys[pygame.K_w]:
                player_pos[1] += player_speed
            if keys[pygame.K_s]:
                player_pos[1] -= player_speed
            if keys[pygame.K_a]:
                player_pos[0] += player_speed
            if keys[pygame.K_d]:
                player_pos[0] -= player_speed

    # Проверка на достижение финиша
    if player_rect.colliderect(finish):
        screen.fill(WHITE)
        text = font.render("Вы выиграли!", True, GREEN)
        screen.blit(text, (WIDTH // 2 - text.get_width() // 2, HEIGHT // 2))
        pygame.display.flip()
        pygame.time.wait(3000)
        running = False

    # Рисование
    screen.fill(BLACK)
    pygame.draw.rect(screen, RED, player_rect)  # Игрок
    for wall in walls:
        pygame.draw.rect(screen, WHITE, wall)  # Стены
    pygame.draw.rect(screen, BLUE, finish)  # Финиш

    # Обновление экрана
    pygame.display.flip()
    clock.tick(30)

pygame.quit()
sys.exit()
