# NASM-to-compile
 Aqui está uma lista de comandos NASM para compilar:

```markdown
# Comandos NASM para Compilação

## Introdução
O NASM (Netwide Assembler) é um montador de código de baixo nível que converte código assembly em código de máquina. Este guia fornece os comandos básicos para compilar e vincular programas escritos em assembly usando o NASM.

## Comandos Básicos

### 1. Compilação
Para compilar um arquivo assembly (`.asm`) em um arquivo objeto (`.o` ou `.obj`), use o comando:
```bash
nasm -f formato arquivo.asm -o arquivo.o
```
- **`-f formato`**: Especifica o formato do arquivo de saída. Formatos comuns incluem:
  - `elf` para Linux
  - `win32` para Windows (32 bits)
  - `win64` para Windows (64 bits)
  - `coff` para outros sistemas
  - `macho` para macOS

**Exemplo**:
```bash
nasm -f elf arquivo.asm -o arquivo.o
```

### 2. Montagem e Linkagem
Após compilar o código, o próximo passo é linkar o arquivo objeto para gerar um executável. Dependendo do sistema operacional, o comando de linkagem varia.

#### Para Linux:
Utilize o `ld` (linker):
```bash
ld -m elf_i386 -s -o executavel arquivo.o
```
- **`-m elf_i386`**: Especifica o formato do arquivo de saída (32 bits).
- **`-s`**: Remove símbolos não utilizados.

**Exemplo**:
```bash
ld -m elf_i386 -s -o meu_programa arquivo.o
```

#### Para Windows:
Use o `gcc` para vincular:
[GCC](https://github.com/0joseDark/NASM-gcc-to-compile/blob/main/gcc.md)

```bash
gcc -o executavel.exe arquivo.o
```

**Exemplo**:
```bash
gcc -o meu_programa.exe arquivo.o
```

### 3. Compilação e Linkagem em Um Só Comando
Em muitos casos, você pode querer compilar e vincular em um único comando. Para isso, o NASM pode ser combinado com o `gcc` ou `ld`.

#### Para Linux:
```bash
nasm -f elf arquivo.asm && ld -m elf_i386 -s -o executavel arquivo.o
```

#### Para Windows:
```bash
nasm -f win32 arquivo.asm && gcc -o executavel.exe arquivo.o
```

## Flags Úteis

### -g
Inclui informações de depuração no arquivo objeto.
```bash
nasm -f elf -g arquivo.asm -o arquivo.o
```

### -l
Gera um arquivo de listagem, que é útil para depuração.
```bash
nasm -f elf arquivo.asm -l arquivo.lst -o arquivo.o
```

### -I
Especifica um diretório para incluir arquivos.
```bash
nasm -I /caminho/para/includes arquivo.asm
```

## Exemplo Completo

Aqui está um exemplo completo de um processo de compilação:

1. Crie um arquivo `programa.asm` com o seguinte conteúdo:
   ```asm
   section .data
   msg db 'Hello, World!', 0

   section .text
   global _start

   _start:
       ; escrever a mensagem
       mov eax, 4          ; syscall: sys_write
       mov ebx, 1          ; file descriptor: stdout
       mov ecx, msg        ; pointer to message
       mov edx, 13         ; message length
       int 0x80            ; call kernel

       ; sair do programa
       mov eax, 1          ; syscall: sys_exit
       xor ebx, ebx        ; return 0
       int 0x80            ; call kernel
   ```

2. Compile e vincule o programa:
   ```bash
   nasm -f elf programa.asm -o programa.o
   ld -m elf_i386 -s -o programa programa.o
   ```

3. Execute o programa:
   ```bash
   ./programa
   ```

## Conclusão
O NASM é uma ferramenta poderosa para desenvolvimento em assembly. Com os comandos acima, você pode compilar e vincular programas de forma eficaz. Para mais informações, consulte a [documentação do NASM](https://www.nasm.us/doc/).
```

Sinta-se à vontade para copiar e usar este conteúdo para seus projetos.
