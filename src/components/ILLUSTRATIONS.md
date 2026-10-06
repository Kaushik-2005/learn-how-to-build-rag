# Illustration inventory

The illustrations are stored as reusable Astro components in this directory. They are native HTML/CSS/SVG visuals, not generated image files.

| Chapter | Illustration | Component / mode | Used for |
| --- | --- | --- | --- |
| Homepage | Knowledge illustration | `KnowledgeIllustration.astro` | Unstructured knowledge -> retrieval -> grounded response |
| Chapter 1 | Two kinds of memory | `RagIllustration.astro` with `kind="rag-basics"` | Parametric model memory complemented by selected, traceable external evidence |
| Chapter 1 | Search versus RAG | `RagIllustration.astro` with `kind="search-vs-rag"` | Ranked evidence list compared with context-backed generated response |
| Chapter 2 | Complete pipeline | `PipelineDiagram.astro` | Indexing path and query path |
| Chapter 2 | Retrievable record | `RagIllustration.astro` with `kind="record-cutaway"` | Search representation connected by ID to recoverable text and provenance |
| Chapter 2 | Document and query lifecycles | `RagIllustration.astro` with `kind="lifecycle-pair"` | Separate indexing and query-time sequences linked by IDs and versions |
| Chapter 3 | Source map | `RagIllustration.astro` with `kind="sources"` | PDFs, web, structured data, repositories, collaboration, and media |
| Chapter 3 | Loader contract | `RagIllustration.astro` with `kind="loading-flow"` | Source -> loader -> content and metadata -> document record |
| Chapter 3 | Structure preservation | `RagIllustration.astro` with `kind="extract-structure"` | Table extraction preserving row/header relationships |
| Chapter 4 | Document preparation | `RagIllustration.astro` with `kind="cleaning"` | Decode, clean, validate, and attach provenance |
| Chapter 4 | Preparation record | `RagIllustration.astro` with `kind="prep-flow"` | Raw source -> extracted representation -> prepared representation -> ready for chunking |
| Chapter 5 | Chunk boundaries and overlap | `RagIllustration.astro` with `kind="chunking"` | Meaningful split with repeated boundary context |
| Chapter 5 | Recursive separator priority | `RagIllustration.astro` with `kind="recursive-flow"` | Larger semantic separators before smaller fallback cuts |
| Chapter 5 | Chunking policy | `RagIllustration.astro` with `kind="decision-record"` | Boundaries, limits, overlap, and traceability made explicit |
| Chapter 5 | Context expansion | `RagIllustration.astro` with `kind="context-flow"` | Child chunks -> parent context -> final context |
| Chapter 5 | Pipeline position | `RagIllustration.astro` with `kind="chunk-position"` | Chunking highlighted between preparation and embedding, before the vector index |
| Chapter 6 | Embedding space | `RagIllustration.astro` with `kind="embeddings"` | Text represented as vectors |
| Chapter 6 | Text to vector | `RagIllustration.astro` with `kind="vector-encoding"` | An input chunk encoded as a schematic list of learned coordinates |
| Chapter 6 | Similarity geometry | `RagIllustration.astro` with `kind="similarity-metrics"` | Cosine angle, dot-product alignment/magnitude, and Euclidean separation |
| Chapter 6 | Embedding flow | `RagIllustration.astro` with `kind="embedding-flow"` | Text/query encoders -> vectors -> candidates |
| Chapter 7 | Vector record | `RagIllustration.astro` with `kind="vector-record"` | Embedding, identity, provenance, metadata, and access constraints |
| Chapter 7 | Exact vs approximate search | `RagIllustration.astro` with `kind="search-modes"` | Exhaustive comparison versus candidate subset exploration |
| Chapter 7 | HNSW layers | `RagIllustration.astro` with `kind="hnsw-layers"` | Sparse upper graph moves and dense lower-layer refinement |
| Chapter 7 | IVF + PQ | `RagIllustration.astro` with `kind="ivf-pq"` | Coarse partition probing and compact product-quantized codes |
| Chapter 8 | Query workbench | `RagIllustration.astro` with `kind="query-workbench"` | Preserve entities and constraints while decomposing a multi-part question |
| Chapter 8 | Query-time position | `RagIllustration.astro` with `kind="query-position"` | Query processing highlighted between the user question and candidate retrieval |
| Chapter 9 | Ranked candidate set | `RagIllustration.astro` with `kind="retrieval-candidates"` | A scoped query ranks indexed passages and returns a top-k candidate set, not an answer |
| Chapter 10 | Dense/sparse rank fusion | `RagIllustration.astro` with `kind="hybrid-fusion"` | Complementary ranked lists are fused and deduplicated into one candidate order |
| Chapter 11 | Query-aware reranking and diversity | `RagIllustration.astro` with `kind="reranking"` | A joint query–passage scorer reorders retrieved candidates; diversity-aware selection avoids spending the shortlist on near-duplicates |
| Chapter 11 | Bi-encoder vs. cross-encoder | `RagIllustration.astro` with `kind="bi-cross-encoders"` | Separately encoded reusable vectors support corpus search; joint query–passage inputs support focused candidate scoring |
| Chapter 12 | Candidate-to-context assembly | `RagIllustration.astro` with `kind="context-assembly"` | Relevant passages are selected, duplicates removed, conflicting versions kept visible, and evidence packed with source labels into a bounded context |
| Chapter 13 | Evidence-grounded generation | `RagIllustration.astro` with `kind="grounded-generation"` | Instructions, a question, and labeled evidence become a prompt; answer claims are linked to sources or qualified when support is missing |
| Chapter 14 | Retrieval and generation scorecards | `RagIllustration.astro` with `kind="evaluation"` | One fixed query set is assessed separately for retrieval evidence and answer quality |
| Chapter 15 | Evidence-loss diagnostic trace | `RagIllustration.astro` with `kind="debugging-map"` | A source fact disappears at loading, producing downstream retrieval and answer symptoms; locate the first broken handoff |
| Chapter 16 | Advanced-pattern decision map | `RagIllustration.astro` with `kind="advanced-patterns"` | Different bottlenecks point to optional patterns, alongside the added costs or complexity |
| Chapter 17 | Production operations loop | `RagIllustration.astro` with `kind="production-loop"` | Versioned ingestion, governed query serving, observability, evaluation, and rollback form an operating cycle |

When adding a new chapter illustration, add its component usage to this table and keep the visual focused on a mechanism, transformation, or relationship that prose alone does not explain as clearly.
