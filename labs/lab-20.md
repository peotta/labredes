# Atividade Extraclasse Prática
## Análise Experimental de Memória Virtual e Paginação

Disciplina: Sistemas Operacionais  
Tema: Fundamentos de Memória Virtual  
Professor: Prof. Dr. Laerte Peotta de Melo  

---

## 1. Objetivo

Investigar, na prática:

- Funcionamento da memória virtual  
- Ocorrência de page faults  
- Impacto do uso de memória na performance  
- Evidências de thrashing  
- Relação entre teoria (working set) e comportamento real  

---

## 2. Ambiente Necessário

- Sistema Linux (máquina física ou VM)  
- Ferramentas:
  - vmstat  
  - top ou htop  
  - free -m  
  - perf (opcional)  
  - Python ou C  

---

## 3. Parte A - Observação do Estado Inicial

Executar:

```
free -m
vmstat 1
```

Registrar:

- Memória total e livre  
- Uso de swap  
- Taxa de page faults  
- Uso de CPU  

---

## 4. Parte B - Programa Gerador de Page Faults

Criar um programa que:

- Aloca grande vetor na memória  
- Acessa posições espaçadas pelo tamanho da página (4 KB)

### Exemplo em Python:

```python
import time

size = 500_000_000
array = bytearray(size)

for i in range(0, size, 4096):
    array[i] = 1
    time.sleep(0.0001)
```

Executar e monitorar:

```
vmstat 1
```

Observar:

- Aumento de page faults  
- Crescimento de uso de memória  
- Uso de swap (se houver)  

---

## 5. Parte C - Pressão de Memória

Executar múltiplas instâncias do programa.

Monitorar:

- Crescimento de swap  
- Aumento da taxa de page faults  
- Tempo de resposta do sistema  

Analisar possível ocorrência de thrashing.

---

## 6. Parte D - Experimento com Working Set

Modificar o programa para:

- Acessar repetidamente apenas uma parte do vetor  
- Expandir progressivamente o conjunto de páginas acessadas  

Comparar:

- Taxa de page faults  
- Tempo de execução  

Relacionar resultados com o conceito de working set.

---

## 7. Parte E - Análise Teórica

Responder:

1. Se o tamanho da página for 4 KB, quantas páginas o programa aloca?  
2. Qual o impacto esperado se a RAM disponível for menor que o conjunto ativo?  
3. Como a TLB influencia o desempenho observado?  

---

## 8. Relatório

Relatório técnico (5 a 7 páginas) contendo:

- Descrição do ambiente  
- Código utilizado  
- Tabelas com dados coletados  
- Gráficos (page faults × tempo)  
- Análise comparando teoria e experimento  

Formato: PDF.

---

## 9. Questões para Discussão

1. Em que momento o sistema começou a degradar?  
2. Houve evidência clara de thrashing?  
3. O aumento da memória virtual melhora desempenho?  
4. A TLB é perceptível diretamente nesse experimento?  
5. Qual algoritmo de substituição o Linux utiliza?  

---

## 10. Critérios de Avaliação

| Critério                    | Peso |
|-----------------------------|------|
| Execução correta            | 25%  |
| Análise quantitativa        | 30%  |
| Fundamentação teórica       | 25%  |
| Clareza e organização       | 20%  |

---

## Competências Desenvolvidas

- Observação prática de memória virtual  
- Análise de page faults  
- Interpretação de thrashing  
- Relação entre modelo teórico e comportamento real  
