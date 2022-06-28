# C# - Informações básicas da Linguagem

## Características gerais da linguagem

### Case Sensitive

C# é uma linguagem sensível ao uso de maiúscula e minúsculas, inclusive as strings.

```c#
string nome = "Amanda";
if (nome == "amanda"){
    Console.WriteLine($"{nome} == amanda");
} else {
    Console.WriteLine($"{nome} != amanda");
}
```

Se quisermos fazer uma comparação de string ignorando maiúsculo e minúsculos, o que podemos fazer é usar um método da classe string.

```c#
string nome = "Amanda";
if (string.Equals(nome, "amanda", StringComparison.OrdinalIgnoreCase)){
    Console.WriteLine($"{nome} == amanda");
} else {
    Console.WriteLine($"{nome} != amanda");
}
```

### Tipagem estática

O compilador vai conferir se estamos utilizando a tipagem correta das variáveis em tempo de execução. Ou seja, o tipo declarado para a variável vai permanecer o mesmo durante toda a execução e não serão aceitos valores que não são compatíveis com o tipo.

> Exemplo:
> uma variável do tipo int não conseguirá receber um valor do tipo String

```c#
int numero;
numero = "Não é um numero"; //C# nao vai permitir essa atribuição
```

## Convenções para nomes

- `Camel Case`: **lastName** (parâmetros de métodos, variáveis dentro de métodos)
- `Pascal Case`: **LastName** (namespaces, classe, properties e métodos)
- `Padrão`: **\_lastName** (atributos "internos" da classe)

```c#
namespace Curso
{
    class ContaBancaria
    {
        public string Titular { get; set; }
        private double _saldo;

        public void Deposito(double quantia)
        {
            _saldo += quantia;
        }
        
        public double GetSaldo()
        {
            return _saldo;
        }
    }
}
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

- Atribuição simples;
- Chamada de métodos
- Incremento e decremento

### Operadores lógicos

Os operadores lógicos são **(&&, ||, !)** .

## Classe Console e namespace System

Namespace é uma forma de organização lógica e vai ser composto por membros.

Console é uma classe do tipo 'static'. Isso significa que a gente não pode criar um objeto do tipo Console.
No caso de uma classe do tipo 'static' todos os membros precisam ser estáticos também. Então, classes estáticas só vão conter funcionalidades dentro delas e os membros desse tipo só vão ser acessados diretamento pelo Tipo.

```c#
Console.WriteLine("Quem chamou o método WriteLine() foi a própria classe Console");
```

## Membros de instância

Quando nós temos um objeto do tipo string ou int, por exemeplo, nós podemos acessar os membros dela através de um ponto (.). Dessa forma serão vistos os membros de instância (e os de extensão também), e não os membros estáticos (justamente porque as classes String e Int não são do tipo 'static').

Contudo, classes não-estáticas podem ter membros estáticos ou não.

## Conversão de tipos de variáveis

Todo valor obtido através do método Console.ReadLine() retorna um inteiro, sendo necessária a conversão do valor para o tipo que se deseja trabalhar.

### Conversão de string para int

#### **Método int.Parse("string")**

```c#
int idade = int.Parse(Console.ReadLine());
```

## Expressões booleanas

São expressões que retornam um valor booleano (do tipo bool, que podem sem true ou false). É o caso das expressões que vão dentro do if.

```c#
int idade = 25;

if (idade>=18){
    Console.WriteLine("Você é maior de idade");
}
```

## Arrays (vetores)

Permite criar um conjunto de objetos do mesmo tipo.

```c#
//os objetos no inicializador são separados por vírgulas
string[] nomes1 = {"Ana", "Bruno", "Carla"};

// o new basicamente utiliza um método construtorno tipo. Os parenteses geralmente utilizados em chamadas de métodos são dispensados no caso de inicialização de vetores
string[] nomes2 = new String [3];
nomes2[0] = "Ana";
nomes2[1] = "Bruno";
nomes2[2] = "Carla";
```

**OBSERVAÇÃO**: Quando uma instância de array é criada, é preciso especificar qual o tamanho dela, ou seja, quantos espaços ela vai ter. Ou seja, **não é possível redimensionar um array.**

Por isso, muitas vezes vale mais a pena utilizar uma lista, principalmente quando se quer adicionar elementos à coleção de dados.

### Formas de acessar os elementos de um array

**Iteração** é o nome dado para cada execução do loop.

- Laço **FOR**

```c#
string[] nomes1 = {"Ana", "Bruno", "Carla"};
for (int i = 0; i < nomes1.length; i++){
    Console.WriteLine(nomes[i]);
}
```

- Laço **FOREACH**

```c#
string[] nomes1 = {"Ana", "Bruno", "Carla"};
foreach (string nome in nomes1){
    Console.WriteLine(nome);
}
```

## Métodos

Em C# todo método precisa ter um tipo de retorno.

### void

Corresponde a um retorno vazio.

```c#
public void EscreveOi()
{
    Console.WriteLine("Oi"); // e não retorna nada
}
```

### int

Métodos desse tipo obrigatoriamente retornam um valor do tipo int.

```c#
public int DescobreIdadeUsuario()
{
    Console.WriteLine("Qual a sua idade?");
    int idade = int.Parse(Console.ReadLine());
    return idade;
}
```

O mesmo princípio vale para os demais tipos de variáveis, inclusive vetores, lista e até mesmo objetos de classes criadas pelo próprio desenvolvedor.

## Operações com String

```c#
string nome = "Amanda";
Console.WriteLine($"A string nome tem {nome.Length()} letras.");
```

Outros métodos relevantes:

- **Contains**
- **StartsWith**
- **EndsWith**
- **IndexOf** -> uma string é como um array de char. se for pesquisado algo que não existe, será retornado o valor '-1'
- **IsNullOrEmpty**
- **IsNullOrWhiteSpace** -> preferível ao comando anterior, pois também retorna verdadeiro caso a string seja vazia
- **Join**

```c#
string nome = "Amanda";
Console.Contains('F');
Console.Contains("Fa"); //a partir de 2 caracteres, é obrigatório o uso das aspas duplas
```

## Operações com número

Para acessar os membros associados a numeros é necessário colocar o numero em parenteses primeiro. Caso contrário, será entendido como um ponto flutuante.

```c#
(10).
```

Outros métodos relevantes:

- **TryParse** -> tenta transformar a string no tipo indicado, retorna true ou false para a operação e caso seja true, já é possível indicar a variavel que receberá o resultado da conversão.

```c#
if(int.TryParse("42", out int x))
{
    Console.WriteLine(x);
} else {
    Console.WriteLine("Não foi possível converter");
}
```

## Tipos de referência e tipos de valor

Todo tipo que é uma classe é um **tipo de referência**.

Uma string, por exemplo, é um tipo de referência.

**Variáveis do tipo de valor** elas vão conter diretamente o valor atribuído a elas.

Tipos de valor geralmente são tipos bem simples que normalmente só armazena informações básicas como o número, por exemplo.

A grande diferença é que com o tipo de referência a variável é usada para manipular o objeto na memória, enquanto a variável de tipo de valor já tem o valor em si.

**Exemplo de variavel do tipo referencia:**

```c#
class Test{
    public int x;
}

class Program{
    static void Main(){
        Test t = new Test();
        t.x = 10;
        Test t2 = t; //não estamos criando um novo objeto do tipo Test, estamos apenas criando UMA CÓPIA pro objeto anterior (t)
        t2.x=20; //altera o valor de x no objeto t também, pois ambos os objetos estão apontando pro mesmo endereço de memória.
        Console.WriteLine(t.x); //imprime 20
    }
}
```

Observação: apesar de variaveis do tipo string serem do tipo referência, nesse quesito elas vão se comportar como variaveis do tipo valor.

```c#
string palavra1 = "Palavra 1";
string palavra2 = palavra1;
palavra2 = "Palavra 2";

Console.WriteLine(palavra1); //não teve o valor alterado
Console.WriteLine(palavra2);
```

## Igualdade de valores e referencias

Ao comparar dois objetos do tipo referência, só teremos um retorno true se o endereço de memória dos dois objetos for o mesmo.

## Tipos anuláveis

Para indicar que uma variavel do tipo valor possa receber uma valor null, indique com '?' após o tipo.

```c#
int? x = 10;
x = null;

Console.WriteLine(x.HasValue);
Console.WriteLine(x.Value);
Console.WriteLine(x.GetValueOrDefault);
Console.WriteLine(x.GetValueOrDefault(1));//se for nula, retorna 1
```

## Tipos de referência anuláveis

Essa funcionalidade foi criada porque um dos erros mais comuns em aplicações C# é exceção de referência nula (NullReferenceException), que acontece quando a aplicação tenta usar um membro de Instância de um tipo de referência que é nulo, ou seja, não tem nenhuma Instância.

## Tratamento de exceção

```c#
string s = null;

try //podemos lançar exceções
{
    Console.WriteLine(s.Length);
}
catch (System.NullReferenceException exception) // definimos o que acontece se uma exceção for lançada
{
    Console.WriteLine($"Erro de referência nula. {exception.Message}{exception.StackTrace}");
}
catch (Exception exception) //pega todas as exceções. Se for usar em conjunto com outras exceções mais específicas, esta deve vir por ultimo.
{
    Console.WriteLine("Erro");
}
/*
catch // equivalente ao catch anterior "catch (Exception exception)"
{
    Console.WriteLine("Erro");
}
*/
```

## Lançamento de exceção

```c#
string name = "   ";
if(string.IsNullOrWhiteSpace(name)){
    throw new Exception ("Nome inválido");
}
```

> **Note**
>
> Quando tentamos fazer uma divisão por zero, é necessário lançar essa exceção antes de tentar fazer a conta, pois a atual versao do C# permite a divisao por 0, com o resultado tendendo ao infinito (representado pelo número 8).

```c#
double dividirValor(double valor)
{
    if (valor == 0)
    {
        throw new DivideByZeroException("CodError001 - Divisão por 0 não é possível.");
    }
    else
    {
        double resultadoDivisao = pegarResultadoDaUltimaOperacaoMatematica() / valor;
        definirResultadoDaUltimaOperacaoMatematica(resultadoDivisao);
        return resultadoDivisao;
    }
}
```

## Parâmetros X Argumentos

Quando a gente **declara** um construtor ou um método que recebe alguma informação, a gente está declarando **parâmetros**.

Quando a gente está **executando** um Construtor ou um método que precisa de informações, a gente tá passando **argumentos**.

```c#
string name = "   ";
if(string.IsNullOrWhiteSpace(name)){
    throw new ArgumentException ("Nome inválido", "name");
}
```

## Classes e campos (fields)

Uma classe é basicamente a definição de um tipo, onde vamos definir um conjunto de atributos (propriedades) e comportamentos (métodos) que objetos desse tipo vão ter.

Utilizamos a palavra chave aqui 'class' seguida pelo identificador (nome da classe) e dentro das chaves criamos um bloco de código, que é o escopo dessa classe. Tudo o que estiver dentro das chaves vai ser um membro dessa classe.

Quanto aos atributos, a maneira mais fácil para a gente permitir que a informação seja usada em objetos desse tipo é através de Campos (ou Fields em inglês).

A declaração de um campo é bem simples e é bem similar ao de uma variável. Basta especificar o tipo e o nome do campo identificador.

#### Acessibilidade de membros e encapsulamento

Antes do tipo do campo, podemos definir a acessibilidade dele (public ou private). Por padrão (caso não seja definido explicitamente o nivel de acesso), a acessibilidade é privada, ou seja, só é possível acessar os tipos dentro da própria classe. Para permitir que o programa acesse àquela propriedade, é preciso definir o campo como público.

O uso de campos públicos não é recomendado em nenhum tipo de aplicação séria porque os tipos não têm controle sobre os valores atribuídos para esses campos.
O ideal seria encapsularmos os comportamentos no tipo em si, o que seria uma boa prática de orientações a objeto.

```c#
class Program{
    static void Main(){
        BankAccount account1 = new BankAccount();
        account1.name = "Amanda";
        account1.balance = 100;
        BankAccount account2 = new BankAccount();
    }
}

class BankAccount{
    public string name;
    public decimal balance;
}
```

## Construtores

Para inicializar objetos, podemos declarar um Construtor, que nada mais é do que um comportamento que vai ser executado quando a gente cria uma instância desse tipo.

Os campos voltam a ser Private, pois queremos que o acesso a eles seja feito somente dentro da classe.

Criamos um Construtor que seja acessível a qualquer um, então a gente vai definir a sensibilidade dele como pública.

Como identificador, vamos utilizar o nome do tipo em si (nesse exemplo, 'BankAccount') e entre parenteses, vamos definir quais serão os parâmetros obrigatórios desse construtor.

A definição de parâmetros é como declaração de variáveis com os parâmetros separados por vírgula.

```c#
class Program{
    static void Main(){
        BankAccount account1 = new BankAccount("Ana", 100);
        BankAccount account2 = new BankAccount("Bruno",250);
    }
}

class BankAccount{
    private string name;
    private decimal balance;

    public BankAccount (string name, decimal balance){

        if(string.IsNullOrWhiteSpace(name)){
            throw new Exception ("Nome inválido"); //sempre que uma exceção é lançada, o código restante não é executado. Ou seja, vai parar a execução do construtor
        }
        if (balance < 0){
            throw New Exception ("Saldo não pode ser negativo");
        }
        this.name = name;
        this.balance = balance;
        // a palavra 'this' é usada para indicar que a variável a qual o valor será atribuido é a variavel global da classe e não a variável que foi passada como parametro da função. Seu uso é necessário pois optamos por usar o mesmo nome de variável.
    }
}
```

## Criando um método

Precisamos definir o método como público para que ele seja acessível pelos objetos no programa principal.

Na criação do método definimos

- acesibilidade
- retorno
- identificador do método
- parametros (não obrigatório)

```c#
class Program{
    static void Main(){
        BankAccount account1 = new BankAccount("Ana", 100);
        BankAccount account2 = new BankAccount("Bruno",250);
        account1.Deposit(-100);
        account2.Deposit(150);

    }
}

class BankAccount{
    private string name;
    private decimal balance;

    public BankAccount (string name, decimal balance){
    /*
    código suprimido, consultar exemplos anteriores.
    */
    }

    public void Deposit (decimal amount){
        if(amount <= 0){
            return;
        }
        balance += amount;
    }
}
```

## Criando um método que retorna um objeto

```c#
class Program{
    static void Main(){
        BankAccount account1 = new BankAccount("Ana", 100);
        BankAccount account2 = new BankAccount("Bruno",250);
        account1.Deposit(-100);
        account2.Deposit(150);
        Console.WriteLine(account2.GetBalance());

    }
}

class BankAccount{
    private string name;
    private decimal balance;

    public BankAccount (string name, decimal balance){
    //código suprimido, consultar exemplos anteriores.
    }

    public void Deposit (decimal amount){
    //código suprimido, consultar exemplos anteriores.
    }

    public decimal GetBalance (){
        return balance;
    }
}
```

## Propriedades (properties)

Propriedades são parecidas com Campos, mas com a vantagem de que a gente vai ter controle sobre a leitura e escrita delas.

```c#
class Program{
    static void Main(){
        BankAccount account1 = new BankAccount("Ana", 100);
        BankAccount account2 = new BankAccount("Bruno",250);
        account1.Deposit(-100);
        account2.Deposit(150);
        Console.WriteLine(account2.Balance());

    }
}

class BankAccount{
    private string name;
    private decimal balance;

    public decimal Balance {
        get { return balance; }
        private set {
            if (value <= 0){
                return;
            {
            balance = value;
        }
    }

    public BankAccount (string name, decimal balance){
    //código suprimido, consultar exemplos anteriores.
    }

    public void Deposit (decimal amount){
    //código suprimido, consultar exemplos anteriores.
    }
}
```

## Operador nameof

Evita erros de compilação em caso de troca de nome de variável do tipo string.

## Interfaces

Além de classe, existe uma outra declaração de tipo de referência bem importante, que é a interface.
Uma interface é basicamente uma declaração de um contrato público, ou seja, quem quer implementar esse contrato precisa implementar todos os membros declarados na interface.

Uma interface é um tipo não concreto, ou seja a gente não pode criar instâncias dele. Normalmente quem implementa a interface é quem vai ser o tipo concreto (no caso do Exemplo, a classe BankAccount).

- Por convenção, nomes de interfaces começam com a letra I maiuscula (Ex: ILogger).
- Por padrão, todos os membros de interface são públicos.
- Por padrão, métodos de interface não tem corpo.

```c#
class Program{
    static void Main(){
        ConsoleLogger logger = new ConsoleLogger();
        BankAccount account1 = new BankAccount("Ana", 100), logger;

    }
}

class ConsoleLogger : ILogger
{
    public void Log (string message){
        Console.WriteLine(message);
    }
}

interface ILogger
{
    void Log (string message);
}

class BankAccount{
    private string name;
    private decimal balance;

    public decimal Balance {
        get { return balance; }
        private set {
            if (value <= 0){
                return;
            {
            balance = value;
        }
    }

    public BankAccount (string name, decimal balance, ILogger logger){
    //código suprimido, consultar exemplos anteriores.
        this.logger = logger;
    }

    public void Deposit (decimal amount){
        if(amount <= 0){
            logger.Log($"Não é possível depositar {amount} na conta de {name} ");
            return;
        }
        balance += amount;
    }
}
```

## Escrevendo e salvando em um arquivo

```c#
class Program{
    static void Main(){
        ILogger logger = new FileLogger("mylog.txt");
        BankAccount account1 = new BankAccount("Ana", 100), logger;

    }
}

///// CONCEITO APRESENTADO
class FileLogger : ILogger
{
    private readonly string filePath;

    public FileLogger (string filePath)
    {
        this.filePath = filePath;
    }

    public void Log (string message){
        File.AppendAllText("log.txt", $"{message}{Enviroment.NewLine}");
    }
}
/////

interface ILogger
{
    void Log (string message);
}

class BankAccount{
    private string name;
    private decimal balance;

    public decimal Balance {
        get { return balance; }
        private set {
            if (value <= 0){
                return;
            {
            balance = value;
        }
    }

    public BankAccount (string name, decimal balance, ILogger logger){
    //código suprimido, consultar exemplos anteriores.
        this.logger = logger;
    }

    public void Deposit (decimal amount){
        if(amount <= 0){
            logger.Log($"Não é possível depositar {amount} na conta de {name} ");
            return;
        }
        balance += amount;
    }
}
```

## Generics

Um tipo genérico vai possuir atributos e comportamentos sem especificar nenhum tipo de dados em particular.

## Criando um tipo genérico

```c#
class Program{
    static void Main(){
        DataStore <int> store = new DataStore<int>();
        store.Value = 42;
        Console.WriteLine(store.Value);


        DataStore <string> storeStrings = new DataStore<string>();
        storeStrings = "Texto";
        Console.WriteLine(storeStrings.Value.Length);
    }
}

class DataStore<T>
{
    public T Value { get; set; }
}
```

## Listas

Um dos tipos genéricos mais famoso do C# é a lista.

```c#
class Program{
    static void Main(){
        ILogger logger = new FileLogger("mylog.txt");
        BankAccount account1 = new BankAccount("Ana", 100), logger;
        BankAccount account2 = new BankAccount("Bruno", 250), logger;

        List<BankAccount> accounts = new List<BankAccount>() ;

        /* outra forma de inicializar listas

        List <BankAccount> accounts = new List<BankAccount> ()
        {
            account1,
            account2
        }
        */

        accounts.Add(account1);
        accounts.Add(account2);

        foreach (BankAccount account in accounts) {
            Console.WriteLine(account.Balance);
        }

        account.Remove(account1);

        List <int> numbers = new List <int> {1,2,4,8,10};

        foreach (int number in numbers) {
            Console.WriteLine(number);
        }

    }
}

```

## Declaração de variáveis com tipo implícito

Qualquer variavel pode ser declarada com o tipo var. Dessa forma, passamos ao compilador a tarefa de definir o tipo de variável de acordo com o tipo de expressão da direita da atribuição.

```c#
class Program{
    static void Main(){
        var store = new DataStore<int>();
        var account2 = new BankAccount("Bruno", 250), logger;
        var nome = "Ana";
    }
}

```

OBSERVAÇÃO: a implementação aqui é diferente do JavaScript, pois a tipagem continua sendo forte. Ou seja, se a variavel account2 for do tipo BankAccount, assim ela permanecerá, não sendo possível atribuir implicitamente um tipo diferente à variável.

## Delegates

Um delegate ou delegado nada mais é do que um objeto que sabe executar métodos.

É uma maneira da gente armazenar métodos em variáveis ou até passar métodos como argumento.
Delegate é um tipo que a gente declara para definir a
espécie de método que as instâncias de delegate podem executar.

```c#
class Program{
    static void Main(){
        Calculate calculate = new Calculate (Sum);
        int result = calculate (10,20);
        Console.WriteLine(result);
    }

    static int Sum (int a, int b)
    {
        return a + b;
    }
}

delegate int Calculate (int x, int y);
```

Como delegates são tipos nós podemos criar métodos que tem parâmetros desse tipo.

```c#
class Program{
    static void Main(){
        Calculate calculate = new Calculate (Sum);
        Run(Sum);
        Run(Multiply);
    }

    static void Run (Calculate calc)
    {
        Console.WriteLine(calc(20,30));
    }
    static int Sum (int a, int b)
    {
        return a + b;
    }
    static int Multiply (int a, int b)
    {
        return a * b;
    }
}

delegate int Calculate (int x, int y);
```

## Métodos anônimos

```c#
class Program{
    static void Main(){
        var multiply = delegate(multiply(10,5));
        Console.WriteLine(multiply(10,5));
    }
}

delegate int Calculate (int x, int y);
```

## Func e Action

Tanto o Func quanto o Action podem receber até 16 parâmetros e a vantagem é que não precisamos ficar declarando nosso próprio delegate.

```c#
class Program{
    static void Main(){
        var multiply = delegate(multiply(10,5));
        Run(multiply);

        Action<string> test = delegate (string name) {Console.WriteLine($"Olá {nome}");};
        test("John Wick");
    }

    static void Run (Func<int, int, int> calc)
    {
        Console.WriteLine(calc(20,30));
    }
    static int Sum (int a, int b)
    {
        return a + b;
    }
    static int Multiply (int a, int b)
    {
        return a * b;
    }
}

delegate int Calculate (int x, int y);
```

A grande diferença entre Func e Action é que:

- Func sempre vai retornar alguma coisa, que vai ser sempre o ultimo parametro de tipo. Ele pode até não receber nada, mas sempre vai retornar algo.

```c#
class Program{
    static void Main(){
        Func<decimal> test2 = delegate () {return 4.2m;};
        //como o Func nao vai receber nada, os parametros poderiam ser omitidos
        // Func<decimal> test2 = delegate {return 4.2m;};


        // por padrão, o C# considera numeros fracionados sendo do tipo flutuante (float), não permitindo a conversão implícita para decimal.
        // Como o nosso retorno foi definido como decimal, é preciso utilizar o sufixo 'm' ou 'M' no numero para indicar que se trata de um número do tipo decimal

        Console.WriteLine(test2);

        Func <string, bool> checkName = delegate (string name) { return name == "Ana"; };
        Console.WriteLine(checkName("Mariana"));
    }
}

delegate int Calculate (int x, int y);
```

## Expressões Lambda

Uma coisa a fazer para simplificar esse código é, ao invés de utilizar delegates, usar expressões lambda.
Para transformar um delegate em uma expressão lambda a gente só precisa remover a palavra-chave delegate e após os parentes a gente utiliza o operador lambda (`=>`).

Quando o corpo da expressão Lambda só possui uma instrução, nós podemos até remover as chaves e o retorno.

```c#
class Program{
    static void Main(){
        var multiply = (int x, int y) => x * y;
        Run(multiply);

        var test = (string name) => {Console.WriteLine($"Olá {nome}");};
        test("John Wick");

        Func<decimal> test2 = () => 4.2m;
        Console.WriteLine(test2());

        Func<string, bool> checkName = (name) => name == "Ana";
        Console.WriteLine(checkName("Mariana"));
    }
}
```

## Métodos de extensão

Outra funcionalidade bem importante no C# é a possibilidade de estender qualquer tipo criando métodos de extensão. Isso é útil quando agente quer estender tipos de valor ou Tipo selados, que tipos que a gente não tem controle sobre eles.

Métodos de extensão existem graças aos métodos estáticos que são executadas através do tipo diretamente e não através de uma Instância de objeto.

```c#
class Program{
    static void Main(){
        WriteLine("Testando", ConsoleColor.Yellow);
    }

    static void WriteLine (string text, ConsoleColor color)
    {
        Console.ForegroundColor = color;
        Console.WriteLine(text);
        Console.ResetColor();
    }
}
```

```c#
static class Program{
    static void Main(){
        "Testando".WriteLine(ConsoleColor.Yellow);
    }

    static void WriteLine (this string text, ConsoleColor color)
    {
        Console.ForegroundColor = color;
        Console.WriteLine(text);
        Console.ResetColor();
    }
}
```

```c#
class Program{
    static void Main(){
        "Testando".WriteLine(ConsoleColor.Yellow);
    }
}

static class Extensions
{
    public static void WriteLine (this string text, ConsoleColor color)
    {
        Console.ForegroundColor = color;
        Console.WriteLine(text);
        Console.ResetColor();
    }
}
```

## Declarando namespaces

## Implicit usings

## Importando um namespace com a diretiva using

[Explicação Fredi](https://www.youtube.com/watch?v=oTivhgjbhIg&t=10492s)

## Serialização e desserialização JSON

[Explicação Fredi](https://www.youtube.com/watch?v=oTivhgjbhIg&t=10616s)

Serialização é um processo que permite que objetos sejam transformados em formato que pode ser armazenado ou transferido com o propósito de Reconstruir objetos a partir desse formato.

JSON é o formato mais popular hoje em dia e é um formato de fácil leitura tanto para computadores quanto para seres humanos.
O .NET possui um tipo para serializar JSON, que é o namespace `System.Text.JSON.`

```c#

using System.Text.Json;
using Bank;

class Program{
    static void Main(){
        BankAccount account = new BankAccount("Fredi", 100);

        // SERIALIZAÇÃO
        string json = JsonSerializer.Serialize(account);
        Console.WriteLine(json);

        // DESSERIALIZAÇÃO
        BankAccount account1 = JsonSerializer.Deserialize<BankAccount>(json);
        Console.WriteLine(account1.Name);
        Console.WriteLine(account1.Balance);
    }
}

namespace Bank
{
    // código suprimido
}
```

## Múltiplos construtores

[Explicação Fredi](https://www.youtube.com/watch?v=oTivhgjbhIg&t=10937s)

## Attributes (anotações de código)

[Explicação Fredi](https://www.youtube.com/watch?v=oTivhgjbhIg&t=11052s)

## LINQ - Language Integrated Query

[Explicação Fredi](https://www.youtube.com/watch?v=oTivhgjbhIg&t=11200s)

LINQ, Language Integrated Query (ou consulta integrada a linguagem, em português) é basicamente um conjunto de tecnologias que permite que a gente realize consultas em coleções, documentos XML e até em banco de dados usando somente códigos C#.

```c#

class Program{
    static void Main(){
        int[] numbers = { 1, 4, 10, 42};

        // QUERY SINTAX (Sintaxe de consulta)
        var query = from number in numbers
                    where number < 10
                    select number;

        // METHOD SYNTAX (Sintaxe de método com lambda)
        var query2 = numbers.Where(number => number < 10);
    }
}

```

## Classe Enumerable

[Explicação Fredi](https://www.youtube.com/watch?v=oTivhgjbhIg&t=11536s)

## Atenção com execução adiada

[Explicação Fredi](https://www.youtube.com/watch?v=oTivhgjbhIg&t=11641s)

## Materializando uma consulta LINQ

[Explicação Fredi](https://www.youtube.com/watch?v=oTivhgjbhIg&t=11795s)

- ToList()
- First()
- FirstOrDefault()
- OrderBy()
- OrderByDescending()
- GroupBy()
- Select()

## Tipos anônimos

[Explicação Fredi](https://www.youtube.com/watch?v=oTivhgjbhIg&t=11795s)

## Enumerable.Empty e Enumerable.Range

[Explicação Fredi](https://www.youtube.com/watch?v=oTivhgjbhIg&t=12789s)

## Usando Range pra retornar letras do alfabeto

[Explicação Fredi](https://www.youtube.com/watch?v=oTivhgjbhIg&t=13065s)

## Programação assíncrona

[Explicação Fredi](https://www.youtube.com/watch?v=oTivhgjbhIg&t=13163s)

## Diferença entre operação sincrona e assincrona

[Explicação Fredi](https://www.youtube.com/watch?v=oTivhgjbhIg&t=13304s)

## Executando código de forma assincrona

[Explicação Fredi](https://www.youtube.com/watch?v=oTivhgjbhIg&t=13436s)

## async e await

[Explicação Fredi](https://www.youtube.com/watch?v=oTivhgjbhIg&t=13644s)

## Retornando objeto em uma Task

[Explicação Fredi](https://www.youtube.com/watch?v=oTivhgjbhIg&t=13812s)

## Gerando o executável da aplicação

[Explicação Fredi](https://www.youtube.com/watch?v=oTivhgjbhIg&t=13947s)

console

```
dotnet publish
```

## Executando em outro computador com o Runtime

[Explicação Fredi](https://www.youtube.com/watch?v=oTivhgjbhIg&t=14015s)

## Próximos passos (Importante)

[Explicação Fredi](https://www.youtube.com/watch?v=oTivhgjbhIg&t=14118s)
