# Legal Named Entities Extraction (L-NER)
India is a highly populated country with the problem of a high number of pending legal cases. Some of these problems can be tackled by automating processes in the pipeline. In this paper, we will be targeting entity recognition for English legal documents to identify entities in the judgment and preamble. 14 Entities like petitioner, respondent, court, statute, provision, precedents, etc are identified which then be used for retrieval-based tasks. Existing NER models cannot be employed to extract these entities as legal texts are different from commonly occurring texts used to train NLP models which is why a custom NER model is necessary to perform NER on Legal Documents using the LegalEval dataset.\cite{kalamkar2022named}.  

The baseline model makes use of spacy-transformers to evaluate legal documents which makes use of compute-intensive pre-trained models like BERT, XLNet, and GPT-2. We have tried to use simpler models to achieve comparable accuracies. The models used take around 15 minutes to train with the usage of 1 GPU core and achieve an overall F1 score of 92.82 and trained using the spacy config system. The model employs sentence-based embeddings using a token-to-vector model followed by a NER parser to identify legal entities in the judgment and preamble. 

We have built the model to take in the data of the LegaEval dataset and process the input into vectors using the tok2vec subnetwork\cite{tok2vec} for mapping tokens into vector representations followed by identifying the entities using a transition-based parser model\cite{transitionbasedparser} consisting of 2 subnetworks. 


<img width="700" alt="Model Architecture" src="https://github.com/maazshaik/semeval-legal-ner/blob/main/sysdesign.png">
