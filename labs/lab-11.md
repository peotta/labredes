# Atividade de Laboratório

## Monitoramento e Controle em uma Rede SDN Simples


## Objetivo

Demonstrar:

- Separação entre plano de controle e plano de dados
    
- Programabilidade da rede via controlador
    
- Visualização de fluxos em tempo real
    

---

## Ambiente Sugerido

- Mininet
    
- Controlador OpenDaylight ou Ryu
    
- Wireshark (opcional)
    

_(Pode ser descrito conceitualmente caso não haja execução real.)_

---

# Parte 1 - Topologia Simples

Criar no Mininet:

- 1 switch OpenFlow
    
- 2 hosts (h1 e h2)
    

Comando exemplo:

`sudo mn --topo single,2 --controller remote`

---

# Parte 2 — Observação Inicial

1. Realizar ping entre h1 e h2
    
2. Observar no controlador a criação dinâmica de fluxos
    
3. Verificar tabela de fluxos:
    

`ovs-ofctl dump-flows s1`

Pergunta ao aluno:

> Quem decide o encaminhamento: o switch ou o controlador?

---

# Parte 3 - Modificação Dinâmica

1. Inserir regra manual no switch
    
2. Alterar prioridade
    
3. Observar mudança no comportamento
    

Demonstrar:

- Programabilidade
    
- Controle centralizado
    
- Mudança dinâmica sem intervenção física
    

---

# Parte 4 - Reflexão Final

Comparar:

- SNMP: monitoramento passivo
    
- SDN: controle ativo e programável
    

Pergunta final:

> Como a centralização do controle facilita automação?

---

# Competências Desenvolvidas

- Compreensão arquitetural de SDN
    
- Visualização prática de fluxos
    
- Entendimento de APIs e controle centralizado
    
- Relação entre monitoramento e automação


# Entrega da Atividade de Laboratório

## Monitoramento e Controle em Redes SDN

------------------------------------------------------------------------

## Produto a ser Entregue

Cada grupo (ou aluno) deverá entregar um **Relatório Técnico
Simplificado (2--3 páginas)** em formato PDF.

------------------------------------------------------------------------

## Estrutura Obrigatória do Relatório

### Descrição da Topologia

-   Diagrama simples da rede criada
-   Identificação de:
    -   Hosts
    -   Switch OpenFlow
    -   Controlador SDN

------------------------------------------------------------------------

### Evidências de Execução

Apresentar:

-   Captura da tabela de fluxos **antes** da geração de tráfego
-   Captura da tabela de fluxos **após** execução de `ping`
-   Explicação objetiva das mudanças observadas

Exemplo de análise esperada:

-   Criação dinâmica de fluxo
-   Campos de *match*
-   Ação associada (*output*)

------------------------------------------------------------------------

### Análise Conceitual

Responder de forma objetiva:

1.  Quem toma a decisão de encaminhamento: o switch ou o controlador?
2.  Como o controlador influencia o plano de dados?
3.  Qual a diferença entre esse modelo e o modelo tradicional baseado em
    SNMP?

------------------------------------------------------------------------

### Reflexão Final (5--8 linhas)

Responder:

> Como a arquitetura SDN facilita automação e gerenciamento
> centralizado?

------------------------------------------------------------------------

## Critérios de Avaliação

 | Critério              | Peso |
|:----------------------|:-----:|
| Correção técnica      | 40%  |
| Clareza e organização | 30%  |
| Evidência de execução | 20%  |
| Reflexão crítica      | 10%  |


------------------------------------------------------------------------

## Prazo e Formato

-   Prazo: até 7 dias após a prática
-   Formato: PDF
-   Entrega via plataforma institucional

------------------------------------------------------------------------

## Objetivo Pedagógico

A atividade busca avaliar:

-   Compreensão da separação entre plano de controle e plano de dados
-   Entendimento da programabilidade da rede
-   Capacidade de análise crítica comparando SDN e modelo tradicional
