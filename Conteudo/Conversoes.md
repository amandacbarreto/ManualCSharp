# Conversões implícitas e explícitas

- Conversão implícita entre tipos
- Conversão explícita entre tipos COMPATÍVEIS

```c#
int i = 10;
long l =10;

l = i;
//Conversão do tipo implícita. O long (64 bits) tem o dobro de tamanho do int (32 bits), de modo que conseguimos colocar o valor de i em l.

i = l;
//O compilador avisa que não pode converter implicitamente um tipo long em um tipo inteiro

i = (int)l;
//Como nós sabemos que o valor de l(10) cabe em i, podemos utilizar uma conversão explícita.
//Porém se o valor de l for superior ao que pode ser armazendo em um inteiro, pode ocorrer a perda de dados.
```

Para converter um valor numerico para string, é preciso usar um membro de instância

```c#
string s = (125).ToString();
```
