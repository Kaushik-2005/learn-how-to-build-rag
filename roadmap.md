# RAG From First Principles --- Roadmap

> A theory-first reference that explains the complete
> Retrieval-Augmented Generation pipeline from first principles.

## 1. Project goal

Build a chapter-based learning website for understanding RAG deeply
without requiring the learner to implement a RAG system.

This repository is the theory companion to **Explore-RAG**. Explore-RAG
is where a learner may experiment with concepts; this repository
explains what those concepts mean, why they exist, how they work, their
trade-offs, and where they fail.

The project should feel like **Backend from First Principle**, but for
RAG: large, self-contained chapters arranged in a logical learning
order.

The curriculum follows the complete RAG pipeline:

**Sources → Loading → Cleaning → Chunking → Embedding → Indexing → Query
Processing → Retrieval → Reranking → Context Construction → Prompt
Assembly → LLM → Grounded Answer → Evaluation**

The architecture diagram supplied for this project is a curriculum
checklist. Every important component shown in that pipeline should be
explained somewhere in the repository.

------------------------------------------------------------------------

## 2. What this project is not

This is not another RAG application.

Do not build:

-   a RAG backend
-   an embedding service
-   a vector database
-   an LLM integration
-   an ingestion pipeline
-   authentication
-   a database
-   a model playground
-   runnable notebooks for every concept
-   artificial implementation exercises
-   a second version of Explore-RAG

The objective is **understanding**, not implementation.

Examples should normally come from publicly available papers, official
documentation, engineering articles, benchmarks, or other reputable
educational material. Cite the original source.

Small illustrative examples may be written when necessary to explain an
idea, but they must not turn into implementation projects or fabricated
empirical results.

------------------------------------------------------------------------

## 3. Website and repository direction

Use the structure and learning flow of:

-   Backend from First Principle ---
    https://github.com/DsThakurRawat/Backend-from-first-Principle
-   Backend from First Principle website ---
    https://backend-from-first-principle.vercel.app/

The exact implementation may use the same kind of static-site tooling as
the reference repository, including Astro/MDX, if useful.

Technology is secondary to the content. Keep the site static and simple.

Acceptable:

-   Astro
-   MDX / Markdown
-   HTML
-   CSS
-   minimal TypeScript or JavaScript for site infrastructure
-   SVG
-   Mermaid
-   static assets

Avoid runtime complexity. No backend or model/API dependency should be
required to read the website.

A chapter-oriented repository is preferred:

``` text
RAG-from-First-Principles/
├── 1.What-is-RAG/
├── 2.RAG-Pipeline-Architecture/
├── 3.Data-Sources-and-Loading/
├── 4.Document-Cleaning-and-Preparation/
├── 5.Chunking/
├── 6.Embeddings/
├── 7.Vector-Stores-and-Indexes/
├── 8.Query-Processing/
├── 9.Retrieval/
├── 10.Hybrid-Retrieval/
├── 11.Reranking/
├── 12.Context-Construction/
├── 13.Prompt-Assembly-and-Grounding/
├── 14.RAG-Evaluation/
├── 15.RAG-Failure-Modes/
├── 16.Advanced-RAG/
├── 17.Production-RAG/
├── assets/
├── src/
├── index.html
├── README.md
├── roadmap.md
└── AGENTS.md
```

The actual file layout may follow the chosen Astro/MDX structure, but
the learner should experience the material as these ordered chapters.

------------------------------------------------------------------------

# 4. Curriculum

## Chapter 1 --- What is RAG?

Start with the problem before introducing the architecture.

Cover:

-   what Retrieval-Augmented Generation means
-   parametric knowledge vs external knowledge
-   stale model knowledge
-   private/domain-specific knowledge
-   hallucination and unsupported generation
-   why retrieval is introduced
-   RAG vs ordinary search
-   RAG vs prompt-only systems
-   RAG vs fine-tuning
-   RAG vs long-context prompting
-   when RAG is useful
-   when RAG is unnecessary
-   what RAG does **not** guarantee

The learner should leave understanding why RAG exists before seeing
vector databases or frameworks.

------------------------------------------------------------------------

## Chapter 2 --- The Complete RAG Pipeline

Introduce the complete architecture before diving into individual
components.

Separate the system into two major paths.

### Indexing / ingestion path

**Data Source → Loader → Cleaning/Preparation → Chunking → Embedding →
Vector Store / Index**

Explain that this path is generally performed when knowledge is added or
updated.

### Query path

**User Query → Query Processing → Query Embedding → Retrieval →
Reranking → Context Builder → Prompt Assembly → LLM → Answer**

Explain which artifacts move between stages.

Cover:

-   offline vs online work
-   document lifecycle
-   query lifecycle
-   retrieval candidates
-   final context
-   provenance
-   citations
-   why one bad stage can affect everything downstream

Use an architecture diagram as the mental map for all later chapters.

------------------------------------------------------------------------

## Chapter 3 --- Data Sources and Document Loading

### Data sources

Explain common sources used to construct a RAG knowledge base:

-   PDF
-   Word documents
-   web pages
-   SQL databases
-   code repositories
-   Confluence/wiki systems
-   Slack/email
-   CSV
-   Excel
-   images
-   scanned documents
-   audio
-   video

Discuss structured, semi-structured, and unstructured data.

### Loading

Explain what a document loader actually does.

Cover examples such as:

-   PDF loaders
-   web/HTML loaders
-   SQL loaders
-   Git/repository loaders
-   structured-data loaders
-   CSV loaders
-   audio transcription loaders

Framework names such as LangChain loaders may be mentioned as examples,
but teach the abstraction first.

Explain common loader output:

-   content
-   metadata
-   source
-   page/location
-   document ID

Discuss extraction failures:

-   broken PDF text
-   missing tables
-   column-order problems
-   scanned PDFs
-   malformed HTML
-   lost headings
-   code formatting loss
-   audio transcription errors

------------------------------------------------------------------------

## Chapter 4 --- Document Cleaning and Preparation

Explain why loaded text is rarely ready for retrieval.

Cover:

-   stripping HTML and boilerplate
-   encoding problems
-   whitespace normalization
-   header/footer removal
-   metadata extraction
-   OCR for scanned documents
-   preserving tables and structure
-   deduplication
-   near-duplicate detection
-   MinHash intuition
-   PII detection/scrubbing
-   quality scoring
-   document IDs
-   source IDs
-   page numbers
-   timestamps
-   versions
-   departments/categories
-   permissions/access metadata
-   provenance

Explain the difference between removing noise and accidentally removing
useful retrieval signals.

------------------------------------------------------------------------

## Chapter 5 --- Chunking

This should be one of the deepest chapters.

### Why chunking exists

Cover:

-   context windows
-   retrieval granularity
-   whole-document retrieval
-   small vs large chunks
-   precision vs context
-   semantic boundaries

### Strategies

Explain:

-   fixed-size chunking
-   character-based chunking
-   token-based chunking
-   recursive character splitting
-   sentence-level chunking
-   paragraph/section-aware chunking
-   semantic chunking
-   parent-child chunking
-   code-aware splitting

### Chunk configuration

Cover:

-   chunk size
-   overlap
-   boundary selection
-   separators
-   metadata inheritance
-   source traceability

### Retrieval chunk vs generation context

Explain the idea of retrieving small passages while providing larger
parent context to the LLM.

### Failure modes

Cover:

-   answer split across chunks
-   lost headings
-   duplicated information
-   excessive overlap
-   tiny meaningless chunks
-   huge low-precision chunks
-   table fragmentation
-   code fragmentation

Link to Explore-RAG's text-splitting experiment where appropriate.

------------------------------------------------------------------------

## Chapter 6 --- Embeddings

Build embedding intuition before discussing vector stores.

Cover:

-   what an embedding is
-   text → numerical vector
-   semantic representation
-   embedding dimensions
-   embedding spaces
-   document embeddings
-   query embeddings
-   why document and query representations must be compatible
-   cosine similarity
-   dot product
-   Euclidean distance
-   normalization
-   multilingual embeddings
-   domain-specific embeddings
-   embedding model selection
-   dimensionality
-   model upgrades
-   stale embeddings
-   re-embedding

Mention representative model families as examples, such as OpenAI
embedding models, Voyage, BGE, E5, and sentence-transformer models,
while avoiding claims that one is universally best.

Explain that an embedding is not a stored fact and similarity is not a
probability of correctness.

------------------------------------------------------------------------

## Chapter 7 --- Vector Stores and Vector Indexes

First distinguish:

-   vector
-   embedding
-   vector record
-   vector store
-   vector database
-   vector index

Explain a typical record:

**vector + chunk text/reference + metadata + source/provenance**

### Vector storage systems

Discuss representative systems such as:

-   Pinecone
-   Weaviate
-   Chroma
-   Qdrant
-   pgvector
-   FAISS
-   Milvus
-   Elasticsearch/OpenSearch vector search

The goal is to explain categories and trade-offs, not rank vendors.

### Search approaches

Cover:

-   brute-force / exact nearest-neighbor search
-   approximate nearest-neighbor search
-   recall vs latency
-   index build cost
-   memory trade-offs

### Index structures

Explain:

-   flat search
-   HNSW
-   IVF / IVF Flat
-   product quantization
-   combinations such as IVF + PQ

For HNSW cover:

-   graph intuition
-   layers
-   neighbors
-   entry points
-   search traversal
-   `M`
-   `efConstruction`
-   `efSearch`

For IVF cover:

-   clustering
-   centroids
-   inverted lists
-   probing lists

For PQ cover:

-   vector compression
-   sub-vectors
-   codebooks
-   memory/accuracy trade-offs

Also cover insertions, updates, deletions, rebuilds, and stale records.

------------------------------------------------------------------------

## Chapter 8 --- Query Processing

A user's raw question does not always need to be searched exactly as
written.

Cover:

-   query normalization
-   spelling/noise handling
-   entity extraction
-   intent
-   constraints
-   dates
-   product/version identifiers
-   metadata constraints

### Query rewriting

Explain why a query may be rewritten and how rewriting can also destroy
useful information.

### Multi-query expansion

Explain generating multiple search formulations to improve candidate
recall.

### HyDE

Explain Hypothetical Document Embeddings:

-   generate a hypothetical answer/document
-   embed it
-   retrieve real documents near that representation

Discuss where it may help and how generated assumptions can mislead
retrieval.

### Query decomposition

Explain breaking multi-part or multi-hop questions into smaller
retrieval problems.

------------------------------------------------------------------------

## Chapter 9 --- Retrieval

Explain candidate retrieval as a separate stage from generation.

### Dense retrieval

Cover:

-   query embedding
-   nearest-neighbor search
-   cosine/dot-product scoring
-   top-k
-   ANN candidate retrieval

### Sparse retrieval

Cover:

-   lexical retrieval
-   term frequency intuition
-   inverse document frequency
-   TF-IDF
-   BM25
-   exact identifiers
-   rare terms
-   error codes
-   names

Explain why lexical search can outperform dense search for some queries.

### Metadata filtering

Cover:

-   date
-   department
-   source
-   language
-   document type
-   version
-   tenant/access constraints

Explain pre-filtering vs post-filtering conceptually.

### Retrieval parameters

Cover:

-   top-k
-   score thresholds
-   candidate recall
-   over-retrieval
-   missing relevant chunks
-   irrelevant high-scoring chunks

------------------------------------------------------------------------

## Chapter 10 --- Hybrid Retrieval

Explain why dense and sparse retrieval solve different problems.

Cover:

-   dense + sparse retrieval
-   parallel candidate generation
-   score normalization problems
-   rank-based fusion
-   Reciprocal Rank Fusion (RRF)
-   weighted fusion
-   deduplication
-   metadata filters with hybrid retrieval

Explain RRF carefully, including the intuition behind combining ranks
rather than incompatible raw scores.

Discuss queries where hybrid retrieval is especially useful:

-   semantic paraphrases containing exact identifiers
-   product names
-   error codes
-   technical terminology
-   proper nouns

------------------------------------------------------------------------

## Chapter 11 --- Reranking

Separate first-stage retrieval from second-stage relevance scoring.

Cover:

-   why reranking exists
-   candidate generation vs reranking
-   bi-encoder intuition
-   cross-encoder intuition
-   query-document joint scoring
-   top-20 → top-3 style pipelines
-   reranking APIs/models as examples
-   latency trade-offs
-   reranking depth

### Diversity

Explain:

-   redundant retrieved chunks
-   diversity-aware selection
-   Maximal Marginal Relevance (MMR)
-   relevance vs diversity

### Failure modes

Cover:

-   reranker removes useful evidence
-   candidate set never contained the answer
-   reranking too many documents
-   duplicate passages dominating context

------------------------------------------------------------------------

## Chapter 12 --- Context Construction

Retrieval results are not automatically good LLM context.

Cover:

-   selecting final passages
-   removing duplicates
-   preserving source IDs
-   grouping related chunks
-   parent expansion
-   formatting chunks
-   ordering chunks
-   document separators
-   citations/source labels
-   token budgets
-   context limits
-   trimming
-   relevance ordering
-   chronological ordering
-   lost-in-the-middle effects
-   conflicting passages
-   redundant passages

Explain the distinction between **retrieved candidates** and **final
context**.

------------------------------------------------------------------------

## Chapter 13 --- Prompt Assembly, Grounding, and Answer Generation

Explain the final transition from retrieved evidence to an answer.

### Prompt assembly

Cover:

-   system instructions
-   user question
-   retrieved context
-   source identifiers
-   answer format
-   citation instructions
-   refusal/abstention instructions

### Grounding

Cover:

-   evidence-supported generation
-   unsupported claims
-   insufficient evidence
-   partial evidence
-   conflicting evidence
-   answer only from supplied context
-   when the model should abstain

### LLM behavior

Explain that the LLM does not automatically become truthful because
context was supplied.

Cover:

-   instruction following
-   context use
-   context neglect
-   hallucination
-   synthesis across passages
-   citation generation

### Final answer

Cover:

-   citations
-   source attribution
-   claim-to-source traceability
-   answer completeness
-   uncertainty

------------------------------------------------------------------------

## Chapter 14 --- RAG Evaluation

Evaluation must separate retrieval quality from generation quality.

### Retrieval evaluation

Cover:

-   relevance labels
-   hit rate
-   precision@k
-   recall@k
-   MRR
-   MAP where useful
-   NDCG intuition
-   candidate recall
-   retrieval latency

### Generation evaluation

Cover:

-   correctness
-   faithfulness / groundedness
-   relevance
-   completeness
-   citation correctness
-   citation completeness
-   abstention quality

### Evaluation datasets

Cover:

-   question
-   expected/reference answer
-   relevant document/chunk IDs
-   answerable vs unanswerable questions
-   difficult negatives
-   conflicting sources
-   version-sensitive questions

### Evaluation methods

Discuss:

-   human evaluation
-   deterministic checks
-   model-as-judge
-   strengths and limitations of LLM judges
-   retrieval traces
-   stage-by-stage evaluation

Never fabricate benchmark numbers.

------------------------------------------------------------------------

## Chapter 15 --- RAG Failure Modes and Debugging

Organize failures by pipeline stage.

### Source failures

-   missing knowledge
-   stale knowledge
-   wrong versions
-   inaccessible sources

### Loading failures

-   broken extraction
-   missing tables
-   OCR errors
-   lost structure

### Cleaning failures

-   useful text removed
-   metadata lost
-   duplicates retained

### Chunking failures

-   wrong boundaries
-   insufficient context
-   oversized chunks
-   excessive overlap

### Embedding failures

-   domain mismatch
-   multilingual mismatch
-   changed embedding model
-   incompatible index/query embeddings

### Retrieval failures

-   answer not in top-k
-   lexical mismatch
-   semantic false positives
-   bad filters
-   low candidate recall

### Reranking failures

-   relevant candidate demoted
-   insufficient candidate pool

### Context failures

-   truncation
-   duplication
-   contradictory evidence
-   poor ordering

### Generation failures

-   unsupported synthesis
-   ignored context
-   fabricated citations
-   failure to abstain

Teach the principle:

**Find the earliest stage where the correct evidence disappeared.**

------------------------------------------------------------------------

## Chapter 16 --- Advanced RAG Patterns

Introduce these only after the basic pipeline is understood.

Cover conceptually:

-   query routing
-   query decomposition
-   multi-hop retrieval
-   parent-child retrieval
-   contextual retrieval
-   sentence-window retrieval
-   hierarchical retrieval
-   metadata-aware retrieval
-   self-query retrieval
-   multi-vector retrieval
-   late interaction / ColBERT intuition
-   contextual compression
-   iterative retrieval
-   corrective RAG
-   self-RAG
-   graph-based RAG / GraphRAG intuition
-   agentic RAG
-   multimodal RAG

For each pattern explain:

**problem → mechanism → advantage → cost → failure mode → when it is
worth considering**

Do not present advanced patterns as mandatory improvements.

------------------------------------------------------------------------

## Chapter 17 --- Production RAG

Finish with system-level concerns.

Cover:

-   ingestion pipelines
-   incremental indexing
-   document updates
-   deletion
-   stale embeddings
-   index migration
-   embedding-model migration
-   caching
-   latency
-   throughput
-   batching
-   cost
-   observability
-   retrieval traces
-   logging
-   evaluation in production
-   feedback loops
-   access control
-   tenant isolation
-   data privacy
-   PII
-   source permissions
-   prompt injection through retrieved documents
-   poisoned documents
-   auditability
-   citations
-   versioning
-   rollback
-   freshness

Explain how production requirements change architecture without turning
this repository into a production implementation guide.

------------------------------------------------------------------------

# 5. Chapter writing format

Do not force every chapter into an identical template, but keep a
recognizable teaching flow.

A strong chapter generally contains:

1.  **The problem**
2.  **Intuition**
3.  **Core mechanism**
4.  **Architecture / flow**
5.  **Important terminology**
6.  **Publicly available example**
7.  **Trade-offs**
8.  **Failure modes**
9.  **Where it appears in a RAG pipeline**
10. **Explore-RAG connection**, when one exists
11. **References / further reading**

Use subsections freely when a topic is large.

There is no requirement for:

-   runnable code
-   a custom dataset
-   exercises
-   quizzes
-   implementation assignments
-   a fictional running example

A chapter may contain formulas, pseudocode, or tiny snippets only when
they materially improve the explanation.

------------------------------------------------------------------------

# 6. Sources and examples

This repository should be reference-driven.

Preferred sources:

1.  original research papers
2.  official project/model/database documentation
3.  respected engineering documentation or technical blogs
4.  reputable educational resources

Use existing public examples when they explain a concept well. Cite the
original source close to the claim or example.

Do not:

-   copy large sections of another article
-   copy another site's diagrams without checking reuse rights
-   invent benchmarks
-   invent production statistics
-   cite an aggregator when the primary source is available
-   present vendor marketing claims as universal facts

When useful, create a new explanatory diagram from first principles
instead of copying a copyrighted image.

------------------------------------------------------------------------

# 7. Explore-RAG relationship

Explore-RAG is an optional experimentation companion.

Relevant chapter sections may include:

> **Try it in Explore-RAG:** change X and observe Y.

Possible mappings include:

-   chunking → Text Splitting
-   embeddings → Vector Embedding
-   indexes → Vector Index
-   retrieval → Semantic Search
-   context → Context Generation

Only link to functionality that actually exists.

The theory site must remain complete without Explore-RAG.

------------------------------------------------------------------------

# 8. Delivery plan

## Milestone 0 --- Repository foundation

-   establish the Astro/MDX or equivalent static structure
-   create landing page
-   create chapter navigation
-   create shared typography/styles
-   support images, diagrams, citations, tables, formulas, and code
    blocks
-   create previous/next chapter navigation
-   deploy static site

**Done when:** the site can render one complete chapter cleanly on
desktop and mobile.

## Milestone 1 --- Pipeline foundation

Write:

-   Chapter 1 --- What is RAG?
-   Chapter 2 --- Complete RAG Pipeline
-   Chapter 3 --- Data Sources and Loading
-   Chapter 4 --- Cleaning and Preparation

## Milestone 2 --- Indexing fundamentals

Write:

-   Chapter 5 --- Chunking
-   Chapter 6 --- Embeddings
-   Chapter 7 --- Vector Stores and Indexes

## Milestone 3 --- Query-time retrieval

Write:

-   Chapter 8 --- Query Processing
-   Chapter 9 --- Retrieval
-   Chapter 10 --- Hybrid Retrieval
-   Chapter 11 --- Reranking
-   Chapter 12 --- Context Construction

## Milestone 4 --- Generation and evaluation

Write:

-   Chapter 13 --- Prompt Assembly, Grounding, and Answer Generation
-   Chapter 14 --- RAG Evaluation
-   Chapter 15 --- Failure Modes and Debugging

## Milestone 5 --- Advanced and production topics

Write:

-   Chapter 16 --- Advanced RAG Patterns
-   Chapter 17 --- Production RAG

## Milestone 6 --- Final review

-   verify chapter ordering
-   remove duplicated explanations
-   verify terminology
-   verify citations and external links
-   verify diagrams
-   verify Explore-RAG links
-   check responsive layout
-   check accessibility
-   check navigation
-   run production build
-   review the complete pipeline against the supplied RAG architecture
    diagram

**Final gate:** every major concept in the supplied architecture diagram
is mapped to a chapter or subsection.

------------------------------------------------------------------------

# 9. Success criteria

The project is successful when a learner can read it from beginning to
end and understand:

-   why RAG exists
-   the difference between indexing and query-time processing
-   how documents become retrievable vectors
-   why cleaning and metadata matter
-   how chunking affects retrieval
-   what embeddings represent
-   how vector indexes work
-   how HNSW, IVF, and PQ differ conceptually
-   why sparse and dense retrieval behave differently
-   how hybrid retrieval and RRF work
-   why reranking is separate from retrieval
-   how final context is constructed
-   how grounding and citations work
-   how RAG is evaluated
-   where RAG systems fail
-   how advanced RAG patterns extend the basic pipeline
-   what changes when RAG is operated in production

The learner should understand the system without having to run an
embedding model, vector database, or LLM.

------------------------------------------------------------------------

# 10. Primary design reference

**Backend from First Principle**\
https://github.com/DsThakurRawat/Backend-from-first-Principle

Use it as inspiration for chapter organization, learning flow,
navigation, and the idea of explaining one engineering area
progressively from fundamentals to advanced topics.

Do not copy its content or branding.
