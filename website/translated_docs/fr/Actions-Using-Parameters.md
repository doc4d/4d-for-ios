---
id: using-parameters
title: Utiliser des paramètres
---

<div class = "objectives"> 

**OBJECTIFS**

Définir des paramètres d'action pour modifier le contenu de votre application.</div> 

Dans le [tutoriel précédent](define-first-action.html), nous avons appris à exécuter du code 4D à partir d'une application iOS en définissant des actions à partir de la [section Actions](actions.html).

Dans ce tutoriel, nous irons encore plus loin et nous créerons :

* une action d'ajout pour **créer une nouvelle tâche**,
* une action d'édition qui vous permettra d'**éditer les tâches existantes** à partir de l'application iOS,
* une action de suppression pour **supprimer une entité**, et
* une action qui vous permettra d'**envoyer par e-mail un commentaire relatif à une tâche spécifique**.

Pour commencer, téléchargeons d'abord le **Projet Starter**, basé sur notre application iOS Tasks.

<div style="text-align: center; margin-top: 20px; margin-bottom: 20px">
  <p>
    

<a class="button"
href="../assets/en/actions/ActionParametersStarterProject.zip">PROJET STARTER</a>

  </p>
</div>

## ÉTAPE 1. Action d'ajout

Commençons par une tâche simple. Ouvrez le projet mobile Tasks et cliquez directement sur la **section Actions**.

![Action section](assets/en/actions/Actions-section.png)

Pour l'instant, elle est assez vide... Voici ce que nous souhaitons faire : **créer une nouvelle tâche à partir de l'application iOS**.

Pour ce faire, nous allons créer une action à l'aide de l'action d'**ajout** :

* Cliquez sur la flèche qui se trouve dans le **bouton +**, en-dessous du tableau d'actions.
* Sélectionnez l'option **action d'ajout**.
* Sélectionnez la **table Task**. 

![Add action creation](assets/en/actions/Add-action-creation.png)

* **Une nouvelle action** nommée *"addTasks"* est affichée avec, par défaut, le libellé *"Add..."*.
* Tous les **paramètres** disponibles ainsi que leurs **propriétés** se trouvent dans la section **Paramètres des actions**.

![Add action parameters](assets/en/actions/Add-action-parameters.png)

A ce stade, tous les **paramètres des actions d'ajout** sont créés automatiquement et sont prêts à l'emploi.

## ÉTAPE 2. Action d'édition

Créons maintenant une action qui vous permettra d'**éditer le contenu de votre application**.

Pour ce faire, nous allons créer une action à l'aide de l'action d'**édition** :

* Cliquez sur la flèche qui se trouve dans le **bouton +**, en-dessous du tableau d'actions.
* Sélectionnez l'option **action d'édition**.
* Sélectionnez la table Tasks. 

![Edit action creation](assets/en/actions/Edit-action-creation.png)

Vous allez donc voir :

* **Une nouvelle action** nommée *"editTasks"* avec, par défaut, le libellé *"Edit..."*.
* Tous les **paramètres** d'action disponibles ainsi que leurs **propriétés** dans la section **Paramètres des actions**.

![Edit action parameters](assets/en/actions/Edit-action-parameters.png)

Pas de panique, nous reviendrons sur le code 4D de ces actions un peu plus tard. :-)

## ÉTAPE 3. Action de suppression

Le processus de création de l'action prédéfinie de **suppression** est à peu près identique à l'action d'édition :

* Cliquez sur la flèche qui se trouve dans le **bouton +**, en-dessous du tableau d'actions.
* Sélectionnez l'option **action de suppression**.
* Sélectionnez la table Tasks. 

![Delete action creation](assets/en/actions/Delete-action-creation.png)

Vous verrez apparaître une **nouvelle action** nommée *"deleteTasks"* avec, par défaut, le libellé *"Remove"*.

![Delete action](assets/en/actions/Delete-action-final.png)

Vous n'avez pas à vous préoccuper des paramètres ou des propritées pour ce type d'action.

## ÉTAPE 4. Action d'envoi de commentaire

Nous souhaitons maintenant **envoyer un commentaire** à une **adresse mail spécifique**, par rapport à une tâche spécifique. Pour ce faire, cliquez sur le bouton + et créez une nouvelle action que vous nommerez **sendComment**.

![Delete action creation](assets/en/actions/Send-comment-action-creation.png)

Nous allons créer trois paramètres :

* Cliquez sur le bouton + et sélectionnez **Title** dans la liste de paramètres des actions, pour l'inclure dans l'e-mail que vous allez envoyer.
* Créez un paramètre **Comment** et sélectionnez le format Zone de texte.
* Créez un paramètre **email** et sélectionnez le format Adresse mail.

Votre section Actions devrait ressembler à ceci :

![Send comment action creation](assets/en/actions/Send-comment-action-definition.png)

## ÉTAPE 5. Création de la méthode base Sur une action app mobile

Comme indiqué dans la [documentation](actions.html), cliquez sur le bouton Créer... pour créer la méthode base *Sur une action app mobile*.

Toutes vos actions seront comprises automatiquement dans la méthode base.

Il ne vous reste qu'à ajouter une référence à votre/vos méthode(s) pour le(s) scénario(s) que vous souhaitez gérer.

Voici la méthode base *Sur une action app mobile* finale :

    C_OBJECT($0;$response)
    C_OBJECT($1;$request)
    
    C_OBJECT($o;$context;$request;$result;$parameters)
    
    $request:=$1  // Informations provided by mobile application
    
    $context:=$request.context
    $parameters:=$request.parameters
    
    Case of 
    
        : ($request.action="addTasks")
    
              // Insert here the code for the action "Add…"
    
            $o:=OB Copy($parameters)
            $o.dataClass:=$context.dataClass
    
            $result:=addAction ($o)
    
        : ($request.action="editTasks")
    
              // Insert here the code for the action "Edit…"
    
            $o:=OB Copy($parameters)
            $o.dataClass:=$context.dataClass
            $o.ID:=$context.entity.primaryKey
    
            $result:=editAction ($o)
    
    
        : ($request.action="deleteTasks")
    
              // Insert here the code for the action "Remove"
    
            $o:=New object(\
            "dataClass";$context.dataClass;\
            "ID";$context.entity.primaryKey)
    
            $result:=deleteAction ($o)
    
        : ($request.action="sendComment")
    
              // Insert here the code for the action "Send Comment"
    
            $o:=OB Copy($parameters)
            $o.dataClass:=$context.dataClass
            $o.ID:=$context.entity.primaryKey
    
    
            $result:=sendMail ($o)
    
        Else 
    
               // Unknown action
            $result:=New object(\
            "success";False;\
            "statusText";"Internal error")
    
    End case 
    
    $0:=$result
    
    
    
    

## ÉTAPE 6. Création de toutes les méthodes nécessaires

### addAction

    <br />C_OBJECT($0)
    C_OBJECT($1)
    
    C_OBJECT($entity;$in;$out)
    
    $in:=$1
    $out:=New object("success";False)
    
    If ($in.dataClass#Null)
    
        $entity:=ds[$in.dataClass].new()  //create a reference
    
        $entity.CompletePercentage:=$in.CompletePercentage
        $entity.StartDate:=$in.StartDate
        $entity.DueDate:=$in.DueDate
        $entity.Description:=$in.Description
        $entity.Title:=$in.Title
        $entity.Status:=$in.Status
        $entity.Priority:=$in.Priority
    
        $entity.save()  //save the entity
    
        $out.success:=True  // notify App that action success
        $out.dataSynchro:=True  // notify App to refresh the selection
        $out.statusText:="Task added"
    
    Else 
    
        $out.errors:=New collection("No Selection")
    
    End if 
    
    $0:=$out
    
    
    

### editAction

    <br />C_OBJECT($0)
    C_OBJECT($1)
    
    C_OBJECT($dataClass;$entity;$in;$out;$status;$selection;$emailToSend)
    
    $in:=$1
    $out:=New object
    
    $selection:=ds[$in.dataClass].query("ID = :1";String($in.ID))
    
    If ($selection.length=1)
    
        $entity:=$selection[0]
    
        $entity.CompletePercentage:=$in.CompletePercentage
        $entity.StartDate:=$in.StartDate
        $entity.DueDate:=$in.DueDate
        $entity.Description:=$in.Description
        $entity.Title:=$in.Title
        $entity.Status:=$in.Status
        $entity.Priority:=$in.Priority
    
        $status:=$entity.save()
    
        If ($status.success)
    
            $out.success:=True  // notify App that action success
            $out.dataSynchro:=True  // notify App to refresh this entity
            $out.statusText:="Task edited"
    
        Else 
    
            $out:=$status  // return status to the App
    
        End if 
    
    Else 
    
        $out.success:=False  // notify App that action failed
    
    End if 
    
    $0:=$out
    
    
    

### deleteAction

    <br />C_OBJECT($0)
    C_OBJECT($1)
    
    C_OBJECT($dataClass;$entity;$in;$out;$status;$selection)
    
    $in:=$1
    $out:=New object
    
    $selection:=ds[$in.dataClass].query("ID = :1";String($in.ID))
    
    If ($selection.length=1)
    
        $entity:=$selection.drop()
    
        If ($entity.length=0)
    
            $out.success:=True  // notify App that action success
            $out.dataSynchro:=True  // notify App to refresh this entity
            $out.statusText:="Task deleted"
    
        Else 
    
            $out:=$status  // return status to the App
    
        End if 
    
    Else 
    
        $out.success:=False  // notify App that action failed
    
    End if 
    
    $0:=$out
    
    
    

### sendEmail

    <br />C_OBJECT($0;$out)
    C_OBJECT($1;$in)
    
    C_OBJECT($dataClass;$entity;$selection)
    
    $in:=$1
    $out:=New object
    
    $selection:=ds[$in.dataClass].query("ID = :1";String($in.ID))
    
    If ($selection.length=1)
    
        $entity:=$selection[0]
    
        $taskTitle:=$in.Title
        $commentToSend:=$in.Comment
        $emailToSend:=$in.Email
    
        $server:=New object
        $server.host:="smtp.gmail.com"
        $server.port:=465
        $server.user:="test@mail.com" //To be replaced by your email
        $server.password:="yourPassword" //To be replaced by your password
    
        $transporter:=SMTP New transporter($server)
    
        $email:=New object
        $email.subject:="New comment about one of your task"
        $email.from:="yourEmail" //To be replaced by your email
        $email.to:=$emailToSend
        $email.htmlBody:="&lt;h1&gt;Comment from Tasks for iOS&lt;/h1&gt;"+"&lt;p&gt;&lt;b&gt;Task:&lt;/b&gt; "+$taskTitle+"&lt;/p&gt;&lt;p&gt;&lt;b&gt;Comment:&lt;/b&gt; "\
        +$commentToSend+"&lt;/p&gt;&lt;br&gt;&lt;p&gt;&lt;i&gt;Send from my 4D for iOS app&lt;/i&gt;&lt;/p&gt;"\
    
        $status:=$transporter.send($email)
        If ($status.success)
            $out.success:=True  // notify App that action success
            $out.statusText:="Mail sent"
    
        Else 
            $out.success:=False  // notify App that action success
            $out.statusText:="Mail not sent"
    
        End if 
    
    Else 
    
        $out.success:=False  // notify App that action failed
    
    End if 
    
    $0:=$out
    
    <div class = "tips"> 

**CONSEILS**

* N'oubliez pas d'ajouter vos propres valeurs pour l'action **sendEmail**.</div> 

## ÉTAPE 7. Génération de l’application

Il est temps de générer votre application !

Si vous cliquez sur le bouton Action de la barre de navigation, vous pourrez **créer une nouvelle tâche**.

![Create new task](assets/en/actions/Action-parameters-addAction.png)

Si vous maintenez votre pouce sur la nouvelle tâche du formulaire Liste, une action d'**édition** s'affichera dans la liste d'actions.

![Edit task](assets/en/actions/Action-parameters-editAction.png)

Envoyez un commentaire à l'aide de l'action **Send comment**.

![Send task comment](assets/en/actions/Action-parameters-sendComment.png)

Enfin, vous pouvez supprimer une entité à l'aide de l'action de **suppression**.

![Delete task](assets/en/actions/Action-parameters-deleteAction.png)

## ÉTAPE 8. Que faire ensuite ?

Félicitations ! Votre application iOS Tasks est désormais complète. Vous pouvez dès à présent modifier les données de votre application directement sur votre appareil et les synchroniser avec votre serveur !

<div style="text-align: center; margin-top: 20px; margin-bottom: 20px">
  <p>
    

<a class="button"
href="../assets/en/actions/ActionParametersFinalProject.zip">PROJET FINAL</a>

  </p>
</div>