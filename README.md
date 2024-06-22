# **Expresiones en QGIS**


En **[QGIS](https://www.qgis.org/es/site/)**, las expresiones son una herramienta poderosa utilizada para realizar cálculos y operaciones lógicas sobre datos geoespaciales. Se emplean en diversos contextos, tales como la simbología de capas, el etiquetado de características, la creación de campos calculados, la filtración de datos y la realización de análisis geoespaciales. Las expresiones en **QGIS** son similares a las fórmulas en programas de hoja de cálculo y se componen de funciones, operadores y referencias a campos de datos. Su sintaxis es similar a la de otras suites GIS (GvSIG, SuperMap, MapInfo, Manifold, _ArcGI$_, etc).    
<br />
<br />
<br />

## **COMPONENTES DE LAS EXPRESIONES EN QGIS** ✨🧮</h1>

### 1. Campos y Atributos:
Los campos de las capas vectoriales pueden ser utilizados en las expresiones para acceder a los valores de los atributos.
> Ejemplo: "population" > 10000
<br />

### 2. Funciones:
QGIS ofrece una amplia variedad de funciones integradas que permiten realizar cálculos matemáticos, operaciones de texto, manipulación de fechas, análisis geoespaciales y más.
> Ejemplo: sqrt("area") (calcula la raíz cuadrada del valor del campo "area").
<br />

### 3. Operadores:  
Los operadores se utilizan para realizar operaciones matemáticas (+, -, *, /), comparaciones (=, >, <, >=, <=, !=, ||), y operaciones lógicas (AND, OR, NOT).
> Ejemplo: "population" > 10000 AND "area" < 5000
<br />

### 4. Valores Literales:
Números, cadenas de texto y fechas pueden ser usados directamente en las expresiones.
> Ejemplo: 'Hello' || ' ' || 'World' (concatena las cadenas de texto).
<br />

### 5. Funciones Geoespaciales:
**QGIS** incluye funciones específicas para trabajar con geometrías, como cálculos de área, longitud, intersecciones, buffers, etc.
> Ejemplo: area($geometry) (calcula el área de la geometría de una característica).
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

