# WPF

## Ícone da aplicação

1. Com a sua aplicação aberta, vá até a guia 'Projeto' e selecione o item 'Propriedades' do seu projeto.

![Tela do Visual Studio com Aba "Projetos" e "Propriedades de 'Nome do projeto selecionado' "  ](./img/wpf_icon_propriedades.png)

2. Na opção "Aplicativo", vá até "Recursos do Win32", "Ícone" e clique em procurar.

![Tela "propriedades do projeto" com a opção para escolher o ícone "  ](./img/wpf_icon_icone.png)

3. Escolha o ícone, que deve ser colocado na pasta da sua aplicação

![Gerenciador de arquivos do Windows com o arquivo selecionado para ser o ícone](./img/wpf_icon_escolha-do-icone.png)

![Aplicação com o ícone alterado](./img/wpf_icon_aplicacao-com-icone-alterado.png)

> **Note**
>
> Nesse exemplo, o arquivo foi colocado diretamente na pasta do projeto, então não foi necessário informar nenhum caminho relativo ou absoluto, mas caso necessário, poderíamos utilizar o atributo `Icon` para informar a localização do arquivo utilizado.

```html
<Window
  x:Class="SetIcon.MainWindow"
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  Icon="favicon.png"
  Title="MainWindow"
  Height="350"
  Width="525"
>
  <Grid> </Grid>
</Window>
```

## Menu

### [ WPF - Criando um menus em tempo de projeto](https://www.macoratti.net/11/03/wpf_mn2.htm)

- **`<Menu>` cria um controle Menu**

Propriedades

- Name: nome do controle
- Height
- Width definem a altura e largura do mesmo.
- Margin
- HorizontalAlignment
- VerticalAlignment
- Background: definir uma cor de fundo para o controle

```html
<menu
  Height="22"
  Name="menu1"
  Width="200"
  Margin="10, 10, 5, 5"
  HorizontalAlignment="Left"
  VerticalAlignment="Top"
  Background="Black"
>
</menu>
```

- **`<MenuItem>` inclui itens e sub-itens de menu**

Um MenuItem pode ter outras tags MenuItem aninhadas em diversos níveis.
As tags MenuItem devem estar contidas na tag Menu.

Propriedades:

- Header: define o nome o item de menu
- Background

```html
<menuitem Header="_Arquivo">
  <menuitem Header="_Abrir" Background="Yellow" />
  <menuitem Header="_Fechar" Background="Blue" />
  <menuitem Header="_Salvar" Background="Orange" />
</menuitem>
```

- **`<Separator/>` separa os itens do menu em categorias (linha divisória)**

```html
<Separator />
<menuitem Header="_Textos" Background="Black" Foreground="Coral">
  <menuitem Header="_Criar" />
  <menuitem Header="_Excluir" />
</menuitem>
<Separator />
```

- **`Tooltip` inclui uma dica ao item de menu**

Usamos a tag MenuItem.Tooltip e no seu interior a tag Tooltip:

```html
<menuitem Header="_Abrir" Background="Yellow">
  <MenuItem.ToolTip>
    <ToolTip> Abrir um arquivo. </ToolTip>
  </MenuItem.ToolTip>
</menuitem>
```

- **`IsCheckable="true` inclui uma caixa de verificação (CheckBox) a um item de menu**

```html
<menuitem IsCheckable="true"> </menuitem>
```

- **`InputGestureText` inclui um atalho de teclado a um item de menu**

```html
<menuitem IsCheckable="true" Header="_Novo" InputGestureText="Ctrl+N">
</menuitem>
```

- **`<MenuItem.Icon>` e `<Image/>` uma imagem a frente do item de menu**

```html
<MenuItem Header="_Sair >
    <MenuItem.Icon>
        <Image Source="Teste.jpg" Width="20" Height="20" />
    </MenuItem.Icon>
</MenuItem>
```

## TextBox

###### [Documentação Microsoft: Visão geral de TextBox](https://docs.microsoft.com/pt-br/dotnet/desktop/wpf/controls/textbox-overview?view=netframeworkdesktop-4.8)

```html
<TextBox
  Grid.ColumnSpan="12"
  Grid.Row="2"
  Name="contentBox"
  TextWrapping="Wrap"
  AcceptsReturn="True"
  VerticalScrollBarVisibility="Visible"
  FontFamily="Consolas"
  FontSize="14"
/>
```

A TextBox com essas configurações permite que o usuário entre com múltiplas linhas de texto. Quando a tecla RETURN for pressionada ou quando o texto alcançar os limites da TextBox, uma nova linha será inserida automaticamente.

## Focus

Para definir que o programa comece com um elemento em foco, utilize o código abaixo no elemento com hierarquia mais alta (geralmente Window ou o Grid que receberá todos os demais elementos)

```html
FocusManager.FocusedElement="{Binding ElementName=yourElement}"
```

[Exemplo](https://github.com/amandacbarreto/BlocoDeNotas/blob/67a42fe1c5b916d083f5f204941be056c99770ed/Bloco_de_notas/MainWindow.xaml#L9)

## Gerar um executável

###### [Documentação Microsoft: Tutorial Criar um aplicativo](https://docs.microsoft.com/pt-br/visualstudio/ide/walkthrough-building-an-application?view=vs-2022)
