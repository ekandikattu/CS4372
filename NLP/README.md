# NLP Text Summarization using BART

This project performs **abstractive text summarization** on *The Strange Case of Dr. Jekyll and Mr. Hyde* using a pre-trained transformer model.

## Dataset

-   Source: Project Gutenberg\
    https://www.gutenberg.org/cache/epub/43/pg43.txt

## Task

-   **Abstractive Text Summarization** using HuggingFace Transformers.

## Model

-   Pre-trained model: **facebook/bart-large-cnn**
-   Implemented via `pipeline("summarization")` in Google Colab.

## Preprocessing

-   Removed Gutenberg header/footer.
-   Normalized formatting.
-   Chunked text into \~1500-character segments.

## Evaluation

-   Metrics: **ROUGE-1, ROUGE-2, ROUGE-L, ROUGE-Lsum**
-   Manual reference summaries were created for selected chunks.

## How to Run Code
Use Google Colab
-   Open the notebook Assignment4_NLP.ipynb in Colab
-   Go to Runtime -> Run all
