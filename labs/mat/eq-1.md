<!-- ===================================================== -->
<!--  Equações Diferenciais — Lista Resolvida               -->
<!--  Autor: Prof. Dr. Laerte Peotta de Melo               -->
<!-- ===================================================== -->

# 📘 Equações Diferenciais — Lista de Exercícios Resolvidos

![Mathematics](https://img.shields.io/badge/Área-Matemática_Aplicada-blue)
![Equações Diferenciais](https://img.shields.io/badge/Tema-Equações_Diferenciais-green)
![LaTeX](https://img.shields.io/badge/LaTeX-MathJax-orange)

---

## 👨‍🏫 Autor

**Prof. Dr. Laerte Peotta de Melo**

---


## Questão 1/10 — Equações Diferenciais

**Enunciado**

Determine uma solução geral para:

$$
(1+y)\,dy - x\,dx = 0
$$

✅ **Resposta correta:** **A**

$$
2y+y^2-x^2+2c=0
$$

**Resolução**

$$
(1+y)\,dy=x\,dx
$$

$$
\int(1+y)\,dy=\int x\,dx
\Rightarrow y+\frac{y^2}{2}=\frac{x^2}{2}+C
$$

$$
2y+y^2=x^2+C' \Rightarrow 2y+y^2-x^2+2c=0
$$

---

## Questão 2/10 — Equações Diferenciais

**Enunciado**

Encontre uma solução geral de:

$$
y'+5y=t^3e^{-5t}
$$

usando fatores integrantes.

✅ **Resposta correta:** **D**

$$
y=\left(\frac{t^4}{4}+c\right)e^{-5t}
$$

**Resolução**

$$
\mu(t)=e^{\int 5\,dt}=e^{5t}
$$

$$
\frac{d}{dt}(e^{5t}y)=t^3
\Rightarrow e^{5t}y=\int t^3dt=\frac{t^4}{4}+C
$$

$$
y=\left(\frac{t^4}{4}+C\right)e^{-5t}
$$

---

## Questão 3/10 — Equações Diferenciais

**Enunciado**

Determine uma solução geral para:

$$
3y\frac{dy}{dx}=2x^2-3
$$

✅ **Resposta correta:** **A**

$$
y=\sqrt{\frac{4x^3}{9}-2x+\frac{2c}{3}}
$$

**Resolução**

$$
3y\,dy=(2x^2-3)\,dx
$$

$$
\int 3y\,dy=\int(2x^2-3)\,dx
\Rightarrow \frac{3}{2}y^2=\frac{2}{3}x^3-3x+C
$$

$$
y^2=\frac{4}{9}x^3-2x+C' \Rightarrow
y=\pm\sqrt{\frac{4}{9}x^3-2x+C'}
$$

---

## Questão 4/10 — Equações Diferenciais

**Enunciado**

Resolva por fatores integrantes:

$$
z'+z=0,\quad z(0)=1
$$

✅ **Resposta correta:** **D**

$$
z=e^{-t}
$$

**Resolução**

$$
\mu(t)=e^{\int 1\,dt}=e^t
$$

$$
\frac{d}{dt}(e^t z)=0 \Rightarrow e^t z=C \Rightarrow z=Ce^{-t}
$$

$$
z(0)=1 \Rightarrow C=1 \Rightarrow z=e^{-t}
$$

---

## Questão 5/10 — Equações Diferenciais

**Enunciado**

Resolva por fatores integrantes:

$$
y'-12y=4,\quad y(0)=1
$$

✅ **Resposta correta:** **C**

$$
y=-\frac{1}{3}+\frac{4}{3}e^{12t}
$$

**Resolução**

$$
\mu(t)=e^{\int(-12)\,dt}=e^{-12t}
$$

$$
\frac{d}{dt}(e^{-12t}y)=4e^{-12t}
\Rightarrow e^{-12t}y=\int 4e^{-12t}dt=-\frac{1}{3}e^{-12t}+C
$$

$$
y=-\frac{1}{3}+Ce^{12t}
$$

$$
y(0)=1 \Rightarrow 1=-\frac{1}{3}+C \Rightarrow C=\frac{4}{3}
$$

---

## Questão 6/10 — Equações Diferenciais

**Enunciado**

Resolva por fatores integrantes:

$$
y'-5y=-25x
$$

✅ **Resposta correta:** **A**

$$
y=5x+1+Ce^{5x}
$$

**Resolução**

$$
\mu(x)=e^{\int(-5)\,dx}=e^{-5x}
$$

$$
\frac{d}{dx}(e^{-5x}y)=-25x e^{-5x}
$$

Integração por partes em $$\int x e^{-5x}dx$$:

$$
\int x e^{-5x}dx=-\frac{x}{5}e^{-5x}-\frac{1}{25}e^{-5x}+C
$$

Logo:

$$
e^{-5x}y=-25\left(-\frac{x}{5}e^{-5x}-\frac{1}{25}e^{-5x}\right)+C
=5x e^{-5x}+e^{-5x}+C
$$

$$
y=5x+1+Ce^{5x}
$$

---

## Questão 7/10 — Equações Diferenciais

**Enunciado**

Resolva a equação separável:

$$
y'=2xy^2
$$

✅ **Resposta correta:** **A**

$$
y=\frac{-1}{x^2+c}
$$

**Resolução**

$$
\frac{dy}{dx}=2xy^2 \Rightarrow \frac{dy}{y^2}=2x\,dx
$$

$$
\int y^{-2}dy=\int 2x\,dx
\Rightarrow -\frac{1}{y}=x^2+C
$$

$$
y=-\frac{1}{x^2+C}
$$

---

## Questão 8/10 — Equações Diferenciais

**Enunciado**

Para verificar se

$$
M(x,y)\,dx+N(x,y)\,dy=0
$$

é exata, qual teste deve ser realizado?

✅ **Resposta correta:** **A**

$$
\frac{\partial M}{\partial y}=\frac{\partial N}{\partial x}
$$

**Resolução**

Uma equação é exata quando existe $$F(x,y)$$ tal que $$dF=Mdx+Ndy$$.  
Isso implica:

$$
F_x=M,\quad F_y=N \Rightarrow (F_x)_y=(F_y)_x
$$

Logo:

$$
\frac{\partial M}{\partial y}=\frac{\partial N}{\partial x}
$$

---

## Questão 9/10 — Equações Diferenciais

**Enunciado**

O fator integrante para uma equação pode ser dado por:

$$
\mu(x)=Ce^{\int R(x)\,dx}
$$

Determine $$R(x)$$.

✅ **Resposta correta:** **A**

$$
R(x)=\frac{1}{N}\left(\frac{\partial M}{\partial y}-\frac{\partial N}{\partial x}\right)
$$

**Resolução**

Para $$\mu=\mu(x)$$ em

$$
Mdx+Ndy=0
$$

pode-se usar a condição (quando depende apenas de $$x$$):

$$
\frac{1}{N}\left(\frac{\partial M}{\partial y}-\frac{\partial N}{\partial x}\right)=R(x)
$$

Então:

$$
\mu(x)=Ce^{\int R(x)\,dx}
$$

---

## Questão 10/10 — Equações Diferenciais

**Enunciado**

Dada

$$
y'+P(x)y=R(x)
$$

utilize

$$
\mu(x)=e^{\int P(x)\,dx}
$$

para resolver:

$$
y'+5y=-25
$$

✅ **Resposta correta:** **D**

$$
y=-5+Ce^{-5x}
$$

**Resolução**

$$
\mu(x)=e^{\int 5dx}=e^{5x}
$$

$$
\frac{d}{dx}(e^{5x}y)=-25e^{5x}
\Rightarrow e^{5x}y=\int -25e^{5x}dx=-5e^{5x}+C
$$

$$
y=-5+Ce^{-5x}
$$
