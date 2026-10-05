# AGENTS.md --- RAG From First Principles

## Mission

Build and maintain a theory-first learning resource that explains
Retrieval-Augmented Generation from first principles.

This repository is **not a RAG application**. It is a structured
technical reference.

The learner should be able to understand the complete pipeline:

**Sources → Loading → Cleaning → Chunking → Embedding → Indexing → Query
Processing → Retrieval → Reranking → Context Construction → Prompt
Assembly → LLM → Grounded Answer → Evaluation**

`roadmap.md` is the source of truth for curriculum scope and order.

------------------------------------------------------------------------

## 1. Reference project

Use the organization and teaching style of:

https://github.com/DsThakurRawat/Backend-from-first-Principle

as the primary structural inspiration.

Useful ideas to borrow:

-   ordered chapters
-   large self-contained topics
-   progressive first-principles explanations
-   documentation-style navigation
-   diagrams and visual explanations
-   a simple learning website

Do not copy its wording, branding, diagrams, or technical content.

The RAG project may use Astro/MDX or similar static-site tooling. The
framework is infrastructure, not the project itself.

------------------------------------------------------------------------

## 2. Core rule: teach, do not build a RAG system

Do not introduce implementation work merely to make a lesson look
practical.

The repository does not need:

-   an embedding API
-   an LLM API
-   a vector database
-   a RAG backend
-   a custom ingestion service
-   notebooks
-   authentication
-   a database
-   user accounts
-   model hosting
-   a custom evaluation service

No chapter should require the learner to run a model or external service
in order to understand it.

If code is useful for explaining an algorithm, a small snippet or
pseudocode is acceptable. Code is explanatory material, not the
chapter's objective.

------------------------------------------------------------------------

## 3. Content workflow

Before writing a chapter:

1.  Read `roadmap.md`.
2.  Identify the exact chapter and its required subtopics.
3.  Research the topic using primary or authoritative sources.
4.  Prefer original papers and official documentation.
5.  Decide which diagrams or examples materially improve understanding.
6.  Write the chapter from first principles.
7.  Cite external claims and examples.
8.  Check that the chapter connects correctly to the stages before and
    after it.
9.  Remove unnecessary framework/vendor-specific detail.
10. Verify links and technical terminology.

Do not auto-generate every chapter as shallow placeholder content.

Finish one chapter well before expanding the next.

------------------------------------------------------------------------

## 4. Chapter philosophy

A chapter should answer four questions:

**Why does this exist?**\
What problem in the RAG pipeline required this component?

**How does it work?**\
Explain the mechanism without hiding it behind framework APIs.

**What are the trade-offs?**\
What improves, what gets worse, and what parameters matter?

**How does it fail?**\
What goes wrong and how does that failure affect later pipeline stages?

The learner should understand the mechanism even if every named
framework disappears tomorrow.

------------------------------------------------------------------------

## 5. Recommended chapter shape

Do not mechanically force identical headings into every chapter. Use the
structure that best explains the subject.

A typical chapter can contain:

1.  Problem
2.  Intuition
3.  Core concept
4.  How it works
5.  Pipeline position
6.  Important terminology
7.  Architecture or diagram
8.  Existing public example
9.  Trade-offs
10. Failure modes
11. Related techniques
12. Explore-RAG connection
13. References

Large chapters may have many subsections.

For example, the Chunking chapter should cover fixed-size, token,
recursive, semantic, sentence, parent-child, code-aware chunking,
overlap, boundaries, and failure modes inside one coherent chapter
rather than creating tiny pages for every term.

------------------------------------------------------------------------

## 6. Sources and citation rules

The site should be built from verifiable references, not invented
practical projects.

Preferred source order:

1.  original research paper
2.  official documentation
3.  official engineering/research blog
4.  respected technical publication
5.  reputable educational material

When explaining a named algorithm, find the original or canonical source
where practical.

Examples:

-   HNSW → original HNSW paper plus current vector-system documentation
    if needed
-   BM25 → authoritative information-retrieval references
-   HyDE → original HyDE paper
-   RRF → original/canonical RRF reference
-   ColBERT → original ColBERT paper
-   Self-RAG → original paper
-   GraphRAG → primary project/paper documentation

Vendor documentation is appropriate for describing that vendor's
implementation. Do not use vendor claims to establish universal
performance conclusions.

Every non-trivial external factual claim should be supportable by a
citation.

Never invent:

-   benchmark numbers
-   latency numbers
-   recall improvements
-   model rankings
-   production statistics
-   citations
-   URLs
-   paper titles
-   experiment results

If a claim cannot be verified, remove it or explicitly qualify it.

------------------------------------------------------------------------

## 7. Using external examples

Prefer existing public examples instead of creating artificial
implementation projects.

Good examples include:

-   a worked example from a paper
-   an official documentation example
-   a published benchmark
-   a public architecture diagram that can be linked/cited
-   a well-known information-retrieval example
-   a small mathematical example derived only to explain a mechanism

When using an external example:

-   cite the original source
-   summarize rather than copy
-   explain why the example matters
-   distinguish the source's observation from this site's explanation
-   do not reproduce copyrighted diagrams unless reuse is permitted

If a diagram is important but cannot safely be reused, create an
original explanatory diagram based on the underlying technical concept
and cite the technical source.

------------------------------------------------------------------------

## 8. Technical writing rules

Write for a developer learning RAG, not for someone already specializing
in information retrieval.

Use plain language first, then introduce the formal term.

Prefer:

> BM25 rewards documents containing useful query terms while reducing
> the importance of terms that appear almost everywhere.

before introducing its full scoring formula.

For algorithms:

**intuition → mechanism → important parameters → trade-offs → failure
modes**

For formulas:

-   define every variable
-   explain what changing each important term does
-   include the formula only when it improves understanding
-   do not turn the site into a mathematics textbook unnecessarily

For vendor/model lists:

-   explain why the examples are being shown
-   avoid exhaustive catalogs
-   avoid declaring a universal winner
-   separate concept from product

------------------------------------------------------------------------

## 9. Technical correctness guardrails

Maintain these distinctions carefully:

-   RAG does not guarantee factual answers.
-   Retrieved text may itself be wrong or malicious.
-   Embeddings do not store facts in a human-readable form.
-   Vector similarity is not a probability of correctness.
-   Semantic similarity is not identical to relevance.
-   Exact search and approximate nearest-neighbor search are different.
-   A vector store and a vector index are not necessarily the same
    thing.
-   Candidate retrieval and reranking are separate stages.
-   Retrieval `top-k` is not a quality guarantee.
-   Dense retrieval and sparse retrieval solve different matching
    problems.
-   Hybrid retrieval requires a method for combining results.
-   RRF combines ranks rather than assuming raw scores are directly
    comparable.
-   Reranking cannot recover evidence that was never retrieved.
-   Retrieved candidates are not automatically the final LLM context.
-   Metadata filters are not a substitute for proper authorization
    enforcement.
-   Prompt instructions are not an access-control mechanism.
-   Citations generated by an LLM must be traceable to actual supplied
    sources.
-   Evaluation must distinguish retrieval quality from answer quality.
-   Advanced RAG techniques are not automatically better than a simple
    pipeline.

When uncertain, research before asserting.

------------------------------------------------------------------------

## 10. Diagrams

Use diagrams when they clarify:

-   sequence
-   hierarchy
-   data transformation
-   search/index structure
-   trade-offs
-   relationships between pipeline stages

Good diagram candidates include:

-   complete RAG architecture
-   indexing vs query-time paths
-   chunking boundaries
-   embedding-space intuition
-   HNSW layers
-   IVF partitioning
-   product quantization
-   dense vs sparse retrieval
-   hybrid retrieval + RRF
-   retrieval → reranking
-   context construction
-   grounded generation
-   evaluation flow

Diagrams should be understandable with surrounding text.

Prefer original diagrams made for the project. Cite the technical source
that informed them when appropriate.

Do not add decorative diagrams merely to make a page longer.

------------------------------------------------------------------------

## 11. Explore-RAG integration

Explore-RAG is an independent experimental companion.

https://explore-rag.vercel.app/

A chapter may contain a small section such as:

> **Explore this:** Open the Text Splitting stage in Explore-RAG and
> compare two chunk sizes.

Only do this when the relevant experiment actually exists.

Likely mappings:

-   Chunking → Text Splitting
-   Embeddings → Vector Embedding
-   Vector Indexes → Vector Index
-   Retrieval → Semantic Search
-   Context Construction → Context Generation

Do not make Explore-RAG a runtime dependency.

Do not claim a control or experiment exists without verifying it.

The theory chapter must remain complete if Explore-RAG is unavailable.

------------------------------------------------------------------------

## 12. Site architecture

Keep the website static.

Astro + MDX is acceptable and may follow the reference repository's
general approach.

Use TypeScript/JavaScript only for site infrastructure where useful:

-   navigation
-   search
-   reusable UI
-   theme behavior
-   content metadata
-   static generation

Do not introduce client-side application complexity without a clear
reading/learning benefit.

Avoid:

-   backend services
-   databases
-   API routes
-   server rendering unless required by deployment
-   authentication
-   heavy state management
-   runtime model calls
-   runtime vector search

The final site should be readable even though the subject being taught
is technically complex.

------------------------------------------------------------------------

## 13. Repository organization

Prefer chapter-oriented organization that mirrors the roadmap.

Conceptually:

``` text
1.What-is-RAG/
2.RAG-Pipeline-Architecture/
3.Data-Sources-and-Loading/
4.Document-Cleaning-and-Preparation/
5.Chunking/
6.Embeddings/
7.Vector-Stores-and-Indexes/
8.Query-Processing/
9.Retrieval/
10.Hybrid-Retrieval/
11.Reranking/
12.Context-Construction/
13.Prompt-Assembly-and-Grounding/
14.RAG-Evaluation/
15.RAG-Failure-Modes/
16.Advanced-RAG/
17.Production-RAG/
```

The physical Astro/MDX layout may differ if needed, but navigation and
learner-facing order must follow this sequence.

Each chapter may have its own image/assets folder when useful.

Keep shared assets shared only when genuinely reused.

------------------------------------------------------------------------

## 14. Scope control

Before adding something, ask:

**Does this help explain RAG?**

If no, do not add it.

Avoid overengineering such as:

-   custom CMS
-   user progress backend
-   accounts
-   analytics infrastructure
-   complex animations
-   interactive vector visualizers when a diagram suffices
-   custom RAG demo
-   large component libraries
-   unnecessary build tooling
-   unnecessary dependencies

This repository succeeds through the quality of its explanations, not
the complexity of its codebase.

------------------------------------------------------------------------

## 15. Milestone execution

Follow milestones in `roadmap.md`.

For each milestone:

1.  complete the required chapters
2.  verify references
3.  verify diagrams
4.  verify navigation
5.  verify responsive rendering
6.  run the production build
7.  remove duplicated material
8.  check terminology against earlier chapters

Do not mark a milestone complete because files exist. The chapters must
actually cover their roadmap requirements.

------------------------------------------------------------------------

## 16. Definition of done for a chapter

A chapter is complete when:

-   all roadmap subtopics are addressed
-   the central mechanism is explained from first principles
-   important terminology is defined
-   major trade-offs are explained
-   major failure modes are explained
-   external factual claims are cited
-   public examples are attributed
-   diagrams are original or properly sourced
-   related pipeline stages are connected
-   Explore-RAG links, if present, are verified
-   navigation works
-   the page renders correctly on desktop and mobile
-   there are no invented benchmarks or unverifiable claims

Runnable code, exercises, quizzes, and implementation assignments are
**not** completion requirements.

------------------------------------------------------------------------

## 17. Final project check

Before declaring the project complete, compare the entire curriculum
against the supplied RAG pipeline architecture.

Confirm coverage of at least:

-   data sources
-   loaders
-   cleaning
-   metadata
-   OCR
-   deduplication
-   PII handling
-   chunking strategies
-   chunk overlap
-   embeddings
-   embedding-model compatibility
-   vector stores
-   HNSW
-   IVF
-   product quantization
-   query rewriting
-   HyDE
-   multi-query expansion
-   dense retrieval
-   BM25/sparse retrieval
-   metadata filtering
-   hybrid retrieval
-   RRF
-   reranking
-   cross-encoders
-   MMR/diversity
-   context formatting
-   citations
-   token limits
-   prompt assembly
-   grounding
-   LLM generation
-   answer traceability
-   retrieval evaluation
-   generation evaluation
-   failure debugging
-   advanced RAG patterns
-   production concerns

If an item is missing, add it to the appropriate existing chapter before
creating a new chapter.

------------------------------------------------------------------------

## 18. Guiding principle

**Explain the system beneath the framework.**

A learner who finishes this resource should understand RAG even if they
never use LangChain, LlamaIndex, Pinecone, Qdrant, OpenAI, or any other
specific tool.

Frameworks and products are examples.

The pipeline and its trade-offs are the subject.
