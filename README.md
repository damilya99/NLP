# NLP
The NLP algorithms that I have explored during my work as Research Assistant
**Compariaon of methods ELMo, GLoVe, Word2Vec, BERT**

A point I haven't seen brought up is tokenization. Word2Vec and Glove handle whole words, and can't easily handle words they haven't seen before. FastText (based on Word2Vec) is word-fragment based and can usually handle unseen words, although it still generates one vector per word. Elmo is purely character-based, providing vectors for each character that can combined through a deep learning model or simply averaged to get a word vector (edit: the off-the-shelf implementation gives whole-word vectors like this already). BERT has it's own method of chunking unrecognized words into ngrams it recognizes (e.g. circumlocution might be broken into "circum", "locu" and "tion"), and these ngrams can be averaged into whole-word vectors.

ELMo and BERT incorporate context, handling polysemy and nuance much better (e.g. sentences like "Time flies like an arrow. Fruit flies like bananas") . This in general improves performance notably on downstream tasks. However, they're designed using whole sentences as context, and in some applications you might be working on individual words or phrases and their context in a sentence isn't easily available, in which case Word2Vec or GloVe might be better.

Availability of pretrained vectors in other languages also varies widely. FastText, for example, has models in dozens of languages. Bert has a general multilingual model and a Chinese pretrained model published.

Bert is also designed to be fine-tuned easily, and is designed so you can drop it into a classifier without having to do much network building or customization. Although note that fine-tuning of these vectors can potentially hurt generalization, especially if your data set is small.

Technically Bert is considered state-of-the-art, but compared to some of the practical concerns like whether you have a good context and whether you have a lot of obscure words, what's state-of-the-art may be a minor consideration.
