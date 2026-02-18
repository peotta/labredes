# Atividade Prática
## Visualizando um Buffer Overflow na Stack

Disciplina: ENE0091 - Sistemas Operacionais de Redes  
Tema: Gerência de Memória e Segurança  
Professor: Prof. Dr. Laerte Peotta de Melo  

---

## 1. Objetivo

Demonstrar experimentalmente:

- Organização da stack
- Como ocorre um buffer overflow
- O que significa sobrescrever memória adjacente
- Como o sistema reage (segmentation fault)

---

## 2. Ambiente Necessário

- Linux (máquina física ou VM isolada)
- GCC
- gdb (debugger)

---

## 3. Parte 1 - Programa Vulnerável

Criar o arquivo `overflow.c`:

```c
#include <stdio.h>
#include <string.h>

void func() {
    char buffer[16];
    printf("Digite algo: ");
    gets(buffer);  // propositalmente inseguro
    printf("Você digitou: %s
", buffer);
}

int main() {
    func();
    return 0;
}
```

---

## 4. Parte 2 - Compilação Controlada

Compilar desativando proteções automáticas (apenas para fins didáticos em ambiente isolado):

```bash
gcc -fno-stack-protector -z execstack -o overflow overflow.c
```

---

## 5. Parte 3 - Execução Normal

Executar:

```bash
./overflow
```

Digite algo curto, por exemplo:

```
abc
```

O programa deve funcionar normalmente.

---

## 6. Parte 4 - Gerando Overflow

Executar novamente e digitar uma sequência longa, por exemplo:

```
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
```

Resultado esperado:

- Travamento do programa
- Ou mensagem de segmentation fault

---

## 7. Parte 5 - Observação com gdb

Abrir com:

```bash
gdb ./overflow
run
```

Inserir uma string longa.

Depois executar:

```bash
info registers
```

Observar possível corrupção do registrador de retorno.

---

## 8. Análise Conceitual

Esta atividade demonstra:

- Escrita além de 16 bytes
- Sobrescrita da stack
- Corrupção do controle de fluxo
- Intervenção do sistema operacional

---

## 9. Questões para Reflexão

1. Em que momento ocorre a falha?
2. O sistema operacional impede o erro?
3. O erro ocorre antes ou depois da tradução de endereços?
4. Qual região da memória foi afetada?
5. Isso viola o isolamento entre processos?

---

## 10. Conclusão Esperada

- O overflow ocorre dentro do próprio processo.
- A MMU não impede corrupção interna.
- Segurança depende também de programação segura.

---

## Observação Ética

Esta atividade é exclusivamente para fins educacionais, com foco em compreensão estrutural de vulnerabilidades e desenvolvimento seguro.
