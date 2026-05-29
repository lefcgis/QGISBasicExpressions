<!-- ===================== ENCABEZADO ===================== -->
<div align="center">

# 🐤 Expresiones con QGIS — Guía del Pollito 😃🎁

### *Top 10 de expresiones clave (¡y un poco más!) para dominar QGIS*

[![QGIS](https://img.shields.io/badge/QGIS-3.x-589632?style=flat-square&logo=qgis&logoColor=white)](https://www.qgis.org/es/site/)
[![Licencia](https://img.shields.io/badge/Licencia-GPL--3.0-blue?style=flat-square)](./LICENSE)
[![Idioma](https://img.shields.io/badge/Idioma-Español-red?style=flat-square)]()
[![Nivel](https://img.shields.io/badge/Nivel-🐤_Pollito-yellow?style=flat-square)]()
[![Comunidad](https://img.shields.io/badge/Asociación-QGIS_Perú-orange?style=flat-square)]()

*Hecho con 🤘 por **Lucho Ferrer 👨‍💻** — Asociación QGIS Perú*

</div>

---

> 🐤 **¿Eres pollito en QGIS?** Tranquilo. Esta guía está escrita para que **cualquiera** entienda las expresiones desde cero, paso a paso, sin tecnicismos innecesarios. Si ya eres gallo de pelea, salta directo al [Top 10](#-top-10-de-expresiones-).

<!-- ===================== TABLA DE CONTENIDOS ===================== -->
## 📑 Tabla de contenidos

1. [¿Qué es una expresión en QGIS?](#-qué-es-una-expresión-en-qgis)
2. [Componentes de una expresión](#-componentes-de-una-expresión)
3. [¿Dónde y cómo se usan? (paso a paso)](#-dónde-y-cómo-se-usan-las-expresiones)
4. [🏆 Top 10 de expresiones](#-top-10-de-expresiones-)
5. [🎁 Bonus: 10 expresiones extra para tu mochila](#-bonus-expresiones-extra-para-tu-mochila)
6. [⚠️ Errores típicos del pollito](#️-errores-típicos-del-pollito-y-cómo-evitarlos)
7. [📖 Glosario pollito](#-glosario-pollito)
8. [💡 Tips de oro](#-tips-de-oro)
9. [🔗 Recursos para seguir aprendiendo](#-recursos-para-seguir-aprendiendo)
10. [👨‍💻 Sobre el autor y la comunidad](#-sobre-el-autor-y-la-comunidad)

---

<!-- ===================== QUÉ ES ===================== -->
## 🧠 ¿Qué es una expresión en QGIS?

En **[QGIS](https://www.qgis.org/es/site/)**, una **expresión** es una pequeña "fórmula" que le da instrucciones al programa para **calcular** o **decidir** algo sobre tus datos geoespaciales.

> 🐤 **Analogía pollito:** una expresión es como una **receta de cocina**.
> Le dices a QGIS *"toma estos ingredientes (campos), hazles esto (funciones y operadores) y dame este plato (un resultado)"*. El resultado puede ser un número, un texto, una fecha o hasta una geometría.

Las expresiones se parecen muchísimo a las **fórmulas de Excel** (esas que empiezan con `=`). Si alguna vez escribiste `=SUMA(A1:A10)`, ya tienes medio camino recorrido. 🎉

Se usan para muchísimas cosas:

| Para qué sirven | Ejemplo de uso |
| :-- | :-- |
| 🎨 **Simbología** | Pintar de rojo los predios con área > 5000 m² |
| 🏷️ **Etiquetado** | Mostrar el nombre + la población de cada distrito |
| 🧮 **Campos calculados** | Crear un campo nuevo con el área en hectáreas |
| 🔍 **Filtros / selecciones** | Mostrar solo las capas con población > 10 000 |
| 🌐 **Análisis geoespacial** | Calcular distancias, áreas, intersecciones, buffers |

> 💡 La sintaxis de las expresiones de QGIS es muy parecida a la de otras suites GIS (GvSIG, SuperMap, MapInfo, Manifold, *ArcGI$*, etc.), así que lo que aprendas aquí te servirá en otros lados.

---

<!-- ===================== COMPONENTES ===================== -->
## 🧩 Componentes de una expresión

Toda expresión se arma con **5 piezas de Lego**. Conócelas y ya nada te detiene:

### 1️⃣ Campos y atributos
Son las **columnas** de tu tabla de atributos. Se escriben **entre comillas dobles** `" "`.

```sql
"total_poblacion" > 10000
```
> 🐤 *Traducción pollito:* "dame las filas donde el campo **total_poblacion** sea **mayor a** 10 000".

### 2️⃣ Funciones
Son **herramientas que ya vienen listas** en QGIS para calcular cosas (matemáticas, texto, fechas, geometría…). Siempre llevan **paréntesis** `( )`.

```sql
sqrt("area")
```
> 🐤 *Traducción pollito:* calcula la **raíz cuadrada** del valor del campo "area".

### 3️⃣ Operadores
Son los **símbolos** que conectan piezas.

| Tipo | Operadores |
| :-- | :-- |
| Matemáticos | `+`  `-`  `*`  `/` |
| Comparación | `=`  `>`  `<`  `>=`  `<=`  `!=` |
| Lógicos | `AND`  `OR`  `NOT` |
| Concatenación (unir textos) | `\|\|` |

```sql
"total_poblacion" > 10000 AND "area" < 5000
```
> 🐤 *Traducción pollito:* el operador **AND** exige que se cumplan **las dos condiciones a la vez**.

### 4️⃣ Valores literales
Son valores que escribes **directamente**: números, textos (entre comillas **simples** `' '`) y fechas.

```sql
'Hola' || ' ' || 'Mundo'
```
> 🐤 *Traducción pollito:* une (concatena) los tres pedacitos de texto → `Hola Mundo`.

> ⚠️ **¡Ojo, pollito!** Comillas **dobles** `" "` = **campos**. Comillas **simples** `' '` = **texto**. Confundirlas es el error #1 de todos.

### 5️⃣ Funciones geoespaciales
Funciones especiales para trabajar con **geometrías**: área, longitud, intersecciones, buffers, etc.

```sql
area($geometry)
```
> 🐤 *Traducción pollito:* calcula el **área** de la geometría de cada elemento.

---

<!-- ===================== DÓNDE Y CÓMO ===================== -->
## 🛠️ ¿Dónde y cómo se usan las expresiones?

Hay **3 lugares principales** donde escribirás expresiones. Aquí te los explico paso a paso:

### 🧮 A) Calculadora de campos
Sirve para **crear un campo nuevo** o **actualizar uno existente**.

1. Selecciona tu capa.
2. Abre la **tabla de atributos** (`F6` o clic derecho → *Abrir tabla de atributos*).
3. Clic en el ícono del **ábaco** 🧮 (*Abrir calculadora de campos*) o presiona `Ctrl + I`.
4. Marca **"Crear un campo nuevo"**, ponle nombre y tipo.
5. Escribe tu expresión y presiona **Aceptar**. ✅

### 🏗️ B) Constructor de expresiones
Es la **ventana** donde escribes y **pruebas** expresiones. Aparece en muchos diálogos: filtrado de capa, simbología, etiquetado, análisis, etc.

> 💡 Tiene un buscador de funciones a la izquierda y un panel de **vista previa** abajo que te dice si tu expresión funciona **antes** de aplicarla. ¡Úsalo siempre!

### 🔍 C) Filtros y selecciones
Sirve para **mostrar solo una parte** de tus datos.

- Clic derecho en la capa → **Filtrar…** (`Query Builder`), o
- Usa el botón de **selección por expresión** en la barra de herramientas.

---

<!-- ===================== TOP 10 ===================== -->
## 🏆 Top 10 de expresiones ✨

> 🐤 **Resumen para que lo pegues en tu monitor:**

| # | Para qué sirve | Expresión | Tipo de geometría |
| :-: | :-- | :-- | :-- |
| I | Numerar filas (correlativo) | `@row_number` | Cualquiera |
| II | Latitud / Norte | `$y` | Punto |
| III | Longitud / Este | `$x` | Punto |
| IV | Área en **m²** | `$area` | Polígono |
| V | Área en **km²** | `$area / 1000000` | Polígono |
| VI | Área en **hectáreas** | `$area / 10000` | Polígono |
| VII | Perímetro | `$perimeter` | Polígono |
| VIII | Distancia / longitud | `$length` | Línea |
| IX | Fecha y hora actual | `now()` | Cualquiera |
| X | Concatenar campos | `"campo1" \|\| "campo2"` | Cualquiera |

Ahora el detalle de cada una 👇

### I. 🔢 Números correlativos
Asigna un número **único ascendente** a cada fila (ideal para ordenar o crear un ID).
```sql
@row_number
```

### II. 🧭 Latitud / Norte
Devuelve la coordenada **Y** (Latitud o Norte, según el SRC de la capa) de geometrías tipo **punto**.
```sql
$y
```

### III. 🧭 Longitud / Este
Devuelve la coordenada **X** (Longitud o Este, según el SRC de la capa) de geometrías tipo **punto**.
```sql
$x
```

### IV. 🟦 Área (m²)
Calcula el área de un **polígono**, en **metros cuadrados**.
```sql
$area
```

### V. 🗺️ Área (km²)
La misma área, pero convertida a **kilómetros cuadrados** (dividimos entre 1 000 000).
```sql
$area / 1000000
```

### VI. 🌳 Área (hectáreas)
La misma área, pero en **hectáreas** (dividimos entre 10 000). Muy usada en temas ambientales y catastrales.
```sql
$area / 10000
```

### VII. 📏 Perímetro
Calcula el **perímetro** (el borde) de un polígono.
```sql
$perimeter
```

### VIII. 📐 Distancias / Longitud
Calcula la **longitud** de una geometría tipo **línea**.
```sql
$length
```
> ✅ **Corrección importante:** la función correcta es `$length` (con **g**), no `$lenght`. Es un error de tipeo súper común. 🐤

### IX. ⏰ Actualizar fecha y hora
Devuelve la **fecha y hora actual** (tiempo real) en el momento de editar la capa.
```sql
now()
```

### X. 🔗 Concatenar campos
Une varios campos de texto para construir información más rica. Usa el operador `||`.
```sql
'¡Ladra!, soy Lucho Ferrer y trabajo con ' || "software_libre" || '. Únete a mi #QGISarmy 🤘'
```
> 🐤 *Traducción pollito:* mezcla texto fijo (entre comillas simples) con el contenido de un campo (entre comillas dobles) para armar una frase personalizada por cada fila.

---

<!-- ===================== BONUS ===================== -->
## 🎁 Bonus: expresiones extra para tu mochila

El Top 10 te hace caminar. Estas 10 te hacen **volar** 🦅. Todas son nivel pollito.

### 1. `concat()` — concatenar sin miedo a los nulos
```sql
concat("nombre", ' - ', "distrito")
```
> 💡 A diferencia de `||`, la función `concat()` **ignora los valores vacíos (NULL)** en lugar de devolver vacío. Más segura.

### 2. `coalesce()` — rellenar campos vacíos
```sql
coalesce("poblacion", 0)
```
> 🐤 Si el campo está vacío (NULL), devuelve `0`. Adiós a los huecos en tus datos.

### 3. `round()` — redondear decimales
```sql
round($area / 10000, 2)
```
> Área en hectáreas con solo **2 decimales**. Más limpio para mostrar.

### 4. `format_number()` — números bonitos con separador de miles
```sql
format_number("poblacion", 0)
```
> Convierte `1234567` en `1,234,567`. Ideal para etiquetas.

### 5. `if()` — decisiones simples
```sql
if("poblacion" > 10000, 'Grande', 'Pequeño')
```
> 🐤 *Si* la población es mayor a 10 000 → "Grande"; *si no* → "Pequeño".

### 6. `CASE WHEN` — decisiones con varias opciones
```sql
CASE
  WHEN "poblacion" > 100000 THEN 'Ciudad'
  WHEN "poblacion" > 10000  THEN 'Pueblo'
  ELSE 'Caserío'
END
```
> El hermano mayor del `if()`, perfecto para clasificar en categorías.

### 7. `upper()` / `lower()` / `title()` — manejar texto
```sql
title("nombre_distrito")
```
> `upper` → TODO MAYÚSCULAS · `lower` → todo minúsculas · `title` → Primera Letra En Mayúscula.

### 8. `x()` / `y()` con centroides — coordenadas de polígonos
```sql
x(centroid($geometry))
```
> 🐤 `$x` y `$y` solo funcionan bien en **puntos**. Para sacar la coordenada del **centro de un polígono**, usa `centroid()` primero.

### 9. `area(transform(...))` — área correcta aunque tu capa esté en grados
```sql
area(transform($geometry, 'EPSG:4326', 'EPSG:32718'))
```
> 🌎 Reproyecta la geometría a **UTM Zona 18S** (Perú) para obtener metros cuadrados reales. (Ver la sección de errores más abajo 👇)

### 10. `@layer_name` y `@map_scale` — variables útiles
```sql
'Capa: ' || @layer_name || ' | Escala: 1:' || @map_scale
```
> Variables que te dan info del proyecto. Útiles en composiciones de mapas (layouts).

---

<!-- ===================== ERRORES ===================== -->
## ⚠️ Errores típicos del pollito (y cómo evitarlos)

| 🐣 El error | 😖 Qué pasa | ✅ La solución |
| :-- | :-- | :-- |
| Usar `'comillas simples'` en un campo | QGIS lo lee como texto literal, no como columna | Campos = `"comillas dobles"` |
| Escribir `$lenght` | No existe, da error | Es `$length` (con **g**) |
| Calcular `$area` con la capa en **grados (EPSG:4326)** | El "área" sale en grados² ¡absurda! | Reproyecta a un **SRC métrico** (UTM 19S = `EPSG:32718`) o usa `transform()` |
| Usar `$x` en un polígono | Devuelve `NULL` o error | Usa `x(centroid($geometry))` |
| Olvidar guardar la edición | El campo calculado se pierde | Clic en **Guardar capa** 💾 (`Ctrl + S`) |
| Concatenar con `\|\|` cuando hay nulos | Toda la frase se vuelve vacía | Usa `concat()` o `coalesce()` |

> 🌎 **Tip peruano:** la mayor parte del Perú cae en **UTM Zona 18S (`EPSG:32718`)** y la zona oriental en **19S (`EPSG:32719`)**. Trabaja siempre en un SRC métrico cuando midas áreas o distancias.

---

<!-- ===================== GLOSARIO ===================== -->
## 📖 Glosario pollito

| Palabra rara | Qué significa en cristiano |
| :-- | :-- |
| **SRC / CRS** | Sistema de Referencia de Coordenadas. El "idioma" en que QGIS ubica tus datos en el mundo (ej. WGS84, UTM 19S). |
| **Geometría** | La forma del dato: punto, línea o polígono. |
| **Campo / Atributo** | Una columna de la tabla de datos. |
| **Función** | Herramienta lista para usar, siempre con `( )`. |
| **Operador** | Símbolo que conecta cosas (`+`, `AND`, `\|\|`…). |
| **Literal** | Un valor escrito tal cual (un número, un texto, una fecha). |
| **NULL** | Un campo **vacío**, sin dato. |
| **Concatenar** | Pegar/unir textos uno tras otro. |
| **Centroide** | El punto central de un polígono. |
| **Buffer** | Una zona de influencia alrededor de una geometría. |

---

<!-- ===================== TIPS ===================== -->
## 💡 Tips de oro

- 🔎 **Usa la vista previa.** El constructor de expresiones te muestra el resultado **antes** de aplicar. Pruébalo siempre.
- 🧱 **Empieza simple.** Arma la expresión por partes y ve agregando piezas.
- 📚 **El buscador es tu amigo.** En el panel izquierdo del constructor encuentras **todas** las funciones con su descripción y ejemplo.
- 🌐 **Sintaxis nueva vs. antigua.** Las variables clásicas con `$` (como `$area`, `$x`) siguen funcionando, pero QGIS moderno también acepta funciones como `area(@geometry)` o `x(@geometry)`. Usa la que te resulte más clara.
- 💾 **Guarda seguido.** Después de calcular un campo, guarda la edición o lo perderás.

---

<!-- ===================== RECURSOS ===================== -->
## 🔗 Recursos para seguir aprendiendo

- 🌐 [QGIS — Sitio oficial en español](https://www.qgis.org/es/site/)
- 📘 [Documentación de expresiones de QGIS](https://docs.qgis.org/latest/es/docs/user_manual/expressions/expression.html)
- 🐍 [Lista completa de funciones de expresiones](https://docs.qgis.org/latest/es/docs/user_manual/expressions/functions_list.html)
- 🇵🇪 Comunidad **Asociación QGIS Perú** — únete al `#QGISarmy` 🤘

> *Si quieres seguir aprendiendo a crear expresiones o a diseñar mapas que impacten en tu público, inscríbete en los próximos cursos online de **El Laboratorio de Lucho**.*

---

<!-- ===================== AUTOR ===================== -->
## 👨‍💻 Sobre el autor y la comunidad

<div align="center">

**Lucho Ferrer** 🏋️‍♀️
*Asociación QGIS Perú · `#QGISarmy`*

[![GitHub](https://img.shields.io/badge/GitHub-lefcgis-181717?style=flat-square&logo=github)](https://github.com/lefcgis)

*"¡Ladra! Abraza la fé del software libre y ponle pausa al software pagado."* 🐶🤘

</div>

---

## 📜 Licencia

Este proyecto está bajo la licencia **[GPL-3.0](./LICENSE)**. Eres libre de usarlo, compartirlo y mejorarlo. 🎁

---

<div align="center">

⭐ **Si esta guía te sirvió, dale una estrella al repo y compártela con otro pollito.** ⭐

*Lucho Ferrer, a vuestros servicios* 🏋️‍♀️

</div>
