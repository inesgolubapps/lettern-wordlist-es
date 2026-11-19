# Fuentes, versiones y licencias

Estado 2026-11-19 · listas `es-2026-11-18+sha256:16d5db0b3673` · fuentes del 2026-11-18

Cada archivo de las fuentes se fijó por su suma SHA-256; quien construya las listas con los mismos
archivos y las mismas versiones de las herramientas, reglas, parámetros y listas de revisión obtiene,
byte por byte, los mismos datos. Las citas de las licencias se leyeron en la fuente
indicada.

## Fuentes que entran en las listas

### 1. Wiktionary en inglés, entradas en español (kaikki.org / wiktextract)

- Archivo: `enwiktionary-Spanish.jsonl.gz`
- URL: https://kaikki.org/dictionary/Spanish/kaikki.org-dictionary-Spanish.jsonl.gz
- Versión: volcado de enwiktionary del 2026-10-01, extraído el 2026-10-30
- SHA-256: `b25cd18584e510c516e4c9afac42a87e5acfd6bc1a13ea96a94057899521a427`
- Licencia: CC BY-SA 4.0 y GFDL. Wikimedia: “dual-licensed … under both the Creative Commons
  Attribution-ShareAlike 4.0 International License … and the GNU Free Documentation License”
  (https://en.wiktionary.org/wiki/Wiktionary:Copyrights). kaikki.org: “This data is made available under
  the same licenses as Wiktionary - both CC-BY-SA and GFDL.”
- Uso: lemas, categorías, formas (conjugación, plural, femenino, voseo), marcas de registro y de región.

### 2. Wiktionary en español (Wikcionario), entradas «Español» (kaikki.org / wiktextract)

- Archivo: `eswiktionary-Espanol.jsonl.gz`
- URL: https://kaikki.org/eswiktionary/Espa%C3%B1ol/kaikki.org-dictionary-Espa%C3%B1ol.jsonl.gz
- Versión: volcado de eswiktionary del 2026-11-01, extraído el 2026-11-02 con wiktextract 19f9a30
- SHA-256: `e43c811b3c7eca0955db41efd978dfb94435694055ea7f23433a5d0e6d878777`
- Licencia: Wikcionario, pie de cada página: “El texto está disponible bajo la Licencia Creative Commons
  Atribución-CompartirIgual 4.0.” kaikki.org: “This data is made available under the same licenses as
  Wiktionary - both CC-BY-SA and GFDL.”
- Uso: segunda opinión sobre lemas y formas, marcas como «malsonante», «despectivo», «en desuso» y la
  región de cada acepción.

kaikki.org y wiktextract: Tatu Ylonen, “Wiktextract: Wiktionary as Machine-Readable Structured Data”,
LREC 2022, pp. 1317-1325.

### 3. wordfreq (Robyn Speer), español `large`

- Paquete: wordfreq 3.1.1, wheel SHA-256 `4b1c6ecffc6198be3396d5cf871c4423ca71c907c231348d352dd54d62b97473`
- Archivo de datos: `wordfreq/data/large_es.msgpack.gz`, SHA-256
  `14f326b4f68d517f9b8b99c1e26ef56a508d2dc8d0ee7a9e6e8732ddab1aa65e`
- Licencia: “`wordfreq` is freely redistributable under the Apache license (see `LICENSE.txt`), and it
  includes data files that may be redistributed under a Creative Commons Attribution-ShareAlike 4.0
  license” (https://github.com/rspeer/wordfreq#license). Datos de Google Books Ngrams: “may be freely used
  for any purpose, although acknowledgement of Google Books Ngram Viewer as the source, and inclusion of a
  link to http://books.google.com/ngrams, would be appreciated.” OpenSubtitles 2018 vía OPUS: “may be used
  with attribution to OpenSubtitles.” La lista española se basa en Wikipedia, subtítulos, noticias,
  libros, web, Twitter y Reddit; no contiene SUBTLEX.
- Uso: la frecuencia de cada forma (columna `zipf`), los umbrales del vocabulario de solución y la
  ortografía visible cuando varias grafías dan la misma forma.

### 4. FrequencyWords (Hermit Dave), `es_full.txt`

- Archivo: `frequencywords-es_full.txt`
- URL: https://raw.githubusercontent.com/hermitdave/FrequencyWords/525f9b560de45753a5ea01069454e72e9aa541c6/content/2018/es/es_full.txt
- Versión: git 525f9b5 (2022-02-07), contenido OpenSubtitles 2018
- SHA-256: `b4794c425f3500c21a0ff9367175e36795a978c928a36670e9ad6ae206fb7728`
- Licencia: “MIT License for code. CC-by-sa-4.0 for content.” (https://github.com/hermitdave/FrequencyWords)
- Uso: solo segunda señal: desempate de la ortografía visible.

## Fuente solo al construir (no forma parte de los datos)

### 5. LDNOOBW, español

- Archivo: `ldnoobw-es.txt`
- URL: https://raw.githubusercontent.com/LDNOOBW/List-of-Dirty-Naughty-Obscene-and-Otherwise-Bad-Words/5faf2ba42d7b1c0977169ec3611df25a3c08eb13/es
- Versión: git 5faf2ba (2020-07-13)
- SHA-256: `073334261cc2e7c08339faefd2f19f9623e8240a0ac18fe2a26c368b897496ce`
- Licencia: “This work is licensed under a Creative Commons Attribution 4.0 International License”,
  “© 2012–2020 Shutterstock, Inc.”
- Uso: solo marca de revisión de palabras ofensivas; no bloquea nada por sí misma y no se publica.

## No utilizadas

Los diccionarios Hunspell del español (RLA-ES y derivados: solo GPL/LGPL/MPL), las listas oficiales de
Scrabble, el diccionario de la RAE y SUBTLEX-ESP no se usan, tampoco como filtro.
