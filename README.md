# Excel a Anki con UiPath (proyecto histórico)

Automatización de escritorio creada como ejercicio de aprendizaje de **UiPath**. Lee vocabulario de un libro Excel y crea tarjetas en **Anki 2.1.40** mediante interacciones con su interfaz gráfica.

El usuario elige el idioma de destino, la primera y última fila que quiere procesar y una etiqueta. El robot busca la columna del idioma, recorre el intervalo y añade tarjetas con el texto en español y su traducción. Omite parejas en las que alguno de los valores está vacío o contiene exactamente `-`.

> **Estado:** proyecto antiguo, conservado como ejemplo educativo. No se ha verificado su ejecución en versiones actuales de UiPath o Anki. El repositorio contiene el flujo `Fill_Anki_Cards.xaml`, pero `project.json` apunta a `Main.xaml`, archivo que no está incluido. Por tanto, no se puede asumir que el proyecto funcione directamente al abrirlo y ejecutarlo.

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
