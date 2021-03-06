---
id: structure
title: Structure
---

This section displays all your database tables and fields exposed by 4D Mobile Service.

![Sección Structure](assets/en/project-editor/Structure-section-4D-for-iOS.png)

Aquí, puede definir un subconjunto de su estructura física para reproducir en dispositivos móviles seleccionando tablas y campos específicos. El seleccionado:

* las tablas seleccionadas se agregarán automáticamente a las pestañas de su aplicación.
* fields will be available later when you will need to define your list and detail forms.

## Relaciones Muchos a Uno

* 4D 17R5 allows you to visualize table relations in the generated app by publishing them from the Structure section. Then, when your related fields are published, they can be used like any other field in the [app creation process](many-to-one-relations.html).

![Publish related tables](assets/en/project-editor/Structure-section-N-to-1-relations-4D-for-iOS.png)

* 4D 18R6 añade la posibilidad de publicar relaciones Muchos a Uno y Uno a Muchos desde sus relaciones Muchos a Uno en la sección Estructura.

Esto significa que podrá mostrar relaciones de muchos a muchos en su aplicación y pasar directamente de un formulario listado a otro formulario listado.


> **RECOMENDACIONES**
> 
> Puede publicar una selección de campos presionando la barra espaciadora, en lugar de seleccionarlos uno por uno.
> 
> To help you define your app's structure, multiple filters and a search engine are available to make the selection of your tables and field easier.


## Relaciones Uno a Muchos

### Tratar las relaciones de Uno a Muchos desde el editor del proyecto

In the latest versions of 4D, you can deal with **One to Many relations** and display a list of related fields in a new page.

All you need to do is:

* Publishing at least one field of the target (Many) table

* Publishing the relation from the source (One) table

![Drop relation in detail form](assets/en/project-editor/Structure-1-to-N-relations-4D-for-iOS.png)

Luego, cuando se publican sus campos relacionados, se pueden utilizar como cualquier otro campo. You will then be able to:

* Definir las propiedades de las relaciones en la sección [ Etiquetas e iconos](labels-and-icons.html#relations-properties).

* Drop the One to Many relation in a Detail form from the Forms Section? to create a link between a detail form and a related table.

### ¿Qué se creará en el proyecto generado?

Basically, a Relation button will be created in detail forms to go straight to the related view.

[Tutoriales](one-to-many-relations.html) están disponibles para ayudarlo a utilizar la relación Uno a Muchos en su proyecto 4D for iOS.



## Recarga incremental

### Autorizar las modificaciones de la estructura

En 4D 17 R5, la recarga de 4D for iOS se vuelve incremental. Esto significa que solo se actualizarán los datos de la base que sean nuevos, modificados o eliminados. ¡Esta es una gran optimización en términos de tiempo de carga!

Para hacerlo, 4D for iOS debe optimizar la estructura y crear:

* Una tabla `__DeletedRecords` para almacenar los registros borrados
* `__GlobalStamp` fields to store modification stamps for each published table in your mobile application

Todo lo que necesita hacer es permitir que 4D for iOS realice los ajustes de estructura necesarios para una actualización optimizada de datos móviles.

Una vez autorizado, 4D for iOS hará todo el trabajo por usted, y usted se beneficiará completamente de todas las ventajas de la recarga incremental de datos.

> **NOTA**
> 
> Estas optimizaciones son necesarias tanto para las bases locales como para las bases del servidor.


### ¡Halar para refrescar!

Del lado de la aplicación iOS, sus datos se actualizan cada vez que inicia su aplicación y cada vez que su aplicación se pone en primer plano, para obtener datos actualizados constantemente.

En uso normal, simplemente deslice hacia abajo desde cualquier formulario Lista para recargar sus datos.

Desde la configuración del iPhone, ahora puede reinicializar los datos de su aplicación y encontrar información sobre su aplicación.

> **NOTA**
> 
> As soon as the admin performs an important maintenance operation, they shall alert 4D for iOS app users that a Full reload is required: Recover by tag / Restoration / Compaction
