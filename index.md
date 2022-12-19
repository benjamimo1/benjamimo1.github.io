# Nociones generales de los sistemas recomendadores

Los sistemas recomendadores o de ranking pueden ser clasificados considerando:

El tipo de dato usado:
- Metodo basado en reglas
- Metodo basado en contenido (aquello que el usuario consumio)
- Filtrado colaborativo: Mutuo basado en usuarios

El tipo de modelo usado:
- Basado en memoria: KNN (KNN se considera un metodo basado en memoria pues compara con la base de datos actuales)
- Basado en modelo: latentes


Modelos disponibles y de facil implementacion:
- Modelo Slope One
- Modelos Bayesianos
- Funk SVD

Metricas relevantes:
- AUC : area under the curve
- Calidad = precision, minimiza error
- Recall = % descubrimiento, volumen
- RMSE: Root Mean Square Error
- DCG y nDCG: permite comparar listas de recomendacion de tamaño distinto
Nociones de item coverage y User coverage


# Sistemas Recomendadores Texto

## Terminos clave: 
- Bag of words, Node2Vec, TF-IDF
- Ley de Zipf
- Token: Termino con significado relevante para el corpus
- NER: Named entity recognition (ciudades etc)
- NLP Collocations, N-grams. Encontrar significado conjunto de palabras (Pontificia Universidad Catolica)
- POS: part of speech. Tagging verbo, sustantivo etc


### Nociones clave vistos en la clase:
Las palabras menos frecuentes son mas significativas para un tema
Remocion de stop words (palabras comunes y repetitivas en un texto)
Nocion de tokens multipalabras, por ejemplo: Pontificia Universidad Catolica de Chile
Tambien considerara la existencia de StopWords importantes como: "NO" que afectan el sentido de la oracion
Tecnicas de normalizacion, como por ejemplo lematizacion, que consiste en  normalizar palabras a su raiz de conjugacion, plural. O tambien Stemming: remocion de caracteres para encontrar raiz
En el proceso de aprender secuencias se obtiene de resultado el embedding w2v. Glove y Fast Text son otras opciones para embeddings

Uso de redes neuronales basadas en ResNet, Bert o Transformers para hacer recomendaciones secuenciales. Considerar la variable temporal a la hora de hacer recomendaciones. Un caso de uso de recomendaciones temporales es por ejemplo un viaje turistico e itinerario.

# Etica de los sistemas recomendadores

Revision de ejemplos de sesgos por ej: sesgo en AI sobre raza debido a datasets no balanceados. 
- Casos de falso positivos en prediccion de delitos que eran mas comun en poblacion negra.
- Sesgo en prediccion de sexo en al utilizar reconocimiento facial en personas negras 
Debido a lo anterior es importante siempre considerar que los RecSys basadaos en AI puede caer en sesgos

En clases tambien se discutio terminos como fairness, accountability y transparency. Estos suelen ser dificiles de abordar en algoritmos no open source como por ejemplo en Youtube. Ahora si bien estos modelos son cerrados, es posible extraer y analizar su comportamiento general a traves de metodologias de Random walks. Esto consiste en realizaer una navegacion aleatoria a traves de sistemas de recomendacion para descubrir el comportamiento de un sistema AI. Consumir solo las recomendaciones para ver patrones de recomendacion subyacentes. 

Descubrimientos puntuales: YouTube de a poco te va recomendando videos mas largos
Convergencia hacia videos mas populares (reduccion teorica de diversidad en la recomendacion)

Discusion sobre derechos digitales y la legislacion que la EU aprobo para proteger a los usuarios, en particular GDPR.

Por cuanto los sistemas recomendadores pueden tener gran impacto social es deseable que estos tengan un alto grado de interpretabilidad, es decir, capacidad de entender, predecir desde la perspectiva humana las recomendaciones que el sistema realiza.

A medida que RecSys se vuelve mas complejo, es mas dificil de explicar. Pero por suerte a surgido una nueva ola de sistemas auto explicables, donde la  explicacion es parte del output del modelo. Un apronte de solucion en particular es el usar explicacion por similaridad en casos de factorizacion matricial, es relativamente sencilla de implementar por lo que puede considerarse o usarse como baseline en sistemas recomendadores que diseñemos.

# Deep Learning en sistemas de recomendaciones visual

Recomendacion basada en contenido. Recomendacion de imagenes similares.
Ejemplo de usuario que consume documentos: TD - IDF. Representacion vectorial de documentos en funcion de las palabras que lo constituyen. Uso de herramientas como VisRank + Pytorch (Factorizacion matricial es similar en estructura a esto, pues se usan embeddings). 

Modelos relevantes:

- NCF: Neural Collaborative Filtering
- Recomendacion basada en autoencoders
- MultVAE: variation auto encoder
- VisRec, CuratorNet
- Difussion visual BPR (bayesian personalized ranking)


Dato clave: No siempre una DL es mejor que una factorizacion matricial si no usamos CONTENIDO.

# Sistemas Recomendadores basados en aprendizaje reforzado 

Buscamos optimizar una función de recompensa a lo largo del tiempo a traves de la interaccion con el usuario. 
Exploracion vs Explotacion: Navego nuevas opciones o juego a la segura. Largo vs Corto plazo.

Problematicas asociadas: 
- Cold start
- Cambios en preferencias de usuarios
- Cambios en el catalogo de productos
- Cambios en el contexto de uso de la aplicacion (plataforma)

Riesgo de exploracion: mala recomendacion
Riesgo de explotacion: perder una alta recompensa al no recomendar algo nuevo

**Multi Armed Bandits**: cada bandit posee una distribucion de rewards que desconozco
Mision: estimar la esperanza de reward con el minimo de juegos posibles
 
Estrategia: explorar y luego explotar
Qt(a) = sum(rewards) / N pasos exploración 

Navegacion aleatoria o una por opcion en exploracion, luego uso de algoritmo greedy en la explotacion

Un parametro epsilon determina el grado de exploracion
Otra estrategia: epsilon decreciente


### Thompson Sampling

En vez de asumir una distribucion subyacente desconocida, intentaremos estimar los parametros de dicha distribucion usando sample. Estimacion a traves de una bernoulli/binomial y una beta. Ademas se introduce la nocion de Intervalos de confianza (UCB). \
Una extension de lo visto anteriormente con los multi armed bandits son los Contextual Bandits y el uso de Linear UCB. Para el caso de Contextual Bandits se hace uso de contextos globales mas amplios y para el caso de linear UCB se hace uso de segmentación parametrica lineal


# RecSys conversacionales

Mas que resumir la clase es sintetizar, conectar, comentar y referenciar.
Recomendaciones basadas en input, criticas, feedback sobre comentarios recibidos
Ejemplo de sistema de Dell para armar computadores a pedidos
Interfaces a traves de NLP: texto, voz. Buscamos apoyar la toma de decisiones de forma dinamica.
Chatbot e IA no son necesariamente lo mismo. Muchos chatbots son simple if/else
El chatbot basado en IA usa reconocimiento semantico de tokens. Es posible configurar un chatbot con varios modelos de NLP subyacentes  (reconocimiento de comandos, dominio de un determinado topico.)
Nocion del test de turing como prueba elemental de la capacidad y calidad de un modelo NLP. Busca medir la capacidad de un computador de imitar a un humano.

Un sistema conversacional busca generar y guardar personal insights a traves de active listening
Tratar de inferir personalidad, esto mejora la calidad de las predicciones y sugerencias
Ejemplo: MovieBot para recomendacion de peliculas
Estado del arte: Goker & Thomson, recomendacion de lugares en considerando prompts
Desde el año 2000 hay un auge de conversational recsys
A partir de 2017 se suma reinforcement learning, ejemplos de alexa

Formalizar el problema: 

RecSys conversacional tiene interacciona en multiple rounds y entiende las querys.
Voice commanding != Recommendation

Input: historial de dialogo, preferencias previas, metadata,
Output: respuestas, recomendaciones y explicaciones

SAUP: Sistema activo, usuario pasivo (sistema pregunta, usuario responde, tipo arbol de decision)
SAUE: Mixto, sistema activo, usuario interactua. Capacidad de procesar input chit/chat, respuestas no directas pero que engrosan el input.
SAUA: Sistema activo y usuario activo. Conversación activa.

Uso de knowledge graphs en la inteligencia subyacente
Decision: respondo, pregunto o recomiendo



Datasets Utilizados se dividen segun su tipo de dialogo: Rec, ChitChat, Q&A
Ejemplo: dataset construido sobre los reviews de amazon, reviews en Yelp. La practica usual es transformar reviews en conversaciones.
ReDail dataset si contiene conversaciones



Academia:
Mejorar el estado del arte, nuevas formas de resolver el problema, proponer nuevas arquitecturas
Industria: mejorar KPI, satisfaccion
Evaluacion de Calidad: Turn level metris, Dialogue level metrics, Business level metric


Se puede medir calidad de la conversacion, calidad de la recomandacion. Uso de encuestas
Medir: usabilidad, inteligencia, confianza, cercania, fidelizacion

Arquitecturas suelen ser modulares:

Objetivo: Conversacion fluida, por turnos y basada en conocimiento
Uso de transformers

Manejar NLP (NLU + NLG)
Dialogue state management: hablo, pregunto o recomiendo. Acotar hasta recomendar. Reinforcement learning y feedback explicito
Sistema recomendador propiamente tal
Generador de explicaciones
Knowledge o grafo de conocimiento
<15:30>

Herramientas: CMU, Deep Pavlov. Hoy se venden frameworks completos