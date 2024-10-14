O GCC (GNU Compiler Collection) é uma ferramenta poderosa para compilar código C e C++ entre outras linguagens. Aqui estão os comandos básicos para compilar um programa em C usando o GCC:

### Comando básico:
```bash
gcc nome_do_arquivo.c -o nome_do_executavel
```

- `nome_do_arquivo.c`: O arquivo de código-fonte C que você deseja compilar.
- `-o nome_do_executavel`: Especifica o nome do arquivo executável resultante.

### Exemplo prático:

#### Código exemplo em C (`hello.c`):
```c
#include <stdio.h>

int main() {
    printf("Olá, mundo!\n");
    return 0;
}
```

### Comando para compilar:
```bash
gcc hello.c -o hello
```

### Executar o programa compilado:
No Linux/MacOS:
```bash
./hello
```
No Windows:
```bash
hello.exe
```

Este exemplo compila o código `hello.c` e cria um executável chamado `hello` (ou `hello.exe` no Windows). 
Quando executado, ele irá imprimir "Olá, mundo!" no terminal.
Para compilar e linkar usando o GCC, você geralmente segue um processo em duas etapas:

1. **Compilar** o código-fonte para arquivos objeto (.o).
2. **Linkar** esses arquivos objeto em um executável.

Aqui estão os comandos específicos para isso:

### 1. Compilar para arquivos objeto (.o)
```bash
gcc -c arquivo1.c -o arquivo1.o
gcc -c arquivo2.c -o arquivo2.o
```
- `-c`: Informa ao GCC para compilar o código-fonte sem fazer o link. O resultado será um arquivo objeto (`.o`).

### 2. Linkar os arquivos objeto para criar o executável
```bash
gcc arquivo1.o arquivo2.o -o nome_do_executavel
```

- Isso combina os arquivos objeto (`.o`) e gera o executável final.

### Exemplo completo

#### Arquivo 1 (`arquivo1.c`):
```c
#include <stdio.h>

void funcao();

int main() {
    printf("Executando o main!\n");
    funcao();
    return 0;
}
```

#### Arquivo 2 (`arquivo2.c`):
```c
#include <stdio.h>

void funcao() {
    printf("Função chamada de outro arquivo!\n");
}
```

### Passo 1: Compilar os arquivos para objeto
```bash
gcc -c arquivo1.c -o arquivo1.o
gcc -c arquivo2.c -o arquivo2.o
```

### Passo 2: Linkar os arquivos objeto e gerar o executável
```bash
gcc arquivo1.o arquivo2.o -o meu_programa
```

### Executar o programa compilado:
No Linux/MacOS:
```bash
./meu_programa
```
No Windows:
```bash
meu_programa.exe
```

O programa irá compilar e imprimir:
```
Executando o main!
Função chamada de outro arquivo!
```