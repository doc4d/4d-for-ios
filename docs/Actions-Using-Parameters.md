---
id: using-parameters
title: Using parameters
---

<div markdown="1" class = "objectives">

**OBJECTIVES**

Define action parameters to edit the content of your app.

</div>

In the [previous tutorial](define-first-action.html), we discoverd how to execute 4D code from an iOS app by defining actions from the [Actions section](actions.html).

In this tutorial we are going to go further and create:

* an Add action in order to **create a new task**.
* an Edit action that will allow you to **edit existing tasks** from the iOS app.
* a Delete action to **delete an entity**.
* an action that will enable you to **email a comment for a specific task**.

To begin, let's first download the **Starter Project** based on our existing Tasks app iOS app.

<div markdown="1" style="text-align: center; margin-top: 20px; margin-bottom: 20px">

<a class="button"
href="../assets/en/actions/ActionParametersStarterProject.zip">STARTER PROJECT</a>

</div>

## STEP 1. Add action

Let's begin simple. Open the Tasks mobile project and go right to the **Actions section**. 

![Action section](assets/en/actions/Actions-section.png)

Quite empty for the moment... But here is what we want for now: **create a new task from the iOS app**.

For that, let's create an action using a **Preset Add action**:

* Clic on the arrow situated into the **Plus button** at the bottom left of the Actions table.
* Select the **Add action for** option.
* Select the **Task table**. 

![Add action creation](assets/en/actions/Add-action-creation.png)

* **A new action** named *"addTasks"* with *"Add..."* as default label.
* **All action parameters** and their **properties** should be available under **Actions parameters**.

![Add action parameters](assets/en/actions/Add-action-parameters.png)

At this point, all **Add action parameters** are automatically created and ready to use.

## STEP 2. Edit action

Now Let's create an action that will allow you to **edit your app content**.

For that, let's create an action using a **Preset Edit action**:

* Click on the arrow situated into the **Plus button** at the bottom left of the Actions table.
* Select the **Edit action for** option.
* Select the Task table. 

![Edit action creation](assets/en/actions/Edit-action-creation.png)

At this point, you should see:

* **A new action** named *"editTasks"* with *"Edit..."* as default label.
* **All action parameters** and their **properties** should be available under **Actions parameters**.


![Edit action parameters](assets/en/actions/Edit-action-parameters.png)

Don't worry, we will manage 4D code later to do what we want to do :)

## STEP 3. Delete action

The **Preset Delete action** creation process is quite the same as for The Edit action:

* Clic on the arrow situated into the **Plus button** at the bottom left of the Actions table.
* Select the **Delete action for** option.
* Select the Tasks table. 

![Delete action creation](assets/en/actions/Delete-action-creation.png)

At this point, you should see a **new action** named *"deleteTasks"* with *"Remove"* as a default label.

![Delete action](assets/en/actions/Delete-action-final.png)

You won't have to worry about parameters or properties for this type of action.

## STEP 4. Send a comment action

There we want to **send a comment** to a **specific email** depending on a specific task. To do so, clic on the Plus button and create a new action named **sendComment**.

![Delete action creation](assets/en/actions/Send-comment-action-creation.png)

Now let's create Three parameters:

* Click on the plus button and select **Title** in the parameter's list because you want to include it in the email your are going to send.
* Create a **Comment parameter** and select Text area as a format property.
* Create an **email parameter** and select Email address as a format property.

Your Actions section should look like that :

![Send comment action creation](assets/en/actions/Send-comment-action-definition.png)


## STEP 5. Create All the method you need


### addAction

```

C_OBJECT($0)
	$out.statusText:="Task added"


```

### editAction

```

C_OBJECT($0)


```

### deleteAction

```

C_OBJECT($0)


```

### sendEmail

```

C_OBJECT($0;$out)

```

<div markdown="1" class = "tips">

**TIPS**

* Don't forget to add your own values for this **sendEmail Action**.

</div>




## STEP 6. Create the on Mobile App Action

As described in the [documentation](actions.html) click on the Create button to create the On Mobile App Action Database method.

All your actions will automatically included in this database method in a case of.

The only thing you got to do is add a reference to your methods depending on the case your want to cover.

Here is the final example of the On Mobile App Action database method:

```
C_OBJECT($0;$response)


```

## STEP 7. Build your app


Build your app ! 

From here, if you click on the action navigation bar button, you will be able to **create a new task**.

![Create new task](assets/en/actions/Action-parameters-addAction.png)

If you make a long pressure on your new task cell in the List Form, you will find that an **Edit...** action has been added in the action list.

![Edit task](assets/en/actions/Action-parameters-editAction.png)

Send a comment using the **Send comment** action.

![Edit task](assets/en/actions/Action-parameters-sendComment.png)

And finally you can delete an entity using **Delete...** action.

![Edit task](assets/en/actions/Action-parameters-deleteAction.png)

## STEP 8. Where to Go From Here?

Congratulations, your Tasks iOS app is now complete. You can modify your app data direclty from your device and sychronize it with your server!

<div markdown="1" style="text-align: center; margin-top: 20px; margin-bottom: 20px">

<a class="button"
href="../assets/en/actions/ActionParametersFinalProject.zip">FINAL PROJECT</a>

</div>
