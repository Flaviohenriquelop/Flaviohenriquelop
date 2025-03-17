-
local libary

import pygame
import random

# Inicializando o Pygame
pygame.init()

# Definindo as dimensões da tela
SCREEN_WIDTH = 800
SCREEN_HEIGHT = 600
screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))
pygame.display.set_caption("Explorer com Hitbox")

# Definindo as cores
WHITE = (255, 255, 255)
GREEN = (0, 255, 0)
RED = (255, 0, 0)
BLUE = (0, 0, 255)

# Configuração da Hitbox
hitbox = pygame.Rect(300, 200, 200, 150)  # Posição e tamanho da hitbox
hitbox_active = False  # Estado inicial da hitbox

# Lista de jogadores (simulados)
players = [
    {'name': 'Jogador1', 'x': random.randint(50, 750), 'y': random.randint(50, 550)},
    {'name': 'Jogador2', 'x': random.randint(50, 750), 'y': random.randint(50, 550)},
    {'name': 'Jogador3', 'x': random.randint(50, 750), 'y': random.randint(50, 550)},
]

# Função para desenhar os jogadores
def draw_players():
    for player in players:
        pygame.draw.circle(screen, BLUE, (player['x'], player['y']), 10)
        font = pygame.font.SysFont('Arial', 18)
        text = font.render(player['name'], True, WHITE)
        screen.blit(text, (player['x'] + 15, player['y'] - 10))

# Função para desenhar a hitbox
def draw_hitbox():
    if hitbox_active:
        pygame.draw.rect(screen, GREEN, hitbox, 3)  # Desenha a hitbox quando ativada
        pygame.draw.rect(screen, GREEN, hitbox.inflate(4, 4), 3)  # Um pouco maior para destacar
    else:
        pygame.draw.rect(screen, RED, hitbox, 3)  # Desenha a hitbox desativada

# Função para verificar se o jogador está dentro da hitbox
def check_players_in_hitbox():
    if hitbox_active:
        for player in players:
            player_rect = pygame.Rect(player['x'] - 10, player['y'] - 10, 20, 20)
            if hitbox.colliderect(player_rect):
                print(f"{player['name']} está dentro da hitbox!")

# Loop principal do jogo
running = True
while running:
    screen.fill(WHITE)
    
    # Desenha os jogadores e a hitbox
    draw_players()
    draw_hitbox()
    
    # Verifica se os jogadores estão dentro da hitbox
    check_players_in_hitbox()
    
    # Processa os eventos de clique
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        if event.type == pygame.MOUSEBUTTONDOWN:
            if event.button == 1:  # Botão esquerdo do mouse
                mouse_pos = pygame.mouse.get_pos()
                # Verifica se o clique foi dentro da hitbox
                if hitbox.collidepoint(mouse_pos):
                    hitbox_active = not hitbox_active  # Alterna o estado da hitbox
                    print("Hitbox ativada!" if hitbox_active else "Hitbox desativada!")
    
    # Atualiza a tela
    pygame.display.update()

# Encerra o Pygame
pygame.quit()
Meu Nick:
Roblox: @hgfcuv
YouTube: @green_mods

