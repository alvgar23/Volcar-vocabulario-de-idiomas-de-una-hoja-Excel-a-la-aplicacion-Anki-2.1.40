# Excel a Anki con UiPath (proyecto histórico)

Automatización de escritorio creada como ejercicio de aprendizaje de **UiPath**. Lee vocabulario de un libro Excel y crea tarjetas en **Anki 2.1.40** mediante interacciones con su interfaz gráfica.

El usuario elige el idioma de destino, la primera y última fila que quiere procesar y una etiqueta. El robot busca la columna del idioma, recorre el intervalo y añade tarjetas con el texto en español y su traducción. Omite parejas en las que alguno de los valores está vacío o contiene exactamente `-`.

> **Estado:** proyecto antiguo, conservado como ejemplo educativo. No se ha verificado su ejecución en versiones actuales de UiPath o Anki. El repositorio contiene el flujo `Fill_Anki_Cards.xaml`, pero `project.json` apunta a `Main.xaml`, archivo que no está incluido. Por tanto, no se puede asumir que el proyecto funcione directamente al abrirlo y ejecutarlo.

## Por qué nació este proyecto

Este fue mi **primer ejercicio libre con UiPath**. Quería practicar lo aprendido construyendo algo que me resultara útil, sin recurrir a actividades especialmente avanzadas ni intentar crear una solución genérica.

Utilizaba **Anki** para memorizar vocabulario de idiomas mediante tarjetas. Tenía una hoja Excel con palabras en español y sus traducciones a varios idiomas, organizadas por categorías que podían convertirse en etiquetas de Anki: verbos, adjetivos, familia, comida, etc. Introducir esas tarjetas manualmente llevaba tiempo, así que decidí automatizar la tarea.

El Excel original reunía vocabulario de **ruso, polaco, alemán, francés, inglés, italiano y portugués**. Algunas traducciones estaban pendientes, representadas por celdas vacías o guiones. La idea era indicar al robot un idioma, una etiqueta y un intervalo de filas para que trasladara las palabras disponibles a Anki.

El objetivo no era desarrollar un producto universal, sino **resolver una necesidad personal mientras aprendía UiPath**. Por eso la implementación utiliza herramientas básicas, depende del formato de mi Excel y tiene limitaciones de portabilidad. Cumplía la función para la que la creé, aunque era consciente de que podía optimizarse.

El código se compartió también para que otras personas pudieran consultarlo, copiarlo y utilizarlo como práctica o para uso personal.

## Archivos

- `Fill_Anki_Cards.xaml`: flujo de automatización y reglas de lectura/escritura.
- `MemoWords.xlsx`: libro de vocabulario utilizado por el proyecto.
- `project.json`: dependencias y configuración original de UiPath Studio.
- `settings-*.json`: ajustes exportados del entorno UiPath.

## Documentación

- [Funcionamiento del robot](docs/funcionamiento.md)
- [Preparación, ejecución y limitaciones](docs/uso-y-limitaciones.md)

## Alcance

La solución automatiza la interfaz de Anki; **no** usa una API ni genera directamente archivos de importación de Anki. Está ligada a la estructura del Excel, a la instalación local de Anki y a controles concretos de su interfaz.

Este repositorio documenta la implementación original, no una versión modernizada.
