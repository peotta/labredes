# Atividade Extraclasse
## Testando Segurança sob Modelo CCA com OpenSSL

---

## Objetivo

Comparar, na prática:

- Um esquema sem autenticação (potencialmente vulnerável sob CCA)
- Um esquema com autenticação (mais robusto sob CCA)

Utilizando OpenSSL no terminal.

---

## Parte 1 — Cenário A (Sem Autenticação)

Utilizar AES-CBC, que fornece confidencialidade, mas não integridade.

### 1. Criar arquivos de teste

```bash
echo "SIM" > sim.txt
echo "NAO" > nao.txt
```

---

### 2. Gerar chave e IV

```bash
openssl rand -hex 16
openssl rand -hex 16
```

Guarde a chave e o IV gerados.

---

### 3. Cifrar com AES-CBC

```bash
openssl enc -aes-128-cbc -in sim.txt -out sim.enc -K CHAVE -iv IV
openssl enc -aes-128-cbc -in nao.txt -out nao.enc -K CHAVE -iv IV
```

---

### 4. Teste CCA Conceitual

Visualizar o conteúdo:

```bash
xxd sim.enc
```

Alterar um byte do arquivo:

```bash
printf '\x00' | dd of=sim.enc bs=1 seek=5 count=1 conv=notrunc
```

Tentar decifrar:

```bash
openssl enc -d -aes-128-cbc -in sim.enc -K CHAVE -iv IV
```

Observar:

- Mensagem de erro?
- Saída parcialmente legível?
- Comportamento diferente?

Objetivo: perceber que o sistema tenta decifrar mesmo com alteração.

---

## Parte 2 — Cenário B (Com Autenticação)

Utilizar AES-256-GCM, que é criptografia autenticada (AEAD).

### 1. Cifrar com GCM

```bash
openssl enc -aes-256-gcm -in sim.txt -out sim_gcm.enc -K CHAVE -iv IV -a
```

---

### 2. Modificar ciphertext

Alterar um byte como feito anteriormente.

---

### 3. Tentar decifrar

```bash
openssl enc -d -aes-256-gcm -in sim_gcm.enc -K CHAVE -iv IV -a
```

Observar:

- O sistema retorna erro?
- Ele se recusa a decifrar?
- A saída é bloqueada?

---

## Análise Esperada

| Modo     | Comportamento ao alterar ciphertext |
|----------|-------------------------------------|
| AES-CBC  | Tenta decifrar; pode produzir saída alterada |
| AES-GCM  | Falha completamente; rejeita ciphertext |

---

## Conclusão Conceitual

- AES-CBC oferece confidencialidade, mas não integridade.
- AES-GCM oferece confidencialidade e integridade.
- Segurança sob CCA exige resistência a modificações de ciphertext.

Relacionar com:

|Pr[b' = b] - 1/2| ≤ ε

---

## Entrega

Relatório de 2 a 4 páginas contendo:

- Descrição dos testes realizados
- Evidências observadas
- Comparação entre os dois modos
- Conclusão sobre segurança sob CCA


## Critérios de Avaliação

| Critério                   | Peso |
|----------------------------|------|
| Correção conceitual        | 30%  |
| Implementação adequada     | 25%  |
| Análise experimental       | 25%  |
| Fundamentação matemática   | 20%  |

---

## Competências Desenvolvidas

- Compreensão formal de IND-CCA
- Relação entre teoria e implementação
- Importância de integridade em criptografia
- Análise probabilística de segurança

---

## Valor Didático

Segurança não depende apenas do algoritmo, mas do modelo de interação.
