# Advanced Retrieval With LangChain

Let's go over a few more complex and advanced retrieval methods with LangChain.

There is no one right way to retrieve data - it'll depend on your application so take some time to think about it before you jump in

Let's have some fun

* **Multi Query** - Given a single user query, use an LLM to synthetically generate multiple other queries. Use each one of the new queries to retrieve documents, take the union of those documents for the final context of your prompt
* **Contextual Compression** - Fluff remover. Normal retrieval but with an extra step of pulling out relevant information from each returned document. This makes each relevant document smaller for your final prompt (which increases information density)
* **Parent Document Retriever** - Split and embed *small* chunks (for maximum information density), then return the parent documents (or larger chunks) those small chunks come from
* **Ensemble Retriever** - Combine multiple retrievers together
* **Self-Query** - When the retriever infers filters from a users query and applies those filters to the underlying data

# ps
* I change OpenAIEmbeddings() to HuggingFaceInstructEmbeddings() since my free openAI toke exced the quota as always (RateLimitError: Error code: 429).
* I changed 'llm = ChatOpenAI(temperature=0)' to 'llm=HuggingFaceHub(repo_id="google/flan-t5-xxl", model_kwargs={"temperature":0.7, "max_length":512})'
* my llm inputs must have less than 1024 tokens
* building 'vectordb = Chroma.from_documents(documents=splits, embedding=embedding)' and 'retriever.add_documents(docs, ids=None)' takes very long time
* the last case has some env error about 'lark' package
* my model has smaller 
  

