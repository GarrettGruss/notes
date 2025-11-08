# BERT

**BERT**: **B**idirectional **E**ncoder **R**epresentations from **T**ransformers. [Link to Article](https://arxiv.org/pdf/1810.04805)
[Search before Bert](https://blog.google/products/search/search-language-understanding-bert/)
[Guide to Bert](https://towardsdatascience.com/a-complete-guide-to-bert-with-code-9f87602e4a11/)
[Stanford](https://nlp.stanford.edu/seminar/details/jdevlin.pdf)

- BERT pretrains on unstructured data, and then is fine-tuned on a task like question answering and language inference.
- BERT is bidirectional, unlike the unidirectional chat gpt
- BERT uses a Masked Language Model **MLM** to randomly mask words during the training process. The model attempts to predict the masks as part of the training process.
- BERT also uses a next-sentance prediction task.
- BERT Transformer uses bidirectional self-attention

## Pretraining phase

- **Stage 1**: Masked LM (MLM). The model is trained on word prediction. 15% of the words in the training data are masked, and the model's job is to predict them. Pre-training is done on BookCorpus and Wikipedia.
- **Stage 2**: Next Sentance Prediciton (NSP). The model is trained on sentance prediction (so it can understand context). 

## Fine-Tuning Phase

-  simply plug in the taskspecific inputs and outputs into BERT and finetune all the parameters end-to-end. At the input, sentence A and sentence B from pre-training are analogous to (1) sentence pairs in paraphrasing, (2) hypothesis-premise pairs in entailment, (3) question-passage pairs in question answering, and (4) a degenerate text-pair in text classification or sequence tagging.

![bert input representation]("BERT_input_representation.png")

## Embedding Layer

[Link](https://medium.com/@_init_/why-bert-has-3-embedding-layers-and-their-implementation-details-9c261108e28a)

# GPT

[Link to Article](https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf)

- GPT Transformer uses constrained self-attention where every token can only attend to context to its left.

# ELMo

[Link to Article](https://arxiv.org/pdf/1802.05365)

# Transformer

[Link to Article](https://arxiv.org/pdf/1706.03762)
[Link to Video](https://www.youtube.com/watch?v=xI0HHN5XKDo)

Improvement over the LSTM Network

# SOTA

# Fine-Tuning

- Epochs
- Learning Rate
- Batch Size

# NLP Use cases

- Question Answering
- Sentiment Analysis
- Named Entity Recognition
- Entailment
- Sequence Tagging

