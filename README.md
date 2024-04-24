# PI-Data
## Proyecto Individual #2
## Bootcamp Data Science - Henry
## *Daniel Andrés Bossio Pérez - DataFT21*
#1. ETL + EDA
Archivo principal: [PIData-EDA](PIData-EDA.ipynb)<br>
Se proporcionó un archivo excel ([homicidios.xlsx](datasets_origen/homicidios.xlsx)) con dos hojas: una para los hechos que constituyen homicidio por siniestro vial, y otro para las víctimas de los mismos.<br>
*Para los homicidios:*
- Se leyó el archivo con pandas.read_excel.
- Se revisaron los nulos y duplicados: el archivo no contenía duplicados, pero muchas de las columnas sí contenían nulos y valores que pueden ser tomados como tal, como SD para varias columnas categóricas y un punto (.) en las columnas latitud y longitud.
- En el caso de las columnas de geolocalización, se intentó realizar una imputación usando la librería geocoder.
- En la columna dirección, se exploró la posibilidad de usar los valores de otras columnas relacionadas, como nombre de la calle, avenida, etc.
- En los demás casos, dado que la información proporcionada no era concluyente sobre una forma eficaz para imputar nulos, y que los datos son pocos y los registros con nulos en alguna columna solían contener información en otra, no se eliminaron.
- Se convirtieron las columnas a formatos adecuados y se exportaron los datos<br>
*Para las víctimas:*
- Se leyó el archivo con pandas.read_excel.
- Se revisaron los nulos y duplicados: el archivo no contenía duplicados, pero muchas de las columnas sí contenían nulos y valores que pueden ser tomados como tal, como SD para varias columnas categóricas.
- Dado que la información proporcionada no era concluyente sobre una forma eficaz para imputar nulos, y que los datos son pocos y los registros con nulos en alguna columna solían contener información en otra, no se eliminaron.
- Se convirtieron las columnas a formatos adecuados y se exportaron los datos<br>
Además se consultaron algunos otros datos disponibles:
- Observaciones de factores de riesgo vial ([autos](datasets_origen/base_obs_autos_2022.xlsx), [motos](base_obs_motos_2022.xlsx)): Estos archivos contienen los resultados de los estudios observacionales de factores de riesgo vial llevados a cabo por el Observatorio de Movilidad y Seguridad Vial en el año 2022. Se enfocan en aspectos como las distracciones al conducir, uso del cinturón/casco e implementacion de medidas de protección adecuadas. En ambos casos se realizó una revisión de nulos, imputación de datos geográficos faltantes y mapeo de valores según lo indicado en el archivo [diccionario_obs](datasets_origen/diccionario_obs_2022.xlsx).
- Archivo geojson de las comunas de Argentina ([comunas](datasets_origen/comunas.geojson)), usado en el EDA para asociar patrones relacionados con las comunas.
- Flujo vehicular ([flujo_vehicular](datasets_origen/dataset_flujo_vehicular.xlsx)): Resumen del flujo vehicular registrado por 7 sensores. Debido a que se consideró que no brindarían información aplicable a toda la ciudad, no se utilizó esta información en el dashboard en Power BI, aunque se hizo su análisis en el EDA.
#2. Archivos
Los datasets procesados están en la carpeta [datasets](datasets). Se tiene un archivo csv y un volcado de base de datos MySQL para cada uno de los siguientes conjuntos de datos: homicidios, víctimas, observaciones de seguridad para autos y para motos.
#3. Dashboard y KPIs
Archivo principal: [PI-Data.pbix](PI-Data.pbix)
<br>En cuanto al análisis de los datos, puede destacarse que:
- Hay más víctimas de hechos en los años 2016, 2017 y 2018 que en 2019, 2020 y 2021. Por otra parte, hay un pico en Diciembre de 2020.
- Las comunas con más hechos registrados son la 1 y la 4.
- Una parte considerable de las víctimas tenía entre 20 y 40 años al momento del hecho.
- La mayoría de víctimas de estos hechos son hombres.
- Asimismo, la mayoría era el conductor del vehículo.
- Aunque el máximo de días de diferencia entre la fecha del hecho y el fallecimiento de la víctima es 27, la mayoría de víctimas murió hasta 2 días después.
- Por un gran margen, la mayoría de distracciones encontradas son con el celular.<br>
**Tasa de homicidios semestral**
<br>En resumen, los semestres en los que la reducción de la tasa de homicidios fue de 10% fueron 2017-1, 2019-1, 2019-2, 2020-1 y 2021-2. Además, en 2018-1 hubo disminución, pero no tan notablemente.
![image](https://github.com/DanielBossio/PI-Data/assets/51429745/7193f0a6-2787-4650-9684-ef60bae157e9)<br>
**Tasa de accidentes de motociclistas**
<br>Los años en los que la tasa de accidentes de motociclistas bajó al menos un 7% fueron 2017, 2019 y 2020.
![image](https://github.com/DanielBossio/PI-Data/assets/51429745/792152db-ebaf-4d6e-838b-e0ab8cc8f6ee)<br>
**Tasa de accidentes de menores de edad y ancianos**
<br>Los semestres en los que la tasa de accidentes de menores de edad y ancianos bajó al menos un 7% fueron 2017-1, 2019-1, 2019-2, 2020-1 y 2021-2.<br>
![image](https://github.com/DanielBossio/PI-Data/assets/51429745/8af27e41-27c1-4b04-8b23-9d87f7890dac)
