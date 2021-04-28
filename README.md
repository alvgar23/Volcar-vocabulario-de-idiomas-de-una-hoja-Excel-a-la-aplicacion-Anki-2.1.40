# Volcar-vocabulario-de-idiomas-de-una-hoja-Excel-a-la-aplicacion-Anki-2.1.40
UIPATH - Nivel principiante. 

Anki es una aplicación para ordenador que contiene tarjetas de memoria. Es muy útil para almacenar vocabulario de idiomas. Puedes crear un mazo que contenga un idioma concreto, y dentro de él, incluir una lista de vocabulario organizado por etiquetas, que bien podrían ser adjetivos, verbos, familia, comida..., y traducirla a nuestro idioma nativo. La aplicación es una herramienta muy útil para memorizar palabras, pero por desgracia no tenemos mucho tiempo para introducir las palabras.

Contamos con un Excel que contiene una lista de palabras en castellano ordenadas por etiquetas (columna A) traducida a varios idiomas: Ruso (Columna B), Polaco (Columna C), Alemán (Columna D), Francés (Columna E), Inglés (Columna F), Italiano (Columna G) y Portugués (Columna H). Esta lista está incompleta para algunos idiomas (celdas en blanco o con un guión).

Quería crear un robot con la herramienta Uipath que introduciendo por teclado el idioma y la etiqueta, la celda de inicio y la celda de fin, volcara automáticamente todas las palabras incluidas en ese rango a la aplicación Anki.

Es mi primer ejercicio libre con Uipath, por esta razón no uso herramientas avanzadas, sino básicas, y lo he utilizado a modo de práctoica. El robot cumple su función, aunque probablemente el código no esté todo lo optimizado que uno desearía.

Algunos problemas son que en caso de que queramos elegir otro documento, debemos cambiarlo manualmente en el código. Por otra parte, la nueva hoja excel tendría que tener este mismo formato (lengua origen en columna A, lengua destino debe coincidir con las anteriormente mencionadas). Con lo cual, el código no es del todo dinámico.

Es necesario tener la versión 2.1.40 de Anki instalada en el ordenador.

Tal vez en el futuro mejore este código, por el momento cumple la función que buscaba, ya que pretendía aplicarlo con mi hoja de Excel específica.

Cualquier persona que lo desee puede copiar el código y utilizarlo como práctica o para uso personal
