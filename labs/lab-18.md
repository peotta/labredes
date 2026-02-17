# Atividade de Laboratório
## Implementação e Análise de QoS em Redes TCP/IP

Disciplina: Redes de Computadores  
Tema: Qualidade de Serviço (QoS)  
Professor: Prof. Dr. Laerte Peotta de Melo  

---

## 1. Objetivo

Implementar e analisar mecanismos básicos de QoS para:

- Classificar e marcar tráfego (DSCP)
- Aplicar priorização de filas
- Observar impacto no desempenho
- Avaliar latência, jitter e perda
- Confirmar marcação via captura de pacotes

---

## 2. Ambiente Necessário

- 2 ou 3 máquinas Linux (ou VMs)
- Ferramentas instaladas:

  - **iperf3** - Mede throughput TCP/UDP sob carga controlada.

  - **ping** - Mede latência (RTT) e perda de pacotes via ICMP.

  - **tc** - Controla banda, atraso e filas para modelar tráfego.

  - **iptables** - Filtro que classifica e marca pacotes para aplicação de políticas.

  - **Wireshark** - Captura e analisa pacotes para diagnóstico de desempenho.


---

## 3. Cenário Experimental

Simular uma rede onde coexistem:

- Tráfego sensível à latência (ex.: ICMP simulando voz/vídeo)
- Tráfego de download intenso (TCP bulk)

Ambos competindo por um enlace limitado.

---

## 4. Parte A - Situação Sem QoS (Best-Effort)

### 1. Limitar o enlace

```
sudo tc qdisc add dev eth0 root tbf rate 10mbit burst 32kbit latency 400ms
```

### 2. Iniciar tráfego pesado

```
iperf3 -c <IP_destino> -P 5 -t 60
```

### 3. Medir latência simultaneamente

```
ping <IP_destino>
```

Registrar:

- RTT médio
- RTT máximo
- Variação do RTT
- Throughput total

---

## 5. Parte B - Marcação de Tráfego (DSCP)

Marcar tráfego ICMP como prioridade alta (EF - Expedited Forwarding):

```
sudo iptables -t mangle -A OUTPUT -p icmp -j DSCP --set-dscp 46
```

Verificar no Wireshark:

- Campo DSCP no cabeçalho IP
- Confirmação da marcação EF (valor 46)

---

## 6. Parte C - Implementação de Fila com Prioridade

Criar fila de prioridade:

```
sudo tc qdisc add dev eth0 root handle 1: prio
```

Associar filtros para priorizar pacotes marcados com DSCP 46.

Repetir testes de carga.

Comparar:

- RTT antes e depois da priorização
- Jitter
- Perda de pacotes
- Throughput agregado

---

## 7. Parte D - Análise com Wireshark

Durante os testes, capturar tráfego e observar:

- Campo DSCP
- Retransmissões TCP
- Duplicated ACKs
- TCP Window Size
- Gráfico de RTT (Statistics → TCP Stream Graph)

Registrar evidências de:

- Redução de latência para tráfego prioritário
- Impacto no tráfego bulk

---

## 8. Análise Esperada

Os alunos devem observar que:

- Sem QoS, a latência cresce sob carga.
- Com priorização, o tráfego marcado mantém RTT menor.
- QoS organiza o tráfego, mas não aumenta a capacidade total do enlace.

---

## 9. Relatório

Relatório técnico (5 a 8 páginas) contendo:

- Descrição da topologia
- Configurações aplicadas
- Tabelas comparativas
- Capturas do Wireshark
- Discussão técnica fundamentada

Formato: PDF.

---

## 10. Questões para Discussão

1. QoS eliminou o congestionamento ou apenas o reorganizou?
2. Qual foi o impacto real da marcação DSCP?
3. O TCP reagiu à priorização implementada?
4. Houve redução perceptível de jitter?
5. QoS pode substituir aumento de banda?

---

## 11. Critérios de Avaliação

| Critério                         | Peso |
|----------------------------------|------|
| Implementação correta            | 30%  |
| Análise quantitativa             | 30%  |
| Uso adequado do Wireshark        | 20%  |
| Discussão crítica                | 20%  |

---

## Competências Desenvolvidas

- Implementação prática de QoS
- Interpretação de métricas de desempenho
- Aplicação de marcação e priorização
- Análise de congestionamento baseada em evidências
