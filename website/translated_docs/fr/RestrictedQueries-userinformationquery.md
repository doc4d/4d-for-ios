---
id: user-information-query
title: Filtre de recherche - informations utilisateur
---

Nous allons filtrer maintenant le contenu de notre application en fonction de l'e-mail de connexion du chargé de clientèle (information utilisateur) :

* Go to the **Data section**.
* Right-click in the **Filter query** field to make **Field, Comparators and Operators buttons** appear.
* Click on the **Operators** button and select **AND**.
* Now define the user information you want to get from the database method, **:email**.
* Remember to validate the query by clicking on the **Validate** button. Sinon, vous ne pourrez plus créer votre application.

![Filtre de recherche - informations utilisateur](assets/en/restricted-queries/user-information-query.png)

```4d
Status = 'In Progress' & manager.Email = :email 
```

The query will filter data depending on the **In Progress** status AND the **Account manager's email address** (accessible from the AccountManager table thanks to the *Many-to-One* relation on the manager's name).

<div markdown="1" class = "tips">
**NOTE**

* A **user icon** is displayed on the right of each table when a user information filter is applied to it.
* As soon as a query is based on user information and validated, you need to edit the **Mobile app authentication method**. To do so, right-click on the **Edit authentication method** button to open the database method edition window.
</div>

Ajoutez la ligne suivante dans la méthode de base de données :

```4d
$response.userInfo:=New object("email";$request.email)
```

Cela permettra de récupérer l’adresse mail de connexion du chargé de clientèle et d'afficher les données selon ce critère.

![Filtre de recherche - informations utilisateur](assets/restricted-queries/database-method-user-information-query.png)

Now if you build your app and enter "michelle.simpson@mail.com" as login email, you'll find all of Michelle Simpson's *"In progress"* contracts.

![Final result](assets/restricted-queries/restricted-queries-final-result.png)




