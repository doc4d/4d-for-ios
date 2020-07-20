---
id: svg-file-listform-template
title: Template.svg
---

O arquivo template.svg é uma representação visual básica de um modelo. Neste arquivo, precisa definir áreas para poder adicionar campos para seu modelo de formulário lista do editor de projeto.

Aqui está a versão terminada:

![Arquivo template svg](assets/en/custom-listform/template-svg-file.png)

Abra o arquivo template.svg com seu editor de código favorito.

Vamos focar nas diferentes partes de seu arquivo SVG e o que vai precisar para editar.

## Título
```xml
<title>Custom List form</title>
```

Adicione o título para seu modelo aqui.

## ios:values

```xml
<text id="cookery" ios:values="search,section,f1,f2,f3"/>
```

Inclui IDs que definem suas áreas formulário:

* **search ID**: Refers to the search field area. Isso permite que arraste e solte um campo como um critério de pesquisa em seu formulário lista (opcional).
*  **section ID**: Refers to the section field area. Isso permite que arraste e solte um campo como o critério de ordenação em seu formulário lista (opcional).
*  **f1, f2 and f3 IDs**: Refers to the fields to display in each cell of your list form. Isso permite que arraste e solte campos para aparecer em suas células de formulário lista.

## Posição, altura, largura e tipo da Área
Pode definir a posição, altura e largura para:

* Campo de pesquisa
* Pesquisa seção
* Outros campos gerais que serão exibidas em cada célula tabela

### Área searchableField:

```xml
//1
<g transform="translate(0,60)”>

//2
<rect class="bg field" x="14" y="12" width="238" height="30”/>

//3
<path class="magnifyingGlass" transform="translate(20,8) scale(1)”/>

//4
<textArea id="search.label" class="label" x="14" y="8" width="238">$4DEVAL(:C991("fieldToUseForSearch"))</textArea>

//5
<rect id="search" class="droppable field optional" x="14" y="0" width="238" height="30" stroke-dasharray="5,2" ios:type=“0,1,2,4,8,9,11,25,35"  ios:bind="searchableField”/>

//6
<use id="search.cancel" x="224" y="1" xlink:href="#cancel" visibility="hidden”/> //6
</g>
```

1. Posição Y toda a área
2. Posição fundo, altura e largura da Área
3. Ícone para exibir um ícone lupa no campo de pesquisa
4. Define a posição e largura área texto.
5. Define the droppable field position, height, and width, as well as accepted **field types**
6. Define um botão cancelar que pode ser exibido para apagar o conteúdo atual

O campo pesquisável é opcional. 

<div markdown="1" class = "tips">
**NOTA **
All Field and Variable Types are available [here](http://doc.4d.com/4Dv17/4D/17/Field-and-Variable-Types.302-3729410.en.html).
</div>
<
div markdown="1" class = "tips">
**TIP**
To make field type definition easier, 4D for iOS allows you to include field types with **positive values** and also exclude field types with **negative values**. For example, `ios:type="-3,-4"` will allow you to drag and drop every field exept images and dates.
To include all types, just type ios:type="all". </div>

### Área SectionField:

```
//1
<rect class="bg field" x="10" y="110" width="246" height="30”/>

//2
<textArea id="section.label" class="label" x="10" y="118" width="246">$4DEVAL(:C991("fieldToUseAsSection"))</textArea>

//3
<rect id="section" class="droppable optional" x="10" y="110" width="246" height="30" stroke-dasharray="5,2" ios:type="0,1,2,4,8,9,11,25,35" ios:bind="sectionField”/>

//4
<use id="section.cancel" x="224" y="111" xlink:href="#cancel" visibility="hidden"/>
```

1. Posição, altura e largura da Área de fundo
2. Define a posição e largura área texto.
3. Define the droppable field position, height and width as well as accepted **field types**
4. Define um botão cancelar que pode ser exibido para apagar o conteúdo atual

The section field is optional.

### Área ImageField:

```
//1
<g transform="translate(0,162)">

//2
<rect class="bg field" x="14" y="0" width="60" height="65"/>

//3
<path class="picture" transform="translate(-60 0) scale(5)"/>

//4
<textArea id="f1.label" class="label" x="14" y="30" width="60">$4DEVAL(:C991("picture"))</textArea>

//5
<rect id="f1" class="droppable field" x="14" y="0" width="60" height="65" stroke-dasharray="5,2" ios:type="3" ios:bind="fields[0]"/>

//6
<use id="f1.cancel" x="47" y="-2" xlink:href="#cancel" visibility="hidden"/>
</g>
```

1. Posição Y toda a área
2. Posição, altura e largura da Área de fundo
3. Ícone para exibir uma imagem no ImageField
4. Define a posição e largura área texto.
5. Define the droppable field position, height and width as well as accepted **field types**
6. Define um botão cancelar que pode ser exibido para apagar o conteúdo atual

### Área Title Field:

```
//1
<g transform="translate(0,162)”>

//2
<rect class="bg field" x="84" y="0" width="168" height="30”/>

//3
<textArea id="f2.label" class="label" x="84" y="8" width="168">$4DEVAL(:C991("titleField"))</textArea>

//4
<rect id="f2" class="droppable field" x="84" y="0" width="168" height="30" stroke-dasharray="5,2" ios:type="0,1,2,4,8,9,11,25,35" ios:bind="fields[1]”/>

//5
<use id="f2.cancel" x="224" y="1" xlink:href="#cancel" visibility="hidden"/>
</g>
```

1. Posição Y toda a área
2. Posição, altura e largura da Área de fundo
3. Define a posição e largura área texto.
4. Define the droppable field position, height and width as well as accepted **field types**
5. Define um botão cancelar que pode ser exibido para apagar o conteúdo atual

### Área Subtitle Field:
```
//1
<g transform="translate(0,198)”>

//2
<rect class="bg field" x="84" y="0" width="168" height="30”/>

//3
<textArea id="f3.label" class="label" x="84" y="8" width="168">$4DEVAL(:C991("subtitleField"))</textArea>

//4
<rect id="f3" class="droppable field" x="84" y="0" width="168" height="30" stroke-dasharray="5,2" ios:type="0,1,2,4,8,9,11,25,35" ios:bind="fields[2]”/>

//5
<use id="f3.cancel" x="224" y="1" xlink:href="#cancel" visibility="hidden"/>
</g>
```

1. Posição Y toda a área
2. Posição, altura e largura da Área de fundo
3. Define a posição e largura área texto.
4. Define the droppable field position, height and width as well as accepted **field types**
5. Define um botão cancelar que pode ser exibido para apagar o conteúdo atual

Now that you have an **icon**, a **basic template description** in the manifest.json file, and your **svg file** ... let's move on to the fun part with Xcode!
