---
id: filter-query-introduction
title: Búsquedas limitadas
---

> **OBJETIVOS**
> 
> Definir los filtros de búsqueda basados en información usuario o básica para mostrar contenido filtrado en la aplicación iOS generada.
> **REQUISITOS PREVIOS**
> 
> Haga clic [aquí](prerequisites.html) para ver lo que necesita para empezar.


In this tutorial, we'll cover **restricted queries** with a simple use case: imagine you're an account manager and you want to consult your *In Progress* contracts simply by connecting to your app with your email address.

First, from the Data section we're going define a **basic filter query** to only display *In Progress* contracts. Then we're going to apply a **user information-based filter** which will depend on the account manager's email.

## Descargue el proyecto Starter

Before we begin, be sure to download the **Starter Project** which includes a **4DforiOSQueries.4dbase** file (a demo database with a ready-to-use mobile app project)

<div markdown="1" style="text-align: center; margin-top: 20px; margin-bottom: 20px">
<a class="button"
href="https://github.com/4d-for-ios/tutorial-RestrictedQueries/releases/latest/download/tutorial-RestrictedQueries.zip">PROYECTO STARTER</a>
</div>

The database includes a:

* **CRM table** with all the data we want to display in the generated iOS app
* **AccountManager table** with basic information about the account managers (email and name).

![CRM database](assets/en/restricted-queries/CRMDatabase.png)

> **NOTA**
> 
> Este proyecto utiliza [plantillas personalizadas](https://4d.github.io/4d-for-ios/docs/en/creating-listform-templates.html), [iconos personalizados](https://4d.github.io/4d-for-ios/docs/en/using-icons.html) y [formatos de datos personalizados](https://4d.github.io/4d -for-ios/docs/es/creating-data-formatter.html).

You're now ready to define your first restricted query!

Open the mobile project by clicking on Open > Mobile Project... and select CRM app > **project.4dmobileapp**.
