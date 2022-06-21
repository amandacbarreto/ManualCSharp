# Estruturas Condicionais

## Desvio condicional com if (se)

##### [Documentação Microsoft](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/statements/selection-statements)

Caso o if tenha uma única instrução, não é necessário o uso das chaves.

```c#
if (idade>=18) Console.WriteLine("Você é maior de idade");
```

Porém, se sua condicional vai executar um bloco de instruções, o uso de chaves é obrigatório.

```c#
int idade = 25;

if (idade>=18){
    Console.WriteLine("Instrução 1");
    Console.WriteLine("Instrução 2");
    Console.WriteLine("Instrução 3");
}
```

## Else e else if

Else e else if são formas de apresentar uma alternativa à expressao testada no if.

O else if permite aninhar várias condições, enquanto o else trata todas as possibilidades restante.

```c#
if (idade>=18) Console.WriteLine("Você é maior de idade");
else if (idade==12) Console.WriteLine("Você tem 12 anos");
else Console.WriteLine("Você é menor de idade");
```

```c#
double IMC;
string entrada;
Console.WriteLine("Informe o seu IMC: ");
entrada = Console.ReadLine()!;
if (entrada.Contains("."))
{
    entrada = entrada.Replace(".", ",");
}
Double.TryParse(entrada, out IMC);

string retornarDiagnosticoDoUsuario(double _IMC)
{
    if (_IMC < 18.5)
    {
        return "Abaixo do peso.";
    }
    else if (_IMC <= 24.9)
    {
        return "Peso Normal.";
    }
    else if (_IMC <= 30)
    {
        return "Sobrepeso";
    }
    else if (_IMC <= 40)
    {
        return "Obesidade";
    }
    else
    {
        return "Obesidade grave";
    }
}


Console.WriteLine($"Seu diagnóstico é {retornarDiagnosticoDoUsuario(IMC)}");
```

## Switch case

### Switch statements

##### [Documentação Microsoft](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/statements/selection-statements)

No switch clássico, utilizamos cases para comparar uma variável/objeto em relação a uma série de valores:

```c#
switch (expression)
{
   case expression_value1:
      Statement
   break;
   case expression_value2:
      Statement
   break;
   case expression_value3:
         Statement
   break;
   default:
      Statement
   break;
}
```

```c#
// Generate a random value between 1 and 9
int caseSwitch = new Random().Next(1, 9);
switch (caseSwitch)
{
   case 1:
      Console.WriteLine("Case 1");
   break;
   case 2:
      Console.WriteLine("Case 2");
   break;
   case 3:
      Console.WriteLine("Case 3");
   break;
   default:
      Console.WriteLine("Value didn't match earlier.");
   break;
}
```

- Usando Enum em um Switch Statement

```c#
// switch..case with enum
void WeekEndOrWeekDay()
{
   switch (DateTime.Now.DayOfWeek)
   {
   case DayOfWeek.Saturday:
   case DayOfWeek.Sunday:
      Console.WriteLine("Today is Weekend");
   break;
   default:
      Console.WriteLine("Today is a work day.");
   break;
   }
}
```

- Comparações com Switch Statement

O switch statement pode fazer comparações, por exemplo:
`case < 100` avalia como verdadeiro quando o valor do switch é menor que 100

```c#
double IMC;
string entrada;
Console.WriteLine("Informe o seu IMC: ");
entrada = Console.ReadLine()!;
if (entrada.Contains("."))
{
    entrada = entrada.Replace(".", ",");
}
Double.TryParse(entrada, out IMC);

string retornarDiagnosticoDoUsuario(double _IMC)
{
    switch (_IMC)
    {
        case < 18.5:
            return "Abaixo do peso.";
        case <= 25:
            return "Peso Normal.";
        case <= 30:
            return "Sobrepeso";
        case <= 40:
            return "Obesidade";
        case > 40:
            return "Obesidade grave";
        default:
            return "Valor não faz sentido";
    }
}

Console.WriteLine($"Seu diagnóstico é {retornarDiagnosticoDoUsuario(IMC)}");
```

- Guardas de caso

Um padrão pode não ser expressivo o suficiente para especificar a condição para a avaliação da expressão. Nesse caso, você pode usar um guarda, ou seja, uma condição adicional que deve ser atendida junto com um padrão correspondente.

Por exemplo:
`case 100 when algumaCoisa > 5 && outraCoisa < 10`
avalia como verdadeiro quando **o valor do switch é exatamente 100** e **`algumaCoisa` for maior que 5** e **`outraCoisa` for menor que 10**

### Switch expressions

##### [Documentação Microsoft](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/switch-expression)

Switch expressions são similares a Switch statements, a diferença é que eles retornam um valor (Switch statements não retornam nada, só executam ações).

```c#
double IMC;
string entrada;
Console.WriteLine("Informe o seu IMC: ");
entrada = Console.ReadLine()!;
if (entrada.Contains("."))
{
    entrada = entrada.Replace(".", ",");
}
Double.TryParse(entrada, out IMC);

string retornarDiagnosticoDoUsuario(double _IMC)
{
    return _IMC switch
    {
        < 18.5 => "Anêmico",
        >= 18.5 and < 25 => "Normal",
        >= 25 and < 30 => "Sobrepeso",
        >= 30 and < 40 => "Obesidade",
        >= 40 => "Obesidade Mórbida",
        _ => "Valor não faz sentido"
    };
}


Console.WriteLine($"Seu diagnóstico é {retornarDiagnosticoDoUsuario(IMC)}");
```
