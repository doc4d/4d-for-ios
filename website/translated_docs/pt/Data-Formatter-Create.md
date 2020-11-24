---
id: creating-data-formatter
title: Criar formato de dados
---

> **OBJETIVOS**
> 
> Criar seus primeiros formatos de dados.

> **PRÉ-REQUISITOS**
> 
> Clique [aqui](prerequisites.html) para ver o que precisa para começar!

Neste tutorial, vamos guiá-lo através da criação de vários exemplos de formatador.

## Baixe o Starter Project

Para começar, baixe o **Starter Project**, que inclui:

* Pastas**integerToImage_Images** e **textToImage_Images** que contêm imagens (para usar mais tarde para formatadores que incluem imagens)
* Um arquivo de **Task Management.4dbase** (com um projeto de app móvel pronto para usar)

<div markdown="1" style="text-align: center; margin-top: 20px; margin-bottom: 20px">
<a class="button"
href="https://github.com/4d-for-ios/tutorial-CustomDataFormatter/archive/66d7eea49bc3353f73dbf784ee06283b3a332d0b.zip">PROJETO STARTER - FORMATO PERSONALIZADO</a>
</div>

Agora você já está pronto para criar seus primeiros formatadores!

## Crie a pasta formatadores

Primeiro, crie uma pasta *Task Management.4dbase/Resources/Mobile/formatters *.

![Formatter folder](assets/en/custom-formatter/formatter-folder.png)

## Formatadores de inteiros

### Número inteiro para string

* Crie uma pasta ** integerToString **na pasta formatadores, que você acabou de criar.
* Em seguida, crie um arquivo **manifest.json ** na pasta **integerToString**.

![Formatter folder](assets/en/custom-formatter/formatter-folder-integertostring.png)

Vamos olhar o conteúdo do arquivo de**manifest.json **:

```json
{
   "name": "integerToString",

   "type": ["integer"],

   "binding": "localizedText",

   "choiceList": {"0":"UX designer","1":"Developer","2":"QA","3":"Product Owner"}
}
```

1. **nome**: o nome do formatador
2. **tipo**: o tipo de formatador 4D você deseja usar
3. **binding**: pode ser **texto localizado** para strings de caracteres ou **imageNamed** para imagens
4. **choiceList**: valores mapeados

### Inteiro para imagem

* Crie uma pasta ** integerToString **na pasta  **formatadores **, que você acabou de criar.

* Em seguida, crie um arquivo de**manifest.json ** na pasta **integerToImage**.

![Formatter folder](assets/en/custom-formatter/formatter-folder-integertoimage.png)

* Em seguida, crie uma pasta** Imagens** na pasta **IntegerToImage**. Pode adicionar as imagens de **IntegerToImage_Images ** em StarterProject.zip para a nova pasta.

![Formatter images](assets/en/custom-formatter/formatter-images-integertoimage.png)

Vamos olhar o conteúdo do arquivo de**manifest.json **:


```json
{
    "name": "integerToImage",

   "type": ["integer"],

   "binding": "imageNamed",

   "choiceList": {"0":"todo.png","1":"inprogress.png","2":"pending.png","3":"done.png"},

   "assets": {
      "size": {
         "width": 40, "height": 40
      }
    }
}
```
1. **nome**: o nome do formatador
2. **tipo**: o tipo de formatador 4D você deseja usar
3. **binding**: pode ser **texto localizado** para strings de caracteres ou **imageNamed** para imagens
4. **choiceList**: valores mapeados
5. **assets**: ajusta o tamanho do display (largura e altura)

## Formatadores de Texto

### Texto para string

* Crie uma pasta ** textToString **na pasta formatadores, que você acabou de criar.

* Crie um arquivo de **manifest.json ** na pasta **textToString**.

![Formatter folder](assets/en/custom-formatter/formatter-folder-texttostring.png)

Vamos olhar o conteúdo do arquivo de**manifest.json **:

```json
{
    "name": "textToString",

   "type": ["text"],

   "binding": "localizedText",

   "choiceList": {"FRA":"France","MAR":"Morocco","USA":"United States","AUS":"Australia"}
}
```

1. **nome**: o nome do formatador
2. **tipo**: o tipo de formatador 4D você deseja usar
3. **binding**: pode ser **texto localizado** para strings de caracteres ou **imageNamed** para imagens
4. **choiceList**: valores mapeados

### Texto para Imagem

* Crie uma pasta ** textToImage **na pasta formatadores, que você acabou de criar.

* Crie um arquivo de**manifest.json ** na pasta **textToImage**.

![Formatter folder](assets/en/custom-formatter/formatter-folder-textToImage.png)

* Em seguida, crie um arquivo de** Imagens** na pasta **textToImage**. Pode adicionar as imagens de **textToImage_Images ** em StarterProject.zip para a nova pasta.

![Formatter images](assets/en/custom-formatter/formatter-images-textToImage.png)

Vamos olhar o conteúdo do arquivo de**manifest.json **:

```json
{
    "name": "textToImage",

   "type": ["integer"],

   "binding": "imageNamed",

   "choiceList": ["image1.png","image2.png","image3.png"],

   "assets": {
  "size": {
   "width": 40, "height": 40
        }
    }
}

```

## Abrir projeto móvel

Abra Task Management.4dbase com 4D e vá para File > abra > Mobile Project... para abrir **Tasks**

Agora, vá para a seção **Labels & Icons** no editor de projetos. Todos os formatadores estão disponíveis para os tipos de campo diferentes que você definiu previamente nos arquivos manifest.json de diferentes  formatadores:

* Selecione o formatador de**integerToString ** para o **campo Job**
* Selecione o formatador de** textToString** para o **campo Country**
* Selecione o formatador ** integerToImage** para o **Task Status**
* Selecione o formatador ** textToImage** para o **Manager**

![Text formatter](assets/en/custom-formatter/formatters-icons-&-labels.png)

## Construa seu app 4D for iOS

Construa seu app 4D for iOS e você verá que o formatador de dados é bem aplicado dependendo do limite de crédito.

![Text formatter](assets/en/custom-formatter/formatters-final-result.png)

Clique em **FORMATADOR FINAL** abaixo para baixar a pasta de modelo formatador concluído.

<div markdown="1" style="text-align: center; margin-top: 20px">

<a class="button"
href="https://github.com/4d-for-ios/tutorial-CustomDataFormatter/releases/latest/download/tutorial-CustomDataFormatter.zip">FORMATO FINAL</a>
</div>
