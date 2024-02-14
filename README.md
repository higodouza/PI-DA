# <h1 align=center> **PROYECTO INDIVIDUAL Nº2** </h1>

# <h1 align=center>**`Data Analytics`**</h1>


## **Presentacion e Introduccion**

Con el objetivo de reducir las lamentables tasas de mortalidad por siniestros viales en la Ciudad Autónoma de Buenos Aires, se presenta un análisis exhaustivo de la base de datos de accidentes de tránsito ocurridos entre los años 2016 y 2021. Este estudio busca identificar patrones, comprender las causas y desarrollar estrategias para prevenir futuros accidentes.

Para tal fin fue importante establecer ciertos objetivos y analizar sus respectivos indicadores de rendimiento (KPIs) planteados.

Se utilizo Python y Pandas para los procesos de extracción, transformación y carga de los datos, como así también para el análisis exploratorio de los datos. En los siguiente apartados se describen los resultados de los analisis revisados, como tambien se presenta [aca](https://github.com/higodouza/PI-DA/blob/main/Dash-PIDA.pbix) un dashboard que resumen las variables estudiadas junto sus relaciones con cada uno de los KPIs estudiados.

## **Manejo de la data - ETL y EDA**

Se realizó un proceso de extracción, transformación y carga de los datos (ETL) y un análisis exploratorio exahustivo ([EDA](https://github.com/higodouza/PI-DA/blob/main/EDA.ipynb)), primero para los datos de "HECHOS" y luego para los de "VÍCTIMAS", donde se estandarizaron nombres de las variables, se analizaron nulos y duplicados de los registros, se eliminaron columnas redundantes o con muchos valores faltantes, entre otras tareas. Una vez finalizado este proceso para los dos conjuntos de datos de "Homicidios" se genero un dataframe 'df_hechos' concatenado, que fue luego exportado en formato csv juntos con los dataset de los KPIs. 

Adicional a la data brindada, se importo un dataset que contenia la [población anual por comuna](`https://www.estadisticaciudad.gob.ar/eyc/?p=28146`), el cual fue extraído de la página oficial del gobierno, para realizar la comparacion poblacional solicitada en el proyecto.

## **Analisis de los KPIs planteados**

- `OBJETIVO 1`:
    Reducir en un 10% la tasa de homicidios en siniestros viales de los últimos seis meses, en CABA, en comparación con la tasa de homicidios en siniestros viales del semestre anterior.
    - `KPI 1`: Se define la tasa de homicidios en siniestros viales como el número de víctimas fatales en accidentes de tránsito por cada 100,000 habitantes en un área geográfica durante un período de tiempo específico.
    - `FORMULA 1`: (Número de homicidios en siniestros viales / Población total) * 100,000
    - `CORECCIÓN FORMULA 1`: (porcentaje de variación): {[[(Número de homicidios en siniestros viales `del semestre anterior` / Población total `del semestre anterior`) * 100,000] - [(Número defxfsddf homicidios en siniestros viales `del semestre actual` / Población total `del semestre actual`) * 100,000]] / [(Número de homicidios en siniestros viales `del semestre anterior` / Población total `del semestre anterior`) * 100,000]} * 100<br>
    <br>
- `OBJETIVO 2`:
    Reducir en un 7% la cantidad de accidentes mortales de motociclistas en el último año, en CABA, respecto al año anterior
    - `KPI 2`: Se define la cantidad de accidentes mortales de motociclistas en siniestros viales como el número absoluto de accidentes fatales en los que estuvieron involucradas víctimas que viajaban en moto en un determinado periodo temporal.
    - `FORMULA 2` (porcentaje de variación): [(Número de accidentes mortales con víctimas en moto en el año anterior - Número de accidentes mortales con víctimas en moto en el año actual) / (Número de accidentes mortales con víctimas en moto en el año anterior)] * 100.<br>
    <br>
- `OBJETIVO 3`:
    Reducir en un 5% el número de accidentes mortales en el ultimo semestre en CABA, ocasionados por el mayor responsable de siniestros viales del ultimo semestre, respecto al mismo responsable en el semestre anterior.
    - `KPI 3`: Se define la cantidad de accidentes mortales ocasionado por el mayor responsable de homicidios en siniestros viales del ultimo semestre como el número absoluto de accidentes fatales causados por el mayor responsable de siniestros viales del ultimo semestre en un determinado periodo temporal. 
    - `FORMULA 3` (porcentaje de variación): {(número de accidentes mortales ocasionados por el mayor responsable de siniestros viales del ultimo semestre en el semestre anterior - número de accidentes mortales ocasionados por el mayor responsable de siniestros viales del ultimo semestre en el semestre actual) / (número de accidentes mortales ocasionados por el mayor responsable de siniestros viales del ultimo semestre en el semestre anterior)} * 100.

## **Analisis de campos utiles**

Las graficas que detallan todas estas conclusiones se presentan en el [EDA](https://github.com/higodouza/PI-DA/blob/main/EDA.ipynb) anteriormente presentado:

**N_VICTIMAS**

- Solamente hay 3 posibilidades de victimas por accidente: 1, 2, 3
- La media del número de víctimas es aproximadamente 1.03, lo que sugiere que, en promedio, la mayoría de los accidentes tienen alrededor de una víctima.
- Dado que el 75% de los valores están en el primer cuartil, esto significa que el 75% de los accidentes tienen 1 víctima, y el segundo y tercer cuartiles son también 1. El valor máximo en el cuartil (75%) es 3, lo que indica que el 25% restante de los accidentes tiene 2 o 3 víctimas.
- Mayor frecuencia de numero de víctimas por accidente: 1 (97.13%)
- Menor frecuencia de numero de víctimas por accidente: 3 (0.14%)

**VICTIMA**

- Hay 10 tipos diferentes de víctimas involucradas.
- El valor más frecuente es "MOTO". Esto significa que "MOTO" es el tipo de víctima más común en los accidentes registrados.
- la frecuencia del tipo de víctima más común ("MOTO") es 295. Esto significa que hubo 295 accidentes en los que estuvieron involucradas motocicletas como víctimas.
- Victima con mayor frecuencia en accidentes: "MOTO" (42.39%)
- Victima con menor frecuencia en accidentes: "PEATON_MOTO" (0.14 %)

**ACUSADO**

- Hay 10 valores únicos en la columna "ACUSADO". Esto significa que existen 10 tipos diferentes de entidades o vehículos acusados en los accidentes registrados.
- El valor más frecuente en la columna "ACUSADO" es "AUTO". Esto significa que "AUTO" es el tipo de entidad o vehículo más comúnmente acusado en los accidentes registrados en el DataFrame.
- Indica que la frecuencia del tipo de entidad o vehículo más comúnmente acusado ("AUTO") es 204. Esto significa que hubo 204 accidentes en los que se acusó a un automóvil como la entidad responsable.
- Acusado con mayor frecuencia de accidentes: AUTO (29.31 %)
- Acusado con menor frecuencia de accidentes: TREN (0.14 %)

**AAAA (anio)**

- Hay 6 años únicos diferentes en la columna "AAAA", desde 2016 hasta 2021.
- (Cuartiles): Estos valores representan los cuartiles del conjunto de datos. Por ejemplo, el valor del primer cuartil (25%) es 2017, lo que significa que el 25% de los accidentes ocurrieron en 2017 o antes. El segundo cuartil (50%) es 2018, que es la mediana, indicando que el 50% de los accidentes ocurrieron en 2018 o antes. El tercer cuartil (75%) es 2020, lo que sugiere que el 75% de los accidentes ocurrieron en 2020 o antes.
- Año con mayor frecuencia de accidentes: 2016 (20.69%)
- Año con menor frecuencia de accidentes: 2020 (11.21%)


## **Resumen de la data a utilizar para cada KPI**

- KPI 1: Tasa de homicidios en siniestros viales
    - Semestre anterior
    - Número homicidios semestre anterior
    - Poblacion total en el semestre anterior
    - Semestre actual
    - Número homicidios semestre actual
    - Poblacion total en el semestre actual<br>
    <br>
- KPI 2: Cantidad de accidentes mortales de motociclistas en siniestros viales
    - Victima = MOTO
    - Año anterior
    - Número accidentes año anterior
    - Año actual
    - Número accidentes año actual<br>
    <br>
- KPI 3: Cantidad de accidentes mortales ocasionado por el mayor responsable de homicidios en siniestros viales del ultimo semestre
    - Mayor responsable de accidentes
    - Semestre anterior
    - Número accidentes semestre anterior
    - Semestre actual
    - Número accidentes semestre actual<br>


### **KPI 1:** Tasa de homicidios en siniestros viales


1. Dado que no tenemos datos previos al año 2016-1 nuestra primer medida relaciona el semestre `2016-1` y `2016-2` por eso solo se evidencian valores a partir del semestre `2016-2`.<br>

2. Si el valor del semestre en la gráfica es positivo significa que para ese semestre hubo ``menos homicidios`` que el semestre pasado.<br>

3. Si la gráfica tiene pendiente positiva (creciente) significa que la ``diferencia de accidentes de motos`` vs. el semestre anterior ``aumentó de manera positiva``.<br>

4. El valor que se representa en la gráfica indica el porcentaje en que se redujo la ``tasa de homicidios en accidentes de tránsito`` del semestre anterior vs. el actual. Dado que el objetivo es que dicho valor sea ``superior al 10%`` se puede concluir que en el periodo de 6 años comprendido entre 2016 y 2021 se cumplió para los semestres:

    - 2017-1: En comparación con el semestre anterior se ``redujeron`` los homicidios y ese numero fue ``mayor`` que el logrado el semestre anterior.<br>

    - 2019-1: En comparación con el semestre anterior se ``redujeron`` los homicidios y ese numero fue ``mayor`` que el logrado el semestre anterior.<br>

    - 2019-2: En comparación con el semestre anterior se ``redujeron`` los homicidios y ese numero fue ``menor`` que el logrado el semestre anterior.<br>
    
    - 2021-2: En comparación con el semestre anterior se ``redujeron`` los homicidios y ese numero fue ``mayor`` que el logrado el semestre anterior.

5. 4 semestres de 11 cumplieron el objetivo lo cual nos indica que ``no es positivo el balance`` de acuerdo a lo planteado inicialmente

6. 5 semestres de 11 tienen un porcentaje de cambio negativo, es decir, aumenta la tasa de homicidios vs. el semestre anterior. Aunque es minoría sigue siendo alarmante la cantidad

### **KPI 2:** Cantidad de accidentes mortales de motociclistas en siniestros viales

1. Dado que no tenemos datos previos al año 2016 nuestra primer medida relaciona el año `2016` y `2017` por eso solo se evidencian valores a partir del año `2017`.<br>

2. Si el valor del año en la gráfica es positivo significa que para ese año hubo ``menos homicidios`` que el año pasado.<br>

3. Si la gráfica tiene pendiente positiva (creciente) significa que la ``diferencia de accidentes de motos`` vs. el año anterior ``aumentó de manera positiva``.<br>

4. El valor que se representa en la gráfica indica el porcentaje en que se redujo la ``cantidad de homicidios en accidentes de motos`` del año anterior vs. el actual. Dado que el objetivo es que dicho valor sea ``superior al 7%`` se puede concluir que en el periodo de 6 años comprendido entre 2016 y 2021 se cumplió para los semestres:

    - 2017: En comparación con el año anterior se ``redujeron`` los homicidios y dado que no tenemos valores para el año anterior no podemos decir si fue mayor o menor respecto de ese año.<br>

    - 2019: En comparación con el año anterior se ``redujeron`` los homicidios y ese numero fue ``mayor`` que el logrado el año anterior.<br>

    - 2020: En comparación con el año anterior se ``redujeron`` los homicidios y ese numero fue ``mayor`` que el logrado el año anterior.<br>

5. 3 años de 5 cumplieron el objetivo lo cual nos indica que ``es positivo el balance`` de acuerdo a lo planteado inicialmente

6. 2 años de 5 tienen un porcentaje de cambio negativo, es decir, aumenta la tasa de accidentes en moto vs. el año anterior. Aunque es minoría sigue siendo alarmante la cantidad

### **KPI 3:** Cantidad de accidentes mortales ocasionado por el mayor responsable de homicidios en siniestros viales del ultimo semestre

1. El mayor responsable de accidentes de tránsito del último semestre (2021-2) es el ``auto`` por está razón de realiza todo el análisis para este acusado.

2. Dado que no tenemos datos previos al año 2016 nuestra primer medida relaciona el semestre `2016_1` y `2016_2` por eso solo se evidencian valores a partir del semestre `2016_2`.<br>

3. Si el valor del semestre en la gráfica es positivo significa que para ese semestre hubo ``menos accidentes ocasionados por autos`` que el semestre pasado.<br>

4. Si la gráfica tiene pendiente positiva (creciente) significa que la ``diferencia de accidentes ocasionados por autos`` vs. el semestre anterior ``aumentó de manera positiva``.<br>

5. El valor que se representa en la gráfica indica el porcentaje en que se redujo la ``cantidad de accidentes causados por autos`` del semestre anterior vs. el actual. Dado que el objetivo es que dicho valor sea ``superior al 5%`` se puede concluir que en el periodo de 6 años comprendido entre 2016 y 2021 se cumplió para los semestres:

    - 2017_2: Se ``reducen`` los accidentes causados por autos vs. el semestre anterior. Dicha diferencia es mayor que la del semestre pasado..<br>

    - 2019_2: Se ``reducen`` los accidentes causados por autos vs. el semestre anterior. Dicha diferencia es mayor que la del semestre pasado.<br>

    - 2020_1: Se ``reducen`` los accidentes causados por autos vs. el semestre anterior. Dicha diferencia es menor que la del semestre pasado.<br>

    - 2021_1: Se ``reducen`` los accidentes causados por autos vs. el semestre anterior. Dicha diferencia es mayor que la del semestre pasado.

6. 4 semestres de 11 cumplieron el objetivo lo cual nos indica que ``no es positivo el balance`` de acuerdo a lo planteado inicialmente

7. 5 semestres de 11 tienen un porcentaje de cambio negativo, es decir, aumentan los accidentes ocasionados vs. el semestre anterior. Aunque es minoría sigue siendo alarmante la cantidad