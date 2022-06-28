# C# - Interações Classe Console

## Quebra de linha

```c#
Console.Write("Com esse método 'Write' não teremos a quebra de linha. ");
Console.WriteLine("Ou seja, o proximo 'Write' ou 'ReadLine' será feito imediatamente após (junto) à frase anterior. ");

Console.WriteLine("\n"); //inclui uma quebra de linha adicional no Windows
Console.WriteLine(Enviroment.NewLine()); //inclui uma quebra de linha independente do ambiente (SO)
```

## Saída de dados

### Formatação de números decimais (ToString)

```c#
double pi = 3.14159265359;
Console.WriteLine(pi.ToString("N2")); // 3.14
Console.WriteLine(pi.ToString("F3")); // 3,141
```

```c#
using System;
using System.Globalization;

namespace ConsoleApplication2 {
    class Program {
        static void Main(string[] args) {
            double x = 10.35784;
            Console.WriteLine(x.ToString("F2", CultureInfo.InvariantCulture)); 
            // InvariantCulture faz com que seja ignorado qualquer formatação específica de país, 
            // entao o número apresentado será com '.'
        }
    }
}
```

### Concatenação

```c#
int idade = 32;
double saldo = 10.35784;
String nome = "Maria";

Console.WriteLine(nome + " tem " + idade + " anos e tem saldo igual a "+ saldo.ToString("F2", CultureInfo.InvariantCulture) + " reais");
```

### Placeholders

```c#
int idade = 32;
double saldo = 10.35784;
String nome = "Maria";
Console.WriteLine("{0} tem {1} anos e tem saldo igual a {2:F2} reais", nome, idade, saldo);
```

### Interpolação

```c#
int idade = 32;
double saldo = 10.35784;
String nome = "Maria";

Console.WriteLine($"{nome} tem {idade} anos e tem saldo igual a {saldo:F2} reais");
```

## Entrada de dados

```c#
Console.ReadLine();
```

* Lê da entrada padrão até a quebra de linha.
* Retorna os dados lidos na forma de string.

```c#
//Para ler três palavras na mesma linha, separadas por espaço, armazenando cada uma em uma variável

string s = Console.ReadLine(); // batata tomate abacaxi
string[] vet = s.Split(' '); // {"batata", "tomate", "abacaxi"}
string p1 = vet[0];  // "batata"
string p2 = vet[1];  // "tomate"
string p3 = vet[2];  // "abacaxi"
```

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

