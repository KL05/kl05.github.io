# Método da Bisseção
Seja $f:[a,b] \rightarrow \mathbb{R}$ uma função contínua. Se $f(a) \cdot f(b) \leq 0$, então existe um zero da função $f$ no intervalo $[a,b]$.

## Algoritmo
### Passo 1:
Defina o extremo direito e o extremo esquerdo do intervalo, o número máximo de iterações e a tolerância.
### Passo 2:
Verifique se $f(a)$ (ou $f(b)$) é nulo. Se for, então $a$ (ou $b$) é o zero da função $f$ e o programa é finalizado. Caso contrário, faça $k = 0$ e passe para o próximo passo.
### Passo 3:
Faça
$$x^{(k)} = \frac{a+b}{2}.$$
### Passo 4:
Enquanto a condição de parada não for atingida, verifique os casos abaixo:

Caso 1: se $f(x^{(k)}) = 0$, então $x^{(k)}$ é o zero da função $f$ e o programa é finalizado; <br>
Caso 2: se $f(a) \cdot f(x^{(k)}) < 0$, então o zero da função $f$ está no intervalo $(a, x^{(k)})$. Portanto, faça $b = x^{(k)}$, $k = k + 1$ e volte para o Passo 3; <br>
Caso 3: se $f(x^{(k)}) \cdot f(b) < 0$, então o zero da função $f$ está no intervalo $(x^{(k)}, b)$. Portanto, faça $a = x^{(k)}$, $k = k + 1$ e volte para o Passo 3.
### Condição de parada:
O programa será finalizado:
1. quando o número máximo de iterações for atingido ou 
2. quando for obtido a aproximação desejada, isto é, $\dfrac{|b-a|}{2} < {\rm{tolerância}}$. Nesse caso, $x^{(k)}$ é o zero da função $f$.


```julia
function inputInt(prompt::String)
    println(prompt)
    parse(UInt64, readline())
end

function inputFloat(prompt::String)
    println(prompt)
    parse(Float64, readline())
end
```




    inputFloat (generic function with 1 method)




```julia
f(x::Float64) = x^2 - 2
```




    f (generic function with 1 method)




```julia
function bissecao(a::Float64,b::Float64,tolerancia::Float64,maxIteracao::UInt64)
    fa = f(a)
    fb = f(b)
    if fa == 0
        println(" Zero da função f: x = $a")
    elseif fb == 0
        println(" Zero da função f: x = $b")
    else
        fa*fb < 0 || error("Não foi possível determinar o zero da função f no intervalo ($a,$b), pois f($a)*f($b) = $(f(a)*f(b)) > 0.")
        iteracao = 1
        local x
        while abs(b-a)/2 > tolerancia
            x = (a+b)/2
            fx = f(x)
            if fx == 0
                break
            elseif fa*fx < 0.0
                b = x
            else
                a = x
                fa = fx
            end
            iteracao != maxIteracao || error("Atingiu o número máximo de iterações! \na = $a, b = $b, f($x) = $fx")
            iteracao += 1
        end
        println(" Zero da função f: x = $x. \n Número de iterações: $iteracao.")
    end
end
```




    bissecao (generic function with 1 method)




```julia
a = inputFloat("Digite o extremo esquerdo: ")
b = inputFloat("Digite o extremo direito: ")
tolerancia = inputFloat("Digite a tolerância: ")
maxIteracao = inputInt("Digite o número máximo de iterações: ")

bissecao(a,b,tolerancia,maxIteracao)
```

    Digite o extremo esquerdo: 
    stdin> 0
    Digite o extremo direito: 
    stdin> 5
    Digite a tolerância: 
    stdin> 0.000001
    Digite o número máximo de iterações: 
    stdin> 1000
     Zero da função f: x = 1.4142143726348877. 
     Número de iterações: 23.
    
