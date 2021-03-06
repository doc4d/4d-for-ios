---
id: user-information-query
title: Filtro de pesquisa usuário
---

Agora vamos filtrar o conteúdo de nosso app dependendo da direção de correio eletrônico de início de sessão de administrador de conta (informação de usuário):

* Acesse a seção **"Dados"**. 
* Dê um clique direito no campo **Filtro de pesquisa** para que apareçam os **botões Campo, Comparadores e Operadores** .
* Clique no botão **Operadores** e selecione **AND**.
* Agora defina a informação de usuário que deseja obter do método de banco de dados, **:email**.
* Lembre de validar a pesquisa clicando no botão **Validate**. Do contrário não poderá criar sua aplicação.

![Filtro de pesquisa usuário](assets/en/restricted-queries/user-information-query.png)

```4d
Status = 'In Progress' & manager.Email = :email 
```

A pesquisa vai filtrar os dados dependendo do status de **In Progress** E do **endereço de email do gerente de conta** (acessível da tabela AccountManager graças a relação *Many-to-One* no nome do gerente).<div class = "tips"> 

**NOTA **

* A **user icon** is displayed on the right of each table when a user information filter is applied to it.
* As soon as a query is based on user information and validated, you need to edit the **Mobile app authentication method**. To do so, right-click on the **Edit authentication method** button to open the database method edition window.</div> 

Add the following line in the database method:

```4d
$response.userInfo:=New object("email";$request.email)
```

This will allow retrieving the manager's login email address and displaying data depending on that criteria.

![Filtro de pesquisa usuário](assets/en/restricted-queries/database-method-user-information-query.png)

Now if you build your app and enter "michelle.simpson@mail.com" as login email, you'll find all of Michelle Simpson's *"In progress"* contracts.

![Final result](assets/en/restricted-queries/restricted-queries-final-result.png)