# Atividade de Laboratório
## Análise Experimental de Filas e Desempenho em Redes IP

Disciplina: Redes de Computadores  
Tema: Comutação por Pacotes e Teoria de Filas  
Professor: Prof. Dr. Laerte Peotta de Melo  

---

## 1. Objetivo

Avaliar experimentalmente:

- Atraso fim-a-fim  
- Impacto da carga na latência  
- Formação de filas  
- Relação entre utilização (ρ) e atraso  
- Evidência de congestionamento  
- Comparação com modelo teórico M/M/1  

---

## 2. Ambiente Necessário

- 2 ou 3 máquinas físicas ou VMs na mesma rede  
- Sistema Linux (preferencial)  
- Ferramentas instaladas:
  - **iperf3** - Mede throughput da rede (TCP/UDP) sob carga controlada.
  - **ping** - Mede latência (RTT) e perda de pacotes via ICMP.
  - **tc (Traffic Control)** - Controla banda, atraso e filas para simular congestionamento.
  - **Wireshark** - Captura e analisa pacotes para identificar retransmissões, RTT e sinais de congestionamento.

---

## 3. Parte A — Medição Base (Sem Congestionamento)

### Procedimento

1. Iniciar servidor:
```
iperf3 -s
```

2. No cliente:
```
iperf3 -c <IP_servidor> -t 30
```

3. Medir RTT médio:
```
ping <IP_servidor>
```

Registrar:

- Throughput médio
- RTT médio
- RTT máximo
- Perda de pacotes

---

## 4. Parte B — Simulação de Gargalo

Criar limitação artificial de banda:

```
sudo tc qdisc add dev eth0 root tbf rate 10mbit burst 32kbit latency 400ms
```

Repetir testes com iperf3 e ping.

Registrar:

- Throughput obtido
- RTT médio
- Variação do RTT (jitter)

---

## 5. Parte C — Aumento Progressivo de Carga

Executar múltiplos fluxos simultâneos:

```
iperf3 -c <IP_servidor> -P 5 -t 30
```

Aumentar progressivamente o número de fluxos até saturação.

Registrar:

- Throughput agregado
- RTT médio
- RTT máximo
- Perdas observadas

---

## 6. Parte D — Coleta e Análise com Wireshark

### Captura de Pacotes

1. Iniciar captura na interface ativa.
2. Aplicar filtro:
```
ip.addr == <IP_servidor>
```

3. Durante testes de carga, observar:

- Intervalo entre pacotes
- Retransmissões TCP
- Janela TCP (Window Size)
- Duplicated ACKs
- TCP Fast Retransmission

### Métricas a Extrair

- RTT calculado pelo Wireshark (Statistics → TCP Stream Graph → Round Trip Time)
- Taxa de retransmissão
- Número de pacotes descartados
- Variação no tempo entre pacotes

---

## 7. Parte E — Comparação com Modelo Teórico

Calcular:

ρ = λ / μ

Onde:

- λ = taxa agregada medida
- μ = capacidade nominal do enlace

Comparar:

- Crescimento do atraso observado
- Comportamento não linear próximo da saturação
- Evidência prática do efeito 1/(1−ρ)

---

## 8. Parte F — Análise de Buffer

Alterar tamanho do buffer:

```
sudo tc qdisc change dev eth0 root pfifo limit 1000
```

Depois:

```
sudo tc qdisc change dev eth0 root pfifo limit 100
```

Comparar:

- RTT médio
- RTT máximo
- Perdas
- Evidência de bufferbloat

---

## 9. Relatório

Relatório técnico (6 a 8 páginas) contendo:

- Metodologia detalhada
- Tabelas de resultados
- Gráficos RTT × carga
- Análise de capturas Wireshark
- Cálculo de utilização
- Comparação teoria × experimento
- Discussão crítica

Formato: PDF.

---

## 10. Questões para Discussão

1. Em que ponto o atraso cresceu abruptamente?
2. O modelo M/M/1 explica adequadamente o comportamento observado?
3. Houve evidência clara de congestionamento no Wireshark?
4. O aumento do buffer reduziu perdas, mas aumentou latência?
5. Como AQM poderia melhorar o desempenho observado?

---

## 11. Critérios de Avaliação

| Critério                          | Peso |
|-----------------------------------|------|
| Execução correta dos testes       | 25%  |
| Análise quantitativa              | 30%  |
| Uso adequado do Wireshark         | 20%  |
| Comparação com teoria             | 15%  |
| Clareza do relatório              | 10%  |

---

## Competências Desenvolvidas

- Medição experimental de desempenho
- Interpretação de teoria de filas aplicada
- Análise de congestionamento via captura de pacotes
- Relação entre utilização, atraso e perda
- Análise crítica baseada em evidências empíricas

---

## Resultado Esperado

O estudante deverá demonstrar compreensão quantitativa do comportamento de filas em redes IP, evidenciando experimentalmente a relação entre carga, atraso e congestionamento.
