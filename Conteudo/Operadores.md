# Operadores

Os operadores **(=, ++, --, +=, -=, ?:)** realizam a operação com os operandos (variáveis e valores).

Operador ternário:

```c#
int i = 43;
int i2 = (i==42 ? 10 : 20);
```

## Operadores de atribuição

`+`, `+=`, `-=`, `*=`, `/=` e `%=`

> **Note**
>
> O operador `+=` pode ser usado para concatenar strings

```c#
string s = "ABC";
s += "DEF";
Console.WriteLine(s); // Saída: ABCDEF
```

> **Note**
>
> `a++` e `++a` tem uma pequena diferença, assim como `a--` e `--a`

```cs
int a = 10;
int b = a++; //a atribuição é feita primeiro (b=10) e só depois a é incrementado (a=11)
Console.WriteLine(a); //11
Console.WriteLine(b); //10
a = 10;
b = ++a;
Console.WriteLine(a); //11
Console.WriteLine(b); //11
```


## Operadores aritméticos

> **Note**
>
> `*`, `/` e `%` tem precedência maior que `+` `-`

```c#
Console.WriteLine(3 + 4 * 2); // 11
Console.WriteLine((3 + 4) * 2); // 14
```

- **`Math.Pow(double x, double y)`**

###### [Math.Pow(Double, Double) Método](https://docs.microsoft.com/pt-br/dotnet/api/system.math.pow?view=net-6.0)

Parâmetros:

- `x` (Double) - Um número de ponto flutuante de precisão dupla a ser elevado a uma potência.
- `y` (Double) - Um número de ponto flutuante de precisão dupla que especifica uma potência.

Retornos:

- (Double) - O número x elevado à potência y.

- **`Math.Sqrt(double x)`**

###### [Math.Sqrt(Double) Método](https://docs.microsoft.com/pt-br/dotnet/api/system.math.sqrt?view=net-6.0)

Parâmetros:

- `x` (Double) - O número cuja raiz quadrada deve ser encontrada.

```c#
double delta = Math.Pow(b, 2.0) - 4.0 * a * c;
double x1 = (-b + Math.Sqrt(delta)) / (2.0 * a);
double x2 = (-b - Math.Sqrt(delta)) / (2.0 * a);
```

## Operadores aritméticos / atribuição

`++` e `--`

## Operadores comparativos

`>`, `<`, `>=`, `<=`, `==` e `!=`

## Operadores lógicos

`&&` (E), `||` (OU) e `!` (NÃO)

> **Note**
>
> Precedência: `!` > `&&` > `||`

```c#
Console.WriteLine(2 > 3 || 4 != 5); // Resultado: true
Console.WriteLine(!(2>3) && 4 != 5); // Resultado: true
```

###### [Para saber mais sobre operadores de comparação](https://docs.microsoft.com/pt-br/dotnet/csharp/language-reference/operators/comparison-operators)
