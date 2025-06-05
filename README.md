# Jogo Batalha naval

Este repositório contém o seguinte arquivo:

- Jogo Batalha naval

## Descrição

Atividade relacionada ao desafio **Super Trunfo**.

**O trabalho contido neste repositório integra o desenvolvimento do TCC.**

Este programa em C simula a fase inicial de preparação de um jogo de Batalha Naval. Ele inicializa um tabuleiro bidimensional, posiciona dois navios de tamanho fixo (um horizontalmente e outro verticalmente) em coordenadas pré-definidas e, em seguida, exibe o tabuleiro resultante. O foco está na representação do tabuleiro e na lógica básica de posicionamento e validação de limites.

## Desenvolvimento e Funções

O código foi desenvolvido de forma modular, dividindo as responsabilidades em funções distintas para clareza e organização.

### Constantes Globais

No início, são definidas constantes importantes usando `#define`:
- `TAMANHO_LINHA`, `TAMANHO_COLUNA`: Definem as dimensões do tabuleiro (10x10).
- `TAMANHO_NAVIO`: Define o comprimento dos navios (3 unidades).
- `VALOR_AGUA`: Valor numérico para representar uma célula com água (0).
- `VALOR_NAVIO`: Valor numérico para representar uma célula ocupada por parte de um navio (3).

### Estruturas de Dados

- **Tabuleiro**: Um array bidimensional `int tabuleiro[TAMANHO_LINHA][TAMANHO_COLUNA]` é usado para representar o campo de batalha.
- **Modelo do Navio**: Um array unidimensional `int navioModelo[TAMANHO_NAVIO]` é inicializado com `VALOR_NAVIO`. Ele serve como um "molde" para preencher as posições do tabuleiro ao posicionar um navio.

### Principais Funções

1.  **`inicializarTabuleiro(int tabuleiro[][TAMANHO_COLUNA])`**:
    * **Função**: Preenche todas as células da matriz `tabuleiro` com o `VALOR_AGUA` (0).
    * **Desenvolvimento**: Esta função garante que o tabuleiro comece em um estado limpo e conhecido antes de qualquer navio ser posicionado. É a primeira etapa lógica na preparação do jogo.

2.  **`exibirTabuleiro(int tabuleiro[][TAMANHO_COLUNA])`**:
    * **Função**: Imprime o estado atual do `tabuleiro` no console de forma organizada. Inclui índices numéricos para linhas e colunas e uma legenda para os valores (água e navio).
    * **Desenvolvimento**: Essencial para a visualização e depuração, permitindo ao usuário (ou desenvolvedor) verificar o resultado do posicionamento dos navios.

3.  **`posicionarNavio(int tabuleiro[][TAMANHO_COLUNA], const int navioModelo[], int tamanhoNavio, int linhaInicial, int colunaInicial, char orientacao)`**:
    * **Função**: Tenta posicionar um navio no tabuleiro.
        * Recebe as coordenadas iniciais (`linhaInicial`, `colunaInicial`), a `orientacao` ('H' para horizontal, 'V' para vertical) e o `tamanhoNavio`.
        * **Validação de Limites**: Verifica se o navio, na orientação e posição dadas, cabe inteiramente dentro dos limites do tabuleiro.
        * **Posicionamento**: Se a validação for bem-sucedida, preenche as células correspondentes do tabuleiro com os valores do `navioModelo` (ou seja, `VALOR_NAVIO`).
        * **Retorno**: Retorna `1` (verdadeiro) se o navio foi posicionado com sucesso, ou `0` (falso) se houve falha (fora dos limites ou orientação inválida).
    * **Desenvolvimento**: Esta é a função central para a lógica do jogo. A validação de sobreposição de navios é mencionada no código como "simplificada", o que significa que o design atual confia que as coordenadas de chamada da função `main` são escolhidas de forma a não causar sobreposição, em vez de a função `posicionarNavio` verificar ativamente por navios já existentes nas células alvo.

4.  **`main()`**:
    * **Função**: Orquestra a execução do programa.
        * Declara a matriz do tabuleiro e inicializa o `navioModelo`.
        * Chama `inicializarTabuleiro()` para preparar o campo.
        * **Posicionamento Fixo**: Tenta posicionar dois navios em coordenadas e orientações fixas, diretamente no código:
            * Um navio horizontal.
            * Um navio vertical.
            * Verifica o valor de retorno de `posicionarNavio()` e encerra o programa com erro se algum navio não puder ser posicionado.
        * Chama `exibirTabuleiro()` para mostrar o resultado final.
    * **Desenvolvimento**: A `main` demonstra o uso das outras funções em sequência para atingir o objetivo do programa. As coordenadas dos navios são "hardcoded" para simplificar esta demonstração de configuração do tabuleiro.

## Detalhes da Implementação

-   **Representação Numérica**: O uso de `0` para água e `3` para navio é uma escolha simples e eficaz para representar os estados das células no tabuleiro.
-   **Validação Simplificada**: Conforme mencionado, a validação de sobreposição de navios não é implementada ativamente na função `posicionarNavio`. Em um jogo completo, essa seria uma verificação crucial.
-   **Feedback ao Usuário**: O programa fornece mensagens de log no console indicando o sucesso ou falha no posicionamento dos navios, além de exibir o tabuleiro final de forma clara.
