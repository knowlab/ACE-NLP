# Averse Childhood Experiences NLP project

## Redddit Mental Health Corpus
- Reddit corpus vector representations: [reddit_vector_data.zip](./Reddit-MH/reddit_vector_data.json.zip). This is a zipped `JSON` file, which is of the format like below.
  ```javascript
  {
    "concept_dimentions":	[...], // a list of concepts (CUI ids)
    "concept vectors":	{...}, // a dictionray from CUI to vector, each dimension of the vector is a concept (the order follows the concept list above)
    "document vectors":	{...} // a dictionary from document name to vector, the dimensions are the same as those of the concept vectors above.
  }
  ```
- Adverse Childhood Concept Embedding: [concept_embedding_322c50d.json](./Reddit-MH/concept_embedding_322c50d.json). This is concept embeddings that are generated from the above data using an `Autoencoder` trained on all document vectors. The dimension size is 50. This is a compact representation of concepts, which as we show in our experiments has very similar performances as those original 322 dimension vectors.
