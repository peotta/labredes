# Atividade de Laboratório
## Análise Experimental de Desempenho em Redes IEEE 802.11

Disciplina: Redes de Computadores  
Tema: Fundamentos e Evolução do IEEE 802.11  
Professor: Prof. Dr. Laerte Peotta de Melo  

---

## 1. Objetivo

Avaliar experimentalmente:

- Diferença entre taxa nominal e throughput real  
- Impacto da largura de canal  
- Influência da distância no desempenho  
- Comportamento sob múltiplos usuários  

---

## 2. Ambiente Necessário

- 1 Access Point configurável (2.4 GHz e 5 GHz)  
- 2 ou mais notebooks  
- Software `iperf3`  
- Ferramenta de análise Wi-Fi (ex.: Wireshark ou inSSIDer)

> **iPerf** é uma ferramenta de linha de comando de código aberto para medição ativa da largura de banda máxima em redes IP, suportando protocolos TCP, UDP e SCTP. Ideal para validar links de operadoras e diagnosticar redes, funciona em modo cliente/servidor, geralmente na porta 5201.

> **inSSIDer** é uma ferramenta de diagnóstico e análise de redes Wi-Fi, desenvolvida pela MetaGeek, que escaneia o ambiente para identificar canais congestionados, força do sinal e interferências de rádio (RF) nas frequências de 2.4 GHz e 5 GHz. Ele permite otimizar o desempenho da rede ao escolher o melhor canal e identificar pontos cegos (dead spots).

> **Wireshark** é o analisador de protocolos de rede mais popular e utilizado no mundo, permitindo capturar e interagir com o tráfego que passa por uma rede em nível microscópico.

---

## 3. Parte A - Medição de Throughput Real

### Procedimento

1. Conectar dois dispositivos ao mesmo AP.
2. Executar no servidor:

```
iperf3 -s
```

3. No cliente:

```
iperf3 -c <IP_do_servidor> -t 30
```

4. Registrar:
   - Taxa nominal da conexão
   - Throughput médio medido

### Análise

Comparar taxa física anunciada vs throughput real.

Eficiência = Throughput_real / Taxa_nominal

---

## 4. Parte B - Impacto da Distância

1. Repetir teste a 1 metro do AP.
2. Repetir a 10 metros.
3. Repetir com obstáculos (paredes).

Registrar variação de:

- Taxa de modulação
- Throughput
- Perda de pacotes

Analisar relação entre SNR e desempenho.

---

## 5. Parte C - Múltiplos Usuários

1. Executar `iperf3` simultaneamente em dois clientes.
2. Comparar throughput individual.
3. Verificar divisão de banda.

Discutir:

- Compartilhamento de airtime
- Efeito da contenção CSMA/CA

---

## 6. Parte D - Largura de Canal

Se possível:

1. Configurar AP em 20 MHz.
2. Repetir testes.
3. Configurar em 40 ou 80 MHz.
4. Repetir medições.

Comparar:

- Throughput
- Estabilidade
- Interferência percebida

---

## 7. Relatório

Relatório técnico (5 a 8 páginas) contendo:

- Descrição do ambiente
- Tabelas com resultados
- Gráficos comparativos
- Cálculo de eficiência
- Análise crítica dos resultados

---

## 8. Questões para Discussão

1. Por que throughput real é inferior à taxa nominal?
2. Como distância afeta modulação?
3. Múltiplos usuários impactam igualmente todos?
4. Aumentar largura de canal sempre melhora desempenho?
5. Resultados confirmam teoria apresentada em aula?

---

## 9. Critérios de Avaliação

| Critério                          | Peso |
|-----------------------------------|------|
| Execução correta dos testes       | 30%  |
| Análise técnica                   | 30%  |
| Fundamentação teórica             | 25%  |
| Clareza do relatório              | 15%  |

---

## Competências Desenvolvidas

- Interpretação de desempenho real  
- Aplicação prática do padrão 802.11  
- Análise crítica de eficiência espectral  
- Conexão entre teoria e experimento  
