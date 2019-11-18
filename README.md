# Análisis de Datos de Twitter        
 En **ConnectaLabs** continuamos con nuestro esfuerzo de entender lo que está pasando en nuestro querido país y saber si la **DATA** nos puede ayudar. Para este ejercicio nosotros comenzamos el 20 de Octubre a descargar todos los tweets los hashtags, trending topic chilenos relacionados con estas protestas.      
      
# Datos      
 Los datos se obtuvieron desde la API pública de Twitter:      
- Información del: **2019-10-20 al: 2019-11-05**.      
- **4.807.736** de tweets.      
- **638.893** usuarios.      
- Las búsquedas se realizaron en base a los principales **hashtags**:      
      
> ['cambiodegabinete', 'renunciapinera', 'chiledesperto', > 'lamarchamasgrandedechile', 'chilesecanso', 'chilequierecambios', > 'pinerarenuncia', 'prensaprostituida', 'toquedequedachile', > 'superlunes', 'lamarchamasgrandedetodas', 'pazparachile', > 'noalaasambleaconstituyente', 'toquedequeda', 'nuevaconstitucion', > 'chilenosquehablan', 'aguantesharp', 'nomasmarchas', 'fuerasharp', > 'nomasviolencia', 'fueracomunistas', 'pineralies', 'evasionmasiva', > 'pineraverguenzamundial', 'chilenoquieremigajas', 'pineramiente', > 'noestamosenguerra', 'acusacionconstitucional', 'sinigualdadnohaypaz', > 'losmilicosnosontusamigos', 'chileseaburrio', 'estadodeemergencia', > 'chalecosamarillos', 'yotengopyme', 'karlarubilar', > 'destitucionarticulo60','evasiontodoeldia', > 'nuevaconstitucionparachile', 'nomasmarcha', 'fueracomunismodechile', > 'chilepaisdepiromanos', 'militaresalacalleya', 'nomasencapuchados', > 'izquierdagolpista', 'toquedequedatotal', 'nuevaconstitucionahora', > 'renunciasharp', 'chileenreveldia', 'toquedequedaahora', > 'metroselevanta', 'chiledepie', 'nomassocialismo', > 'nomasdelincuencia', 'nomastag', 'evasionmetro', 'pazporchile', > 'votocastigo', 'destitucionahora', 'plebicito15d']      
 # Descubrimientos        
 1. Tráfico anómalo en Twitter impulsando algunos hashtags.      
2. Análisis tweets sobre el levantamiento social en Chile por Nacionalidad y Polaridad.      
          
 # 1. Descubrimiento | Tráfico Anómalo      
 Usamos la librería de Facebook Prophet para poder analizar la serie de tiempo de **cantidad de tweets por minuto** que se han producido, esta reveló que existen comportamientos anómalos, se llegó a un peak de 3.217 tweets en 1 minuto, que está completamente sobre la media y el techo superior estimado por Prophet.      
      
![anomalia 01](https://raw.githubusercontent.com/connectalabs/riots_chile_analisis/master/plots/ts_anomaly_mark.png)      
      
[**Click Aquí Para Ver Análisis Tráfico Anómalo**](https://github.com/connectalabs/riots_chile_analisis/blob/master/time_series_twitter_analisis.ipynb)      
 # 2. Análisis tweets sobre el levantamiento social Nacionalidad y Polaridad.      
     
 Se identifica de manera transversal en las tres categoría (marchas, orden público y política) la existencias de 3 clusters bien definidos los cuales presentan homogeneidad en términos de nacionalidad y polaridad. La relevancia y principales actores en éstas varían según la categoría:      
 1. **Cuentas nacionales pro movilizaciones y cambios políticos**    
 2. **Cuentas extranjeras pro movilizaciones y cambios políticos**    
 3. **Cuentas nacionales en contra de las movilizaciones y cambios políticos**    
   
 ![Análisis Hashtags vs Nacionalidad](https://raw.githubusercontent.com/connectalabs/riots_chile_analisis/master/plots/marchas_location_legend.png)      
    
[**Click Aquí Para Ver Análisis por Tema**](https://github.com/connectalabs/riots_chile_analisis/blob/master/analisis_tweets_sobre_levantamiento_social.md)

# ConnectaLabs AI

ConnectaLabs AI es una empresa especialista en el desarrollo de soluciones de inteligencia artificial para la comprensión del cliente. Si quieres saber más de nosotros y nuestros servicios puedes contactarnos en nuestras RRSS.

 - Email: [ai@connectalabs.ai](mailto:ai@connectalabs.ai?subject=Riots-Chile)
 - Web: [https://www.connectalabs.ai](https://www.connectalabs.ai)
 - Linkedin: [https://www.linkedin.com/company/connecta-labs-ai](https://www.linkedin.com/company/connecta-labs-ai)
 - Medium: [https://medium.com/connecta-ai](https://medium.com/connecta-ai)