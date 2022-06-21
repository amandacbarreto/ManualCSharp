# C# - Interações Classe Console

## Conversão do valor lido através do Console.ReadLine()

### TryParse

```c#
Console.WriteLine("Insira o valor da compra em reais: ");
Double.TryParse(Console.ReadLine(), out double valorDaCompraEmReais);
```

### Números fracionados com `.` e com `,`

##### [System.Globalization](https://docs.microsoft.com/pt-br/dotnet/api/system.globalization?view=net-6.0)

##### [CultureInfo](https://docs.microsoft.com/pt-br/dotnet/api/system.globalization.cultureinfo?view=net-6.0)

No meu caso, por padrão o C# ignoraria o `.` de um número fracionado. Por exemplo:

```c#
double peso;
Console.WriteLine("Informe o seu peso em quilos: ");
Double.TryParse(Console.ReadLine(), out peso); // Entrada: 50.85
Console.WriteLine(peso); // Sáida: 5085
```

Para resolver esse problema, é possível usar o `CultureInfo.InvariantCulture` sendo necessário o uso do namespace `System.Globalization`. Porém pode acontecer o seguinte erro (CASO 2).

```c#
using System.Globalization;
Console.WriteLine("Informe o seu peso em quilos: ");
double peso = double.Parse(Console.ReadLine(), CultureInfo.InvariantCulture);
Console.WriteLine(peso);

/* CASO 1
Entrada: 25.2
Saída: 25,2

CASO 2
Entrada: 25,2
Saída: 252
```

Outra forma de resolver é substituindo o `.` por `,` na string, como no exemplo abaixo:

```c#
double peso;
string entrada;
Console.WriteLine("Informe o seu peso em quilos: ");
entrada = Console.ReadLine()!;
if (entrada.Contains("."))
{
    entrada = entrada.Replace(".", ",");
}
Double.TryParse(entrada, out peso);
Console.WriteLine(peso);

/* CASO 1
Entrada: 50.8
Saída: 50,8

CASO 2
Entrada: 50,8
Saída: 50,8
```

> **Note** o método `Replace` utilizado na string entrada apenas retorna uma nova string. Ele não modifica a string original, por isso é necessário que a variável entrada recebe o novo valor.

## Formatação de números decimais

### ToString("N2")

```c#
double pi = 3.14159265359;
Console.WriteLine(pi.ToString("N2")); // 3.14
Console.WriteLine(pi.ToString("F3")); // 3,141
```
