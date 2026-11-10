# Funcionamiento del flujo

Fuente principal: [Fill_Anki_Cards.xaml](../Fill_Anki_Cards.xaml).

## Secuencia

1. Abre `MemoWords.xlsx` con `Excel Application Scope` y lee la hoja `Todos los idiomas` como tabla, con encabezados.
2. Solicita el nombre del idioma. Una actividad `Find` de **BalaReva.EasyExcel** busca el texto del idioma en `A1:Z1` y obtiene la columna correspondiente.
3. Solicita las filas de inicio y fin y la etiqueta de las tarjetas.
4. Comprueba si está abierta una ventana de Anki identificada como `Usuario 1 - Anki`. Si la encuentra, pulsa `Cerrar` antes de abrir Anki.
5. Abre `anki.exe`, entra en la opción `Añadir` y selecciona un mazo cuyo nombre coincide con el idioma solicitado.
6. Recorre las filas leídas del Excel. Procesa únicamente las filas entre los límites indicados, ambos incluidos. Como la tabla tiene encabezado, convierte el índice interno a fila de Excel mediante `indexFila + 2`.
7. Para cada fila, lee la palabra española y la traducción; descarta la pareja cuando cualquiera es cadena vacía o exactamente `-`.
8. En las filas válidas, introduce ambos textos, escribe la etiqueta y pulsa `Añadir`.
9. Al terminar, muestra el mensaje `El programa ha finalizado con éxito.`

## Datos y variables principales

| Variable | Uso |
| --- | --- |
| `idioma` | Idioma solicitado; se usa para buscar la columna y seleccionar el mazo de Anki |
| `FilaInicio` y `FilaFin` | Intervalo de filas a procesar |
| `etiqueta` | Etiqueta escrita en las tarjetas |
| `tablaIdiomas` | Datos leídos de la hoja Excel |
| `columnaIdioma` | Columna devuelta por la búsqueda del encabezado |
| `palabraEspañola` y `palabraExtranjera` | Campos de cada tarjeta |
| `indexFila` | Índice de la fila que recorre el robot |

## Detalles relevantes

- El flujo **lee la palabra española desde la columna B**, mediante `"B" & (indexFila + 2).ToString`. Esto contradice la descripción antigua del README, que situaba el español en A. Antes de usar otro libro, hay que comprobar el formato real y no dar por válida esa descripción.
- La columna de destino se busca en la primera fila con coincidencia parcial y sin distinguir mayúsculas/minúsculas. El resultado se utiliza sin una comprobación explícita de búsqueda vacía.
- La selección del mazo se hace a través de la interfaz de Anki, no creando mazos de forma programática.
- La selección del mazo aparece condicionada a que el índice coincida con la primera fila del intervalo. Si esa fila se descarta por estar vacía, podría no ejecutarse la selección prevista.
- El filtro solo compara con `""` y `"-"`; no equivale a una limpieza general de espacios o errores de Excel.
- El aviso final no constituye una verificación independiente del número de tarjetas creadas.

## Tecnologías

UiPath Studio 21.4.0.0, proyecto **Legacy** con expresiones Visual Basic. Dependencias declaradas: `BalaReva.EasyExcel.Activities [28.1.2]`, `UiPath.Excel.Activities [2.10.3-preview]`, `UiPath.Mail.Activities [1.10.3-preview]`, `UiPath.System.Activities [21.4.0-preview]` y `UiPath.UIAutomation.Activities [21.4.1-preview]`.

No se ha encontrado en el flujo un uso que justifique afirmar que todas las dependencias declaradas son imprescindibles.
