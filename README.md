# Laboratório de Compiladores

Este repositório contém os projetos e avaliações disciplina de **Compiladores**. Os projetos exploram a criação de analisadores léxicos e sintáticos utilizando as ferramentas **Flex** (Fast Lexical Analyzer Generator) e **Bison** (GNU Parser Generator), com foco na tradução para código intermediário (ILOC).

## 📂 Estrutura do Projeto

O repositório está organizado em três diretórios principais, cada um representando uma etapa ou versão diferente do compilador:

### 1. [ap2](./ap2)
Avaliação Parcial 2. Implementação inicial de um compilador simples.
- **Funcionalidades:** Declaração de variáveis (`VAR`), atribuição (`OP_ATT`), impressão (`PRINT`) e operações matemáticas básicas.
- **Gramática:** Suporta expressões matemáticas com precedência (soma, subtração, multiplicação e divisão).
- **Saída:** Gera comandos simplificados no estilo ILOC (ex: `loadI`, `add`, `mult`).

### 2. [ap3](./ap3)
Avaliação Parcial 3. Uma versão mais completa e robusta do compilador.
- **Funcionalidades:**
    - Estrutura de programa definida por `PROGRAM { ... }`.
    - Declaração de tipos: `int`, `float`, `string`.
    - Estruturas de controle: `if`, `else` e loop `for`.
    - Entrada e Saída: Comandos `in()` e `out()`.
    - Expressões matemáticas completas.
- **Geração de Código:** Tradução para **ILOC** salva no arquivo `output.il`.
- **Scripts:** Inclui `eder.sh` para facilitar o processo de compilação e teste.

### 3. [equipe](./equipe)
Projeto desenvolvido em equipe, focado em um avaliador de expressões matemáticas.
- **Funcionalidades:** Suporta soma, subtração, multiplicação, divisão, potência (`POW`) e resto da divisão (`MOD`).
- **Geração de Código:** Exibe os comandos ILOC correspondentes no terminal.

---

## 🛠️ Pré-requisitos

Para compilar e executar os projetos, você precisará de:
- **GCC** (GNU Compiler Collection)
- **Flex**
- **Bison**

No Linux (Ubuntu/Debian), você pode instalá-los via:
```bash
sudo apt-get update
sudo apt-get install flex bison build-essential
```

---

## 🚀 Como Executar

Cada subpastas possui sua própria lógica de compilação. Abaixo, um exemplo de como compilar e rodar a **ap3**:

1. Navegue até a pasta do projeto:
   ```bash
   cd ap3
   ```
2. Execute o script de automação (ou siga os passos manuais):
   ```bash
   # Utilizando o script fornecido
   chmod +x eder.sh
   ./eder.sh
   ```

**Passos Manuais (Exemplo ap3):**
```bash
# 1. Gerar o analisador léxico
flex ap3Flex.l

# 2. Gerar o analisador sintático
bison -d ap3Bison.y

# 3. Compilar os arquivos gerados com o GCC
gcc lex.yy.c ap3Bison.tab.c -lfl -lm

# 4. Executar passando um arquivo de entrada
./a.out < input.txt
```

---

## 📝 Linguagem Suportada (Exemplificação ap3)

```c
PROGRAM {
    int x;
    int y;
    x = 10;
    y = 5 + x;
    
    if (y > 10) {
        out(y);
    } else {
        out(x);
    }

    for (i = 0; i < 10; i + 1) {
        out(i);
    }
}
```

## ✒️ Autores

Desenvolvido para fins acadêmicos na disciplina de Compiladores.
