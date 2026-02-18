# Atividade Extraclasse
## Escalonamento Dinâmico Orientado por Métricas de Rede em Ambientes Cloud

**Disciplina: ENE0017 – Avaliação de Desempenho de Redes e Sistemas** 

Tema: Monitoramento, Escalonamento Dinâmico e Decisão Autônoma em Nuvem  
Professor: Prof. Dr. Laerte Peotta de Melo  

---

## 1. Objetivo

Analisar como métricas de rede podem influenciar decisões de escalonamento em ambientes de computação em nuvem, relacionando:

- Latência
- Throughput
- Perda de pacotes
- SLA (Service Level Agreement)
- Provisionamento de recursos

---

## 2. Contexto

Considere uma aplicação web hospedada em nuvem que atende usuários distribuídos geograficamente.  
Mesmo com CPU abaixo de 50%, usuários relatam lentidão.

Investigue se o problema está relacionado à rede e proponha uma política de escalonamento baseada em métricas de comunicação.

---

## 3. Parte Prática - Simulação de Congestionamento

### Ferramentas

- **iperf3** - Mede throughput TCP/UDP sob carga controlada entre cliente e servidor.
- **ping** - Mede latência (RTT) e perda de pacotes via ICMP.
- **tc (Traffic Control)** - Controla banda, atraso e filas para simular condições de rede.
- **vmstat ou top** - Monitora uso de CPU, memória e atividade do sistema em tempo real.

---

### Etapa 1 - Limitação de Banda

Simule um gargalo de rede:

```
sudo tc qdisc add dev eth0 root tbf rate 5mbit burst 32kbit latency 400ms
```

---

### Etapa 2 - Geração de Tráfego

Em uma máquina cliente:

```
iperf3 -c <IP_SERVIDOR> -t 60
```

---

### Etapa 3 - Monitoramento de Latência

Simultaneamente:

```
ping <IP_SERVIDOR>
```

Registrar:

- Latência média
- Latência máxima
- Variação (jitter aproximado)
- Throughput obtido
- Uso de CPU

---

## 4. Análise

Responder:

1. A CPU foi o gargalo do sistema?
2. A latência ultrapassou um SLA hipotético de 80 ms?
3. O throughput ficou próximo da capacidade configurada?
4. Em que momento deveria ocorrer escalonamento?
5. O escalonamento deveria ser horizontal ou vertical? Justifique.

---

## 5. Projeto Conceitual

Proponha uma política de escalonamento baseada em:

- Threshold de latência
- Percentual de perda aceitável
- Número mínimo de instâncias
- Tempo de estabilização para evitar oscilações

Apresente o fluxo de decisão no formato:

Monitoramento → Análise → Decisão → Ação → Reavaliação

---

## 6. Entrega

Relatório técnico (5 a 7 páginas) contendo:

- Ambiente utilizado
- Métricas coletadas (tabelas)
- Gráficos de latência e throughput
- Análise crítica
- Proposta de política de escalonamento

Formato: PDF.

---

## 7. Critérios de Avaliação

| Critério                          | Peso |
|-----------------------------------|------|
| Execução correta do experimento   | 25%  |
| Análise quantitativa              | 30%  |
| Fundamentação conceitual          | 25%  |
| Clareza e organização             | 20%  |

---

## 8. Competências Desenvolvidas

- Interpretação de métricas de rede
- Relação entre QoS e provisionamento
- Tomada de decisão baseada em dados
- Visão sistêmica de redes em nuvem
