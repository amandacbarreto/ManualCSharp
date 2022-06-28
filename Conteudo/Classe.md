# Classes

Classe é um tipo estruturado que pode conter (membros):

- `Atributos` (dados / campos)
- `Métodos` (funções / operações)

![Exemplo de classe](./img//classe_estrutura(curso%20Nelio%20Alves).png)
###### [Fonte: Curso "C# COMPLETO Programação Orientada a Objetos + Projetos"](https://www.udemy.com/course/programacao-orientada-a-objetos-csharp/)

Uma classe é basicamente a definição de um tipo, onde vamos definir um conjunto de atributos (propriedades) e comportamentos (métodos) que objetos desse tipo vão ter.

A classe é uma referência para um objeto composto.

Utilizamos a palavra chave aqui 'class' seguida pelo identificador (nome da classe) e dentro das chaves criamos um bloco de código, que é o escopo dessa classe. Tudo o que estiver dentro das chaves vai ser um membro dessa classe.

Quanto aos atributos, a maneira mais fácil para a gente permitir que a informação seja usada em objetos desse tipo é através de Campos (ou Fields em inglês).

A declaração de um campo é bem simples e é bem similar ao de uma variável. Basta especificar o tipo e o nome do campo identificador.

A classe também pode prover muitos outros recursos, tais como:
• Construtores
• Sobrecarga
• Encapsulamento
• Herança
• Polimorfismo

## Instanciação

- `Classe` é a definição do tipo
- `Objetos` são instâncias da classe

```c#
namespace Course {
    class Triangulo {
        public double A;
        public double B;
        public double C;
    }

    class Program {
        static void Main(string[] args) {
            Triangulo x;
            x = new Triangulo(); //instanciação de um objeto x do tipo (Classe) triângulo
            Triangulo y = new Triangulo(); //instanciação de um objeto y do tipo (Classe) triângulo
        }
    }
}
```

## Acessibilidade de membros e encapsulamento

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

## Encapsulamento

Agrupamento das variáveis e funções em uma classe.
Podemos dizer que separamos em `atributos` (variáveis) e `métodos` (funções).

```c#
public class Lampada
{
    // Propriedade (variáveis)
    public string Fabricante = String.Empty;
    private int Voltagem;

    // Métodos (funções)
    public virtual bool LigarOuDesligar()
    {

    }
}
```

`public` propriedade ou método público, acessível fora dda classe.
`private` propriedade ou método privado, escopo local, acessível apenas dentro da classe.

## Abstração

Abstraimos atributos e métodos através de controladores de acesso, separando os recursosque poderão ser acessados externamente.

```c#
public class Lampada
{
    // Propriedade (variáveis)
    public string Fabricante = { get; set; };

    // Definimos propriedades que serão Abstraídas/Privados de acesso.
    private int Voltagem = 110;

    // Definimos método que serão Abstraídos/Privados de acesso.
    private void GerarRelatorioDeUso() { }

    // Método Acessível/Público - Funções
    public virtual bool LigarOuDesligar()
    {
        return true;
    }
}
```

> **Note**
>
> Quando não especificamos o controlador de acesso, entende-se que o acesso é do tipo `private`. Ou seja, caso precisemos que o acesso a(o) propriedade/método seja público, precisamos declarar isso para o programa através do controlador `public`.

## Herança

É possível herdar as características (atributos e métodos) de outro objeto e continuar a implementação de novos recursos em um novo escopo.

```c#
class Lampada
{
    public string Fabricante = { get; set; };
    private int Voltagem = 110;
    private void GerarRelatorioDeUso() { }
    public virtual bool LigarOuDesligar()  { }
}

// Herdamos os atributos e métodos da classe Lampada.
class Hue : Lampada {
    public void VariarIluminosidade() { }
}

```

## Polimorfismo

A partir de uma herança, podemos sobrescrever da classe herdada, sobrescrevendo alguns recursos herdados, ou seja, gerando novas formas de realizar a tarefa.

```c#
class Lampada
{
    public string Fabricante = { get; set; };
    private int Voltagem = 110;
    private void GerarRelatorioDeUso() { }
    public virtual bool LigarOuDesligar() { }
}

class Hue : Lampada
{
    public void VariarIluminosidade() { }

    // Sobrescrevemos a funcionalidade de ligar/Desligar.
    public override bool LigarOuDesligar() { }
}
```

## Controladores de acesso

`Modificador de Classe` define a visibilidade/comportamento da Classe.

`Controlador de Acesso` especifica em que momento um membro (atributos e métodos) da Classe poderá ser acessível.

```c#
[Modificador Classe] class Lampada
{

    [Controlador de Acesso] string Fabricante = { get; set; };

    [Controlador de Acesso] virtual bool LigarOuDesligar()
    {

    }
}
```

### Modificadores de visibilidade/comportamento da classe

- **`public`**: sem restrições de visibilidade. Objetos dessa classe poderão acessar todos os membros (atributos e métodos) que também forem do tipo público.

- **`abstract`**: classe-base para outras classes, não podem ser instânciadas. Métodos do tipo abstrato não podem ser definidos na própria classe abstrata, podem apenas ser declarados e posteriormente reescritos nas classes que herdam seus membros.

```c#
namespace Aula11
{
    public abstract class Conversao
    {
        abstract public double cotacaoDaMoedaHoje { get; set; }
        abstract public string moeda { get; set; }
        abstract public string simboloMoeda { get; set; }
        public abstract void ConversaoCompra(double valorCompra);
        public abstract void VerificarCompra(double valorCompra);
    }
}
```

- **`sealed`**: classe não permite herança.

- **`static`**: Classe pode ser utilizanda sem a necessidade de instânciá-la. Um exemplo de classe estática é a classe Console, que permite a chamada de seus métodos diretamente pelo nome da classe, sem ser preciso instanciar um objeto do tipo console antes.

```c#
Console.WriteLine("Não foi preciso declarar um objeto do tipo Console para utilizarmos esse método.");
```

### Lista de controladores de acesso dos membros da classe

- **`public`**: Sem restrição de acesso.

- **`private`**: Só podem ser acessados pela própria classe.

- **`protected`**: Podem ser acessados pela própria classe e por classes derivadas/herdeiras.

- **`virtual`**: permite que o método seja redefinido por classes derivadas/herdeiras. Ou seja, diferente da classe do tipo `abstract` que só permite a declaração de métodos, sem permitir a criação de um escopo, os métodos do tipo `virtual` permitem que além de declarado, esse método já tenha algum código, o qual **poderá ser reescrito** (mas não é obrigatório) nas classes derivadas, através do uso de `override`. Inclusive, é possível criar métodos virtuais dentro de uma classe abstrata.

```c#

// Nesse exemplo, uma classe do tipo abstrata (Conversao),
// possui propriedades abstratas (referentes às informações das moedas)
// e métodos virtuais que serão aproveitados completamente pelas classes derivadas.
// Assim, nas classes derivadas (ConversaoDolar e ConversaoEuro) só será necessário
// atualizar as informações referentes às moedas.

namespace Refatoracao_Aula07
{
    internal abstract class Conversao
    {
        abstract public double cotacaoDaMoedaHoje { get; set; }
        abstract public string simboloMoeda { get; set; }
        public double valorConvertido { get; set; }

        public virtual double ConversaoCompra(double valorCompra)
        {
            return valorCompra / cotacaoDaMoedaHoje;
        }
        public virtual void VerificarCompra(double valorCompra)
        {
            valorConvertido = ConversaoCompra(valorCompra);

            string mensagem;
            mensagem = $"Você pode comprar {simboloMoeda}{valorConvertido.ToString("F2")}";
            Console.WriteLine(mensagem + Environment.NewLine);
        }
    }

    // CLASSE DERIVADA
    internal class ConversaoDolar: Conversao
    {

        public override double cotacaoDaMoedaHoje
        {
            get { return 5.20; }
            set { }
        }
        public override string simboloMoeda
        {
            get { return "$"; }
            set { }
        }

    }

    // CLASSE DERIVADA
    internal class ConversaoEuro: Conversao
    {
        public override double cotacaoDaMoedaHoje
        {
            get { return 5.46; }
            set { }
        }
        public override string simboloMoeda
        {
            get { return "EUR"; }
            set { }
        }

    }
}
```

- **`static`**: Permite que os membros da classe possam ser acessados sem a necessidade de instanciar a classe.

```c#
namespace aula11_controladores_de_acesso
{

    class Cotar
    {
        // Variável
        private string nome;
        public string Nome { get; set; }
        private const int ANO_ATUAL = 2022;

        public static int retornarDataDeNascimento(int idadeDoUsuario)
        {
            int dataNascimento = ANO_ATUAL - idadeDoUsuario;
            return dataNascimento;
        }
    }

    internal class Program
    {
        static void Main(string[] args)
        {

            Cotar cotacao = new Cotar();

            // Utilize a mensagem a seguir como base do retorno esperado:
            // Olá João, você nasceu em XXXX.
            Console.WriteLine("Digite seu nome:");
            string nomeDoUsuario = Console.ReadLine();

            cotacao.Nome = nomeDoUsuario;

            Console.WriteLine("Digite sua idade:");
            int idadeDoUsuario = int.Parse(Console.ReadLine());

            int dataDeNascimentoDoUsuario = Cotar.retornarDataDeNascimento(idadeDoUsuario);
            // Repare que o método retornarDataDeNascimento() foi chamado diretamente
            // pela classe Cotar, apesar de ter um objeto instanciado (cotacao)

            Console.WriteLine($"Olá {cotacao.Nome}, você nasceu em {dataDeNascimentoDoUsuario}.");

        }
    }
}
```

## Membros estáticos

Também chamados membros de classe (em oposição a membros e instância)

São membros que fazem sentido independentemente de objetos. Não
precisam de objeto para serem chamados, ou seja, não precisam ser instanciados. São chamados a partir do próprio nome da classe.

Aplicações comuns:
- Classes utilitárias (como a Math.Sqrt(double))
- Declaração de constantes

Uma classe que possui somente membros estáticos, pode ser uma classe
estática também. Esta classe não poderá ser instanciada.

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

## Object e ToString

Toda classe C Sharp é uma subclasse de Object.

Object possui os seguintes métodos:
* `GetType` retorna o tipo do objeto
* `Equals` compara se o objeto é igual a outro
* `GetHashCode` retorna um código hash do objeto
* `ToString` converte o objeto para string

Então se quisermos imprimir um objeto, basta utilizarmos a função .ToString(), ou como no exemplo abaixo, o C# já identifica que o objeto 'p' está numa concatenção de string, então ele já subentende que o método ToString pode ser utilizado.
Além disso, o método ToString pode ser reescrito (a partir do identificador 'override'), de modo a apresentar uma formatação específica.

```c#
using System.Globalization;
namespace Course {
    class Produto {
        public string Nome;
        public double Preco;
        public int Quantidade;

        public double ValorTotalEmEstoque() {
            return Preco * Quantidade;
        }

        public override string ToString() {
            return Nome
            + ", $ "
            + Preco.ToString("F2", CultureInfo.InvariantCulture)
            + ", "
            + Quantidade
            + " unidades, Total: $ "
            + ValorTotalEmEstoque().ToString("F2", CultureInfo.InvariantCulture);
        }
    }

    class Program{
        static void Main(){
            Produto p = new Produto("TV", 2300, 20);
            Console.WriteLine(p);
        }
    }
}

```