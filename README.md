# Batalha-Naval
#include <stdio.h>

#define TAM 5 // Tamanho do tabuleiro (5x5)

// Função para inicializar o tabuleiro com água
void inicializarTabuleiro(char tabuleiro[TAM][TAM]) {
    for (int i = 0; i < TAM; i++) {
        for (int j = 0; j < TAM; j++) {
            tabuleiro[i][j] = '~'; // '~' representa água
        }
    }
}

// Função para exibir o tabuleiro
void exibirTabuleiro(char tabuleiro[TAM][TAM]) {
    printf("   ");
    for (int j = 0; j < TAM; j++) {
        printf("%d ", j);
    }
    printf("\n");
    for (int i = 0; i < TAM; i++) {
        printf("%d  ", i);
        for (int j = 0; j < TAM; j++) {
            printf("%c ", tabuleiro[i][j]);
        }
        printf("\n");
    }
}

// Função que aplica uma habilidade especial (área em cruz)
void aplicarHabilidade(char tabuleiro[TAM][TAM], int linha, int coluna) {
    // Marca o centro da habilidade
    tabuleiro[linha][coluna] = 'X';

    // Cima
    if (linha > 0)
        tabuleiro[linha - 1][coluna] = 'X';

    // Baixo
    if (linha < TAM - 1)
        tabuleiro[linha + 1][coluna] = 'X';

    // Esquerda
    if (coluna > 0)
        tabuleiro[linha][coluna - 1] = 'X';

    // Direita
    if (coluna < TAM - 1)
        tabuleiro[linha][coluna + 1] = 'X';
}

int main() {
    char tabuleiro[TAM][TAM];

    // Inicializa o tabuleiro
    inicializarTabuleiro(tabuleiro);

    printf("Tabuleiro inicial:\n");
    exibirTabuleiro(tabuleiro);

    // Simula o uso de uma habilidade especial na posição (2,2)
    int linha = 2;
    int coluna = 2;
    aplicarHabilidade(tabuleiro, linha, coluna);

    printf("\nTabuleiro após aplicar habilidade na posição (%d,%d):\n", linha, coluna);
    exibirTabuleiro(tabuleiro);

    return 0;
}
