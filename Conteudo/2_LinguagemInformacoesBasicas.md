# C# - Informações básicas da Linguagem

## Características gerais da linguagem

### Tipagem estática
O compilador vai conferir se estamos utilizando a tipagem correta das variáveis em tempo de execução. Ou seja, o tipo declarado para a variável vai permanecer o mesmo durante toda a execução e não serão aceitos valores que não são compatíveis com o tipo.
> Exemplo:
> uma variável do tipo int não conseguirá receber um valor do tipo String
```c#
int numero;
numero = "Não é um numero"; //C# nao vai permitir essa atribuição
```

## Tipos mais comuns de variáveis
```c#
bool varBool = true;
varBool = false;

char varChar = 'a';
varChar = '&';

byte varByte;
int varInt;
long varLong;
float varFloat;
double varDouble;
decimal varDecimal;
string varString = "Essa é uma variável do tipo String";
```

## Statements (instrução)
Instruções são linhas de código que fazem alguma coisa, mas que não retornam nada.

Geralmente utilizada para declaração de variáveis.
```c#
decimal varDecimal;
```

## Expressions (expressões)
São linhas de códigos que serão avaliadas e vão retornar um valor.
Toda espressão tem um tipo.
```c#
Console.WriteLine("Hello, World!");
```

O exemplo abaixo é tanto uma instrução quanto uma expressão.
```c#
string varString = "Essa é uma variável do tipo String";
```

Coisas que podem ser instrução e expressão ao mesmo tempo:
* Atribuição simples;
* Chamada de métodos
* Incremento e decremento

## Operadores e operandos

Os operadores __(=, ++, --, +=, -=, ?:)__ realizam a operação com os operandos (variáveis e valores).

Operador ternário: 

```c#
int i = 43;
int i2 = (i==42 ? 10 : 20);
```










Criar uma aplicação .NET usando o template de uma aplicação console
```
dotnet new console
```

Devido à extensão instalada, o VS Code sugere a inclusão de alguns assets para construção e debug (aceite!)

![Adicionar extensão](Conteudo\img\extensoes_csharp.png)

Caso a opção não apareça, aperte "Ctrl+Shift+P" e selecione a seguinte opção

![Assets C#](Conteudo\img\assets_csharp.png)


Para rodar a aplicação
```
dotnet run
```

