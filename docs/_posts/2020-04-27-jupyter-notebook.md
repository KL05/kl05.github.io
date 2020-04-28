---
title: Introdução à Julia
tags: [Introdução, Julia]
style: fill
color: secondary
description: Compiladores, editores e comandos básicos.
---

# Tópicos
1. 
2. 
3. 
4. 
5. 
6. 

## 

Colocar compiladores ou interpretadores (saber a diferença)

Online
Jupyter Notebook
https://jupyter.org/try

Offline
JuliaPro:
https://juliacomputing.com/products/juliapro#download-table
Visual Studio Code
https://code.visualstudio.com/
Anaconda + Jupyter Notebook
https://www.anaconda.com/products/individual


Lembrar que estou escrevendo para quem já entende de linguagens de programação

## Comandos Básicos

### Operações Básicas

```julia
soma = 3 + 7
diferenca = 10 - 3
produto = 20 * 5
quociente = 100 / 10
resto = 101 % 2
potencia = 10 ^ 2
fracao = 10 // 6
raiz_quadrada1 = sqrt(2)
raiz_quadrada2 = √2
# parte inteira do quociente:
quociente_inteiro1 = div(10, 6)
quociente_inteiro2 = 10 ÷ 6
```

Observação 1: para escrever `÷` basta digitar `\div` e apertar `Tab`.
Observação 2: para escrever `√` basta digitar `\sqrt` e apertar `Tab`.

### Imprimir

```julia
# string, variaveis

println("Imprime e pula uma linha.")

print("Imprime e não pula ")
print("linha.")

show("Hello World!") #imprime e não pula linha

println(""" É possível escrever 
            entre "aspas" e
            escreve do jeito que está 
            sendo apresentado.""")

#imprimir variavel,....

println("\t") # tab
println("\n") # pula linha


linguagem = "Julia"
versao = 1.4
println("Linguagem: $linguagem \nVersão: $versao") # também imprime a variável linguagem
println("Linguagem: ", linguagem, "\nVersão: ", versao) # outra maneira

numero1 = 10
numero2 = 20
println("$numero1 + $numero2 = $(numero1 + numero2)") # retorna a soma

# Concatenação:
s1 = "Hello "
s2 = "World!"
string(s1, s2)
s1*s2


```

### Variáveis

```julia
numero_inteiro = 10
numero_real = 3.14159
texto = "Hello World!"
caractere = 'a'
valor_lógico = true

quarenta_e_dois = (42, 42.0, 4.20e1, 4.20f1, 84//2, 0x2a)
```

### Comentário

```julia
# Comentário de uma linha.

#=
Comentário 
de 
múltiplas 
linhas.
=#

```
### Operadores Lógicos

```julia
and = false && true # retorna false
or = false || true # retorna true
```

### Comparação

```julia
igual = 1 == 1.0
diferente = 1 != 0
menor = 3 < π
menor_igual = 3 <= π
maior = 4 > 3
maior_igual = 4 => 4 
chain = 1 < 2 < 3
```

Observação 1: para escrever `π` basta digitar `\pi` e apertar `Tab`.
Observação 2: `π` = 3.1415926535897... 


### Tipos de Variável

Árvore dos tipos

```julia
typeof(variável) # retorna o tipo da variável

```

### Outros Comandos

```julia
y += 1 # equivalente à y = y + 1


# retorna como um erro
x = -42
x > 0 || error("x must be positive")

# retorna a documentação (em inglês)
?typeof

# variaveis especiais

#### Exemplo 2: Alfabeto Grego
Digite `\epsilon` e aperte `Tab`.<br>
Resultado (após atribuir um valor):

### Variáveis Especiais
Exemplos de algumas variáveis especiais.<br>
Para digitar outras variáveis basta seguir o mesmo procedimento mas mudando algumas letras. <br>
:::Deixar um link de outras variáveis.

#### Exemplo 1: Emoji
Digite `\:smi`, aperte `Tab`, selecione `smile_cat:`, aperte `Enter`, aperte `Tab` novamente, selecione a imagem e, por fim, aperte `Enter`.<br>
Resultado:

😺
# Atribuindo um valor:
😺 = "Smiley Cat!"
typeof(😺)

```


for x in fortytwos
    show(x)
    println("\t é um $(typeof(x))")
end



### Entrada e Saída

#readline(), parse
