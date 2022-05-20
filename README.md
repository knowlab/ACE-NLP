# Averse Childhood Experiences NLP project
Adverse Childhood Experiences (ACEs) are defined as a collection of highly stressful, and potentially traumatic, events or circumstances that occur throughout childhood and/or adolescence. They have been shown to be associated with increased risks of mental health diseases or other abnormal behaviours in later lives. This repo is for creating a publicly accessible resource for facilitating NLP for surfacing ACEs from free-text data.

## ACE Ontology and NLP resources generated from Redddit Mental Health Corpus
- Reddit corpus vector representations: [reddit_vector_data.zip](./Reddit-MH/reddit_vector_data.json.zip). This is a zipped `JSON` file, which is of the format like below.
  ```javascript
  {
    "concept_dimentions":	[...], // a list of 322 ACE concepts (identified as UMLS CUIs)
    "concept vectors":	{...}, // a dictionray from CUI to vector, each dimension of the vector is a concept (the order follows the concept list above)
    "document vectors":	{...} // a dictionary from document name to vector, the dimensions are the same as those of the concept vectors above.
  }
  ```
- Adverse Childhood Concept Embedding: [concept_embedding_322c50d.json](./Reddit-MH/concept_embedding_322c50d.json). This is concept embeddings that are generated from the above data using an `Autoencoder` trained on all document vectors. The dimension size is 50. This is a compact representation of concepts, which as we show in our experiments has very similar performances as those original 322 dimension vectors.
- Full NLP results on Reddit Mental Health Corpus for identifying 322 concepts: [aces_reddits_mental_health_322_ACEs.zip](./Reddit-MH/aces_reddits_mental_health_322_ACEs.zip). This is a zipped `JSON` file.
  ```javascript
  {
    "se_ann_12382.json": [
      {
        "ruled_by": [], 
        "end": 514,                                 // end offset of the mention
        "pref": "Depression",                       // preferred label of the concept as defined in UMLS
        "negation": "Affirmed",                     // negation or not
        "sty": "Mental or Behavioral Dysfunction",  // semantic type of the concept as defined in UMLS
        "start": 504,                               // start offset of the mention
        "study_concepts": [], 
        "experiencer": "Patient",                   // who is the experiencer
        "str": "depression",                        // the original string
        "temporality": "Recent",                    // history or recent mention
        "id": "cui-1", 
        "cui": "C0011570"                           // the CUI of the concept as in UMLS
       }...
    ]...
  }
  ```
