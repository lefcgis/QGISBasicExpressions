# <h1> Expresiones en QGIS  😃🎁 </h1>

![Calculadora de expresiones](https://farm66.static.flickr.com/65535/51114788190_480db1aef0.jpg).


En **[QGIS](https://www.qgis.org/es/site/)**, las expresiones son una herramienta poderosa utilizada para realizar cálculos y operaciones lógicas sobre datos geoespaciales. Se emplean en diversos contextos, tales como la simbología de capas, el etiquetado de características, la creación de campos calculados, la filtración de datos y la realización de análisis geoespaciales. Las expresiones en **QGIS** son similares a las fórmulas en programas de hoja de cálculo y se componen de funciones, operadores y referencias a campos de datos. Su sintaxis es similar a la de otras suites GIS (GvSIG, SuperMap, MapInfo, Manifold, _ArcGI$_, etc).  
<br />

**Lucho Ferrer 👨‍💻 - Asociación QGIS Perú**
<br />
<br />
<br />
<br />
<br />

## **COMPONENTES DE LAS EXPRESIONES EN QGIS** ✨🧮</h1>

### 1. Campos y Atributos:
Los campos de las capas vectoriales pueden ser utilizados en las expresiones para acceder a los valores de los atributos.
> Ejemplo: "total_poblacion" > 10000  
> _Aquí indicamos que en el campo de total de población queremos la que supere el atributo **mayor a** 10000._
<br />

### 2. Funciones:
QGIS ofrece una amplia variedad de funciones integradas que permiten realizar cálculos matemáticos, operaciones de texto, manipulación de fechas, análisis geoespaciales y más.
> Ejemplo: sqrt("area")  
> _Calcula la **raíz cuadrada** del valor del campo "area" con la Función "sqrt"._
<br />

### 3. Operadores:  
Los operadores se utilizan para realizar operaciones matemáticas (+, -, *, /), comparaciones (=, >, <, >=, <=, !=, ||), y operaciones lógicas (AND, OR, NOT).
> Ejemplo: "total_poblacion" > 10000 AND "area" < 5000  
> _El operador **AND** nos permite interactuar entre diferentes campos para obtener resultados específicos._
<br />

### 4. Valores Literales:
Números, cadenas de texto y fechas pueden ser usados directamente en las expresiones.
> Ejemplo: 'Hello' || ' ' || 'World'.  
> _Concatena las dos cadenas de texto._
<br />

### 5. Funciones Geoespaciales:
**QGIS** incluye funciones específicas para trabajar con geometrías, como cálculos de área, longitud, intersecciones, buffers, etc.
> Ejemplo: area($geometry)  
> _Calcula el área de la geometría de una característica._
<br />
<br />
<br />
<br />

## **¿Cómo Utilizar las Expresiones en QGIS?** ✨🏆</h1>

### Calculadora de Campos.  
Abre la calculadora de campos desde el menú de atributos o el panel de atributos y usa expresiones para crear nuevos campos o actualizar existentes.

### Constructor de Expresiones.  
El constructor de expresiones en QGIS se puede abrir en varios diálogos, como el de filtrado de capa, simbología, etiquetado y expresiones de análisis. Proporciona una interfaz para escribir y probar expresiones.

### Filtros y Selecciones:  
Utiliza expresiones en la barra de filtros de atributos para seleccionar subconjuntos de datos.
<br />
<br />
<br />
<br />


## **Top 10 de expresiones** ✨🏆</h1>

### I. Números correlativos
Nos permite asignar un número único correlativo ascendente (vale decir, ordenará nuestra información con un campo y valor único).  
Función:
> @row_number
<br />

### II. Latitud / Norte
Calcula el valor Latitud / Norte de una coordenada (de acuerdo al SRC en que se encuentre la capa geoespacial), en geometrías tipo punto.  
Función:
> $y
<br />

### III. Longitud / Este
Calcula el valor Longitud / Estede una coordenada (de acuerdo al SRC en que se encuentre la capa geoespacial), en geometrías tipo punto.  
Función:
> $x
<br />

### IV. Áreas:
Calcula la dimensión del área de una geometría tipo poligonal, estimado en **metros cuadrados**.  
Función:
> $area
<br />

### V. Áreas (km2):
Calcula la dimensión del área de una geometría tipo poligonal, estimado en **kilómetros cuadrados**.  
Función:
> $area / 1000000
<br />

### VI. Hectáreas:
Calcula la dimensión del **área** de una geometría tipo poligonal, estimado en **hectáreas**.  
Función:
> $area/10000
<br />

### VII. Perímetro:
Calcula la dimensión del **perímetro** de una geometría tipo poligonal.  
Función:
> $perimeter
<br />

### VIII. Distancias:
Calcula la **distancia** de una geometría tipo lineal.  
Función:
> $lenght
<br />

### IX. Actualizar fecha y hora
Nos brinda la fecha y la hora actual (tiempo real) de la edición  de una capa geoespacial.  
Función:
> now()
<br />

### X. Concatenar campos
Utilizamos la combinación de una serie de campos con información textual para construir una nueva información más detallada.  
Ejemplo:
> '¡Ladra!, soy Lucho Ferrer y trabajo con ' **||** "name__software_libre" **||** 'Únete y sé parte de mi #QGISarmy. Abraza la fé y ponle pausa a '' **||** "names_software_pagado" ''

