#Sistemas Recomendadores Texto

Terminos clave: 
Bag of words, Node2Vec, TF-IDF
Ley de Zipf
Token: Termino con significado relevante para el corpus
NER: Named entity recognition (ciudades etc)
NLP Collocations, N-grams. Encontrar significado conjunto de palabras (Pontificia Universidad Catolica)
POS: part of speech. Tagging verbo, sustantivo etc


Nociones clave:
Las palabras menos frecuentes son mas significativas para un tema
Remocion de stop words (palabras comunes y repetitivas en un texto)
Nocion de tokens multipalabras, por ejemplo: Pontificia Universidad Catolica de Chile
Tambien considerara la existencia de StopWords importantes como: "NO" que afectan el sentido de la oracion
Tecnicas de normalizacion, como por ejemplo lematizacion, que consiste en  normalizar palabras a su raiz de conjugacion, plural. O tambien Stemming: remocion de caracteres para encontrar raiz
En el proceso de aprender secuencias se obtiene de resultado el embedding w2v. Glove y Fast Text son otras opciones para embeddings

Uso de redes neuronales basadas en ResNet, Bert o Transformers para hacer recomendaciones secuenciales. Considerar la variable temporal a la hora de hacer recomendaciones. Un caso de uso de recomendaciones temporales es por ejemplo un viaje turistico e itinerario.
