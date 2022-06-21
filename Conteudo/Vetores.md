# Vetores

## Adicionando elementos a um vetor (Métodos `Append` e `ToArray`)

##### [String.Append Método](https://docs.microsoft.com/pt-br/dotnet/api/system.text.stringbuilder.append?view=net-6.0)

```c#
// Essa é a lista de filmes disponibilizada pelo professor inicialmente.
string[] listaDeFilmes = { "Clube dos Cinco", "A Hora do Pesadelo", "Karatê Kid", "Rocky IV", "Conan, o Bárbaro", "Highlander" };


//Adiciona um novo filme a lista pelo seu nome.
string[] adicionaUmNovoFilmePeloSeuNome(string nomeDoFilme)
{
    listaDeFilmes = listaDeFilmes.Append(nomeDoFilme).ToArray();
    return listaDeFilmes;
}

// Se o filme for Sexta-feira 13th, retorna Clube dos Cinco; A Hora do Pesadelo; Karatê Kid; Rocky IV; Conan, o Bárbaro; Highlander, Sexta-feira 13th
Console.WriteLine($"4. Adiciona um filme pelo nome {string.Join("; ", adicionaUmNovoFilmePeloSeuNome("Sexta-feira 13th"))}");

```

> **Note**
>
> É preciso que o vetor listaDeFilmes receba o retorno do statement 'listaDeFilmes.Append(nomeDoFilme).ToArray()', pois esse statement não modifica a string por si só. Ele retorna uma string com o texto "apensado", mas mantém a string original.

## Imprimindo os itens de um vetor sem iterar (Métodos `String.join`)

```c#
// Essa é a lista de filmes disponibilizada pelo professor inicialmente.
string[] listaDeFilmes = { "Clube dos Cinco", "A Hora do Pesadelo", "Karatê Kid", "Rocky IV", "Conan, o Bárbaro", "Highlander" };

// Listar todos os filmes com seu índice/posição na lista.
String[] listarTodosOsFilmesComSeuIndiceNaLista()
{
    string[] listaComIndice = new string[listaDeFilmes.Length];
    int count;
    for (count = 0; count < listaDeFilmes.Length; count++)
    {
        listaComIndice[count] = $"{count} - {listaDeFilmes[count]}";
    }
    return listaComIndice;
}

// Imprime 
// 0 - Clube dos Cinco 
// 1 - A Hora do Pesadelo 
// 2 - Karatê Kid
// 3 - Rocky III
// 4 - Conan, o Bárbaro
// 5 - Highlander
// 6 - Sexta-feira 13th
Console.WriteLine($"6. Listar todos os filmes com seu indice/posicao na lista. {string.Join(Environment.NewLine, listarTodosOsFilmesComSeuIndiceNaLista())}");
```