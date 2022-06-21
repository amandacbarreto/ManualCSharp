# String

## Concatenando elementos de uma coleção com `Join`

##### [String.Join Método](https://docs.microsoft.com/pt-br/dotnet/api/system.string.join?view=net-6.0)

Concatena os elementos de uma matriz especificada ou os membros de uma coleção, usando o separador especificado entre cada elemento ou membro.

```c#
public static string Join (string? separator, params object?[] values);
```

- **Parâmetros**

`separator` String

A cadeia de caracteres a ser usada como um separador. `separator` estará incluído na cadeia de caracteres retornada somente se `values` tiver mais de um elemento.

`values` Object[]

Uma matriz que contém os elementos a concatenar.

- **Retornos**

**String**

Uma cadeia de caracteres composta pelos elementos de `values` delimitados pela cadeia de caracteres `separator`.

-ou-

**Empty** se `values` não tiver elementos.

-ou-

.NET Framework somente: Empty se o primeiro elemento for `values` `null`.

```c#
string apresentaTodosOsFilmesSeparadosPorPontoVirgula()
{
    return string.Join("; ", listaDeFilmes);
}
```


