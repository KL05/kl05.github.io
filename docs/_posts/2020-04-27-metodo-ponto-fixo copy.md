---
title: Método do Ponto Fixo [Julia]
tags: [Implementação, Julia, Link Externo, Métodos]
style: fill
color: secondary
description: Implementação em Julia do Método do Ponto Fixo.
---

{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Método da Secante\n",
    "\n",
    "Seja $f:\\mathbb{R} \\rightarrow \\mathbb{R}$ uma função contínua.\n",
    "\n",
    "## Algoritmo\n",
    "### Passo 1:\n",
    "Defina os pontos de partida $x^{(0)}$ e $x^{(1)}$, o número máximo de iterações e a tolerância.\n",
    "### Passo 2:\n",
    "Se $f(x^{(0)}) = 0$ (ou $f(x^{(1)}) = 0$), então $x^{(0)}$ (ou $x^{(1)})$ é o zero da função $f$, e o programa é finalizado. Caso contrário, faça $k = 0$ e passe para o próximo passo.\n",
    "### Passo 3:\n",
    "Faça\n",
    "$$x^{(k+2)} = x^{(k+1)} - f(x^{(k+1)}) \\cdot \\frac{x^{(k+1)} - x^{(k)}}{f(x^{(k+1)}) - f(x^{(k)})}.$$\n",
    "### Passo 4:\n",
    "Enquanto a condição de parada não for atingida, faça $k = k + 1$ e volte para o Passo 3.\n",
    "\n",
    "### Condição de parada:\n",
    "O programa será finalizado:\n",
    "1. quando o número máximo de iterações for atingido ou \n",
    "2. quando for obtido a aproximação desejada, isto é, $|x^{(k+2)}-x^{(k+1)}| < {\\rm{tolerância}}$. Nesse caso, $x^{(k+2)}$ é o zero da função $f$."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "inputFloat (generic function with 1 method)"
      ]
     },
     "execution_count": 5,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "function inputInt(prompt::String)\n",
    "    println(prompt)\n",
    "    parse(UInt64, readline())\n",
    "end\n",
    "\n",
    "function inputFloat(prompt::String)\n",
    "    println(prompt)\n",
    "    parse(Float64, readline())\n",
    "end"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "f (generic function with 1 method)"
      ]
     },
     "execution_count": 6,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "f(x::Float64) = x^2 - 2"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "secante (generic function with 1 method)"
      ]
     },
     "execution_count": 7,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "function secante(x0::Float64,x1::Float64,tolerancia::Float64,maxIteracao::UInt64)\n",
    "    fx0 = f(x0)\n",
    "    fx1 = f(x1)\n",
    "    if fx0 == 0\n",
    "        println(\" Zero da função f: x = $x0\")\n",
    "    elseif fx1 == 0\n",
    "        println(\" Zero da função f: x = $x1\")\n",
    "    else\n",
    "        for iteracao = 1:maxIteracao\n",
    "            if fx1 == fx0\n",
    "                error(\"Divisão por 0 na $iteracao iteracao!\")\n",
    "            end\n",
    "            x2 = x1 - fx1*(x1-x0)/(fx1-fx0)\n",
    "            if abs(x2 - x1) < tolerancia\n",
    "                return println(\" Zero da função f: x = $x2.\\n Número de iterações: $iteracao.\")\n",
    "            end\n",
    "            x0 = x1\n",
    "            x1 = x2\n",
    "            fx0 = f(x0)\n",
    "            fx1 = f(x1)\n",
    "        end\n",
    "        error(\"Atingiu o número máximo de iterações!\")\n",
    "    end\n",
    "end"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Digite o primeiro ponto de partida: \n",
      "stdin> 0\n",
      "Digite o segundo ponto de partida: \n",
      "stdin> 1\n",
      "Digite a tolerância: \n",
      "stdin> 0.0000001\n",
      "Digite o número máximo de iterações:\n",
      "stdin> 1000\n",
      " Zero da função f: x = 1.4142135623730954.\n",
      " Número de iterações: 7.\n"
     ]
    }
   ],
   "source": [
    "x0 = inputFloat(\"Digite o primeiro ponto de partida: \")\n",
    "x1 = inputFloat(\"Digite o segundo ponto de partida: \")\n",
    "tolerancia = inputFloat(\"Digite a tolerância: \")\n",
    "maxIteracao = inputInt(\"Digite o número máximo de iterações:\") \n",
    "\n",
    "secante(x0,x1,tolerancia,maxIteracao)"
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Julia 1.4.0",
   "language": "julia",
   "name": "julia-1.4"
  },
  "language_info": {
   "file_extension": ".jl",
   "mimetype": "application/julia",
   "name": "julia",
   "version": "1.4.0"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 4
}
