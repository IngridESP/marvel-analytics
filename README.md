# Marvel Analytics

**Análisis de personajes y superpoderes con Python y Power BI**
**Ingrid Espinel**

Soy fan de las películas y series de Marvel y quería explorar con datos algunas preguntas que me surgían al verlas y además a partir de ahora las veré con una perspectiva más amplia. 
¿Quien es realmente el personaje más poderoso?, ¿Cuántos poderes tiene cada personaje?, ¿Qué poderes aparecen con más frecuencia?, ¿Son más poderosos los personajes masculinos o femeninos?, ¿cual es la distribución entre héroes, villanos y personajes neutrales?, ¿Son los villanos tan fuertes como parece?, ¿Qué raza destaca más?...


## ⚡ Cómo fue evolucionando el proyecto

| Etapa | Trabajo realizado |
|---|---|
| Python y Jupyter | Exploración y limpieza inicial de los CSV de personajes y poderes. Filtré Marvel Comics, traté los marcadores de datos faltantes, uní los archivos por nombre y calculé un primer recuento de poderes. También preparé gráficos exploratorios, exportaciones CSV y un prototipo de buscador. |
| Power BI Desktop | Refiné el análisis y el diseño durante la construcción del informe. Incorporé medidas y columnas, agrupé el número de poderes en tres niveles y en intervalos de cinco, y añadí comparativas por bando, género y personaje. |

El notebook conserva los resultados exploratorios. Su salida guardada muestra 388 filas de Marvel, de las cuales 341 encontraron una coincidencia por nombre en la tabla de poderes. En esa etapa, la suma inicial puede dar cero para las filas sin coincidencia, por lo que ese valor requiere distinguir ausencia de registro de ausencia de poderes. En el informe final la muestra es de 151 personajes en la vista general. Los hallazgos de esta página se refieren al informe de Power BI.

## 🎯 Cómo seleccioné la muestra

Elegí 151 personajes priorizando los más reconocibles para quienes conocen Marvel por sus películas y series. El catálogo de los cómics es mucho más amplio. Acoté la muestra para que el informe fuera fácil de explorar para ese público, además para que resultara más atractivo y divertido de ver. Los resultados describen esta selección.

## 🗂️ Los cuatro CSV del modelo

Durante el EDA generé 18 CSV para probar distintos análisis y visualizaciones. En Power BI consolidé el modelo alrededor de cuatro CSV principales y conecté la información mediante relaciones, medidas y tablas creadas dentro del informe. Así reduje la repetición de datos entre las exportaciones.

| CSV principal | Uso en el informe |
|---|---|
| `marvel_buscador` | Datos de personajes y poderes que sirven de base al buscador y a cálculos del informe. |
| `marvel_heroes_clean` | Atributos de los personajes, como género, raza y bando, y base para el recuento de poderes por personaje. |
| `marvel_powers_long` | Poderes en formato largo para analizar su frecuencia y compararlos entre grupos. |
| `marvel_dc_jerarquia` | Jerarquía de editorial, universo y personaje para el árbol de contexto. |

En Power BI también preparé las tablas auxiliares `base_heatmap`, `correlacion_poderes`, `matriz_correlaciones` y `top_12_poderes`.

## 📊 Páginas del informe

| Página | Qué puedes explorar |
|---|---|
| Contexto editoriales | Árbol que permite recorrer editorial, universo y personaje. Incluye Marvel y DC como contexto. |
| Marvel general | Composición de la muestra por bando, género y raza. |
| Mapa de poderes | Frecuencia de poderes, ranking de personajes y promedios por raza. |
| Comparativa de poderes | Matriz de correlaciones, comparación entre héroes y villanos, niveles por bando e histograma. |
| Mujeres vs. hombres | Distribución por género y exploración de poderes frecuentes y poco frecuentes. |
| Mujeres poderosas | Rankings femeninos general y por bando, y composición por raza. |
| Buscador interactivo | Selección y comparación de personajes mediante el recuento de poderes y sus atributos. |
| Conclusiones | Síntesis de los resultados del informe. |

## 🔎 Hallazgos generales

- En la vista general, 102 personajes (68%) están clasificados como héroes, 39 (26%) como villanos y 10 (7%) como neutrales.
- La razas mas comunes son humanos y mutantes que juntas suman el 51% del total de personajes.
- El personaje Living Tribunal encabeza el ranking general con 35 poderes registrados. Captain Marvel es el segundo personaje más poderoso de todos, además de liderar el ranking femenino con 33 poderes.
- El poder de Super fuerza lo tienen 107 personajes, resistencia 98 y durabilidad 86, son los poderes más frecuentes. La inteligencia destaca en el ranking femenino y en el masculino no aparece dentro del top 10.
- Los poderes relacionados con fuerza, resistencia y velocidad tienen una mayor relación positiva, tienden a combinarse más.
- El intervalo más frecuente de poderes es de 6 a 10 poderes, con 50 de 151 personajes,el 33% del total.En segundo lugar el intervalo de 11 a 15 reúne a otros 38 personajes, el 25% de la muestra.
- El 10% de heroes y el 10% de villanos solamente, se encuentran en el nivel más altos de poder (21 a 35 poderes). Del grupo neutral el 40 % está en el nivel Alto.


Los rankings se basan en el número de poderes registrados en la muestra. Las categorías y los nombres proceden del dataset utilizado.

## 🛠️ Tecnologías utilizadas

Utilicé **Python** y **Jupiter Notebook** para explorar y limpiar datos. Para preparar los archivos CSV y las primeras visualizaciones, **Pandas**, **Numpy** y **Matpltlib**. Con **ipywidgets** cree un prototipo inicial del buscador de personajes. En **Power BI Desktop** con **Power Query**, prepare los datos, contruí el modelo y utilice **DAX** para calcular indicadores, porcentajes, rankings.En el informe final incorporé filtros, comparativas y un buscador interactivo.

## 🛠️ Retos superados

Uno de los retos fue pasar de 18 csv exploratorios a 4 archivos principales para hacer el modelado final. Para poder conseguirlo, hice la relación de las tablas en Power BI y trasladé la mayoría de los calculos al modelo. Otro reto fue hacer que el buscador sirviera tanto para consultar la ficha de un personaje como para comparar varios a la vez. Con DAX consegui que la ficha solo mostrara datos cuando hay un único personaje seleccionado, sin solapar información y para evitar confusiones, mientras el gráfico permite comparar los poderes de todos los personajes seleccionados. 



## 📦 Archivos y ejecución

- `Marvel_Analytics.pbix` contiene el informe final. Ábrelo con Power BI Desktop. Para actualizar los datos, revisa las conexiones de origen en Power Query y vuelve a enlazarlas con tus archivos locales.
- `marvel_eda_ylimpieza.ipynb` contiene el análisis exploratorio original, EDA. Usa Python con pandas, NumPy, Matplotlib e ipywidgets. Coloca `heroes_information.csv` y `super_hero_powers.csv` en el directorio de trabajo del notebook. Instala ipywidgets en el entorno de Jupyter y omite la celda de instalación escrita como comando de terminal si ejecutas el notebook completo como Python.

## Fuentes y créditos

- Fuente de los datos originales — [Super Heroes Dataset, ClaudioDavi (Kaggle)](https://www.kaggle.com/datasets/claudiodavi/superhero-set). Los archivos de entrada son `heroes_information.csv` (734 filas, 11 columnas) y `super_hero_powers.csv` (667 filas, 168 columnas).

**Autora: Ingrid Espinel.**