# Proyecto de predicción de ventas y clasificación de productos en diferentes clúster, según diferentes características


<p align="center">
   <img align="center" width="200" src="https://raw.githubusercontent.com/Sergiochueco-94/DSmarket_cluster_y_prediction/main/img/DsMarket.PNG" />
</p>

 <p align="left">
   <img src="https://img.shields.io/badge/STATUS-EN%20DESAROLLO-green">
</p>

version https://git-lfs.github.com/spec/v1
oid sha256:7faffe61a084669fa5295aaca8150a5e89df0cc0acb9711bbd7cf2e0ddf7b592
size 5005

## Tecnologías utilizadas:

 - Python
 - Pandas
 - Numpy
 - XGBoost
 - KMEANS
 - Scikit-learn
 - Google Colab
 - Visual Studio Code
 - Jupyter Notebook
 - Git
 - Github


## Descripción proyecto

Partimos de una BBDD compuesta de 3 archivos csv:

- daily_calendar_with_events.csv
- item_sales.csv
- item_prices

De aquí generaremos varios archivos csv más para poder utilizar una presentación en Power BI.

Una vez explicado esto, en este proyecto se busca poder categorizar los productos en **diferentes grupos(clúster)** para poder identificar sus principales características y poder tomar mejores decisiones a nivel de negocio basándonos en esto.

Por otro lado, también se busca **predecir las ventas** de los 28 días siguientes a la última fecha.

Para poder conseguir todo esto, el proyecto se divide en varias partes:

1) Crear un único dataframe en el que poder recoger toda la información necesaria que contienen los 3 CSV distinto.

   Para esto se han utilizado varias técnicas como se puede observar en el código.
   También aclarar que en el dataframe final(df_semanal_fechas), se imputa el valor anterior o posterior (bfill, ffill) a los precios con nulos, asumiendo que es parecido a lo posterior/anterior, ya que hablamos de una semana de diferencia en la que el precio puede que no sea muy diferente.

   El archivo que se ha originado es df_final_fechas_14102023.csv. Este archivo ha sido generado con un .ipynb en la carpeta /src llamado JOIN_DF.ipynb. Dicho archivo ha tenido que ser ejecutado en Google Colab Pro, ya que consume +25GB de RAM, debido al tamaño de los  dataframe. Utilizamos Google Colab Pro, para poder hacer frente a esta demanda de RAM. 
   Si tienes una RAM de +30GB no tendrás problema en ejecutar todo el proyecto en local, para poder hacer cualquier comprobación o modificación.
   
   Una vez ejecutado todo en colab se convierte el dataframe resultante a CSV y se descarga para poder luego trabajar con este archivo en local y poder realizar el EDA y los diferentes modelos del proyecto.

2) Una vez tenemos esto, pasamos a crear un modelo de clusterización en el que poder clasificar los productos. Para ellos utilizaremos el algoritmo KMEANS, calcularemos mediante la curva del codo y las variables que sacamos, cuál es la cantidad óptima de clúster.

3) En este punto, generamos otro modelo a través de el algoritmo XGBoostRegressor, con el que pretendemos predecir la venta durante los próximos 28 días. Evaluaremos como de buenos es nuestro modelo modelo con diferentes métricas como el RMSE para ver cuál es el margen de error que tiene..



Tenemos diversas carpetas:

 - **CSV**: donde tenemos los CSV utilizado para obtner los datos de trabajo (item_prices.csv,item_sales.csv, daily_calendar_with_events.csv). El resto de CSV han sido creado dentro de los jupyter notebook para poder exportar en esta caso la información a un Power BI y poder hacer una presentación a negocio. Sobre diferntes insights y también sobre el funcionamiento de nuestros 2 modelos (predicción de ventas y clustering de tipos de productos)

 - **img**: compuesta por imagenes para el readme.

 - **models**: contiene archivos .pkl que contienen los modelos generados para poder ponerlos en producción.

 - **src**:  contiene 4 archivos .ipynb. Clustering.ipynb como el propio nombre indica es nuestro notebook donde hemos entrenado el modelo de clustering. Por otro lado, el Predict_ventas.ipynb es nuestro nuestro notebook donde hemos entrenado el modelo de predicción de ventas para el mes siguiente.

   También tenemos dos archivos más, uno de EDA.ipynb donde realizamos un pequeño EDA de nuestros datos para decidir como entrenar después a nuestros modelos y ver también como se distribuye nuestros datos sacando insights para el negocio.
   Por último, esta carpea contiene el archivo JOIN_DF donde se realiza la limpieza, organización e unión de los 3 archivos de datos con los que empezamos inicialmente, para poder trabajar sobre una única base de datos. Recientemente, se ha añadido otro notebook que convierte el csv limpio en formato JSON.

- **JSON**: contiene los datos ya limpios, estructurados y unificados del proyecto para poder utilizarlos en una posible implementación en web.


## 🛠️ Este proyecto está actualmente en proceso de terminar... se irá añadiendo más información y más código conforme se vaya avanzando... 🛠️

- [x] Extracción, limpieza, transformación de datos
- [x] Archivos a formato JSON
- [x] Entrenamiento de modelo de Machine Learning (Predicción de ventas y Clustering de productos)
- [ ] Dockerfile
- [ ] Uso de Airflow, MLflow
- [ ] Puesta en producción
