# Lista de palabras de Lettern (español)

Las listas de palabras y los datos de los pasatiempos del libro en español de **Lettern**, un pasatiempo
de palabras tranquilo para iPhone de Tickwork, abiertos bajo
[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.es).

Estado 2026-11-19 · listas `es-2026-11-18+sha256:16d5db0b3673` · Lettern 1.2.0 ·
el libro en alemán: <https://github.com/inesgolubapps/lettern-wortliste>

En Lettern arrastras el dedo sobre una rueda de letras para formar palabras y rellenar con ellas un
pequeño crucigrama. Qué palabras pide un pasatiempo y cuáles acepta como palabras extra está en este
repositorio, junto con cada página del libro y cada pasatiempo del día. Los datos proceden de fuentes
abiertas, entre ellas Wiktionary y wordfreq, y por eso están, como ellas, bajo CC BY-SA 4.0.

## Contenido

| Archivo | Contenido | Tamaño |
| --- | --- | --- |
| `data/ziel.tsv` | vocabulario de solución: palabras que un pasatiempo puede pedir, con ortografía, forma base, categoría y frecuencia | 9,723 formas en 15,254 filas |
| `data/bonus.tsv` | palabras aceptadas: cada forma que cuenta como palabra extra, con su ortografía | 598,574 formas |
| `data/levels.json` | el libro: cada página con sus fichas, cuadrícula, palabras de solución y extra | 640 páginas en 40 capítulos |
| `data/daily.json` | los pasatiempos del día, en el mismo formato | 420 pasatiempos |
| `curation/decisions.tsv` | registro de la revisión palabra por palabra: una fila por decisión, con su motivo | 11,199 filas |
| `curation/never-target.txt` | palabras válidas que nunca se piden, con el motivo | |
| `curation/always-target.txt` | palabras que son de solución aunque una regla las dejaría fuera | |
| `SOURCES.md` | cada fuente con versión, suma de comprobación y licencia | |
| `FORMAT.md` | las columnas y campos de cada archivo | |
| `LICENSE` | el texto legal de CC BY-SA 4.0 | |
| `VERSION`, `SHA256SUMS` | estado y sumas de comprobación de cada archivo | |

Los nombres de archivo (`ziel.tsv`, “ziel” = objetivo en alemán) y de columnas siguen el repositorio
alemán, para que las mismas herramientas lean ambos. Cómo se construyen está en [FORMAT.md](FORMAT.md).

## Qué palabras cuentan

- **Palabras de solución** son palabras de uso diario **en España y en América**, en su forma base o en
  una forma corriente como *casas* o *comió*. Solo ellas se piden. Los regionalismos, las formas de
  *vosotros* y de *vos* y los verbos con pronombre enclítico (*dame*) nunca se piden.
- **Palabras extra** son otras palabras de la lista de Lettern: formas españolas de Wiktionary de 3 a 10
  letras, también flexionadas, raras o regionales (*vosotros*, *vos*, *dame*), salvo las que filtramos
  (véase abajo). Se aceptan, nunca se piden.
- Las **fichas y la cuadrícula no llevan tilde ni diéresis**: la ficha A sirve para A y Á, la U para U y Ü.
  La **Ñ** es una letra propia con su propia ficha. La ortografía correcta, con tildes y diéresis, aparece
  donde se listan las palabras (tras “Resuelto.”) y al consultarlas.
- No cuentan los nombres propios, las abreviaturas, las palabras con apóstrofo, guion o espacio ni las de
  menos de tres letras. Las palabras malsonantes más fuertes y los insultos contra grupos no cuentan;
  algunas palabras con un sentido vulgar solo en ciertos países (*concha*, *coger*) y algunos insultos
  leves siguen valiendo como palabras extra, pero nunca se piden.

## Atribución

Los datos derivan de estas obras. Archivos, versiones y sumas de comprobación en [SOURCES.md](SOURCES.md).

1. **Wiktionary en español (Wikcionario)** – de las autoras y autores del Wiktionary en español,
   <https://es.wiktionary.org>, legible por máquina gracias a kaikki.org con wiktextract (Tatu Ylonen),
   <https://kaikki.org/eswiktionary/>. Licencia: CC BY-SA 4.0.
2. **Wiktionary en inglés, entradas en español** – de las autoras y autores del Wiktionary en inglés,
   <https://en.wiktionary.org>, vía kaikki.org / wiktextract, <https://kaikki.org/dictionary/Spanish/>.
   Licencia: CC BY-SA 4.0 (también GFDL; usamos CC BY-SA 4.0).
3. **wordfreq** – de Robyn Speer, <https://github.com/rspeer/wordfreq>. Licencia de los datos:
   CC BY-SA 4.0. Las frecuencias españolas incluyen subtítulos del proyecto **OpenSubtitles**
   (<http://www.opensubtitles.org/>) vía OPUS y el **Google Books Ngram Viewer**
   (<https://books.google.com/ngrams>), además de Wikipedia, noticias, web, Twitter y Reddit.
4. **FrequencyWords** – de Hermit Dave, <https://github.com/hermitdave/FrequencyWords>, recuentos de
   OpenSubtitles 2018. Licencia del contenido: CC BY-SA 4.0. Solo como segunda señal (ortografía visible).

Estas obras se ofrecen por sus autores tal cual; rige la limitación de responsabilidad de su licencia
(para CC BY-SA 4.0 la sección 5, véase [LICENSE](LICENSE)).

## Qué hemos cambiado

Los archivos se han elaborado a partir de las fuentes; indicamos a continuación los cambios realizados,
conforme a la sección 3(a)(1)(B) de la licencia:

- **Extraído.** De Wiktionary solo entradas del idioma español: lema, categoría, formas y marcas (vulgar,
  despectivo, anticuado, regional …). Sin definiciones.
- **Plegado.** Cada forma se escribe con las letras de las fichas: las vocales pierden la tilde o la
  diéresis (á é í ó ú ü → a e i o u), la ñ se queda. La ortografía real va en la columna `show`. Si varias grafías dan la misma forma (*esta*/*está*),
  es una sola forma, y `show` es la grafía elegida para mostrar la palabra: normalmente la más frecuente,
  salvo correcciones y decisiones de lectura.
- **Filtrado.** Fuera quedan nombres propios, abreviaturas, formas con apóstrofo, guion o espacio, y las
  palabras vulgares, ofensivas y sexuales más fuertes (véase “No incluido”); las de doble sentido solo
  regional quedan como palabras extra que nunca se piden.
- **Combinado.** La frecuencia de cada forma (columna `zipf`) viene de wordfreq.
- **Seleccionado por frecuencia.** Las palabras de solución son formas con un significado neutro y
  común en todo el mundo hispanohablante, por encima de un umbral de frecuencia.
- **Revisado.** Las formas de solución se revisaron una por una; lo que se quitó, añadió o corrigió está
  en `curation/`, con su motivo.
- **Pasatiempos generados.** `levels.json` y `daily.json` se generaron a partir de las listas con nuestro
  propio programa. Desde el capítulo 3, las palabras clave salen a menudo de nuestras propias listas de temas.

## Licencia

Los datos de este repositorio están bajo **Creative Commons Atribución-CompartirIgual 4.0 Internacional
(CC BY-SA 4.0)**: <https://creativecommons.org/licenses/by-sa/4.0/deed.es>. El texto legal completo está
en [LICENSE](LICENSE) (obtenido el 2026-10-01 de
<https://creativecommons.org/licenses/by-sa/4.0/legalcode.txt>).

Puedes copiar, modificar y compartir los datos, también con fines comerciales, siempre que cites a los
autores, indiques tus cambios y compartas tu versión bajo la misma licencia o una compatible.

## Reutilización

Esta línea cita a todos los autores y se puede copiar tal cual:

```
"Lista de palabras de Lettern (español)" de Tickwork, estado 2026-11-19, https://github.com/inesgolubapps/lettern-wordlist-es, bajo CC BY-SA 4.0 (https://creativecommons.org/licenses/by-sa/4.0/). Derivada de Wiktionary (autoras y autores del Wiktionary en español y en inglés, vía kaikki.org/wiktextract), wordfreq (Robyn Speer) con datos de OpenSubtitles y Google Books Ngram, y FrequencyWords (Hermit Dave), CC BY-SA 4.0.
```

Si has cambiado los datos, di qué has cambiado, por ejemplo “reducido a palabras de cinco letras”.

## Avisar de un error

¿Falta una palabra, está mal escrita o no encaja en un pasatiempo? Avísanos:

- como issue en este repositorio: <https://github.com/inesgolubapps/lettern-wordlist-es/issues>
- en la app: tras “Resuelto.” toca la palabra y avísanos
- por correo a inesgolubapps@gmail.com

Ayudan la palabra y, en un pasatiempo, el número de página o la fecha del pasatiempo del día. Las
correcciones llegan a la app y a este repositorio con una versión posterior.

## No incluido

- **El código.** El código de la app y las herramientas que construyen estos archivos no forman parte de
  este repositorio ni de la licencia. La licencia cubre los datos.
- **La lista de filtro.** Al construir las listas, otra lista aparta palabras vulgares, ofensivas y
  sexuales, a partir de Wiktionary y de una lista pública de palabras ofensivas (véase SOURCES.md). Esa
  lista no forma parte de los datos: no publicamos los archivos de filtro, ni aquí ni con la app. Los
  homónimos y las palabras de doble sentido que admitimos sí pueden aparecer en los datos. Por eso `curation/decisions.tsv` omite las 26
  filas que se refieren a ella.
- El nombre de la app, sus imágenes, sonidos, tipografías y textos.

## Sin garantía

Los datos se reunieron para un juego, no como diccionario ni corrector ortográfico. Se ofrecen tal cual,
sin garantía de exactitud o integridad; puede haber errores y entradas discutibles. Se excluye la
responsabilidad por su uso en la medida en que la ley lo permita (sección 5 de la licencia).
