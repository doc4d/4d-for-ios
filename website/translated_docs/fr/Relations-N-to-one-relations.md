---
id: many-to-one-relations
title: Liens N vers 1
---

4D v17 R5 lance un nouveau concept : les liens N vers 1

<div markdown="1" class = "tips">
**NOTE**
Dans ce tutoriel, nous allons utiliser les noms des liens reliant vos tables. En attribuant des noms de liens descriptifs, vous simplifierez la structure de votre projet.
</div>

Commençons par télécharger le Projet Starter :

<div markdown="1" style="text-align: center; margin-top: 20px; margin-bottom: 20px">
<a class="button"
href="https://github.com/4d-for-ios/tutorial-ManyToOneRelations/releases/latest/download/tutorial-ManyToOneRelations.zip">PROJET STARTER N VERS UN</a>
</div>

Here we want to display the category for each task in the detail form of your generated app. To do so, open the **StarteriOSProject** from **Open > Mobile Project...**

Then go right to your Structure section and select the **Task table**.

### Section Structure

* You can notice that the **TaskCategory relation** is underlined

* En cliquant dessus, vous afficherez les champs disponibles à travers ce lien

* Select the **Name field**

![Select link from structure section](assets/en/relations/select-link-from-structure.png)

* Ce champ aura le même fonctionnement que n’importe quel autre champ pour la suite de la création de l’application

* Vous pouvez également filtrer le contenu de votre application à l’aide des champs liés, à partir de la section Données. To do so enter `TaskCategory.Name != 'Personal'` in the Filter query field to exclude personal tasks.

 ![Champs liés depuis la section Données](assets/en/relations/Related-field-from-Data-section.png)

* You can then select an **icon** as well as **formatters** and define **short and long labels** from the Labels and Icons section

![Related field from Labels and Icons section](assets/en/relations/related-field-from-labels-icons.png)

* Cliquez sur la section Formulaires et faites glisser le champ dans le formulaire détaillé Tasks

![Related field in Forms section](assets/en/relations/related-field-forms.png)

* Build and Run

Votre champ lié devrait apparaitre dans le formulaire détaillé de votre application !

![Related field in Forms section](assets/en/relations/final-result-n-to-one-relations.png)


