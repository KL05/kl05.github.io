---
title: Método do Ponto Fixo [Julia]
tags: [Implementação, Julia, Link Externo, Métodos]
style: fill
color: secondary
description: Implementação em Julia do Método do Ponto Fixo.
---

# Método do ponto fixo
Seja $f: \mathbb{R} \rightarrow \mathbb{R}$ uma função contínua. Escrevendo $f(x) = 0$ como $g(x) = x$, pode-se encontrar o zero da função $f$ encontrando o ponto fixo da função $g$.
## Algoritmo
### Passo 1:
Defina o ponto de partida $x^{(0)}$, o número máximo de iterações e a tolerância.
### Passo 2:
Se $f(x^{(0)}) = 0$, então $x^{(0)}$ é o zero da função $f$ e o programa é finalizado. Caso contrário, faça $k = 0$ e passe para o próximo passo.
### Passo 3:
Faça
$$x^{(k+1)} = g(x^{(k)})$$
### Passo 4:
Enquanto a condição de parada não for atingida, faça $k = k + 1$ e volte para o Passo 3.

### Condição de Parada:
O programa será finalizado:
1. quando o número máximo de iterações for atingido ou 
2. quando for obtido a aproximação desejada, isto é, $\|x^{(k+1)}-x^{(k)}\| < {\rm{tolerância}}$. Nesse caso, $x^{(k+1)}$ é o zero da função $f$.



```Julia
function inputInt(msg::String)
    println(msg)
    parse(UInt64, readline())
end

function inputFloat(msg::String)
    println(msg)
    parse(Float64, readline())
end

f(x::Float64) = exp(x) - x - 2
g(x::Float64) = exp(x) - 2

function pontoFixo(x0::Float64,tolerancia::Float64,maxIteracao::UInt64)
    fx = f(x0)
    if fx == 0
        println(" Zero da função f: x = $x. \n Número de iterações: Nenhuma")
    else
        for iteracao = 1:maxIteracao
            x1 = g(x0)
            if abs(x1 - x0) < tolerancia
                return println(" Ponto fixo de g e zero da função f: x = $x1. \n Número de iterações: $iteracao.")
            end
            x0 = x1
        end
        error("Atingiu o número máximo de iterações!")
    end
end

x0 = inputFloat("Digite o ponto de partida: ")
tolerancia = inputFloat("Digite a tolerância: ")
maxIteracao = inputInt("Digite o número máximo de iterações:") 

pontoFixo(x0,tolerancia,maxIteracao)
```