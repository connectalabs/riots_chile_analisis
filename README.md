
# Análisis de Datos de Twitter  
  Continuando con el análisis de la con  
  
# Descubrimientos  
  
 - Tráfico anómalo.  
 - Influencia extranjera en este tem  
   
 # Descubrimiento 1 | Tráfico Anómalos

Usamos la librería de Facebook Prophet para poder analizar la serie de tiempo de cantidad de tweets por minuto que se han producido, esta reveló que existen comportamientos anómalos, se llegó a un peak de 3.217 tweets en 1 minuto, que está completamente sobre la media y el techo superior estimado por Prophet.

![anomalia 01](https://raw.githubusercontent.com/connectalabs/riots_chile_analisis/master/plots/ts_anomaly_mark.png)

[**Ver Análisis**](https://github.com/connectalabs/riots_chile_analisis/blob/master/time_series_twitter_analisis.ipynb)