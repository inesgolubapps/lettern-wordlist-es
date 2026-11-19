# Formatos de archivo

Estado 2026-11-19 · listas `es-2026-11-18+sha256:16d5db0b3673`

Todos los archivos están en UTF-8, en forma normal NFC, con saltos de línea LF. Los TSV tienen una fila
de cabecera y separan las columnas con un tabulador; no hay comillas ni escapes. Los decimales llevan
punto.

**Formas** (`form`, `lemma`, `w`, `leit`, `bonus`) se escriben en minúscula y **con las letras de las
fichas**: a–z y ñ. Las vocales pierden la tilde o la diéresis (*árbol* → `arbol`, *pingüino* →
`pinguino`); la ñ es una letra propia. La ortografía real, con tildes, está en `show`. Una forma de las
listas tiene de 3 a 10 letras. Orden: por letras, con la ñ como carácter propio tras la z (orden de
bytes UTF-8; la app ordena la cumbre con la ñ tras la n).

Los nombres de archivo y de columna vienen del repositorio alemán (`ziel` = objetivo,
`entscheidung` = decisión, `grund` = motivo), para que las mismas herramientas lean ambos.

## data/ziel.tsv — vocabulario de solución

Las palabras que un pasatiempo puede pedir. Una fila por **lectura**: una forma que pertenece a varias
formas base aparece varias veces. La primera fila de una forma es la lectura que el generador trata como
principal (forma base y categoría). La ortografía `show` es la misma en todas las filas de una forma: la
grafía más frecuente, salvo correcciones a mano (`récords`, `andén`). Filas ordenadas por `form`, dentro de una forma en ese orden.

| Columna | Contenido | Ejemplo |
| --- | --- | --- |
| `form` | la forma, con las letras de las fichas | `comio` |
| `show` | ortografía real, en minúscula, con tildes; igual en todas las filas de una forma | `comió` |
| `lemma` | forma base de esta lectura, con las letras de las fichas | `comer` |
| `pos` | categoría: `noun` sustantivo, `verb` verbo, `adj` adjetivo, `adv` adverbio, `pron` pronombre, `prep` preposición, `conj` conjunción, `num` numeral, `other` artículos y otras | `verb` |
| `zipf` | frecuencia de la forma en la escala Zipf, dos decimales: log10 de la suma de las frecuencias de todas sus grafías aceptadas (*esta* + *está*; puede incluir grafías mal escritas que caen en las mismas fichas) | `4.38` |

- **Zipf** es el logaritmo decimal de las apariciones por cada mil millones de palabras: 3 es una vez
  por millón, 6 una vez por mil. Los valores vienen de wordfreq. Algunas palabras están por debajo del
  umbral y son de solución porque una lista manual las añade (`curation/always-target.txt`).
- Un pasatiempo pide como mucho una forma por forma base.

9,723 formas en 15,254 filas; las primeras lecturas pertenecen a 6,207
formas base.

## data/bonus.tsv — palabras aceptadas

Cada forma que el juego acepta, con su ortografía. Todas las formas de `ziel.tsv` están aquí también.
Ordenado por `form`.

| Columna | Contenido | Ejemplo |
| --- | --- | --- |
| `form` | la forma | `arbol` |
| `show` | ortografía real (si varias grafías dan la misma forma, normalmente la más frecuente, salvo correcciones y decisiones de lectura) | `árbol` |

```
arbol	árbol
esta	esta
niño	niño
```

598,574 formas.

## data/levels.json, data/daily.json — pasatiempos

Ambos archivos tienen el mismo formato: un objeto JSON, una página por línea.

| Campo | Contenido |
| --- | --- |
| `v` | versión del formato, ahora `1` |
| `lang` | idioma del libro, `es` |
| `lexicon` | estado de las listas con que se generaron y comprobaron los pasatiempos (el mismo que `lexicon` en `VERSION`): `es-`, la fecha de las fuentes y parte de una suma de comprobación de las listas; no se puede recalcular desde este repositorio porque incluye la lista de filtro no publicada |
| `generator` | programa y versión que generaron los pasatiempos |
| `pages` | las páginas |

### Una página

| Campo | Contenido |
| --- | --- |
| `page` | número de página, 1–640 en el libro; en los pasatiempos del día, el número correlativo |
| `bogen` | capítulo 1–40, de 16 páginas; `0` en los pasatiempos del día |
| `kind` | `kreuz` (crucigrama) o `freisatz` (la cumbre: palabras sin cruces, en columnas) |
| `theme` | solo en el libro desde el capítulo 3: el tema del capítulo como identificador interno, p. ej. `garten` (los identificadores son alemanes; la app muestra un nombre en español) |
| `leit` | palabra clave: la palabra de solución que usa todas las fichas |
| `tiles` | las fichas de la rueda en su posición inicial, en el sentido de las agujas del reloj desde arriba: mayúsculas `A`–`Z` y `Ñ` |
| `cols`, `rows` | solo en `kreuz`: ancho y alto de la cuadrícula en casillas |
| `words` | las palabras de solución, véase abajo |
| `bonus` | las palabras extra: cada forma de la lista aceptada que se puede formar con las fichas y no es de solución en la página; completa y ordenada |
| `bonusShow` | ortografía de cada palabra extra, en la misma posición que en `bonus` |
| `difficulty` | medida de dificultad entre 0 y 1, tres decimales; solo para ordenar |
| `seed` | valor inicial del generador (hexadecimal) |

Una palabra de solución en `words`:

| Campo | Contenido |
| --- | --- |
| `w` | la forma |
| `show` | ortografía real, como la muestra la lista de palabras de “Resuelto.” (la cuadrícula muestra las letras de las fichas, sin tilde) |
| `r`, `c` | solo en `kreuz`: fila y columna de la primera letra, desde 0 arriba a la izquierda |
| `d` | solo en `kreuz`: dirección, `H` horizontal hacia la derecha, `V` vertical hacia abajo |

**Tildes:** la rueda y la cuadrícula muestran las letras de las fichas (mayúsculas sin tilde, `Ñ` como
letra propia); la ortografía con tilde (`show`, `bonusShow`) aparece donde se listan las palabras.

## curation/decisions.tsv — registro de la revisión

| Columna | Contenido |
| --- | --- |
| `form` | la forma |
| `entscheidung` | decisión: `ok` (sigue de solución), `ziel-nein` (válida, nunca se pide), `ziel-pflicht` (de solución aunque una regla la dejaría fuera) |
| `grund` | motivo, en alemán |
| `pass` | ronda de revisión |

11,199 filas; se omiten las 26 que afectan a la lista de filtro.

## curation/never-target.txt, curation/always-target.txt

Una forma por línea, `#` empieza un comentario con el motivo.
