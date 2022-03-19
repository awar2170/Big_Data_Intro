## NLP Pipeline (Natural Language Processing)

NLP is complicated. To manage it, you must build an NLP pipeline, a process breaking NLP down into a series of smaller, less complex tasks. Below we'll provide a high overview of this process, and in the next section, we'll dive deeper with the code.

Each step of the NLP pipeline involves a separate task. The output data from one step, in turn, becomes the input data for the next step, with an opportunity to evaluate and refine each task, if needed. A basic NLP pipeline follows:

1. Raw Text 
2. Tokenization 
3. Stop Words Diltering 
4. TF-IDF
5. Machine Learning 

Here's a breakdown of each step:

    1. Raw Text: Start with the raw data.

    2. Tokenization: Separate the words from paragraphs or sentences, into individual words. [Google Collab Link to more infomration on Tokenization](https://colab.research.google.com/drive/1RDJ13T45jY12yeYcE62f3PJ1MFL3_pS1)

    3. Stop Words Filtering: Remove common words like "a" and "the" that add no real value to what we are looking to analyze. [Google Collab Link with more information](https://colab.research.google.com/drive/1omVDqu4XKcGCgSvsRrxpVKCgR5LGfviN#scrollTo=c14tj-6m8sj6)
    
    4. Term Frequency-Inverse Document Frequency (TF-IDF): Statistically rank the words by importance compared to the rest of the words in the text. This is also when the words are converted from text to numbers. [Google Collab Link to more infomration on Term Freq-Inverse Doc Freq](https://colab.research.google.com/drive/1gN_CWHueFUcLnxP5Jc_S0mLqaa1J24Es#scrollTo=CwcRINHM-c1K)

    5. Machine Learning: Put everything together and run through the machine learning model to produce an output. [More infomration](https://colab.research.google.com/drive/1WyTFx6Hn8Z86u12RQ4TLNQDDHbmGtpZv#scrollTo=-EGh8LZ6DPuO)
