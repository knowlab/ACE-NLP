# Adverse Childhood Experiences NLP project
Adverse Childhood Experiences (ACEs) are defined as a collection of highly stressful, and potentially traumatic, events or circumstances that occur throughout childhood and/or adolescence. They have been shown to be associated with increased risks of mental health diseases or other abnormal behaviours in later lives. This repo is for creating a publicly accessible resource for facilitating NLP for surfacing ACEs from free-text data.

Please see below an example Reddit post with annotated ACEs + ACE related mental disorders.

![image](https://user-images.githubusercontent.com/6075558/169579155-988bf561-4dd1-4dd6-ab78-13d332e9be0b.png)


## ACE Ontology and NLP resources generated from Redddit Mental Health Corpus
The Reddit Mental Health Corpus is from https://zenodo.org/record/3941387#%23.YFfi3EhJHL8. We applied baseline NLP ([SemEHR](https://academic.oup.com/jamia/article/25/5/530/4817428)) and then introduced a self-supervised method for learning concept embeddings. This generates the following reusable resources.

- Reddit corpus vector representations: [reddit_vector_data.zip](./Reddit-MH/reddit_vector_data.json.zip). This is a zipped `JSON` file, which is of the format like below.
  ```javascript
  {
    "concept_dimentions":	[...], // a list of 322 ACE concepts (identified as UMLS CUIs)
    "concept vectors":	{...}, // a dictionray from CUI to vector, each dimension of the vector is a concept (the order follows the concept list above)
    "document vectors":	{...} // a dictionary from document name to vector, the dimensions are the same as those of the concept vectors above.
  }
  ```
- Adverse Childhood Concept Embedding: [concept_embedding_322c50d.json](./Reddit-MH/concept_embedding_322c50d.json). This is concept embeddings that are generated from the above data using an `Autoencoder` trained on all document vectors. The dimension size is 50. This is a compact representation of concepts, which as we show in our experiments has very similar performances as those original 322 dimension vectors. For example, the figure below shows the cosine similarities between 780 documents which contain the concept `Suicide[CUI:C0038661]`. The x-axis is the similarity from original vectors (322 dimensions) and the y-axis is that of encoded vectors (50 dimensions). They form a near linear correlation while the dimension has been reduced >6 times.

![image](https://user-images.githubusercontent.com/6075558/169578177-c8b1ecdb-b526-4f31-95ef-87b294b7e868.png)

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
