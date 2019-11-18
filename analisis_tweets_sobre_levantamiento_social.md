# ANALISIS TWITTER PROTESTAS CHILE (Parte 2)  
##   Detección de comunidades y comportamientos en base a Nacionalidad y Polaridad  
  
<img src="https://raw.githubusercontent.com/connectalabs/riots_chile_analisis/master/plots/marchas_location_legend.png" width="800" align="middle">  
  
Continuando con nuestro segundo análisis de los tweets relativos a las masivas movilizaciones y demandas sociales vividas en Chile (ver primera parte [**Análisis Tráfico Anómalo**](https://github.com/connectalabs/riots_chile_analisis/blob/master/time_series_twitter_analisis.ipynb)), buscamos entender los grupos, nacionalidades, y opinión de las principales cuentas de Twitter en temas de interés.    
    
Para ésto, tomamos una muestra amplia de hashtags relevantes y los separamos en 3 categorías:    
 1. **Marchas**: Referentes a las marchas y manifestaciones (por ejemplo #chiledesperto)    
 2. **Política**: Referentes a la aprobación del gobierno y cambios al sistema político/constitucional (por ejemplo #fuerzapresidente o #nuevaconstitucionahora)    
 3. **Orden Publico**: Referentes a los actos de violencia o evasión y el actuar de fuerzas de orden (por ejemplo #nomasencapuchados o #losmilicosnosontusamigos)    
 Ademas se determino la "polaridad" de cada hashtag entre aquellos que estaban a favor o en contra en cada categoría (ver detalle y polaridad asignada [**aquí**](https://github.com/connectalabs/riots_chile_analisis/blob/master/data/summary_hashtags.csv))    
 ## Resumen Conclusiones
 Se identifica de manera transversal en las tres categoría (marchas, orden público y política) la existencias de **3 grupos/clusters** bien definidos, los cuales presentan homogeneidad en términos de nacionalidad y polaridad. La relevancia y principales actores en éstas varían según la categoría:    
 1. **Cuentas nacionales pro movilizaciones y cambios políticos**: Estas cuentas presentan una polaridad positiva hacia las marchas, cambios políticos y mixto respecto a temas de orden publico.    
 2. **Cuentas extranjeras pro movilizaciones y cambios políticos**: Estas son principalmente de nacionalidad **venezolana, nicaragüense y cubana**. Similar al cluster anterior, presentan una polaridad positiva hacia las marchas, cambios políticos y mixto respecto a temas de orden publico.     
 3. **Cuentas nacionales en contra de las movilizaciones y cambios políticos**: Estas son cuentas que muestran un sesgo en contra las marchas y los cambios al sistema político, además de apoyar el orden público y las fuerzas de orden.    
    
Destaca la **baja relevancia de medios de comunicación tradicional y políticos nacionales** (salvo algunas cuantas excepciones), dando pasos a cuentas extranjeras, periodistas independientes y sitios de noticias **no mainstream** (revistas y grupos independientes).    
  
RESUMEN RELEVANCIA TOP 400 CUENTAS POR CATEGORÍA  
![resumen cruces](https://github.com/connectalabs/riots_chile_analisis/raw/master/plots/heat_map.png)  
[Visualización Interactiva en Tableau aquí](https://public.tableau.com/views/resumen_twiiter_chile/Story1?:display_count=y&publish=yes&:origin=viz_share_link)  
  
  
## Metodología
Empleando los tweets relacionados con los hashtags de cada categoría entre el  2019-10-20 al 2019-11-05 (un total de 4.807.736 tweets y 638.893 cuentas) se realizó el siguiente proceso:    
    
 1. **Consolidar la polaridad** promedio de cada cuenta     
 2. **Homogeneizar la ubicación** de cada cuenta (vía [fuzzy matching](https://www.researchgate.net/publication/320603299_Research_on_string_similarity_algorithm_based_on_Levenshtein_Distance)).    
 3. **Definir relaciones entre cuentas** ("A" retweetea o hace like a cuenta "B"). Se agregan las interacciones para definir peso normalizado de cada vértice (usando tanh para reducir dispersión).    
 4. **Generar grafo** dirigido entre éstas (nodos = cuentas, vértices = relaciones normalizadas).    
 5. **Estimar relevancia** de cada cuenta mediante algoritmo de [Pagerank](https://es.wikipedia.org/wiki/PageRank) aplicado al grafo.    
 6. **Filtrar** las top 2000 cuentas acorde a Pagerank    
 7. **Reducir numero de vertices** mediante [Marginal Likelihood Filter](https://arxiv.org/abs/1503.04085) (se eliminan todos aquellos que no afectan la conectividad completa del grafo)    
 8. **Calcular posiciones** de los nodos mediante [Force Atlas 2](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0098679)    
 9. **Generar visualizaciones** en html    
    
>**Observación:** Debido a que la implementación y optimización de múltiples de los métodos y algoritmos empleados son de carácter interno, el código en Python con el análisis no es posible compartirlo sin divulgar propiedad intelectual de **ConnectaLabs AI**.    
 ## Resultados Hashtags | Marchas  
  Se identifican tres clusters relevantes:    
 1. Grupo mayoritariamente chileno (con algunas cuentas relevantes argentinas). Su inclinación es relativamente a favor de las marchas (polaridad positiva).     
 2. Grupo mayoritariamente extranjero (principalmente cuentas venezolanas, nicaragüenses y cubanas). Su polaridad es marcadamente a favor de las marchas.    
 3. Grupo mayoritariamente chileno. Con una polaridad con sesgo en contra de las marchas.  
  
<img src="https://raw.githubusercontent.com/connectalabs/riots_chile_analisis/master/plots/marchas_location_legend.png" width="800" align="middle">  
  
**[Click para ver mapa interactivo | Marchas Ubicación](http://bit.ly/2qpKdSr)**  
  
<img src="https://raw.githubusercontent.com/connectalabs/riots_chile_analisis/master/plots/marchas_polarity_legend.png" width="800" align="middle">  
  
**[Click para ver mapa interactivo | Polaridad](http://bit.ly/2r46zZO)**  
  
## Resultados Hashtags | Política  
  Se identifican tres clusters relevantes:    
 1. Grupo mayoritariamente chileno (con algunas cuentas relevantes argentinas). Su inclinación es relativamente a favor cambios políticos/desaprobación del actual gobierno.     
 2. Grupo mayoritariamente extranjero (principalmente cuentas venezolanas, nicaragüenses y cubanas). Su inclinación es marcadamente a favor cambios políticos/desaprobación del actual gobierno.    
 3. Grupo mayoritariamente chileno. Con una polaridad marcada a favor del gobierno y en contra de cambios a la constitución.    
  
<img src="https://raw.githubusercontent.com/connectalabs/riots_chile_analisis/master/plots/politico_location_legend.png" width="800" align="middle">  
  
**[Click para ver mapa interactivo | Política Ubicación](http://bit.ly/2KsEthG)**  
  
<img src="https://raw.githubusercontent.com/connectalabs/riots_chile_analisis/master/plots/politico_polarity_legend.png" width="800" align="middle">  
  
**[Click para ver mapa interactivo | Política Polaridad](http://bit.ly/2CQabkv)**  
  
## Resultados Hashtags | Orden Público / Fuerzas de Orden    
 Se identifican tres clusters relevantes:    
 1. Grupo mayoritariamente chileno (con algunas cuentas relevantes argentinas). Su inclinación es mixta.     
 2. Grupo mayoritariamente extranjero (principalmente cuentas venezolanas, nicaragüenses y cubanas). Su inclinación también mixta.    
 3. Grupo mayoritariamente chileno. Con una polaridad marcada a favor del orden público y aprobación a las fuerzas de orden.   
  
<img src="https://raw.githubusercontent.com/connectalabs/riots_chile_analisis/master/plots/orden_location_legend.png" width="800" align="middle">  
  
**[Click para ver mapa interactivo | Orden Ubicación](http://bit.ly/331bacw)**  
  
<img src="https://raw.githubusercontent.com/connectalabs/riots_chile_analisis/master/plots/orden_polarity_legend.png" width="800" align="middle">  
  
**[Click para ver mapa interactivo | Orden Polaridad](http://bit.ly/2NWnVAC)**


# ConnectaLabs AI

ConnectaLabs AI es una empresa especialista en el desarrollo de soluciones de inteligencia artificial para la comprensión del cliente. Si quieres saber más de nosotros y nuestros servicios puedes contactarnos en nuestras RRSS.

 - Email: [ai@connectalabs.ai](mailto:ai@connectalabs.ai?subject=Riots-Chile)
 - Web: [https://www.connectalabs.ai](https://www.connectalabs.ai)
 - Linkedin: [https://www.linkedin.com/company/connecta-labs-ai](https://www.linkedin.com/company/connecta-labs-ai)
 - Medium: [https://medium.com/connecta-ai](https://medium.com/connecta-ai)