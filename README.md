#include <stdio.h>
#include <string.h>

typedef struct {
    char estado[50];
    int codigo;
    char nome[50];
    long populacao;
    double pib;
    double area;
    int pontos_turisticos;
    double densidade_populacional;
    double pib_per_capita;
} Cidade;

void calcular_propriedades(Cidade *c) {
    c->densidade_populacional = c->populacao / c->area;
    c->pib_per_capita = c->pib / c->populacao;
}

void registrar_cidade(Cidade *c) {
    printf("Digite o estado: ");
    scanf(" %[^\n]", c->estado);

    printf("Digite o codigo: ");
    scanf("%d", &c->codigo);

    printf("Digite o nome da cidade: ");
    scanf(" %[^\n]", c->nome);

    printf("Digite a populacao: ");
    scanf("%ld", &c->populacao);

    printf("Digite o PIB (em reais): ");
    scanf("%lf", &c->pib);

    printf("Digite a area (em km²): ");
    scanf("%lf", &c->area);

    printf("Digite o numero de pontos turisticos: ");
    scanf("%d", &c->pontos_turisticos);

    calcular_propriedades(c);
}

void mostrar_cidade(Cidade c) {
    printf("\n=== CARTA SUPER TRUNFO ===\n");
    printf("Estado: %s\n", c.estado);
    printf("Codigo: %d\n", c.codigo);
    printf("Nome: %s\n", c.nome);
    printf("Populacao: %ld\n", c.populacao);
    printf("PIB: R$ %.2lf\n", c.pib);
    printf("Area: %.2lf km²\n", c.area);
    printf("Pontos Turisticos: %d\n", c.pontos_turisticos);
    printf("Densidade Populacional: %.2lf hab/km²\n", c.densidade_populacional);
    printf("PIB per Capita: R$ %.2lf\n", c.pib_per_capita);
}

int main() {
    int n;
    printf("Quantas cartas deseja registrar? ");
    scanf("%d", &n);

    Cidade cartas[n];

    for (int i = 0; i < n; i++) {
        printf("\n--- Registrando carta %d ---\n", i + 1);
        registrar_cidade(&cartas[i]);
    }

    for (int i = 0; i < n; i++) {
        mostrar_cidade(cartas[i]);
    }

    return 0;
}
