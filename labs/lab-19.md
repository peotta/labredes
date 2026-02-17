# Atividade de Laboratório
## Análise de Convergência e Comportamento do RIP

Disciplina: Redes de Computadores  
Tema: RIP - Routing Information Protocol  
Professor: Prof. Dr. Laerte Peotta de Melo  

---

## 1. Objetivo

- Implementar roteamento dinâmico com RIP  
- Observar atualizações periódicas  
- Medir tempo de convergência  
- Analisar comportamento diante de falhas  
- Identificar limitações do protocolo  

---

## 2. Ambiente Necessário

- PNetLab instalado e funcional  
- 3 roteadores (Cisco IOS, FRRouting ou equivalente)  
- 2 PCs virtuais (VPCS ou Linux)  
- Ferramentas:
  - ping  
  - traceroute  
  - show ip route  
  - debug ip rip  

---

## 3. Topologia Proposta

```
PC1 - R1 - R2 - R3 - PC2
```

Cada roteador com rede própria.  
RIP habilitado apenas nas interfaces internas.

---

## 4. Parte A - Configuração Inicial no PNetLab

### 1. Configuração de IP

Atribuir endereços IP às interfaces e testar conectividade local.

### 2. Ativar RIP (Exemplo Cisco IOS)

```
router rip
 version 2
 no auto-summary
 network 10.0.0.0
```

### 3. Verificar Tabela de Rotas

```
show ip route
```

Confirmar rotas marcadas com “R”.

---

## 5. Parte B - Observação das Atualizações

Executar:

```
debug ip rip
```

Observar:

- Atualizações a cada 30 segundos  
- Métrica (hop count)  
- Uso de multicast 224.0.0.9  

---

## 6. Parte C - Teste de Conectividade

A partir do PC1:

```
ping <IP_PC2>
traceroute <IP_PC2>
```

Verificar caminho escolhido com base na métrica.

---

## 7. Parte D - Simulação de Falha

Desativar interface entre R2 e R3.

Observar:

- Tempo até perda de conectividade  
- Tempo até nova rota ser propagada  
- Atualização gradual da métrica  

Medir o tempo de convergência.

---

## 8. Parte E - Análise de Problemas

Durante a falha, analisar:

- Existência de loop temporário  
- Aumento progressivo da métrica (count-to-infinity)  
- Tempo total de estabilização  

---

## 9. Relatório

Relatório técnico (4 a 6 páginas) contendo:

- Topologia utilizada  
- Configuração aplicada  
- Tabelas de rotas antes e depois da falha  
- Tempo de convergência medido  
- Análise crítica das limitações do RIP  

Formato: PDF.

---

## 10. Questões para Discussão

1. Por que o RIP apresenta convergência lenta?  
2. Qual o impacto do limite de 15 saltos?  
3. O que caracteriza o problema de count-to-infinity?  
4. Split horizon ajudaria neste cenário?  
5. RIP é adequado para redes modernas?  

---

## 11. Critérios de Avaliação

| Critério                      | Peso |
|-------------------------------|------|
| Configuração correta          | 30%  |
| Medição da convergência       | 25%  |
| Análise técnica               | 30%  |
| Clareza e organização         | 15%  |

---

## Competências Desenvolvidas

- Implementação prática de vetor de distância  
- Medição experimental de convergência  
- Análise de comportamento sob falha  
- Avaliação crítica de protocolo de roteamento
