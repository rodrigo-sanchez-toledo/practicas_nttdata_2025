README breve — Ejercicio 1: Tipo de contenido "Event" con taxonomía "Event category"
Este primer ejercicio consistió en preparar un contenido “Event” con sus campos 
y una taxonomía para categorizarlo. Empecé creando el vocabulario en Estructura → Taxonomía, 
lo llamé "Event category" con nombre de máquina event_category y le añadí algunos 
términos básicos como "Party" y "Webinar" para tener algo con lo que probar.

Luego pasé a Estructura → Tipos de contenido y creé el tipo "Event" (event). 
Mantuve los campos base (Title y Body) y, desde Manage fields, añadí "Description" como texto (usé texto largo) 
con nombre teaser_description, "Start date" como campo de fecha (start_date), "Image" como referencia a Media 
limitada al tipo de media Imagen (image) y "Category" como referencia a término de taxonomía apuntando al vocabulario 
que acabábamos de crear (event_category). Para la visualización, en Manage display ordené los campos 
de forma natural (título, fecha, imagen, categoría, descripción, body), escogí un formato de fecha sencillo y un estilo de imagen medio. 

Finalmente, exporté la configuración con un ddev drush cex.

Este es el Ejercicio 1. Si añadimos más ejercicios, los iremos listando a continuación con el mismo formato.




Ejercicios 3:

Objetivo: que los eventos tengan URLs tipo /event/nombre-del-evento y quitar palabras como “of”, “the” y “and”.

Módulos usados:

Token
Pathauto
Instalación y activación:
composer require drupal/token drupal/pathauto

Patrón de alias para Event:
Ir a Configuración > Búsqueda y metadatos > URL aliases > Patterns (/admin/config/search/path/patterns).
Crear un patrón para “Content” limitado al tipo “Event (event)” con:
/event/[node:title]

Quitar palabras del alias:
Ir a Configuración > Búsqueda y metadatos > URL aliases > Settings (/admin/config/search/path/settings).
Añadir las palabras a String to Remove

Resultado esperado:
Un título “The Best of Rock and Roll” genera /event/best-rock-roll.

Regenerar alias existentes (opcional):
/admin/config/search/path/update_bulk → filtrar por “Event” → Regenerate URL aliases.

Exportar configuración:
drush cex