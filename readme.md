# Simplified Retrieval Augmented Generation (RAG) Demonstration

This demonstration illustrates the ease of implementing Retrieval Augmented Generation (RAG) using ChatGPT's built-in capabilities. It's based on: https://www.youtube.com/watch?v=P8tOjiYEFqU&ab_channel=DonWoodlock

We'll construct a minimal, or "micro," dataset to serve as the knowledge base for our Language Model (LLM). The core concept of RAG involves retrieving relevant information from this external dataset based on the user's query and incorporating it into the LLM's response. We will also visualize the similarity between the query and dataset embeddings using the dot product, highlighting how proximity in embedding space correlates with semantic relevance.

## Key Concepts:

* **RAG (Retrieval Augmented Generation):** A technique that enhances LLMs by allowing them to access and incorporate information from external knowledge sources. This improves accuracy and reduces hallucinations by grounding responses in real data.
* **Embeddings:** Numerical representations of text, capturing semantic meaning. These are vectors in a high-dimensional space where similar texts have closer vectors.
* **Dot Product Similarity:** A measure of similarity between two vectors. In the context of embeddings, a higher dot product indicates greater similarity. The dot product of two vectors $a$ and $b$ is calculated as:

    $$a \cdot b = \sum_{i=1}^{n} a_i b_i$$

    where $n$ is the dimension of the vectors.
* **Visualization:** We will plot the dot product results to visually represent the similarity scores, aiding in understanding how the query's embedding relates to the dataset embeddings.

## Detailed Steps:

1.  **Environment Setup and API Configuration:**
    * Install necessary Python libraries, including `openai` for accessing the OpenAI API and potentially `numpy` and `matplotlib` for numerical operations and plotting.
    * Configure the OpenAI API key to enable communication with the API. This typically involves setting an environment variable or loading the key from a configuration file.

2.  **Dataset Embedding Generation:**
    * Create a small dataset of text snippets.
    * Utilize the OpenAI API's embedding model (e.g., `text-embedding-ada-002`) to generate embeddings for each text snippet in the dataset. This transforms the text into numerical vectors. Store these embeddings along with the corresponding text.

3.  **Query Embedding Generation:**
    * Formulate a user query.
    * Generate the embedding for the query using the same embedding model used for the dataset. This ensures consistency in the embedding space.

4.  **Similarity Calculation and Visualization:**
    * Calculate the dot product between the query embedding and each dataset embedding. This yields a similarity score for each dataset entry.
    * Store the similarity scores.
    * Visualize the similarity scores. This can be done by creating a bar plot, where the x-axis represents the dataset entries, and the y-axis represents the dot product similarity scores. This visualization will clearly show which dataset entries are most relevant to the query.

5.  **RAG Integration:**
    * Provide the LLM with the user query, and the most relevant information retrieved from the dataset, based on the highest dot product scores.
    * Instruct the LLM to use the retrieved information to generate a response.
    * Observe the response generated by the LLM, noting how the retrieved information influences the output.