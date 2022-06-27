# Tipos básicos de dados em C#

## Tipos do C# e do .NET

Se você usar o tipo da variável com a primeira letra maiúscula, é necessário utilizar o "using System;" no início do programa, para que esse tipo seja reconhecido.



```c#
// TIPO PRE DEFINIDO: sbyte

namespace Course
{
    class Program
    {
        static void Main (string[] args) {
            sbyte x = 100;
            Console.WriteLine(x);
        }
    }
}
```

```c#
//TIPO EQUIVALENTE DO .NET: SByte

using System;

namespace Course
{
    class Program
    {
        static void Main (string[] args) {
            SByte x = 100;
            Console.WriteLine(x);
        }
    }
}
```

## Tipos valor

Os mais utilizados:

* `int`: números inteiros, com sinal e de 4 bytes.
* `float`: números com casas decimais, com sinal e de 4 bytes.
* `double`: números com casas decimais, com sinal e de 8 bytes.
* `decimal`: números com casas decimais, com sinal e de 12 bytes. Exemplo de uso: cálculos financeiros de alta precisão
* `char`: armazena um caractere UNICODE
* `bool`: armazena valor verdadeiro ou falso

```c#
byte n1 = 126;
int n2 = 1000;
int n3 = 2147483647;

long n4 = 2147483648L; 
// para variáveis do tipo long, recomenda-se o uso do sufixo L para
// indicar explicitamente que se trata de uma variavel long

bool completo = false;

char genero = 'F'; // o tipo char aceita declaração através de aspas simples ou através do código unicode
char letra = '\u0041'; // o '\u' indica que se trata de um código unicode

float n5 = 4.5f; 
// se fosse declarado apenas "float n5 = 4.5" sem o sufixo f,
// o C# entenderia que o número 4.5 seria um double (com 8 bytes)
// por isso, é preciso o sufixo, para explicitar que se trata de um float (com 4 bytes)

double n6 = 4.5;

string nome = "Maria";

```

> **Note** Overflow é quando um cálculo extrapola o limite da sua variável. Quando isso acontece, a variável pula para o seu limite oposto.

## Tipos referência

* `string`: cadeia de caracteres unicode, IMUTAVEL
* `object`: um objeto genérico (toda classe em C# é uma subclasse de object) - GetType, Equals, GetHashCode, ToString

```c#
string nome = "Fulano da Silva";
object obj1 = "Alex Brown";
object obj2 = 4.5f;

```