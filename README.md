# Text_Mining
*Trabajo práctico* for Laura Alonso Alemany and Cristian Cardellino's "*Minería de Datos para Texto*" class at the *Facultad de Matemática, Astronomía, Física y Computación* (FaMAF), *Universidad Nacional de Córdoba* fall 2019. 

## *La Voz del Interior* COOC and Clustering 
This notebook demonstrates standard text mining methods for unsupervised learning: a coocurrence matrix, Word2Vec neural embeddings, and k-means clustering.
### Description of dataset
The data was taken from 1666 recent articles (4646557 words) from *La Voz del Interior*, the newspaper of record in Córdoba, Argentina.

## Preprocessing Pipeline with nltk
1. sentence tokenize
2. word tokenize
3. eliminate numbers
4. eliminate stopwords
5. lowercase
6. lemmatize

# COOC: four-word window
Context is a essential to meaning in human language. A **cooccurrence matrix** gives us semantic and idiomatic insight into the language by showing us which words appear together often and if any dependencies are present between words. I chose a four-word window because I wanted to get as much context as possible into my matrix.
* Example of cooccurrence: **"albert"** will have a high cooccurrence count with the word **"einstein"**

# Vectorization with DictVectorizer
A mathematical representation of our words allows us to apply sophisticated statistical and probabilistic methods to our data, such as the **k-means** clustering algoritm, which will enable us to see the underlying structure of the language use in *La Voz del Interior*.

## Word2Vec: it's not a vectorization, it's an embedding!
For my clusters I decided not to use the hand-made cooccurence matrix now in favor of the more 'information-rich' **neural embeddings** of Word2Vec. 
This two-layer neural network provides us with much more than our counts-basd cooccurrence matrix. These neural embeddings carry much lower demensionality and have semantic representation, useful in processes such as [Latent Semantic Analysis](https://en.wikipedia.org/wiki/Latent_semantic_analysis).

**Word2Vec Parameters:**
* four-word window ```(window=4)``` to be consistent with the cooc above
* dimensionality ```(size=300)``` the maximum available
* downsampling of high frequency words ```(sample=6e-5)```
* drown out the noise words ```(negative=20)``` set at maximum


![Latent Semantic Analysis](https://upload.wikimedia.org/wikipedia/commons/thumb/7/70/Topic_model_scheme.webm/600px-seek%3D17.6-Topic_model_scheme.webm.jpg)
(photo of Latent Semantic Analysis from Wikipedia)


# Clustering with k-means
* normalized the embeddings before clustering; k-means automatically uses euclidean distance

# Analysis
After much trial and error with hyperparameters and parameters, patterns began to emerge in the results. Each time I ran the k-means algorithm a cluster appeared with the following: 
* numbers and scientific words of measurement
* political names and words associated with politics in Argentina
* industrial/ and agricultural words 
-------------------------------------------------------------------------
## Example Clusters from Above:

>Cluster 11 - **Education**
Words: secundario, ipem, belgrano, alejandro, carbó, tomar, jerónimo, luis, cabrero, colegio, edilicio, educación, estudiante, escuela, estudiantil, protestar, reclamo, docente, educativo, instituto, preuniversitario, garzón, agulla, tosco, asamblea, grahovac, colegiar, walter, alumno, buffoni

>Cluster 29 - **Agriculture and Industry**
Words: año, mil, subir, ciento, promediar, hectárea, pagar, exportación, tonelada, precio, millón, valor, cuota, dólar, mes, peso, incrementar, cosechar, soja, maíz, trigo

>Cluster 31 - **Brazilian Politics**
Words: verde, marino, candidato, silva, dilma, rousseff, serra, pt, psdb, luiz, inácio, lula

>Cluster 41 - **Argentine Politics**
Words: manuel, ex, daniel, presidente, josé, cristino, fernández, kirchner, intendente, néstor, gobernador, juan, sota, schiaretti

Acknowledgements: Code inspired by and taken from María Florencia Alonso, Cristian Cardellino, Dani Bosch and Facu Molina. Thank you!
