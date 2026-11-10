# Preparación, ejecución y limitaciones

Esta guía describe la **configuración original**. No se ha probado una instalación nueva.

## Antes de ejecutar

1. Utilizar un entorno Windows con UiPath Studio compatible con el proyecto **Legacy** y sus paquetes antiguos.
2. Instalar Anki **2.1.40**, versión para la que se diseñaron los selectores de interfaz.
3. Revisar el libro `MemoWords.xlsx` y su hoja `Todos los idiomas`. Los encabezados de idiomas deben encontrarse en la fila 1; el flujo busca entre A y Z.
4. Comprobar qué columna contiene el español: el código actual lee la **B**, aunque el README original decía **A**.
5. Crear previamente en Anki un mazo cuyo nombre coincida con el idioma elegido; la automatización intenta seleccionarlo, no crearlo.
6. Revisar y adaptar las rutas locales codificadas en el XAML: el ámbito principal usa `MemoWords.xlsx` como ruta relativa, pero el ámbito BalaReva usa una **ruta absoluta de un ordenador antiguo**. La apertura de Anki también depende de `C:\Program Files\Anki\anki.exe`.
7. Resolver la discrepancia del punto de entrada: `project.json` declara `Main.xaml`, que **no está en el repositorio**. El único flujo disponible es `Fill_Anki_Cards.xaml`. Será necesario abrirlo o configurar un punto de entrada válido en UiPath.

## Datos que solicita

- Idioma: nombre del encabezado y del mazo de Anki; debe coincidir con los nombres utilizados.
- Fila de inicio y fila de fin: números de fila de Excel, incluidos ambos extremos.
- Etiqueta: texto para clasificar las tarjetas; el propio flujo indica que puede dejarse vacío.

Se recomienda probar primero con **dos o tres filas** y un mazo de prueba. No hay en el código una comprobación final de tarjetas creadas ni una estrategia de recuperación documentada.

## Limitaciones conocidas

| Área | Situación |
| --- | --- |
| Portabilidad | Rutas locales fijas en el XAML |
| Arranque | Falta `Main.xaml`, aunque figura como entrada en `project.json` |
| Excel | Nombre de hoja fijo, encabezados en fila 1, columna B fija para español |
| Anki | Selectores de ventanas en español y controles con índices concretos; sensibles a cambios de versión o interfaz |
| Perfil de Anki | Busca una ventana con el título `Usuario 1 - Anki` |
| Calidad de datos | Omite vacíos y guiones exactos, sin validación avanzada |
| Duplicados | No se comprueba si una tarjeta ya existe |
| Confirmación | El mensaje de éxito no comprueba el resultado en Anki |
| Compatibilidad | No hay pruebas de ejecución actuales ni garantía de compatibilidad con versiones nuevas |

## Posibles mejoras futuras (no implementadas)

Parametrizar las rutas, corregir el punto de entrada, validar columnas y rangos, registrar cuántas tarjetas se añaden o descartan y evitar duplicados. Otra alternativa sería generar un archivo de importación para Anki en lugar de depender de clics y selectores de la interfaz.

Son ideas de evolución, **no capacidades del proyecto actual**.
