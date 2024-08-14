

# System Diagram

This is a standard RAG architecture.

1. **CWE Corpus Ingestion** Grounded Closed-System i.e. CWE specification and known good examples are the corpus only.
2. **Logger**: Log of all prompts and responses for feedback and improvement
3. **System Prompt**: Additional instructions to the LLM e.g. Mappings, Confidence, Rationale, Format...
4. Machine or Brower Interface


```mermaid

graph TD
    Person[Person] -->|Types prompt| Browser[Web Browser]
    Browser -->|User Prompt| User[Prompt Interface]
    Machine -->|User Prompt| User[Prompt Interface]
    
    
    subgraph "System"
        User[Prompt Interface] -->|Prompt and Resoonse| Logger

        Embedder -->|Document Vectors| VectorDB
        User -->|Query| QueryProcessor[Query Processor]
        QueryProcessor -->|Processed Query| Retriever[Retriever]
        Retriever -->|Search Query| VectorDB[(Vector Database)]
        VectorDB -->|Relevant Documents| Retriever
        Retriever -->|Retrieved Context| Prompter[Prompter]
        SystemPrompt -->|System Prompt| Prompter[Prompter]
        QueryProcessor -->|Processed Query| Prompter
        Prompter -->|Augmented Prompt| LLM[Large Language Model]
        LLM -->|Generated Response| ResponseGenerator[Response Generator]
    end

    ResponseGenerator -->|Final Answer| User
    User -->|Response| Browser
    User -->|Response| Machine

    Browser -->|Shows result| Person

    subgraph "CWE Corpus"
        CWEDocs[Trimmed MITRE CWE Spec] -->|Preprocessing| Embedder[Embedding Model]
        CWEExamples[Known Good CVE-CWE Mappings] -->|Preprocessing| Embedder[Embedding Model]

    end

    style Person fill:#f96,stroke:#333,stroke-width:2px
    style Browser fill:#ff9,stroke:#333,stroke-width:2px
    style Machine fill:#ff9,stroke:#333,stroke-width:2px
    style User fill:#f9f,stroke:#333,stroke-width:4px
    style LLM fill:#bbf,stroke:#333,stroke-width:4px
    style VectorDB fill:#dfd,stroke:#333,stroke-width:4px

```

