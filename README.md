import pygame
import sys
import random

# Inicialização do Pygame
pygame.init()

# Configurações do jogo
largura = 800
altura = 600
cor_fundo = (255, 255, 255)  # Branco

# Configurações da frutinha
cor_frutinha = (255, 0, 0)  # Vermelho
tamanho_frutinha = 20

# Configurações do jogador
cor_jogador = (0, 0, 255)  # Azul
tamanho_jogador = 50
posicao_jogador = [largura // 2, altura - tamanho_jogador]

# Configurações da janela
tela = pygame.display.set_mode((largura, altura))
pygame.display.set_caption('Pegar Frutinhas Vermelhas')

# Loop principal
while True:
    for evento in pygame.event.get():
        if evento.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

    # Movimentação do jogador
    teclas = pygame.key.get_pressed()
    if teclas[pygame.K_LEFT] and posicao_jogador[0] > 0:
        posicao_jogador[0] -= 5
    if teclas[pygame.K_RIGHT] and posicao_jogador[0] < largura - tamanho_jogador:
        posicao_jogador[0] += 5

    # Desenhar fundo
    tela.fill(cor_fundo)

    # Criar frutinha
    frutinha_pos = [random.randint(0, largura - tamanho_frutinha), random.randint(0, altura - tamanho_frutinha)]
    pygame.draw.rect(tela, cor_frutinha, (frutinha_pos[0], frutinha_pos[1], tamanho_frutinha, tamanho_frutinha))

    # Desenhar jogador
    pygame.draw.rect(tela, cor_jogador, (posicao_jogador[0], posicao_jogador[1], tamanho_jogador, tamanho_jogador))

    # Atualizar a tela
    pygame.display.flip()

    # Controlar a taxa de atualização
    pygame.time.Clock().tick(30)
