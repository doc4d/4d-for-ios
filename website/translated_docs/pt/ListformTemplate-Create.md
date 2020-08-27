---
id: creating-listform-templates
title: Modelos de formulários Lista
---

> **OBJETIVOS**
> 
> Criar seu primeiro modelo de formulário listado.


> **PRÉ-REQUISITOS**
> 
> Clique [aqui](prerequisites.html) para ver o que precisa para começar!


In this tutorial, we'll cover nearly all aspects of creating a list form template such as: creating a list form with a **searchBar** and a table displaying an **image**, a **title**, and a **subtitle** for each cell.

![List form template final result](assets/en/custom-listform/custom-template-final-result.png)

## Baixe o Starter Project

Before we begin, be sure to download the **Starter Project** which includes:

* A **List form** folder
* A **Contact.4dbase** file (a demo database with a ready-to-use mobile app project)

<div markdown="1" style="text-align: center; margin-top: 20px; margin-bottom: 20px">
<a class="button"
href="https://github.com/4d-for-ios/tutorial-CustomListForm/archive/513e9d4c378ac52a2a4bf84c7a96a132aecfb1c0.zip">LISTFORM STARTER PROJECT</a>
</div>

You are now ready to create your first list form template!

## Adicione um modelo de formulário lista para seu projeto móvel

The first thing you'll need to do is create a *Contact.4dbase/Resources/Mobile/form/list* folder. Then drag and drop your **list form** folder into it.

![Mobile folder list form template](assets/en/custom-listform/mobile-folder-custom-template.png)

Next, open the Contact.4dbase file with 4D. (File > open > Mobile Project > **Contact Demo App**)

Finally, in the **Forms section** of the project editor, you'll see that your list form template has been successfully added to the list of available list form templates!

![Seção Formulários](assets/en/custom-listform/custom-listform-template.png)

Now let's focus on the contents of the **Custom List form** folder.

## Conteúdos do modelo formulário lista

In this folder, you'll find:

* **a layoutIconx2.png** icon in 160x160px : it'll be displayed in the project editor when you select your template
* **a manifest.json file** : includes a basic description of the template
* **a template.svg file** : the visual representation of your template displayed when you define your list form content.
* Source folder : including the **storyboard** (graphical interface) and **Swift** file (code for the form)

What are these files? What are they used for? How can you customize them?
